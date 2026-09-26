# C++ 万年历

[![build](https://github.com/ting2698009013/cpp-perpetual-calendar/actions/workflows/build.yml/badge.svg)](https://github.com/ting2698009013/cpp-perpetual-calendar/actions/workflows/build.yml)

一个 Windows 控制台万年历，也是我的 C++ 课程作业。程序在单个源文件中实现了公历、农历、节气和日期运算等功能，保留了当时从基础语法逐步完成综合程序的记录。

## 功能

- 公历转农历，并显示干支年
- 农历转公历
- 显示指定月份的月历
- 计算某一天距离今天的天数
- 根据前后天数推算日期
- 计算任意两个日期之间的天数差
- 查询二十四节气
- 查询常见公历和农历节日
- 日期合法性及闰年判断

农历和节气数据覆盖 **1900—2025 年**，超出范围的输入会给出提示。

## 构建

环境要求：Windows 10/11、Visual Studio 2022、MSVC v143。

1. 打开 `Project2.sln`。
2. 选择 `Release | x64` 或 `Debug | x64`。
3. 按 `Ctrl + F5` 编译并运行。

也可以在 Visual Studio Developer PowerShell 中运行：

```powershell
msbuild Project2.sln /p:Configuration=Release /p:Platform=x64
```

## 自动验证

程序带有一个无需交互的自检入口，覆盖闰日合法性、日期正反向换算和一个已知农历日期：

```powershell
.\x64\Release\Project2.exe --self-test
```

GitHub Actions 会在每次推送和 Pull Request 时使用 Visual Studio 构建并运行自检。

## 整理说明

公开版本保留了原作业的核心实现，同时完成了以下整理：

- 将源码统一为 UTF-8，避免中文注释乱码
- 使用更明确的源文件名 `perpetual_calendar.cpp`
- 修复 Windows SDK 宏名冲突和旧式 `getch` 编译问题
- 补充年份与日期边界检查，避免查询超出内置数据范围
- 修复跨闰年的反向日期换算和重复进入菜单导致的递归堆栈增长
- 移除 Visual Studio 缓存与编译产物

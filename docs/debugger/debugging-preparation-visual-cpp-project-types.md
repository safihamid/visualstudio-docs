---
title: "Prepare to debug C++ projects | Microsoft Docs"
description: Get information about preparing to debug the basic project types created by the Visual C++ project templates in Visual Studio.

ms.date: "11/04/2016"
ms.topic: "conceptual"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "project templates, debugging"
  - "C++ projects, debugging"
  - "debug builds, project settings"
  - "debugging [C++]"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: "mikejo5000"
ms.author: "mikejo"
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - "cplusplus"
---
# Debugging Preparation: C++ Project Types

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]
This section describes how to debug the basic project types created by the [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] project templates.

 Note that those project types that create DLLs as their output have been grouped into [Debugging DLL Projects](../debugger/debugging-dll-projects.md) because of the common features they share.

## <a name="BKMK_In_this_topic"></a> In this topic
 [Recommended property settings](#BKMK_Recommended_Property_Settings)

 [Win32 projects](#BKMK_Win32_Projects)

- [To debug a C or C++ Win32 application](#BKMK_To_debug_a_C_or_C___Win32_application)

- [To manually set a Debug configuration](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="BKMK_Recommended_Property_Settings"></a> Recommended property settings
 Certain properties should be set the same way for all unmanaged debugging scenarios. The following tables display recommended property settings. Settings not listed here may vary among the different unmanaged project types. For more information, see [Project Settings for a C++ Debug Configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### Configuration Properties &#124; C/C++ &#124; Optimization node

|Property Name|Setting|
|-------------------|-------------|
|**Optimization**|Set to **Disabled (/0d).** Optimized code is harder to debug, because the generated instructions do not correspond directly to your source code. If you find your program has a bug that appears only in optimized code, you can turn this setting on, but remember that code shown in the **Disassembly** window is generated from optimized source that might not match what you see in your source windows. Other features, such as stepping, might not behave as expected.|

### Configuration Properties &#124; Linker &#124; Debugging node

|Property Name|Setting|
|-------------------|-------------|
|**Generate debugging information**|You should always set this option to **Yes (/DEBUG)** to create debugging symbols and files needed for debugging. When the application goes into production, you can set it to off.|

 [In this topic](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a> Win32 projects
 Win32 applications are traditional Windows programs written in C or C++. Debugging this type of application in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] is straightforward.

 Win32 applications include MFC applications and ATL projects. They use Windows APIs and may use MFC or ATL, but they do not use the common language runtime (CLR). They can, however, call managed code that uses the CLR.

 The following procedure explains how to debug a Win32 project from within [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Another way to debug a Win32 application is to start the application outside of [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] and attach to it. For more information, see [Attach to Running Processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> To debug a C or C++ Win32 application

1. Open the project in Visual Studio.

2. On the **Debug** menu, choose **Start**.

3. Debug using the techniques discussed in [First look at the debugger](../debugger/debugger-feature-tour.md).

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a> To manually set a Debug configuration

1. On the **View** menu, click **Property Pages**.

2. Click the **Configuration Properties** node to open it if it is not already

3. Select **General**, and set the value of the **Output** row to **Debug**.

4. Open the **C/C++** node, and select **General**.

    In the **Debug** row you specify the type of debugging information to be generated by the compiler. Values you might choose include **Program Database (/Zi)** or **Program Database for Edit & Continue (/ZI)**.

5. Select **Optimization**, and in the **Optimization** row, select **Disabled (/0d)** from the drop-down list.

    Optimized code is harder to debug, because the generated instructions do not correspond directly to your source code. If you find your program has a bug that appears only in optimized code, you can turn this setting on, but remember that code shown in the Disassembly window is generated from optimized source that may not match what you see in your source windows. Features such as stepping are likely to show breakpoints and execution point incorrectly.

6. Open the **Linker** node, and select **Debugging**. In the first **Generate** row, select **Yes (/DEBUG)** from the drop-down list. Always set this when you are debugging.

   For more information, see[Project Settings for a C++ Debug Configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [In this topic](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## See also
- [First look at the debugger](../debugger/debugger-feature-tour.md)
- [Project Settings for a C++ Debug Configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Attaching to a Running Program or Multiple Programs](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debug and Release Configurations](../debugger/how-to-set-debug-and-release-configurations.md)
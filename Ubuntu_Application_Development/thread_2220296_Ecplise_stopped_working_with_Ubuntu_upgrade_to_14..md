---
title: "Ecplise stopped working with Ubuntu upgrade to 14.04"
date: 2014-04-27
forum: Ubuntu Application Development
---

### Post by Ibrahim mufeed on 2014-04-27
Hello,

Two days ago I upgraded to the latest Ubuntu 14.04. Everything was working fine, until I tried to open Eclipse that I use for Java development. It shows the loading window but the program never loads. I started Eclipse from command line:

```
eclipse -consolelog

```

I receive the following output:

[PHP]!SESSION 2014-04-27 17:57:42.917 -----------------------------------------------
eclipse.buildId=debbuild
java.version=1.7.0_51
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86 -consolelog

!ENTRY org.eclipse.ui 4 0 2014-04-27 17:57:49.167
!MESSAGE Unable to create editor ID org.eclipse.jdt.ui.CompilationUnitEditor: No editor descriptor for id org.eclipse.jdt.ui.CompilationUnitEditor
!STACK 1
org.eclipse.ui.PartInitException: No editor descriptor for id org.eclipse.jdt.ui.CompilationUnitEditor
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:601)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:465)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:271)
	at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1459)
	at org.eclipse.ui.internal.EditorManager$5.runWithException(EditorManager.java:972)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3537)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3189)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$33.runWithException(Workbench.java:1600)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3537)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3189)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2609)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
	at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:124)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
!SUBENTRY 1 org.eclipse.ui 4 0 2014-04-27 17:57:49.174
!MESSAGE No editor descriptor for id org.eclipse.jdt.ui.CompilationUnitEditor

!ENTRY org.eclipse.ui 2 2 2014-04-27 17:57:49.416
!MESSAGE Ignored attempt to add saveable that was already registered
!STACK 0
org.eclipse.core.runtime.AssertionFailedException: unknown saveable: org.eclipse.ui.internal.DefaultSaveable@13b2f29 from part: org.eclipse.ui.internal.ErrorEditorPart@13b2f29
	at org.eclipse.ui.internal.SaveablesList.logWarning(SaveablesList.java:187)
	at org.eclipse.ui.internal.SaveablesList.addModel(SaveablesList.java:116)
	at org.eclipse.ui.internal.SaveablesList.addModels(SaveablesList.java:289)
	at org.eclipse.ui.internal.SaveablesList.postOpen(SaveablesList.java:695)
	at org.eclipse.ui.internal.PartList.partOpened(PartList.java:234)
	at org.eclipse.ui.internal.PartList.access$0(PartList.java:210)
	at org.eclipse.ui.internal.PartList$1.propertyChanged(PartList.java:40)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:375)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:610)
	at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:271)
	at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1459)
	at org.eclipse.ui.internal.EditorManager$5.runWithException(EditorManager.java:972)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3537)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3189)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$33.runWithException(Workbench.java:1600)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3537)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3189)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2609)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
	at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:124)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1438)

!ENTRY org.eclipse.ui 4 4 2014-04-27 17:57:49.586
!MESSAGE Could not create view: 'org.eclipse.jdt.ui.JavadocView'.

!ENTRY org.eclipse.ui 4 4 2014-04-27 17:57:49.589
!MESSAGE Could not create view: 'org.eclipse.jdt.ui.SourceView'.

!ENTRY org.eclipse.ui 2 2 2014-04-27 17:57:49.851
!MESSAGE Perspective Java has been made into a local copy
[/PHP]

The past two days I was searching the internet and the farthest I could reach was; deleting the "workspace" folder makes Eclipse starts but without any projects, plugins or settings.

Any idea how to resolve this issue?

Thanks in advance.

---


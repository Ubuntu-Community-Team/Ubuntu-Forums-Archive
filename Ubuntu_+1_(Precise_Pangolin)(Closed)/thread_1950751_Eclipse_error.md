---
title: "Eclipse error"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teachop on 2012-04-01
I installed eclipse cdt from the 12.04 repos and it won't start.  (An eclipse cdt downloaded into a folder starts fine)  Is this a package dependency problem or I need to do something to a config...

This is the error:

```
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry.
```

---

### Post by lucazade on 2012-04-01
here eclipse works without problem but I had to use a new configuration from scratch (removing .eclipse folder)

---

### Post by teachop on 2012-04-01
> **lucazade said:**
> here eclipse works without problem but I had to use a new configuration from scratch (removing .eclipse folder)
I am not 100% sure what you are saying.

Are you using the package from the repos, or one downloaded someplace else?  I am able to download an eclipse from the eclipse website and work with it fine.  What doesn't work for me is installing eclipse with package management.  Yes it did put itself in a ~/.eclipse folder.

---

### Post by sacridex on 2012-04-01
> **teachop said:**
> Yes it did put itself in a ~/.eclipse folder.
Thats just the config folder, remove it and the config will be reset.

---

### Post by teachop on 2012-04-01
Ok I understand.  I deleted the ~/.eclipse and it was recreated.  I get the same error afterwards.

---

### Post by lucazade on 2012-04-01
> **teachop said:**
> I am not 100% sure what you are saying.

Are you using the package from the repos, or one downloaded someplace else?  I am able to download an eclipse from the eclipse website and work with it fine.  What doesn't work for me is installing eclipse with package management.  Yes it did put itself in a ~/.eclipse folder.

Yes, I'm using the package from repos.. the only thing I had to do was to reset the eclipse settings I was using in Oneiric.

---

### Post by teachop on 2012-04-01
My install is "fresh" from beta 2 (reformat) and was just reapplying all the things I use.  Don't know what is causing the problem, I guess the eclipse packages is assuming something.  Java is fine, since the downloaded version worked OK when I tested that.

---

### Post by FabriceMG on 2012-04-01
Hello,

I confirm this error on a new install 12.04
Eclipse start and close with this error.

> !ENTRY org.eclipse.osgi 4 0 2012-04-01 20:38:59.676
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry. The applications available are: org.eclipse.ant.core.antRunner, org.eclipse.equinox.app.error, org.eclipse.equinox.p2.director, org.eclipse.equinox.p2.garbagecollector.application, org.eclipse.equinox.p2.publisher.InstallPublisher, org.eclipse.equinox.p2.publisher.EclipseGenerator, org.eclipse.equinox.p2.publisher.ProductPublisher, org.eclipse.equinox.p2.publisher.FeaturesAndBundlesPublisher, org.eclipse.equinox.p2.reconciler.application, org.eclipse.equinox.p2.repository.repo2runnable, org.eclipse.equinox.p2.repository.metadataverifier, org.eclipse.equinox.p2.artifact.repository.mirrorApplication, org.eclipse.equinox.p2.metadata.repository.mirrorApplication, org.eclipse.equinox.p2.updatesite.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.CategoryPublisher, org.eclipse.update.core.standaloneUpdate, org.eclipse.update.core.siteOptimizer.
    at org.eclipse.equinox.internal.app.EclipseAppContainer.startDefaultApp(EclipseAppContainer.java:248)
    at org.eclipse.equinox.internal.app.MainApplicationLauncher.run(MainApplicationLauncher.java:29)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1386)

---

### Post by teachop on 2012-04-01
Just for giggles I did sudo eclipse, and it came up fine.  Seems to work now.  Only had to sudo once.

---

### Post by LinuxN00b92 on 2012-04-02
I just upgraded my system from 11.10 to the 12.04 alpha today and experienced this problem. Initially Eclipse did launch, but it did not have the java functionalities working properly. It was unable to run any of my projects, create a new JAVA project or open the package explorer (where .class files are hidden, I could navigate through the projects but the source files and .class files were mixed). Synaptic reported that I had a jdk, the eclipse-jdt and what seemed like all of the necessary tools for working with java in eclipse installed. I got pissed and just purged everything related to java from my system. After I reinstalled it was still having the same problem :p  I tried running eclipse -clean and then I ran into the problem described by the other commentors on this thread. I tried renaming the .eclipse folder to make it generate a new one, but it did not help. It was resolved by the interesting 'sudo eclipse' suggestion. Everything was working again, w00t for random solutions that make no sense!

---

### Post by teachop on 2012-04-02
> **LinuxN00b92 said:**
> random solutions that make no sense
It perhaps needed to write to its install directory to finish the configuration on first execution.  When I had eclipse in my home directory there was no problem.  So it is a permissions issue (thus sudo).  I don't think the package is quite right.

---

### Post by kid1000002000 on 2012-04-03
fixed it for me. been looking all over for a solution, thank you!

---

### Post by afspear on 2012-04-04
> **teachop said:**
> Just for giggles I did sudo eclipse, and it came up fine.  Seems to work now.  Only had to sudo once.

that did it. thanks

---

### Post by otama71 on 2012-04-06
I changed the ownership of eclipse in the /usr/bin directory.

```
vettriano@ubuntu:/usr/bin$ ls -l | grep eclipse
-rwxr-xr-x 1 root   root       1160 Jan  2 03:19 eclipse
-rwxr-xr-x 1 root   root       2642 Feb  3 13:11 fetch-eclipse-source
-rwxr-xr-x 1 root   root       6885 Feb  3 13:11 jh_installeclipse
vettriano@ubuntu:/usr/bin$ sudo chown -vR vettriano:vettriano eclipse
changed ownership of `eclipse' from root:root to vettriano:vettriano
vettriano@ubuntu:/usr/bin$ ls -l | grep eclipse
-rwxr-xr-x 1 vettriano vettriano    1160 Jan  2 03:19 eclipse
-rwxr-xr-x 1 root      root         2642 Feb  3 13:11 fetch-eclipse-source
-rwxr-xr-x 1 root      root         6885 Feb  3 13:11 jh_installeclipse
vettriano@ubuntu:/usr/bin$ ./eclipse 

```

---


---
title: "UEC won't run images not provided in store"
date: 2010-10-05
forum: Server Platforms
---

### Post by tonymaro on 2010-10-05
First, my specs:

Maverick RC (both servers)
MANAGED-NOVLAN mode
CC + SC + Walrus server: 1 TB bukkit hard drive (after problem started just to see if the problem was related to the LVM), 500 GB root, 6 GB RAM, 8 core
NC: 500 GB HD, 24 GB RAM, 16 core

I have downloaded all images available in the "store" and they all work perfectly.

If I download a UEC image from [http://uec-images.ubuntu.com/releases/lucid/release/](http://uec-images.ubuntu.com/releases/lucid/release/) or if I try to roll my own from an ISO image, it uploads just fine to the server, but when I start an instance it sticks in "pending" and fails to decrypt and cache.

**Walrus error on CC:**
```
21:20:00 ERROR [WalrusImageManager:Bukkit.16] Tired of waiting to cache image: docstore/vmlinuz-2.6.32-25-server.manifest.xml giving up
21:20:00 DEBUG [ReplyQueue:Bukkit.16] :1286241600507:ReplyQueue:MSG_REPLY:String:NativeMethodAccessorImpl.invoke0.-2
21:20:00 ERROR [ReplyQueue:Bukkit.16] org.mule.api.service.ServiceException: Component that caused exception is: Bukkit. Message payload is of type: GetDecryptedImageType
org.mule.api.service.ServiceException: Component that caused exception is: Bukkit. Message payload is of type: GetDecryptedImageType
at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:214)
at org.mule.component.AbstractJavaComponent.invokeComponentInstance(AbstractJavaComponent.java:82)
at org.mule.component.AbstractJavaComponent.doOnCall(AbstractJavaComponent.java:73)
at org.mule.component.AbstractComponent.onCall(AbstractComponent.java:87)
at org.mule.model.seda.SedaService$ComponentStageWorker.run(SedaService.java:533)
at org.mule.work.WorkerContext.run(WorkerContext.java:310)
at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1061)
at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:575)
at java.lang.Thread.run(Thread.java:636)
Caused by: com.eucalyptus.util.EucalyptusCloudException: caching failure
at edu.ucsb.eucalyptus.cloud.ws.WalrusImageManager.getDecryptedImage(WalrusImageManager.java:1124)
at edu.ucsb.eucalyptus.cloud.ws.WalrusControl.GetDecryptedImage(WalrusControl.java:342)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:127)
at org.mule.model.resolvers.DefaultEntryPointResolverSet.invoke(DefaultEntryPointResolverSet.java:50)
at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:202)
... 8 more
```

Node controller:

```

[Mon Oct 4 21:04:16 2010][012751][EUCADEBUG ] doStartNetwork() invoked
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] StartNetwork(): SUCCESS return from vnetStartNetwork 0
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] StartNetwork(): done
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] doRunInstance() invoked (id=i-4DB7099B cores=2 disk=15 memory=1024)
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] image=emi-ACCB1009 at http://192.168.1.240:8773/services/Walrus/docstore/docstore.img.manifest...
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] krnel=eki-67951300 at http://192.168.1.240:8773/services/Walrus/docstore/vmlinuz-2.6.32-25-ser...
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] rmdsk=eri-A21B13ED at http://192.168.1.240:8773/services/Walrus/docstore/initrd.img-2.6.32-25-...
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] vlan=10 priMAC=D0:0D:4D:B7:09:9B privIp=172.19.1.4
[Mon Oct 4 21:04:16 2010][012751][EUCADEBUG ] state change for instance i-4DB7099B: Unknown -> Staging (Pending)
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] network started for instance i-4DB7099B
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] retrieving images for instance i-4DB7099B (disk limit=15360MB)...
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] waiting for disapperance of /var/lib/eucalyptus/instances//eucalyptus/cache/eki-67951300/kernel-staging...
[Mon Oct 4 21:04:16 2010][012751][EUCAINFO ] waiting for cached image to become ready...
....
[Mon Oct 4 21:20:06 2010][012751][EUCAFATAL ] Failed to prepare images for instance i-4DB7099B (error=1)
[Mon Oct 4 21:20:06 2010][012751][EUCADEBUG ] state change for instance i-4DB7099B: Staging -> Shutoff (Extant)
...
[Mon Oct 4 21:23:15 2010][012751][EUCAINFO ] forgetting about instance i-4DB7099B
```

On the node it creates a cache directory for the kernel, and places a zero byte "kernel.staging" file inside.  After it gives up it deletes the folder.

I know it's not a connectivity issue between the two because the "store" images cache properly to the NC.

Uploading of the image to the CC from the client seems to work fine. The destination bukkit directory contents are the same size as the compressed image uploaded using euca-upload-bundle for an image I made, and the same as the source when using euc-publish-tarball to upload the official Ubuntu UEC image I tried.

---

### Post by tonymaro on 2010-10-05
Out of frustration I formatted and reinstalled the cloud controller machine.

**Now it works.**

The only thing I've done different is to set up a user as another administrator instead of trying to login as admin each time.

---

### Post by wcorey on 2011-01-08
I, also, have this issue, be it a maverick image or a natty image. I do think reinstalling the cloud/cc/sc controller server image is very Microsoft Windows like... "did you reboot 3 times", "yes, I did just what you told me to do last time" Reference is to Web Dude vs Sales Guy YouTube skit. 

I wish someone had responded with what the issue was. If I happen across it I will post here as reinstall, while maybe the required solution, is not an adequate solution..least ways not for me, and I assume others.

Did you ever find out what there was about reinstalling that resolved the problem? In other words did reinstalling resolve the problem or did adding a new user and getting (presumably) new credentials resolve it or did it actually require both?

---

### Post by Sesshomurai on 2011-01-26
Hi,
  I have this problem on 10.10 64bit. I cannot reformat the machine since its my laptop.

FWIW, I not only can't run instances NOT in the store, I can't install images from the store.

Any tips?

thank you.

---

### Post by wcorey on 2011-02-05
> **Sesshomurai said:**
> Hi,
  I have this problem on 10.10 64bit. I cannot reformat the machine since its my laptop.

FWIW, I not only can't run instances NOT in the store, I can't install images from the store.

Any tips?

thank you.

No, reformatting is a red herring. The solution was to upload/run the images not from store as a non-admin user.

Tony, if you are happy with the answer and it solved the problem, would you mark this thread as solved? Thanks!

---


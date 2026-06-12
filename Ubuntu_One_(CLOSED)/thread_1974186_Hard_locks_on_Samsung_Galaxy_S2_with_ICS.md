---
title: "Hard locks on Samsung Galaxy S2 with ICS"
date: 2012-05-05
forum: Ubuntu One (CLOSED)
---

### Post by RichardUK on 2012-05-05
Since my S2 was upgraded to ICS Ubuntu one has died. It hard locks the phone on a regular basis fails to sync and file and if I do get to open a file it locks the phone so bad I have to reboot. Uninstalling Ubuntu one and all problems go away.

Known issue?

Get the following from the app.


E/AndroidRuntime(22501): FATAL EXCEPTION: AutoUploadThread
E/AndroidRuntime(22501): java.lang.IllegalArgumentException: Method takes folder paths only.
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.util.MediaImportUtils.isPhotoAutoUploadCandidate(MediaImportUtils.java:85)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.util.MediaImportUtils.saveWatchedFolder(MediaImportUtils.java:175)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.util.MediaImportUtils.importImageBucketsForUri(MediaImportUtils.java:141)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.util.MediaImportUtils.importImageBuckets(MediaImportUtils.java:70)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.service.AutoUploadService.rescanMedia(AutoUploadService.java:234)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.service.AutoUploadService.access$0(AutoUploadService.java:231)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.service.AutoUploadService$MediaObserver$1.run(AutoUploadService.java:208)
E/AndroidRuntime(22501): 	at com.ubuntuone.android.files.service.AutoUploadService$1.handleMessage(AutoUploadService.java:110)
E/AndroidRuntime(22501): 	at android.os.Handler.dispatchMessage(Handler.java:99)
E/AndroidRuntime(22501): 	at android.os.Looper.loop(Looper.java:137)
E/AndroidRuntime(22501): 	at android.os.HandlerThread.run(HandlerThread.java:60)
W/ActivityManager( 2006):   Force finishing activity r.intent.getComponent().flattenToShortString()

---

### Post by mkarnicki on 2012-05-07
Hi Richard!

I badly need a Samsung S II tester. It has some additional storage that seems to be the problem.

Could you please head here:
[https://bugs.launchpad.net/ubuntuone-android-files/+bug/993683](https://bugs.launchpad.net/ubuntuone-android-files/+bug/993683)
and try the apk from the first comment? If it still doesn't work, could you paste the logcat output, just like you have here?

THANKS!

---

### Post by RichardUK on 2012-05-07
Hi, done that for you, unfortunately didn't work. Left feedback on the bug report.

 I'm a software engineer and amongst many other projects at work I'm working on two Android apps so all set up for android dev, using Ubuntu of cause. So if there is any way I can help send me a private message so we can exchange email addresses. I have a few other Android systems at work I can test on for you.

---

### Post by mkarnicki on 2012-05-15
Thanks Richard! Sent you a PM.

---


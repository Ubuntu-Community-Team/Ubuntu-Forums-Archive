---
title: "Ninan problem on Ubuntu Server"
date: 2011-04-29
forum: Server Platforms
---

### Post by ransae on 2011-04-29
I've been using Ninan on a Centos server for some time without issues. Recently,  I've moved my server to Ubuntu, and haven't been able to get Ninan to  work.

It installs and starts ok.

I can log in using a browser. It uploads nzbfiles, then hangs.

In the "Detailed View" there's the list of files to be downloaded, the first is stuck at 0%, the rest are "waiting."

There is no activity shown in the "Connections" and "Processes" pages. 

It seems it can't access the network, although it does test the newsgroup URL ok in settings.

The log files shows the following when the program starts:

```
2011-04-27 10:23:28,301 INFO  backend.configuration.Config.initProperties - Initializing configuration properties
2011-04-27 10:23:28,529 INFO  backend.configuration.Config.load - Ninan properties has been loaded.
2011-04-27 10:23:28,588 DEBUG backend.db.AbstractDAO.<init> - Database type is HSQLDB - org.hsqldb.jdbcDriver
2011-04-27 10:23:28,603 INFO  backend.newsfile.ArticleCache.<clinit> - Max memory used by Ninan: 592 Mb.
2011-04-27 10:23:28,603 DEBUG backend.newsfile.ArticleCache.<clinit> - BUFSIZE: 262144 bytes.
2011-04-27 10:23:28,603 DEBUG backend.newsfile.ArticleCache.<init> - Article cache enabled
2011-04-27 10:23:28,769 DEBUG backend.newsserver.SpeedManager.<init> - MS_BETWEEN_FULLSPEED_SAMPLES: 1000 SAMPLE_DURATION_FULLSPEED: 30000
2011-04-27 10:23:28,769 DEBUG backend.newsserver.SpeedManager.<init> - MS_BETWEEN_THROTTLE_SAMPLES: 100 SAMPLE_DURATION_THROTTLE: 15000
2011-04-27 10:23:28,775 DEBUG backend.rmi.server.threading.RMIThreads.addListener - Addlistener: Thread[NinanRMIServer_1,5,main]
2011-04-27 10:23:29,007 DEBUG frontend.ApplicationEventReceiver.onApplicationEvent - Got ContextRefreshedEvent at 1303863808978
2011-04-27 10:23:29,433 DEBUG backend.VersionChecker$1.run - running version: 2.1.0
```I've tried both the free and Sun versions of Jave RE. and both Ninan V2.1.0 and V2.0.2. No difference with either. 

Are there any dependencies I don't know about? Does Ubuntu server restrict Java from accessing the outside world when run as an ordinary user?

Any assistance would be appreciated.

---


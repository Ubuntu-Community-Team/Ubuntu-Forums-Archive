---
title: "Limit Java RAM consumption?"
date: 2015-12-16
forum: Server Platforms
---

### Post by timonoj on 2015-12-16
Hi guys,

I have a small Banana Pi running several server tasks (Seafile and Crashplan backup, most importantly). This BananaPi already has 1GB of RAM, which isn't bad for an ARM all-in-one board, but Crashplan runs on Java, and I can see it's hammering the RAM really bad. Is there a way to constraint the maximum RAM consumption to either 512MB or 768MB? 

Thanks!

---

### Post by deepakdeshp on 2015-12-17
This may help
[http://askubuntu.com/questions/120765/memory-limiting-solutions-for-greedy-applications-that-can-crash-os](http://askubuntu.com/questions/120765/memory-limiting-solutions-for-greedy-applications-that-can-crash-os)

---

### Post by timonoj on 2015-12-18
Thanks! In the end I decided to give it a a 4GB swap file in the NAS, it accesses it through NFS. I know it's dirty/exposed, but neither the NAS nor the BPi are to be moved, they're pretty much together for most tasks anyway. 
Since using the Swap, the Banana Pi has been performing really well, no more freezes.

---

### Post by MAFoElffen on 2015-12-23
I run into this in Dev using Eclipse and using Apache Tomcat. To get a better understanding of how the Java Runtime uses memory, you might want to refer to these two articles:
    [Thanks for the Memory]("http://www.ibm.com/developerworks/java/library/j-nativememory-linux/")
    [Tomcat Wiki- FAQ/Memory]("https://wiki.apache.org/tomcat/FAQ/Memory")

To check on want to adjust:
```

C:\WINDOWS\system32>java -X
    -Xmixed           mixed mode execution (default)
    -Xint             interpreted mode execution only
    -Xbootclasspath:<directories and zip/jar files separated by ;>
                      set search path for bootstrap classes and resources
    -Xbootclasspath/a:<directories and zip/jar files separated by ;>
                      append to end of bootstrap class path
    -Xbootclasspath/p:<directories and zip/jar files separated by ;>
                      prepend in front of bootstrap class path
    -Xdiag            show additional diagnostic messages
    -Xnoclassgc       disable class garbage collection
    -Xincgc           enable incremental garbage collection
    -Xloggc:<file>    log GC status to a file with time stamps
    -Xbatch           disable background compilation
    -Xms<size>        set initial Java heap size
    -Xmx<size>        set maximum Java heap size
    -Xss<size>        set java thread stack size
    -Xprof            output cpu profiling data
    -Xfuture          enable strictest checks, anticipating future default
    -Xrs              reduce use of OS signals by Java/VM (see documentation)
    -Xcheck:jni       perform additional checks for JNI functions
    -Xshare:off       do not attempt to use shared class data
    -Xshare:auto      use shared class data if possible (default)
    -Xshare:on        require using shared class data, otherwise fail.
    -XshowSettings    show all settings and continue
    -XshowSettings:all
                      show all settings and continue
    -XshowSettings:vm show all vm related settings and continue
    -XshowSettings:properties
                      show all property settings and continue
    -XshowSettings:locale
                      show all locale related settings and continue


The -X options are non-standard and subject to change without notice.

```
Yes, this is in Win, but is the same in Linux... except use "-x" instead of "-X"... To understand what the options mean and what you are changing, refer to man java.

A summarized explanation is that the JRE (java runtime environment) runs with default settings for it's memory stack and heap. The first time I tried to start a big project in Eclipse and got an out-of-memory error on a dev machine with 32GB's of memory ... it was a mystery, until I learned what it actually meant.

You could set the environment temporarily from the commandline (would have to do manually each boot)... or those two apps I mention have config files which you set them from (otherwise, they take the same as startup arguments in their startup) ... or you could set the environment from a script...

I just thought you might want enough info to understand what you are doing, instead of a "just do this," without understanding what you did.

---


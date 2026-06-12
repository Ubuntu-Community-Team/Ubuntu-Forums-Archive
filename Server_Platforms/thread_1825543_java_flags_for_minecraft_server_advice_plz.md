---
title: "java flags for minecraft server? advice plz"
date: 2011-08-15
forum: Server Platforms
---

### Post by SlugSlug on 2011-08-15
A while ago a little game got the better of me, 
I've now running a minecraft server and forum and wondering if any java ppl here can help me get the best performance?

Specs
2.8 quad core
8GB ram

World is sat on a /dev/shm

flags am using to launch server
```

java -Xmx1536M -XX:ParallelGCThreads=4 -server -Xincgc -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+CMSIncrementalPacing -XX:+AggressiveOpts -XX:+CMSParallelRemarkEnabled -XX:+DisableExplicitGC -XX:MaxGCPauseMillis=500 -XX:SurvivorRatio=16 -XX:TargetSurvivorRatio=90 -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -Xnoclassgc -XX:UseSSE=3 -XX:PermSize=128m -XX:LargePageSizeInBytes=4m -jar craftbukkit-0.0.1-SNAPSHOT.jar nogui"
```Just wondering if it could be better?

---

### Post by SlugSlug on 2011-08-22
bump

---

### Post by shadowofblood on 2011-09-04
Those flags are terrible =O
They are conflicting with each other and paving the way for serious memory leaks.

The standard JVM optimization will work just fine.  The only flags I can recommend are:

-server -Xmx####M -Xms####M -XX:+DisableExplicitGC -XX:+AggressiveOpts

If you are going to specify a garbage collector, please specify only one.  The only exception being -XX:+UseConcMarkSweepGC -XX:+UseParNewGC for concurrent and young.  Those two can be used together.

Edit:  If you use a bukkit server, do NOT use -xnoclassgc.  This can cause serious memory leaks.

---

### Post by SlugSlug on 2011-09-04
> **shadowofblood said:**
> Those flags are terrible =O
They are conflicting with each other and paving the way for serious memory leaks.

The standard JVM optimization will work just fine.  The only flags I can recommend are:

-server -Xmx####M -Xms####M -XX:+DisableExplicitGC -XX:+AggressiveOpts

If you are going to specify a garbage collector, please specify only one.  The only exception being -XX:+UseConcMarkSweepGC -XX:+UseParNewGC for concurrent and young.  Those two can be used together.

Edit:  If you use a bukkit server, do NOT use -xnoclassgc.  This can cause serious memory leaks.


Thanks, for the ####  is 4096  OK for both (server has 8gig and want to give bukkit 4)

---


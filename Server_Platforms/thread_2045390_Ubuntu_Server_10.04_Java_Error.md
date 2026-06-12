---
title: "Ubuntu Server 10.04 Java Error"
date: 2012-08-21
forum: Server Platforms
---

### Post by xb2003 on 2012-08-21
This might be something that should go in a Java forum instead of Ubuntu, but im starting here because this site is really helpful.

First off, i know little about the commands and what now, but im trying to learn as much as possible.

What im going is making a server to run minecraft, which is a java intensive game. I installed Ubuntu 10.04 and then Java, and then the Minecraft_Server.jar file. For the first day or 2, i would run the server and it would start like up, and run great. But this evening i tried to start it, and it gives me a never ending error..

at ev.a(SourceFile:38)
at ev.b(SourceFile:48)

over and over and over again. I use CTRL+C to stop it, and this shows up.


Exception in thread "Thread-3" java.lang.NullPointerException
        at net.minecraft.server.MinecraftServer.a(SourceFile:238)
        at net.minecraft.server.MinecraftServer.j(SourceFile:262)
        at eo.run(SourceFile:527)

I cant find anything on the internet besides a forum post from 2005. Any help that i could get would be really greatly appreciated.

Thanks in advance,
xb2003

---

### Post by LHammonds on 2012-08-21
Is that an unmodded CraftBukkit server?  Or does it have plugins?  What version are you running?  CraftBukkit 1.3.2-R2.0? or a beta build?  Plugins?  Their version numbers?

You need to know if the error is in a particular plugin or if it is a base craftbukkit problem.

I'd recommend setting up an Ubuntu Server 12.04 server with Java 1.7.0_06

Some plugins, such as "auto-shutdown" will not work with some versions of Java such as 1.6.0_31 but will with the 1.7 branch.

If you cannot determine if it is a plugin, simply rename the plugin folder and start the server.  If the errors go away, it was a plugin causing the issue.  Then start to introduce the plugins until you find the one causing the error.

Or you can just try a different version of Java.

It all depends on what you have installed and the versions of what you have installed.

**EDIT: **Hopefully you will get an idea on how to track down the problem (cause I'm going on vacation for the rest of the week starting......NOW)

LHammonds

---


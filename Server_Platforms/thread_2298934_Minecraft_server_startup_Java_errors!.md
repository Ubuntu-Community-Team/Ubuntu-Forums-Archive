---
title: "Minecraft server startup Java errors!"
date: 2015-10-14
forum: Server Platforms
---

### Post by Dragonbite on 2015-10-14
I have a couple of Ubuntu Servers ver. 14.04 running Minecraft Server and one of them is giving me some issue and won't start.  I access them via SSH and no desktop environment is installed on them.

I am running this on openJDK, which it has always run on and worked fine.  I haven't changed anything though some work with command blocks has crashed the server a few times PLUS the log files filled up the / partition.  I have since cleaned up the hard drive and moved the Minecraft server to where I had originally placed it (my son did the whole install and put Minecraft server in his /home directory.)

**Java version**
```
$ java -version
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.14.04.1)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)
```
**Ubuntu version**
```
 $ uname -a
Linux CrotherKingdoms 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 
```
I set up the server with a symbolic link to the actual server .jar file so that when I upgrade the server I just have to repoint this to he new .jar file.  When this error started showing up I downloaded the latest server version (1.8.8) and re-pointed the link to it, to see if that would fix anything but there was no change.  ```
$ ls -l
total 17732
-rw-r--r-- 1 root root       2 Oct 14 19:38 banned-ips.json
-rw-r--r-- 1 root root     227 Oct 14 19:38 banned-players.json
drwxr-xr-x 2 root root    4096 Oct 14 19:13 crash-reports
-rw-r--r-- 1 root root     180 Oct 14 19:38 eula.txt
drwxr-xr-x 2 root root    4096 Oct 14 20:12 logs
-rw-r--r-- 1 root root 9780646 Oct 14 19:38 minecraft_server.1.8.7.jar
-rw-r--r-- 1 root root 8322852 Jul 27 07:11 minecraft_server.1.8.8.jar
lrwxrwxrwx 1 root root      28 Oct 14 19:55 minecraft_server.jar -> ./minecraft_server.1.8.8.jar
-rw-r--r-- 1 root root     960 Oct 14 19:38 ops.json
-rw-r--r-- 1 root root     829 Oct 14 19:56 server.properties
-rwxr-xr-x 1 root root     179 Oct 14 19:38 start
-rw-r--r-- 1 root root       0 Oct 14 19:38 usercache.json
-rw-r--r-- 1 root root       2 Oct 14 19:38 whitelist.json
drwxr-xr-x 8 root root    4096 Oct 14 19:38 world 
```
**Start Script**
I also created a "start" file which runs the command to start the server so that I don't have to remember all of my settings.  ```
#!/bin/sh

# ORIGINAL CODE
#java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui

# PROVIDE MORE MEMORY - dk 9.25.15
java -Xmx1536M -Xms1536M -jar minecraft_server.jar nogui 
```
**Error Message**
And finally, the message I get when I try to run it (from the start script or typing in the command directly) ```
$ sudo ./start 
[20:32:26] [main/FATAL]: Failed to start the minecraft server
java.lang.NullPointerException
        at com.google.common.base.Preconditions.checkNotNull(Preconditions.java:213) ~[minecraft_server.1.8.8.jar:?]
        at com.google.common.collect.Lists$ReverseList.<init>(Lists.java:767) ~[minecraft_server.1.8.8.jar:?]
        at com.google.common.collect.Lists.reverse(Lists.java:759) ~[minecraft_server.1.8.8.jar:?]
        at lt.b(SourceFile:156) ~[minecraft_server.1.8.8.jar:?]
        at lt.<init>(SourceFile:43) ~[minecraft_server.1.8.8.jar:?]
        at net.minecraft.server.MinecraftServer.<init>(SourceFile:168) ~[minecraft_server.1.8.8.jar:?]
        at ko.<init>(SourceFile:53) ~[minecraft_server.1.8.8.jar:?]
        at net.minecraft.server.MinecraftServer.main(SourceFile:689) [minecraft_server.1.8.8.jar:?] 
```

Any help is greatly appreciated.  The servers are shared with my son's friends and I play on it too!

---

### Post by efflandt on 2015-10-16
Not sure if it would have something to do with running java or minecraft as "root" (which may be considered hazardous) and/or using the symlink. When I download a different minecraft-server.x.y.z.jar I cp that to minecraft-server.jar in the server directory.

And it works fine for me (as a normal user) in 64-bit Ubuntu 14.04 (I just briefly connected to it with client on same PC, then I disconnected):```
efflandt@XPS-8100-1404:~$ java -version
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.14.04.1)
OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)

efflandt@XPS-8100-1404:~$ cd Minecraft-server
efflandt@XPS-8100-1404:~/Minecraft-server$ java -Xmx3G -Xms3G -jar minecraft_server.jar nogui
[07:38:39] [Server thread/INFO]: Starting minecraft server version 1.8.8
[07:38:39] [Server thread/INFO]: Loading properties
[07:38:39] [Server thread/INFO]: Default game type: SURVIVAL
[07:38:39] [Server thread/INFO]: Generating keypair
[07:38:39] [Server thread/INFO]: Starting Minecraft server on *:25565
[07:38:39] [Server thread/INFO]: Using epoll channel type
[07:38:39] [Server thread/INFO]: Preparing level "1.4"
[07:38:39] [Server thread/INFO]: Preparing start region for level 0
[07:38:40] [Server thread/INFO]: Preparing spawn area: 97%
[07:38:40] [Server thread/INFO]: Done (1.144s)! For help, type "help" or "?"
[07:42:05] [User Authenticator #1/INFO]: UUID of player efflandt is 96ecc569-0847-40a5-a690-8678f879ef42
[07:42:05] [Server thread/INFO]: efflandt[/127.0.0.1:44198] logged in with entity id 161 at (1352.2304563546015, 30.0, -268.69999998807907)
[07:42:05] [Server thread/INFO]: efflandt joined the game
[07:42:14] [Server thread/INFO]: efflandt lost connection: TextComponent{text='Disconnected', siblings=[], style=Style{hasParent=false, color=null, bold=null, italic=null, underlined=null, obfuscated=null, clickEvent=null, hoverEvent=null, insertion=null}}
[07:42:14] [Server thread/INFO]: efflandt left the game
stop
[07:54:00] [Server thread/INFO]: Stopping the server
[07:54:00] [Server thread/INFO]: Stopping server
[07:54:00] [Server thread/INFO]: Saving players
[07:54:00] [Server thread/INFO]: Saving worlds
[07:54:00] [Server thread/INFO]: Saving chunks for level '1.4'/Overworld
[07:54:00] [Server thread/INFO]: Saving chunks for level '1.4'/Nether
[07:54:00] [Server thread/INFO]: Saving chunks for level '1.4'/The End
[07:54:00] [Server Shutdown Thread/INFO]: Stopping server
[07:54:00] [Server Shutdown Thread/INFO]: Saving players
```

---


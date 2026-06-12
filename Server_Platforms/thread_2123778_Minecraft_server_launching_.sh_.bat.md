---
title: "Minecraft server launching .sh .bat"
date: 2013-03-08
forum: Server Platforms
---

### Post by Eyeball114 on 2013-03-08
I was using Ubuntu desktop on my server, now I am using xubuntu. Now with Xubuntu I am unable to launch the servers with the .bat. Where and how should I be launching the .sh? I tried open with terminal but that did nothing at all. I had to move the .sh to home to get the " allow to launch as a program" check to stay. Double click. Nothing. These are minecraft servers so I need them to open in a terminal. New at this so any help is appreciated by me and my community who is waiting to get back on the servers :P

---

### Post by drmrgd on 2013-03-09
First, I think the .bat files are batch files specific to Windows.  So, they likely won't help you here.  The .sh or shell scripts would be what you're after.  In order to run them from the terminal, you need to be sure that they are set as executable.  A quick way would be:

```
 chmod +x <script.sh> 
```

Once the script is made executable, you can run it by explicitly defining the interpreter (not sure what shell it's written for without seeing it) with either:

```
 bash <script.sh> 
``` 
or
```
 sh <script.sh> 
```

If the script was written well, it should contain a shebang line as the first line in the script.  It would look something like:

```
#!/bin/bash
```

in that case, the correct interpreter has already been defined, and you can run the script like this:

```
./<script.sh>
```

If you've done all this already and still are not getting results, it might be useful for us to see the script to know why it might not be working.

---

### Post by Eyeball114 on 2013-03-09
Thanks Ill check all this out, I only brought up the batch file because when I was running Ubuntu desktop it was launching from them. Not sure why or how lol. Hopefully this will work. If linux detects a .bat does it make a script in the folder? I never had the scripts in the folder until after I transferred from windows to ubuntu. The scripts that were created seem to just be the same content as the .bat. Hopefully this will fix it. If not Ill post up my scripts.

Thnaks.


EDIT:
 java -Xms4g -Xmx4G -jar mindcrack.jar


Thats what was in the script, and I'm pretty sure that is, in so many ways, wrong. lol.

---

### Post by LHammonds on 2013-03-12
There are many ways to do what you are needing.  I have no idea what "mindcrack.jar" is but typically, it is "craftbukkit.jar" that you run for a server.

I usually setup my CraftBukkit servers to start with on a Windows PC so I use a .bat batch file to startup the server.

Once I'm happy with the server, I then transfer the files to an Ubuntu Server and use .sh scripts to start and manage the server.

Since it needs to run in a terminal so we can type console commands such as "stop" in order to manage it, I use a program called "screen" in my scripts.  This allows me to start the server from crontab schedule without ever having to login and I can have other scripts schedule to run that access the console and send it commands such as saving the world to disk, sending messages to users, etc.

I have a rather detailed guide on how I did it in [this post](http://forums.bukkit.org/threads/how-to-setup-a-trickd-out-craftbukkit-server-1-3-1-r2-0.100406/).

The command I use to start it is like this:

```

screen -d -m -S "CraftBukkit" -t "CraftBukkit" java -d64 -Xincgc -Xmx3072 -jar /opt/craftbukkit/craftbukkit.jar nogui

```

LHammonds

---


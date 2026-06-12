---
title: "Auto-restarting a crashing application"
date: 2011-11-19
forum: Tutorials
---

### Post by kenji_03 on 2011-11-19
Be it Firefox, a P2P client, a Java program, or whatever!  Ubuntu makes it easy, but there's still some light editing to do (sorry, I don't know how to make these terminal commands yet).

For an example of how to make a Minecraft server (java app) auto-restart after crashing, see [this]("http://ubuntuforums.org/showthread.php?p=11471319#post11471319") post.

For everything else, see below:

Code via PID (Not all applications use a constant PID)
> [LIST=1]
[*]Run the application
[*]Find the "ID" or **[COLOR="DarkOrchid"]PID[/COLOR]** (Process ID) in the System Monitor program (start bar > Systems > Administration) 
[*]Create a document with the following code (anywhere on your machien), _be sure to change the [COLOR="purple"]four purple pound symbols[/COLOR] (#) to the process ID number you found._
```
#!/bin/bash

while true
do
if [ ! `PID [COLOR="purple"]**####**[/COLOR]` ] ; then
/usr/bin/autorestart1.sh
fi
sleep 30
done
```
[*]Create another document in the install folder of the application you wish to run.  Title it "autorestart1.sh" with the following code
```
**[COLOR="Red"]cd *(Path to install folder)*[/COLOR]**
*[COLOR="DarkOrange"]Application File Name[/COLOR]*
```
[*]**<Important>** You must change the "change directory" (**[COLOR="Red"]cd[/COLOR]**) portion to direct terminal to your application's install folder
[*]**<Important>** You also must change the orange "[COLOR="DarkOrange"]Application File Name[/COLOR]" to the actual name of the application you wish to run.
[*]_Make a link_ to your "Start server.sh"
[*]Copy it
[*]Go to your /usr/bin as the root user (you can use Terminal's "sudo nautilus" browser to do this with a GUI).
[*]Paste the link and rename it "autorestart1.sh" (case sensitive)
[*]You're done!
[/LIST]




Code via Process Name
> [LIST=1]
[*]Run the application
[*]Find the "Process Name" in the System Monitor program (start bar > Systems > Administration) 
[*]Create a document with the following code (anywhere on your machien), _be sure to change the purple "**[COLOR="Purple"]Process Name[/COLOR]**" to the process name you found._
```
#!/bin/bash

while true
do
if [ ! `pgrep **[COLOR="Purple"]Process Name[/COLOR]**` ] ; then
/usr/bin/autorestart1.sh
fi
sleep 30
done
```
[*]Create another document in the install folder of the application you wish to run.  Title it "autorestart1.sh" with the following code
```
**[COLOR="Red"]cd *(Path to install folder)*[/COLOR]**
*[COLOR="DarkOrange"]Application File Name[/COLOR]*
```
[*]**<Important>** You must change the "change directory" (**[COLOR="Red"]cd[/COLOR]**) portion to direct terminal to your application's install folder
[*]**<Important>** You also must change the orange "[COLOR="DarkOrange"]Application File Name[/COLOR]" to the actual name of the application you wish to run.
[*]_Make a link_ to your "Start server.sh"
[*]Copy it
[*]Go to your /usr/bin as the root user (you can use Terminal's "sudo nautilus" browser to do this with a GUI).
[*]Paste the link and rename it "autorestart1.sh" (case sensitive)
[*]You're done!
[/LIST]

A fair warning is that the only two ways to terminate the auto-restarting of the application is through killing the autorestart sh process or restarting your machine.

---


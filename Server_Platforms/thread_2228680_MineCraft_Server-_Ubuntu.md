---
title: "MineCraft Server- Ubuntu"
date: 2014-06-08
forum: Server Platforms
---

### Post by tom105 on 2014-06-08
[COLOR=#000000][FONT=Verdana][FONT=Verdana]i have a couple questions regarding hosting a mine craft server on ubuntu:[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]first off i am still new to ubuntu and am using this as a way to become more familiar with it.[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]current system specs:[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]dell 690 precision  work station,[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]2x Intel Xeon 5240 3.33[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]ram 4 gig ram 667Mhz, [/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]i am planing to upgrade to 16 gigs of ram after i get everything setup[/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][FONT=Verdana]Wakeonlan implementation:[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]I want to be able have the computer go in to a standby/ hibernation if no on is on the server for a prolonged time just a time out and when someone tries to access the server. im trying to keep it completely server side, where when someone checks to see if the server is active it takes the computer out of standby. I am pretty sure this can be done ill be doing more research into it. I am just wondering if anyone has any idea and links i can look at. [/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana][FONT=Verdana]next is im trying to run multiple servers on my machine. i am hoping to run a vanilla server, pixel mon and a forge server(with multiple mods). my issue is when i install a new server, i try to put it in its own folder but it seems to reference the home (in Ubuntu) folder for all the server files (properties, world folders and mods). so all the servers try to use the same files and folders and it causes issues. 

[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=Verdana]thats it for now, if you have any idea to help me let me know[/FONT][/FONT][/COLOR][COLOR=#282828][FONT=Verdana] [/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2014-06-08
> [COLOR=#000000][FONT=Verdana]next is im trying to run multiple servers on my machine. i am hoping to run a vanilla server, pixel mon and a forge server(with multiple mods). my issue is when i install a new server, i try to put it in its own folder but it seems to reference the home (in Ubuntu) folder for all the server files (properties, world folders and mods). so all the servers try to use the same files and folders and it causes issues. [/FONT][/COLOR]

Virtualize the servers separately. [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) and manage with the virt-manager package remotely. I find it easier to manage individual systems with a set purpose instead of multi-purpose single systems, for servers anyhow. Still working on getting it to run in a ramdisk : /

> [COLOR=#000000][COLOR=#000000][FONT=Verdana]Wakeonlan implementation:[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Verdana]I want to be able have the computer go in to a standby/ hibernation if no on is on the server for a prolonged time just a time out and when someone tries to access the server. im trying to keep it completely server side, where when someone checks to see if the server is active it takes the computer out of standby. I am pretty sure this can be done ill be doing more research into it. I am just wondering if anyone has any idea and links i can look at. [/FONT][/COLOR][/COLOR]

This is likely possible. But it won't have the effect you are looking for. Assuming you set it to be triggered by someone trying to log into a Minecraft server, they would try... and fail. They would have to know to try again in 30 seconds to a minute or two. If power usage is a concern you can cut a significant amount of that with either SSD's or with a program on the server called hdparm and set the spinner HDDs to spin down to a stop if not accessed after.... say 10 minutes or something. I'm kind of curious why would want to do this though, it causes unneeded issues. There is a reason servers are generally designed for running 24/7. Combined with virtualizing the servers I'm not entirely sure how the virtual machines would handle being paused so often for a suspend operation.

---


---
title: "Server Falls Asleep, how to stop it"
date: 2012-01-04
forum: Server Platforms
---

### Post by LERecords on 2012-01-04
Setup:
Whats installed
  Ubuntu server 11.04
  Samba
  SSH
 
I use this as a no security file share server for my office. the problem im having is that after say 5-10 mins, the server does into like a sleep mode where i cant ssh into it untill i click (on a windows pc) the network share icon (that links to the samba share on the ubuntu server). It wont open on the first few clicks, but then everything starts working perfectly again. but then a few mins go by and it falls back "asleep". oh and i only have one account and allow as guests to connect
 
I have no GUI Loaded and do not want to load one, so any answers must be cmd line based. 
 
I have tried to edit the bios for power save settings, but i can only change from s1 or s3. There is nothing in the bios about times to spin stuff down or anything like that. It is an old dell and I havent tried to pull the battery to unlock the bios.
 
I have also tried to get it to work right by adding acpi=off in the GRUB_CMDLINE_LINUX_DEFAULT line.. that didnt work.. so i tired acpi=force and it didnt work either.
 
I really would like it if this thing never sleeps.
 
I'm still a newbie when it comes to ubuntu, so please be gentle.. any help is appriciated.. thanks :D

---

### Post by LERecords on 2012-01-04
I've thought about putting in a cronjob to keep the server from falling asleep. Would this be a good idea or just a waste of resources???
 
anyone??

---

### Post by LERecords on 2012-01-04
nothing from anyone??
I tried this. I had to create teh X11.conf so i may need to add in somewhere to tell ubuntu to run it.. but i dont know
Create xorg.conf file
sudo vi /etc/X11/xorg.conf
And pasted these lines:
Section "ServerFlags"Option "BlankTime" "0"Option "StandbyTime" "0"Option "SuspendTime" "0"
Option "OffTime" "0"
Option "DontZap" "false"
EndSectionRebooted.. still not working correctly

---

### Post by egpetrich on 2012-01-04
The x11.conf file isn't likely to do anything unless you have X Windows installed. You didn't have that on your list, so I'm assuming it isn't there.

Check the log file /var/log/messages. If the kernel is aware of the suspension, I'd expect a message like:

```
ACPI: Preparing to enter system sleep state...
```

At the moment, I'm not sure what additional information is in this log. I just think it's a good starting point.

Most of the threads I've seen here on suspend/resume deal with how to get your system to suspend, not how to keep it from suspending....

---

### Post by LERecords on 2012-01-05
I looked into the kern.log and did not see anything like that message.. I am almost wondering if the wired network is dropping out for some reason but im not sure.. still looking for any help with this..

---

### Post by LERecords on 2012-01-05
so right after i start up the server and try to log in from windows xp, it works fine.. after about 10 mins i try to open the share folder up (on windows xp) and it tells me this: the network name can't be found... if i click on it  few times, it will load up the sahre folder. 
 
this is leading me to think that there is an issue with either samba or the ethernet connection... anybody have any ideas???

---

### Post by LERecords on 2012-01-05
posted too soon... it is still looking like (from the windows xp computer) that it disconects from the network.. but when i click on the icon to open the share, it will pop up after a few click.. im thinking still that this is a samba issue.. i have just "samba" installed.. should i use "samba4"??? any help or any thoughts???

---

### Post by egpetrich on 2012-01-05
I'm not clear what you mean when you say you can "log in from Windows XP". From the rest of your post, I infer that you can connect to the Samba share.

Have you tried logging in to your Linux machine using SSH from Windows? (If you haven't installed the PuTTY SSH client on your Windows machine, I highly recommend that you do so.)

If you can log in using SSH, then your problem is much more likely to be with Samba.

---

### Post by LERecords on 2012-01-05
I can connect to the server via winxp file explorer (i added an icon to my win xp desktop that when clicked on, opens a window and connect to the share)
i can connect via ssh..

Important: i set up samba with guest access as to not have to have user accounts. Its ok that everyone connects as a guest as it is more of a share library where everyone can add and delete file.

Steps
I start the server, i click on the icon or connect with ssh and it works fine.. let everything sit for say 10 mins. go back and click on the icon and it says that "the network name can't be found".. but if i click a few more times (and get the same error message) the share eventually pops up and works fine.. then it happens all over again.. I feel that somehow either samba or the server is falling "asleep"... 

i thought there might be a connection drop but i would never be able to reach the server again without a reboot and thats not the case as it just takes a minute for the server to "wake up" and it works fine.. 

any more help would be really appreciated.. I want to just get this thing working for work so we can all use it with no issues...

---

### Post by LERecords on 2012-01-06
bump...

---

### Post by LERecords on 2012-01-06
So, after about 2 weeks of pulling my hair out not understanding why this server was not working properly, I have figured it out.
 
In our office, we had a co-workers printer trying to use the same ip address as the share server.. this is what was causeing the share to not look visible on the net. There was no reason of why this printer was trying to access the network (wirelessly) so i turned the wireless off on the printer and now the share works perfectly.. someday i'll have to asign an ip address to it permently, but this offices network is really screwy.. thankfully its up to me to fix it and then it will work alot smoother..  Thanks for all the help here!!

---

### Post by spacecheck on 2012-01-06
Glad you were able to discover the solution!

Have fun!

---


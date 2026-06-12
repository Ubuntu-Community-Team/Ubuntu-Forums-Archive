---
title: "System Admin Skills"
date: 2019-02-24
forum: Server Platforms
---

### Post by bensontan on 2019-02-24
Hi Everyone, 

Can you please help me out for the following since I am new to Ubuntu from Singapore. 

I have successfully installed Ubuntu Server 18.04 on a Hyper-V system and it is running fine based on the documentation I went through but now, I am stuck since I am a Windows user I want to know the following commands how you check the system before it went on production so I hope through this forum I can learn something from the experts. 

From Windows Server, you can check the following through GUI but not in Ubuntu Server 18.04 because everything are in command line. 

1. How do I know all the drivers are installed in the system? (from Windows, you click on "Device Manager" and know which drivers are missing) What is the command line to check? 

2. How to check the error log file using command line? 

3. What is the command line to upgrade old version to latest version? 

4. In Windows, there is "Task Manager". What is in Ubuntu Server and what is the commands to have "Task Manager" in Ubuntu Server? 

Best Regards,
Benson Tan

---

### Post by oldrocker99 on 2019-02-24
1) The drivers are almost certainly already in the kernel and working.
2) [https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)
3) ```
sudo apt update
sudo apt upgrade
```
4) Lots of ways to monitor the system:[http://www.linuxandubuntu.com/home/10-best-linux-task-managers](http://www.linuxandubuntu.com/home/10-best-linux-task-managers)

Good luck!

---

### Post by richard378 on 2019-02-24
To see all processes that are running type top on the command line press q to quit.
To see the boot logs journalctl -b and other logs use the journalctl command on the command line

---

### Post by richard378 on 2019-02-24
sudo apt update && sudo apt dist-upgrade 
To upgrade the system to the next version type the above in the command line.

---

### Post by richard378 on 2019-02-24
To see the devices on your computer and the drivers loaded for each device type the following
lspci -v | less

---

### Post by him610 on 2019-02-24
You can also get some help in available books, for instance, "The Linux Command Line" by William Schotts. A link to a free downloadable pdf version can be found here, [http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php")

Ubuntu Documentation can be found at [https://help.ubuntu.com/]("https://help.ubuntu.com/")

Good luck, and have fun.

---

### Post by richard378 on 2019-02-24
If you want to learn linux I suggest if you have access take the Intoduction to LInux course at [https://www.edx.org](https://www.edx.org)  It is the official way to start learning linux by the Linux foundation.  I don't know if you have access in Singapore.   I am currently in that course as I am still a newbie.

---

### Post by mastablasta on 2019-02-25
> **richard378 said:**
> sudo apt update && sudo apt dist-upgrade 
To upgrade the system to the next version type the above in the command line.


that will update the system. to upgrade to latest version you need to do:

[COLOR=#333333][FONT=&quot]To upgrade on a server system (this is from 18.04 to 18.10 which is not an LTS):[/FONT][/COLOR]

[LIST]
[*]Install the update-manager-core package if it is not already installed.

[*]Make sure the Prompt line in /etc/update-manager/release-upgrades is set to normal.

[*]Launch the upgrade tool with the command sudo do-release-upgrade.

[*]Follow the on-screen instructions.
[/LIST]

---

### Post by slickymaster on 2019-02-25
Thread moved to **Server Platforms** for a better fit

---

### Post by mastablasta on 2019-02-25
> **bensontan said:**
> 
From Windows Server, you can check the following through GUI but not in Ubuntu Server 18.04 because everything are in command line. 


not quite true. linux is modular so unlike windows you can add or take away the desktop or GUI. there are a couple server GUIs out there that offer web administration.

i use Ajenti for the home data server, but Zentyal is a small business server GUI. there are of course even more available, some have too many features, some maybe not enough. 

on server the desktop interface is of course not necessary (and offer another potential attack vector), but can easily be added. the choice here is quite big. from full desktop environments (Gnome, KDE, Cinnamon, Mate, XFCE...) to various windows managers (i think over 20 of them) that offer classic windows like interface (e.g. IceWM, openbox...) or tiled interface (i3, dwm, wmii...).

---

### Post by bensontan on 2019-02-25
Thank you to all who leave their comments & advise in this thread. I appreciate it very much. I will close this thread for the meantime.

---


---
title: "Problem with rc.local after bad manipulations"
date: 2011-10-15
forum: Server Platforms
---

### Post by Sudoist on 2011-10-15
Good evening,

I just installed ubuntu server and I like it! However since I'm not very used to linux I'm quite lost. I have a problem, I was using rc.local to start a program when booting up, but I messed around with visudo and some sudo command and now my program doesn't start on boot up anymore. I was trying to remove the need of sudo since i wanted to use WinScp to transfer some files to my server and the access was denied... I found out how to bypass the transfer denial, altough I think I altered something.


[B]Here is the recap of what I did

I used this command : sudo passwd -l root
and I modified ALL=(ALL) ALL to ALL=(ALL) NOPASSWD: ALL

exemple :
 # User privilege specification
root %admin ALL=(ALL) NOPASSWD: ALL[/B]

_[SIZE="3"]This what my visudo looks like now[/SIZE]_

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

_[SIZE="3"]rc.local content[/SIZE]_

cd /opt/minecraft
sudo mono /opt/minecraft/McMyAdmin.exe


Just a little recap of my problem,the rc.local was working fine until I played in visudo and sudo things... now it doesn`t work anymore.

Thank you very much!

---

### Post by Sudoist on 2011-10-15
anyone can help me, I didn't find any solution yet..

---

### Post by Sudoist on 2011-11-04
Please?

---

### Post by vasile002 on 2011-11-05
try changing the command from rc.local to:
cd /opt/minecraft
sudo -u mono /opt/minecraft/McMyAdmin.exe

---

### Post by ian dobson on 2011-11-05
Hi,

Don't forget to include exit 0 at the end of the script.

Regards
Ian Dobson

---


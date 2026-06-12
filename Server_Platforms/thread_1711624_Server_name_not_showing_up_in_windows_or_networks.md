---
title: "Server name not showing up in windows or networks"
date: 2011-03-21
forum: Server Platforms
---

### Post by n4pgw on 2011-03-21
My server name, salamander, is not showing up in windows networking or in the networking items on linux computers.  I have checked, double checked and tried several samba settings to see if I can make it work, but to no avail. Its shares can be accessed by any computer by going directly to 10.10.1.101, salamander's fixed IP. 

My workstation, bear, shows up.  I edited hosts to read: "10.10.1.101  salamander"
Any machine can access the share on salamander using the ip address, but not even Bear can connect directly with the computer name. 

When I go to networks in Salamander, all it views is itself and a windows network.  Inside the windows network is only salamander. 

Bear shows up in the list of servers, and also has samba running.  Eagle and Bearcub are also ubuntu without samba and do not show up in the list either.  Understandably so.

Here is my smb.conf:

```
[global]
    workgroup = WILDLIFE
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[childmovies]
    comment = Movies for babies through early school years
    path = /media/movies/allmovies/youth/children
    guest ok = Yes

```**Edited:** in smb.conf.master, I have included the line "netbios name = salamander" but it does not show up in this version with all the comments removed.  (I use testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf)

---

### Post by garfonzo on 2011-03-21
Are all computers part of the same workgroup? One of the first few lines of smb.conf is ```
workgroup = WORKGROUP
```
(That is the default). I would check what workgroup all the windows machines run under and then set salamander to be on the same.

---

### Post by n4pgw on 2011-03-21
> **garfonzo said:**
> Are all computers part of the same workgroup? One of the first few lines of smb.conf is [CODE]WORKGROUP = WORKGROUP[\CODE]
(That is the default). I would check what workgroup all the windows machines run under and then set salamander to be on the same.

Yes, they are all in WILDLIFE.  Even though salamander is in wildlife, it only shows itself, but not the other computers.  Other computers in wildlife, including this one, Bear, sees all other wildlife computers.  The ubuntu computers that do not have samba installed are not showing up in wildlife, but they show all wildlife computers in Places|Network.

---

### Post by oldschoolgentoo on 2011-03-21
What is the OS of your systems on your network?  XP  Windows Vista?  Windows 7?


Is your Salamander, workstation the ¨master¨?   

I assume ¨Bear" sees the other  windows systems and not your Nix box.

[http://www.howtonetworking.com/Windows/computerbrowser.htm](http://www.howtonetworking.com/Windows/computerbrowser.htm)

this will help if all your windows  systems are trying to be master in your network.   they are set to browse by default.

backup your smb.cfg file.  start from scratch  with a clean copy.   make sure you have a note book and write in the note book what you change or insert.  It will help you when you are troubleshooting.

also  smb4k is a good  Network browser from your linux system ....


try a clean  smb.cfg  file first....

---

### Post by n4pgw on 2011-03-21
> **oldschoolgentoo said:**
> What is the OS of your systems on your network?  XP  Windows Vista?  Windows 7?
Beth_PC - WV
Cat - W7
Kitten - W7
Bear - U-10.10
Bearcub - U-10.04
Eagle - U - 10.04
Salamander - U-10.10 - Server + ubuntu_desktop

> 
Is your Salamander, workstation the ¨master¨?   
I don't know.  It only sees itself in the Networks and under Windows Network
> 

I assume ¨Bear" sees the other  windows systems and not your Nix box.
Yes, it sees the same thing every other computer sees (that sees the network).
> 

[http://www.howtonetworking.com/Windows/computerbrowser.htm](http://www.howtonetworking.com/Windows/computerbrowser.htm)

this will help if all your windows  systems are trying to be master in your network.   they are set to browse by default.
I followed the link and tried to follow the instructions.  Nothing worked, so something must be over my head there.  

I did see another link where the commenter said he used nbtstat to see the master browser.  I tried it on all the listed computers and found that only Beth-PC has --__MSBROWSE__-<01> GROUP Registered

It is the only computer in 'WORKGROUP' and ..... it belongs to my mother-in-law who doesn't like the idea of anyone tinkering with her computer... 

nbtstat -a bear brings up the following:
BEAR  <00>  UNIQUE  Registered
BEAR  <03>  UNIQUE  Registered
BEAR  <20>  UNIQUE  Registered
WILDLIFE  <00>  GROUP  Registered
__SAMBA__  <00>  GROUP  Registered
__SAMBA__  <20>  GROUP  Registered

nbtstat -a salamander brings up "Host not found" for both the wired and wireless. (server is wired.)

For each computer found, it displays the mac address.

> 
backup your smb.cfg file.  start from scratch  with a clean copy.   make sure you have a note book and write in the note book what you change or insert.  It will help you when you are troubleshooting.
I assume you mean /etc/samba/smb.conf.  I did that.  I commented out all the original content so I have it for reference.  Then I started from scratch at the top and added comments about what I did and what I expected.  If I delete a section, I comment it out and mark why.  So, I guess I have that notebook there.  
> 
also  smb4k is a good  Network browser from your linux system ....
It was already installed on Bear.  I looked at the configuration and checked everything that looked like it would feed me more information, but I don't understand most of what it was asking for. 

I think it says that Bear is the master browser.....  

Ok, when I point the finger at any computer, it says the master browser is Bear.  (Whew!  I am glad it wasn't Beth :)
> 
try a clean  smb.cfg  file first....I think I did that.

So, now how do I change the master browser to the server?

PS Thanks for the information.

---

### Post by ArtMitchell on 2013-01-13
This may not be relevant to your situation but when I had this problem I traced it to the Ubuntu machine name.

The name was either too long or had incompatible charaters in it. When shortened and simplified the system worked and the Linux machine appeared in the windows 7 network pane.

Regards,
Arthur

---

### Post by volkswagner on 2013-01-14
You can add your netbios name to smb.conf to help advertise itself by name.

```
netbios name = salamander
```


Do you have specific reasons for choosing:

```
security = SHARE
```

Typically security = user is easier to manage.  See the various types [here]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559439").

---


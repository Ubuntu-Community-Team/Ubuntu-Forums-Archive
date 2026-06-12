---
title: "Samba is doing strage things"
date: 2020-08-31
forum: Ubuntu/Debian BASED
---

### Post by svenmatti on 2020-08-31
Hi there,

I'm just installing linux lite on a computer. It's supposed to be kind of a file server for the little workgroup (so far working under WinXP). There are 2 partitions that should be completely accessible from every computer in the workgroup. I went through [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) but I cannot access the computer, instead the remaining XP-computer can now not access the workgroup at all, error massage is no rights to access. So Samba is doing something, but not what it is supposed to do.

Here is the smb.conf, someone finds the errors? I tried it like in the manual with first creating a folder sambashare and added later the printer and one of the partitions that everybody should be able to access, the thing called [Daten]. Workgroupname is the same as in XP, on the other computer there is a different username (at the moment I'm working on my wife's computer). The [liteshare] section was already there, I don't know where that came from.

```
#======================= Global Settings ====================================
[global]
workgroup = Abacus
server string = Linux Shares
netbios name = linux-moni
security = user
username map = /etc/samba/smbusers
map to guest = bad user
guest account = nobody
read only = no
dns proxy = no
#======================= Share Definitions ===================================
[liteshare]
path = /home/%U/linux_share
available = yes
valid users = %U %G

write list = %U
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[sambashare]
    comment = Samba on Ubuntu
    path = /home/username/sambashare
    read only = no
    browsable = yes

[printers] 
    path = /var/tmp
    printable = yes
    min print space = 2000

[Daten]
    path = /media/moni/Daten
    comment = Daten Moni Linux
    volume = Daten
    writable = yes
    browsable = yes
    guest only = yes
    guest ok = yes
```

---

### Post by Morbius1 on 2020-08-31
I'm going to give this a shot but I haven't used WinXP in more than a decade so it's going to be from memory ....... 

First: LinuxLite does in fact do funny things with samba. It does something even funnier with avahi which I can't quite figure out but that would only affect another Linux or MacOS client.

If "moni" is in fact a LinuxLite user name this will not work. At least it will not work as a guest accessible share:
> [Daten]
    path = /media/moni/Daten
    comment = Daten Moni Linux
    volume = Daten
    writable = yes
    browsable = yes
    guest only = yes
    guest ok = yes
Replace **guest only = yes** with **force** [B]user = moni

[/B]If you are running the latest version of Linux Lite it will disable SMB1 ( NT1 ) and without it disables netbios host name discovery. So you will need to enable it. There is another security related setting that make access to it from a WinXP an issue which will have to be altered as well.

Right under your **workgroup = Abacus** line add these:
```
server min protocol = NT1
ntlm auth = Yes
```

[COLOR=#ff0000]**EDIT**: I keep forgetting to mention this but when you modify protocol settings the server needs to be rebooted.[/COLOR]

[COLOR=#0000cd][I]Side Note: Discovery ( browsing ) by NetBIOS is a tricky thing to pull off. Microsoft pretty much abandoned it in Win10 because of that. My advice is to give your Linux server a static ip address - your router can do that since I don't know how LinuxLite does it - then access the server by ip address rather than by by name.

[/I][/COLOR][COLOR=#000000]That is the best I can do since I don't have any WinXP systems here to use to reproduce any issues you might have.[/COLOR]

---

### Post by svenmatti on 2020-08-31
Thanks, we are getting closer!

1. I can see the workgroup again and there are icons for the linux computer!
2. I could get the printer on the linux computer running, yeah!
but
3. I cannot access the data jet. It asks me to lock in, but after locking in it tells me I don't have the rights.

yes, "moni" is a username on linuxlite.

I want everybody to be able to access the [Daten], doesn't **force** **user = moni **[FONT=arial]do just the opposite?[/FONT]

This is just a tiny private network, no special security necessary.

---

### Post by Morbius1 on 2020-08-31
>  I want everybody to be able to access the [Daten], doesn't **force** **user = moni **[FONT=arial]do just the opposite?[/FONT]
No.
> [Daten]
    path = /media/moni/Daten
    comment = Daten Moni Linux
    volume = Daten
    writable = yes
    browsable = yes
    guest only = yes
    guest ok = yes                      

That share will allow any user on the network access to the "samba share". But after that you have to deal with Linux permissions. /media/moni has special permissions that allow only "moni" the abilty to traverse the folder to get to the Daten folder. 

> [Daten]
    path = /media/moni/Daten
    comment = Daten Moni Linux
    volume = Daten
    writable = yes
    browsable = yes
[COLOR=#ff0000]** force user = moni**[/COLOR]
    guest ok = yes                      


"force user = moni" makes the client user appear to be "moni". This is done after the client tries to access the folder not before. Now the "guest" user will appear to be "moni" so he is able to get to the Daten folder.

---

### Post by svenmatti on 2020-08-31
THANK YOU!

I got the idea and finally it works. The partitions were not mounted, that was the problem. So now I just have to automount them, which schould not be a big deal.

---

### Post by svenmatti on 2020-09-01
Well, yesterday I could connect to the printer from Win XP, today connection is denied. What's wrong?

---

### Post by svenmatti on 2020-09-01
That's pretty strange: I can print test pages, but I can't print documents. The window for the printer in Win XP says no permission.

I played around a bit, so here is the momentary smb.conf:

#======================= Global Settings ====================================
[global]
workgroup = Abacus
server min protocol = NT1
ntlm auth = Yes
server string = Linux Shares
netbios name = linux-moni
security = user
username map = /etc/samba/smbusers
map to guest = bad user
guest account = nobody
read only = no
dns proxy = no
printcap name = /etc/printcap
load printers = yes

#======================= Share Definitions ===================================

[printers]
# path = /var/spool/samba
   path = /var/tmp
browseable = yes
public = yes
guest ok = yes
writable = no
printable = yes

---


---
title: "10 Terabyte RAID 10 HELP PLEASE"
date: 2010-12-04
forum: Server Platforms
---

### Post by nqbus2001 on 2010-12-04
I have a new server (N00B) to ubuntu server, but i want to make it work, and im having so many problems....I have been following the ubuntu setup guide advanced setup, and for 36 hours it was stuck at 47%.  How should i set this up, or can somebody help me.  Please sooner rather than later, i leave for afghanistan in 7 days....:(



Please help

---

### Post by rubylaser on 2010-12-04
You need to provide us more detail.  Are you trying to use software RAID with mdadm or using fakeraid, or a hardware RAID card.  If it's mdadm, please paste the commands you used to build the array, and also provide the output of this command...
```
cat /proc/mdstat
```

The useful facts would be the hardware (processor, RAM) you used. And, more importantly, are the disks IDE / SATA/ SAS / SCSI, how are they connected the motherboard (controller card in PCI-Express, PCI-X, or PCI slot, etc?  Also, did all the disks pass a smart test before you built the array?

Thanks.

---

### Post by nqbus2001 on 2010-12-05
i got it to work, decided to jus use a 4 gb slot for the /boot, and 4 gb for swap

then put raid as ext4

problem im having now is with the samba side of things...is there a good way to learn this, or is it all trial by fire?

what would i have to type in order to be able to share files with a win 7 computer in a workgroup?

also what is a good program to stream with on a server?

---

### Post by Vegan on 2010-12-05
To use SAMBA, make a folder somewhere on the root file system and mount the array under it. Then you can tell SAMBA to share it.

SAMBA is very sophisticated but also easy to use.

I recommend using a SSD for the boot disk, and a real RAID card for the array.

---

### Post by nqbus2001 on 2010-12-07
so heres the odd thing.....samba works...kinda

it allows my computer to work, but my wifes computer it wants a password...where would i change it?

when i try to add users, it gives the error that it neither computer can log on due to permissions.

---

### Post by nqbus2001 on 2010-12-07
Its odd....it will work on my computer, but my wifes always asks for a password

any ideas?

heres my config

[global]
netbios name = BlackMannequin
server string = Samba file server
workgroup = WORKGROUP

[homes]
read only = no
browseable = no

[Entertainment]
path = /etc/nqbus/Desktop

browseable = yes
readonly = no

---

### Post by nqbus2001 on 2010-12-07
bump

---

### Post by arrrghhh on 2010-12-08
> **nqbus2001 said:**
> bump

No need to bump this thread...

I googled "samba, asks for password" and [this](http://www.debuntu.org/guest-file-sharing-with-samba) was the first link.  Please do some reading about [samba](https://help.ubuntu.com/community/Samba).

---

### Post by nqbus2001 on 2010-12-08
weird thing is i have never had the /init.d/ file for samba...when i first installed or even when i reinstalled with synaptic.

---

### Post by iponeverything on 2010-12-08
> i leave for afghanistan in 7 days.

I'll be back out there in a couple of months..

---

### Post by arrrghhh on 2010-12-08
> **nqbus2001 said:**
> weird thing is i have never had the /init.d/ file for samba...when i first installed or even when i reinstalled with synaptic.

You never will, it's smbd.  Also, if you're using 10.04 or newer you should use upstart scripts - ```
sudo service smbd [start|restart|etc]
```

---

### Post by nqbus2001 on 2010-12-08
i do use that but it still wont allow my wife to share...


now with the current setup i have, it should allow anyone access right?

is there an easy way that you guys can help me get this so it shares both my computer and wifes computer?


please and thank you

---

### Post by windependence on 2010-12-08
You need to add your wife as a SAMBA user on your server with the same user ID and password as her Windows box.
 
-Tim

---

### Post by nqbus2001 on 2010-12-08
done that, and i still cant get it to connect....cause then it asks for a password, and username for her computer name domain.

---

### Post by nqbus2001 on 2010-12-08
tried the page you listed, but didnt work, in fact now it wont let me log into it..

any ideas?

---

### Post by nqbus2001 on 2010-12-08
so i made a new samba config, but now it wont let anyone in...

[global]
workgroup = Workgroup
netbios name = BlackMannequin
server string = Samba Server %v
max log size = 50
security = user
password level = 8
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
username map = /etc/samba/smbusers
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
domain guest group = nobody @guest
name resolve order = wins lmhosts bcast
wins support = yes

[homes]
   comment = Home Directories
   browseable = no
   writable = yes

[Entertainment]
   path = /home/nqbus/Desktop/
   comment = nqbus
   browsable = yes
   browseable =yes
   read only = no
   guest ok = yes

with a testparm of

[global]
    netbios name = BLACKMANNEQUIN
    server string = Samba file server

[homes]
    read only = No
    browseable = No
    browsable = No

[Entertainment]
    path = /etc/nqbus/Desktop
    read only = No

---

### Post by nqbus2001 on 2010-12-09
anyone? 


any help would be greatly appreciated

---

### Post by arrrghhh on 2010-12-09
> **nqbus2001 said:**
> anyone? 


any help would be greatly appreciated

Did you run testparm on that config?  KISS, there looks like a lot in there that isn't necessary for your environment.  Start simple, then work your way up to the complicated stuff - that's how you learn.  You're not going to learn anything by having one of us just give you the answer.

---

### Post by nqbus2001 on 2010-12-09
i got it to work finally....but i had to use the IP address instead of the netbios name...i find that to be odd....went and fixed  my nvlm2 security settings, but i dont know if that is what fixed it

---


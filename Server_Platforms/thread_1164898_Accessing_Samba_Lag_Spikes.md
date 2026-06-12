---
title: "Accessing Samba Lag Spikes"
date: 2009-05-20
forum: Server Platforms
---

### Post by ubila on 2009-05-20
Hello all :)
 
I seem to be having large lag spikes when accessing my mapped network drive, which runs off a VM using Ubunutu server 8.10 mapped with Samba Server.
 
It happens every once in a while, for example, ill open the network drive and it might take 20 seconds to open, other times its instant.
 
I use eclipse for web development, and the project im running is on the samba server. Eclipse with "lock up" or freeze almost every time i save the file.
 
Ive looked all over for a solution to this, and cant seem to find a working solution!
 
I configured my Ubuntu 8.10 Server using this guide : 
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)
 
So yes i do have Bind9 setup and configured correctly.
 
Any help would be greatly appreciated.
 
Cheers

---

### Post by ubila on 2009-05-20
Anyone got any ideas why this might be happening :( ?

---

### Post by ubila on 2009-05-20
After searching around about this problem, i have seem to find many people with the same issue, yet no one has ever seemed to resolve it...

Heres someone else with the same issue :
[http://ubuntuforums.org/showthread.php?t=326055](http://ubuntuforums.org/showthread.php?t=326055)
[http://www.linuxquestions.org/questions/linux-networking-3/samba-shares-slow-down-or-freeze-windows-explorer-682535/](http://www.linuxquestions.org/questions/linux-networking-3/samba-shares-slow-down-or-freeze-windows-explorer-682535/)

I will post my smb.conf tonight when im home from work.

I have found people saying it might have something to do with DNS ?
Im using bind9 - and its all setup with the setting from the "Perfect Server" guide.
[URL="http://www.howtoforge.com/perfect-server-ubuntu-8.10-p4"]http://www.howtoforge.com/perfect-server-ubuntu-8.10-p4
[/URL]
- If you take a look at that link, in the bind9 section it says to add folders "named"
like this:

```
mkdir -p /var/lib/named/etc
  mkdir /var/lib/named/dev
  mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
```Am i supposed to replace 'named' with a hostname or username relating to my setup? Or is the folder definatly supposed to be called 'named'?

---

The problem Might be my Windows ?
Running XP Home Service Pack 2
Realy trying to avoid doing a fresh re-format, but might try that tonight if no replys

If anyones got anymore info/tips/ideas - please post :)
Realy stuck on this one :(

Cheers.

---

### Post by ubila on 2009-05-21
Seems like it could be XP Home thats causing the issue...
Works fine on my XP Pro laptop, and my XP Pro PC at work.

Unless anyone can confirm XP Home works perfect for them with mapped drives via samba im gonna install the "next best thing i have" - Vista..... "shudders"

---

### Post by ubila on 2009-05-29
So i re-installed XP Home - and for a few days, everything seemed fine.

But the lag spikes have come back.
When i open My Computer, it hangs for around 30-40 seconds, Eclipse will not save a file onto the samba mapped network drive without hanging for around 30 seconds. And browsing files on the samba drive every once in a while cause windows to freeze for again around 30 seconds.

Things i have tried :

- Re-installing Windows
- Re-installing UBUNTU 
- Re-configuring UBUNTU and SAMBA from scratch (done this twise)
- Re-mapping network drives
- Checked the logs, Nothing strange happening in there...
- Changed workgroup to MSHOME which is what my windows network runs on.

- Commented out all other samba shares.. the only thing i have shared is my custom [dev] share which looks like this :

```


[dev]
    comment = Client Work Folder
    browseable = yes
    path = /var/www
    public = no
    read only = no
    create mode = 0766
    directory mode = 0775
    guest ok = no
    writeable = yes


```

My /etc/samba/smbusers file looks like this:

```


<richard> = "<richard>"


```


(my login from windows is richard)
[B]
Please someone help!!!
Have no ideas left at all. [/B]

---

### Post by Vegan on 2009-05-30
I use SAMBA but not virtualized, I use it native on a dedicated machine. I never have any problems.

---

### Post by ubila on 2009-05-30
> **Vegan said:**
> I use SAMBA but not virtualized, I use it native on a dedicated machine. I never have any problems.

I orginaly had samba running from my real linux box, but i was getting the same issue, so i thought i might be quicker running from a virtual machine on the same pc i use to access the samba.... same problem though :(

Windows XP SP2
Ubuntu 8.10 Server

---


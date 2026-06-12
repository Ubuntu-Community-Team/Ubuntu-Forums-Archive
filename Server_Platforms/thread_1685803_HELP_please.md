---
title: "HELP please"
date: 2011-02-11
forum: Server Platforms
---

### Post by dj07707 on 2011-02-11
Great ones, i need abit of help please
I want to install linux on a usb and have it run a small script when it boot.
Where shall i start.

Live CDs run in memory so thats no good for me in terms of saving my scrip on there. 

What i want is basically a portable OS i can pop into any machine and have it load up and run my custom script.

Any ideas please....

---

### Post by iiz on 2011-02-11
> **dj07707 said:**
> Great ones, i need abit of help please
I want to install linux on a usb and have it run a small script when it boot.
Where shall i start.

Live CDs run in memory so thats no good for me in terms of saving my scrip on there. 

What i want is basically a portable OS i can pop into any machine and have it load up and run my custom script.

Any ideas please....

Check out unetboot: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

i made a guide a while back on our company blog about unetbootin: [http://www.usbtalk.net/2009/12/booting-linux-from-a-flash-drive/](http://www.usbtalk.net/2009/12/booting-linux-from-a-flash-drive/)

It installs different distros to flash disks, as for a startup script check your rdX.d folders. Depending on your run level they are rc1.d - rc6.d located in /etc/. Those folders contain links to init.d scripts and S in front stands for startup script K stands for kill script. The numbers in the links stand for the priority. I don't know if this is the best way to execute a start script, but this is how services are started like syslog and postfix.

hope this helps

---

### Post by dj07707 on 2011-02-13
Hey...thanks for the response. I know about unetbootin but i dont think that will meet my requirements since it acts as a live CD on a USB. I want to be able to do an install to usb that i can use on different machines when needed. An install which means i want to be able to save files, etc and all those changes will be available to me when i plug the usb in another machine and boot. I hope am making sense.

---

### Post by dj07707 on 2011-02-15
OK i got the live CD thing sorted. Another issue. All my liveCD does is mount any NTFS filesystem and writes to it. I can do the mounting but i cant write to it. Any suggestions?

---

### Post by iiz on 2011-02-21
> **dj07707 said:**
> OK i got the live CD thing sorted. Another issue. All my liveCD does is mount any NTFS filesystem and writes to it. I can do the mounting but i cant write to it. Any suggestions?

try using:

```
ntfs-3g
```

regular ntfs does not support write operations ntfs-3g gives you full write capability.

Also:
[Installing ubuntu onto a usb drive.]("http://www.usbtalk.net/2010/10/how-to-3-ways-to-boot-ubuntu-10-04-from-a-usb-flash-drive/")
This guide explains how to install ubuntu to a flash drive, not the live cd.

---

### Post by dj07707 on 2011-02-21
> **iiz said:**
> try using:

```
ntfs-3g
```regular ntfs does not support write operations ntfs-3g gives you full write capability.

Also:
[Installing ubuntu onto a usb drive.]("http://www.usbtalk.net/2010/10/how-to-3-ways-to-boot-ubuntu-10-04-from-a-usb-flash-drive/")
This guide explains how to install ubuntu to a flash drive, not the live cd.

Hey thanks. I found out about ntfs-3g after using system rescue cd, just didnt know it worked on ubuntu. thanks a lot

---

### Post by dj07707 on 2011-02-28
Of course ntfs-3g comes with ubuntu. All sorted. Thanks.

---


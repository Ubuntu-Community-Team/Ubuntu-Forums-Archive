---
title: "How do I change the computer name?"
date: 2008-11-20
forum: Server Platforms
---

### Post by GreenCare on 2008-11-20
How do I change the computer name?

---

### Post by MJN on 2008-11-20
Strictly speaking, the answer 'it depends'! (many applications/services maintain their own definition)
 
However, for most common purposes the first place you should be looking is in /etc/hostname
 
Mathew

---

### Post by GreenCare on 2008-11-20
Thanks for replying. When I installed 8.04 server it asked me for the computer name in one of the first screens. I have since changed my mind on my server name. I looked at the etc/hostname and nothing came up. Tom

---

### Post by snova on 2008-11-20
I don't think you should modify /etc/hostname directly.

From the command line, I believe the command is:

```
sudo hostname <new name>
```

---

### Post by tubezninja on 2008-11-20
> **snova said:**
> I don't think you should modify /etc/hostname directly.

From the command line, I believe the command is:

```
sudo hostname <new name>
```

In my experience, that only works until the system is shutdown/rebooted.  Then it reverts to the previous setting.

The way to do it permanently is to edit /etc/hostname, and then run 

```
sudo /etc/init.d/hostname.sh start
```

to make the box reflect the changes.

If you don't have an /etc/hostname, I don't know what to tell you.  maybe it would be wise to do a "sudo find / -name hostname" to see if it's somewhere else, and if nothing pops up, then simply create the file.

---

### Post by Thirtysixway on 2008-11-20
See post #3

[http://ubuntuforums.org/showthread.php?t=224722](http://ubuntuforums.org/showthread.php?t=224722)


You need to edit and save /etc/hostname and /etc/hosts at the same time, then reboot.

---

### Post by pvanos on 2009-06-04
> **Thirtysixway said:**
> See post #3

[http://ubuntuforums.org/showthread.php?t=224722](http://ubuntuforums.org/showthread.php?t=224722)


You need to edit and save /etc/hostname and /etc/hosts at the same time, then reboot.

In the above mentioned thread, a GUI method is mentioned (Steve Horsley):
System > Administration > Networking , and look in the General tab for Hostname.

Now, since I installed Kubuntu 9.04, this is NO LONGER THERE !
Then, as alternative, I installed Ubuntu 9.04, and also here, I can no longer find this "Networking" !!!
Only "Network Tools", which is apparently not the same.

If the only solution is to simultaneously alter the files /etc/hosts and /etc/hostname , I wonder what the Ubuntu GUI shell is for ???
Why is this System > Administration > Networking feature no longer available in the standard installation ?

---


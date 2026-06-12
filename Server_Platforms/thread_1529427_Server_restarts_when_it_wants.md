---
title: "Server restarts when it wants ?"
date: 2010-07-12
forum: Server Platforms
---

### Post by xx77aBs on 2010-07-12
Hello ! 

I'm currently using ubuntu desktop 9.10 (without desktop - I've removed packages) as OS on my server.

But there's going on some strange thing ... There are about 8 users, and the thing is they many times user rar or some other disk-demanding programs. What I've noticed is that sometimes server will go with load over 20 (I know that's not good ...) and it will come down in few minutes and everything is OK, but sometimes it just restarts itself. I would like to disable that so it won't restart, or at least find out why it restarts ... So if you know how to help me, please do :D


Thanks !!

---

### Post by ruffEdgz on 2010-07-12
> **xx77aBs said:**
> Hello ! 

I'm currently using ubuntu desktop 9.10 (without desktop - I've removed packages) as OS on my server.

But there's going on some strange thing ... There are about 8 users, and the thing is they many times user rar or some other disk-demanding programs. What I've noticed is that sometimes server will go with load over 20 (I know that's not good ...) and it will come down in few minutes and everything is OK, but sometimes it just restarts itself. I would like to disable that so it won't restart, or at least find out why it restarts ... So if you know how to help me, please do :D


Thanks !!

Because you are using the desktop version of Ubuntu, the kernel parameter is probably set to a value that tells the server to restart. If you do this command:

```
sudo sysctl -a | grep kernel.panic
```

What value do you get? If you don't get a '0' for that value, you will want to make sure that kernel parameter is set to '0' at all times.

To set that value while the computer is up, type in this command:

```
sudo sysctl -w "kernel.panic=0"
```

To make sure you don't need to set this parameter again on a reboot, type in the following command:

```
sudo echo "kernel.panic = 0" >> /etc/sysctl.conf
```

And that should do it. If that isn't the issue, then report back but just from the sound of it, it just sounds like the kernel panics because of the high load to the computer. Hope this helps.

---

### Post by xx77aBs on 2010-07-12
> **ruffEdgz said:**
> Because you are using the desktop version of Ubuntu, the kernel parameter is probably set to a value that tells the server to restart. If you do this command:

```
sudo sysctl -a | grep kernel.panic
```

What value do you get? If you don't get a '0' for that value, you will want to make sure that kernel parameter is set to '0' at all times.

To set that value while the computer is up, type in this command:

```
sudo sysctl -w "kernel.panic=0"
```

To make sure you don't need to set this parameter again on a reboot, type in the following command:

```
sudo echo "kernel.panic = 0" >> /etc/sysctl.conf
```

And that should do it. If that isn't the issue, then report back but just from the sound of it, it just sounds like the kernel panics because of the high load to the computer. Hope this helps.

Thanks for replying !!

When I run 
```
sudo sysctl -a | grep kernel.panic
```
I get this:
> error: "Invalid argument" reading key "fs.binfmt_misc.register"
kernel.panic = 0
kernel.panic_on_oops = 0
kernel.panic_on_unrecovered_nmi = 0
kernel.panic_on_io_nmi = 0
error: permission denied on key 'net.ipv4.route.flush'


So I guess it's not about kernel panic ?

---

### Post by xx77aBs on 2010-07-12
oh, it restarted again, load was about 2-3 (that's not much !!), and I was hashing 14gb torrent ...

what could be the problem ?

---

### Post by arrrghhh on 2010-07-12
Just curious, why don't you install the normal server edition?  From the sounds of it you hacked a -desktop version to work as a server.  That *should* work, but it can cause issues if you're not careful!  (Or know what you're doing ;))

I'm not much of an expert on why servers reboot, but immediately after the reboot you should check your logs if possible, see what is in there right before it restarts...

---

### Post by ruffEdgz on 2010-07-12
> **arrrghhh said:**
> 
I'm not much of an expert on why servers reboot, but immediately after the reboot you should check your logs if possible, see what is in there right before it restarts...

I was thinking about this as well.

One thing I would do is check your /var/log/messages or /var/log/syslog, find a time when you had a restart and place it into this forum. That might help with why it is rebooting on its own.

The torrent thing could be the logs will be a bit more accurate as to what could be causing the reboots.

---

### Post by arrrghhh on 2010-07-12
You could have a hardware issue, but hopefully that will be exposed in the logs...

---

### Post by xx77aBs on 2010-07-12
> **arrrghhh said:**
> Just curious, why don't you install the normal server edition?  From the sounds of it you hacked a -desktop version to work as a server.  That *should* work, but it can cause issues if you're not careful!  (Or know what you're doing ;))

I'm not much of an expert on why servers reboot, but immediately after the reboot you should check your logs if possible, see what is in there right before it restarts...

Well, server is hosted by OVH, and OVH doesn't do business with my country, so I had to buy it from reseller ... And reseller won't give me access to OVH control panel because they have all server in one account. So I can't install new OS on it ...

> **arrrghhh said:**
> You could have a hardware issue, but hopefully that will be exposed in the logs...

I was thinking about that, but I'm not sure because this behavior started like few days ago, and I've removed all desktop-things about that time ... But I've used tasksel tool, so I'm not sure if it maybe did something wrong

> **ruffEdgz said:**
> I was thinking about this as well.

One thing I would do is check your /var/log/messages or /var/log/syslog, find a time when you had a restart and place it into this forum. That might help with why it is rebooting on its own.

The torrent thing could be the logs will be a bit more accurate as to what could be causing the reboots.

Ok, but I can't do that right now. Server looks like it rebooted (I couldn't access it over SSH or ping it) - now I can ping it and it responds OK.

But I can't access it via HTTP, SSH of FTP ... It seems that something is awfully wrong. This has never happened before :(

---

### Post by Vegan on 2010-07-12
First use the server edition, second looks like your CPU is overheating so check the HSF and make sure the thermal grease is OK

---

### Post by doogy2004 on 2010-07-12
check your uptime to see if it is actually rebooting and not just locking up while it processes large requests (tasks such as hashing 14GB takes a long time).

What is the result of this command?

```
uptime
```

---

### Post by xx77aBs on 2010-07-12
> **Vegan said:**
> First use the server edition, second looks like your CPU is overheating so check the HSF and make sure the thermal grease is OK

Can't do that, server is in data center :) But I don't think that CPU is overheating, because it is almost never about 50% ...

> **doogy2004 said:**
> check your uptime to see if it is actually rebooting and not just locking up while it processes large requests (tasks such as hashing 14GB takes a long time).

What is the result of this command?

```
uptime
```

I check uptime every time that I think it has rebooted :) Now uptime is about 30 min :)

@all: Ok now I can access it again. I've checked messages and syslog and there's some nasty stuff that I don't understand :D

Server rebooted about 00:10, but I've included all after that :) 

messages file
[http://paste-it.net/public/p7cbfc1/](http://paste-it.net/public/p7cbfc1/)

syslog
[http://paste-it.net/public/q4c31b8/](http://paste-it.net/public/q4c31b8/)


After looking at these files, I think that there's some problem with swap memory space, it couldn't be allocated or something like that. But the thing is, memory usage doesn't go above 1gb, and server has 2GB of RAM. I know that "free" space is used for system cache and generally to speed the system up, but why would linux try to use swap when it has 1GB "free" ? But OK, even if it wants to use swap while it has "free" RAM, I don't know what the problem could be, because size of my swap is 1GB (500MB on each HD - I have two hard disks in RAID 0) ...

I hope that at least I'm right about one thing, but I'm here only to learn, so please correct me and/or say something new :D

---

### Post by arrrghhh on 2010-07-12
I see a lot of these ```
swapper: page allocation failure. order:0, mode:0x20
``` with a bunch of other debug error messages around it...

Not sure if that indicates a hardware issue with the hard drive or RAM or what is the underlying issue... But I would think that is probably related.

From a quick-n-dirty google search, looks like your programs are not getting the memory they need.  I still can't explain the restarts however...

---

### Post by xx77aBs on 2010-07-12
So I was very curious and tried this:

right now no one was on the server, I was the only user (in my country right now it's 1:13 AM, so that's nothing surprising :D ), and when I've connected server load was 0.01 

Then I started just one rtorrent instance (with screen) - it had to 14GB torrents do check hash... It has started doing hashes and I've hidden it and started htop ... after 5 to 10 minutes I got message from PuTTY that connection has failed, and here is my last screen that was in PuTTY

So CPU wasn't used very much, and RAM (and swap too) isn't even at 15%

Here's screenshot:
[IMG]http://i30.tinypic.com/1hs407.jpg[/IMG]


> **arrrghhh said:**
> I see a lot of these ```
swapper: page allocation failure. order:0, mode:0x20
``` with a bunch of other debug error messages around it...

Not sure if that indicates a hardware issue with the hard drive or what... But I would think that is probably related.

Yeah, unfortunately I'm starting to think that there's problem with hard drive, because it clearly happens when I'm doing hash checking ... I'm still new to linux, so can you tell me some tools to check harddrive (for logical FS error, bad sectors and that stuff) ?

Thank you all for all your help :) !!!

---

### Post by arrrghhh on 2010-07-12
Do you have any SMART monitoring enabled?  I'm not extremely knowledgable on the subject (starting to sound like a broken record here!) but I use SMART in conjunction with Webmin.  That's what I use to monitor the health of the drives, I'm sure there are many other alternatives.  As for stress testing the drives, again I just run the SMART extended/self tests.  Not sure what else is out there, I'd like to know as well :D

Obviously you could just run an FSCK check on the drive...

From a quick Google, FSCK would be the place to start.  I'd be curious to know if there are any more advanced tools.

---

### Post by xx77aBs on 2010-07-12
I've done some research and here is tool for checking ext2/3 FS :D

e2fsck

I've just seen SMART info and it reports OK for booth hard disks. I'll first do e2fsck and if there are no errors, I'll run long SMART check :D

---

### Post by xx77aBs on 2010-07-13
Just to tell you guys, the problem was solved by running e2fsck :D 

thanks for help :)

---


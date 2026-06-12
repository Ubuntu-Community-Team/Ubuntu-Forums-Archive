---
title: "Crisis Averted. Did I ever screw up ;)"
date: 2006-08-21
forum: The Cafe
---

### Post by Burke on 2006-08-21
So I was running this script called 'faster-dapper.sh', which is supposed to speed up dapper. It's supposed to be run as sudo.

It wasn't.

It tried to install dash and replace sh with it, but unfortunately enough, it only succeeded in perma-linking /bin/sh to /bin/dash, which didn't exist. 

Great.

So I loaded up a 6.06 LiveCD and just copied over /bin/sh to replace the bad link. Unfortunately, when I rebooted, ubuntu decided that it had to link /bin/sh to /bin/dash again, and it wouldn't even boot.

At this point, I went and got some coffee.

When I got back, I had an idea of what to do. 

I booted up the liveCD again, mounted my hard drive, and chrooted into /mnt/hda4 (my linux drive). I ran 'sudo apt-get install dash', and rebooted. 

Success! 

I didn't have to murder a perfectly good Linux ;)

---

### Post by Sam on 2006-08-21
That's one argument when I try to convert people to Linux: you don't have to reinstall everything when something blows up...

---

### Post by Burke on 2006-08-21
heh. the best part was, even though I screwed up my system, when I got it working again, it was even faster than before (I've been doing a *lot* of optimisations).

Yeah, if something like that happened on Windows, there'd be no two ways about it, you'd have to reinstall. 

Then again, I wouldn't have been able to figure out what to do up until about 3 months ago. It's all a matter of expertise.

---

### Post by 3rdalbum on 2006-08-21
I screwed up my system a couple of months ago. I changed my computer's hostname to blank, which then stopped the sudo command from working. If I logged in into Recovery Mode, it wouldn't display the Networking control panel.

As Linux stores configuration data in human-readable text files, I just had to find /etc/hostname and change it back. Easy!

---

### Post by prizrak on 2006-08-21
> **Burke said:**
> heh. the best part was, even though I screwed up my system, when I got it working again, it was even faster than before (I've been doing a *lot* of optimisations).

Yeah, if something like that happened on Windows, there'd be no two ways about it, you'd have to reinstall. 

Then again, I wouldn't have been able to figure out what to do up until about 3 months ago. It's all a matter of expertise.

It's a matter of experience in Windows as well. I have replaced corrupted system files from the Windows install CD before. It was a pain in the butt but possible. apt-get way is quite a bit easier of course.

---

### Post by saracen on 2006-08-21
> **3rdalbum said:**
> I screwed up my system a couple of months ago. I changed my computer's hostname to blank, which then stopped the sudo command from working. If I logged in into Recovery Mode, it wouldn't display the Networking control panel.

As Linux stores configuration data in human-readable text files, I just had to find /etc/hostname and change it back. Easy!

What is the right way to change a computer's hostname?

---


---
title: "How difficult is it to secure a home server?"
date: 2009-09-05
forum: Server Platforms
---

### Post by oozydigg on 2009-09-05
Hi Everybody,

It might help people answer this question if I say a little bit about my experience with computers.  I've worked as a programmer and Windows sysadmin, but it's been a while since those days.  I've also worked as a Linux sysadmin, but that was back when you could get buy a desktop edition of redhat at a local store!

I'd like to build a home server.  At this point it's primary purpose will be as a NAS, but I plan to eventually make a basic webserver, and perhaps other stuff in the future.  Having that flexibility for the future is important.

I realize the easiest solution is to buy a NAS from QNAP or Synology.  But I'm weary of a short EOL cycle as I'd like it to last (including software updates) for 5 years and lack of flexibility as far as software.  Beyond that, I can build a nice ATOM based rig for not much more than built NAS box costs.

But I have one big fear with building my own server - **Security**.  How difficult is it to secure a Ubuntu server?  Would be there a difference if I used Ubuntu Desktop?  How much time would I be required to invest to make sure the OS is secure?

Back when I was a sysadmin security included messing with IP tables, software/hardware firewalls, messing with file permission and other stuff I can't remember now.  This is beyond what I want to do.  I don't want to spend my life administering the server.

I realize my question is very vague, but any help is appreciated.

Thanks,

-odigg

---

### Post by Whiffle on 2009-09-05
I think this would be an excellent read for you:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Lori700698 on 2009-09-05
Since you have experience (and I'm an average wanna be, actually IT student) you shouldn't have too much trouble. I've learned that killer passwords, uncommon user names,  and watching your logs for attempted hacks will keep you fairly safe.  I just got hacked over a dumb user name & password by a brute force SSH attack.  I wasn't watching the logs and well, I've learned my lesson.  Ubuntu has some awesome tools.  Fail2ban, logwatch, snort, clamav, ossec, and many more.  I'm running these at the moment but I have a lot of ports open to run all my stuff I wanted to try.  Hit the security threads and look at the stickys...Lots of info and great advice.

Enjoy!!!

---

### Post by Sporkman on 2009-09-05
Ubuntu server is pretty secure out-of-the-box, so you'd have to actively undermine its security. :)

---

### Post by R.Bucky on 2009-09-07
If all that you want is NAS, then the box should not even be open to the web. With that said, I have found that changing the default SSH port eliminates 99% of the hacker problem (aside from web server traffic, SQL, and php hacks). Coupled with fail2ban, I have not had a single attempt on my box using SSH in 2 months. Before changing from port 22, I was logging hundreds of failed attempts daily. 

I currently operate a RAID1 array (web server disks) with a single 500GB hdd using Samba for network storage access to that drive within the same tower. It is all backed up to a 1TB drive nightly. You can have your NAS, RAID1, and eat it too!

---

### Post by lykwydchykyn on 2009-09-07
Technically speaking, you don't secure a server.  You secure services, and you secure them from something.
So the answer to your question hinges entirely on what services you plan to run, and what you intend to expose it to.

---

### Post by bear24rw on 2009-09-07
If you keep it local you dont really have much to worry about. If you want out of lan access with ssh, like others said, change /etc/ssh/sshd_conf port to something other than 22 and sudo apt-get install fail2ban also search the forums and google for "hardening" ubuntu server

---


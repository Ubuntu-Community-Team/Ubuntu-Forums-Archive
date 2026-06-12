---
title: "Owned in 30 minutes"
date: 2006-05-11
forum: Server Platforms
---

### Post by izvie on 2006-05-11
After loading Ubuntu 5.10 on my laptop, I added Java and Flash to the original Ubuntu distro, 
right from the Synaptic Package Manager and then updated the latest security updates for all 
the packages. That was all I did.  My laptop is behind a Netgear router.

After that, I went surfing to every malicious site I know of using this Ubuntu setup.  
It was connected to the Net for about 30 minutes, tops.

The next day, I turned on the machine and when prompted to enter my Ubuntu password so I 
could grab system updates (the red button was lit up at the top right), I received a message
stating (sorry I erased the original message, so this is not exact): "The system could not 
grab your mouse.  You may have a malicious user on the system."  It also stated my root 
password was invalid.

I had nothing on the Ubuntu install, so I am going to erase the partition and start over.  
I had read the post in the Ubuntu Security forum titled "Sticky: Are firestarter and clamav 
really necessary??" and concluded that they were not.  This time I’ll be loading a Firewall 
and AV. 

Aside from advice like "don't go to those sites" what can I do to truly harden Ubuntu when
I reinstall besides AV and firewall?  Thanks.

---

### Post by aysiu on 2006-05-11
Anti-virus won't stop people from cracking into your system. People "owning" you are not viruses. Getting a firewall is not a bad idea, but, honestly, Ubuntu doesn't start off listening to any ports.

Why were you going to every malicious site you could think of...? Just as some sort of experiment?

---

### Post by johnc4510 on 2006-05-11
I run firestarter firewall, very secure and very easy to configure from the gui. I don't have any antivirus, but am very careful about my mail. As to other resources, there are two that I run and they are both rootkit scanners. The first is rkhunter and the other is chkrootkit. They are both run from the terminal as:
sudo rkhunter -c
sudo chkrootkit
Hope this helps

---

### Post by izvie on 2006-05-11
Yes, Aysiu just experiments.  I was curious.  Once I reinstall with a firewall I'll try again at the same sites and see what happens.

---

### Post by izvie on 2006-05-11
Yes, that does help, John4510.  I have added those to my "to-do" list for the re-install.  Thanks.

---

### Post by az on 2006-05-11
[QUOTE=izvie]"The system could not 
grab your mouse.  You may have a malicious user on the system."  It also stated my root 
password was invalid.[/QUOTE]

That message can be cause by a number of things.  An X session uses an authentification system that is pretty cautious.  You would have to look in the auth logs to see if someone logged into your box remotely - did you install telnet or ssh?

I think you just had a filesystem corruption rather than a security breach.

---

### Post by izvie on 2006-05-11
Interesting, azz.  I didn't load telnet or ssh, but I am adding them to the list of things to load on the reinstall.  Are there any logs I could look at without those two utilities installed?  If it was a filesystem corruption, is there a way to clean up the corruption?

---

### Post by towsonu2003 on 2006-05-11
[QUOTE=izvie]Interesting, azz.  I didn't load telnet or ssh, but I am adding them to the list of things to load on the reinstall.  Is there any logs I could look at without those two utilities installed?[/QUOTE]
I don't think he meant "install them to see logs" or similar. both connect/listen to outside world and hence open up new venues for security vulnerabilities. 

logs you could look at are under /var/log
useful ones include dmesg, Xorg.0.log, auth, syslog, and a couple of more that I don't remember... 

if you wanna re-do the experiment, try doing it with [firefox 1.5.0.3]("https://wiki.ubuntu.com/FirefoxNewVersion") to see if the same thing occurs again. note the sites you visit so anyone can duplicate your actions :)

---

### Post by izvie on 2006-05-11
Thanks towsonu2003, I see what you mean...dmesg, Xorg.0.log, auth, syslog...got it.  I'll look at the logs tonight and see if I can understand them.

Edit: Slapping my head now, Telnet and ssh...sheesh.  I know what those are, but I have been fooling around with Ubuntu so much lately that the acronyms didn't register...I thought they were something for Ubuntu log viewing.

---

### Post by RavenOfOdin on 2006-05-11
[QUOTE=izvie]Slapping my head now, Telnet and ssh...sheesh.  I know what those are, but I have been fooling around with Ubuntu so much lately that the acronyms didn't register...I thought they were something for Ubuntu log viewing.[/QUOTE]

Ouch.

There's a saying which goes as follows, and which this proves: "Security is only as good as the admin responsible for it."

---

### Post by izvie on 2006-05-11
[QUOTE=RavenOfOdin]Ouch.

There's a saying which goes as follows, and which this proves: "Security is only as good as the admin responsible for it."[/QUOTE]
True.  But I'll get better as I learn more, which reminds *me* of a quote:  "Experience is a comb that life hands you after you have lost all your hair."

---

### Post by linbetwin on 2006-05-11
izvie, could you provide some of the malicious addresses you visited? I'd rather you wrote them in such a way that they cannot appear as hyperlinks. And put a big red warning in front of them, so that people will know what to expect.

---

### Post by Azrael on 2006-05-11
I'm not sure I believe this story. I find it extremely unlikely for an unfixed security flaw that critical to be present in Firefox version 1.0.8 or higher. OP, are you sure you didn't deliberately try to run trojans (i.e. downloading and executing arbitrary code from untrusted sources)? Also, are you sure no individual at any moment had *physical* access to your computer?

If things really happened like you described them, then please add as much detail as you can remember (e.g. the sites you visited); it might be of interest to the Ubuntu developers. :-k

---

### Post by az on 2006-05-11
[QUOTE=RavenOfOdin]Ouch.

There's a saying which goes as follows, and which this proves: "Security is only as good as the admin responsible for it."[/QUOTE]
Which is why ubuntu doesn't ship with anything listening to the outside world.

---

### Post by izvie on 2006-05-12
azz, I think you are correct;  the file system got corrupted.  When I turned on the machine last night to look at the log files I got the following message as it booted (please note that I typed this manually off the screen as Ubuntu wouldn't boot and I only copied out the relevant part):

* Setting disc parameters...
* Checking root file system...
/ contains a file system with errors, check forced.
/:
Inodes that were part of a corrupted orphan linked
list found.

/: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
   (i.e., without -a or -p options)

* fsck failed.  Please repair manually and reboot.
Please note that the root file system is currently
mounted read-only.To remount it read-write:

* # mount -n -o remount,rw /

* CONTROL-D will exit from this shell and REBOOT the
system.

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none): # (blinking cursor)

Now the question is, why did it corrupt and why did Ubuntu throw up a malicious user comment on a corrupted file system?  Anyway, I am going to reload the OS this weekend and try surfing around again and see what happens.  

Thanks to all so far who have offered advice.

---

### Post by RavenOfOdin on 2006-05-12
[QUOTE=izvie]and why did Ubuntu throw up a malicious user comment on a corrupted file system?[/QUOTE]

Probably for the same reason that chkwtmp threw up 4 deleted log entries on mine, when no one breached my box.

---

### Post by Azrael on 2006-05-12
> Now the question is, why did it corrupt and why did Ubuntu throw up a malicious user comment on a corrupted file system?
I, for one, have no idea why... If you are able to repeat the events and get that comment again (or even if you don't), then I think a message *that misleading* is worth being reported as a bug on Ubuntu's bug tracker.

---

### Post by az on 2006-05-12
[QUOTE=Azrael]I, for one, have no idea why... If you are able to repeat the events and get that comment again (or even if you don't), then I think a message *that misleading* is worth being reported as a bug on Ubuntu's bug tracker.[/QUOTE]

It may be that the process that was the result of a filesystem corruption tried to access priviledged ressources, like the X server, in the process of crashing.

---

### Post by izvie on 2006-05-13
azz, I think your reasoning wins out here.  Check this post out from another thread on dslreports, from Sybille (Thanks Sybille):

 [http://www.dslreports.com/forum/remark,16077714](http://www.dslreports.com/forum/remark,16077714)

Azz, apparently you were dead-on correct.  Here's the post from Sybille if you don't feel like wading through the whole thing:

 I think that "malicious user may be grabbing your keyboard or mouse" error message is one of the standard error messages for gksudo and gksu, which are graphical interfaces for sudo and su.

I saw the message on my computer once when I was making a script to run an application with sudo from my fluxbox menu. I t was a problem with the script, or at least I think it was. In any case, I've since paid close attention to my system, the logs and so on, and also run rkhunter for what that's worth, and I haven't seen anything suspicious so I have no reason to think it was anything but an error in the script, lol.

Anyway, I think it's a case in which a particularly alarming kind of error message can serve to hide another problem - in your case a file system error, in my case a syntax mistake in a little script.

---

### Post by pelago on 2006-05-15
[QUOTE=izvie]"The system could not grab your mouse.  You may have a malicious user on the system."[/QUOTE]
I've had that message appear when I've tried to run e.g. Synaptic when the computer is still starting up and the hard disk is rattling away. I think if it takes more than a few seconds to respond, that message pops up. I just cancel it and try it again and it's fine.

So basically, that message doesn't always mean you've been owned.

---

### Post by Slim Odds on 2006-05-15
It might be worth noting that it is always a good idea **NOT TO PANIC!**

Assumptions can lead to a lot of wasted time and effort.

Admittedly, the message was scary, but do a little investigation before posting a message with the title "Owned in 30 minute" (unless it's a Windows machine, then change to "Owned in 15 minutes").

Any linux system that's behind a firewall is quite safe (unless you run everything as root, which you should _never_ do).

---

### Post by nocturn on 2006-05-18
[QUOTE=izvie]
stating (sorry I erased the original message, so this is not exact): "The system could not 
grab your mouse.  You may have a malicious user on the system."  It also stated my root 
password was invalid.
[/QUOTE]

About not grabbing the mouse/keyboard, this is an error I've seen before, it happens also when you click twice on an admin item.

So far, indications that you actually have been hacked are quite slim.  I recommend a reboot (to make sure) and try you root password again.

Also check if you are still a member of the admin group (the id or groups command).

A firewall helps, but only marginally on a default install (unless you also enable outbound filtering).  
But AV is a flawed dogma.   It's great for a post mortem, but not to prevent intrusions.

---


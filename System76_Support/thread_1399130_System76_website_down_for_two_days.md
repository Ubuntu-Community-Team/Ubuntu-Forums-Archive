---
title: "System76 website down for two days"
date: 2010-02-05
forum: System76 Support
---

### Post by thomasaaron on 2010-02-05
**DON'T WORRY! WE HAVEN'T GONE AWAY!**

Our web hosting service is experiencing a data center-wide outage. We are currently transferring our site to other servers and expect this process to take a couple of days.

This will also keep the System76 Driver from running, as it pings our website to determine that there is an Internet connection. We're sorry for this inconvenience.

While we will be unable to take orders while the site is down, we are still available via forums, phone and email to answer any sales or support questions you have.

Thank you for your understanding.

Tom Aaron
[email]support@system76.com[/email]
720-226-9269

---

### Post by tlroche on 2010-02-05
> **thomasaaron said:**
> Our [...] data center-wide outage [...] will also keep the System76 Driver from running

arrggghhhh: before I saw this, my GF's starling started a Software Update on the kernel, which is invoking a connection to planet76.com, which is stuck in a loop of timeout/retry. What's the best way to abort this without bricking the box?

---

### Post by thomasaaron on 2010-02-05
I'm not sure. If it is in the Install phase of the download, that means it's trying to compile the wireless driver. So if you run...

killall update-manager

It *should* just leave the wireless card inop without bricking the whole kernel.

---

### Post by SamsLembas on 2010-02-05
I don't actually have a System76 machine, so I might not be understanding how this works, but: Couldn't you just remap the website in /etc/hosts to a functional web server (such as google) or to localhost?

---

### Post by tlroche on 2010-02-05
> **thomasaaron said:**
> `killall update-manager` *should* just leave the wireless card inop without bricking the whole kernel.

Yep, except that, by the time I got back to it, Update Manager had timed itself out. As you guessed, that whacked the wireless but not the whole kernel. I was able to [kludge the wireless by booting the previous kernel]("http://ubuntuforums.org/showthread.php?t=1399404"), but would like to know [how to fix the new kernel once planet76.com returns]("http://ubuntuforums.org/showthread.php?t=1399413").

---

### Post by jdb on 2010-02-05
> **SamsLembas said:**
> I don't actually have a System76 machine, so I might not be understanding how this works, but: Couldn't you just remap the website in /etc/hosts to a functional web server (such as google) or to localhost?

The server is were all the web site code & files are.
An agreement has to be made with a new company & then all the stuff has to be moved & the new site set up.

Also, how do you get /etc/hosts changed in all the user machines out there if they can't get to the old site?
What really needs to be done is the DNS servers need to get updated & it takes a while for that to happen.

If everything is running smoothly by Monday, they've really done something.

jdb

---

### Post by seanmccaskey on 2010-02-05
RATS!!  I just received my new System76 desktop and left it on for a couple of evenings after applying updates and installing a few packages...The screen was blank, so I rebooted.  It takes me to some sort of recovery screen!  I was just going to try a system restore, but the site for the documentation is down too....
 
Can anyone point me to an alternate location for documentation a restore on a new Ratel box??
 
Thanks!
 
-SeanM

---

### Post by Lee_Machine on 2010-02-07
Kudos for getting the site back up so fast :P

---


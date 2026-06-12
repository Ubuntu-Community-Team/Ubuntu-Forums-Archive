---
title: "Ubuntu to backtrack conversion I NEED HELP !!!!!"
date: 2010-10-07
forum: Security
---

### Post by axor1337 on 2010-10-07
Ok so here is the deal I have been using Backtrack for a couple of years now as well as Ubuntu. but with being back in school I have also been using win 7. I am tired of having to use a Live version of Backtrack but really prefer the gnome interface of ubuntu along with some other features for an installed OS. iwant help converting Ubuntu 10.10 RC to Backtrack (or at least add 90% of the backtrack functionality. I am currently running Ubuntu via a Wubi install and I would replace Ubuntu with Backtrack but there is no Wubi for Backtrack. any help on either front is appreciated.

---

### Post by jwhendy on 2010-10-07
> **axor1337 said:**
> iwant help converting Ubuntu 10.10 RC to Backtrack (or at least add 90% of the backtrack functionality. I am currently running Ubuntu via a Wubi install and I would replace Ubuntu with Backtrack but there is no Wubi for Backtrack. any help on either front is appreciated.

Just my opinion, here, but I think other users would greatly appreciate if you could list the specific features you're looking for. Also, I haven't used Wubi, but it looks like just another way to run a virtual machine in Windows. What about just using [VirtualBox]("http://www.virtualbox.org/") and the ISO download of [Backtrack]("http://www.backtrack-linux.org/downloads/") to make a virtual machine install?

There's already [INSTRUCTIONS]("http://www.backtrack-linux.org/tutorials/dual-boot-install/") on installing BackTrack for dual booting Windows as well.

If you just want to add the packages necessary for Ubuntu to have BackTrack capabilities... I'd still suggest listing what it is that you want... just the stuff from the Wiki list of [TOOLS]("http://en.wikipedia.org/wiki/BackTrack#Tools")? Be more specific so others can help you. Your post seemed a little jumbled and confusing.

---

### Post by axor1337 on 2010-10-07
UM I want all the features! and NO Wubi is not a virtual machine. wubi creates a virtual hard disk the Ubuntu boots from instead of windows. the benefit of it is not needing to re partition the HDD. several people have said "just load Backtrack in a VM" the problem with it is that for true penetration testing that doesn't work. the VM method limits the ability to run certain apps I have reason I won't go into refusing to do a traditional dualboot.    the simple version is I want to load the Repo from Backtrack into Ubuntu10.10 and have it actually work. all the the walkthroughs I have tried fail at one point or another on 10.10.

---

### Post by jwhendy on 2010-10-07
Cool. By "load the Repo from Backtrack into Ubuntu10.10..." what is it that you mean? Add BackTrack functionality to Ubuntu?

Again, just list your specific features if you want specific help. I can't necessarily help you but think that if you're more specific, others will be able to chime in more easily.

For example, a clear statement like:

----
"I want the following to work in Ubuntu 10.10:
- aircrack-ng
- john the ripper
- feature x
- feature y"
----

will help out a lot.

---

### Post by BrokenFishCake on 2010-12-18
lol, necromamncer here, but who cares. Why don't you just install Backtrack to your disk, uninstall KDE, then install gnome?? that would make more sense than 'converting.'

if you want to do it  the long way, you could just install the hundreds of packages, configs, scripts etc into an ubuntu installation and change your repositories.

---

### Post by wcdrotar on 2010-12-19
I feel ya, but the Backtrack tools are best left where they are.  It'd be so much work to make them each compatible in Ubuntu that you'd be MUCH better off just booting a VM when you need it.  

I understand it's nice to have them, and you never know when you'll need a tool or when an idea springs up so you want them all available on a dime, but it's just not reasonable to do them individually each.  You can transport the big names over easily like Wireshark and 5nmp, Ophcrack, and so forth.  In fact some of them are in the Synaptic already.  

Do NOT replace KDE with GNOME!  (Or actually I guess you can since it's just a Live version).  You'll end up having to do a fresh install if you remove KDE.  

Backtrack now is essentially Ubuntu anyways, the only major difference besides GNOME is always being logged in as root (horrible idea, I think they keep it that way for security purposes so they're not just giving hackers this invincibility package).  

There's really nothing you can do about it.  My advice is to install packages or compile the programs you liked from Backtrack AS NEEDED, otherwise you'd be wasting an insane amount of time.  Or submit your work and I'll be happy to install all the Backtrack repo on Ubuntu since I miss it too.  

Good luck!  And the answer is no.

---

### Post by Lintnewbie on 2010-12-19
On the backtrack forum they specifically state not to use their repos and the wireless drivers is specific to their kernel. it might not all work.
 
[http://www.backtrack-linux.org/forums/frequently-asked-questions/1800-can-i-add-backtrack-repositories-my-ubuntu-other-distro.html](http://www.backtrack-linux.org/forums/frequently-asked-questions/1800-can-i-add-backtrack-repositories-my-ubuntu-other-distro.html)
 
fyi

---

### Post by barrieluv on 2010-12-19
For a Ubuntu 10.10+Gnome based solution, have a look at [Gnacktrack](http://www.gnacktrack.co.uk/).

---

### Post by c0rrupt0r on 2010-12-20
> **barrieluv said:**
> For a Ubuntu 10.10+Gnome based solution, have a look at [Gnacktrack](http://www.gnacktrack.co.uk/).

Thank you barrieluv this is just what I been looking for. works great

---

### Post by wcdrotar on 2010-12-21
Not bad, but at that rate why not just install Backtrack?  That's based in Ubuntu also.  

Now if someone had a package that would install all the tools on the distro of choice, that would be something spectacular.  Probably not coming anytime soon tho, unless we do it ourselves.

---


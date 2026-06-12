---
title: "Wine dissapeared"
date: 2010-02-12
forum: Wine
---

### Post by Roll FizzleBeef on 2010-02-12
Okay, so I ran update manager and was prompted to run a "partial update."  I followed the prompts, then restarted my computer.  I went to go play some starcraft, and nothing happened.  Upon further inspection I had found that wine was nowhere to be found!!!:-s

From what I can tell, Wine has been uninstalled, and yet the starcraft installation remains somewhat.  Can I just reinstall?  When I search for it, pieces of it remain, but not the whole thing.  Synaptic shows it but not all of its components installed.  

What happened????

---

### Post by Roll FizzleBeef on 2010-02-13
Bump

I ran "sudo apt-get remove wine" and got this"  > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmpg123-0 winbind binfmt-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.I ran "sudo apt-get install wine" and got this:  > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packagesI tried full removal and installation with synaptic, and all looked right, but to no avail.  There are a bunch of wine files on my system that I cannot remove.  It tells me I do not have permission to delete them.  WTF?  


Please help.




Edit: Sorry, forgot to mention, I'm running Xubuntu 9.10

---

### Post by Soulcage on 2010-02-14
Karmic uses wine1.2 not wine, wine is for upgrading from jaunty.
Atleast I think so on that last one.

---

### Post by Roll FizzleBeef on 2010-02-21
I am installing and uninstalling wine 1.2


BUMP!!!!


HELP ME!  PLEASE!  I WANNA PLAY STARCRAFT!!!!!!!!!   

C'mon, consider it a challenge to all you Linux gurus out there.

---

### Post by YokoZar on 2010-02-21
Can you start earlier?  This didn't start with just running update manager - what version of Ubuntu did you have installed?  How did you install Wine?  Did you enable a PPA?

---

### Post by Roll FizzleBeef on 2010-02-22
Xubuntu 9.10, as mentioned earlier.  Installed 1.2 through terminal.  I dunno.  

It started with update manager, whether you want to admit it or not.  

I figured it out on my own.  used synaptic to find that although they were uninstalled, I still had the option for "complete removal" of a few wine components.  Did that, then reinstalled without a hitch.  Thanks anyway.

---

### Post by YokoZar on 2010-02-22
> **Roll FizzleBeef said:**
> Xubuntu 9.10, as mentioned earlier.  Installed 1.2 through terminal.  I dunno.
Did you install a .deb package manually with dpkg?  Or did you just sudo apt-get install wine1.2?

> It started with update manager, whether you want to admit it or not.
Well yes, it broke when you ran update manager, but something else contributed to this.

I'm trying to figure out under what conditions exactly this happens, as it's not affecting everyone.  Which means that it's particular to the way Wine is installed, because a "partial upgrade" in update manager is just like running sudo apt-get dist-upgrade.

> I figured it out on my own.  used synaptic to find that although they were uninstalled, I still had the option for "complete removal" of a few wine components.  Did that, then reinstalled without a hitch.  Thanks anyway.
Complete removal clears out the package cache on your system.  If that worked, but reinstalling didn't, it likely means that for whatever reason the package you installed from originally was different from the one it got automatically when you reinstalled.  That's why I wanted to know about PPAs and such.

---

### Post by __lonewolf on 2010-02-24
well, it sounds similar to what happened to me.  here is the information if it helps.

ppa: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)

had ppa for wine enabled.  back a couple of updates to wine, had an issue with wine, so removed that version and installed a deb package.  it got fixed and I upgraded to that new version.  Same thing happened with the 1.1.38 release, so I did the same thing.  Each time I put in the deb package, I would get the partial updated upgrade message, when when doing that, would remove wine, plus the ia32 libs.  

I got 1.1.39 installed now.  I had to clean out the cache for apt-get and then I installed wine1.2.  Now everything is clean and working again.  

My theory is that having the ppa active and installing from the deb package, they where close enough that the symantic thought it was it's version and got confused.

if there is any other information, let me know.

---


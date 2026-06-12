---
title: "zynjacku and lv2rack for Karmic available"
date: 2009-12-27
forum: Ubuntu Studio
---

### Post by Scott L on 2009-12-27
As the title says, I've build zynjacku and lv2rack for Karmic and it's available in my ppa.

** Adding my PPA quick method:**
```
ppa:slavender/karmic
```**Adding my PPA more laborious:**
```
deb [http://ppa.launchpad.net/slavender/karmic/ubuntu](http://ppa.launchpad.net/slavender/karmic/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/slavender/karmic/ubuntu](http://ppa.launchpad.net/slavender/karmic/ubuntu) karmic main 
```and signing key
```
1024R/0020F80E 
```They appear to work as I started each application and inserted various effects but did not run any sound through them.  I would be very interested to hear any reports of success or failure using these.

Also it should be noted that these do not include desktop files so there will not be a menu entry at this point (but you can add one after installation by hand of course).  To be honest, I don't know how to add them yet when building the application.  I have run them from the terminal.

Regards,
Scott

---

### Post by s.Oliver on 2010-03-19
Hi,
i added your PPA to my repositories, installed both zynjacku and lv2rack with synaptic, but i have no idea how to start them. neither they are in the menu nor i can start them in a terminal.
what's wrong?
Thanks
s.Oliver

---

### Post by Scott L on 2010-03-19
Thanks for using my repository!

I did not get the .desktop file working when I made the PPA package.

However it is possible to run both applications from the command line but you must start the JACK daemon first.

If you have any other questions please let me know.

Regards,
ScottL

---

### Post by s.Oliver on 2010-03-21
thanks for your reply!


oliver@oliver-desktop:~$ zynjacku
zynjacku: command not found
oliver@oliver-desktop:~$ lv2rack
lv2rack: command not found

what do i have to enter to get them running?


s.Oliver

---

### Post by Capoeira on 2010-03-22
try /usr/bin/(software)

---

### Post by s.Oliver on 2010-03-23
doesn't work...

is it normal that these are the only files the application needs?

installed files of zynjacku:

/.
/usr
/usr/share
/usr/share/pixmaps
/usr/share/pixmaps/zynjacku.xpm
/usr/share/doc
/usr/share/doc/zynjacku
/usr/share/doc/zynjacku/copyright
/usr/share/doc/zynjacku/changelog.Debian.gz
/usr/share/applications
/usr/share/applications/lv2rack.desktop
/usr/share/applications/zynjacku.desktop
/usr/share/menu
/usr/share/menu/zynjacku

and there are no dependencies at all.


Thanks for reply
s.Oliver

---

### Post by Capoeira on 2010-03-23
i don't konw but try those comands:

/usr/share/applications/lv2rack.desktop
/usr/share/applications/zynjacku.desktop

---

### Post by Scott L on 2010-03-24
Sorry about that Oliver, apparently I borked the build..I'm guessing between switching between trying to build for Karmic and Lucid and also trying to get dh7 to build correctly.

Here is a new repository just for zynjacku and lv2rack:

ppa:slavender/zynjacku

or

deb [http://ppa.launchpad.net/slavender/zynjacku/ubuntu](http://ppa.launchpad.net/slavender/zynjacku/ubuntu) karmic main 

1024R/0020F80E


I installed a fresh Ubuntu Studio Karmic on a new partition to test this out and it worked.  Start JACK first as mentioned before.  However, since I took my source code from Lucid to build for Karmic you have the added benefit of menu entries.  Both 'zynjacku' and 'lv2rack' should both be under 'Sound & Video' menu (instead of the 'Audio Production' submenu).

Please let me know if this works.

Regards,
ScottL

---

### Post by s.Oliver on 2010-03-25
:D yeah!
they both are working, and they both have a menu entry!


thanks a lot! you're the best ;)!

---

### Post by Scott L on 2010-03-25
I'm very glad that it is working now.

I was working towards getting zynjacku and lv2rack into the archives for Lucid but fell short.  Therefore, I'll make sure my ppa has working builds for Lucid as well.

And hopefully, zynjacku and lv2rack will be accepted for Lucid+1.

And now I can delete that Karmic partition and move back into testing the beta1 for Ubuntu Studio Lucid again.

Oh, and if there are other applications you would like to see, either in Ubuntu Studio or in ppa, please let me know or email the developer mailing list at [EMAIL="ubuntu-studio-devel@lists.ubuntu.com"]ubuntu-studio-devel@lists.ubuntu.com[/EMAIL].

Regards,
ScottL

---

### Post by AutoStatic on 2010-03-25
> **Scott L said:**
> And now I can delete that Karmic partition and move back into testing the beta1 for Ubuntu Studio Lucid again.Why not use a chrooted Karmic install? Or do you desperately need the space? Just curious :)

---

### Post by Scott L on 2010-03-25
> **AutoStatic said:**
> Why not use a chrooted Karmic install? Or do you desperately need the space? Just curious :)

A little explanation to answer your question.

I didn't have a Karmic install of Ubuntu Studio on this machine.  I currently record using Hardy still and am transitioning to Lucid as I test it.

And since this machine is a P4, which I found doesn't handle VM very well, I tend to make partitions to install and test.

If I were only building a package I would use pbuilder for Karmic, but actually in this case I had already built the package in Lucid so I eschewed testing building locally and opted for revising the changelog and sending it to my ppa to build.

Essentially, the Karmic install was only used as an acid test for the build, but I felt confident about it.  It also afforded me a chance to troubleshoot if the build failed to work again.

---

### Post by tehk on 2010-07-05
Thanks for the PPA!

How about a Lucid and Maverick PPA as well? Using Lucid myself and just installed from the Karmic with np.

+2 and cheers!

---


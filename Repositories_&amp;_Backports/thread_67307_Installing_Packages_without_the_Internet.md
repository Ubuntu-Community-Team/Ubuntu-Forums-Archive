---
title: "Installing Packages without the Internet"
date: 2005-09-19
forum: Repositories &amp; Backports
---

### Post by icelizarrd on 2005-09-19
Hi, my apologies if this is in the wrong section -- and my apologies also because a similar topic has been covered in previous forum posts, but I wasn't able to find the exact answer I need.

Anyway, I installed Ubuntu on an old Grape iMac.  Installation went great, no problems, actually probably the easiest install I've had yet with a Linux distro. But, since my computer is so ancient, I decided to try the minimal server install and then downloading IceWM (or XFCE) and some other apps.  

Server install went great, but here's my problem: the college I'm at has an authentication process for their network.  Before they allow you to access anything else on the network or internet, you must send an HTTP request for some site or other, which will redirect you to the login screen.  Unfortunately, of course, there's no browser included with the minimal install (as far as I know, that is?).  And I can't access the internet to download one until I've done the authentication process. Hence my problem.

So, I discovered that you can download packages manually from [http://archive.ubuntu.com](http://archive.ubuntu.com), but a few glances at all the insane amount of necessary package dependencies (which each depend, in turn, on yet more packages) for installing the X System Core convinced me of the folly of this route.

I need some way of getting a working browser onto the computer which won't require downloading thousands of other dependencies.  Or, if it does, then I need a way to calculate this list ahead of time rather than searching individually through the [http://packages.ubuntu.com](http://packages.ubuntu.com) site (i.e., I need a way to calculate ALL dependencies automatically, not just what each individual package depends on).

Links, which I had installed when the system was running Gentoo, does not work with the college's authentication process (don't know why... perhaps it doesn't support https?).  Firefox does.  Don't know about Lynx, but since it's so similar to Links, I doubt it would work.

I would highly appreciate any suggestions.

Perhaps I could send a spoofed HTTPS login using the iMac's MAC address and ip? =P (Heh, not that I'd really know how to do this, or if it'd work).

---

### Post by aysiu on 2005-09-19
Mozilla has a Firefox .tar-ball that you can download and install completely graphically (you don't need the command line).

Just double-click the .tarball
Extract.
Double-click *firefox-installer* and go through the wizard.
*firefox* starts the program (different from *firefox.bin*).

---

### Post by icelizarrd on 2005-09-20
Well, thanks for your help, but I've realized that I can still apt-get packages from the CD.

So I've installed x-window-system-core and firefox from CD.  But attempting to run Firefox gives me the following error:

"Gtk-WARNING **: cannot open display:"

Am I missing something else essential (such as the gtk libraries? ...which I thought that the Firefox package already installed) Do I need to have a window manager installed for Firefox to run?

Thanks for help in advance.

---

### Post by icelizarrd on 2005-09-20
*Rolls eyes at self*

Well, I apparently solved my problem now.  Just had to mess around enough to get Firefox to run...

So, I don't need any help after all.  For now. =P

---


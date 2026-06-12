---
title: "Virtualbox OSE to closed source..."
date: 2009-05-20
forum: Virtualisation
---

### Post by javyn999 on 2009-05-20
Hey all.  I'm running a Windows XP guest inside Vbox OSE.  I would like to set up MS Outlook in the guest OS so I can sync my Blackberry contacts and calendar with it inside the Windows virtual machine.  

Come to find out, the OSE version of Virtualbox doesn't support USB connections to the guest OS.

When I first installed Ubuntu, I tried uninstalling Virtualbox OSE through syntapic, then I installed Virtualbox which I downloaded from the web. 

I went to Applications > Accessories, and apparently the closed source Vbox I downloaded didn't put a shortcut icon in my menu after it installed.  So I removed it, re-installed Virtualbox OSE, and went merrily on my way.

Well, now, I really do want to keep the closed source Vbox b/c of  the reason previously mentioned.

How would I go about setting it up so I can actually run the closed source Virtualbox from my App menu once it is installed?

Also, if I remove OSE and replace it with closed source, does this mean I will lose my current vdi guest OSes?  

Appreciate any help!

---

### Post by pratekin on 2009-05-20
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Follow the commands below were you download the .deb and it should replace the ose version with the version that supports usb.  It should also import your virtual drive, but just in case, you can back it up.  It is a hidden folder in your home folder.  It is named .VirtualBox.  Back that up and you should be fine.

---


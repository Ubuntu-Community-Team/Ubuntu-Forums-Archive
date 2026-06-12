---
title: "VirtualBox guest addition iso problems"
date: 2011-10-30
forum: Virtualisation
---

### Post by Alexander83 on 2011-10-30
Hello everyone,

I can't install the guest additions in the normal way because the download path can't be found. I get the following error, preceded by some German message saying pretty much the same thing:

Error downloading [http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso) - server replied: Not Found

The reason for this is that the real path is
[http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2/VBoxGuestAdditions_4.1.2.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2/VBoxGuestAdditions_4.1.2.iso)
without the "_Ubuntu". So to install it I need to
a) change the path where VirtualBox looks for the file, which I don't know how to do
b) download it manually and
b1) copy it into one of the 2 folders where VB looks for it first, i.e. usr/share/[...] or usr/lib/[...] (where I don't have writing permission apparently and since I'm completely new to Linux I don't know much about writing permissions).
b2) tell VB to look in a different local folder, i.e. the one I downloaded the iso to, which I don't know how to do either.
c) mount the iso into the CD of the VM manually, which finally worked!

I'm just posting this in case anyone else has this problem.

Do you think I should propose to the creator of VB to add functionality which allows the user to change the paths (local and internet) where VB looks for the iso or is there an important reason why this isn't possible?

Btw: I have Ubuntu 11.10 and VB 4.1.2 installed.

Kind regards,
Alex

---

### Post by memilanuk on 2011-10-30
Is there some reason the normal guest additions that comes with Ubuntu isn't working for you?

I was kind of surprised myself when I re-installed 11.10 and had some issues with the guest additions iso not being found, but it turned out that (for whatever reason) when I installed Virtualbox 4.1.2, it did *not* by default install the guest additions - I had to go in and manually check that box and update it.

---


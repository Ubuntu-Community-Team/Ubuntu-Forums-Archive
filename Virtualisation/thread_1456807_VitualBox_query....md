---
title: "VitualBox query..."
date: 2010-04-17
forum: Virtualisation
---

### Post by Baldrick_NZ on 2010-04-17
OK, so I've had a quick check thru previous postings and haven't seen a similar one to this..

I installed VB (and guest additions) from synaptic and then loaded XP as my guest. It installed well, but I seem to have to delve under several layers of files to see my external drive under windows explorer. Shouldn't this drive just show up as a "D" or "E"? Or, even under "Guest Additions (D)"?

Secondly, how can I see and access the guest drive (when VB is running) under Ubuntu? IE: Is there a way I can see the Ubuntu drives under XP through VB, and/or the other way round?

This would be handy to know as I use iTunes to download music from XP, but then I'd like to move them across to my Ubuntu music folder directly, without having to move them to my external drive and then to my music folder.

I hope this makes sense!

Cheers.

---

### Post by MattTastic on 2010-04-17
Well I am not so sure about your hard-drive problem, it should show up as a removable media drive, D/E/F...etc You are loading them on correctly?

Having them plugged into usb, unmounting them on host (ubuntu) and then clicking on the little usb icon on the bottom of the Vbox window and adding usb device?

As for sharing the ubuntu drive... well I guess you could what I do though is use the share folder facility. You click on the folder icon on the bottom panel on Vbox window running XP, you'll get a dialog box pop up add a folder from Ubuntu say Desktop then go into your guest (windows) and go to the command line...

Then run a command like:

Command line network tool for windows.
\/         The drive letter you are going to use
\/         \/
net use x: \\vboxsvr\Desktop

And you should be rolling after that. Of course you can use whatever Ubuntu folder on your system you like.

---


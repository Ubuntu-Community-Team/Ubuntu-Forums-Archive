---
title: "transfering Windows XP from one computer to VirtualBox on an Ubuntu system"
date: 2013-01-16
forum: Virtualisation
---

### Post by majorburt on 2013-01-16
hopefully i have the right place for the thread this time lol.

my goal is to transfer the XP operating system from a Sony VAIO laptop on to either my desktop computer or (preferably)onto Virtualbox itself.

would this be at all possible? and if so, can the OS be "cloned" onto Virtualbox and leave the XP laptop fully functioning? 

i have a good hard-drive adapter so capability isn't a problem. 
i also have an external hard-drive if a "middleman" hard-drive is required for some reason.

any details for either computers can be provided upon request.



thanks in advance for all the help!

---

### Post by leclerc65 on 2013-01-16
I have a suggestion, don't blame me if it doesn't work.
Use a program like k9copy or Imgburn (Windows) to make an ISO out of the files in your Windows C drive, then mount the ISO in Virtual Box.

---

### Post by CharlesA on 2013-01-16
> **leclerc65 said:**
> I have a suggestion, don't blame me if it doesn't work.
Use a program like k9copy or Imgburn (Windows) to make an ISO out of the files in your Windows C drive, then mount the ISO in Virtual Box.

Wouldn't work.

@OP: It is highly unlikely that will work, but you could try it. My bet is it will not even boot - probably blue screen when it tries to access the hard drive.

Even if it does work, you would still need two licenses - one for the laptop and one for the vbox instance of XP.

---

### Post by majorburt on 2013-01-16
> **CharlesA said:**
> Wouldn't work.

@OP: It is highly unlikely that will work, but you could try it. My bet is it will not even boot - probably blue screen when it tries to access the hard drive.

Even if it does work, you would still need two licenses - one for the laptop and one for the vbox instance of XP.

still worth a try even if its just to get the proverbial gears turning. 

might end up trying it tomorrow. i'll be back with results as soon as i can.

---

### Post by brusegadi on 2013-01-16
You could try dd the image of the disc onto a vdi file stored on an external hard drive with enough space.  I doubt these boot the same way, so the virtualization software may not be able to boot it.  I also have no idea about hardware issues.  That said, I also found:


[http://www.makeuseof.com/tag/create-a-virtual-machine-image-of-your-existing-hard-drive-windows/](http://www.makeuseof.com/tag/create-a-virtual-machine-image-of-your-existing-hard-drive-windows/)

Good luck!

---

### Post by majorburt on 2013-01-16
> **brusegadi said:**
> You could try dd the image of the disc onto a vdi file stored on an external hard drive with enough space.  I doubt these boot the same way, so the virtualization software may not be able to boot it.  I also have no idea about hardware issues.  That said, I also found:


[http://www.makeuseof.com/tag/create-a-virtual-machine-image-of-your-existing-hard-drive-windows/](http://www.makeuseof.com/tag/create-a-virtual-machine-image-of-your-existing-hard-drive-windows/)

Good luck!

now that looks like it could work.
do you know if i can select which parts of the hard-drive to create an "image" of? 
i don't think i gave enough space for the entirety of another computer's files on my hard-drive.:(

---

### Post by brusegadi on 2013-01-16
I dont know.  I would try parted magic or gparted to resize the windows partition before doing the move.  That said, I have never resized a partition to make it smaller (only bigger, it was a virtual disk, so I could increase the size of the HD and not steal from another partition) so I dont know the issues you might encounter.  Good luck!

EDIT  check out    [http://partedmagic.com/doku.php?id=using_gparted](http://partedmagic.com/doku.php?id=using_gparted)

---

### Post by majorburt on 2013-01-17
> **brusegadi said:**
> I dont know.  I would try parted magic or gparted to resize the windows partition before doing the move.  That said, I have never resized a partition to make it smaller (only bigger, it was a virtual disk, so I could increase the size of the HD and not steal from another partition) so I dont know the issues you might encounter.  Good luck!

EDIT  check out    [http://partedmagic.com/doku.php?id=using_gparted](http://partedmagic.com/doku.php?id=using_gparted)

no, i meant actual space. i only have about 300 gig (about half of max) left. 

i'll try to get on this whole project today as soon as possible.

---

### Post by brusegadi on 2013-01-17
Well, I am assuming that your windows installation has its own NTFS partition.  If that is the case, delete anything you dont need and resize the partition.  That way the resulting virtual hard disk will be smaller.  If you run into a space constraint, then there is little you can do about that.  Good luck.

---

### Post by coldraven on 2013-01-17
If it's an OEM install on the Sony I don't think it will be possible.
If you try using a Windows restore disc in a different brand PC it will not work because it looks into the BIOS for manufacturer information etc.
With such a disc you could trick Windows into installing in a virtual machine on your desktop but you would be in breach of the EULA . Forum rules dictate that  I cannot tell you how to do it. Try the Virtualbox forum instead.

---

### Post by sdpagent on 2013-01-18
Here's what I would do.

[LIST=1]
[*]Move all your data from the xp machine. (probably to the ubuntu machine)
[*]Find the licence on the bottom of your laptop and copy it. (taking note which kind of xp it is)
[*]Install xp in virtualbox using that licence. You will need to 'find' the ISO of that particular xp, ie. 'home' or 'media' editions do matter, however you dont need to worry about which SP though really.
[*]Install over the top of your laptop with another OS such as Ubuntu. (this avoids the two licence issue)
[*]Move the data back onto your xp machine. (virtualbox shared folder? windows xp doesnt have my favourite budy ssh/scp)
[/LIST]
I believe this is all completely legal. One licence of windows remains in use. I'm not sure how legal it would be to torrent a copy of xp as long as you are using a licence you paid for....

---

### Post by majorburt on 2013-01-20
thanks for all the help guys!!!

after weighing my options and trying a few of the suggestions, i have decided to try to track down a windows XP disk use that instead. 

XP was OEM on the laptop and i cant't find half the stickers on it (VERY used computer) and so i don't think i'll be able to get it to run even if i successfully image the windows files.

i'll mark the thread as solved but if any of you have an idea that could still word, feel free to comment.

---


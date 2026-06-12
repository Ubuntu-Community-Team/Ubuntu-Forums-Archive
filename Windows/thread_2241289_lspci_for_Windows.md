---
title: "lspci for Windows"
date: 2014-08-25
forum: Windows
---

### Post by Dragonbite on 2014-08-25
I was just fixing a friend's computer that wouldn't boot. So I was there with him and Ubuntu for the rescue:[LIST=1]
[*]proved the motherboard and hardware was working by booting to CD and then to USB
[*]proved the hard disk was still working because could navigate through it and pick out files
[*]allowed copying the files in /Users to a USB drive so didn't have to worry about losing them all (he had no backups)
[*]provided information on the system (video, etc.)
[/LIST]

After re-installing Windows (Repair and Restore both failed) I realized that I needed to find out what his video card was for getting the proper drivers for it.  

I don't know of any means to determine this from within Windows, so I ended up booting back into Linux and running #lspci and writing down the results.

Does anybody know of a means to do in Windows what 'lspci' does?

Best choice would be something that is built-in for Windows, but 3rd parties are better than nothing (but probably not as good as running lspci in linux ;) )

---

### Post by deadflowr on 2014-08-26
Does anything here help
[http://support.microsoft.com/kb/300887](http://support.microsoft.com/kb/300887)

---

### Post by fyfe54 on 2014-08-26
Install Ubuntu?

---

### Post by deadflowr on 2014-08-26
> **fyfe54 said:**
> Install Ubuntu?

I think that misses the point of the question.

---

### Post by Dragonbite on 2014-08-27
> **deadflowr said:**
> Does anything here help
[http://support.microsoft.com/kb/300887](http://support.microsoft.com/kb/300887)

Thanks!  I'll have to try it on his machine.  

I tried it here (at work) and went into **Components** >> **Display** and it shows me the video adapter's information (which is via VMware SVGA 3D).  I'm not sure if it will show me the information if it does not know what the device is.

I wonder what it shows under the **Components** / **Problem Devices**?  

This actually may be a good thing to check out because it showed another device being unknown and I don't know what it is (or whether it is the Video adapter showing up 2x).

---


---
title: "Lost XP"
date: 2007-02-10
forum: Ubuntu Christian Edition
---

### Post by HareBall on 2007-02-10
I know this doesn't sound like a big deal, but I lost XP in my GRUB. I need to be able to access XP to print and it doesn't show up anymore. I haven't checked it in about 2 weeks. This morning I tried to reboot and it wasn't there. I have updated my computer just about every morning this week with the updates they have been sending out.
I tried to remove my second drive(Ubuntu) and reboot without it in, but I got an error number 21 I believe. Wouldn't boot at all without my Linux drive in.
I really need to have this access. I have important tax info on that drive and am trying to get it done.:(

---

### Post by mysticrider92 on 2007-02-11
First, check /boot/grub/menu.lst in Ubuntu and see if there is a section for Windows still there. From the error, it looks like Grub is looking in the wrong place forthe hard drive. Make sure that the root   (hd*,*) is the correct drive/parition.

If there is no entry, you will need to add a section to the end of the list. Here is what I have for Windows:
> title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

On the root section, you will need to change the hard drive to match your computer (hd0,0 is the first partition of the first physical hard drive).

Also, Grub would be installed on your Linux drive, so without it, Grub won't boot, but I don't know why the XP drive won't work unless the BIOS is configured wrong.

---

### Post by HareBall on 2007-02-12
> **mysticrider92 said:**
> First, check /boot/grub/menu.lst in Ubuntu and see if there is a section for Windows still there. From the error, it looks like Grub is looking in the wrong place forthe hard drive. Make sure that the root   (hd*,*) is the correct drive/parition.

If there is no entry, you will need to add a section to the end of the list. Here is what I have for Windows:

On the root section, you will need to change the hard drive to match your computer (hd0,0 is the first partition of the first physical hard drive).

Also, Grub would be installed on your Linux drive, so without it, Grub won't boot, but I don't know why the XP drive won't work unless the BIOS is configured wrong.
I got this taken care of.
Thanx anyway.

---

### Post by doobit on 2007-02-12
> **HareBall said:**
> I got this taken care of.
Thanx anyway.

What caused the problem and how did you fix it?

---

### Post by HareBall on 2007-02-13
> **doobit said:**
> What caused the problem and how did you fix it?
Turned out it wasn't really a problem. When the GRUB screen came up, it just wasn't able to show all of my options. I had to hit page down to see the XP option.
I did however edit my GRUB menu to hide some of the kernal options. I did this by going here [http://users.bigpond.net.au/hermanzone/p15.htm#hide_items](http://users.bigpond.net.au/hermanzone/p15.htm#hide_items). Really helped a lot. I was starting to get a whole lot of kernals showing that I don't use anyway.
That page has a lot of helpful stuff about your GRUB menu:KS

---

### Post by shane2peru on 2007-02-13
Are all of these kernels in your Ubuntu distro?  If you don't use them you can un-install them and save yourself some disk space.  However if you like collecting them, you can keep them.  :lolflag: 

To uninstall them just open Synaptic and do a search on kernel, it will show you what kernels are installed.  Just select remove for the kernels you don't use.  You may want to write the number of the kernel down that you are using so you don't accidentally select that kernel.  ;)   Hope that helps.  That will also clean out your menu.lst too.

Shane

---

### Post by HareBall on 2007-02-14
> **shane2peru said:**
> Are all of these kernels in your Ubuntu distro?  If you don't use them you can un-install them and save yourself some disk space.  However if you like collecting them, you can keep them.  :lolflag: 

To uninstall them just open Synaptic and do a search on kernel, it will show you what kernels are installed.  Just select remove for the kernels you don't use.  You may want to write the number of the kernel down that you are using so you don't accidentally select that kernel.  ;)   Hope that helps.  That will also clean out your menu.lst too.

Shane
I went and did a search for kernel and didn't see anything that was highlighted. They weren't showing up for me.

---

### Post by shane2peru on 2007-02-14
HareBall,

  Sorry about that my directions were not really clear.  I should have checked them out better.  Here is what you need to do.  After you know what kernel you want to keep.  Open Synaptics, and do a search for 'linux-image'  that will really narrow the results.  You can use kernel too, however this will really narrow the field down.  Ok, see how there are columns in the top the first one is an empty box, not the box for the first item, but the box for the very top, next to it is another empty box, and then **Package | Installed Version | Latest Version ...**, if you click on the first column empty box, it will sort all of them by what is installed and what is not installed. Now scroll down the list until you see the green boxes instead of white boxes beside the package name.  Everything in green is installed.  Click the green box that you want to get rid of and mark it for complete removal.  Sorry I wasn't clear the first time around, I usually use the command line, or terminal.  If you don´t have any extra linux-images then we need to edit your menu.lst, but it should do that as kernels are removed, it should automatically remove them from your menu.lst.  Hope this helps!  

Shane

---

### Post by HareBall on 2007-02-14
> **shane2peru said:**
> HareBall,

  Sorry about that my directions were not really clear.  I should have checked them out better.  Here is what you need to do.  After you know what kernel you want to keep.  Open Synaptics, and do a search for 'linux-image'  that will really narrow the results.  You can use kernel too, however this will really narrow the field down.  Ok, see how there are columns in the top the first one is an empty box, not the box for the first item, but the box for the very top, next to it is another empty box, and then **Package | Installed Version | Latest Version ...**, if you click on the first column empty box, it will sort all of them by what is installed and what is not installed. Now scroll down the list until you see the green boxes instead of white boxes beside the package name.  Everything in green is installed.  Click the green box that you want to get rid of and mark it for complete removal.  Sorry I wasn't clear the first time around, I usually use the command line, or terminal.  If you don´t have any extra linux-images then we need to edit your menu.lst, but it should do that as kernels are removed, it should automatically remove them from your menu.lst.  Hope this helps!  

Shane
OK, I did this. Now I'll see what happens the next time I reboot.

---

### Post by HareBall on 2007-02-14
> **HareBall said:**
> OK, I did this. Now I'll see what happens the next time I reboot.
Works good. :guitar:  Thanx Shane.

---

### Post by shane2peru on 2007-02-14
Great, glad to hear it!

Shane

---


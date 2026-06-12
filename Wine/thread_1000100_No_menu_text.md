---
title: "No menu text"
date: 2008-12-02
forum: Wine
---

### Post by sjbaugh on 2008-12-02
I had some radio frequency interference whilst using a windows program under Wine. The result is that, whilst programs appear to run correctly, all the menus and button/control text is blank (apart from some underscores). Some text in applications appears but characters are overlapping making it impossible to read.

To try and fix this I have tried (in various orders):

installed msttcorefonts
Uninstalled Wine (complete removal)
Deleted .wine directory
Re-installed Wine (1.0.1 from repository (universe/otherosfs))

I have tried to run Notepad after the re-install (all the other apps went when I deleted .wine) with the same (no menu/control text) and when I type in it characters seem to appear very briefly and then go away, leaving a blank text area (the cursor displays and moves along).

I am using Intrepid 32 bit.

Any ideas what I can try next?

Steve

---

### Post by iOverflow on 2008-12-02
Have you enabled any Visual Effects for your desktop?

What graphics card do you have?

Are the graphics perfectly operational?

---

### Post by sjbaugh on 2008-12-02
I had Normal visual effects set.

I have now disabled visual effects with the following consequences:

Text in the Notepad window now appears.
Menu/control text now appears but is overlapped (it is just readable sometimes).

Video card is an nvidia MX440. I am using the restricted driver (version 96). Linux applications work correctly (now and before).

---

### Post by iOverflow on 2008-12-02
Hmm are you using this driver at the moment?
[http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)

And also did you install any previous drivers?

---

### Post by sjbaugh on 2008-12-02
When I installed Ubuntu (clean install, there was no previous version of Ubuntu) I used the driver which wa installed at this time. A update came up saying there was a restricted driver (version 96, Recoomended) so I installed this. Since your last message I have been into System>Administration>Hardware Drivers and De-activated this driver (no change to effects). It now says that a different version of this driver is in use (does not say what version). I have gone into Nvidia X server Setting and this reports the driver as being 96.43.09.

I there a way to get back to a generic driver?

I could try a complete re-install of Ubuntu as there is not much on this machine (it is not my main PC)

Thanks for your patience,

Steve

---

### Post by iOverflow on 2008-12-02
hmm apparently driver 96.43.09 had a bug,
There is 2 fixes apparently for this:

# Downgrade the driver to 96.43.07, if possible
# Or put the following into the Device section of your xorg.conf, at the expense of slower 2D drawing  

Option "RenderAccel" "0" 

-For further information on this go to this site
( [http://forum.compiz-fusion.org/showthread.php?t=10304](http://forum.compiz-fusion.org/showthread.php?t=10304) )

---

### Post by sjbaugh on 2008-12-02
Yes, that looks like the same bug. I have had this working, I don't use this machine much (only to run radio apps that are ony available under Windows) so it may have been before I installed the restricted driver. I will see what I can do.

Thanks again,

Steve

---

### Post by sjbaugh on 2008-12-02
I had no joy with:

Option "RenderAccel" "0"

So I have re-installed Ubuntu from scratch without installing the restricted driver, and now that I have installed Wine (1.0.1) on this new install everything is working fine. I am tempted to install the restricted driver and see what happens, but if it ain't broke...

Thanks,

Steve

---


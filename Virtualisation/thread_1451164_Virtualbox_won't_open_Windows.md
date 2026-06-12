---
title: "Virtualbox won't open Windows"
date: 2010-04-10
forum: Virtualisation
---

### Post by asharpham on 2010-04-10
I have Windows XP Pro installed in vitualbox with Ubuntu 9.10 host. When I click "Start" on Sun Virtualbox, the black window opens but nothing else happens. It just sits there with a black rectangle on the screen. Will i need to reinstall Windows in the virtualbox? If so, how do I uninstall the current installation? Will removing the .Virtualbox folder do this?

---

### Post by howefield on 2010-04-10
Was XP previously working and all of a sudden is now not, and what version of Virtualbox are you using ?

---

### Post by jerenept on 2010-04-10
Try Changin the operating system selection in vbox from "Windows XP" to "Other Windows"

---

### Post by SecretCode on 2010-04-10
Do you get the Virtualbox splash screen (usually lasts about 2 seconds)?

And then just a black screen - no error message like 'Non-system disk' or anything?

Could it just be power-saving in the vm? - Click inside the vm window, move the mouse around, press a key or two.

---

### Post by asharpham on 2010-04-10
To answer the last 3 questions: yes, XP was working fine in virtualbox but now isn't. I tried changing the OS type to Other Windows but it made no difference. Yes, the virtualbox splash screen comes up for a few seconds then it goes to black, changes shape and then just sits there with WinXP not loading. I'm sure it's not just power saving as I've only just opened the window. Anyway, when it was working before, the default screensaver would operate first. No error messages.

Also I have reinstalled Sun Virtualbox but that made no difference. I don't mind reinstalling Windows as I haven't installed anything much since loading Windows but I'd like to know if there's anything I can do to fix it before doing that.

---

### Post by SecretCode on 2010-04-11
If you're not getting any message or graphics from the installed XP, I'd go ahead and reinstall it.

First, you could ...
- load an Ubuntu Live CD iso into the virtual CD drive, boot to that, mount the virtual hard drive (it should automatically detect and support the NTFS format) and rescue any data
- load the XP iso and try a repair install

---

### Post by asharpham on 2010-04-11
I tried the last suggestion but the window remained black and the Ubuntu Live CD didn't load. So I've decided to reinstall Windows XP again, wiping the old installation. I'm not really losing anything as I had very little installed.

---

### Post by wilee-nilee on 2010-04-11
In the latest Sun Vbox I have just saved the vdi and have started it on W7 virtual or Ubuntu's no problem by just loading the vdi into the virtual media managers hard disc. I you look there it may just be unattached or didn't get reloaded with a reinstall.

I have done this switching with XP/W7/Lucid.

---

### Post by asharpham on 2010-04-12
What is the vdi and where do i find it?

---

### Post by wilee-nilee on 2010-04-12
> **asharpham said:**
> What is the vdi and where do i find it?

vdi is the hard disc file created when you create a virtualbox machine look in virtualbox-file media manager click on hard discs and you will see it there. Where it actually is so you can save it is in .virtualbox-folder- hard discs in home, it is hidden hit ctrl-h to show hidden files.

So you can save this vdi so that in case you need it as a backup and use it. This is not the normal way to save and reload Vbox but I find it works for me.

So you might just try releasing all the attachments of XP to Vbox, and then just add the vdi back on in the media manager make a new machine and if it is a working vdi and nothing has actually gone wrong in there it should boot.

Now if you have made snapshots you can delete them starting at the top and they will merge with the current system, XP has to be off to do all of this. Do this before trying to release, it wont unless you do I believe.

In the end if you have nothing to lose messing around might be helpful to understand Vbox more, but hey do a reinstall if that is the most efficient move.

---

### Post by asharpham on 2010-04-12
"Fiddling" is what causes me a lot of trouble. That's why I prefer to ask in these forums, even if it seems a simple question. Thanks for giving me some advice. This time I'll reinstall XP as I have very little to lose and nothing that I can't get back. But I'll keep your reply handy by copying and pasting it into a text file - just in case!

---

### Post by wilee-nilee on 2010-04-12
> **asharpham said:**
> "Fiddling" is what causes me a lot of trouble. That's why I prefer to ask in these forums, even if it seems a simple question. Thanks for giving me some advice. This time I'll reinstall XP as I have very little to lose and nothing that I can't get back. But I'll keep your reply handy by copying and pasting it into a text file - just in case!

Yes my first try at Ubuntu was 3 years ago with dapper I had to reimage my computer 3 times in the 1st 6 months, never looked back though.

---

### Post by asharpham on 2010-04-13
Just out of interest, have you updated Ubuntu with the later versions as they became available, and if so, did you run into any problems?

I was advised from the start NOT to run the updates that arrive every day. In past when I have ignored this instruction, I ran into loads of trouble with things not working and therefore having to reinstall Ubuntu. So having learnt my lesson, I never update these days.

---


---
title: "[SOLVED] Mouse captured in Virtual Box! Help!"
date: 2008-08-27
forum: Virtualisation
---

### Post by randykelli on 2008-08-27
I have had trouble with virtual box capturing my mouse and not letting go, even when I press the right control button. I can't get out!:confused:  All I am able to do is shut down the WinXP in the VB. My host is Ubuntu Hardy.  

I did not have this problem until I followed instructions, [here]("http://ubuntuforums.org/showthread.php?p=5224346"), to get VB to recognize my usb flash. (It works great now! Thanks to docplastic!)  Could that have caused it, you think?  Whatever anyone knows will be helpful.

---

### Post by Masoris on 2008-08-28
Push host key (Right Ctrl is default)

---

### Post by leepesjee on 2008-08-28
Have you installed the guest-additions?
Mouse-capture shouldn't be an issue after that.
Leo.

---

### Post by randykelli on 2008-08-28
Unfortunately, I have not yet installed guest additions, so the cursor doesn't move through.  It is captured in WinXP limbo with no way out that I can find.  The right control button obviously isn't working.  The other nasty thing is that Linux's screensaver kicks in after 10 minutes as well!  [Easily disabled, though.]  Yaaaa!  My computer is in WinXP prison!  Who can help here?      :-?

---

### Post by randykelli on 2008-08-28
Does anyone know how to install "guest-additions" from the command line?  This way, in theory, the mouse should be freed to go out of Virtual Box from WinXP to Ubuntu.    :idea:

---

### Post by leepesjee on 2008-08-31
You can do it from within the virtual machine:
Devices - Install Guest additions

I don't know if it's possible from the command line.

---

### Post by randykelli on 2008-09-02
I figured out the problem!! Hopefully, this will help someone else save many hours of work. In my case, I went to the virtual box details and clicked on USB. I noticed that I had a filter for USBPC2 installed. It was locking up my mouse and apparently not necessary. I uninstalled it and now everything is coming up roses!    :)

Attention: only use the following if the above doesn't work.  If the above works, this is not necessary!  

In the midst of my problems (with no mouse control), I did get my guest additions installed by using the "iso" file that came with the Virual Box install. It can be done without having to go to the much easier 'Devices' menu in VB after the guest OS comes up.  WIKI: in VB dialog's 'Details' tab, click the CD/DVD-ROM drive.  Then mount the "iso" in the box that comes up.  In my system, the path to the .iso was /usr/share/virtualbox, just in case someone else needs it.

---

### Post by paddygman on 2009-03-11
Hey all, 
Had a similar issue, my control key didnt kick the mouse back to normal desktop. I found that if i held down the shift key, it first tried to turn on the windows sticky keys and then the ubuntu sticky keys. When the ubuntu prompt appeared, i was free.
Now to install the additions that i had forgotten.

Hope this helps

Random

---


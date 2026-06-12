---
title: "How to stop a window manager?"
date: 2009-04-13
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-04-13
Thanks to a response to my "how to start a window manager?" thread, I got XFCE running.

Unfortunately it started at a resolution not supported by my monitor.  Can anyone tell me how to kill the XFCE process without being able to see anything on the screen?

And, if possible, how to re-start it at a lower resolution?

Thanks!

---

### Post by mltucker on 2009-04-13
Hello,

Press Ctrl-Alt-Backspace to log out from X.

-Mark

---

### Post by mltucker on 2009-04-13
Once you've logged out, what is in your /etc/X11/xorg.conf?

---

### Post by Nixie Pixel on 2009-04-13
Hmm, I'm frozen on "waiting for X server to shut down."

---

### Post by mltucker on 2009-04-13
OK -- 

1. Press Ctrl-Alt F1.

2. login

3. Run "top"

```

>> top

```

4. Find the PID (left column) that matches up with Xorg (should be at the top since it uses a lot of memory).  Mine is 4807.

5. sudo kill [your Xorg PID]

X might restart at this point.  If so, try to logout again, or just go back to the CLI and configure it to a native resolution for your monitor.

-Mark

---

### Post by Nixie Pixel on 2009-04-13
Hmm, with CTRL-ALT-F1 all I get is a beep from the system speaker and a blinking cursor in the upper-left of the screen (with no text being replaced).

I think I hosed my server somehow :P

---

### Post by RuleMaker on 2009-04-13
Never kill your window manager, it will freeze your system.
Just temporarily replace it with another WM.
For example, metacity:
Alt+F2 and type
metacity --replace

---

### Post by Nixie Pixel on 2009-04-13
> **mltucker said:**
> If so, try to logout again, or just go back to the CLI and configure it to a native resolution for your monitor.
Ok, I had to do a hard reset as CTRL-ALT-BACKSPACE froze my server.  I'll try the other method now, but how do I configure it at the CLI?

Sorry, I'm brand new to running Ubuntu server.

---

### Post by Nixie Pixel on 2009-04-13
Hmm, actually, after booting to the server (with XFCE running now, and not being able to see), I hit CTRL-ALT-F1, get a login prompt, enter my username, and the cursor blinks fast in the upper left and I'm frozen again....any ideas?

---

### Post by Nixie Pixel on 2009-04-13
Well, does anything bad happen if you just power off the computer manually?  

It was frozen and I was tired of watching the cursor blink at me, taunting me and my inability to resolve the issue.

I'll keep it shut down for now until I can find more information on how to resolve the issue.

---

### Post by Nixie Pixel on 2009-04-13
Is there a way to make adjustments to what boots before I'm able to boot?  Or will I need a live CD here?

---

### Post by ugm6hr on 2009-04-13
A few pointers:

1. You can shutdown a Linux computer with the key combination:
Ctrl+Alt+PrntScrn, while holding these down, type the following R-E-I-S-U-B (busier backwards).  Can't remember exactly what each does, but it is probably better for your computer than a hard reset.

2. You should be able to enter the Recover boot from Grub... just press escape as grub boots at the beginning, and select the recovery option.

3. If you remove GDM, it will stop XFCE from booting automatically:
sudo apt-get remove gdm
This will probably remove XFCE too (uncertain whether it is a necessary dependency of XFCE or not).

4. Once GDM is removed, just reboot:
sudo shutdown -r now

---

### Post by Nixie Pixel on 2009-04-13
I don't get it, I think I have a problem - I see the prompt to "press ESC to enter the menu" at boot, but pressing ESC does nothing, it just boots back into the server at the resolution my monitor can't handle.

What in the world can be preventing this from working?  I can press DEL and get into BIOS, so I doubt it is a keyboard problem...

---

### Post by Nixie Pixel on 2009-04-14
Ok, I guess it was a keyboard problem - I found a PS/2 keyboard and plugged it in, so ESC works.

I tried uninstalling gdm, it told me that package wasn't installed.  So I went ahead and removed xfce4.  

Also, sudo shutdown -r didn't work, I needed to add a time, so I did sudo shutdown -r now.  Hopefully that was the correct syntax (it did shut it down, so...:).

Ok, now when I install xfce again, what file do I need to edit to configure it so that it doesn't load in a resolution that my monitor can't handle?  

Thanks again!

Edit:  Hah!  Rebooting, even after removing xfce, leads me to a server running a window manager where I can't see the screen.  Please help?

---

### Post by Nixie Pixel on 2009-04-14
Found it - the culprit was wdm.  I have smashed it to bits.

Now for the configuration...if I can install & find the file I need.

---


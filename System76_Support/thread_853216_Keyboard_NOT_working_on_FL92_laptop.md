---
title: "Keyboard NOT working on FL92 laptop"
date: 2008-07-08
forum: System76 Support
---

### Post by iheartubuntu on 2008-07-08
My sister has a Serval Performance, model number is FL92.

This morning her keyboard stopped working in Ubuntu. It works fine in the BIOS. After the computer boots up to ask for username and password, she cannot enter anything because the keyboard wont work. Ive also tried to boot into recovery mode and when I get the recovery menu, I also am unable to use the keyboard to select my option.

Any help would be greatly appreciated! Thanks.

---

### Post by iheartubuntu on 2008-07-08
Well, my sister has been trying to reboot for a couple hours and her keyboard hasnt worked all that time. I had her shut the system down the last 30 or so minutes and when she turned it back on, it works again!

Is there anything we can check now that she is back in her computer? Any tests I can run? Any software I can run to fix problems? Thanks.

---

### Post by thomasaaron on 2008-07-08
That's odd that it works in the BIOS. Sounds like a hosed configuration somewhere rather than a hardware problem... maybe.

A sure way to check would be to try with a live CD.

And, just to clarify, what exactly happens when you open, say, a text editor and start typing? Do you get nothing at all? Do you get characters that you didn't type?

Finally, in System > Preferences > Keyboard > Layouts, what do you have as your default layout?

---

### Post by Sciri on 2009-07-06
Bump! ;)

Our office administrator here in the Canonical USA office is experiencing the exact same symptoms on her FL90 Serval Pro.

This morning her keyboard died mid-session, she rebooted, and was unable to login due to the internal keyboard and trackpad being unresponsive. Her external mouse worked fine.

I gave her an external USB keyboard and she was able to login and continue working.

Troubleshooting:

 * Keyboard/trackpad does not work on Jaunty LiveCD
 * Keyboard works fine in BIOS
 * Keyboard works fine in grub
 * Keyboard initially did not work in console recovery mode
 * Reapplied settings in Preferences -> Keyboard for 105-Key
 * Reboot and keyboard started working in console recovery mode
 * Brought up Gnome and keyboard still did not work
 * Reboot and keyboard was no longer working in console recovery mode

Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

---

### Post by Sciri on 2009-07-06
Right, one more update:

 * Tried booting off Intrepid LiveCD; internal keyboard/trackpad started working agin
 * Rebooted off internal hard drive (Intrepid), internal keybaord/trackpad still broken on 2.6.27-14 kernel
 * Rebooted off internal hard drive (Intrepid), internal keyboard/trackpad working on 2.6.27-11 kernel
 * Rebooted off internal hard drive (Intrepid), internal keyboard/trackpad started working again on 2.6.27-14 kernel

---

### Post by thomasaaron on 2009-07-07
That's pretty intermittent, which makes me wonder if the ribbon cable that connects the keyboard to the mobo is loose.

---

### Post by Trevor Bramble on 2009-08-12
I'm experiencing the same trouble with my FL90, except I can't get the built-in keyboard and mouse to work again at all.

They just stopped working overnight.  Nothing changed.

Here's what makes the ribbon cable theory not apply: they work fine when I boot to WinXP.

I tried the different kernels I still have installed and there is no change.  I tried updating System76 drivers but these days I'm just told that Ubuntu has all my drivers.

I don't really have room on my lap for the external keyboard and mouse....

---

### Post by thomasaaron on 2009-08-12
That's the first I've heard of the keyboard not working. But this should fix the touchpad...

run...
sudo gedit /etc/modprobe.d/touchpad.conf 

...and enter this line...
options psmouse proto=imps 

...and then reboot.

If you boot into a previous kernel (press Esc. when you see the grub countdown), does your keyboard work?

---

### Post by Trevor Bramble on 2009-08-12
Responded to your email but for completeness here was my reply:

Unfortunately that didn't affect the trackpad at all.  And no, booting to earlier kernels didn't change anything (I have I think 3 of them still installed.)

Anything else I could try?

---

### Post by thomasaaron on 2009-08-12
You might try booting from a live CD (I'd try 8.10). If they don't work there, it's a hardware problem.

---

### Post by Trevor Bramble on 2009-08-12
> **thomasaaron said:**
> You might try booting from a live CD (I'd try 8.10). If they don't work there, it's a hardware problem.

I don't have a Live CD on-hand to try (downloading ISO now) but how could it be a hardware problem when everything works under Windows?

---

### Post by thomasaaron on 2009-08-13
Ah, I missed that. Sorry.

Let me know, though, what you try from the live CD. I'll try do run some tests tomorrow when I get back in the office to see if I get similar results.

I know I had you set this up earlier. But just to make sure I didn't make an error in how I formatted the module entry, try going to a terminal and running...

sudo modprobe psmouse proto=imps 

...to see if that fixes the mouse. I'm not seeing the keyboard problem across the board, though (yet), so I'm wondering if you did anything special to your keyboard layout.

---

### Post by Trevor Bramble on 2009-08-13
Hi, Tom.

I experienced the same problems in the LiveCD.  I was able to navigate the boot menu using the built-in keyboard, but in X I could only use external devices.

After running the modprobe line, the trackpad is still unresponsive.

Under Keyboard Preferences I see the model as "Generic 105-key (Intl) PC" and the layout is "USA".

I know I've added some keyboard shortcuts, but otherwise nothing's been altered there.  And definitely nothing close to when the HICs stopped working.

---

### Post by thomasaaron on 2009-08-14
Trevor, what LiveCD did you use? 8.10? (Was the computer previously working well in 8.10?)

It sounds like bad hardware... but then it doesn't!

---

### Post by Trevor Bramble on 2009-08-14
I grabbed 9.04 (64).  On reflection, I'd actually encountered this problem months ago before upgrading from 8.10.  For a long time I only used the serval as a portable workstation, with keyboard, mouse, and monitor setups at both home and office.  So it was only while trying to log in before hooking up the external devices that I noticed.

Since I didn't even attempt using the built-in devices for months after that, I have no idea how long it took or what the circumstances were for its return to a fully working state.

Between then and now I've upgraded the hard disk (with a fresh install of 9.04 64-bit) and RAM (4GB) and gone through maybe 5 (?) kernel revisions.

I moved about a month ago and don't have a stationary location for all the external gear and I'm working from home so I've been using it full-time with the built-in inputs.  All working fine until two days ago.

Should I bother with an 8.10 LiveCD?  Could it be a loose connection that maybe Windows drivers are more forgiving about, and I should just crack open the case and try re-seating it?  If the hardware if faulty, what's the turn-around for repair?  Is there a trade-in program? ;^)

---

### Post by thomasaaron on 2009-08-14
I'd definitely try with 8.10. But I've got an FL92 in the shop now, and the keyboard and mouse both work great under 9.04. 

You could try re-seating the keyboard. You have to remove that panel above the keyboard *carefully*. Then it's all pretty straight forward. Email me if you need any help with that.

---

### Post by Trevor Bramble on 2009-08-17
Tom, I'm not sure what to make of it, but everything started working again this morning.

All that changes between not-working and working?

- Last night I cleaned up some redundant apps that had been sitting around for awhile just taking up space on disk and in the menu.  Emacs, Scribus, Thunar, Songbird, Exaile, and others like that.  Nothing more critical.  Just some apps.

- This morning the automatic disk checking started.  I let it run (I normally do) and when X came up, I could use my built-in controls once more.

...Doesn't make any sense to me.  All the apps I removed have been there for months, unchanged.  The previous disk check ran uninterrupted as well.  But I can't think of anything else that changed other than some Compiz preferences (enabling the cube stuff again now that I'm not on dual displays).

What do you make of it?  Should I expect this to happen again if I don't avoid some certain behavior?

---

### Post by Trevor Bramble on 2009-08-31
Easy come, easy go.

Not working again this morning.  Only system change yesterday was removing the ia32 libs for chromium ppa package....

---

### Post by thomasaaron on 2009-08-31
Trevor,

There is a bug that is supposedly affecting some of the FL9** laptops. I've got an FL92 on my desk right now, and I've been unable to reproduce the problem. Basically, the hard drive gets corrupted, and it supposedly happens in conjunction with heavy data transfers. I'm not seeing it across the board, but only with customers that do a lot of heavy file transfers. (Actually, I can count the cases on one hand, and we have a LOT of FL9** notebooks out there.)

Here is the bug report is here...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)
...and it does not happen prior to the Jaunty-11 kernel, in 32-bit Ubuntu or in Karmic 64-bit.

I bring it up because you say fsck fixed it. But I'm not sure that this is what is going on with your system.

It also sounds like your keyboard's ribbon cable (which connects it to the mobo) may be loose -- and thus intermittent.

To check that, you would have to remove the panel that runs horizontally above the keyboard and check the connection beneath the keyboard.

---


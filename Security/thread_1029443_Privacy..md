---
title: "Privacy."
date: 2009-01-03
forum: Security
---

### Post by lightspeed500oard on 2009-01-03
On Winxp I used Cyberscrub to wipe all deleted data from my PC. It will not install as it is a windows based program. In Ubuntu I found in synaptic Package Manager, a program called 'Wipe', This is the discription under proporties   >>>----> Secure file deletion
Recovery of supposedly erased data from magnetic media is easier than what many
people would like to believe. A technique called Magnetic Force Microscopy
(MFM) allows any moderately funded opponent to recover the last two or three
layers of data written to disk. Wipe repeatedly writes special patterns to the
files to be destroyed, using the fsync() call and/or the O_SYNC bit to force
disk access.   ......I did install this but cannot find it listed anywhere as a program + how to rur it. Any sujestions would be great. Ubuntu 8.10, Dell Inspiron 2200, Intel Penium.

---

### Post by 2hot6ft2 on 2009-01-03
Have you tried the terminal?
Applications>Accessories>Terminal
just put in
```
wipe
``` may not work unless you put sudo in front of it, and it should show you all the options that can be used with it. It is probably a terminal app and may not have a gui.

---

### Post by 2hot6ft2 on 2009-01-03
You could try secure-delete too it is in synaptic as well. I don't know if it has a gui or if it has to be run in a terminal.

---

### Post by Kinstonian on 2009-01-03
Just so you know, MFM laboratory attacks no longer work on modern hard drives, and that has been the case for a long time now.  The reason why the government and some other organizations still require multiple overwrites is in case someone once again discovers a similar method of data recovery.  You only need to overwrite data once before it is unrecoverable.

---

### Post by Piro24 on 2009-01-03
Data recovery is still possible, from just about any FS. I've personally done it from NTFS and a bit of a test/play-around thing in ext3.

---

### Post by lightspeed500oard on 2009-01-03
I tryed to run the codes in terminal, but now when it requests the password, I can't type anything at all. I have searched for a solution, others have had the same problem, so far no solutions. I have tried the Recovery and File check on restart, no go. Anyone have a fix for this? Also, I have used Winxp for some time know. In Windows Start>run>msconfig or chkdsk is used to run utilities and commands. Where can I find a list for Ubuntu 8.10?

---

### Post by bodhi.zazen on 2009-01-03
> **lightspeed500oard said:**
> I tryed to run the codes in terminal, but now when it requests the password, I can't type anything at all. I have searched for a solution, others have had the same problem, so far no solutions. I have tried the Recovery and File check on restart, no go. Anyone have a fix for this? Also, I have used Winxp for some time know. In Windows Start>run>msconfig or chkdsk is used to run utilities and commands. Where can I find a list for Ubuntu 8.10?

I assume when you say it is aaasking for a password you are using sudo in a terminal.

In that case, just type your log in password and hit enter. Nothing will show on the screen as you type.

---


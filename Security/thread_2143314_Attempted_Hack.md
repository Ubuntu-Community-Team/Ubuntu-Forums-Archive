---
title: "Attempted Hack?"
date: 2013-05-08
forum: Security
---

### Post by fuzzman17 on 2013-05-08
Something weird seems to be going on. One day I came home from work and I noticed when I went to log on to my computer that the remote log in had been selected. Then a few days ago I went to log in and saw "password incorrect" displayed under my user name. I never set up the remote lod in and don't remember it being on my log in screen before though it may have been.  I have just recently installed 13.04 and that's when the weirdness started. My system is set to log in automatically at boot up but to reguire a password to log back in once I log out. This is to prevent accidental entry from the keyboard caused by the cat walking across it. I doubt it was the cat this time. what are the chances that the very last key she steped on was enter?  Is there a way to set up a log with the time and dates of failed log in attmpts/remote log ins? I have a USB camera so in addition if I could get it to snap a picture that would be great. The most puzzling aspect of all this is there is nothing secret on my computer. the only thing I have that migh be of interest is a personal journal but it's on an external drive that is powered down unless I'm using it and the journal is password protected. In addition I have the guest account set up so anyone that wants to use it can log on as guest and half the time I forget to log out so the computer is open anyway.  I'm behind a NAT router but I was in a DMZ. I'm going to change that now just incase. Any suggestions as to how I can find out what is going on?

---

### Post by CharlesA on 2013-05-08
Why did you put your PC in the DMZ? If you enabled remote desktop (vino) while the machine was in the DMZ, you may have been cracked, but you won't know until you read the Basic Security link in my signature.

---

### Post by fuzzman17 on 2013-05-08
"Why did you put your PC in the DMZ? If you enabled remote desktop (vino) while the machine was in the DMZ, you may have been cracked"


Short answer, I didn't enable remote desktop, Someone else did.

---

### Post by CharlesA on 2013-05-09
Read this:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

If vino was enabled, it does not do any logging, so you cannot be sure if someone connected to your box or not. Check the options for "remote desktop" and see what they are set to.

---

### Post by fuzzman17 on 2013-05-09
CharlesA, thanks for the link. Seems I have a lot to learn. 
I do have  one question though. My log files do not have date/time stamps. Is this  normal in 13.04 and if so can I change it?

---

### Post by fuzzman17 on 2013-05-09
> **CharlesA said:**
> Read this:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

If vino was enabled, it does not do any logging, so you cannot be sure if someone connected to your box or not. Check the options for "remote desktop" and see what they are set to.

They seem to be set to the defaults. first 2 and 4th boxes checked. Nothing looks strange to me.

---

### Post by CharlesA on 2013-05-09
They should have date/time stamps, unless something has changed. Are you using the log file viewer or just opening them in nano or gedit or something?

It would probably be a good idea to make a backup of any of the stuff you have on your machine and either wipe it or try to track down what happened. VNC doesn't get turned on magically and Ubuntu has no listening services installed by default.

---

### Post by Irihapeti on 2013-05-09
I've noticed that the log file viewer in 13.10 - and therefore, presumably, 13.04 - doesn't display the date/time information. But if you drag the mouse over the text, you can see it.

If you just use an ordinary text editor to view it (or "cat" in the terminal), it's visible by default.

---

### Post by fuzzman17 on 2013-05-09
I was thinking the same thing myself. I keep all my important files on an external drive that is powered down unless I'm saving something, so I don't need to backup anything.
I was using log viewer to look at the logs.

---

### Post by CharlesA on 2013-05-09
It would probably be a good idea to wipe the machine and reinstall, but it would also be a good idea to figure out how vino got enabled and who enabled it because remote access is disabled by default - so unless you installed something like SSH or another vnc server, someone would have had to enable vino from the box itself.

---

### Post by fuzzman17 on 2013-05-09
> **Irihapeti said:**
> I've noticed that the log file viewer in 13.10 - and therefore, presumably, 13.04 - doesn't display the date/time information. But if you drag the mouse over the text, you can see it.

If you just use an ordinary text editor to view it (or "cat" in the terminal), it's visible by default.

Thanks that was the case. I can see them fine using a text editor.

---


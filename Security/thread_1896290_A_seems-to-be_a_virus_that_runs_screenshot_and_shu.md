---
title: "A seems-to-be a virus that runs screenshot and shut down window"
date: 2011-12-16
forum: Security
---

### Post by maxlit on 2011-12-16
Hello everyone,
could you please help me with the following problem.
Sometimes all of the sudden, it appears (even if I don't type anything on the keyboard) either a screenshot window with the proposal to save it, or the shut down window.
Recently, it even filled out my password automatically, when I changed it, it stopped.

It starts when I mount external hard drive or usb stick, also offline. 
I rarely use root user. 

Even though it sounds improbable, for me it looks like a virus. I ran clamAV antivirus on my file system, but it didn't find anything. I also don't see anything suspicious in the list of processes (obtained with htop), however, I've been using ubuntu since 2 months and highly unexperienced with this OS.

Does anyone have an idea, what it is and how I can fight it?

Thanks in advance!

---

### Post by jerome1232 on 2011-12-16
Spilled a soda into your keyboard?

It honestly sounds like a keyboard malfunction to me, I've had a very similar experience after dropping a bottle of soda into my keyboard. Do you have a second computer you can plug that keyboard into to see if that is the issue?

---

### Post by maxlit on 2011-12-16
No, i didn't spill anything on the keyboard. My second hypothesis is that keyboard usb conflicts with external drive usb in some way. 
I don't have an extra pc to plug my keyboard in. Btw, as for me this malfunction shows rather an intelligent behaviour.

---

### Post by sea_dawg on 2011-12-16
I recently had a similar problem.  It did indeed turn out to be a dirty keyboard.

---

### Post by jerome1232 on 2011-12-16
Do you run any services that can be exploited (vnc, any other remote login service? ssh?)

Did you install software from an untrusted source prior to this behavior?

If you feel the computer has been exploited somehow, the only sure answer to get rid of it is to reinstall the system.

---

### Post by maxlit on 2011-12-16
> **jerome1232 said:**
> Do you run any services that can be exploited (vnc, any other remote login service? ssh?)
yes, I use ssh, but I have this problem also offline.

> 
Did you install software from an untrusted source prior to this behavior?
I think yes, however, I'm not able to identify it. If it were a source of a problem, I'd like to see this software identified as a virus by antivirus or at least to see it in the processes list and kill it manually.

> 
If you feel the computer has been exploited somehow, the only sure answer to get rid of it is to reinstall the system.
If I were short of other options, I'll do this, but before I'd like to try a less painful solution.

---

### Post by haqking on 2011-12-16
change your keyboard

---

### Post by jerome1232 on 2011-12-16
I still think it's your keyboard as well.

If (I'm trying to be open minded here) you've managed to install some malicious software that randomly takes screenshots and starts deleting your password when you type, it's some very odd malicious software indeed (I could almost believe it if you were running vnc and got comprimsed via that). Malicious software isn't necessarily a Virus, and there are no known viruses in the wild for linux, my understanding is Clam is primarily intended for a server which has windows clients, so that it may check files or mail before sending them off to said windows clients.

---

### Post by wirelessmonkey on 2011-12-16
I have a USB keyboard that for some reason will do things this from time to time. It's virtually new, and certainly not dirty. I honestly think it's something with the keyboard's USB connection.

---

### Post by maxlit on 2011-12-16
I changed my keyboard and the problem disappeared. Until it comes again, I'll assume that was the source of the problem.
Thanks everyone for the input!

---


---
title: "Loading encryption key file from encrypted USB drive on boot"
date: 2013-05-20
forum: Security
---

### Post by Ranko Kohime on 2013-05-20
This is an interesting little use case I've dreamed up, and I'd like to know how I might go about it.

I have 2 drives in my system, sda and sdb.  sda currently contains /boot and /, the latter of which is encrypted.  sdb contains /home, and is encrypted using a key file stored in /root.  sda is an SSD.

I'm planning on upgrading soon to 13.04, and in the process I'm going to reformat sda, and install unencrypted, for performance reasons.  Which leaves me with the conundrum of what to do with the key file for sdb.

My first thought was, to put it on a USB drive.  Then I realized, that if someone got the drive, (unlikely without them killing me first, but still), they would be able to unlock sdb.  Then I looked over at my IronKey*, and a light bulb came on.

So here's the idea.
[LIST=1]
[*]The system boots as a normal unencrypted system until it tries to mount /home
[*]Check for the presence of the IK, and if available, mount the R/O portion and start the unlocking agent.  If not available, prompt me to insert the IK
[*]I enter in my IK password
[*]R/W portion is unlocked, mounted, and /home unlocked with the now-available key file
[*]The system sends the lock command to the IK, and unmounts it
[*]Booting continues normally.
[/LIST]

Why the complexity, you may ask?  I don't trust myself to use a strong enough password that it can't be cracked fairly easily.  I run out of memory space around 12-14 random characters.  Beyond that I'm either using sentences, (which are subject to dictionary attacks), or pieces of paper.  The IK has the advantage that it is potted, (the memory chips cannot be directly accessed without being destroyed in the process), and the unlocker, after 10 tries, permanently erases the memory chips.  Therefore, password strength is of less (but more than no) concern.

So, is my idea feasible, or no?  And if it is, are there any guides about how to go about it?  (Google has failed me here)


* For those who don't know how the IronKey works, it is an encrypted USB stick, which mounts first as R/O CD-ROM device, with an unlocker application on that drive, and when the unlocker is run and the password entered, then the encrypted R/W portion is exposed to the OS.

---

### Post by Ranko Kohime on 2013-05-22
Too estoteric?  :P

---


---
title: "Persistent Live vs. Traditional Install on SD card."
date: 2012-11-05
forum: The Cafe
---

### Post by newb85 on 2012-11-05
Okay, this question came to mind because of a couple comments in a support thread.  (It's [here]("http://ubuntuforums.org/showthread.php?t=2080729"), if you're interested.)  However, I have no intention of carting conclusions/thoughts from this thread back to that one.  I'm starting a new thread in a discussion forum because it was too much of a tangent for the support thread.

Please note, I am fully aware that I am only an uninformed (or ill-informed, if you prefer) critical thinker on this subject.

So, here's the "hypothetical" situation.  A user has a machine with a dead HDD, and wants to use a 16GB SD card instead of a HDD.  My initial thought was that a traditional install (treating the SD card as an SSD) would be a more satisfying experience than making the card into a Persistent Live SD.  Someone else suggested that because of the limited number of Program/Erase cycles in flash memory (order-of-magnitude 100,000), Persistent Live was the way to go.

Now it seems to me that with both approaches, all changes you make to the system have to be stored.  In my understanding, the difference is basically that in Persistent Live, those changes are all stored in one small portion of the drive, whereas in Traditional, they are stored throughout the used drive space.  It seems to follow, therefore, that if the two approaches are treated the same way, the blocks within the persistence file of the Persistent Live install would undergo a lot more P/E cycles than any block in the Traditional install.

Any thoughts?

---

### Post by Paqman on 2012-11-06
Either way, since an SD card lacks any wear levelling you'll still run into the same problem. Whether you do lots of little writes to various system files, or to a persistence area then you're still hammering the same spots over and over.

I would say that the persistent live image would probably have the edge by default, as it's designed to run from RAM. Having said that, it's not hard to tweak a normal install to shift stuff like /tmp into RAM, which will cut down on some writes.

Bottom line is I'd say there's not a great deal in it, with the persistent having a slight edge for longevity, but the standard install being easier to maintain and troubleshoot.

---

### Post by newb85 on 2012-11-06
> **Paqman said:**
> I would say that the persistent live image would probably have the edge by default, as it's designed to run from RAM.

Let me see if I understand what you're driving at with that point.  Are you saying that changes to the persistence file are only made at shutdown?  If that's the case, I can see how that would cut down on P/E cycles.  I guess I had envisioned a Persistent Live install writing changes to the persistence file on-the-fly.

But come to think of it, if changes to the persistence file are only written at shutdown, that creates another issue.  If the system were not shut down properly, that would mean *everything* the user had done would be lost.  Programs they had installed would not be installed.  Settings they had set would be unset.  Worst of all, documents they had saved would be unsaved.  And given that our hypothetical user is doing this because the HDD went belly-up, it's not unlikely that other hardware failures will occur.

---

### Post by Paqman on 2012-11-06
> **newb85 said:**
> Let me see if I understand what you're driving at with that point.  Are you saying that changes to the persistence file are only made at shutdown?

No I'm saying that the live system will load more stuff into RAM at boot time and run from there. Changes to things like files in /tmp will get written only to RAM, not the storage device. If you install to a storage device those writes would get written to the device (assuming you have /tmp mounted there as is the default setting).

I'd be interested in seeing some actual numbers on how the number of writes to disk differed though, I'm just making some educated guesses based on what I know of how the system works. Nothing compares to real data!

---

### Post by newb85 on 2012-11-06
Ah, so Perisistent Live has more of the file hierarchy set up as virtual filesystems, namely /tmp and (I'm assuming) /var.  Definitely a better approach than what I assumed in my last post.

(From my initial conceptualization)
> ...all changes you make to the system have to be stored. ...in Traditional, they are stored throughout the used drive space.

So, In reality, P/E cycles in a Traditional install are still largely concentrated in a few directories.

---

### Post by newb85 on 2012-11-06
> **Paqman said:**
> Having said that, it's not hard to tweak a normal install to shift stuff like /tmp into RAM, which will cut down on some writes.

So, to rabbit trail from my initial thought experiment a little, my brother is considering both replacing his HDD with an SSD and installing Ubuntu.  (His experience with Linux is limited to attempts to recover data from his first two HDDs when they failed.)  If he does, would it be a good idea to shift /tmp and /var into RAM?  Would that be difficult to set up or maintain?

---

### Post by Paqman on 2012-11-06
> **newb85 said:**
> If he does, would it be a good idea to shift /tmp and /var into RAM?  Would that be difficult to set up or maintain?

If he's using a proper SSD that has wear levelling then he doesn't need to do anything. 

You can move /tmp into a ramdisk if you want (I do) but it isn't compulsory. All it requires is a single line entry in /etc/fstab and a reboot. You could do likewise with /var/log, but I wouldn't advise putting all of /var in a ramdisk!

---


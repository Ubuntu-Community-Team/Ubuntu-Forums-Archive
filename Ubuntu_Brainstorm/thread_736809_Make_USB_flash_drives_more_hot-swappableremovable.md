---
title: "Make USB flash drives more hot-swappable/removable"
date: 2008-03-27
forum: Ubuntu Brainstorm
---

### Post by diablo75 on 2008-03-27
I have this up on Ubuntu Brainstorm [here]("http://brainstorm.ubuntu.com/idea/5813/"), but was looking for some more activity and feedback.  I'll link this thread to the idea so people can read your feedback to what I came up with.

--------------------

> Sometimes when I unmount a USB flash drive, it has the "writing data to drive" warning up for a good minute before saying its safe to remove.

My idea: Don't make me wait on stupid stuff like that. Whatever Linux needed to do to that USB drive, it should have gotten it out of the way a long time ago while I was distracted with something else. I can see the LED light not blinking; it wasn't doing anything before, but now it's got something to do that it forgot about?? If I had it my way, I'd be allowed to pull my USB flash drive out whenever I'd like to....

So! The midway suggestion here is to get these mystery processes automated better so the drives will be that much closer to being ready to be removed safely from the PC.

But how about this: What if you made the drive constantly tidy up on the above stuff mentioned, but then logically dismount itself from the system after some inactivity, but not actually remove the drives' icon from the screen (so it will appear to still be mounted).

The icon could also have a green check mark next to it that would indicate to the user "This thing is ready to be pulled out any time." And if it's not yet dismounted, then it should have busy icon, and be busy getting itself "ready" ("dismounted"), and then actually dismount so you could pull it at will from the computer.

When I plug in a flash drive, I'd like to see a new status icon for that drive on my task bar, either with a green check mark (indicating that if I wanted to pull it out of the computer RIGHT NOW, I could do so safely), or with some other kind of icon that would indicate the drive is busy.

Now, if a person gets used to pulling their drive out whenever they please, and it actually causes a problem because they weren't paying attention to the status icon (or the frigging status LIGHT on the drive itself), make it so the system will request the user to reinsert their drive for a moment so it can finished whatever it needed to finish, and correct errors if necessary.

Good idea?  Bad idea?  Why/Why not?

Thanks!

---

### Post by scragar on 2008-03-27
> Sometimes when I unmount a USB flash drive, it has the "writing data to drive" warning up for a good minute before saying its safe to remove.since pen drives are not synced perminantly it will often say it's done before it's finished, when you unmount the volume it would still be moving/saving files. there are methods of editing you fstab to mount it without this problem, but then you will notice the slower write speed.


[http://en.wikipedia.org/wiki/Asynchronous_I/O](http://en.wikipedia.org/wiki/Asynchronous_I/O) <-- good point on how async works, dunno why pen drives are always mounted in this way though...

if you wanna make your edits may I recomend adding this line(more or less) to your fstab:
```
/dev/sda1	/media/disk	auto	auto,user,exec,rw,sync	0
```cannot be sure that this will work for everyone though(all I know is that it works for me)

---

### Post by FuturePilot on 2008-03-27
Mounting a flash drive with the sync option is a good way to kill a flash drive in a short amount of time.

---

### Post by scragar on 2008-03-27
meh, I got my pen drives for free because windows broke them(how can it destroy the partition table so easily?), so if they die it's fine by me, I never put anything on them that I don't carry a second copy off. Oh, and no-one tell windows users that it comes with a partition fixing program hidden somewhere in the troubleshoot options, I love getting free drives because people think they are beyond repair :P)

---

### Post by diablo75 on 2008-03-27
Could you mail one of those free drives to me?  :)

I lost one a few days ago.  I've bought some neck straps for the next ones I get so that doesn't happen again (hopefully).

---


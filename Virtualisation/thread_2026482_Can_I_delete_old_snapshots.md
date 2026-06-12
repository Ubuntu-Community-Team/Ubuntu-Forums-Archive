---
title: "Can I delete old snapshots"
date: 2012-07-15
forum: Virtualisation
---

### Post by Jonners59 on 2012-07-15
Simple question....
Ubuntu 12.04
I take a snapshot whenever I have done a major update to MS Windows 7 OS on my virtual machine Oracle Virtual Box 4.1....

I am now filling up my Home directory, namely because of all these snapshots.  Can I remove any of the previous snapshots without affecting the current snapshot, and does that completely remove it from my machine.....  If not, how do I?

---

### Post by CharlesA on 2012-07-15
Yes you can remove old snapshots without affecting the current one.

---

### Post by Jonners59 on 2012-07-15
Hi Charles
Lovely to hear from you after so long...  Hope you are well.

When deleting via VB, that does not delete the actual image though, does it?  I have just deleted one and there seem to be just as many as there were before, so I am still not freeing up space.  In fact it is not allowing me to delete any more because it can not merge images due to lack of space available

---

### Post by L a r r y on 2012-07-15
> **Jonners59 said:**
> Hi Charles
Lovely to hear from you after so long...  Hope you are well.

When deleting via VB, that does not delete the actual image though, does it?  I have just deleted one and there seem to be just as many as there were before, so I am still not freeing up space.  In fact it is not allowing me to delete any more because it can not merge images due to lack of space available

Is it possible that you moved the old snapshot to trash, and have not emptied the trash?  It will remain on the drive until it has been deleted from trash.

---

### Post by CharlesA on 2012-07-15
> **Jonners59 said:**
> Hi Charles
Lovely to hear from you after so long...  Hope you are well.

When deleting via VB, that does not delete the actual image though, does it?  I have just deleted one and there seem to be just as many as there were before, so I am still not freeing up space.  In fact it is not allowing me to delete any more because it can not merge images due to lack of space available

It should merge the snapshot back into the main vdi file. Check the snapshots folder and see how many files are in there.

You can also check the virtual media manager.

---

### Post by L a r r y on 2012-07-15
An addendum --- If you are trying to delete using the point-and-click gui, and unable to do so for lack of space, you might be able to open a Terminal and use the rm command from the folder containing the file, or boot from a Live CD and accomplish the task.

If the file is in the trash and not able to be deleted, then you may be able to delete it from the .trash hidden folder using the rm command or from a Live CD.

---

### Post by Jonners59 on 2012-07-15
> **L a r r y said:**
> An addendum --- If you are trying to delete using the point-and-click gui, and unable to do so for lack of space, you might be able to open a Terminal and use the rm command from the folder containing the file, or boot from a Live CD and accomplish the task.

If the file is in the trash and not able to be deleted, then you may be able to delete it from the .trash hidden folder using the rm command or from a Live CD.

Thank you Larry, but I think in VM it is slightly different as the VM needs the directories

Charles
Thanks.  I'll take a count.  It said it was merging but when I went in to the directory there seemed to be too many still there.  I would take a count and try again, but due to other problems with my VB install I am trying some other things at the moment.  I am currently trying to move the entire VM to spare drive, that shall free up 149Gb.  I then intend to try and fix the VM, see my other Thread.  If I succeed I'll come back to this.

---

### Post by CharlesA on 2012-07-15
> **Jonners59 said:**
> Thank you Larry, but I think in VM it is slightly different as the VM needs the directories

Charles
Thanks.  I'll take a count.  It said it was merging but when I went in to the directory there seemed to be too many still there.  I would take a count and try again, but due to other problems with my VB install I am trying some other things at the moment.  I am currently trying to move the entire VM to spare drive, that shall free up 149Gb.  I then intend to try and fix the VM, see my other Thread.  If I succeed I'll come back to this.
I ran into a problem where a snapshot was still "linked" in virtual media manager, and VBox thought it was still in use even tho it wasn't.

---

### Post by Jonners59 on 2012-07-15
> **CharlesA said:**
> I ran into a problem where a snapshot was still "linked" in virtual media manager, and VBox thought it was still in use even tho it wasn't.
In a way I get reassured when you have a prob, sorry, but it makes me feel less an idiot.

My main prob is VB does not work anymore since the last Update Manager update, and the more I try and fix it the worse it is getting.  ANyway that is another thread - glad if you could take a look.

[http://ubuntuforums.org/showthread.php?t=2026478](http://ubuntuforums.org/showthread.php?t=2026478)

---

### Post by Jonners59 on 2012-07-20
OK, I have rebuilt my server, so shall now rebuild the virtual machine....  Snapshots I have grasped and shall take on board....  Many thanks Charles....  Still need you to build this thing, so don't go away!

---

### Post by CharlesA on 2012-07-20
> **Jonners59 said:**
> OK, I have rebuilt my server, so shall now rebuild the virtual machine....  Snapshots I have grasped and shall take on board....  Many thanks Charles....  Still need you to build this thing, so don't go away!
You might not have to rebuilt the VM if you copied ~/.VirtualBox and ~/VirtualBox VMs, but it might not be such a bad idea. Start fresh and all that.

---

### Post by Jonners59 on 2012-07-21
I found an old one (9 March 2012) in my backups, the current would not work for whatever reason.

Is working and up to date now.

Just removing old snapshots and then just do a refresh back up.

When I get back - August 28 I need to do the auto start again.  VM starts on boot, but the machine does not and I can not recall how to do it.  It was a script you gave me if I recall?

I also need to do the same for mediatomb, but I never had one for that...

---

### Post by CharlesA on 2012-07-21
Probably. The only thread I found about it was here:
[http://ubuntuforums.org/showthread.php?t=1078689](http://ubuntuforums.org/showthread.php?t=1078689)

---

### Post by Jonners59 on 2012-07-21
> **CharlesA said:**
> Probably. The only thread I found about it was here:
[http://ubuntuforums.org/showthread.php?t=1078689](http://ubuntuforums.org/showthread.php?t=1078689)

That was it....  Many thanks, as always..  :D:D:D:D:D:D

---

### Post by CharlesA on 2012-07-21
Welcome. If you have any other questions or need help. Feel free to ask.

---

### Post by Jonners59 on 2012-07-30
> **CharlesA said:**
> Welcome. If you have any other questions or need help. Feel free to ask.
Charles
I recived an update email to this thread, but it contained within it's text a link to Indian porn.....  I was going to report it as abuse here but the reply does not seem to exist.  Has the server been hacked?

---

### Post by CharlesA on 2012-07-30
Nah, just a spammer who was banned shortly after posting.

---


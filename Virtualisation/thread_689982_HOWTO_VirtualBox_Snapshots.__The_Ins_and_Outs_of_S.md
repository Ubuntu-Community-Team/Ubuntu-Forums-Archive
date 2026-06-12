---
title: "HOWTO: VirtualBox Snapshots.  The Ins and Outs of Snapshots."
date: 2008-02-07
forum: Virtualisation
---

### Post by Sugi on 2008-02-07
[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=58962&d=1202363371[/IMG][/CENTER]
Description of a Snapshot in VirtualBox:
* A Snapshot is like a making system restore point for your virtual operating system.  This is how it's done.

System Tool>VirtualBox>Snapshot>Take Snapshot
Title: *Whatever You Want* (Mine are usally Dates like "Since 02/06/08*)
Description: *Whatever You Want* (Mine talks about Fresh Installation of the OS or whatever is install  during each snapshots.)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63657&stc=1&d=1206378928[/IMG]

Now, everything up to this point has been saved, but now, you are currently working with the new snapshot.  So, basicly: the new snapshot *Whatever You Want* snapshot [Mine was "Since 02/06/08]) is going to be used for now on. Meaning any files and/or installation of applications will be saved under *Whatever You Want* snapshot (Mine was "Since 02/06/08) for now on.  You can as well make additional snapshots as time increase or any time during your time with your virtual operating system.  Maybe a snapshot day by day, if you want really wanted.

Example:
***NOTE:  To make new snapshot: (like adove)
System Tool>VirtualBox>Snapshot>Take Snapshot
Title: *Whatever_You_Want*
Description: *Whatever_You_Want_For_a_Description*

To start off:
 - Make New snapshot call it "Whatever_You_Want" (for this Example I will use a snapshot called "Since 02/07/08")
 - Boot up your Virtual Operating System (for this example I will use "Windows Vista")
 - Create a folder on your desktop, call it "New Folder" (Mine was "02/07/08")
 - Shut down the Virtual Operating System (Mine was Windows Vista)
 - Create another snapshot "Whatever_You_Want2" (for this Example I will use "Since 02/08/08")
 - Boot up your Virtual Operating System (Mine was Windows Vista)
 - Create another folder on your desktop, call it "New Folder (2)" (Mine was "02/08/08")
 - Now, You should see two folders on the Desktop "New Folder" & "New Folder (2)" (Mine was "02/07/08" & "02/08/08")
 - Shut down your Virtual Operating System (Mine was Windows Vista)
 - Revert back to "Whatever_You_Want" (Mine was "02/07/08")
*Note:Within VirtualBox>Snapshots (#)>click on "Whatever_You_Want2" (Mine was "Since 02/08/08")>click the icon that says "Revert to Current Snapshot (Crtl+Shift+R)
 - Start up your Virtual Operating System (Mine was Windows Vista)
 - Look at your desktop
 - Now, You will only see the one folder named "New Folder" (Mine was "02/07/08")
 - You have fullly loaded up "Whatever_You_Want" snapshot (Mine was "Since 02/07/08" snapshot)


"Revert a Snapshot" Reverting to an old Snapshot and "Discard a Snapshot" Discarding the current Snapshot:
Be careful, these two options "Revert a Snapshot" and "Discard a Snapshot" are very different.

"Revert a Snapshot" allows you to use the snapshot before the current snapshot you are using at the moment, but the current snapshot is still store. (like in the Example, "Whatever_You_Want" [Mine was "02/07/08])

"Discard a Snapshot" deletes the current Snapshot.  Now, you HAVE to use the Snapshot before the snapshot you just deleted. (like in the Example, "Discard a Snapshot" "Whatever_You_Want2" [Mine was "02/08/08"] and now you HAVE to use snapshot "Whatever_You_Want" [Mine was "02/07/08"]).



I wrote this long HOWTO on Snapshots, because I always write little notes on my personal computer adventures.  Everything from installing a game through wine to terminal codes.  It's so I don't forget anything.  A while back, I discard my one of my current state on my windows virtual operating system (I didn't mean to >.<) and had no snapshot to revert back to.  I lost a few months of homework and fully working seamless windows operating system within my linux box.   So, I am hoping someone out there will takes my advince and make a snapshots of their operating system.  Hopefully a few snapshots.  So, they don't lose everything like I did. :-/

Desktop with XP
[http://ubuntuforums.org/attachment.php?attachmentid=58963&stc=1&d=1202363645]("http://ubuntuforums.org/attachment.php?attachmentid=58963&stc=1&d=1202363645")

Cheers,
Sugi

---

### Post by dccrens on 2008-03-23
Great howto. I also have had a lot of issues with snapshots and understanding how they work. I love VB but their snapshot terminology really sucks. 

I still don't understand what to select to incorporate the current "machine state" or snapshot as the "default". 

Let say I have my original default VDI (a basic install). I take a snapshot on say 03/20/08. I then install some software and take another snapshot on 03/21/08. I install some more software and take a snapshot on 03/23/08. Everything is working good so I want to keep the machine state as it is on 03/23/08 with all of the software and changes. If I just "leave" the snapshots and do nothing I will be ok BUT the other previous snapshots are taking up disk space. So, is there a way to get rid of them and make the "last" snapshot I took on 03/23/08 the "only" disk image/snapshot???

---

### Post by glenn69 on 2008-03-27
I'm a bit confused about the terminology of the "state" of my computer being saved.  If I install a new piece of software to a snapshot, will it be t here when I next open the snapshot or does it revert to before I installed the software?  In other words, do I have to create a new snapshot sfter every piece of software is installed ?

Thanks

---

### Post by delian66 on 2008-05-17
> **dccrens said:**
> Great howto. I also have had a lot of issues with snapshots and understanding how they work. I love VB but their snapshot terminology really sucks. 

I still don't understand what to select to incorporate the current "machine state" or snapshot as the "default". 

Let say I have my original default VDI (a basic install). I take a snapshot on say 03/20/08. I then install some software and take another snapshot on 03/21/08. I install some more software and take a snapshot on 03/23/08. Everything is working good so I want to keep the machine state as it is on 03/23/08 with all of the software and changes. If I just "leave" the snapshots and do nothing I will be ok BUT the other previous snapshots are taking up disk space. So, is there a way to get rid of them and make the "last" snapshot I took on 03/23/08 the "only" disk image/snapshot???

No, these *fine* people do not supply a way to merge snapshots as I think will be the proper way to name this functionality. There was a ticket, ignored by them saying ([http://www.virtualbox.org/ticket/1101):](http://www.virtualbox.org/ticket/1101):)
> 
01/17/08 10:19:10 changed by michael 

I'm not exactly clear about what you want here. The "Discard snapshot" feature merges the snapshot disk image into the parent disk image.


which of course is absolutely utter rubbishly wrong. I've just lost 5 hours of configuration and work ... thank god I've used version control, so not everything had been lost, but still it is very annoying. 

   Please, stay away from snapshots, for now ( 05/17/2008 ), it is much better to make backups from your VDI manually, at least you will not be lied in your expectations.

---

### Post by SlappyPappy on 2008-05-17
Cool, this is good to know.

So I should copy the .vdi to say a DVD for safety and then if my install of W2K goes wonky I can just pop that baby back in from the DVD, right?

---

### Post by delian66 on 2008-05-17
> **SlappyPappy said:**
> Cool, this is good to know.

So I should copy the .vdi to say a DVD for safety and then if my install of W2K goes wonky I can just pop that baby back in from the DVD, right?

Yes, as long as you do not use snapshots, it should be fine.

---

### Post by bartman on 2008-05-17
I've had a wonky experience with snapshots myself.

I had fresh WinXP install patched as of 1st May. The vdi file was 1.8 GB large. I took a snapshot called pre-SP3 and proceeded with installing SP3 on the machine. Very quickly I was surprised that I ran out of space on my root partition because the snapshot grew to over 2 GB in size. I find it funny that it came to overgrow the size of the vdi it was supposed to revert to.

So yeah, just backing up the current vdi file manually seems to be the most space efficient method for now, although it isn't exactly time efficient.

---

### Post by Chris_Z on 2008-09-13
> **delian66 said:**
> No, these *fine* people do not supply a way to merge snapshots as I think will be the proper way to name this functionality.

This is not entirely correct.
Merge works just fine.

What you do is "Discard"ing snapshots, one by one, by discarding always the *topmost* one until you have only the "Current state" entry left. Done.

Everything is now merged into a single file. 

Note that discarding from bottom up has a very, very different effect, and a confusing one.  

Regards,
/Chris Z.

---

### Post by beartooth on 2008-10-17
You know, I had to play with this for quite a spell before how "merges" worked. *IF* I understand things correctly, the tree view is really just a temporal history, and not a "component history", that is, each snapshot stands on its own from the base image.

This is why "discarding" early snapshots is actually merging them, because the last image already contains all the preceding snapshots already merged in.  If you have the following snapshots: 

base-> snap1 -> snap2 -> snap3 

You can just "discard" snap1 and end up with

base-> snap2 -> snap3

Because the later snapshots don't "need" snap1, snap1 is already incorporated into them

Granted, this isn't obvious (can't say I like the UI for this feature), but now that I understand it, I can live with it.

---

### Post by statikeffeck on 2008-11-17
wow. wish I saw this topic earlier. but it was stupid of me for not backing anything up. I set up a VirtualBox image with Ubuntu Server so I could run a PHP/MySQL server within my own computer for web development.
I spent a night writing some new scripts... it was late and when I powered off I chose' Power Off Machine (Discard Snapshot). I didn't think the snapshot had anything to do with the VDI image, so I ended up losing that information.
luckily it was only 1 night, not months like with your homework.... :(

---

### Post by sadohert on 2008-12-22
> **Chris_Z said:**
> 
Note that discarding from bottom up has a very, very different effect, and a confusing one.  

Regards,
/Chris Z.

For other peoples benefit, I just made the mistake of not deleting snapshots in the top to bottom direction, and had the opposite effect of what I wanted.  Basically, I lost all my most recent setup/install, and was reverted back to the 2nd last state.  Thankfully in an odd round about way this reverted the SP3 update that had happened, which I wanted, and now things are okay... but it could have been a lot worse.

---

### Post by thierrybo on 2008-12-28
The manual says just this text (on more 200 pages...), but it clearly explains what does the “Revert to current snapshot” choice. This si not so clear about the last sentence:

To revert to an earlier snapshot, you right-click on the “Current state” item and
select “Revert to current snapshot”. This will bring the VM back to the state of the
nearest (most recent) snapshot. Similarly, you can merge several earlier snapshots
into one by right-clicking on a snapshot and selecting “Discard snapshot”.

---

### Post by Orographic on 2008-12-29
I'm trying to understand all of this as I lost some work (only installed AV, FF3, other progs etc) myself.

I have re-installed VB 2.1.0 after some initial shutdown problems but all is working fine now.

This time I haven't made any snapshots but just have the 'Current State' of Windows XP. In my .VirtualBox folder I just have my 'XP.vdi' in the Harddisks folder. Is this the .vdi that I backup so that I can re-use it if I have to re-install Intrepid and VB 2.1.0? This would give me back my activated XP install, correct?'

For now I am just backing up the whole .VirtualBox folder.

---

### Post by sehe on 2009-01-05
> **Chris_Z said:**
> This is not entirely correct.
Merge works just fine.

What you do is "Discard"ing snapshots, one by one, by discarding always the *topmost* one until you have only the "Current state" entry left. Done.

Everything is now merged into a single file. 

Note that discarding from bottom up has a very, very different effect, and a confusing one.  

Regards,
/Chris Z.

Now the sickening irony is that I have ruined a good number of VMs and I have still to figure out whether you are (a) plain wrong (b) what the heck you mean by 'top' or 'bottom'. Top could mean: top of the window, top of the tree (ironically, the 'trunk'), the top of the snapshot stack (in the LIFO sense of the word, so: the actual leaf-node or treetop to be completely confusing)... mirror that for bottom.

It couldn't be more unclear. IMHO

Seth

---

### Post by Dedoimedo on 2009-01-06
Hi,

Snapshots are much like differential backups. Very useful for making large changes to the system and then reverting back.

It is important not to manually delete them, because this can break virtual machines.

Another useful methods is to simply copy over the entire virtual machine hard disk file. This is an effective clone. And there's also the clone feature.

Dedoimedo

---

### Post by Spyderizer on 2009-03-06
Is it possible to revert to an old snapshot without discarding a newer one, like in VMWare?

---

### Post by HermanAB on 2009-03-07
Hmm, on both VMware and Vbox, I stop the VM and then make a tar ball of the directory.  In my humble experience, that is the the only sure fire way to know what you got and be able to revert back to any saved version.  When debugging problems I sometimes run multiple versions (effectively clones) of the same system which allows me to compare results.

Cheers,

Herman

---

### Post by UranUtan on 2009-03-10
Hi,

I am sorry, but the original post is still too confusing. 

Found this blog which explains perfectly how to manage VirtualBox snapshots and cloning a VDI which has snapshots:

[http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/](http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/)

---

### Post by oleros on 2009-06-24
I am running virtualbox from Vista (hope I'm still welcome on this forum;) and have made a snapshot of Windows7. Someone told me I can use the snapshot to run/boot win7 directly from an external source like a usb-stick on any machine, independent of virtualbox. Is this correct? I have copied the snapshot vdi file to a stick but no surprise - I can't run it just by clicking on it..
Any experiece with this?

---

### Post by sleeping on 2009-07-02
Is there a way to have a "tree" of snapshots instead of a "line" of snapshots? The way the VBox GUI presents it, it leads me to believe I can build a whole hierarchy of snapshots, but I can't find how. Here's an example of what I would want:

```

base ---> snap1 ---> snap2 ---> snap3
      |          |
      |          |
      |          --> snap2.1 --- snap2.2
      |
      |
      --> snap1.1 ---> snap1.2 ---> snap1.3
                                |
                                |
                                --> snap1.3.1

```

The Snapshots tab in the VBox gui displays the snapshots in a tree-like fashion, which makes it appear that such a tree is possible. When I'm at snap3, I would like to go back to snap2 and "fork" a new state to make snap2.1, then go back to base and "fork" yet another state to make snap1.1.

---

### Post by iniesta on 2009-09-24
> **sleeping said:**
> Is there a way to have a "tree" of snapshots instead of a "line" of snapshots? The way the VBox GUI presents it, it leads me to believe I can build a whole hierarchy of snapshots, but I can't find how. Here's an example of what I would want:

```

base ---> snap1 ---> snap2 ---> snap3
      |          |
      |          |
      |          --> snap2.1 --- snap2.2
      |
      |
      --> snap1.1 ---> snap1.2 ---> snap1.3
                                |
                                |
                                --> snap1.3.1

```

The Snapshots tab in the VBox gui displays the snapshots in a tree-like fashion, which makes it appear that such a tree is possible. When I'm at snap3, I would like to go back to snap2 and "fork" a new state to make snap2.1, then go back to base and "fork" yet another state to make snap1.1.

As far as I know there is no way you can do this with VirtualBox. The snapshot feature of VirtualBox sucks. It does not allow you to move freely between the snapshots in your snapshot tree. Moreover, if you return one step backward, you will lost your current snapshot.

You can do all of these (and even more) very easily in VMware.

In my opinion, the snapshot feature of VirtualBox is far too bad compared to what the users expect it should be (and what it could be). Sadly, the developers have not made any move in improving the feature yet, despite the fact that many requests have already been sent to their support forum. It seems that they just ignore our opinions about this issue.

---

### Post by freackout on 2009-09-24
> **glenn69 said:**
> I'm a bit confused about the terminology of the "state" of my computer being saved.  If I install a new piece of software to a snapshot, will it be t here when I next open the snapshot or does it revert to before I installed the software?  In other words, do I have to create a new snapshot sfter every piece of software is installed ?

Thanks

Look in your home directory (show hidden) .VirtualBox/Machines/whichever/blahblah.xml edit it with whatever and also change the states it saved last time ok... got me out of a state.

---

### Post by polocanada on 2009-10-11
Reading the user guide for VB I find it is not very clear in several areas from command line functions to taking snapshots. Today, I looked into snapshots and decided to write this simple, easy to understand guide:

**Prerequisites:**

Virtual Machine
Initial Snapshot (optional, e.g week ago)
Snapshot DAY 1 (e.g. 2 days ago)
Snapshot DAY 2 (e.g. 1 day ago)
Current state (changed today)

**Snapshot commands explained:**

**1) REVERT TO CURRENT SNAPSHOT (Ctrl+Shift+R)**

This will discard changes in the "Current State" and go back to how the machine was in the LAST = MOST RECENT snapshot we've done, that is DAY 2.

When to use this: e.g. You installed a crappy software and machine doesn't boot. So you want to go back. Result would be like if you would go to "Last Known Good Configuration" under Windows.

**2) DISCARD CURRENT SNAPSHOT AND STATE (Ctrl+Shift+B)**

This will discard changes in the "Current State" AND in "LAST = MOST RECENT snapshot" we've done, that is DAY 2 and it will go back to how it was on DAY 1.

When to use this: A) You installed crappy software before you took Snapshot DAY 2. So you need to go to DAY 1.  B) You decided to go back to ORIGINAL state of Virtual Machine (or to Initial Snapshot) and you don't need/want snapshots. Initial Snapshot is an option, you don't need it if you plan to revert to original state of virtual machine.

**3) DISCARD SNAPSHOT (Ctrl + Shift + D)**

This will be done without warning dialog! It will just delete the snapshot which is marked but keep the CURRENT STATE. The current state will have all changes up-to-date. If you want to delete all snapshots, you will have to do it to each of them. You can delete the snapshots in any order you like without effect on the current state.

When to use this: e.g. When you are satisfied with the current system state or your work and you don't need to keep the old(er) snapshots because you don't want to go back. It's like if you delete old Windows System Restore profiles to make more space in Windows.

----
_Important note:_ 

If you have done snapshots and you want to go back to original virtual machine you must to it the way in point #2 above. (At least I haven't found any other way.) If you try to delete snapshot manually (in Windows Explorer), you won't be able to load the machine. If you try to delete the machine from Virtualbox GUI, it will tell you it can't unregister because it has snapshots attached to it.

It is not possible to move snapshots between identical installations of same virtual machine because they have unique identifier in the file name.

_Some ideas ..._

However, it could be possible to copy snapshots between 2 computers with exactly identical virtual machines. If we create ONE snapshot AND take a copy of your virtual machine complete with that snapshot and copy it on a second computer (to possibly exact drive and location) and THEN we should be able exchange just the snapshot back and forth between computers and keep the whole virtual machine up-to-date. This remains a theory until somebody can prove. Perhaps, using Livemesh.com we could keep the virtual machines in sync that way. If we don't use Paging file in VM or it is deleted on machine shut-down, then the snapshot should be reasonably sized.

Maybe sounds like a crazy idea, but perhaps it may work for a limited number of cases when required. For instance, we would need to sync the whole machine state, not just the files changed (which of course can be done using USB flash drive, as well as using a shared folder which is then synchronized using Livemesh.com). Expanding on this, perhaps this could be a good idea for Sun Virtualbox to incorporate into next version of VB 4.x

[i]Anyway I'm talking too much. Hope this guide helps.
[/i]

---

### Post by frogotronic on 2009-11-13
So....


You can only take a snapshot of a virtual machine when its shutdown?  (i.e. not running)?

- CH

---

### Post by teohhanhui on 2009-11-22
> **cement_head said:**
> So....


You can only take a snapshot of a virtual machine when its shutdown?  (i.e. not running)?

- CH

No, you can take a snapshot when the virtual machine is running (Machine > Take Snapshot...)

---

### Post by markba on 2009-12-02
> **sleeping said:**
> Is there a way to have a "tree" of snapshots instead of a "line" of snapshots? The way the VBox GUI presents it, it leads me to believe I can build a whole hierarchy of snapshots, but I can't find how. Here's an example of what I would want:

```

base ---> snap1 ---> snap2 ---> snap3
      |          |
      |          |
      |          --> snap2.1 --- snap2.2
      |
      |
      --> snap1.1 ---> snap1.2 ---> snap1.3
                                |
                                |
                                --> snap1.3.1

```

The Snapshots tab in the VBox gui displays the snapshots in a tree-like fashion, which makes it appear that such a tree is possible. When I'm at snap3, I would like to go back to snap2 and "fork" a new state to make snap2.1, then go back to base and "fork" yet another state to make snap1.1.


VBox 3.1.0 provides just this. Snapshots are now on par with VMware Workststation.

---

### Post by coilwinder on 2010-03-13
@polocanada:

Thank you for clearing that up! :-) I've been afraid to mess with snapshots as they seem to revert my VM's unpredictably. I kind of still am. Talk about confusing command names in virtualbox! (Other than that, its a really great piece of software, of course!)


@sehe:
> Now the sickening irony is that I have ruined a good number of VMs and I have still to figure out whether you are (a) plain wrong (b) what the heck you mean by 'top' or 'bottom'. Top could mean: top of the window, top of the tree (ironically, the 'trunk'), the top of the snapshot stack (in the LIFO sense of the word, so: the actual leaf-node or treetop to be completely confusing)... mirror that for bottom.

It couldn't be more unclear. IMHO

Seth
I completely agree!

---

### Post by areteichi on 2010-03-13
> Latest version of Sun VirtualBox 3.1 under desktop virtualization software came with some new features including Branched Snapshots. Here I explain how branched snapshots works in VirtualBox with examples.
[http://www.sysprobs.com/branched-snapshots-virtualbox](http://www.sysprobs.com/branched-snapshots-virtualbox)

---

### Post by Tikkyca on 2010-03-13
> **dccrens said:**
> Great howto. I also have had a lot of issues with snapshots and understanding how they work. I love VB but their snapshot terminology really sucks. 

I still don't understand what to select to incorporate the current "machine state" or snapshot as the "default". 

Let say I have my original default VDI (a basic install). I take a snapshot on say 03/20/08. I then install some software and take another snapshot on 03/21/08. I install some more software and take a snapshot on 03/23/08. Everything is working good so I want to keep the machine state as it is on 03/23/08 with all of the software and changes. If I just "leave" the snapshots and do nothing I will be ok BUT the other previous snapshots are taking up disk space. So, is there a way to get rid of them and make the "last" snapshot I took on 03/23/08 the "only" disk image/snapshot???

Wow you have same icon as me :D

---

### Post by cometdog on 2010-03-17
OK, will try this without making reference to top or bottom.

let's say you have the following tree:

originalsnap -> snap1 -> snap2 -> current state

Just forget for a moment about how this is accomplished in terms of disk images and focus on the end result.  Pretend that each of these snapshots, including the "current state," is a full image of your disk some point in time (and memory, too, if the VM was powered up when you took the snapshot).  Then it should be clear that you don't lose any of your recent work by deleting originalsnap or snap1.  If you delete originalsnap, then you will simply never be able to revert back to that point in time.  You have not lost any data, though, since you still have "current state" intact.  You can delete the oldest one, or something from somewhere in the middle, without problem.

If you delete the newest one, "current state," then you will lose all information since snap2.  So don't go deleting things from the most recent end of the tree unless you really mean to.

It does get confusing when you start to try to think about this in terms of what is happening to the .vdi files as you add and delete snapshots, and how the contents are merged.  My advice is not to worry about it.

There are a couple of things that I haven't spelled out here, because I haven't tried them out myself.
* I believe that the "current state" actually behaves differently than other snapshots.  I think that if you revert to an older snapshot then your "current state" will actually be lost, even though you didn't explicitly choose to delete it.  I don't know though, since I haven't tried it.  The solution to this would be to take another snapshot to preserve the "current state" before reverting.
* I believe it is also OK to delete "snap2" (most recent snapshot, just before "current state"), and that your current state would be retained in this case.  But I have not tried this either.

---

### Post by maddentim on 2010-05-06
I just wanted to add that I read that you shouldn't copy the vdi virtual disk file.  apparently this hoses it (I assume that the problem would be in the copy file not the original).  Instead, you are supposed to use the vboxmanage clone command.  I am guessing that the uuid of original disk doesn't authenticate or something with the copied file.

---

### Post by maddentim on 2010-05-06
Also, one another thought, is each snapshot a whole bit for bit copy of the system or is it really just a difference from a reference version?

---

### Post by grazanaut on 2010-05-08
> **maddentim said:**
> Also, one another thought, is each snapshot a whole bit for bit copy of the system or is it really just a difference from a reference version?

The files themselves are really just differencing files, referencing the previous snapshot which references the one prior to that, and so on.

But I think the point being made here is that when managing snapshots from *within* VBox (or VBoxManage), you should *assume/pretend* they are bit-for-bit copies.

For example, if you "discard" a snapshot from somewhere in the middle of the tree/history:
[LIST]
[*]If each snapshot were a full copy of the disk, you could safely discard it
[*]...thus when doing this inside VirtualBox (or VBoxManage) you can assume the above to be the case
[*]Internally, however, the "diffs" in that snapshot are then merged into the next most recent one (so the snapshots either side of the one being discarded will appear not to have changed)
[*]WARNING: this is the mindset you need to use from *within* VirtualBox or VBoxManage, but you cannot use this mindset if you start messing with the physical VDI files themselves. Under the surface, they *are* just incremental diffs, so removing a physical VDI file from the middle of the chain will render any more recent snapshots useless
[/LIST]

---

### Post by grazanaut on 2010-05-08
> **UranUtan said:**
> 
Found this blog which explains perfectly how to manage VirtualBox snapshots and cloning a VDI which has snapshots:

[http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/](http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/)

There is an easier way, I discovered last night, which does not require you to merge/discard snapshots in order  to clone the most recent (or any) snapshot/state. I've posted the answer to the above blog post, but will add it here as well:

You do not actually need to do all the merges to clone the latest (or any) snapshot, as "VBoxManage clonehd" allows you to provide a snapshot identifier as an alternative to a VDI filename, and this merges all the changes up to the chosen snapshot into the output file.

You need to get the snapshot id for the drive first, but this is not difficult.
The following works from the VBox GUI, but there would also be a commandline way to do it:

[LIST=1]
[*]Select the VM, and click on "snapshots"
[*]Note the name/description of the snapshot you want to clone (if you want to clone "current state" you will need to snapshot this state first, and give it a name)
[*]Go to the "VirtualMediaManager" and expand the entire tree of the drive you want to clone
[*]Find the diff file relating to the snapshot you want to clone --> As you select each "child" or diff-file, the bottom of the window will display the full filepath/location, and also "Attached to: <VM Name> (<snapshot name>)" and it is the snapshot name that will help you find the relevant vdi file
[*]Once found, you are able to select and copy the location. It will be something like ".VirtualBox/Machines/MyVM/Snapshots/{297a42c0-236c-474b-af3c-6393b31518ef}.vdi" 
[*]Paste the location into a text editor and remove everything except the ID of the diff file, eg "297a42c0-236c-474b-af3c-6393b31518ef" (note, no braces or ".vdi" - just the ID)
[*]You can then use this ID to clone the snapshot, using CLONEHD (not clonevdi), eg "VBoxManage clonehd 297a42c0-236c-474b-af3c-6393b31518ef /home/myClonedVHD.vdi"
[/LIST]

And that's it - no need to merge all the snapshots - clonehd will do that for you for the new vdi, but leave the original chain/tree of snapshots untouched!

Edit: for the record, I did this on Mac OSX Snow Leopard, with Version 3.1.6 of VBox. The GUI for Ubuntu (which I also use) is pretty much the same, so the same instructions should still apply. I can't say for sure which version of VBox is the earliest one that let you use clonehd in this way, but VBox is one of those apps that's worth keeping right up to date anyway.

---

### Post by maddentim on 2010-05-10
Thanks, I am clear now.  My main concern that prompted my question was whether using snapshots would consume my hard drive by replicating the entire virtual drive, but I see now that the .VirtualBox folder includes the snapshot diff files and they are quite reasonable in size (so far!).  I think thinking these snapshots as diff files as the key to getting your head around how they work.

I wonder how much overhead using the snapshot files creates...  If you build up a bunch of snapshots, does it increase the latency of the process as the software navigates through the diff files??  Maybe it is loaded at runtime as a single thing making it negligible...

---

### Post by student-18 on 2010-06-26
hi, i ahve created multiple snaphots of different systems like ubuntu server10.4, windows xp , windows 2008 on virtual box. now i want to install virtual box on another system at work and use these snapshots to make new machines for the above mentioned operating systems.
but when i do so i get error message and the snapshot vdi is not enough i guess.
u need anything else for it? image also ?
any one can suggest .?

thanks

---

### Post by maddentim on 2010-06-27
I think you have to use the vdi manage clone command. Search google for a guide If you don't know how to clone.  If you use just use regular file system copy command, linux or otherwise, the copy will not function. Not sure why, seems like some sort of underlying security control related to the disk's uuid. > **student-18 said:**
> hi, i ahve created multiple snaphots of different systems like ubuntu server10.4, windows xp , windows 2008 on virtual box. now i want to install virtual box on another system at work and use these snapshots to make new machines for the above mentioned operating systems.
but when i do so i get error message and the snapshot vdi is not enough i guess.
u need anything else for it? image also ?
any one can suggest .?

thanks

---

### Post by grazanaut on 2010-06-28
> **maddentim said:**
> I think you have to use the vdi manage clone command. Search google for a guide If you don't know how to clone.  If you use just use regular file system copy command, linux or otherwise, the copy will not function. Not sure why, seems like some sort of underlying security control related to the disk's uuid.

Yes, he will need to use the vboxmanage clonehd command described elsewhere in this thread. Copying the latest snapshot is only copying the "differencing disk" and not the actual disk - using clonehd on the snapshot will get the whole disk.

Note that you will probably have issues with Windows - it will likely complain about the hardware having changed - you'll need to Google how to get around this as well.

---

### Post by CyberCod on 2010-07-12
Copying the .vdi doesn't work even if you're going to put it back in the same place as the original (in event of failure)?

Also, if I delete all of the snapshots and keep only the Current State, surely then there won't be any issues with copying the .vdi, no?

---

### Post by adamf663 on 2013-04-16
I was able to reattach an orphaned snapshot by going to the VM's settings, storage, deleting the drive and then readding the *snapshot* (found in .VirtualBox/Machines/<vmname>/Snapshots/

---

### Post by overdrank on 2013-04-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


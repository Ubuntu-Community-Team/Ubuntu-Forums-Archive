---
title: "Reformatting back to System76 original setup"
date: 2008-06-22
forum: System76 Support
---

### Post by glacialfury on 2008-06-22
As a new linux user, I've been messing around, installing, uninstalling, and generally playing with my system.  I've learned a lot, probably run a few commands I shouldn't have, and there are bits and pieces now that don't work as they should.  I don't know enough to fix them and I can't recall back to a certain point when they started occurring.  So, I'd like to reformat the system to the factory settings and start from a clean state, now that I know a little more.

My questions are:

1) I know that System76 comes with 3 partitions; one for the OS, one for the swap, and one for everything else.  Will formatting/reinstalling affect anything in the Home directory?  (ie, do I need to move my documents/music/etc to another computer before doing this).

2) Does linux need to be formatted and then reinstalled (a la Windows), or do you simply reinstall over your existing install?  What are the basic steps to do this?

3) What additional work needs to be done regarding the System76 driver or specific software in addition to the standard Ubuntu installation?

4) Do you think it's worth trying to track down specific problems rather than format/reinstall?  Am I taking too drastic a step here?

Edit: I have since fixed the problems, but the principle remains, should this happen again.

---

### Post by thomasaaron on 2008-06-23
> 1) I know that System76 comes with 3 partitions; one for the OS, one for the swap, and one for everything else. Will formatting/reinstalling affect anything in the Home directory? (ie, do I need to move my documents/music/etc to another computer before doing this).

For laptops and desktops, there is generally a 15GB root partition, a swap partition equal to the amount of memory installed, and a separate /home partition utilizing the remaining space. However, you can also just use the installation disk defaults for partitioning. The only difference there is that you won't have a separate partition for your /home dir.

Regarding a separate /home dir, the only reason I keep one is that, from experience, if your filesystem gets hosed on the other partitions, there is usually a way to mount the /home partition to save your important files, etc... When I'm re-imaging my computer, though, I never save the /home dir, as it contains a lot of config files that may or may not work perfectly with your new installation. Just my $0.02.

> 2) Does linux need to be formatted and then reinstalled (a la Windows), or do you simply reinstall over your existing install? What are the basic steps to do this?

Just install over the existing install.

> 3) What additional work needs to be done regarding the System76 driver or specific software in addition to the standard Ubuntu installation?

You would just need to re-install and run the System76 driver. It has a Restore function that will bring everything back to factory specs.

> 4) Do you think it's worth trying to track down specific problems rather than format/reinstall? Am I taking too drastic a step here?

Depends on the problem (which you didn't specify). Personally, on my own computers, I like to weigh the time I suspect it will take to find / fix the problem with the time it will take to install (about an hour, including custom configurations, software, etc...). Not everybody feels the same about it, but I image computers so frequently that it really doesn't have any impact on me.

---

### Post by hmfishing on 2010-06-06
Mr Thomasaarron my system76 starling netbook has this error message when i try to boot (process:309): GLib-WARNING **: getpwuid_r(): failed due to unknown user  id (0)
what should i do:confused::confused::confused:
please help

---

### Post by jml on 2010-06-07
hmfishing, you will probably get a faster response from Tom if you post your question on this forum as a new thread.  Attaching it to an old post (nearly 2 years old,) makes getting a response less likely.  If your Starling is still under warranty, you may want to e-mail Tom at "support@system76.com"  Without the quotation marks of course.  I'm affraid I do not know the meaning of the error message you posted.  Hopefully Tom will be able to help you.  Good luck.

Joe

---

### Post by isantop on 2010-06-07
hmfishing: I'll need a little more information. I can try and provide some solutions, but nothing more than general stuff until I learn a little more about your system.

First, I need to know the model of the computer you are using. Of you can manage to get to your desktop, you can check this by clicking on System > Administration > System76 Driver. The entry I need is labeled "System Model". 

Also, I need to know which version of Ubuntu you are using. With all of the big changes in recent versions, this can be especially important.

Now, for the general solution:

If you had a previous version of Ubuntu and upgraded to a newer version via the online update tool, you can run into problems. This happened a lot with upgrades from version 9.10 to 10.04 LTS, the most recent one. Installing Ubuntu fresh (from a CD) will probably fix the problem in this case. You can find instructions for that [Here](http://knowledge76.com/index.php/Restoring_Your_System).

Note that your problem may be something else, and while you can always try this, it can be time consuming, and is usually faster to wait for a more definitive answer.

---


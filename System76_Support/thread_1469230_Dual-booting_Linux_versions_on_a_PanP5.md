---
title: "Dual-booting Linux versions on a PanP5"
date: 2010-05-02
forum: System76 Support
---

### Post by japhyr on 2010-05-02
Hello,

I have been using ubuntu for 2 years now, and I am thinking about installations a little differently than I used to.  I am still running 9.04 on my panp5, because it has worked quite fine.  Since it has /home in its own partition, is it possible to create a new partition to install 10.04 alongside 9.04?

In the more general sense, can I create several partitions and install several different flavors of Linux?  I must admit some curiosity inspired by the new issue of Linux Journal.

---

### Post by miniyak on 2010-05-02
you mean using multiple file systems/OS partitions all sharing one home partition right?

i was curious and asked about this once. I think the general verdict was this was ok to do with same distro... Kinda missed how to do it though, it must be easy. I have just yet to try it out because i have forgotten to set things up that way when i switched to karmic... and to lucid... I guess its not too late to reinstall lucid though cause im still using karmic for the most part. (still have to get my bamboo pad up and working again in lucid plus stand-by and the graphics drivers)

---

### Post by bill516 on 2010-05-02
You might not have a problem so long as you are using two variations of the same distribution, but this can get messy with different sets of configuration files in the same home directory.  I think there really is a cleaner way.

etc/fstab holds a list of the files/devices and mount points for your distribution.  If you create a "documents" (or whatever name you like) partition you can edit etc/fstab so that your "documents" partition is automatically mounted to your Home partition when you start up.  That way the Home partition contains only the configuration files for your distribution.  A side benefit is that your home partition can be much smaller because "documents" will contain all of your personal files.  So if you are running two or three Linux distributions you can have this same "documents" partition mount to each Home partition on each distribution.  Doing so will keep all of your personal files in the same place regardless of the distribution you use.

Here is a link that I found quite good when I learned how to do this.  Just follow along and it should work.

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by japhyr on 2010-05-02
If I am understanding you right bill516, I would have something like this:
[LIST]
[*]partition 1: OS-1 /
[*]partition 2: OS-1 /home
[*]partition 3: OS-2 /
[*]partition 4: OS-2 /home
[*]partition 5: OS-3 /
[*]partition 6: OS-3 /home
[*]partion 7: data (largest partition)
[/LIST]

This seems straightforward, although I might be tempted to try it out on my old laptop before trying this on my main everyday laptop.

I have not seen tuxfiles.org before, that looks like a useful reference.

---

### Post by thomasaaron on 2010-05-03
If you're just wanting to try a bunch of different OSes, I'd not dual boot them. I'd download VirtualBox from the Ubuntu Software Center (or from Sun MicroSystems, if you want USB support) and create Virtual Machines. Then, if you don't like them, you can just delete the virtual machine to recover you disk space.

---

### Post by miniyak on 2010-05-03
i think more of a "easing upgrades" solution/trick is sought then a "trying out new things" one. 

One still needs a pretty powerful machine do anything practical with vbox, for example i still only have 1 dimm of 2gb ram in my panp5. Thinking of upgrading soon but till then thats kinda a limitation for everyday uses of VMs. Virtualbox itself is inherently unsuited for everyday uses regardless, unless you really need the resources of another platform and have dual screen set-up. Ive never gotten usb to work with it even using the non-free version to be honest... but maybe thats just a personal issue. Overall all i like it just to check new OSs out.

I'm dual-booting karmic and lucid right now and one thing that bothered me was that i got the option to import my settings from firefox... but nothing happend... if we had reliable settings importing/syncing tools, maybe though ubuntu one or something, i think this conversation would prob. be null.

---

### Post by japhyr on 2010-05-04
> i think more of a "easing upgrades" solution/trick is sought then a "trying out new things" one. 

I'm thinking of two things.  One is to refine the upgrading process on my main laptop.  The other piece is a little different. 

I run a high school program where I teach students to refurbish donated computers by installing ubuntu.  So I have a steady stream of used computers to work with, and I have watched a fair number of installations happen now.  I have students who are interested in seeing other flavors of Linux, but it would get complicated quickly to have more than a few machines running different flavors, all begging to be maintained well.  I'd rather develop in-school expertise with ubuntu, but it might be interesting to have one machine running a number of different distros.  It would also be a good demonstration for helping students understand the file system, and how partitions work.

Only the first has much to do with System 76, although as our program develops I have more and more students asking about my nice laptop that has never seen Windows on it!

---

### Post by bill516 on 2010-05-04
Hi Japhyr, sorry to have been AWOL.

Yes, you have a correct understanding of how I set up my drive and it works very reliably.

I agree with Tom Aaron, if all a person wants is a fast look, a virtual environment works.  But depending on what a person wants to learn it may not be the best testing environment.

I find several distributions useful so I like to keep them all on hand.  My setup does that nicely for me.  It might work well for you as well.

Good luck!

---

### Post by isantop on 2010-05-04
First, I'd recommend VirtualBox. It's much easier than just about any other solution out there, and there's virtually no risk of data loss.

Next on the tier is to shrink your existing Home partition, install Lucid normally, then set your existing home partition to mount automatically and create a symlink to your documents.

I wouldn't recommend sharing config files at all, especially since you are completely skipping a version (9.10). I managed to get a setup exactly like the one you want on my laptop, but I really only used on of the OS's, and mine was with Karmic and Lucid.

---

### Post by japhyr on 2010-05-05
Thanks everyone, these responses have clarified a lot for me.

---


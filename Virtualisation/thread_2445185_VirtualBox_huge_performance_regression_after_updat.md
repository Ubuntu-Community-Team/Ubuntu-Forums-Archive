---
title: "VirtualBox huge performance regression after update host to 20.04"
date: 2020-06-10
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2020-06-10
I upgraded my host machine from Xubuntu 18.04 to 20.04.  Since then, VirtualBox VMs have become epically slow.  It seems to be a similar issue to [this thread]("https://ubuntuforums.org/showthread.php?t=2427240").  Except in my case it affects much more than just kernel updates.

VirtualBox version before and after the OS upgrade remains at 6.0.22 (I can't use 6.1.x).  No changes were made to the guest VMs.  The only change is the host OS.

I'm uneasy about trying the solution from the other thread, because I do some heavy work loads in my VMs (e.g. compiling software) and I need to be able to use the host OS while that's going.  And I never needed to use host I/O cache before.

How to get VirtualBox VM performance to at least as good as what it was under 18.04 host?
Is it unreasonable for me to be concerned about using host I/O cache?

---

### Post by SeijiSensei on 2020-06-10
If you follow the process at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) for "Debian-based" systems, you should be able to install 6.1.  I'm on 6.1.10, but I haven't updated lately.

Use "eoan" when you create the sources.list entry for this version, because there isn't a binary for "Focal Fossa" yet.  

```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian eoan contrib
```

I create the file /etc/apt/sources.list.d/virtualbox.list and put that deb statement in there.  Don't forget to run "sudo apt update" when you've made these changes but before you install virtualbox-6.1.

---

### Post by &amp;KyT$0P# on 2020-06-11
"can't use 6.1.x" because 6.1 removed features without full replacement for the lost functionality.  It's not clear if/when the lost functionality is coming back.  I need to continue using 6.0.x for the foreseeable future.

---

### Post by ajgreeny on 2020-06-11
I am using VBox 6.1.10 on Xubuntu 20.04 with guests of Lubuntu and Ubuntu 20.04.

At the linux-image and headers install yesterday and again today on two separate machines there has been a huge delay (perhaps 15 - 20 minutes) when unpacking the packages.
All other packages when installing act normally and without the delay, and I do not see any other performance hits that I'm aware of, and prior to using 20.04 as host I never saw any problems of this sort.

Incidentally, if you use the debian based distro method of installing direct from the virtualbox repos directly, as mentioned by SeijiSensei above, you can now use "focal" instead of "eoan" in the line of text added to sources.list file, ie, ```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib
```
EDIT:

PS:
I also have a problem enabling touchpad scrolling in these VMs as mentioned in the thread I started at [https://ubuntuforums.org/showthread.php?t=2444679](https://ubuntuforums.org/showthread.php?t=2444679)
No replies to that so far, but it is very annoying having to add a mouse which scrolls fine with the wheel.

---

### Post by &amp;KyT$0P# on 2020-06-11
Ok, I tried enabling use host I/O cache as a test, being careful to pick a VM with not-too-large HDD file and trying not to do anything too heavy, and watching resource usage.  I tested updating the system (which happened to include kernel updates) and installing some packages.  Not only did using host I/O cache seem to eliminate the performance problem, I think it might be faster than what I had before under 18.04 :-k

So this might be an answer to my first question, but I still wonder how uneasy I should be about this setting for my general use of these VMs, especially the heavier loads?

---

### Post by ajgreeny on 2020-06-12
Interesting!

I have "Host I/O cache" enabled on my *ubuntu guests and have had since they were installed, and I will now try disabling it to see if it makes any difference.  

From what you say it appears it may make kernel installation even slower than it is at present if that's possible.
We shall see; watch this space and I'll report back as soon as I can.

---

### Post by ajgreeny on 2020-06-12
I have created a thread at the VBox forums regarding this problem and one of the VBox volunteers is trying to help with this problem.
[https://forums.virtualbox.org/viewtopic.php?f=7&t=98586&p=478107#p478107](https://forums.virtualbox.org/viewtopic.php?f=7&t=98586&p=478107#p478107)

---

### Post by ajgreeny on 2020-06-13
Oh dear!

Having  said that I already have the Host I/O cache enabled on my VMs, a more careful investigation shows that it was, unfortunately, only the IDE CDrom disk that was in that state, the SATA Virtual hard disk was still not running with Host I/O Cache enabled.

I have now done so, and tested by removing, then reinstalling a kernel and like you, the problem has now disappeared.

---

### Post by &amp;KyT$0P# on 2020-06-22
> Is it unreasonable for me to be concerned about using host I/O cache?

> I still wonder how uneasy I should be about this setting for my general use of these VMs, especially the heavier loads?

I ended up needing to reinstall my 20.04 VM and I have used it for what I think are some "moderate" loads (including customising a live CD).  This stuff cause the host to use a few MB of swap.  And there were some noticeable performance glitches during these loads.

So I still hesitate to just try the heavy loads and see how it goes, even if I do backup my system first.

I did find [this]("https://forums.virtualbox.org/viewtopic.php?t=45245"), but it is almost 10 years old and I don't know how that info would apply to the multiple-virtual-disk setup I use for the heavy software compiling loads?

Advice would be appreciated. :)

---

### Post by ajgreeny on 2020-06-22
Judging by what is said in the blog at [https://www.electricmonk.nl/log/2016/03/14/terrible-virtualbox-disk-performance/](https://www.electricmonk.nl/log/2016/03/14/terrible-virtualbox-disk-performance/) which is linked to in one of the threads mentioned above, I suspect you should not have too many problems, though this may depend on how you run your VMs.
> 2. Disk image files tend to be very large. Caching them can therefore
quickly use up the entire host OS cache. Depending on the efficiency
of the host OS caching, this may slow down the host immensely,
especially if several VMs run at the same time. For example, on Linux
hosts, host caching may result in Linux delaying all writes until the
host cache is nearly full and then writing out all these changes at
once, possibly stalling VM execution for minutes. This can result in
I/O errors in the guest as I/O requests time out there.
Personally I never run more than one VM at a time so I believe from that behaviour that my system should be OK; my own experience also points to this being so.

---

### Post by &amp;KyT$0P# on 2020-06-23
Hmm.  I too have 16 GB physical RAM, same as the author of that blog entry.

I sometimes do run a couple VMs concurrently, and haven't noticed any problems at all with that and host I/O cache.  Then again, I don't do heavy loads with multiple VMs running, and I did temporarily reduce the RAM of at least one VM.

Ah, key word in that quote is "immensely".  So far that has not been my experience at all.  I think I will backup my system and then just try some heavy loads and report back.  Thanks!

---

### Post by &amp;KyT$0P# on 2020-06-23
Just tested some heavy loads with host I/O cache enabled.  That lot drove host swap usage up to only 26 MB.  And the host had only one or two minor performance glitches over a few hours of heavy load.  So I think I should be good to use host I/O cache :KS

(With numbers like that, I would wonder if reducing the amount of RAM of the VM by up to 512 MB would completely avoid swap usage?  Is it worth trying?)

Unfortunately I'm not sure if the heavy loads might still have performance regression compared to under 18.04 host.  Like approximately an extra 10 minutes on workloads that under 18.04 host lasted 1-2 hours.  Now I did update that guest since using it under 18.04 host.  And I was intentionally pushing things in a way I know can slow this down, but I don't recall it being that significant? :-k

---

### Post by &amp;KyT$0P# on 2020-06-24
I did try reducing the VM's RAM slightly.  It significantly reduced swap usage.  And it improved performance of the heavy load.  Still not as good as it was under 18.04 host, but I got close.  I think my VMs might just be slightly over-provisioned for using host I/O cache.

---

### Post by ajgreeny on 2020-06-25
> **halogen2 said:**
> I did try reducing the VM's RAM slightly.  It significantly reduced swap usage.  And it improved performance of the heavy load.  Still not as good as it was under 18.04 host, but I got close.  I think my VMs might just be slightly over-provisioned for using host I/O cache.Interesting thought!
I the past I have always provisioned my VMs with as much RAM as I could from the host, ie 4G from the host's  8G, but perhaps reducing it to 3G or 3.5G is worth a try.

I am not seeing any real problems now, though, with the host I/O cache enabled, as I don't  use the VMs for any heavy load work; they are simply to test different DE versions of 20.04 or totally different distros

---

### Post by ajgreeny on 2020-06-25
I reduced the RAM of my VMs that had 4G to 3G RAM and I am pleasantly surprised that it seems to make them all run smoother and quicker, particularly an Arcolinux-Xfce VM which suddenly is now booting to a full xfce4 GUI in about 10 seconds, much faster than before.

This has certainly made me rethink the resources that I set for any VMs in future!

---

### Post by &amp;KyT$0P# on 2020-06-26
... and solved.

To sum up:

1) Enable "Use host I/O cache" for the SATA controller with the VM's hard disk(s).

2) Then, if the VM inevitably causes the host to use swap, reduce the RAM of the VM.  Reduce at least to the point the host seems not to need swap, and possibly some beyond that.  I reduced mine to 6 GB (6144 MB).  There seems to be something special about that number I don't understand.  Even small deviations in either direction result in measurably worse performance on heavy loads :?

Anyway, with these changes my VirtualBox VMs performance is slightly better than before under 18.04 host. 8-)

---


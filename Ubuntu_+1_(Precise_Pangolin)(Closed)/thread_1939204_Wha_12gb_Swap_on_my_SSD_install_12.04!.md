---
title: "Wha? 12gb Swap on my SSD install 12.04!?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Fictitious1 on 2012-03-11
So I just did a standard install of 12.04 LTS on a new SSD.  64gb M4 - its pretty fast, but I just notice like now a couple hours after installing everything that it created a 12gb swap!! - thats crazy --  I have 12gb memory - but I really think that's a waste of my precious ssd space-- can I get rid of that without having to reinstall?  Should I get rid of that?

Thanks

---

### Post by Fictitious1 on 2012-03-11
Think I found the answer here  - looks like I'm going to have to reinstall again from scratch - 

[http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)

I think it shows I don't need swap on a desktop because it seems from that it is mostly for hibernating.  I have 3 other HDD in the machine I guess I could put swap on if I absolutely had to, but from what I'm reading it does not seem necessary.

---

### Post by Elfy on 2012-03-11
Why do you have to reinstall to deal with swap?

I've never done that.

---

### Post by howefield on 2012-03-11
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by fabricator4 on 2012-03-11
> **forestpiskie said:**
> Why do you have to reinstall to deal with swap?

I've never done that.

Agreed.  Boot off the LiveCD, then delete the swap partition and resize the ext4 partition.  You'd also edit /etc/fstab on the SSD to remove reference to the swap partition.

Chris.

---

### Post by oldfred on 2012-03-11
Why would anyone want to hibernate with an SSD. My new (low end) SSD booted in 20 sec and after reconfiguring to mount everything from my rotating drives now is 25% slower or a whopping 25sec.

Some say it does take slightly longer to boot if no swap is found, but with 12GB of RAM you would have to be running every program Ubuntu offers and editing videos. You normally do not even want to use swap as then you are not running system at RAM speed but drive speed. 

You can edit fstab to remove swap entry and then modify swap partition.

I normally install to 20 to 25GB / (root) partitions. So with my new 60GB SSD, I put two / partitions. One for current install and one for next install. All data is on rotating drives, but /home is still in /.

---

### Post by dino99 on 2012-03-11
can also tweak swappiness

---

### Post by durand on 2012-03-11
Yeah, I agree with the others. You could also suspend to RAM instead of hibernating. Not exactly the same thing but it is much more useful in my opinion. With 12GB ram, I'd get rid of swap completely.

---

### Post by effenberg0x0 on 2012-03-11
I can see some need for hibernation when the battery goes critical. My current laptop boots really fast (I5, 16GB, Corsair SSD). I have no problems with shutting it down and powering on again. But s happens eventually: You leave it on while working on something complex and go to lunch, have a walk, visit a client, etc and forget to save your stuff. When you come back you see power was out for more time than your batteries could handle, you lost your stuff. Or you forget it unplugged in someones desk when and you're called for a meeting that unfortunately takes more than 3 or 4 hours. Adios unsaved stuff. 

As with most current issues we have in the OO and PP cycle, most mistakes come from two sources:

- When we try to judge if a feature is useful or not and simply eliminate it without proper research. What percentage of Ubuntu users need hibernation, even when using an SSD? I have no idea. The truth is that no one does.
- The lack of proper and working GUI (gnome-control-center-like) controls to enable/disable/customize features justifies excluding a feature or enabling it as a default.
 
Hibernation is a common feature in modern OSs. Some people use it, that's enough for the feature to exist, as long as it can be enabled/disabled/customized by any average-user via GUI. And activating it via GUI could dynamically create a swap file, there's no need for a partition. 

It's exactly like Plymouth. There's no interface for enabling/disabling/customizing it via GUI, so let's assume most people like it and make it a default. Great. Well, it seems like a lot of people don't want it. How many percent? No idea - but there are users that don't want it: that should be enough to make it controllable via GUI.

Now, can we really find 200 Million PC users, all willing to not use Windows, and all with the exact same preferences regarding all default features? Wouldn't it be easier to find 200 Million users and let they configure the system as they wish?

Regards,
Effenberg

---

### Post by Fictitious1 on 2012-03-12
Just tried booting from 12.04 LTS live - could not do it.. got stuck at the try/install screen and tried every combination of keys i could to get gparted to open. Could get about everything but that open.  Tried a 11.10 cd and a 10.04 Cd but black screened after the keyboard=person screen -  so don't know where to go to try to get it resized -

---

### Post by dcstar on 2012-03-12
> **Fictitious1 said:**
> Just tried booting from 12.04 LTS live - could not do it.. got stuck at the try/install screen and tried every combination of keys i could to get gparted to open. Could get about everything but that open.  Tried a 11.10 cd and a 10.04 Cd but black screened after the keyboard=person screen -  so don't know where to go to try to get it resized -

Boot normally, then:

```
sudo swapoff -a
sudo gedit /etc/fstab
```
Download a gparted CD and boot off that.

---

### Post by durand on 2012-03-12
> **Fictitious1 said:**
> Just tried booting from 12.04 LTS live - could not do it.. got stuck at the try/install screen and tried every combination of keys i could to get gparted to open. Could get about everything but that open.  Tried a 11.10 cd and a 10.04 Cd but black screened after the keyboard=person screen -  so don't know where to go to try to get it resized -

To get to gparted, you have to click on Try, then search for gparted in the dash.

---

### Post by cariboo on 2012-03-12
Gparted isn't installed by default, it's part of the Live CD, but not a normal install. You can of course install it, using your favourite method of installing packages.

---

### Post by kansasnoob on 2012-03-12
> **Fictitious1 said:**
> Just tried booting from 12.04 LTS live - could not do it.. got stuck at the try/install screen and tried every combination of keys i could to get gparted to open. Could get about everything but that open.  Tried a 11.10 cd and a 10.04 Cd but black screened after the keyboard=person screen -  so don't know where to go to try to get it resized -

Getting stuck at the try/install screen along with the black screen in older versions makes me think it's graphics chip related, so when you boot the live CD and the keyboard/person screen appears press a key (you have a whopping 3 seconds to do so) and select language. Then the boot menu will appear so press F6 (I think) and select "nomodeset" to see if that'll get you to the live desktop.

Then you should be able to use Gparted from the live desktop to delete that swap partition, grow the Precise root partition, and create a new swap elsewhere. But I have a few additional hints about creating a new swap.

Once the new swap is created be sure to identify it's location once you've booted into your installed Precise again. The easiest way is to run:

```
sudo fdisk -l
```

Example output:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84646484    42323211   83  Linux
/dev/sda2        84646485   168313004    41833260   83  Linux
/dev/sda3       168313005   252349019    42018007+  83  Linux
/dev/sda4       252350462   976768064   362208801+   5  Extended
/dev/sda5       631209978   730464255    49627139   83  Linux
/dev/sda6       738861543   843637409    52387933+  83  Linux
/dev/sda7       843637473   950919479    53641003+  83  Linux
/dev/sda8       950919543   971852174    10466316   83  Linux
**[COLOR="Red"]/dev/sda9[/COLOR]       971852238   976768064     2457913+  82  Linux swap / Solaris**
/dev/sda10      588637728   631209914    21286093+  83  Linux
/dev/sda11      546161868   588637664    21237898+  83  Linux
/dev/sda12      503878788   546161804    21141508+  83  Linux
/dev/sda13      460904913   503878724    21486906   83  Linux
/dev/sda14      295001721   336144059    20571169+  83  Linux
/dev/sda15      336144123   377318654    20587266   83  Linux
/dev/sda16      377318718   419119784    20900533+  83  Linux
/dev/sda17      419119848   460904849    20892501   83  Linux
/dev/sda18      252350464   295000063    21324800   83  Linux

Partition table entries are not in disk order

```

You'll notice that I put the swap in bold and used red to highlight the device designation. You'll need to use that "/dev/sdXY" in just a bit.

Then also run both of these commands to check UUID's:

```
cat /etc/fstab | grep swap
```

```
cat /etc/initramfs-tools/conf.d/resume
```

```
lance@lance-desktop:~$ cat /etc/fstab | grep swap
# swap was on /dev/sda9 during installation
UUID=**[COLOR="Red"]80627269-1ccd-4774-b4ea-a5ef8824ffaa[/COLOR]** none            swap    sw              0       0
lance@lance-desktop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=**[COLOR="Red"]80627269-1ccd-4774-b4ea-a5ef8824ffaa[/COLOR]**

```

Those UUID's should match, if not just stop and ask for additional advice, but if they do match you'll need to use that UUID to properly assign the newly created swap. It's simple really, just two commands:

```
sudo mkswap -U <original swap UUID> /dev/sdXY
```

Note: You will of course replace both "<original swap UUID>" and "/dev/sdXY" with what you found running those previous commands, **[COLOR="Red"]example only[/COLOR]**:

```
sudo mkswap -U &#65279;80627269-1ccd-4774-b4ea-a5ef8824ffaa /dev/sda9
```

Then just run:

```
sudo swapon -a
```

Then reboot and run:

```
free -m
```

Which should show all available RAM and SWAP ;)

Let us know how you get along.

---


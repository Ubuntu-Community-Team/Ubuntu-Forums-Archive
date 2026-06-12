---
title: "what happened to gnome-disk-utility?"
date: 2012-06-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-07
what happened to gnome-disk-utility and all of it's features?

---

### Post by mc4man on 2012-06-07
Well this is the new version & like a lot of new gnome stuff is visually understated. I'd image you'd find most of the previous well laid out & upfront options there, somewhere..

---

### Post by cariboo on 2012-06-07
As far as I'm concerned, it's broken. The rewrite left out some features that I used all the time, Remote server access is missing. Bug #[lpbug]1004094[/lpbug].

---

### Post by Gompa on 2012-06-08
yeah and all the benchmark features are missing to ? its kinda weak

---

### Post by zika on 2012-06-08
> **Gompa said:**
> its kinda weakYou meant „its kinda tweak“ ... ;) ?

---

### Post by philinux on 2012-06-09
> **ventrical said:**
> what happened to gnome-disk-utility and all of it's features?

Horrible backwards step.

[edit] The user interface I mean. And this.

> If there is one mantra that has driven this effort, it may very well be "don't try to expose everything in a desktop user interface" and I think this is something that extends to the greater GNOME 3 effort as well.

From blog link in post #17

---

### Post by mc4man on 2012-06-09
One could file a bug on though bugs of this nature, (crap interface, limited options, ect.) don't generally go over to well, though you never know

_For the moment_ the old gnome-disc-utility (3.0.2) is still installable & usable though it isn't set to use udisks2
(and will mount to /media instead of /run/ & maybe other not correct behavior

The new gnome-disc-utility is where one is getting the 'Disk Image Mounter' option so the package did do something positive
 

Atm there still is a gdu-notification-daemon.desktop in autostart that trys to run but can't do so for obvious reasons

---

### Post by ronacc on 2012-06-09
you can download the REAL gdu from here not the " oh no we never dumb things down version" [ http://packages.debian.org/source/sid/gnome-disk-utility ]( http://packages.debian.org/source/sid/gnome-disk-utility ) , see SS ,the deb installs just fine with dpkg .

---

### Post by mc4man on 2012-06-09
I wouldn't expect the interface to improve with a newer version - 
tried the latest git which may or may not make it into 12.10, (needs libpwquality which isn't in ubuntu yet) & it looks just the same so I guess they are happy with it..

---

### Post by ventrical on 2012-06-09
> **cariboo907 said:**
> As far as I'm concerned, it's broken. The rewrite left out some features that I used all the time, Remote server access is missing. Bug #[lpbug]1004094[/lpbug].

  I used it as a benchmarker to test my drives' speed. I always considered it a alpha/beta testing tool. As it is now it is completely useless unless there are other disk testing apps in the SC. I'll take a look.

---

### Post by ventrical on 2012-06-09
> **ronacc said:**
> you can download the REAL gdu from here not the " oh no we never dumb things down version" [ http://packages.debian.org/source/sid/gnome-disk-utility ]("http://packages.debian.org/source/sid/gnome-disk-utility") , see SS ,the deb installs just fine with dpkg .


Here is what happened.

```
ventrical@ventrical-Dell-DV051:~/Downloads$ sudo dpkg -i gnome-disk-utility_3.0.2-2_i386.deb
dpkg: warning: downgrading gnome-disk-utility from 3.5.1-0ubuntu3 to 3.0.2-2.
(Reading database ... 146554 files and directories currently installed.)
Preparing to replace gnome-disk-utility 3.5.1-0ubuntu3 (using gnome-disk-utility_3.0.2-2_i386.deb) ...
Unpacking replacement gnome-disk-utility ...
dpkg: dependency problems prevent configuration of gnome-disk-utility:
 gnome-disk-utility depends on libavahi-ui-gtk3-0 (>= 0.6.30); however:
  Package libavahi-ui-gtk3-0 is not installed.
 gnome-disk-utility depends on libgdu-gtk0 (>= 3.0.0); however:
  Package libgdu-gtk0 is not installed.
dpkg: error processing gnome-disk-utility (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 gnome-disk-utility
ventrical@ventrical-Dell-DV051:~/Downloads$ 

```

and when I click the icon I get nothing.

---

### Post by mc4man on 2012-06-09
> **ventrical said:**
> Here is what happened.

```
sudo apt-get install libgdu-gtk0 
```
Which will also install libavahi-ui-gtk3-0

You could use this package if desired, under "Builds"
[https://launchpad.net/ubuntu/+source/gnome-disk-utility/3.0.2-2ubuntu8](https://launchpad.net/ubuntu/+source/gnome-disk-utility/3.0.2-2ubuntu8)

---

### Post by Mr. Picklesworth on 2012-06-09
There are some cool *new* features, though ;)

If you head to the Actions menu for a partition you can edit all of its mount options, and it has a very capable dialog for doing it. You can also create, restore and mount disk images.

For some reason I recall that benchmarking might be pulled to a standalone application, but perhaps that didn't happen&#8230; it would be nice if that *did*, because it was a nice function to have.

Meanwhile the stuff to configure RAID / LVM was removed because the theory is someone who wants these things probably would be happy to edit [config files]("http://tldp.org/HOWTO/LVM-HOWTO/") manually. Can't say I agree with that, but I imagine some separate GUI tools would do the job better than the built in disk manager since they don't need to be included by default. It's a shame we don't seem to have many such things.

---

### Post by ronacc on 2012-06-09
> 
and when I click the icon I get nothing.

I'm running gnome shell so I already had the depends , forgot to mention that , sorry .

---

### Post by ventrical on 2012-06-11
> **mc4man said:**
> ```
sudo apt-get install libgdu-gtk0 
```Which will also install libavahi-ui-gtk3-0

You could use this package if desired, under "Builds"
[https://launchpad.net/ubuntu/+source/gnome-disk-utility/3.0.2-2ubuntu8](https://launchpad.net/ubuntu/+source/gnome-disk-utility/3.0.2-2ubuntu8)


Thanks Mac. I tried to get it running but it kept comming back with broken depends so I removed it and re-installed the 'disk-utility'.

---

### Post by ventrical on 2012-06-11
> **ronacc said:**
> I'm running gnome shell so I already had the depends , forgot to mention that , sorry .


No problem ronacc. I learn something new everyday. There is so much stuff, so many hidden treasures in Ubuntu that I got to be willing to even bust or bork up my systems once in a while. 

  I should have mentioned I was using Unity 3D.

---

### Post by hugmenot on 2012-06-11
Here’s the developer’s blog post about the changes:

[http://davidz25.blogspot.de/2012/03/simpler-faster-better.html](http://davidz25.blogspot.de/2012/03/simpler-faster-better.html)

---

### Post by ventrical on 2012-06-11
> **Mr. Picklesworth said:**
> There are some cool *new* features, though ;)

If you head to the Actions menu for a partition you can edit all of its mount options, and it has a very capable dialog for doing it. You can also create and restore disk images.

For some reason I recall that benchmarking might be pulled to a standalone application, but perhaps that didn't happen… it would be nice if that *did*, because it was a nice function to have.

Meanwhile the stuff to configure RAID / LVM was removed because the theory is someone who wants these things probably would be happy to edit [config files]("http://tldp.org/HOWTO/LVM-HOWTO/") manually. Can't say I agree with that, but I imagine some separate GUI tools would do the job better than the built in disk manager since they don't need to be included by default. It's a shame we don't seem to have many such things.


 Yes.. thanks .. I had just seen this.

---

### Post by ventrical on 2012-06-11
> **hugmenot said:**
> Here’s the developer’s blog post about the changes:

[http://davidz25.blogspot.de/2012/03/simpler-faster-better.html](http://davidz25.blogspot.de/2012/03/simpler-faster-better.html)


Thank you.

---

### Post by ventrical on 2012-06-11
So I tried to create a disk image and got this:

---

### Post by Mr. Picklesworth on 2012-06-11
> **ventrical said:**
> So I tried to create a disk image and got this:

Ack! Looks like it needs the disk or volume to be unmounted, so for your root filesystem you'd need to run that from a live usb. I guess the time I used that feature was with something that already _was_ unmounted.

Horrible error message, though. That looks like a bug to me (in more ways that one&#8230;) so I filed a bug report over here: [https://bugzilla.gnome.org/show_bug.cgi?id=677869](https://bugzilla.gnome.org/show_bug.cgi?id=677869)

---

### Post by bash on 2012-06-15
Benchmarks just made a comeback. So everyone can put out their torches again and move on to bugging whatever maintaner is in charge of getting this into Ubuntu.

Commit: [http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c](http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c)

Screenshot: [http://people.freedesktop.org/~david/disks-show-sample-size-and-num-samples.png](http://people.freedesktop.org/~david/disks-show-sample-size-and-num-samples.png)

---

### Post by mc4man on 2012-06-15
> **bash said:**
> Benchmarks just made a comeback. So everyone can put out their torches again and move on to bugging whatever maintaner is in charge of getting this into Ubuntu.

Commit: [http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c](http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c)

Screenshot: [http://people.freedesktop.org/~david/disks-show-sample-size-and-num-samples.png](http://people.freedesktop.org/~david/disks-show-sample-size-and-num-samples.png)
Couldn't find an upstream bug associated with that commit??, so started here (if you know of please link
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885)

---

### Post by Mr. Picklesworth on 2012-06-16
> **mc4man said:**
> Couldn't find an upstream bug associated with that commit??, so started here (if you know of please link
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885)

Why make a new bug report for that? If it's committed, it's coming once it has a release and its dependencies are caught up downstream. I don't see how a bug report will affect the operation in a meaningful way. Perhaps I'm missing something? ;)

---

### Post by flemur13013 on 2012-06-16
It's easy to downgrade to palimpsest v.3.0.2 with synaptic:

  Package->Force version

---

### Post by ventrical on 2012-06-16
> **Mr. Picklesworth said:**
> Ack! Looks like it needs the disk or volume to be unmounted, so for your root filesystem you'd need to run that from a live usb. I guess the time I used that feature was with something that already _was_ unmounted.

Horrible error message, though. That looks like a bug to me (in more ways that one…) so I filed a bug report over here: [https://bugzilla.gnome.org/show_bug.cgi?id=677869](https://bugzilla.gnome.org/show_bug.cgi?id=677869)

Ok.. thanks Mark. I am still just experimenting with this. I will try that out.

---

### Post by ventrical on 2012-06-16
> **flemur13013 said:**
> It's easy to downgrade to palimpsest v.3.0.2 with synaptic:

  Package->Force version

Tried this too but got broken depends so I installed back to original 'disk'.. I'll try again.

---

### Post by ventrical on 2012-06-16
Oooohhh Boy .. OK!  I got it running and it started to create the WHOLE disk image (29GBs) which is actually what it should do. So I had to cancell it. I can see now that this tool can be used  to create a clone or use another disk as a back up. I think I misunderstood the capabilities of this tool.

---

### Post by EgoGratis on 2012-06-19
Mixed feelings:

I do like some of the new features a lot and i am quite happy with the new version.

I don't know why removing GUI management for more complex disk management is a good thing. 

Linux lacks GUI editors and removing current ones is by definition a giant step back and i don't  think Linux in general is in position that it can afford removing GUI editors.

---

### Post by ventrical on 2012-06-19
I have always thought since I have been using the 'disk-utility' tool that it has been a handy and rather good beta-benchmarking tool to test for speed of data_transfer. After seeing those result I could then have some data to go on to make my next  trouble shoot.

---

### Post by EgoGratis on 2012-06-19
If i understand correctly benchmarking tool was added back and it was improved too and yes i use it a lot too.

---

### Post by mc4man on 2012-06-19
> **Mr. Picklesworth said:**
> Why make a new bug report for that? If it's committed, it's coming once it has a release and its dependencies are caught up downstream. I don't see how a bug report will affect the operation in a meaningful way. Perhaps I'm missing something? ;)

Maybe it will, maybe it won't (show in 12.10
Just because someone fixes something upstream doesn't mean it will make it into the the current ubuntu dev, things have tendency to fall by the wayside recently (11.10 had quite a number

---

### Post by ventrical on 2012-06-20
> **EgoGratis said:**
> If i understand correctly benchmarking tool was added back and it was improved too and yes i use it a lot too.

Nope! Not here anyways.

---

### Post by EgoGratis on 2012-06-20
[http://ubuntuforums.org/showpost.php?p=12029793&postcount=22](http://ubuntuforums.org/showpost.php?p=12029793&postcount=22)

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1013885)

---

### Post by ventrical on 2012-06-20
> **bash said:**
> Benchmarks just made a comeback. So everyone can put out their torches again and move on to bugging whatever maintaner is in charge of getting this into Ubuntu.

Commit: [http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c](http://git.gnome.org/browse/gnome-disk-utility/commit/?id=e2c6aeeb79fe6e938e2b38c47ee3ac69a892950c)

Screenshot: [http://people.freedesktop.org/~david/disks-show-sample-size-and-num-samples.png]("http://people.freedesktop.org/%7Edavid/disks-show-sample-size-and-num-samples.png")


?? nadda

and this is on another system (Dell dimension 3100)

 I tried to use the synaptic work-a-round .. but no go.

what am I doing wrong.?

---

### Post by EgoGratis on 2012-06-20
The "BUG" needs to get fixed first. Benchmark tool was removed (this is what we have now) and then added back but this last "upstream change" is not available in  Ubuntu 12.10 at this moment.

I don't know what the procedure is but hopefully "upstream change" will land in Ubuntu 12.10 soon. Benchmark tool was removed and then reintroduced again and we will be able to use it in the future too hopefully it will be available in Ubuntu 12.10 ASAP we just have to wait a bit for this to happen!

---

### Post by jbicha on 2012-06-20
The next release of gnome-disk-utility (with benchmarking re-enabled) is scheduled for next week. I expect that it will land in quantal soon after (reasonable chance that it will happen next week too).

[https://live.gnome.org/ThreePointFive](https://live.gnome.org/ThreePointFive)

[https://bugs.launchpad.net/ubuntu/+bug/1011361](https://bugs.launchpad.net/ubuntu/+bug/1011361)

---

### Post by EgoGratis on 2012-06-20
Great!

---

### Post by ventrical on 2012-06-20
> **jbicha said:**
> The next release of gnome-disk-utility (with benchmarking re-enabled) is scheduled for next week. I expect that it will land in quantal soon after (reasonable chance that it will happen next week too).

[https://live.gnome.org/ThreePointFive](https://live.gnome.org/ThreePointFive)

[https://bugs.launchpad.net/ubuntu/+bug/1011361](https://bugs.launchpad.net/ubuntu/+bug/1011361)

Thanks for the update Jeremy!

Thanks for the clarification EgoGratis.

---


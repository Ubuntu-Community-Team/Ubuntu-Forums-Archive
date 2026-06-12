---
title: "My Whacky RAID Install of Quantal Alternate:)"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-10-03
I don't want to hijack Nick's page so I thought I would put this up here.

I decided to zsync quantal-alternate-i386.iso and it updated from Sept. 10th/2012. I guess that was the shut off point.

I hooked up 4 Maxtor IDE drives to a VIA MoBo, 2.8GHz with ATi Radeon(Unity 3d Friendly).

With a lot of tweaking and working in the partitioning manager everything went well until I accepted 'Finish'. The warning told me that It could not find the target. I went back and found out that I rooted (/) the wrong disk. After cleaning up that and resetting everything - when I click finish  the setup will not recognize (sda1(0.0.0) as root even though I set it up in partioner manually. So, basically what is happening is that it appears the 'settings' are being wiped out after I 'finish' and it will not install.

 I am going to try again.

**edit**

Please delete those crappy screenshots !:)

Thanks.

---

### Post by ventrical on 2012-10-03
Ahem.... It *is* important to note that once the  hdd array is set up for RAID that, unless it is  formatted and system installed that  on some machines the DMI pool data stage of boot-up will lock up and freeze, emulating a busted machine and I can see no other alternative that to re-formtat those hdds  on another system because USB will not boot up once DMI is locked.!

:)

Wow . what fun ! :)

---

### Post by ventrical on 2012-10-03
Iv'e done this before and have been successful :)lol

  I decided to take a small back-step and use 2 hdds, then I will up it to four. I will be using the old quantal alpha iso.

---

### Post by ventrical on 2012-10-05
I had seen the other cross post on this topic. I decided to try setting up RAID using a Lucid CD and a program called 'mdadm' from Ubuntu software center: on another PC.
(note- the PC in question does not have the RAID microchip controller so it is totally software dependent).

[http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx/2](http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx/2)

  I got the hardware aspect set-up but unfortunately I got so busy with 'work' that I had to let it sit on the shelf.  Here, In Canada, our thanksgiving day is comming up and I am hosting some international exchange students for thanksgiving dinner from our local university so I will be busy.. however I do plan to spend some more time on this problem to see if I can make the migration and post the results here when they are forthcomming.

Also .. this may be helpful:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Regards,

ventrical

---

### Post by ventrical on 2012-10-10
So far , so good with  the RAID 5 but I am going to have to back peddle to a RAID 0 on this system. Then load quantal.

If you are using precise-alternate (or other) to make your array , just be patient and wait for the drives to resync and see if performance increases.

 The theory is that you can get 2X the speed increase on a RAID 0 array.

---


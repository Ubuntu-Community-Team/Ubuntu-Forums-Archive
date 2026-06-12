---
title: "USB ver.3.0 persistive drive now will not boot on ver. 3 hardware"
date: 2014-11-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-11-16
Looks like a bug either with Trusty version SDC or , after an update/upgrade on persisitve USB key! The KingstonDatatraveler USB 8GB ver 3.0 will boot just fine on  USB ver 2.0 but all of a sudden will not boot on USB version 3.0 hardware. I am assuming perhaps a driver fail - but I will experiement  with an  earlier version of ubuntu SDC as I suspect there is a major bug with SDC and trusty. I know that this is not the place for trusty bug report but since it appears to affect development version (as is which I am running) then I thought it pertitnent.

Regards..

---

### Post by sammiev on 2014-11-16
I'm glad to see this bug pop up as it has been around for a while. Now it's confirmed.

---

### Post by ventrical on 2014-11-17
Currently trying to authenticate this assumption.  

Regards..

Edit:

 I used a different brand USB flash drive. Verbatim 8GB. ver 3.0

  I also tried  to use SDC on Maveric with KingstonDT USB.. but it still failed USB ver 3.0 hardware.

  Currently on ubuntu-gnome (perisitve-updated/upgraded) with Verbatim USB ver 3.0

  I can still use Kingston brand to boot ISOs on version 3 but will only boot a perisitve drive on ver 2.0 hardware.

  I'll monitor this install and try xubuntu-vivid on the KingstonDT and see what happens.

Regards..

---

### Post by sudodus on 2014-11-17
It would be interesting to find out if this depends on the way you create the USB boot drive. You tried it with the SDC. What about mkusb (or dd)? You mentioned persistence. Do you think it makes a difference?

-o-

I can mention that I have an old and much used Sandisk Extreme USB 3 pendrive. Something happened to it maybe one year ago. I think some electronic component was damaged. It stopped working in my Toshiba's USB 3 port, but works well in USB 2 ports. I have other Sandisk Extreme USB 3 pendrives that still work in the USB 3 port.

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
>  You mentioned persistence. Do you think it makes a difference?

Yuppers. I've aways had trouble since after Maveric. So I just did  actual installs onto the USB , some of which still work today.

-o-

> 
I can mention that I have an old and much used Sandisk Extreme USB 3 pendrive. Something happened to it maybe one year ago. I think some electronic component was damaged. It stopped working in my Toshiba's USB 3 port, but works well in USB 2 ports. I have other Sandisk Extreme USB 3 pendrives that still work in the USB 3 port.


I am leaning towards this theory atm.  I am also tempted to propound that these issues come up now and again in ubuntu-desktop but not xubuntu-desktop and kubuntu can do things that ubuntu-desktop(unity) iso  will just refuse (like identifying graphical adapters but I will have to research this futher.

-note- I do know that there are major bug reports out on SDC, I myself creating one but this was a real surprise  when the Kingston quit.

  Regards..

---

### Post by ventrical on 2014-11-17
Here is a screen shot from a Maveric install. It reads two seperate disks. 1.1GB File:Ubuntu-GNOME 15.04 amd64 and Kingston Data Traveler 3.0:7.9 GB Filesystem.

  I will try persistive xubuntu now.

---

### Post by ventrical on 2014-11-17
xubuntu persistive install did not work either. Still busted. It may be that  the whole process of putting gnome3 persisent busted it's version 3 capabilities. I don't know atm .. but the Verbatim(3) 'live' persistent gnome3 vivid is working just fine on USB ver 3 hardware, updates and all.

Regards..

---

### Post by sudodus on 2014-11-17
I suspect that the Kingston pendrive is damaged. What would happen if you wipe it clean an start from the beginning with either mkusb or SDC or Unetbootin?

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> I suspect that the Kingston pendrive is damaged. What would happen if you wipe it clean an start from the beginning with either mkusb or SDC or Unetbootin?

Here is what I get now with my Verbatim USB 3.0
```

Cannot mount /dev/loop1 on cow

```

 Keep in mind that I am doing 

```

sudo apt-get update
sudo apt-get dist-upgrade

```

so it must  be busting the persistive during this process.

> 

 What would happen if you wipe it clean an start from the beginning..


I did this earlier and used FAT32 and it booted with persisitve!!

  It seems to deprecate after you turn the machine off and let it sit for a while.

I'm seriously thinking it is the persistive bug that is doing this.

Regards..

---

### Post by ventrical on 2014-11-17
I did the process all over again and it auto defaulted to FAT32. I am overwriting the old data with new format ext4.

I haven' tried your suggest as of yet.

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> I suspect that the Kingston pendrive is damaged.


[s]I conceed[/s] :) , I'm pooped.

I take that back. SDC is busted, plain and simple.

---

### Post by ventrical on 2014-11-17
(Sucking wind .....!)


 I went here and did this:  [http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)


Kingston fixed!!

SDC is not dependable for these most recent .isos. Why?? Haven't got a clue, but, when I did the method described in the link above it even gave me Ubiquity and the option to Install or Try Ubuntu (gnome3-vivid) . Recalling from past experience from SDC I just had a deja vu. :) lol

---

### Post by ventrical on 2014-11-17
> **sammiev said:**
> I'm glad to see this bug pop up as it has been around for a while. Now it's confirmed.

+1 .. behaves like malware.

Regards..

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> [s]I conceed[/s] :) , I'm pooped.

I take that back. SDC is busted, plain and simple.

Yes, I think it is still suffering from the erase bug (the SDC cannot erase the drive). Some other bugs are squashed, but unfortunately there are many of them, like mosquitos around a fisherman in a sub-arctic river.

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> (Sucking wind .....!)


 I went here and did this:  [http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)


Kingston fixed!!

SDC is not dependable for these most recent .isos. Why?? Haven't got a clue, but, when I did the method described in the link above it even gave me Ubiquity and the option to Install or Try Ubuntu (gnome3-vivid) . Recalling from past experience from SDC I just had a deja vu. :) lol

Congratulations :KS So it was a software problem and you can continue using the Kingston pendrive :-)

There is also these bugs:

[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install)

I think particularly this one can cause trouble with the SDC if running from 14.04.1 when trying to create the boot drive:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

---

### Post by ventrical on 2014-11-17
> **sudodus said:**
> Congratulations :KS So it was a software problem and you can continue using the Kingston pendrive :-)

There is also these bugs:

[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install)

I think particularly this one can cause trouble with the SDC if running from 14.04.1 when trying to create the boot drive:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)


The last one is a real ummm.. as we say in Canada .. a real 'puppy' :)  One friend became disenfrancished. I was so sure and confident.. and the prospected convert just gave up and gave away the 32GB Transcend to a complete noob , who I am also tutoring...  New Ubuntu converts will usually not tells us that there are koniption bugs flying around because they just feel so embarrassed. This is a serious marketing problem that I have mentioned before.

 Thanks for your input.

Regards..

---

### Post by sammiev on 2014-11-17
Just got home from work, looks like you had a very exciting day!

---

### Post by ventrical on 2014-11-17
> **sammiev said:**
> Just got home from work, looks like you had a very exciting day!

Yep .. just wild ... and I think I was one of the original posters about that SDC 'will not erase' bug and now this.

The 'restore image' method from 'disks' works just great but no persistive.

---

### Post by sudodus on 2014-11-17
> **ventrical said:**
> The last one is a real ummm.. as we say in Canada .. a real 'puppy' :)  One friend became disenfrancished. I was so sure and confident.. and the prospected convert just gave up and gave away the 32GB Transcend to a complete noob , who I am also tutoring...  New Ubuntu converts will usually not tells us that there are koniption bugs flying around because they just feel so embarrassed. This is a [COLOR=#ff0000]serious marketing problem[/COLOR] that I have mentioned before.

 Thanks for your input.

Regards..

I agree that this is a serious marketing problem. I don't understand why they are still offering the SDC as the first choice.

'Disks' works (If I understand correctly cloning in a very similar way as mkusb), but it is hidden away as 'restore', and not easily found by beginners. To me 'restore' is something else than 'create a USB boot drive'.

Unetbootin works now, and can be used to create persistent live pendrives, but

-o-

[I]openSUSE is distributed via iso files with a UDF file system (instead of ISO 9660). It can be cloned with mkusb (and it should work with 'Disks' too, but I have not tested). When booted, it creates persistence automatically. Borrowing this technology would make us able to skip the SDC completely.
[/I]
Debian and Ubuntu based ISO files contain read only ISO 9660 file systems and make read-only systems in USB drives (as well as in CD/DVD disks), when copied/flashed/cloned with mkusb. They need a tool, that recognizes and picks the pieces and install them into another file system (usually FAT32), and after that a casper-rw file or partition can be created for persistence.

openSUSE comes with different ISO files for live systems. I have checked and both of

openSUSE-13.1-GNOME-Live-i686.iso
openSUSE-13.2-KDE-Live-x86_64.iso

contain UDF file systems and create an ext3 'hybrid' read-write partition for persistence automatically, when installed by mkusb into USB drives. I guess it works also with read-write CD/DVD disks but I have not tried that (I have never used such a disk).

So the openSUSE kind of live system will get persistence, when installed with mkusb. This UDF system can be both an advantage and disadvantage.

+ It is very convenient to get persistence this way, and the success rate making USB boot drives is higher than with other methods.

- You may not want persistence

. because it make the live session slower
. because you want to avoid the risk of virus or other malware

- There may be booting problems in very old computers, that might not work with the UDF file system.

I think it can be worthwhile considering for a future release, at the latest '16.04 LTS'. Maybe it is fairly easy to borrow the technology and replace the ISO file system with UDF and let the installer create a partition for persistence, when the target drive can be written to.

---

### Post by ventrical on 2014-11-17
@sudodus

 Thanks for that very interesting dissertation. The only reason I have been experimenting with persistent USB with SDC is so that I can streamline and economize testing on different machines. So I can make a drive persistent (theoretically) and update/upgrade on the USB drive and then try that particular flavour on different machines. I try to focus on  Ubuntu-desktop, Ubuntu-next, Ubuntu-gnome, xubuntu, lubuntu and sometimes kubuntu.   Being able to update/upgrade on persistent  USB save hours of downtime and bandwidth (and so there is less transport time for me via zsyncing isos daily-live currents etc.. 

  The process worked just fine with 10.04 Lucid.  Yes , they were a little slower but with USB 3 they are a breeze. Some bootups were near or equal to my ver. 3 SSD card! That's pretty fast.!  I am going to re-read what you have submitted and try a few more experiments. maybe even with one of my Lucid installs and see what happens. They only seem to bust now after update/upgrade .. so maybe this is a process that is not permitted with the new set. Maybe we can trick it with the old set. 

> 
 but it is hidden away as 'restore', and not easily found by beginners. 


and hence Ubuntu finds itself with a tag of certain exclusivity  for brainiac club members only :)  Ya know.. it's no laughing matter , really.  I know bright people in my area who have sworn off Ubuntu because of what Samba did to their RAID arrays. These kind of bugs really put my back against the wall when working with existing converts and worse even with making new ones. Honest ..Ubuntu is awesome .. but these bugs are real doozers. The migration process is one of the most crucial and vulnerable up times and these bugs have to be fixed , plain and simple, elst how can we really trust the convergence transition? (my opinions only).

Regards..

---

### Post by ventrical on 2014-11-18
> 
The process worked just fine with 10.04 Lucid.  Yes , they were a little  slower but with USB 3 they are a breeze. Some bootups were near or  equal to my ver. 3 SSD card! That's pretty fast.!  I am going to re-read  what you have submitted and try a few more experiments. maybe even with  one of my Lucid installs and see what happens. They only seem to bust  now after update/upgrade .. so maybe this is a process that is not  permitted with the new set. Maybe we can trick it with the old set. 


My experiment with Lucid was a complete fail. The .isos are a whole new these days.

Regards..

---


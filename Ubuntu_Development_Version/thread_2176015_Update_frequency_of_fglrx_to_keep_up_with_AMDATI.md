---
title: "Update frequency of fglrx to keep up with AMD/ATI"
date: 2013-09-22
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-22
Hi all,

After struggling with Intel Integrated Graphics and OpenGL games I decided to throw in the towel and install an addon graphics card. Card is AMD/ATI Radeon HD 6670.

I decided to go with the fglrx packaged in the Ubuntu repositories (distro is Lubuntu 13.10 beta), and the driver does work fine on the face of it.

However the fglrx in 10.10's repositories did not recognise my 6670 card, and hence I downloaded AMD's latest Linux 64 bit driver package for my card and installed it. Although it (the driver) is the latest and 10.10 is ancient in the fast moving Linux world, the driver actually seems to work flawlessly with the old 2.6 kernel!

But I noticed that while AMD's latest driver is at version 13.152 (2D: 13.15.3, cccle: 2.19, OpenGL: 4.2.12422), the fglrx from 13.10's repos is at version 13.101 (2D: 13.10.10, cccle: 2.18, OpenGL: 4.2.12337), a little bit behind AMD's.

I'm just wondering normally how long it would take the Ubuntu developers to package the latest fglrx for an release, after it becomes available from AMD?

I see from AMD that they released the latest driver back in May. So how long until Ubuntu starts shipping it for the latest release? Or do they stick with whatever driver version they chose for a release till the latter's end of life?

Although the current driver works fine, it'd still be good if Ubuntu can test and release the latest graphics drivers a reasonable amount of time after they become available from the manufacturers. Especially for a non-LTS release where rock solid stability is not paramount.

---

### Post by jfernyhough on 2013-09-22
Catalyst 13.9 (fglrx 13.152) has only just been released (like, three days ago). It takes a little time for packagers to check what has changed and patch the driver to ensure it works - it's not a case of simply taking AMDs version (for example, in the previous release there were issues with kernel 3.11 support and /proc/ati issues). This takes a little time.

If you want a more up-to-date package you can try the XOrg Edgers PPA. This normally has more cutting-edge and significantly less tested driver versions.

I also maintain a thread (which I'm surprised you didn't find) which details most of the changes. However, given the progress of the open source driver, the inclusion of DPM in kernel 3.11, the fact the open source driver has none of the issues that fglrx has (and for me performance in Source games is much greater), and that each Catalyst release (re)introduces regressions and new bugs, I'd be inclined to dump fglrx altogether.

There's also the issue with Mir/XMir support. Intel have already announced they won't be supporting it in their drivers, so I imagine talks are underway with Nvidia and AMD for support in their proprietary drivers. Ubuntu has had a "special" relationship with AMD for a while, which may explain why there hasn't been a more recent official Ubuntu fglrx package for a while.

Finally, why are you installing a driver from the 10.10 repo in 13.10?

---

### Post by santosh83 on 2013-09-22
> **jfernyhough said:**
> Catalyst 13.9 (fglrx 13.152) has only just been released (like, three days ago). It takes a little time for packagers to check what has changed and patch the driver to ensure it works - it's not a case of simply taking AMDs version (for example, in the previous release there were issues with kernel 3.11 support and /proc/ati issues). This takes a little time.

Ah sorry about that. From the AMD download page for 13.152 I gathered that the release date was 29th May, hence my surprise.

> I also maintain a thread (which I'm surprised you didn't find) which details most of the changes. However, given the progress of the open source driver, the inclusion of DPM in kernel 3.11, the fact the open source driver has none of the issues that fglrx has (and for me performance in Source games is much greater), and that each Catalyst release (re)introduces regressions and new bugs, I'd be inclined to dump fglrx altogether.

Can you provide the address of your thread?

 The open source version is the 'xserver-xorg-ati' package? If it can run games like Morrowind and FGFS as well as fglrx then I'd have no problems switching. I'll uninstall fglrx and try out the open source versions.

> There's also the issue with Mir/XMir support. Intel have already announced they won't be supporting it in their drivers, so I imagine talks are underway with Nvidia and AMD for support in their proprietary drivers. Ubuntu has had a "special" relationship with AMD for a while, which may explain why there hasn't been a more recent official Ubuntu fglrx package for a while.

Finally, why are you installing a driver from the 10.10 repo in 13.10?

No I installed the latest driver from AMD's website in 10.10, since 10.10's repo's fglrx didn't recognise my newer card. For 13.10 I've the fglrx from it's own repo installed, which is a version behind AMD's, and hence my post here.

---

### Post by kaldor on 2013-09-22
> However, given the progress of the open source driver, the inclusion of  DPM in kernel 3.11, the fact the open source driver has none of the  issues that fglrx has (and for me performance in Source games is much  greater), and that each Catalyst release (re)introduces regressions and  new bugs, I'd be inclined to dump fglrx altogether.


I strongly agree with this. Given how well the Radeon driver progressed lately, there are fewer reasons to use the terrible FGLRX driver. I really recommend you give the open source driver a go. Make sure you have the most recent version of Ubuntu and use at least kernel 3.11.

---

### Post by Yellow Pasque on 2013-09-23
> Or do they stick with whatever driver version they chose for a release till the latter's end of life?
That's generally true with non-LTS releases. Although it talks about nvidia, this bug will give you an idea: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1219908](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1219908)


> Ah sorry about that. From the AMD download page for 13.152 I gathered that the release date was 29th May, hence my surprise.
fglrx versoning is nonsensical to sane people these days, especially since AMD moved away from monthly releases but didn't drop the <year>-<month> version scheme (which also is seen as <year>.<month>). On top of that, they kept the old version scheme going too, and stepped it up another notch by making the old and new schemes use similar numbers.
Even the devs can't keep it straight: [http://wiki.cchtml.com/index.php/Catalyst_13.9](http://wiki.cchtml.com/index.php/Catalyst_13.9)
Accidental release? LMAO!

---

### Post by su:bhatta on 2013-09-24
> **kaldor said:**
> I strongly agree with this. Given how well the Radeon driver progressed lately, there are fewer reasons to use the terrible FGLRX driver. I really recommend you give the open source driver a go. Make sure you have the most recent version of Ubuntu and use at least kernel 3.11.

Sadly, I still have to use 'nomodeset & quiet splash' with 3.11.0-2-lowlatency as well as 3.11.0-5-generic kernels for my Radeon HD 6480G GPU.

No luck with open source drivers yet.

---


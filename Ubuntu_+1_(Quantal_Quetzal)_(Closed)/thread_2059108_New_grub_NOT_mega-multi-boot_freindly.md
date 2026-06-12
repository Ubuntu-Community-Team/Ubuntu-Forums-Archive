---
title: "New grub NOT mega-multi-boot freindly"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-17
I was too busy to help with the new grub testing before it hit the repos, but finally had time to check it out.

I multi-boot a lot for testing purposes:

[ATTACH]224266[/ATTACH]

[ATTACH]224267[/ATTACH]

And the first thing I noticed with the new grub is that the names do NOT include a device designation:

[ATTACH]224268[/ATTACH]

But also once switching to another distros older grub the device name is super long:

[ATTACH]224269[/ATTACH]

I did search just a little bit for an existing bug report but I guess I'll have to do my own ;)

Anyone else notice this?

---

### Post by arpanaut on 2012-09-17
Yup, bugs:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)

> And the first thing I noticed with the new grub is that the names do NOT include a device designation:
A big +1 to this one, really a mess when having several installations. have to go to 'e' to see where things are.

Colin is working on the script errors, and the long extraneous menu items.
Very strange ATM

---

### Post by kansasnoob on 2012-09-17
> **arpanaut said:**
> Yup, bugs:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)


A big +1 to this one, really a mess when having several installations. have to go to 'e' to see where things are.

Colin is working on the script errors, and the long extraneous menu items.
Very strange ATM

Many, many thanks :D

---

### Post by kansasnoob on 2012-09-17
> **arpanaut said:**
> Yup, bugs:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)


A big +1 to this one, really a mess when having several installations. have to go to 'e' to see where things are.

Colin is working on the script errors, and the long extraneous menu items.
Very strange ATM

Super dumb question :redface:

Did you just use "ubuntu-bug grub" to file bug reports?

Or "ubuntu-bug grub-pc"?

Or does it even matter?

---

### Post by cecilpierce on 2012-09-17
Very confusing, I edited my grub for now, some of the Advance menus are huge with two differant partitions?
The grub-emu doesn't show but I put a theme (journey).

---

### Post by Elfy on 2012-09-17
> **kansasnoob said:**
> Super dumb question :redface:

Did you just use "ubuntu-bug grub" to file bug reports?

Or "ubuntu-bug grub-pc"?

Or does it even matter?
I used 

```
ubuntu-bug grub2
```

---

### Post by arpanaut on 2012-09-17
@kansasnoob  I did ubuntu-bug grub-pc, kinda a pia as apport made a crash report in /var/crash but didn't report. (I like the automation)  but that crash report was against < _usr_bin_grub-script-check.0.crash>  which is what Colin is looking into.  I just reported what the error at the end of 'update-grub" asked for and added some more info. 
This initially happened while in Ubuntu Gnome Remix so I don't know if apport is working properly there???  Now I am seeing the error on other installs and apport is pointing to dino's bug.

Just along for the ride here. LOL
I'm in the middle of packing to move so 'am doing what I can when I can.

---

### Post by dino99 on 2012-09-17
Due to the trouble i got/get and Colin comments/blog, i've decided to change my grub installation:

- stop using different grub version due to multiple OS on several devices.
- only use the LTS grub version (as grub does not propose fallback choice)
- and go a bit ahead: 
 a) proposed by yann 
[HTML]Please try creating a little boot partition at the start of your Quantal disk ( sdb). See https://help.ubuntu.com/community/BootPartition[/HTML]
 b) proposed by herman
> [http://ubuntuforums.org/showpost.php?p=8285027&postcount=4](http://ubuntuforums.org/showpost.php?p=8285027&postcount=4)

---

### Post by kansasnoob on 2012-09-17
> **I'm in the middle of packing to move so 'am doing what I can when I can.**

I'm in the middle of some medical stuff :)

Some time ago I'd noticed a true decline in my already limited mental abilities so the docs got busy.

The first thing they found wrong was a partially collapsed arterial stent. Getting that fixed was a piece of cake and I felt much better :D

But the docs were very thorough and they also found some new melanomas. I know I'm not going to live forever so I don't care a whole lot, but the treatments are making me so sick I sometimes wish I'd just die in my sleep ;)

I wish I could sleep more than two hours at a time w/o vomiting or crapping the bed :lolflag:

---

### Post by arpanaut on 2012-09-17
Sorry to hear that, I hope the doc's got you going in the right direction!
Compared to what you are enduring, the stressors in my life seem minor.

Good Luck with your treatments.

---

### Post by jerrylamos on 2012-09-17
> **kansasnoob said:**
> I'm in the middle of some medical stuff :)  Our son has some sort of encephalitis problem the specialists are studying with no known treatment toubling symptoms.

He's getting some relief from the life style promoted by Dr. George Jelinek in "Overcoming MS" another brain disease.

More direct is prof. Jane Plant CBE in her book "The No-Dairy Breast Cancer Prevention Program".  In her case multiple surgeries, radiations, chemo's were not working and she had months to go.  Changed her life style, that was 17 years ago and now she's doing fine.  Importantly, she's found that men's prostate cancer is also susceptible to the same things and is also resposive to life style changes.  

One of the considerations is cow's milk is intended to grow calves into steers as fast as possible.  Many things in cow's milk enable fast growing cells to grow faster....such as calves or human cancer cells...

Our son after a year of poor sleep, waking up after a couple hours, etc. is now doing better granted his condition is much different than yours- but does involve the brain.

We find the standard medical practices are drugs, surgery, radiation, etc. with little knowledge of life style. Much more is in Cornell nutritional bioligist prof. T. Colin Campbell's book "The China Study".  A specialty of his is liver cancer which is also very responsive to life style.  

All 3 books are available from Amazon and bookstores.  All three of these authors are scientists so they do get into detail of studies and evidence and how and why as well as what to do.

---

### Post by ronacc on 2012-09-17
> **dino99 said:**
> Due to the trouble i got/get and Colin comments/blog, i've decided to change my grub installation:

- stop using different grub version due to multiple OS on several devices.
- only use the LTS grub version (as grub does not propose fallback choice)
- and go a bit ahead: 
 a) proposed by yann 
[HTML]Please try creating a little boot partition at the start of your Quantal disk ( sdb). See https://help.ubuntu.com/community/BootPartition[/HTML]
 b) proposed by herman

wouldn't it be better if they fixed the existing grub ? Or reverted to one that actually works ?

---

### Post by zika on 2012-09-17
> **kansasnoob said:**
> I'm in the middle of some medical stuff :)

Some time ago I'd noticed a true decline in my already limited mental abilities so the docs got busy.

The first thing they found wrong was a partially collapsed arterial stent. Getting that fixed was a piece of cake and I felt much better :D

But the docs were very thorough and they also found some new melanomas. I know I'm not going to live forever so I don't care a whole lot, but the treatments are making me so sick I sometimes wish I'd just die in my sleep ;)

I wish I could sleep more than two hours at a time w/o vomiting or crapping the bed :lolflag:Fingers are crossed and wishing You all the best!

---

### Post by jerrylamos on 2012-09-17
Makes no sense to me, a tester/user.  For example I just tried:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "QuantalB1 on sda1" {
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet
initrd /initrd.img
}

How simple is that.  

Make the file executable, example 
sudo chmod +x custom

If you name it 06_custom 
sudo cp 06_custom /etc/grub.d

it will show up in the grub boot list as the first entry, the default.

If you name it 40_custom 
sudo cp 40_custom /etc/grub.d

it will show up at the end of the list which is what I usually do.

After copying do 
sudo update-grub

As usual, expect some oops and fixes.  Grub2 does some wierd things like mix up /dev/sda1 and /dev/sdb1 vs. hd(0,1) and hd(1,1)

I cannot tell the difference between boot times or the resulting booted ubuntu with either the simple or the hugely complex mess that grub2 spills out.  

?

Now do note I'm using the /vmlinuz and /initrd.img links to /boot.

If instead you use 

/boot/vmlinuz-3.5.0-14-generic
/boot/initrd.img-3.5.0-14-generic

you can select different kernels example if you are using some ppa's but you have to change the _custom file whenever there's a change in /boot.  Seems to me in the old days grub used to enable booting the different kernels in the boot list, now grub2 doesn't do that I've seen.

---

### Post by dino99 on 2012-09-17
> **ronacc said:**
> wouldn't it be better if they fixed the existing grub ? Or reverted to one that actually works ?

Colin works on it right now, you can follow via the report. But grub is way too sensible of extern packages version. So my choice.

---

### Post by dino99 on 2012-09-17
@Jerry

if you want really doing test, its with the real package, not with added workarounds, except if they are going to upstream, which i doubt a little.

---

### Post by QIII on 2012-09-17
(Begin rant.)

I almost feel like putting a big, fat "Bite Me!" on the Launchpad bug for Colin.

I know this stuff isn't easy.  I know he's working on it.  But c'mon.

After updating both Quantal installs (Ubuntu and Xubuntu) on my multi-disk multi-boot machine, to go back to my primary and update GRUB and find the monstrously verbose and incomprehensible entries, I was miffed.

When I shut down and tried to boot into my primary the next time and got the "alloc magic" error (I think the alloc magic error is generated because the insanely verbose entries for the other Ubuntu selections overflow the buffer.  Maybe if that is fixed, I can get into Precise and just update GRUB.) and then had to restart, change the boot order in BIOS and use the GRUB from my Quantal install to get into Precise on my primary disk, I was somewhat less than happy.  It would take me more time than it is worth to sort out GRUB on my primary disk since I'll be going to Quantal on it soon enough, so I'll just go with what I have and switch the boot order back when I've installed Quantal on that disk.  

We expect stuff to go wrong from time to time in testing.  But for something like this to cause problems with getting into my primary install in a multiboot situation is really inexecusable.  Dual and multibooting is so common as to be almost a certainty for many users.  This is something that should have been spotted.

(End of rant.  And my genuine thanks to Colin for working on it - which is why I won't actually rant in the bug report.)

---

### Post by ronacc on 2012-09-17
> **dino99 said:**
> Colin works on it right now, you can follow via the report. But grub is way too sensible of extern packages version. So my choice.

grub has been very good at finding and adding all of my installs regardless of the grub version the install used for atleast the last year , infact I commented on this back during the precise cycle that I was happyt that it was working at last . So this represents a definite regression .Glad to hear colin is working on it , in the meantime I'll just switch 1st boot drives in bios and let another distro handle the booting .

---

### Post by jerrylamos on 2012-09-17
> **dino99 said:**
> @Jerry, if you want really doing test, its with the real package, not with added workarounds, except if they are going to upstream, which i doubt a little.

I mostly use the real package as is & some testing of Unity for bugs, since I'm no Unity expert on all the frills and functions for general utility I switch desktops.  That still tests lots of Ubuntu things like kernel & ubiquity & gedit (has a launchpad bug right now) and "Files" and Firefox (has a launchpad bug) & Xorg & hidden wireless (has a launchpad bug) & on and on.  

I've been using the Grub2 mess as is except some special purpose activity.  Somebody asked why Grub2 is so complex so I gave a working example which I use on occasion, showing Ubuntu 12.10 booted just fine with simple human readable four line syntax.  

Perhaps you prefer as follows.  With a quick glance, what partition is being booted?  Hint: I have 12, a variety of ubuntu levels, a fairly small setup.

/boot/grub/grub.cfg
......lots of prolog, now for what I think is the default boot image:
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f3f05f04-bafa-4e54-a52d-aab85819263b' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos8'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos8 --hint-efi=hd1,msdos8 --hint-baremetal=ahci1,msdos8  f3f05f04-bafa-4e54-a52d-aab85819263b
	else
	  search --no-floppy --fs-uuid --set=root f3f05f04-bafa-4e54-a52d-aab85819263b
	fi
	linux	/boot/vmlinuz-3.5.0-14-generic root=UUID=f3f05f04-bafa-4e54-a52d-aab85819263b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-14-generic
}

BTW I worked 42 years in IBM main frame computer development where speed and efficiency are worth real $$ price/performance.  Tends to color my outlook.

---

### Post by amjjawad on 2012-09-30
> **kansasnoob said:**
> But also once switching to another distros older grub the device name is super long:

[ATTACH]224269[/ATTACH]

Anyone else notice this?

Yes, same here. I didn't install GRUB version 2.0 to MBR yet. I'm still using GRUB 1.99 and I have the same issue (LONG names/entries).

---

### Post by amjjawad on 2012-09-30
> **arpanaut said:**
> Yup, bugs:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1051624)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)


A big +1 to this one, really a mess when having several installations. have to go to 'e' to see where things are.

Colin is working on the script errors, and the long extraneous menu items.
Very strange ATM

But these bugs for something else, if I read correctly?!
The issue that the OP is talking about, if I'm not mistaken, is something else? or perhaps I'm too confuse?

---

### Post by arpanaut on 2012-09-30
> **amjjawad said:**
> But these bugs for something else, if I read correctly?!
The issue that the OP is talking about, if I'm not mistaken, is something else? or perhaps I'm too confuse?
I am not sure, I am using the new Grub 2.0 from Quantal on my test rig, and the long entries issue has been fixed but IDK about how it is working with using older grub installs.
I do know it took me going back into my other installs and running 'update-grub' to get all the long entries to clean up.  
I've been busy with other things so haven't investigated the issue since it was resolved for my installation of Grub to MBR of this machine. Sorry I can't be of more help.

---

### Post by dino99 on 2012-09-30
Since a week or so, when i boot on QQ, i first see this mysterious error: "prereset failed errno=-19", then booting continue. PP is not affected, even if now grub2.0 (QQ) is only installed on all hdds.

---

### Post by grahammechanical on 2012-09-30
This actual Grub 2 will be great on a simple dual boot machine with only two OS. It does not show any of that Ubuntu with Linux 3.5.0-15 stuff which a new user would find confusing. I certainly did when I set up my first dual boot and that was with another version of Ubuntu.

But Grub 2 is most definitely not helping when there are several installs of Ubuntu on the hard disk. I have 1 x 12.04 and 3 x 12.10 and 12.04 is the only one I know that I am booting into.

We should also not that in Grub.cfg set root = 'hd0, msdos5' is the way it identifies sda5. The other partitions follow a similar pattern.

It think that a lot of confusion in the menu is being caused by Grub update not only interrogating the partitions looking for boot images but it also reads old Grub configuration files. So, the old 'with Linux' designations get put in the menu as bootable images when they are already covered by Ubuntu (development branch) (12.10). Duplicate boot choices, in other words.

Regards.

---

### Post by scradock on 2012-09-30
Not to mention the fact that GRUB2 2.00 STILL doesn't identify and list a Vista install, if there is (as there usually is) a Vista Recovery partition first. 

Had to put mine into a 40_custom to be able to access it....

Launchpad bug #1058476

---

### Post by amjjawad on 2012-09-30
Haven't installed GRUB version 2.0 on the MBR yet but from what I'm reading here, it seems that installing GRUB Customizer is necessary now, specially if it's a multi-boot system.

Edit:
YES, I know this is not a solution.

---

### Post by amjjawad on 2012-09-30
> **arpanaut said:**
> I am not sure, I am using the new Grub 2.0 from Quantal on my test rig, and the long entries issue has been fixed but IDK about how it is working with using older grub installs.
I do know it took me going back into my other installs and running 'update-grub' to get all the long entries to clean up.  
I've been busy with other things so haven't investigated the issue since it was resolved for my installation of Grub to MBR of this machine. Sorry I can't be of more help.

Never mind but since I'm not the only one who noticed that long entries and since you guys are discussing that here, it seems it's a bug but with what exactly? with GRUB version 2 or 1.99? I mean as long as GRUB version 1.99 is installed on the MBR and we run "update-grub" to update GRUB 1.99 menu then, IMHO, I think GRUB 1.99 is not yet 100% compatible with GRUB 2.0 and vice versa.

---

### Post by grahammechanical on 2012-10-01
In my humble opinion I think that the issue is with update-grub and how it works.

Yesterday the update to my 12.04 brought in an update to Grub 1.99 and now the 12.04 Grub menu is in control and there are about 30 menu lines.

I have 12.10 on sda5, sda7, sda8. But Grub 1.99 is putting set root hd0,msdos5 for kernels that are on sda7 and sda8. By the way msdos5 = sda5. I have not tested out to see what happens if I select one of those crossed matched references. Not yet.

I have also tried running update-grub on the three Quantal installs and the read out is as it should be. But the 12.04 Grub remains in charge. It is not over written.

I have also tested the latest Grub customizer as I like that utility a lot but it does not cope very well with the sub menu options. The author has not noticed that there is a difference between Grub 1.99 and Grub 2. So, we need to be patient here also.

Regards.

---

### Post by kansasnoob on 2012-10-01
> I have 12.10 on sda5, sda7, sda8. But Grub 1.99 is putting set root hd0,msdos5 for kernels that are on sda7 and sda8. By the way msdos5 = sda5. I have not tested out to see what happens if I select one of those crossed matched references. Not yet.


I noticed something similar. I'd just installed a fresh 12.10 on sda15, but the boot menu line that indicated msdos15 actually booted an Lubuntu 12.10 on sda10 :(

Since I've been using a *somewhat* stable Ubuntu 12.04 to control my multi-boot mess I've just been reverting my 12.10 installs to legacy grub. I know that's not a good way of doing things but I just have too much on my plate to deal with the new grub issues :frown:

---

### Post by Cavsfan on 2012-10-03
A smart guy Ranch Hand on this forum showed me how to make custom entries on Grub and
they work just as well on Quantal Quetzal with Grub 2.00 as on every Ubuntu back to Lucid Lynx and before.

If you have ever deleted a partition that one of your Buntus were on and reinstalled it there
You need to edit fstab to correct the entries which show up on the grub menu.
Since even when you delete a partition, somehow the UUID that it used before is kept until you correct it.
I had removed and reinstalled 2 of my Ubuntus and wondered why the normal grub2 screen displayed the wrong partitions.
This is because the fstab entries were wrong on those 2 Ubuntus.
The How to in my signature also solves this problem. The How to has been converted into a wiki but, has not been linked to my How to yet.
But, there is a link to the wiki on the above link if you want to check it out.
It has several examples of what my grub2 screens have looked like over time.
And you would want to install grub on which ever Ubuntu you want to be your main OS.
By logging into that Ubuntu and entering 
```
sudo grub-install /dev/sda
``` (where sda is drive 1) as mentioned earlier.

The only difference between Grub 1.99 and Grub 2.00 is that if you have windows installed,
Grub 1.99 gives an erroneous error when selecting windows:
```
Error: No argument specified.  

Press any key to contiue...
```But, if you wait or just press enter it goes into windows without any problems.

I am glad that Grub 2.00 does not give that error when selecting windows.

---

### Post by Cavsfan on 2012-10-04
My Grub 2.00 screen on Quantal Quetzel 12.10 quad booting:

[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8496[/IMG]

Pretty cluttered right? ;)

---

### Post by kansasnoob on 2012-10-04
> **Cavsfan said:**
> My Grub 2.00 screen on Quantal Quetzel 12.10 quad booting:

[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8496[/IMG]

Pretty cluttered right? ;)

I'm guessing that you meant to include a screenshot but it didn't take ;)

---

### Post by cecilpierce on 2012-10-04
> **Cavsfan said:**
> My Grub 2.00 screen on Quantal Quetzel 12.10 quad booting:

[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8496[/IMG]

Pretty cluttered right? ;)I don't see the pic.

Just saw grub-updates and the grub-emu doesn't show the Starfield theme and the colors are black, had to change them in theme.txt to be able to see:

+ boot_menu {
        left = 10%
        width = 80%
        top = 20%
        height = 50%
        item_font = "DejaVu Sans Regular 12"
        item_color = "#6ac"
        selected_item_font = "DejaVu Sans Bold 14"
        selected_item_color= "#fff"
        selected_item_pixmap_style = "blob_*.png"
        icon_height = 25
        icon_width = 25
        item_height = 26
        item_padding = 0
        item_icon_space = 0
        item_spacing = 1
        scrollbar = true
        scrollbar_width = 20
        scrollbar_thumb = "slider_*.png"
        menu_pixmap_style = "boot_menu_*.png"
}

---

### Post by Cavsfan on 2012-10-04
Betterer? I had my photos with the wrong security settings. ;)

---

### Post by Cavsfan on 2012-10-04
Pretty dang nice eh? ;)

---

### Post by ronacc on 2012-10-04
the new grub is still not finding and adding all of my linux installs . Since 1.99 did find and make available all of my installs I can only consider this a serious regression . It is not that ubuntu dosen't see those installs because I can mount and read them from nautilus ( I refuse to call it files) and it is not that they are in any way dammaged I can boot into them by going into bios and changing my first boot drive to one of the "missing" installs .

---

### Post by Cavsfan on 2012-10-05
Here is the wiki if any one is interested. It is broken into 2 parts.
Part 1 is Lucid Lynx grub 1.98.
 Part 2 is everything after that: grub 1.99 and 2.00 as they are almost the same in the way to customize it.
The only difference between grub 1.99 and 2.00 is where you put the custom font colors.
With grub 1.99 in **/etc/grub.d/05_debian_theme** the colors go after line 98.
With grub 2.00 the colors go after line 108.


[[COLOR=blue]_https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen_[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

---

### Post by dino99 on 2012-10-05
Very good wiki, thanks.

but have seen screenshot not displaying Windows menu as described :confused:

---

### Post by Cavsfan on 2012-10-05
> **dino99 said:**
> Very good wiki, thanks.

but have seen screenshot not displaying Windows menu as described :confused:

Thanks! I am not understanding what you mean. :confused:
It will work if you have 1 Ubuntu, or if you have 12 Ubuntus with or without windows.
I also works with a Debian Squeeze install.

The font size is adjustable but, I would check the link I put in there concerning that before doing so.

---

### Post by Cavsfan on 2012-10-05
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
```This will show you what grub menu will display.
This is a new version of that grep command. The older one does not work any more even on Lucid. 
Drs305 gave it to me.
Here is my output:
```
     0    menuentry "Lycid Lynx 10.04" {
     1    menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
     2    menuentry "Precise Pangolin 12.04" {
     3    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     4    menuentry "Quantal Quetzal 12.10" {
     5    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     6    menuentry "Windows 7" {
```*Note: I forgot to mention that command will not parse the submenus of other ubuntus with multiple kernels.

---

### Post by Cavsfan on 2012-10-05
Congratulations **kansasnoob** on your **GnomeClassicTweaks** wiki! 
I was told to model mine after yours. :D  So, you are the standard bearer!

I'm just glad my How To was also chosen to be migrated over to a wiki.

---

### Post by bzd454 on 2012-10-05
seems like continual improvement of GRUB (and mega-multi boot etc) should be a priority.  if we ever got to the point where avg noob (like me) can just make a few partitions(GParted is easy) and cut/paste/copy/delete an OS here and there as easily as if they were folders, and GRUB can recognize them all then avg computer user might start to realize that Windows is just another OS.

---

### Post by Cavsfan on 2012-10-05
> **bzd454 said:**
> seems like continual improvement of GRUB (and mega-multi boot etc) should be a priority.  if we ever got to the point where avg noob (like me) can just make a few partitions(GParted is easy) and cut/paste/copy/delete an OS here and there as easily as if they were folders, and GRUB can recognize them all then avg computer user might start to realize that Windows is just another OS.

That wiki of mine above only changes 3 files and adds another and the changes are minor.
You can enter **sudo blkid** in terminal to get the partitions and then modify this text and save it as **/etc/grub.d/06_custom**.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=[COLOR="Red"](hd0,2)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=[COLOR="Red"](hd0,2)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda2[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=[COLOR="Red"](hd0,5)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=[COLOR="Red"](hd0,5)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda5[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=[COLOR="Red"](hd0,8)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda8[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/[COLOR="Red"]sda8[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='[COLOR="Red"](hd0,1)[/COLOR]'
    search --no-floppy --fs-uuid --set [COLOR="Red"]1CFC7A8DFC7A60C6[/COLOR]
    chainloader +1
}

```

Change what it is red to match your system(s), change the text and delete the rest. The text can be whatever you want to see displayed.
The last entry is for windows. If you have that modify the red and the text if not delete that part.

Then make it executable **sudo chmod +x /etc/grub.d/06_custom**
Enter **sudo update-grub**, reboot and you will see how simple it is.
Then you can go from there.
HTH

---

### Post by bzd454 on 2012-10-07
> **Cavsfan said:**
> That wiki of mine above only changes 3 files and adds another and the changes are minor.
You can enter **sudo blkid** in terminal to get the partitions and then modify this text and save it as **/etc/grub.d/06_custom**.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=[COLOR="Red"](hd0,2)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=[COLOR="Red"](hd0,2)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda2[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=[COLOR="Red"](hd0,5)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=[COLOR="Red"](hd0,5)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda5[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=[COLOR="Red"](hd0,8)[/COLOR]
        linux /vmlinuz root=/dev/[COLOR="Red"]sda8[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/[COLOR="Red"]sda8[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='[COLOR="Red"](hd0,1)[/COLOR]'
    search --no-floppy --fs-uuid --set [COLOR="Red"]1CFC7A8DFC7A60C6[/COLOR]
    chainloader +1
}

```

Change what it is red to match your system(s), change the text and delete the rest. The text can be whatever you want to see displayed.
The last entry is for windows. If you have that modify the red and the text if not delete that part.

Then make it executable **sudo chmod +x /etc/grub.d/06_custom**
Enter **sudo update-grub**, reboot and you will see how simple it is.
Then you can go from there.
HTH

eh, tbh thats still too difficult for me. took me about 6 months of looking at the grub menu or GParted with all these SDA3, SDA5  etc before i started to understand a little bit of it.  Most of the stuff like ubuntu installs pretty easy and doesn't overwrite Windows but then something like Fedora uses a weird partition or file system (can't read it or resize it from GParted running in Ubuntu iirc) and steals control of GRUB  :(

and GRUB should have some easy way to delete or hide all of these excess listings like all the old kernels and the "recovery modes" that are very rarely necessary. 

Linux side is getting better though. 3-4 years ago i couldn't find a USB cell modem with my ISP that would work with Linux and now the Sierra 598 works better on linux (recognized and connects much quicker) than it does on Windows.  and it works on all the Live CDs i've tried too. awesome.

---


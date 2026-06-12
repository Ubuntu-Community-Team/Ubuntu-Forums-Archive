---
title: "New entry in Grub menu (SystemD)"
date: 2015-01-06
forum: Ubuntu Development Version
---

### Post by zika on 2015-01-06
You might have noticed that Grub's got new entry in each and every linux kernel section (UpStart one or SystemD one depending of default on Your install)...
So, for those of You that count for each kernel in Advance_section two entries change is that they shoud count now three... ;) 
„1>k“ where k=3*i+j, 
i=0, 1, 2,... # of kernel in the list
j=0 for regular default session (depending of what is default for pid 1 (init) on Your system (UpStart or SystemD), default will be used for init(ialization)) 
j=1 for alternative session (depending of what is default for pid 1 (init) on Your sastem (UpStart od systemD) alternative to default will be used for init(ialization))
j=2 for recovery_mode session
Let alone the fact that (I am reporting ths from Upstart session even thoigh I had each and every instance of UpStart removed as repoted in detail in other threads) there is a possibilty to boot with UpStart instead of SystemD and vice versa. Nice.

---

### Post by grahammechanical on 2015-01-06
I just rebooted to check for myself. I get a SystemD option. I am running Vivid as it comes through daily updates. I have not messed with SystemD in anyway. I guess it means that the options are being kept open to not break the development release. At some point the switch to SystemD will have to be complete with Upstart being removed but in the mean time we can test what is coming in from SystemD and still have a working development release (running Upstart) if something breaks.

Regards

---

### Post by ventrical on 2015-01-06
Works just fine here when I choose systemd option from Grub.

Nice work.

---

### Post by Cavsfan on 2015-01-07
I was wondering about that. Pretty cool!

Except instead of PID 1 being init it is now upstart.

That complicates my wiki possibly. Not sure yet... everything is happening so fast... Too fast for me...

---

### Post by Cavsfan on 2015-01-07
Now I get it - systemd is now the default and to boot into upstart you need an init= command. I guess the $vt_handoff is new too.

 This would be default systemd:

```
menuentry "Vivid Vervet 15.04 (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash [COLOR=#ff0000]$vt_handoff [/COLOR]
        initrd /initrd.img
}
```

and this would be for upstart:

```
menuentry "Vivid Vervet 15.04 Upstart (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash [COLOR=#ff0000]$vt_handoff init=/sbin/upstart[/COLOR]
        initrd /initrd.img
}
```

Thank you very much [_zika_]("http://ubuntuforums.org/member.php?u=690937") for bringing this to my attention.

---

### Post by Cavsfan on 2015-01-07
Tested this and it does indeed work. :)

---

### Post by Elfy on 2015-01-08
> **Cavsfan said:**
> Now I get it - systemd is now the defaultNot here it isn't. Standard default grub has upstart first

> **Cavsfan said:**
>  and to boot into upstart you need an init= command.with systemd needing the init= stanza

> **Cavsfan said:**
>  I guess the $vt_handoff is new too.
Not here it isn't :)

---

### Post by grahammechanical on 2015-01-08
In the Vivid that I have been using since the start of its development cycle the SystemD option is in the Advanced options for Ubuntu sub-menu. This is a comparison of the two relevant lines from grub.cfg. First the default and then the systemD option.

> linux    /boot/vmlinuz-3.16.0-24-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff

> linux    /boot/vmlinuz-3.16.0-24-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff init=/lib/systemd/systemd

I have just loaded into Ubuntu with the SystemD option and the loading reached a point where it seemed to be going nowhere. Then I tapped Enter and the disk activity continued and it loaded to the login screen. And beyond, in case you were wondering.

I am using a digital TV as a monitor and the screen tends to dim if there is little video activity. And I had the "No signal" message with its count down to sleep mode at the time. This is normal with this monitor. So, I am wondering if there was a confirmation request that did not appear on my screen. I am also wondering if an install from the latest Vivid daily will reverse the options with Upstart in the Advanced options sub-menu. I cannot test this today. I will do so tomorrow.

Regards.

EDIT: The systemd option will load to a the login screen without the need to press Enter but it takes a lot longer to do it then the Upstart option.

---

### Post by Elfy on 2015-01-08
> **grahammechanical said:**
> ... I am also wondering if an install from the latest Vivid daily will reverse the options with Upstart in the Advanced options sub-menu. I cannot test this today. I will do so tomorrow...

Assuming that a vbox install is not any different then ... 

Livesession boots with upstart
Install defaults to upstart with systemd available in Advanced

---

### Post by Cavsfan on 2015-01-08
> **Elfy said:**
> Not here it isn't. Standard default grub has upstart first

with systemd needing the init= stanza

Not here it isn't :)

It definitely is on my system and I have proof. :)

> **grahammechanical said:**
> In the Vivid that I have been using since the start of its development cycle the SystemD option is in the Advanced options for Ubuntu sub-menu. This is a comparison of the two relevant lines from grub.cfg. First the default and then the systemD option.

>  linux    /boot/vmlinuz-3.16.0-24-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff                      

[QUOTE]linux    /boot/vmlinuz-3.16.0-24-generic  root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash  $vt_handoff init=/lib/systemd/systemd                      

I have just loaded into Ubuntu with the SystemD option and the loading reached a point where it seemed to be going nowhere. Then I tapped Enter and the disk activity continued and it loaded to the login screen. And beyond, in case you were wondering.

I am using a digital TV as a monitor and the screen tends to dim if there is little video activity. And I had the "No signal" message with its count down to sleep mode at the time. This is normal with this monitor. So, I am wondering if there was a confirmation request that did not appear on my screen. I am also wondering if an install from the latest Vivid daily will reverse the options with Upstart in the Advanced options sub-menu. I cannot test this today. I will do so tomorrow.

Regards.

EDIT: The systemd option will load to a the login screen without the need to press Enter but it takes a lot longer to do it then the Upstart option.[/QUOTE]

It may very well be that it changed because I installed the alpha1 on December 18th when it came out. My boot lines in the default grub show as I posted above.
Just [COLOR=#ff0000]$vt_handoff [/COLOR] on the default systemd line and [COLOR=#ff0000]$vt_handoff init=/sbin/upstart[/COLOR] on the non-default option of upstart.
I don't really notice that much difference but upstart does appear to be a few seconds slower on this old pc.

Those lines I posted do indeed boot and work well in my custom grub. And I have it as 10_linux does: systemd default and upstart as an option.

> **Elfy said:**
> Assuming that a vbox install is not any different then ... 

Livesession boots with upstart
Install defaults to upstart with systemd available in Advanced

That's rather peculiar as it's the opposite on my system and here the proof:

[[IMG]http://en.zimagez.com/miniature/20150108132112.jpg[/IMG]]("http://en.zimagez.com/zimage/20150108132112.php")

I zoomed in a bit because of the background picture, but if I'm lying I'm dying. :p


Edit: perhaps a vbox install is different. I did a regular install from ISO on December 18th.

---

### Post by Elfy on 2015-01-08
> **Cavsfan said:**
> It definitely is on my system and I have proof. :)



It may very well be that it changed because I installed the alpha1 on December 18th when it came out. My boot lines in the default grub show as I posted above.
Just [COLOR=#ff0000]$vt_handoff [/COLOR] on the default systemd line and [COLOR=#ff0000]$vt_handoff init=/sbin/upstart[/COLOR] on the non-default option of upstart.
I don't really notice that much difference but upstart does appear to be a few seconds slower on this old pc.

Those lines I posted do indeed boot and work well in my custom grub. And I have it as 10_linux does: systemd default and upstart as an option.



That's rather peculiar as it's the opposite on my system and here the proof:

[[IMG]http://en.zimagez.com/miniature/20150108132112.jpg[/IMG]]("http://en.zimagez.com/zimage/20150108132112.php")

I zoomed in a bit because of the background picture, but if I'm lying I'm dying. :p


Edit: perhaps a vbox install is different. I did a regular install from ISO on December 18th.

But - is any of what you're seeing down to [http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Because - other than a couple of xubuntu specific ppa's and app installs - this install could be called vanilla ;)

This install was done the morning after 14.10 released.

Oct 24 07:50 casper.log

---

### Post by zika on 2015-01-08
> **Elfy said:**
> But - is any of what you're seeing down to [http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Because - other than a couple of xubuntu specific ppa's and app installs - this install could be called vanilla ;)

This install was done the morning after 14.10 released.

Oct 24 07:50 casper.logI [have]("http://ubuntuforums.org/showthread.php?t=2259716&p=13202120#post13202120") same order of entries in Grub menu and I did not customize it other than enetering quite a couple of kernel-line-switches. Vanilla Vivid (Sep 24 17:22 casper.log) with no PPAs that could change anything about Grub. Grub was changed last time:```
Start-Date: 2015-01-04  18:23:16Commandline: apt-get upgrade
Upgrade: grub-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub2-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc-bin:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc:amd64 (2.02~beta2-19, 2.02~beta2-20)
End-Date: 2015-01-04  18:23:59
```Just trying to help in this conversation. ;)

---

### Post by Elfy on 2015-01-08
> **zika said:**
> I [have]("http://ubuntuforums.org/showthread.php?t=2259716&p=13202120#post13202120") same order of entries in Grub menu and I did not customize it other than enetering quite a couple of kernel-line-switches. Vanilla Vivid (Sep 24 17:22 casper.log) with no PPAs that could change anything about Grub. Grub was changed last time:```
Start-Date: 2015-01-04  18:23:16Commandline: apt-get upgrade
Upgrade: grub-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub2-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc-bin:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc:amd64 (2.02~beta2-19, 2.02~beta2-20)
End-Date: 2015-01-04  18:23:59
```Just trying to help in this conversation. ;)

I'll be clean installing tomorrow some time on a new drive. 

I'll post with what a default install shows on hardware then. Not sure there'll be any difference to what one sees in a livesession

Again - I'm not sure if what you see is because of changes that you've made to the default setup :) (There are probably 100 posts in the last couple of months from both you and cavsfan fiddling with systemd/grub etc ;) )

---

### Post by zika on 2015-01-08
> **Elfy said:**
> Again - I'm not sure if what you see is because of changes that you've made to the default setup :) (There are probably 100 posts in the last couple of months from both you and cavsfan fiddling with systemd/grub etc ;) )Guilty as charged (for only a very small fraction of posts You've counted, just humbly noting) and ready for any (even harsh) consequences. I only can assure You that I'm quite certain that no change of mine provoked what I reported at the very beginning of this thread. Time will tell and just check versions of Grub I've reported... ;) Changelog is not (yet) available. But [https://launchpad.net/ubuntu/+source/grub2](https://launchpad.net/ubuntu/+source/grub2) gives the answer to You, I presume:> [COLOR=#333333]grub2 (2.02~beta2-20) unstable; urgency=medium[/COLOR]

  [ Colin Watson ]
  * Generate alternative init entries in advanced menu (closes: #757298,
    #773173).
  * When configuring grub-pc, copy unicode.pf2 to /boot/grub/ even if
    /boot/grub/grub.cfg does not exist yet; this matches the behaviour of
    grub-efi-* (thanks, Luca Capello; closes: #617196).

  [ Debconf translations ]
  * [fi] Finnish (Timo Jyrinki; closes: #774060).
  * [mr] Marathi (sampada nakhare; closes: #773901).

 -- Colin Watson <[cjwatson@debian.org]("https://launchpad.net/~cjwatson")>  Sat, 03 Jan 2015 12:39:52 +0000To help You in reading:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=757298](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=757298)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=773173](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=773173)

---

### Post by Cavsfan on 2015-01-08
> **Cavsfan said:**
> It definitely is on my system and I have proof. :)



It may very well be that it changed because I installed the alpha1 on December 18th when it came out. My boot lines in the default grub show as I posted above.
Just [COLOR=#ff0000]$vt_handoff [/COLOR] on the default systemd line and [COLOR=#ff0000]$vt_handoff init=/sbin/upstart[/COLOR] on the non-default option of upstart.
I don't really notice that much difference but upstart does appear to be a few seconds slower on this old pc.

Those lines I posted do indeed boot and work well in my custom grub. And I have it as 10_linux does: systemd default and upstart as an option.



That's rather peculiar as it's the opposite on my system and here the proof:

[[IMG]http://en.zimagez.com/miniature/20150108132112.jpg[/IMG]]("http://en.zimagez.com/zimage/20150108132112.php")

I zoomed in a bit because of the background picture, but if I'm lying I'm dying. :p


Edit: perhaps a vbox install is different. I did a regular install from ISO on December 18th.

> **Elfy said:**
> But - is any of what you're seeing down to [http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Because - other than a couple of xubuntu specific ppa's and app installs - this install could be called vanilla ;)

This install was done the morning after 14.10 released.

Oct 24 07:50 casper.log

Short answer no. I have all of my custom entries in **/etc/grub/06_custom** which displays at the top. I made **/etc/grub/10_linux** executable so I could show you the normal grub entries.
Which is what you see in the picture.


> **zika said:**
> I [have]("http://ubuntuforums.org/showthread.php?t=2259716&p=13202120#post13202120") same order of entries in Grub menu and I did not customize it other than entering quite a couple of kernel-line-switches. Vanilla Vivid (Sep 24 17:22 casper.log) with no PPAs that could change anything about Grub. Grub was changed last time:```
Start-Date: 2015-01-04  18:23:16Commandline: apt-get upgrade
Upgrade: grub-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub2-common:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc-bin:amd64 (2.02~beta2-19, 2.02~beta2-20), grub-pc:amd64 (2.02~beta2-19, 2.02~beta2-20)
End-Date: 2015-01-04  18:23:59
```Just trying to help in this conversation. ;)

Glad to see that someone else has systemd as default and upstart as the option. 

Like I said thanks zika for pointing this out. I will incorporate it into the wiki after final release. Once we do indeed know which one is default.
But that [COLOR=#ff0000]$vt_handoff[/COLOR] is new and I needed to know about that.

Could it be because we installed systemd-sysv and cut the line to upstart/init?

No that couldn't be it because how would that effect grub? I don't know as I've said most of you people have forgotten more than I know.

Do all of you with the different grub entries have vbox installs?

---

### Post by zika on 2015-01-09
> **Cavsfan said:**
> But that [COLOR=#ff0000]$vt_handoff[/COLOR] is new and I needed to know about that.? vt_handoff is here for at least several Ubuntu editions or better to say 4 years at least...
First pick, just to show date: [http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg](http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg) or even better: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658)

---

### Post by Elfy on 2015-01-09
So - clean install - the vampire bits of grub cfg

As you can see.

Standard option - no systemd
Advanced:
Standard option - no systemd
Second option - systemd
Recovery mode

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e' {
	recordfail
	savedefault
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
	else
	  search --no-floppy --fs-uuid --set=root 2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
	fi
	linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.18.0-8-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e' {
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-advanced-2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e' {
		recordfail
	savedefault
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		else
		  search --no-floppy --fs-uuid --set=root 2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-init-systemd-2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e' {
		recordfail
	savedefault
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		else
		  search --no-floppy --fs-uuid --set=root 2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e ro  quiet splash $vt_handoff init=/lib/systemd/systemd
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-recovery-2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		else
		  search --no-floppy --fs-uuid --set=root 2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=2a6a3ef2-ac77-4eed-83fb-fa5016ee9a5e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
}
```

---

### Post by Cavsfan on 2015-01-09
> **Cavsfan said:**
> 
But that [COLOR=#ff0000]$vt_handoff[/COLOR] is new and I needed to know about that.

> **zika said:**
> ? vt_handoff is here for at least several Ubuntu editions or better to say 4 years at least...
First pick, just to show date: [http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg](http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg) or even better: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658)

That's very interesting! Thanks for finding that. It mentions Natty.
When I joined my first version was Jaunty, then Karmic but when Lucid LTS came out I skipped Maverick, Natty and Oneiric but got back in with Quantal as I seen the HowTo Ranch hand helped me create was becoming obsolete and wrong. So, then I started joining in on the development of every release since.
Luckily Drs305 was there to help me out then.

I don't think it matters at least very much if you don't have $vt_handoff in there. I haven't had it once and no problems whatsoever. It may not in this instance either. I think I'll check that theory out shortly.
You know that bug is a dup of this one [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686)
And the fix was released for Natty. :p

What I do not get at all is when I install a version after final release and use the default grub no matter which OS I select besides the one I just installed I it "looks like" it is booting into say Mint 17.
I see the green dots and everything and it says Mint 17 but never goes anywhere and after several minutes of waiting for something to happen. 
I press the Alt+Cntl+F1 to get to tty and it says I'm in Precise 12.04.5! :confused: I've tried several others and the same thing happens.
So then I install grub on Precise and then and only then when using my custom grub menu I boot into which one I had the grub on in the first place and install it there.

One would think that the new install would have a working grub selection but not so at least in my case.

---

### Post by Cavsfan on 2015-01-09
Here is my grub.cfg (and it is straight from 10_linux like yours is):
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bef4bb7d-6065-45ff-ab83-aac86a26c859' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bef4bb7d-6065-45ff-ab83-aac86a26c859
    else
      search --no-floppy --fs-uuid --set=root bef4bb7d-6065-45ff-ab83-aac86a26c859
    fi
    linux    /boot/vmlinuz-3.18.0-8-generic root=UUID=bef4bb7d-6065-45ff-ab83-aac86a26c859 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.18.0-8-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bef4bb7d-6065-45ff-ab83-aac86a26c859' {
    menuentry 'Ubuntu, with Linux 3.18.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-advanced-bef4bb7d-6065-45ff-ab83-aac86a26c859' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bef4bb7d-6065-45ff-ab83-aac86a26c859
        else
          search --no-floppy --fs-uuid --set=root bef4bb7d-6065-45ff-ab83-aac86a26c859
        fi
        echo    'Loading Linux 3.18.0-8-generic ...'
        linux    /boot/vmlinuz-3.18.0-8-generic root=UUID=bef4bb7d-6065-45ff-ab83-aac86a26c859 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-8-generic
    }
    menuentry 'Ubuntu, with Linux 3.18.0-8-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-init-upstart-bef4bb7d-6065-45ff-ab83-aac86a26c859' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bef4bb7d-6065-45ff-ab83-aac86a26c859
        else
          search --no-floppy --fs-uuid --set=root bef4bb7d-6065-45ff-ab83-aac86a26c859
        fi
        echo    'Loading Linux 3.18.0-8-generic ...'
        linux    /boot/vmlinuz-3.18.0-8-generic root=UUID=bef4bb7d-6065-45ff-ab83-aac86a26c859 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-8-generic
    }
    menuentry 'Ubuntu, with Linux 3.18.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-recovery-bef4bb7d-6065-45ff-ab83-aac86a26c859' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  bef4bb7d-6065-45ff-ab83-aac86a26c859
        else
          search --no-floppy --fs-uuid --set=root bef4bb7d-6065-45ff-ab83-aac86a26c859
        fi
        echo    'Loading Linux 3.18.0-8-generic ...'
        linux    /boot/vmlinuz-3.18.0-8-generic root=UUID=bef4bb7d-6065-45ff-ab83-aac86a26c859 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-8-generic
    }

```
I'm pretty sure it's because zika and I installed **systemd-sysv** which made our default systemd. But I cannot prove it.

This is getting interesting. :p

If you haven't installed systemd-sysv try doing that and then see what happens.

---

### Post by Elfy on 2015-01-09
I'll check that out in a vm probably :p

---

### Post by Cavsfan on 2015-01-09
> **Elfy said:**
> I'll check that out in a vm probably :p

You do that and I'll checkout removing the $vt_handoff from my custom boot lines. :p

---

### Post by Cavsfan on 2015-01-09
Nope $vt_handoff makes nary a difference. :p

I don't really see any Plymouth screen but it just displays a few lines in tty like starting version 218 etc and then I'm looking at LightDM login screen.

---

### Post by Elfy on 2015-01-09
Well installing systemd-sysv didn't appear to make any difference to that.

as installed in vbox

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
	else
	  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
	fi
	linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.18.0-8-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-advanced-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-init-systemd-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff init=/lib/systemd/systemd
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-recovery-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
```

as it appears following systemd-sysv install

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
	else
	  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
	fi
	linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.18.0-8-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-advanced-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (systemd)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-init-systemd-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro  quiet splash $vt_handoff init=/lib/systemd/systemd
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-8-generic-recovery-8bc64147-c4b0-432f-a04e-d3fcd7fe14b3' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		else
		  search --no-floppy --fs-uuid --set=root 8bc64147-c4b0-432f-a04e-d3fcd7fe14b3
		fi
		echo	'Loading Linux 3.18.0-8-generic ...'
		linux	/boot/vmlinuz-3.18.0-8-generic root=UUID=8bc64147-c4b0-432f-a04e-d3fcd7fe14b3 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.18.0-8-generic
```

---

### Post by zika on 2015-01-09
> **Elfy said:**
> Well installing systemd-sysv didn't appear to make any difference to that.
as installed in vbox...
as it appears following systemd-sysv install...I've altered my post (1st in this thread) to reflect correctly the current state of matter in Grub now. Thank You for additional effort to clarify.

---

### Post by Cavsfan on 2015-01-09
I don't know the answer to this but I don't think a VirtualBox install is like a hard install. Someone prove me wrong.

Zika installed systemd-sysv a long time ago and the first thing I did was install systemd-sysv after I installed the alpha from ISO doing away with Upstart/init.
As zika said remove the init=/lib/systemd/systemd boot line and I booted systemd everytime. I could no longer get to upstart.

So a few days ago I found out from zika's first post in this thread that there is a way to boot upstart by adding init=/sbin/upstart to that boot line.
So I made /etc/grub.d/10_linux executable to see what the cfg file looked like and it looked probably just like zika's does. 
1)default systemd 
2)upstart 
3)recovery.

It has to be one way or the other. This keep getting stranger and stranger! :p

---

### Post by Elfy on 2015-01-09
> **zika said:**
> I've altered my post (1st in this thread) to reflect correctly the current state of matter in Grub now. Thank You for additional effort to clarify.

Heh - well we all do that where we can.

For the most part I was trying to make sure I wasn't going doolally here :)

---

### Post by Cavsfan on 2015-01-09
Yes, but, but but, doesn't there have to be a definitive answer as to which is default?

2 systems are one way and apparently everyone else's systems are the opposite.

That's the most enigmatic thing I've ever heard of.

---

### Post by Elfy on 2015-01-09
> **Cavsfan said:**
> Yes, but, but but, doesn't there have to be a definitive answer as to which is default?

2 systems are one way and apparently everyone else's systems are the opposite.

That's the most enigmatic thing I've ever heard of.

Do a clean install, don't fiddle about with it  - if THAT is different than mine - let me know :)

---

### Post by Elfy on 2015-01-10
so - perhaps this IS a bug :)

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch)

---

### Post by zika on 2015-01-10
> **Elfy said:**
> so - perhaps this IS a bug :)

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch)My previous (see footnote) case:
> **Permanent switch**

[COLOR=#333333][FONT=Ubuntu Beta]Install the systemd-sysv package. This will remove ubuntu-minimal, ureadahead, andupstart (but should not remove anything else -- if it does, yell!). After that, grub's "Advanced options" menu will have a corresponding "Ubuntu, with Linux ... (upstart)" entry where you can do an one-time boot with upstart.[/FONT][/COLOR]

Update&#8321;: OK, You've made me install (again) ubuntu-minimal, ureadahead and upstart and now I have additional SystemD entry (which I've embraced wholeheartedly) and UpStart is at place &#8222;0&#8220;... ;) After cleaning machine (deep down below he desk) from dust (fan was crying) this was (especially at my age) an easy job... ;)
Update&#8322;: Corrected the name of this thread...
Update&#8323;: Do not forget to run *update-grub* after returning to Upstart as default... ;) I did forget here on my office machine after 11 days break and was perplexed for .001ms... ;)

---

### Post by Cavsfan on 2015-01-10
I guess I understand now.
If you do the **Permanent switch** then you will have systemd as default and upstart as an option.
If you don't it will be vice versa.

Makes sense to me.

---

### Post by Mateusz Stachowski on 2015-01-11
I've upgraded yesterday from 14.04 LTS to 15.04 directly:

> sudo sed -i 's/trusty/vivid/g' /etc/apt/sources.list

and Upstart is the default init with systemd appearing in advanced options as alternative.

---

### Post by grahammechanical on 2015-01-12
I just put in a vivid server install daily 20150112 and upstart is default and systemd an advanced option.

---

### Post by Elfy on 2015-01-13
> **Elfy said:**
> so - perhaps this IS a bug :)

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch](https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch)

nvm ... note to self - think about what you're doing if you're doing it early in the day.

For those who'll go to that wiki over the next few months - sudo update-grub is now in the list of things to do :D

---

### Post by grahammechanical on 2015-01-13
That wiki does make clear why some of us have upstart as an advanced option while others have systemd as an advanced option.

> [COLOR=#333333][FONT=Ubuntu Beta]Install the [/FONT][/COLOR]systemd-sysv[COLOR=#333333][FONT=Ubuntu Beta] package. This will remove [/FONT][/COLOR]ubuntu-minimal[COLOR=#333333][FONT=Ubuntu Beta], [/FONT][/COLOR]ureadahead[COLOR=#333333][FONT=Ubuntu Beta], and[/FONT][/COLOR]upstart[COLOR=#333333][FONT=Ubuntu Beta] (but should not remove anything else -- if it does, yell!). After that and [/FONT][/COLOR]sudo update-grub[COLOR=#333333][FONT=Ubuntu Beta], grub's "Advanced options" menu will have a corresponding "Ubuntu, with Linux ... (upstart)" entry where you can do an one-time boot with upstart.[/FONT][/COLOR]

A kernel upgrade will run update-grub. And we have had a few of them. Oh, isn't every boot a "one time" boot until the next boot? What happens if I run the option twice?

---

### Post by Cavsfan on 2015-01-13
> **grahammechanical said:**
> That wiki does make clear why some of us have upstart as an advanced option while others have systemd as an advanced option.

> [COLOR=#333333][FONT=Ubuntu Beta]Install the [/FONT][/COLOR]systemd-sysv[COLOR=#333333][FONT=Ubuntu Beta] package. This will remove [/FONT][/COLOR]ubuntu-minimal[COLOR=#333333][FONT=Ubuntu Beta], [/FONT][/COLOR]ureadahead[COLOR=#333333][FONT=Ubuntu Beta], and[/FONT][/COLOR]upstart[COLOR=#333333][FONT=Ubuntu Beta] (but should not remove anything else -- if it does, yell!). After that and [/FONT][/COLOR]sudo update-grub[COLOR=#333333][FONT=Ubuntu Beta],  grub's "Advanced options" menu will have a corresponding "Ubuntu, with  Linux ... (upstart)" entry where you can do an one-time boot with  upstart.[/FONT][/COLOR]

A kernel upgrade will run update-grub. And we have had a few of them. Oh, isn't every boot a "one time" boot until the next boot? What happens if I run the option twice?

I agree that is the best answer so far.

If you mean **sudo update-grub** - nothing will change unless you changed something in a grub file. You can run it over and over and the results will be the same. 
It's if you _do not_ run it after making changes that they will not become permanent. But, I'm fairly sure you already know this.

---

### Post by Elfy on 2015-01-13
> **grahammechanical said:**
> That wiki does make clear why some of us have upstart as an advanced option while others have systemd as an advanced option.



A kernel upgrade will run update-grub. And we have had a few of them. Oh, isn't every boot a "one time" boot until the next boot? What happens if I run the option twice?

Kernel upgrade might run update-grub.

Doing those changes without running update-grub will leave grub showing systemd as the one-time boot option.

Run the option twice and you'll be booting what isn't default - either systemd or upstart.

Wording could possibly be slightly different perhaps, maybe something like

> where you can do use the one-time boot option with upstart.

but I'm not interested enough nor bothered enough to change it.

---

### Post by ventrical on 2015-01-13
> **grahammechanical said:**
> That wiki does make clear why some of us have upstart as an advanced option while others have systemd as an advanced option.



A kernel upgrade will run update-grub. And we have had a few of them. Oh, isn't every boot a "one time" boot until the next boot? What happens if I run the option twice?

Have you checked your Unity-Desktop-Next install because  it pretty well destroyed my (original) install and the systemd option does not present itself - even though I seen it install before my very eyes.

Regards..

---

### Post by grahammechanical on 2015-01-13
I have Unity-Desktop-Next and Unity8-lxc but I have kept away from them over the holiday period because it was clear that there was little in the way of updates to Vivid let alone Unity8. I have seen some videos from developers showing the work that they are doing but the code has not come down on my installs.

A recent video showed a dialog that let us switch between desktop mode with apps in re-sizable windows and phone mode with apps full screen. So, things are moving forward. 

I am not surprised if systemd breaks Unity 8 because the phone uses Upstart. The only issue I have with the decision to switch to systemd is that it should not delay the release of a Ubuntu phone. Just as convergence brings Unity 8 from the phone to the desktop, So it will bring systemd from the desktop to the phone.

Regards.

EDIT: Have now updated both of my Ubuntu Desktop Next installs (Nouveau and Nvidia) and both now have Grub 2.02~beta2-20 with a systemd advanced option and in both Mir+Unity8 are now broken - black screen with white hardware cursor. Neither install has kernel 3.18 yet, so that is not the problem. They work up to the LightDM login screen.

---

### Post by Cavsfan on 2015-01-15
A simple solution to "the dilemma" or Permanent switch is to enter this:

**sudo apt-get install systemd-sysv && sudo update-grub** 

I believe that will solve the dilemma. That is if you don't want upstart as default even though you will have systemd as an option.

---

### Post by Cavsfan on 2015-03-06
FWIW: Martin Pitt made the change to do an update-grub when you first install systemd-sysv and go total systemd.

I just did that and seen the update-grub in the output.

```
systemd (219-4ubuntu3) vivid; urgency=medium

  * Merge experimental branch.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 05 Mar 2015 16:41:24 +0100

systemd (219-5) UNRELEASED; urgency=medium

  [ Didier Roche ]
  * Add "systemd-fsckd" autopkgtest. (LP: #1427312)

  [ Martin Pitt ]
  * journald: Suppress expected cases of "Failed to set file attributes"
    errors. (LP: #1427899)
  * Add systemd-sysv.postinst: Update grub on first installation, so that the
    alternative init system boot entries get updated.
  * debian/tests: Call /tmp/autopkgtest-reboot, to work with autopkgtest >=
    3.11.1.
  * Check for correct architecture identifiers for SuperH. (Closes: #779710)
  * Fix tmpfiles.d to only apply the first match again (regression in 219).
    (LP: #1428540)

 -- Martin Pitt <mpitt@debian.org>  Tue, 03 Mar 2015 14:51:46 +0100
```

---


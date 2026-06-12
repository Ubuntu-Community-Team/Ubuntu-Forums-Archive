---
title: "Initng = Improving Boot by leaps and bounds!"
date: 2005-05-07
forum: The Cafe
---

### Post by vassalle on 2005-05-07
Hi guys, i really dont know where to post this request, so i guess ill just put it here.. anyways, theres this new program/software that could really improve the boot time. However, the guy whos creating it is using gentoo, so he said that its a bit gentooish.. 

as u can see, i dont really know much of this stuff. so, my request is that some of the ubuntu gurus check it out and possibly maybe find a way to integrate it into this already great distro! anyway, check it out ureself.. the website is here, [http://jw.dyndns.org/initng/](http://jw.dyndns.org/initng/) and theres also a link to the wiki from that page.. 

I did try to install it on my machine, but i get loads of errors.. but thankfully its not something that could broke my machine.. hope u guys could check it out and help a newbie like me..  ](*,)

---

### Post by RastaMahata on 2005-05-07
woah, from 41 to 21 seconds... nice :)

---

### Post by vassalle on 2005-05-07
[QUOTE=RastaMahata]woah, from 41 to 21 seconds... nice :)[/QUOTE]
 i installed bootchart and mine is like 85 seconds! heh.. and im on p4 3.0 @ 3.5ghz with 1 gig of ram.. grrr

---

### Post by XDevHald on 2005-05-07
[QUOTE=vassalle]i installed bootchart and mine is like 85 seconds! heh.. and im on p4 3.0 @ 3.5ghz with 1 gig of ram.. grrr[/QUOTE]

Also note that the link below also gives great information as well on this topic too.
[http://www.ubuntuforums.org/showthread.php?t=32004&highlight=initng]("http://www.ubuntuforums.org/showthread.php?t=32004&highlight=initng")

To keep topics from being made again that are in same relation, please use the search button on the navigation as this will keep the forums from getting double posting of the same topics or same subject to the relations of the same users.

Cheers :D

---

### Post by vassalle on 2005-05-07
well, kinda.. but both of it are actually for launchd, which is different compared to initng.. besides for both of the forums, u'll need to go to page 2 or something to even see anything about initng..  hope that made sense ? :D

---

### Post by AndersAA on 2005-05-12
[QUOTE=vassalle]I did try to install it on my machine, but i get loads of errors.. but thankfully its not something that could broke my machine.. hope u guys could check it out and help a newbie like me..  ](*,)[/QUOTE]

if you cp system/agetty.i system/getty.i and search and replace agetty with getty in getty.i, then fix system.runlevels to load getty instead of agetty it should work.
(although you'll only have getty listening on tty2-9 for some reason).

initng is going through some massive changes right now as you can see on the mailinglist archive available on the site, it should be far better service files soon and I'll cook up some ubuntu (debian really) tweaked services ;)

---

### Post by vassalle on 2005-05-12
[QUOTE=AndersAA]if you cp system/agetty.i system/getty.i and search and replace agetty with getty in getty.i, then fix system.runlevels to load getty instead of agetty it should work.
(although you'll only have getty listening on tty2-9 for some reason).

initng is going through some massive changes right now as you can see on the mailinglist archive available on the site, it should be far better service files soon and I'll cook up some ubuntu (debian really) tweaked services ;)[/QUOTE]
 thanks Anders! finally theres someone who would try to port this to Ubuntu/debian.. ;)

---

### Post by verbalshadow on 2005-05-15
Any progress on this yet?, i get errors just trying to compile it. oh well. i'll just wait.

---

### Post by AndersAA on 2005-05-15
[QUOTE=verbalshadow]Any progress on this yet?, i get errors just trying to compile it. oh well. i'll just wait.[/QUOTE]

it's in so rapid development at this point if I were you I'd use the svn source (apt-get install subversion and use the svn address on the homepage).

Also "i get errors" ain't really gonna get you any help ;), it doesn't compile cleanly for me either atm (because of glibc errors, not initng) but the block which causes it is a DEBUG one and can be safely commented out.

---

### Post by verbalshadow on 2005-05-16
> **AndersAA]it's in so rapid development at this point if I were you I'd use the svn source (apt-get install subversion and use the svn address on the homepage).

Also "i get errors" ain't really gonna get you any help  said:**
> 
 here is the error i get. i haven't looked into it yet, maybe tonight
not sure if this is the error your talking about. doubt it as it looks to be bash_executor.c related.

[QUOTE]make[1]: Entering directory `/home/verbalshadow/fert/code/initng-0.0.17/src'
gcc -fPIC -O2 -pipe -g  -Wall -W -Werror -c bash_executor.c
bash_executor.c: In function `bash_this':
bash_executor.c:133: warning: implicit declaration of function `WIFCONTINUED'
make[1]: *** [bash_executor.o] Error 1

---

### Post by XDevHald on 2005-05-16
[QUOTE=verbalshadow]here is the error i get. i haven't looked into it yet, maybe tonight
not sure if this is the error your talking about. doubt it as it looks to be bash_executor.c related.[/QUOTE]
 Hmm,

[php]Cant execute source /sbin/agetty, "9600 tty2" !
	 tgetty/2						 [error]	 (ret_code: 1)
	 tgetty/2						 [restart][/php]

That's my error :p Anyone have a great idea of how I can fix this little mess?

---

### Post by AndersAA on 2005-05-16
comment out and remove the lines causing it (it's a DEBUG block).

---

### Post by AndersAA on 2005-05-16
[QUOTE=BB]Hmm,

[php]Cant execute source /sbin/agetty, "9600 tty2" !
	 tgetty/2						 [error]	 (ret_code: 1)
	 tgetty/2						 [restart][/php]

That's my error :p Anyone have a great idea of how I can fix this little mess?[/QUOTE]

yeah, do as I said earlier and make a getty service, your using the agetty one and that's bound to fail (ubuntu doesn't have agetty), also modify system.runlevel to run that getty service instead of agetty.

---

### Post by XDevHald on 2005-05-16
[QUOTE=AndersAA]yeah, do as I said earlier and make a getty service, your using the agetty one and that's bound to fail (ubuntu doesn't have agetty), also modify system.runlevel to run that getty service instead of agetty.[/QUOTE]

 Ok did that, I also updated to 0.0.18 from .17. I had to reimpliment the command back into grub.conf and now I get this.

[php] FAIL initng_handler.c: handle_killed_start(tgetty/2): Returned with exit 1.
	 tgetty/2						 [restart]
100% tgetty/2						 [started]	 (pid : 7997).
 ** FAIL remote_control.c: error open /etc/initng/in-test and /etc/initng/out-test
[/php]

Ooo, I love this stuff :D

---

### Post by AndersAA on 2005-05-16
do you get that when you reboot or when you boot?


"FAIL remote_control.c: error open /etc/initng/in-test "
that should be greated during compile.  So unless you rm -rf'ed /etc/initng and cp -r'ed in new ones (much like myself) that shouldn't happen.

---

### Post by XDevHald on 2005-05-16
oh, it only happens when I type **initng **in a terminal. But other than that, the startup is 15 seconds, was 40-45.

---

### Post by AndersAA on 2005-05-18
if those of you who are feeling suicidal could have a look at :
[http://forum.initng.thinktux.net/viewtopic.php?t=5](http://forum.initng.thinktux.net/viewtopic.php?t=5)

it should boot, even with lvm2 on root like I use, but if your in any way unsure about how to use this, dont bother.  This is for those who are feeling like experimenting, it's not a good idea to try to replace your boot system with just yet ;)

---

### Post by vassalle on 2005-05-22
[QUOTE=AndersAA]if those of you who are feeling suicidal could have a look at :
[http://forum.initng.thinktux.net/viewtopic.php?t=5](http://forum.initng.thinktux.net/viewtopic.php?t=5)

it should boot, even with lvm2 on root like I use, but if your in any way unsure about how to use this, dont bother.  This is for those who are feeling like experimenting, it's not a good idea to try to replace your boot system with just yet ;)[/QUOTE]
 which one is ure post again ? neuron is it ?

---

### Post by AndersAA on 2005-05-22
[QUOTE=vassalle]which one is ure post again ? neuron is it ?[/QUOTE]

correct

---

### Post by vassalle on 2005-05-22
[QUOTE=AndersAA]correct[/QUOTE]
 let me get this clear? u said that ill have to replace my initng files.. but i cant even install the initng in the first place.. by the way, theres a new forum in the website. and theres a guy who have created a .deb for initng-0.1.18.. could i install using that and then replace it with ures ?

---


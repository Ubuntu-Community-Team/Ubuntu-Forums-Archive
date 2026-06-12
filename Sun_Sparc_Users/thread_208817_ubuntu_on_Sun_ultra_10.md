---
title: "ubuntu on Sun ultra 10???"
date: 2006-07-04
forum: Sun Sparc Users
---

### Post by jpgeerets on 2006-07-04
hi folks!

i have here a sun ultra10. this machine has nothing to do this moment.

is it possible to install ubuntu server on this?

perhaps someone knows?

tnx in advance!!!

Jean-Paul

---

### Post by chris_andrew on 2006-07-04
This is what i'd like to do, but am currently having problems with the install.  Due (I think) to my OBP *.version*.  See my post.

Cheers,

Chris.

---

### Post by jpgeerets on 2006-07-04
[QUOTE=chris_andrew]This is what i'd like to do, but am currently having problems with the install.  Due (I think) to my OBP *.version*.  See my post.

Cheers,

Chris.[/QUOTE]


chris,
thanks for your fast responce!


so i guess the only thing i can do is wait.....?

cheers

Jean-Paul

---

### Post by chris_andrew on 2006-07-04
Jean-Paul,

Can you download the *iso* an d try to install it on your U10.  It would be useful to know what version of OBP you are running, too.

Type:

```
.version
```

at the OBP prompt.

Thanks,

Chris.

---

### Post by jpgeerets on 2006-07-04
[QUOTE=chris_andrew]Jean-Paul,

Can you download the *iso* an d try to install it on your U10.  It would be useful to know what version of OBP you are running, too.

Type:

```
.version
```

at the OBP prompt.

Thanks,

Chris.[/QUOTE]



ok,
this sounds exciting... :-)
but, im not that smart on sun machines.....
if you can tell what OBP means?
thanks!

Jean-Paul

---

### Post by chris_andrew on 2006-07-04
Jean-Paul,

The OBP is like the BIOS on a PC, but seems to be much more powerful.

You can get to the prompt by pressing *STOP+A *on a Sun keyboard.

If you type *.version*, it should tell you your OBP version.

There is a great OBP overview on the net, but I couldn't find it, a few seconds ago.  Anyone got the link?

Cheers,

Chris.

---

### Post by allnameswereout on 2006-07-04
Normally this should work:

> Start the U10 with a monitor and keyboard connected to it.
Put the Ubuntu Server CDROM into it.
Press Stop + A. If you get the *ok* prompt, you're in OBP. If not, let the machine try to boot up and press Stop + A again.
In the OBP, type *boot cdrom*.
You should boot up the CDROM now. You can now install Ubuntu Server.

This worked for me on a U5 machine (almost identical to U10) with OBP 3.25. Also, OpenBSD installed on a U5 machine with OBP 3.15.

If your OBP is too old, search at [www.sun.com](www.sun.com) for documentation how to upgrade your OBP.
In the other thread about OBP this was found out by others:

* Documentation on how to upgrade OBP [http://sunsolve.sun.com/search/advsearch.do?collection=PATCH&type=collections&queryKey5=106121&toDocument=yes](http://sunsolve.sun.com/search/advsearch.do?collection=PATCH&type=collections&queryKey5=106121&toDocument=yes)

* You need a working Solaris (freely downloadable) environment to upgrade your OBP.

Thread on this, here: [http://www.ubuntuforums.org/showthread.php?t=200603](http://www.ubuntuforums.org/showthread.php?t=200603)

---

### Post by allnameswereout on 2006-07-04
I found this a useful start on OBP upgrading as well [http://developers.sun.com/solaris/articles/openboot_sparc.html](http://developers.sun.com/solaris/articles/openboot_sparc.html)

---

### Post by jpgeerets on 2006-07-05
[QUOTE=allnameswereout]I found this a useful start on OBP upgrading as well [http://developers.sun.com/solaris/articles/openboot_sparc.html](http://developers.sun.com/solaris/articles/openboot_sparc.html)[/QUOTE]


this all sounds great!
i hope i have some time today at work so i can try this all!
i will put the results here.... :-)

thanks for all you efforts

---

### Post by jpgeerets on 2006-07-05
[QUOTE=chris_andrew]Jean-Paul,

The OBP is like the BIOS on a PC, but seems to be much more powerful.

You can get to the prompt by pressing *STOP+A *on a Sun keyboard.

If you type *.version*, it should tell you your OBP version.

There is a great OBP overview on the net, but I couldn't find it, a few seconds ago.  Anyone got the link?

Cheers,

Chris.[/QUOTE]


chris,

i boot the system to the OBP.
type .version
this it tells me....

OBP: 3.31.0 25/07/2001
POST: 3.1.0 27/07/2001

perhaps this is older? newer? ok? :-)

Jean-Paul

---

### Post by chris_andrew on 2006-07-05
This is the same OBP version that I now have.  Unfortunately Ubuntu fails to get past "Booting Linux...", still.

I have tried Debian Etch, and that also has the same problem.  if you boot with a 2.4 kernel not 2.6), everything is fine.  I am doing this at the moment, but then am going to replace the 2.4 kernel with a 2.6 one.  I think my machine will then become unbootable.

From this I can conclude that it is not actually SILO that is buggy, for some reason, the 2.6 kernel just doesn't seem very happy on U10 (and 5's?).  I wonder what kernel Gentoo use, because that installs fine on my U10?

Cheers,

Chris.

---

### Post by jpgeerets on 2006-07-05
[QUOTE=chris_andrew]This is the same OBP version that I now have.  Unfortunately Ubuntu fails to get past "Booting Linux...", still.

I have tried Debian Etch, and that also has the same problem.  if you boot with a 2.4 kernel not 2.6), everything is fine.  I am doing this at the moment, but then am going to replace the 2.4 kernel with a 2.6 one.  I think my machine will then become unbootable.

From this I can conclude that it is not actually SILO that is buggy, for some reason, the 2.6 kernel just doesn't seem very happy on U10 (and 5's?).  I wonder what kernel Gentoo use, because that installs fine on my U10?

Cheers,

Chris.[/QUOTE]


i found this on the internet.....

[http://developers.sun.com/solaris/articles/openboot_sparc.html](http://developers.sun.com/solaris/articles/openboot_sparc.html)

here is a link on the page that points to this page:
[http://onesearch.sun.com/search/onesearch/index.jsp?qt=flash+update+ultra+10&charset=UTF-8&rf=0&rt=1&site=sunsolve&nh=10&cs=0&col=support-patches&otf=ss&otf=sunsolve](http://onesearch.sun.com/search/onesearch/index.jsp?qt=flash+update+ultra+10&charset=UTF-8&rf=0&rt=1&site=sunsolve&nh=10&cs=0&col=support-patches&otf=ss&otf=sunsolve)

finaly here is to read a doc for the firmware U10
[http://sunsolve.sun.com/search/document.do?assetkey=1-21-106121-18-1](http://sunsolve.sun.com/search/document.do?assetkey=1-21-106121-18-1)

this doc said:
...
LATEST  flash-update-Ultra510-18; flash-update-Ultra510-latest 
        All Models
            OBP: 3.31 Version 0 created 2001/07/25 20:36
            POST: 3.1.0
...

so it seems this is the latest OBP sun delivers for this hardware.

but it is great to read this page totaly.
there they also tells how to update the OBP if it is necessary....

Jean-Paul

---

### Post by chris_andrew on 2006-07-05
Jean-Paul,

Have you tried to do an installation?

I have filed the following bug-report.

I would appreciate it if you could add comments, should you want to.

[https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236](https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236)

Thanks,

Chris.

---

### Post by allnameswereout on 2006-07-05
Congrats on the OBP upgrade :)

Its a known bug also spoken of in
[http://www.ubuntuforums.org/showthread.php?t=200686](http://www.ubuntuforums.org/showthread.php?t=200686)
And
[https://wiki.ubuntu.com/sparc/KnownIssues](https://wiki.ubuntu.com/sparc/KnownIssues)
The latter suggests netboot. I wonder if using the CD to boot up would work?

(I assume is same issue.)

Did you both verify you burned the CD correctly btw? MD5?

As for 2.4.x vs 2.6.x. If 2.4.x works, keep that image around. In SILO you should then be able to boot it. Keep an install/rescue CD which can boot up around just in case (or netboot).

---

### Post by chris_andrew on 2006-07-05
Hi,

Burned CD at x4, should be fine, it is with other distros.  2.4 kernel is only available on Debian, not Ubuntu, so can't use the 2.4.

Cheers,

Chris.

---

### Post by jpgeerets on 2006-07-06
[QUOTE=chris_andrew]Jean-Paul,

Have you tried to do an installation?

I have filed the following bug-report.

I would appreciate it if you could add comments, should you want to.

[https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236](https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236)

Thanks,

Chris.[/QUOTE]


back at work now, so time to play... ;-)

i have tryed yesterday to download the sparc iso. this was no problem, but burning the iso to disk was less easyer.
im going to try to make a cd today, after that i can try to install.
i work on a windowsxp machine, so i guess i will have "play" a little when trying to burn the cd.

shure i will add my comments chris, i will help where it is possible for me... :-)

what about netboot? shout it be possible to boot and install over the network?


cheers

Jean-Paul

---

### Post by allnameswereout on 2006-07-06
Odd. I used Debian before Ubuntu with both 2.4.x and 2.6.x on a U5, with SILO on HDD. Both kernels booted flawless. Consider using Debian? Or using Debian to install SILO, eventually chrooting, or is that not possible? Or netboot.

(Even though a U5 is almost identical to a U10 its interesting you both have a U10 whereas both machines fail to cooperate with SILO.)

[QUOTE=jpgeerets]i have tryed yesterday to download the sparc iso. this was no problem, but burning the iso to disk was less easyer.
im going to try to make a cd today, after that i can try to install.[/quote]

Shouldn't be a big issue to burn it. Just make sure the integrity of the ISO is correct, using e.g. md5sum.exe. A search engine gives you a Windows port of this utility. Developers should not take people who do not do this too seriously because a broken ISO is among the most plausible reasons an install fails. Make sure you don't fall into this category of ignorant users. After you verified this you can use e.g. Nero, select the image, and off you go. Nero can also verify the burn is authentic which together with having done a md5 compare lowers the chance of not having an authentic CD to one with a *lot * of decimals after the 0%. This is as easy (or hard) as burning any other ISO.

> what about netboot? shout it be possible to boot and install over the network?

Yes. Not only booting and installing. Using netboot, one could completely evade the need for a bootloader. This is why the netboot method is stated as alternative to SILO. You could also install Ubuntu using the CD and then instead of installing SILO you will use netboot.

About any *NIX can be used for this, client or server. All Unices have support for the server software. From a client-side perspective OBP is notorious for supporting this very well whereas on x86 BIOS this is hard to accomplish. I've never done this with SPARC, but have on MIPS as client using a Linux machine to serve the files. I've installed IRIX and Linux this way. You need some basic networking knowledge to set up the server. There are various howtos for this floating around the Internet. Some probably even OBP-specific.

If you're on Windows XP, try tftpd32 it comes with a TFTP and BOOTP implementation (you need both). [http://tftpd32.jounin.net/](http://tftpd32.jounin.net/). Later, if you're satisfied, you can tell OBP to default to netbooting. Given your Sun will depend on the Windows XP machine as server for netbooting, it better be stable.

Let me know if you have any specific questions. Good luck!

---

### Post by jpgeerets on 2006-07-06
[QUOTE=allnameswereout]Odd. I used Debian before Ubuntu with both 2.4.x and 2.6.x on a U5, with SILO on HDD. Both kernels booted flawless. Consider using Debian? Or using Debian to install SILO, eventually chrooting, or is that not possible? Or netboot.

(Even though a U5 is almost identical to a U10 its interesting you both have a U10 whereas both machines fail to cooperate with SILO.)



Shouldn't be a big issue to burn it. Just make sure the integrity of the ISO is correct, using e.g. md5sum.exe. A search engine gives you a Windows port of this utility. Developers should not take people who do not do this too seriously because a broken ISO is among the most plausible reasons an install fails. Make sure you don't fall into this category of ignorant users. After you verified this you can use e.g. Nero, select the image, and off you go. Nero can also verify the burn is authentic which together with having done a md5 compare lowers the chance of not having an authentic CD to one with a *lot * of decimals after the 0%. This is as easy (or hard) as burning any other ISO.



Yes. Not only booting and installing. Using netboot, one could completely evade the need for a bootloader. This is why the netboot method is stated as alternative to SILO. You could also install Ubuntu using the CD and then instead of installing SILO you will use netboot.

About any *NIX can be used for this, client or server. All Unices have support for the server software. From a client-side perspective OBP is notorious for supporting this very well whereas on x86 BIOS this is hard to accomplish. I've never done this with SPARC, but have on MIPS as client using a Linux machine to serve the files. I've installed IRIX and Linux this way. You need some basic networking knowledge to set up the server. There are various howtos for this floating around the Internet. Some probably even OBP-specific.

If you're on Windows XP, try tftpd32 it comes with a TFTP and BOOTP implementation (you need both). [http://tftpd32.jounin.net/](http://tftpd32.jounin.net/). Later, if you're satisfied, you can tell OBP to default to netbooting. Given your Sun will depend on the Windows XP machine as server for netbooting, it better be stable.

Let me know if you have any specific questions. Good luck![/QUOTE]



past hours i have download the iso again. this time from the US.
burn on cd was no problem. perhaps my previous iso was not 100%.

but the cd into the U10 and type <boot cdrom>

yeah! stuff seems to work.
at this moment he is copy-ing the files.
it says: unpacking base system. 48%

just take a cup of coffee (with beans ofcourse) and wait....

more later!!!

byebye

Jean-Paul

---

### Post by jpgeerets on 2006-07-06
[QUOTE=jpgeerets]past hours i have download the iso again. this time from the US.
burn on cd was no problem. perhaps my previous iso was not 100%.

but the cd into the U10 and type <boot cdrom>

yeah! stuff seems to work.
at this moment he is copy-ing the files.
it says: unpacking base system. 48%

just take a cup of coffee (with beans ofcourse) and wait....

more later!!!

byebye

Jean-Paul[/QUOTE]


back again!

installation is done!!

system is running... :-)

almost no problems.
only....

1.
when booting the machine, it says:
[    9.080109] rtc_init: no PC rtc found                                      [ok]

i dont know if this can harm the system....

2.
i dont have an option to install "lamp" on the system, so i have to install apache2, mysql, php etc manually.
if i install on a i386, then i can select a lamp installation, there is all in it.

3. 
keyboard layout doenst match the keyboard. no it is a american english layout, but it is an originally sun keyboard...

that's all.
i guess nothing very important stuff. point 2. could make live more easy... :-)


Jean-Paul

---

### Post by chris_andrew on 2006-07-06
Jean-Paul,

Can you post the link that you down loaded your ISO from, in the US?

I will try this one.

Cheers,

Chris.

---

### Post by jpgeerets on 2006-07-06
[QUOTE=chris_andrew]Jean-Paul,

Can you post the link that you down loaded your ISO from, in the US?

I will try this one.

Cheers,

Chris.[/QUOTE]


hi chris,

i used this link:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

there i select the SPARC server install CD to download the iso.

im curius to your experience...

Jean-Paul

---

### Post by netztier on 2006-07-06
[QUOTE=jpgeerets]
3. 
keyboard layout doenst match the keyboard. no it is a american english layout, but it is an originally sun keyboard...
[/QUOTE]

Select a standard US-layout 104/105key ***PC Keyboard***. Yes,  PC Keyboard. ***NOT*** Sun Type 4 or Type 5. Strange enough, I know, but it works.

See: [http://www.ubuntuforums.org/showthread.php?t=148356&highlight=sparc+keyboard]("http://www.ubuntuforums.org/showthread.php?t=148356&highlight=sparc+keyboard")

kind regards

Marc

---

### Post by chris_andrew on 2006-07-06
Jean-Paul,

I was going to suggest filing a bug for the keyboard mapping.  Maybe that is in hand.  I will probably have to use that mapping, too.  If my new download works (thanks for the link), I require my Type 5 keyboard to be UK English layout.

Will let you know how the new ISO goes./

Cheers, all.

Chris.

---

### Post by chris_andrew on 2006-07-06
Hmmm,

Still the same problem.  Jean-Paul, when you booted the CDROM, did you do anything special?  

Downloading the Alternate-Install image, to try.

Thanks,

Chris.

---

### Post by jpgeerets on 2006-07-06
[QUOTE=chris_andrew]Hmmm,

Still the same problem.  Jean-Paul, when you booted the CDROM, did you do anything special?

Thanks,

Chris.[/QUOTE]

hi chris,

nop, nothing special.
during systemboot i press <stop><a>.
the i get the OBP prompt.
there i typed: boot cdrom <enter>.

the system is going to find the cdrom and start boot/install.

do you have the same OBP version?

Jean-Paul

---

### Post by jpgeerets on 2006-07-06
question moved

---

### Post by jpgeerets on 2006-07-06
question moved to new topic

---

### Post by jpgeerets on 2006-07-06
[QUOTE=chris_andrew]Jean-Paul,

I was going to suggest filing a bug for the keyboard mapping.  Maybe that is in hand.  I will probably have to use that mapping, too.  If my new download works (thanks for the link), I require my Type 5 keyboard to be UK English layout.

Will let you know how the new ISO goes./

Cheers, all.

Chris.[/QUOTE]


how do i know what kind of keyb i have? i read something like type 4, type 5, type 6.....
it is a qwerty layout, but some keys have other symbols....:-k 

thanks!

Jean-Paul

---

### Post by jpgeerets on 2006-07-06
[QUOTE=chris_andrew]Jean-Paul,

Have you tried to do an installation?

I have filed the following bug-report.

I would appreciate it if you could add comments, should you want to.

[https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236](https://launchpad.net/distros/ubuntu/+source/silo/+bug/50236)

Thanks,

Chris.[/QUOTE]

chris,

can i help you with this?
do i need to report something?
i guess the system now works....
if needed, i will try to help

Jean-Paul

---

### Post by chris_andrew on 2006-07-06
Jean-Paul,

You can do a LAMP install by selecting "Lamp-server" at the boot prompt (as mentioned in LAMP thread).

Can you please create new threads for your new questions.

In relation to the original thread, my OBP version is 3.31.0

Thanks,

Chris.

---

### Post by recupero on 2006-07-06
I had no problem installing Ubuntu-Server on Ultra10.
But I found it still doesn't work with the Desktop version.
But one could start with the Server version, then by installing packets obtain something that's really close to the Desktop version. 
I haven't been successful in that, maybe because I know little about xorg.config for the ATI-Rage.
Has anyone tried that?
A lot of applications nowadays lack a server counterpart, so why not have a desktop install instead?
What's the energy breakdown desktop/server normally?

---

### Post by netztier on 2006-07-07
> **jpgeerets said:**
> how do i know what kind of keyb i have? i read something like type 4, type 5, type 6.....
it is a qwerty layout, but some keys have other symbols....:-k 


Maybe this [Wikipedia article on keyboard layouts ]("http://en.wikipedia.org/wiki/Keyboard_layout") will help determine what layout your keyboard has.

In most cases you'll have a [[COLOR="Blue"]Sun Type 5[/COLOR]]("http://images.google.com/images?q=Sun+Type+5+keyboard&hl=de&btnG=Bilder-Suche") or [[COLOR="Blue"]Sun Type 6[/COLOR]]("http://images.google.com/images?q=Sun+Type+6+keyboard&hl=de&btnG=Bilder-Suche") keyboard. 

Again: use a pc104/105 keymap that best matches your keyboard's language version, don't select "Sun" and "Type4/5" for it, it will garble your inputs badly. Been there, done that...

---

### Post by allnameswereout on 2006-07-07
I had this problem with layout too. The Sun type 4 i used worked fine on Linux 2.4.x, but not on a Linux 2.6 kernel (2.6.8.1). This was one Debian.

---

### Post by pvz on 2006-07-12
It's working fine on my Ultra 10. After the server-install I did a "apt-get install kubuntu-desktop" and now it has a shiney new KDE.

---

### Post by jpgeerets on 2006-07-13
hi folks,

finaly im back. was a little to busy at work... :-)

i have tryed to install xubuntu-desktop on ubuntu server, but now system doesnt work anymore...:cool: 
no problem, i will format it again and try and try and try...
when the server is booting, i can follow the boot, until it switch to graphic mode....
perhaps i choose the wrong video driver...?
dont know yet.....

---

### Post by pvz on 2006-07-13
> **jpgeerets said:**
> 
when the server is booting, i can follow the boot, until it switch to graphic mode....
perhaps i choose the wrong video driver...?
dont know yet.....

What graphic card do you have? What is the output of lspci?
My Ultra 10 has a Ati Technologies Inc 3D Rage Pro 215GP (rev 5c)
During xorg setup I just had to confirm the selected ati driver, and X was automagically configured.

Ultra 10, OB 3.25, 440MHZ

---

### Post by chris_andrew on 2006-07-18
Could it be that I am using an old hdd, and this is causing problems?

Cheers,

Chris.

---

### Post by gavinj44 on 2006-07-22
Hi Chris,

Are you stull having issues with your Ultra 10 ?

With all the issues i was having with the installer and SILO bit being able to write to the disk I was just about to give up.

Then i decided to try downloading the iso again and burning a fresh CD, this was once the link appeared on the download Ubuntu server page for the sparc platform.

I decided to burn this at single speed as I have had issues before with burning linux distro CD's.

Went through the installer with the new CD and all installed well and it is all up and running now ... just waiting for the seti enhanced binaries for boinc to become available now ;)

Let me know how it is going for you now.

Regards,
Gavin

---

### Post by chris_andrew on 2006-07-22
Gavin,

Thanks for your kind message.  I have all but given up.  Believe it or not, moments before reading your message, I just ordered a new HDD for the Ultra, to eliminate that possibility (I can use it elsewhere, too).  

I will have to see if I have a PC lying around that can burn at 1x...that is not possible on my usual drive.

I will give this a go and let you know what happens.

BTW, I didn't think BOINC ran on Sparc, I have been trying to find such a package.

Cheers,

Chris.

---

### Post by gavinj44 on 2006-07-24
BOINC runs, well I run it command line, but the binaries for SETI Enhanced haven't been compiled yet for linux on sparc.

But BOINC runs and I have attached it to the SETI project, it just can't get any work :(

I have posted here:

[http://setiweb.ssl.berkeley.edu/forum_forum.php?id=13](http://setiweb.ssl.berkeley.edu/forum_forum.php?id=13)

I hope you manage to get it working.

Regards,
Gavin

---

### Post by chris_andrew on 2006-07-25
Thanks, Gavin.

Chris.

---

### Post by chris_andrew on 2006-07-28
Well, still the same old problem, can't get past "Booting linux...", even after HDD and CDROM upgrade :-(

---

### Post by jpgeerets on 2006-07-29
perhaps your videocard?
guess?

---

### Post by chris_andrew on 2006-07-29
Good guess, but other versions of linux work, that use the 2.4 kernel, and it's before it gets to X mode.

Thanks,

Chris.

---

### Post by recupero on 2006-07-29
Chris, what processor you have?
With 330MHz I do the entire install, with 440MHz which I was able to get working only thanks to a forum-partially-aided (give all the details please!) OBP-upgrade, [SIZE="5"]It is stuck [/SIZE]at 
Booting Linux...
:confused:

---

### Post by chris_andrew on 2006-07-29
I don't have a problem with the OBP.  It is just that when I try to install Ubuntu or Debian Etch, the install fails at "Booting Linux...."

---

### Post by recupero on 2006-07-29
Sorry, it was not the processor.
It's the video-card.
With the built-in ATI both processor go through the Booting Linux
with Elite, they stop

---

### Post by hakankarakas on 2006-08-15
I also tried to install ubuntu on a Sun Ultra 10. 

It boots from the CD however, After I got the following messages and return back to OBP.

Loaded kernel version 2.6.15
Loading initial ramdisk(.....
Illegal Instruction
ok

My OBP version is 3.25

Any clue what is going on?

Thanks

---

### Post by fajensen on 2006-08-23
I got one right here - it worked straight out of the cdrom boot too (with the niglet that the installer whined about LILO could not be installed - said <continue anyway> and it did). I ran /etc/sbin/silo off the command line just to be sure!

Sound does not work - haven't found out why yet, maybe the cufty old kernel?

---

### Post by fajensen on 2006-08-23
Forgot to say this:

Having been burned once-too-many times on Debian screwing dependencies up and only installing half of the X windows system, this time I did it right and installed first the Ubuntu-sparc "server-edition" then Xorg and finally Fluxbox on top of that. 

I.M.O. One should *always* do the server/minimum install, then slap the desktop and other apps over that for maximum reliability and the least grief. 

Without GNOME/KDE to leach all ressources ye olde box runs very smooth :biggrin: 

FWIW: Xorg still takes 13% of the 256K RAM and 2-5% of the 440 MHz CPU.

---

### Post by chris_andrew on 2006-08-23
Recupero,

Your findings are interesting.  Please can you add this comment to the following bug:

[https://launchpad.net/bugs/50236](https://launchpad.net/bugs/50236)

Perhaps this could be the break that we need.

Cheers,

Chris.

---

### Post by netced on 2006-08-26
Hi @ all, I have my Ultra 5 (440Mhz, 512Mo, SCSI drives) under Debian Sarge at the moment, I'm pretty happy with it (that's impressive to see that old system running so well, even on KDE :D ). But I did not find a way to make sound work (worse : the system hangs if I try, this doesn't help to make many tests...) and to print from parallel port (it seems that this port is not known at all). It's a problem for me since I would like to turn the system to a print server. So here are my questions:

Using Ubuntu on U5/10:
1. Do you have any sound ?
2. Does the parallel port work ?
3. Did you succed to put a USB PCI-card ?

---

### Post by netztier on 2006-08-27
> **netced said:**
> Using Ubuntu on U5/10:
1. Do you have any sound ?

Yes: See also this post: [http://www.ubuntuforums.org/showpost.php?p=988772&postcount=9]("http://www.ubuntuforums.org/showpost.php?p=988772&postcount=9")

Spelling in that post seems inconsistent; the kernel module's path is [FONT="Courier New"]**/lib/modules/<kernel-version>/kernel/sound/sparc/[B]snd-sun-cs4231**.ko[/B][/FONT], and with this filename spelling (with dashes) is how I appended it to /etc/modules. 

Yet, in lsmod, it appears as **snd_sun_cs4231** (with underscores).

This U5 runs Ubuntu (with GNOME), and all the sound deamons etc didn't need any further configuration. "Just runs", as we know it from Ubuntu :-).

> **netced said:**
> 2. Does the parallel port work ?
3. Did you succed to put a USB PCI-card ?

Can't tell for I haven't tried.

Kind regards

Marc

---

### Post by hts on 2006-08-27
> **netced said:**
> 1. Do you have any sound ?
2. Does the parallel port work ?
3. Did you succed to put a USB PCI-card ?

I managed to get sound on my ultra 10. I found a page on ultralinux.org that listed the sound cards of the different sparc machines. Then I went to alsa-project.org to look up the right drivers. I think I just had to add 'soundcore' and 'snd-sun-cs4231' to /etc/modules, and that brought up the entire sound system.

And yes, I did install a USB PCI card. It worked out of the box—I can't tell you much more.

I don't know about the parallel port—I've never tried it.

I hope this helps you some.

---

### Post by mips on 2006-08-28
> **hts said:**
> 
And yes, I did install a USB PCI card. It worked out of the box—I can't tell you much more.


It will probably help others if you could share what card you are using.

---

### Post by netced on 2006-08-28
Thank you for your answers :) HTS, I'm interested to know which USB card you have too !
---

So I tried Ubuntu on my U5 (440MHz, 512MB, OBP 3.29) and it worked... Up to the moment I tried to install  desktop. Intalling and trying to run either xubuntu-desktop or kubuntu-desktop on a fresh install leads to a hard-freeze :( The problem happened to at least two people:[http://ubuntuforums.org/showthread.php?t=227278]("http://ubuntuforums.org/showthread.php?t=227278")

The video shipset is a "Rage pro turbo pci" and the lspci command returns "3D Rage Pro 215GP (rev 5c)", the motherboard is a 375-0115 (it's written on a stick on the brown port behind the PCI port). Can  anyone having the same chip and a working X server can show me his /etc/X11/xorg.conf file ? Thank you !

---

### Post by hts on 2006-08-29
> **netced said:**
> Thank you for your answers :) HTS, I'm interested to know which USB card you have too !

I'm afraid I don't have the box anymore, and I don't remember the brand name. But it is a 5-port USB 2.0 interface, with one port inside the case. It was brand new.

lspci says:
--------
0000:02:01.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 8, IRQ 7616128
        Memory at 000001ff00002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:02:01.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 8, IRQ 7616160
        Memory at 000001ff00004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:02:01.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: HaSoTec GmbH: Unknown device 2928
        Flags: bus master, medium devsel, latency 68, IRQ 7616192
        Memory at 000001ff00006000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2
-------

Does your ultra 5 have two video cards? My 10 does: it has an ATI 3D Rage Pro 215GP, and a sun 'ffb', which is VGA, but uses a proprietary connector. I was lucky enough to find an adaptor to connect a normal monitor to it. Debconf wanted to use my ATI by default, and I had to tell it to use 'sunffb', and enter the SBUS address, which I got from the 'show-devs' command on OBP.

The ffb vga port is similar to a parallel port, but has three strange-looking coaxial pins.

Edit:
It's a rip-off, but here's a place you can find the adaptor:
[http://www.kvm-switches-online.com/13w3m-15hdf.html](http://www.kvm-switches-online.com/13w3m-15hdf.html)

---

### Post by pvz on 2006-08-30
> **netced said:**
> 
Using Ubuntu on U5/10:
1. Do you have any sound ?
2. Does the parallel port work ?
3. Did you succed to put a USB PCI-card ?

Sound works on my Ultra 5 running Debian Sarge after upgrading to a  recent kernel, which has the right drivers

Look at 
[http://www.sun.com/io_technologies/PCI.html](http://www.sun.com/io_technologies/PCI.html)
for compatible cards, but the basic thing is to look at the chipset. VIA (most cards) doesn't work, you need the NEC chipset. I have a Belkin that is listed on the mentioned page and it runs fine, with a Nec chipset indeed.

---

### Post by allnameswereout on 2006-08-31
> **pvz said:**
> Sound works on my Ultra 5 running Debian Sarge after upgrading to a  recent kernel, which has the right drivers

Look at 
[http://www.sun.com/io_technologies/PCI.html](http://www.sun.com/io_technologies/PCI.html)
for compatible cards, but the basic thing is to look at the chipset. VIA (most cards) doesn't work, you need the NEC chipset. I have a Belkin that is listed on the mentioned page and it runs fine, with a Nec chipset indeed.

That list is not complete for all hardware btw. I am using different NICs as listed there and they work fine on BSD/Linux.

You can also have a look at /lib/modules/`uname -r`/kernel/drivers

15V <-> 13W3 converters can also be found on eBay for about 10 EUR (still expensive but whatever) or you could get a 13W3 monitor also avail second hand.

---

### Post by cruger28 on 2007-01-09
Hi,

I'd successfully installed ubuntu sparc on Ultra 10..Unfortunately, its goes to the command line. How to start Xwindows (in other word, gnome). 

I noticed that in my etc/X11, only have 
rgb.txt      Xresources      Xsession.d      Xwrapper.config
xkb          Xsession          Xsession.options

Anybody out there can help me ??

---

### Post by netztier on 2007-01-09
> **cruger28 said:**
> Hi,

I'd successfully installed ubuntu sparc on Ultra 10..Unfortunately, its goes to the command line. How to start Xwindows (in other word, gnome). 

I noticed that in my etc/X11, only have 
rgb.txt      Xresources      Xsession.d      Xwrapper.config
xkb          Xsession          Xsession.options

Anybody out there can help me ??

Ubuntu for SPARC is server-oriented, and therefore comes without desktop environment. You'll have to install one of the packages **ubuntu-desktop**, **kubuntu-desktop**, or **xubuntu-desktop**.

A bit of forum research could also have helped...

best regards

Marc

---

### Post by JungleG on 2007-01-18
I imagine you figured this out from the previous post but I also have Ubuntu installed on by Ultra 10 and I ran 

# sudo apt-get install ubuntu-desktop

after about 35 minutes, I rebooted and viola Gnome Desktop 

C ya

---

### Post by whitebunnyflock on 2007-01-19
a little off-topic but what windows manager does xubuntu-desktop come with?

i will be installing Ubuntu on my U5 shortly so now thanks to you guys I will have a working knowledge of how its done!

---

### Post by mips on 2007-01-19
> **whitebunnyflock said:**
> a little off-topic but what windows manager does xubuntu-desktop come with?


**[XFCE]("http://www.xfce.org/")** 

If you want something even lighter try Fluxbox, I tend to like it after kde.

Or maybe one of these tickles your fancy, [http://xwinman.org/](http://xwinman.org/)

---

### Post by jplegat on 2007-01-23
Just to let you know that I sucessfully installed Ubuntu 6.10 on a Ultra 10 station a few minutes ago :-D . Installation is really smooth. Congratulations to the Ubuntu SPARC Team \\:D/ .

Linux ubuntu-sparc 2.6.17-10-sparc64 #2 Fri Oct 13 17:04:28 UTC 2006 sparc64 GNU/Linux

cpu             : TI UltraSparc IIi (Sabre)
fpu             : UltraSparc IIi integrated FPU
prom            : OBP 3.25.1 2000/01/14 13:40
type            : sun4u
ncpus probed    : 1
ncpus active    : 1
D$ parity tl1   : 0
I$ parity tl1   : 0
Cpu0Bogo        : 880.38
Cpu0ClkTck      : 000000001a39de00
MMU Type        : Spitfire

---

### Post by netztier on 2007-01-23
> **jplegat said:**
> Just to let you know that I sucessfully installed Ubuntu 6.10 on a Ultra 10 station a few minutes ago :-D . Installation is really smooth. Congratulations to the Ubuntu SPARC Team \\:D/ .


Great :-).

Does your installation include a desktop environment, too? What framebuffer/graphics card does your system have, and did you manage to get X.org running? I am asking this since this tends to be a more problematic area, and any additional information about success or failure can help when reported to the developpers. 

Known problems are

[LIST]
[*]ATI chipsets not working properly, X.org driver not handling PCI ressources properly (fixed in Debian, but not in Ubuntu)
[*]OpenGL emulation with Mesa crashes X.org
[*]some framebuffers/video chipset not supported (most XVR versions) and some PGX cards
[/LIST]

best regards 

Marc

---

### Post by jplegat on 2007-01-24
Hello, netztier. I´m sorry, I forgot to mention in the previous post that I made a server install, I didn´t try to install the desktop environment.

---

### Post by Moulton on 2007-02-03
On the 64-bit Sparc, the Desktop can be installed, but the X.Org drivers are only known to work with the UPA Creator or ATI graphics adaptors.  The drivers for the S-Bus graphic adaptors are uniformly reported not to work in the 64-bit Sparc distro.

Even if you cannot run a console X-Server (for lack of a supported graphic adaptor), you can still use XDMCP to connect remotely from another X-Server on your LAN, and you can get the Desktop that way.  If you do that, be sure to disable the animated screensaver, as the animations will flood your LAN.

Note also that web browsers and their plugins are somewhat limited in the 64-bit Sparc platform.  I found that Firefox and Epiphany locked up, but Opera worked.  A lot of multiimedia plugins don't exist for the Sparc platform.

---

### Post by jpgeerets on 2007-02-03
hi folks,
at this moment my ultra10 works great. 
but only with clui.

for some less technical people i would like it when there should be a simple gui on.
i have only the internal, onboard, videocard in.
i have installed ubuntu-desktop. this doenst work. i get no gui.
during boot system hungs.
only way was <stop><a> and boot cdrom... :-)
after that a new install.
now is this a experimental machine, so thats no problem....

but, still i want to use a (simple/light) gui on the machine....

---

### Post by mips on 2007-02-03
Why not start by installing just X. If that all goes well or you get it to work fine add Fluxbox window manager or something you like.

---

### Post by jpgeerets on 2007-02-03
what part of X is needed in this case?
just: sudo apt-get install X
?
something else?
does that works on a ultra10?
can i also use a program lyke cygwin (on windows) to make a desktop connection?

tia

Jean-Paul

---

### Post by Moulton on 2007-02-04
The lightest fully supported desktop environment is the XFCE Desktop used in the Xubuntu distribution.

There is a meta-package that should install everything you need for Xubuntu Desktop:
```
apt-get install xubuntu-desktop
```
Until you have a working GUI desktop, you have to do everything at the command line interface.  There is a text-based package browser called 'aptitude' that is functionally equivalent to Synaptic, but (being curses-based) is somewhat harder to use.  If you don't already know exactly which packages you want to obtain, you can browse the package repositories with 'aptitude' until you have your GUI up and running.

If you are lucky, the X.Org video drivers that are installed will work properly with your onboard graphics adaptor.  In the 64-bit Linux Sparc distros there are some graphic adaptors for which the X.Org drivers don't work properly.  As far as I know, the Sparc 32-bit architecture doesn't have this problem.

If X tries to start and either displays an error message or leaves you with a blank screen, use the Alt-Ctl-F1 key to get back to your VT console.  Debugging X.Org drivers and settings is often tricky.  If you get to that point, expect to spend days diagnosing and solving it.

---

### Post by mips on 2007-02-04
> **jpgeerets said:**
> what part of X is needed in this case?
just: sudo apt-get install X
?


I started copying and pasting stuff for you but realised it would be easier for you to follow this:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Consider each link a step:
[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-f1a950ab8ea49c237934dc8ba823e53e6f23b965](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-f1a950ab8ea49c237934dc8ba823e53e6f23b965)
[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-15ecc03527a9f9cc25a419ee3930da40cf12cc99](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-15ecc03527a9f9cc25a419ee3930da40cf12cc99)
[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-56f5663adabcf5cb466de390ac754d444a05b0a4](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-56f5663adabcf5cb466de390ac754d444a05b0a4)
rox-filer
[https://help.ubuntu.com/community/Installation/LowMemorySystems#head-99ac37a8dabf2f7a68a6e27a04ffe131f037e034](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-99ac37a8dabf2f7a68a6e27a04ffe131f037e034)

There are other things you could add: Search for fluxbox threads or look at 
[http://fluxbuntu.org/](http://fluxbuntu.org/)  or   [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)   or  [http://techbycolin.com/?p=88](http://techbycolin.com/?p=88)

---

### Post by jpgeerets on 2007-02-05
@Moulton:

i have tryed to do:
apt-get install xubuntu-desktop

install was ok.
during install i could select what resolution i want to use.
i just left it at default.

when i had done a reboot, the system hungs.

keyboard did not work anymore, so also <ctrl><alt><F1> doenst work.
also ssh doesnt work anymore.

i guess the only thing i can do is a new install of cdrom....:confused: 

any idea?

---

### Post by mips on 2007-02-05
Like I said, do a server install first and then X. You need to get it working up to this point before you can carry on.

---

### Post by jpgeerets on 2007-02-05
sorry...
you r right...

so, i start to do so.

i followd the first link.

item: startx
all before went well.
when i give the command 
 startx
the system came with an error:

---
Fatal server error:
xf86MapPciMem: Could not mmap PCI memory [base=0xe2000000,hostbase=0xe2000000,size=2000] (Inappropriate ioctl for device)

(WW) Attempt to disable VGA routing through Simba at 0:1:0 disallowed.
---
is this because there is no window manager on the system at this moment?
can i go on?

Jean-Paul

---

### Post by mips on 2007-02-05
> **jpgeerets said:**
> sorry...
you r right...

so, i start to do so.

i followd the first link.

item: startx
all before went well.
when i give the command 
 startx
the system came with an error:

---
Fatal server error:
xf86MapPciMem: Could not mmap PCI memory [base=0xe2000000,hostbase=0xe2000000,size=2000] (Inappropriate ioctl for device)

(WW) Attempt to disable VGA routing through Simba at 0:1:0 disallowed.
---
is this because there is no window manager on the system at this moment?
can i go on?

Jean-Paul

startx should load the X-window environment for you. Do you get anything or does it leave you at the command prompt ? I suspect you only have command prompt ?

I will look up the error and get back to you a bit later.

---

### Post by jpgeerets on 2007-02-05
when i typed  startx, the screen becomes blanc fora few seconds.
then i get the commandline back.
perhaps this is usefull information for you.

---

### Post by Moulton on 2007-02-05
What graphic adaptor do you have?  

Keep in mind that X.Org drivers may not exist (or work) for some Sun graphic adaptors in the 64-bit environment.

---

### Post by jpgeerets on 2007-02-06
well, its the onboard vga-adapter.

where can i see what exact type this is?

Jean-Paul

---

### Post by mips on 2007-02-06
> **jpgeerets said:**
> well, its the onboard vga-adapter.

where can i see what exact type this is?

Jean-Paul

Do you have any other adapters installed maybe that you are not using ?

The onboard one should work as it does for others. It's a ATI Rage Pro I think.

---

### Post by jpgeerets on 2007-02-06
the onboard is an ATI card. i dont know which one....

this is the only graphics card in this machine.

Jean-Paul

---

### Post by Moulton on 2007-02-06
There are several things that all have to work before you can start X and bring up the GUI.

First (and this goes without saying) you must have the requisite X.Org packages installed and configured for your hardware.

You also need to be using a monitor that mates with the graphic adaptor, in terms of synch rate, resolution, and frame refresh rate.  And then your X.Org settings have to select a combination that is supported by both the graphic adaptor and the monitor.

Because there are so many possible combinations, it is easy to intially set up X.Org with settings that don't work with your hardware.

In /var/log there should be logs associated with starting X on the console.  Those logs are a bit intimidating for a beginner, but buried in all that chaff you can often find a reliable clue to where the problem lies.

---

### Post by KBelosludtsev on 2007-04-02
Hello Friends,

I managed to get X desktop on my Ultra 10. 
If you have Elite 3D graphics card, all your efforts are useless until you install Debian package "afbinit". This will upload microcode to your graphics card.

Good luck!

---

### Post by timothyjones on 2007-04-16
For whatever it's worth... I have just installed Ubuntu 7.04 on a Sparc Ultra 5 with OBP 3.15.

Just another data point, and another happy user!


Timothy Jones
[http://timjones.com](http://timjones.com)
[http://linuxtampa.com](http://linuxtampa.com)

---

### Post by capt_caveman on 2007-04-23
If you see the :
[INDENT]xf86MapPciMem: Could not mmap PCI memory
Inappropiate ioctl for device[/INDENT]
error, then there  is some workaround required for the X server for 6.10 -- see the following for some details [http://www.skynet.ie/~ivan/install_ubuntu_on_ultra10.html#Running%20X%20on%20a%20Creator3D%20card](http://www.skynet.ie/~ivan/install_ubuntu_on_ultra10.html#Running%20X%20on%20a%20Creator3D%20card)

Alternatively, try 7.04 - perhaps they have fixed the issue now.

---

### Post by tolkan on 2007-05-23
Hey there,

I just obtained an Ultra Sparc 10 and trying to install ubuntu-server 7.04 on it.  After reading the threads started in the fourm, i think i may know what the issue is with the freezing.

When installing Gentoo, The live disc instructs the user to force the video framebuffer to off.  The only way i can get the Linux to react when i start booting is to type at the boot: prompt

2620 video=atyfb:off 

This tells the cd to boot kernel 2.6.20 and passes to the atyfb (ATi Framebuffer) to turn off.  This is the only way i can get Gentoo Live to boot.

Perhaps the difference in the people who are installing Ubuntu on the Sparcs, regardless of the OBP version or the sparc machine no, is the video device itself.  The people who get Ubuntu to hang at "Booting Linux..." (me) are using ATi chips.

Does anyone know if there is a way to pass this video=atyfb:off parameter in ubuntu's Live CD Boot: prompt?  I think we'd just need to know the name of the kernel to boot.

Any help would be appreciated...

UltraSparc 10, OBP 3.25

-Mike

---

### Post by capt_caveman on 2008-03-27
That should be video=atyfb:off

The :o was turning into a smilie in the earlier posts...

---

### Post by pks_loss on 2008-04-04
For me, my install was as simple as this for ubuntu 7.10: even though I have an old Openboot version.

Start up the Machine:
Insert the Ubuntu 7.10 cdrom in the disk drive.
Send a Break:
when you get to the prompt that says ok> type this
```
setenv boot-device cdrom disk net
```
reboot the machine. 

  It should install all good after that. No updating OpenBoot, or anything. 


 Hope it helps,

    -- PK

---


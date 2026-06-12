---
title: "Trusty to get a beta version of Grub."
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-01-17
We need the proposed repository enabled and we get Grub 2.02~beta2-2 instead of Grub 2.00-22. I do not know of any benefits but at least it did not break the boot.

[http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts?utm_source=rss&utm_medium=rss&utm_campaign=grub-2-beta-ubuntu-14-04-lts](http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts?utm_source=rss&utm_medium=rss&utm_campaign=grub-2-beta-ubuntu-14-04-lts)

[https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html)

> Please ensure that you have rescue media to hand before starting testing.  The simplest way to upgrade is to enable trusty-proposed, upgrade ONLY packages whose names start with "grub" (e.g. use "apt-get dist-upgrade" to show the full list, say no to the upgrade, and then pass all the relevant package names to "apt-get install"), and then (very important!) disable trusty-proposed again.  Provided that there were no errors in this process, you should be safe to reboot.  If there were errors, you should be able to downgrade back to 2.00-22 (or 1.27+2.00-22 in the case of grub-efi-amd64-signed).
Regards.

---

### Post by The Cog on 2014-01-17
Successful boot here on proposed grub 2.0b2. AMD64, sataII disk with msdos partition table and Xubuntu on logical partition.

But:
The font on my desktop icons has changed. Is that possible, even? 
Maybe it was another recent update that changed the background behind the icon font change and I didn't notice before. Hmm...

One thing is that I chose to keep my modified /etc/default/grub because it had this line added:
GRUB_GFXPAYLOAD_LINUX=1920x1200
Now I'm wondering if I missed any important change in that file.

---

### Post by Elfy on 2014-01-17
> The font on my desktop icons has changed. Is that possible, even?
Maybe it was another recent update that changed the background behind the icon font change and I didn't notice before. Hmm...~If you happen to have any of the xubuntu team ppa's enabled - there is a bit of flux going on at the moment :)

---

### Post by The Cog on 2014-01-17
> **Elfy said:**
> ~If you happen to have any of the xubuntu team ppa's enabled - there is a bit of flux going on at the moment :)
No special PPAs enabled, mate. 

Maybe I'm just not being very observant. If nobody else has noticed anything similar then I'm inclined to let it pass as a problem with the nut on the chair at this end.

---

### Post by ventrical on 2014-01-17
I used synaptic. Worked just fine. No font change. Only difference I noticed was an '*' preceeding the entries in the GRuB menu.

I wonder if this will prevent Windows 8 bootloader from overwriting GRuB during an install and not having to use GRuB Rescueto get back a previously installed ubuntu partition?

Regards..

---

### Post by Elfy on 2014-01-17
well ... that went horribly wrong, ended up in rescue mode and then busybox

installed fine

commented in bug

> No special PPAs enabled, mate. I sent gremlin out earlier for a walk - perhaps she found you :p

---

### Post by mc4man on 2014-01-17
> The simplest way to upgrade is to enable trusty-proposed, upgrade ONLY packages whose names start with "grub" (e.g. use "apt-get dist-upgrade" to show the full list, say no to the upgrade, and then pass all the relevant package names to "apt-get install"), and then (very important!) disable trusty-proposed again. Provided that there were no errors in this process, you should be safe to reboot. If there were errors, you should be able to downgrade back to 2.00-22 (or 1.27+2.00-22 in the case of grub-efi-amd64-signed). 
Seems a bit convoluted to me, I simply go 
```
 sudo apt-get -s  install --only-upgrade grub*
```

If it checks out then remove the -s & do for real

---

### Post by ventrical on 2014-01-17
> **mc4man said:**
> Seems a bit convoluted to me, I simply go 
```
 sudo apt-get -s  install --only-upgrade grub*
```

If it checks out then remove the -s & do for real

Is there a 

```


sudo apt-get install --only-downgrade grub*


```


?

regards..

---

### Post by mc4man on 2014-01-17
> **ventrical said:**
> Is there a 

```


sudo apt-get install --only-downgrade grub*


```


?

regards..

no

---

### Post by ventrical on 2014-01-18
> **mc4man said:**
> no

@mc4man

what would be a reasonable equivalent. I used synaptic and it worked well but your method seems more economically designed and I am just curious as to what  code in terminal could be used  to downgrade .etc..

---

### Post by zika on 2014-01-18
> **ventrical said:**
> @mc4man

what would be a reasonable equivalent. I used synaptic and it worked well but your method seems more economically designed and I am just curious as to what  code in terminal could be used  to downgrade .etc..&#8222;No&#8220; was the answer to proposed command as that switch does not exist. Downgrading is possible, of course in many ways, and is, also, very easy... Once You have a plan and know what You want. Command dependes only on Your needs and wishes...

---

### Post by grahammechanical on 2014-01-18
A little more information from Colin Watson's blog on this Grub 2.02 version and his motivation.

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2014/01/18#2014-01-18-testing-wanted-grub-2.02-beta2](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2014/01/18#2014-01-18-testing-wanted-grub-2.02-beta2)

Regards.

---

### Post by ventrical on 2014-01-20
> **zika said:**
> „No“ was the answer to proposed command as that switch does not exist. Downgrading is possible, of course in many ways, and is, also, very easy... Once You have a plan and know what You want. Command dependes only on Your needs and wishes...

I'll |  use |  synaptic.

thnx

---

### Post by Cavsfan on 2014-01-21
> **The Cog said:**
> Successful boot here on proposed grub 2.0b2. AMD64, sataII disk with msdos partition table and Xubuntu on logical partition.

But:
The font on my desktop icons has changed. Is that possible, even? 
Maybe it was another recent update that changed the background behind the icon font change and I didn't notice before. Hmm...

One thing is that I chose to keep my modified /etc/default/grub because it had this line added:
GRUB_GFXPAYLOAD_LINUX=1920x1200
Now I'm wondering if I missed any important change in that file.

I just installed it via mc4man's way although it looked like it picked the i386 files instead of AMD64 files.
```
sudo apt-get -s  install --only-upgrade grub*
```
I took the newer version of **/etc/default/grub**: if you are interested here is the original new file.
I will just set this up GRUB_GFXMODE=1920x1200-24
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Now let's see how well it likes being customized.

---

### Post by Cavsfan on 2014-01-21
Made a few changes to **/etc/default/grub** rebooted and the only change I saw was a asterisk beside the selection.

I did notice that **grub-install -v** no longer works to provide the version number:

```
cavsfan@cavsfan-MS-7529:~$ grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.

```

**grub-install -V** (capital V) provides the version now.

I also noticed that grub-pc-bin only comes in i386 and not 64 bit at the present.

---

### Post by Cavsfan on 2014-01-22
> **grahammechanical said:**
> We need the proposed repository enabled and we get Grub 2.02~beta2-2 instead of Grub 2.00-22. I do not know of any benefits but at least it did not break the boot.

[http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts?utm_source=rss&utm_medium=rss&utm_campaign=grub-2-beta-ubuntu-14-04-lts](http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts?utm_source=rss&utm_medium=rss&utm_campaign=grub-2-beta-ubuntu-14-04-lts)

[https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html)


Regards.

The bug mentioned in that 2nd link pulls in the period and therefore goes no where.
Here is the bug, which I subscribed to: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1269992](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1269992)

---

### Post by QDR06VV9 on 2014-01-28
```
grub-probe -V 
grub-probe (GRUB) 2.02~beta2-5
```
Grub gets upgraded in Todays Updates!
Was a little nervous because I have 6 partitions on just this machine.
All is Good!:D

---

### Post by Cavsfan on 2014-01-28
> **runrickus said:**
> ```
grub-probe -V 
grub-probe (GRUB) 2.02~beta2-5
```
Grub gets upgraded in Todays Updates!
Was a little nervous because I have 6 partitions on just this machine.
All is Good!:D

I got the update too, all went well and can I see in SPM that they are indeed in the regular updates.
Just curious about why it said it was building for i386-pc when I have amd64.

---

### Post by Cavsfan on 2014-01-28
A little bit of an update from Colin Watson.

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2014/01/18](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2014/01/18)

---

### Post by QDR06VV9 on 2014-01-28
> **Cavsfan said:**
> Just curious about why it said it was building for i386-pc when I have amd64.
Thats the part that had me a bit apprehensive:D
But I always have my handy boot-repair at the ready;)
Oh the link in your second post(from Colin Watson) was a good read.

---

### Post by zika on 2014-01-29
Any news about Grub 2.02-beta in SS?

---

### Post by Cavsfan on 2014-01-30
I take it everyone got the new update today.

```
cavsfan@cavsfan-MS-7529:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-6
```

While I did notice it pulled in all AMD64 packages I still seen this message displayed in the output:
 
[PHP]Installing for i386-pc platform.[/PHP]

```
grub2 (2.02~beta2-6) experimental; urgency=medium

  * Install bootinfo.txt and grub.chrp into grub-ieee1275-bin on powerpc and
    ppc64el.
  * Port yaboot logic to improve installation for various powerpc machine
    types.
  * Improve parsing of /etc/default/grub.d/*.cfg in C utilities
    (LP: #1273694).
  * Run grub-install on install or upgrade on grub-ieee1275/ppc64el.

 -- Colin Watson <cjwatson@debian.org>  Tue, 28 Jan 2014 23:50:55 +0000
```

---

### Post by craig10x on 2014-01-30
When i did my recent upgrade from 13.10 final into 14.04 development, you may recall i mentioned in another posting that each time i boot up, i get the GNU GRUB appearing on the screen for about 10 seconds before it continues to the sign in screen as normal....i had checked in the terminal and it is set to hide (but it doesn't for me)....i just happened to noticed that the grub i have apparently is this 2.02 beta version....and i did get the update for it today (still appears on my screen each time i boot up, though)...

My proposed is not activated in software sources...and yet when i upgraded...somehow i ended up with this testing grub...strange, right? :rolleyes:

---

### Post by Cavsfan on 2014-01-30
> **craig10x said:**
> When i did my recent upgrade from 13.10 final into 14.04 development, you may recall i mentioned in another posting that each time i boot up, i get the GNU GRUB appearing on the screen for about 10 seconds before it continues to the sign in screen as normal....i had checked in the terminal and it is set to hide (but it doesn't for me)....i just happened to noticed that the grub i have apparently is this 2.02 beta version....and i did get the update for it today (still appears on my screen each time i boot up, though)...

My proposed is not activated in software sources...and yet when i upgraded...somehow i ended up with this testing grub...strange, right? :rolleyes:

The beta Grub is in in the main repository and it will ship with Trusty Tahr14.04 LTS.

[http://ubuntuportal.com/2014/01/ubuntu-14-04-trusty-tahr-will-included-grub-2-02.html](http://ubuntuportal.com/2014/01/ubuntu-14-04-trusty-tahr-will-included-grub-2-02.html)

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy grub-pc
grub-pc:
  Installed: 2.02~beta2-6
  Candidate: 2.02~beta2-6
  Version table:
 *** 2.02~beta2-6 0
        500 http://mirrors.advancedhosters.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

Mine is customized from the wiki in my signature so I do not see anything different really. It seems faster is about the only thing I notice along with a asterisk beside the selected line.

---

### Post by craig10x on 2014-01-30
@Cavsfan: Oh, i see now...then i guess that makes sense as to why i have it by default...thanks :D

---

### Post by ventrical on 2014-01-30
Still works fine here.

```

ventrical@ventrical-desktop:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-6
ventrical@ventrical-desktop:~$ 

```

---

### Post by Cavsfan on 2014-01-30
> **craig10x said:**
> @Cavsfan: Oh, i see now...then i guess that makes sense as to why i have it by default...thanks :D

You are welcome! :D

> **ventrical said:**
> Still works fine here.

```

ventrical@ventrical-desktop:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-6
ventrical@ventrical-desktop:~$ 

```

Good deal! I'ts looking good to me too.

This is what I see (just one screen upon bootup):

[http://ubuntuforums.org/showthread.php?t=2076205&page=22&p=12915020#post12915020](http://ubuntuforums.org/showthread.php?t=2076205&page=22&p=12915020#post12915020)

---

### Post by zika on 2014-01-31
You see Windows7 as default...?
;)

---

### Post by grahammechanical on 2014-01-31
> [COLOR=#000000]My proposed is not activated in software sources...and yet when i upgraded...somehow i ended up with this testing grub...strange, right?[/COLOR]

Perhaps Grub 2.02 is now in the main repository but still being classed as beta until nearer 14.04 release day. I got Grub 2.02 by enabling the proposed repository. Then I disabled the proposed repository and yet Grub 2.02 has been upgraded four times through the usual update channels. I guess it means that Colin Watson is becoming more confident in the stability of Grub 2.02.

Regards.

---

### Post by Elfy on 2014-01-31
It got installed here a short while ago - proposed is disabled.

```
grub2-common:
  Installed: 2.02~beta2-6
  Candidate: 2.02~beta2-6
  Version table:
 *** 2.02~beta2-6 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Cavsfan on 2014-01-31
> **zika said:**
> You see Windows7 as default...?
;)

Indeed. That is in case my wife encounters a reboot. ;) Plus I like to keep my options open. There are things I cannot do in Ubuntu that I can in Windows; likewise there are things I cannot do in Windows but can in Ubuntu. Plus I like to play around with anything I can get my hands on.

---

### Post by Cavsfan on 2014-02-13
> **zika said:**
> You see Windows7 as default...?
;)

> **Cavsfan said:**
> Indeed. That is in case my wife encounters a reboot. ;) Plus I like to keep my options open. There are things I cannot do in Ubuntu that I can in Windows; likewise there are things I cannot do in Windows but can in Ubuntu. Plus I like to play around with anything I can get my hands on.

@zika, I forgot to mention that the custom grub menu idea's *entire purpose* was to make a **static** menu for those that dual boot or multi boot.
**Ranch hand** taught me many things about grub; one of them was how to do the custom grub. I asked him if he minded if I made it into a How To. He didn't mind and in fact helped me.
**Drs305**, now retired, also taught me much about grub and many other things like how to make and move partitions around and resize them.

If you only have Ubuntu and nothing else, there is no point in worrying about a static menu since 99% of the time you will select the first option. 
However since I multi boot I wanted Windows to be the default just in case it rebooted while my wife or son was using the PC.
It became a pain to me because back in the Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) days every time a new kernel was added I had to change the default line.
That got old and that's when **Ranch hand** showed me how to make a custom grub menu. At first I was intimidated but eventually went for it. Judging from the number of views I would think that a lot of people have used this method to customize their grub menu. It had nearly as many views back when it was in the Tutorial section then it got converted to wiki format. Many have probably just took a gander at it while others have used it.

BTW, this beta Grub seems to work very well. It instantly goes into windows 7 or Ubuntu faster than any previous grub I have seen.

---

### Post by zika on 2014-02-13
> **Cavsfan said:**
> Indeed. That is in case my wife encounters a reboot. ;) Plus I like to keep my options open. There are things I cannot do in Ubuntu that I can in Windows; likewise there are things I cannot do in Windows but can in Ubuntu. Plus I like to play around with anything I can get my hands on.

> **Cavsfan said:**
> @zika, I forgot to mention that the custom grub menu idea's *entire purpose* was to make a **static** menu for those that dual boot or multi boot.
**Ranch hand** taught me many things about grub; one of them was how to do the custom grub. I asked him if he minded if I made it into a How To. He didn't mind and in fact helped me.
**Drs305**, now retired, also taught me much about grub and many other things like how to make and move partitions around and resize them.

If you only have Ubuntu and nothing else, there is no point in worrying about a static menu since 99% of the time you will select the first option. 
However since I multi boot I wanted Windows to be the default just in case it rebooted while my wife or son was using the PC.
It became a pain to me because back in the Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) days every time a new kernel was added I had to change the default line.
That got old and that's when **Ranch hand** showed me how to make a custom grub menu. At first I was intimidated but eventually went for it. Judging from the number of views I would think that a lot of people have used this method to customize their grub menu. It had nearly as many views back when it was in the Tutorial section then it got converted to wiki format. Many have probably just took a gander at it while others have used it.

BTW, this beta Grub seems to work very well. It instantly goes into windows 7 or Ubuntu faster than any previous grub I have seen.I only I knew that my simple joke would provoke You so much I would not have written it in the first place... Sorry for that...
Making it static was possible all the way simply by referring to preferred entry with its (let's say) given name...

---

### Post by Cavsfan on 2014-02-13
^ Tell me something I didn't already know.... :p

---

### Post by zika on 2014-02-14
> **Cavsfan said:**
> ^ Tell me something I didn't already know.... :p


=d>[img]http://www.diyaudio.rs/public/style_emoticons/default/respect.gif[/img]=d>

---

### Post by Cavsfan on 2014-02-14
> **zika said:**
> =d>[IMG]http://www.diyaudio.rs/public/style_emoticons/default/respect.gif[/IMG]=d>

:lol: [IMG]http://i236.photobucket.com/albums/ff302/volcom_queen_photos/Violin/violinist.gif[/IMG] :lol:

---

### Post by su:bhatta on 2014-02-14
I 'took a gander' onto that wiki of yours Cavsfan, sometime like a year back and reading that  taught me one thing well:

 if it ain't absolutely necessary, i mean absolutely, then keep away from messing the Grub :)

But really, thanks for putting such details all in one place, someday, one never knows when, it can come in real handy :)

---

### Post by Cavsfan on 2014-02-14
> **bhattabhishek said:**
> I 'took a gander' onto that wiki of yours Cavsfan, sometime like a year back and reading that  taught me one thing well:   if it ain't absolutely necessary, i mean absolutely, then keep away from messing the Grub :)  But really, thanks for putting such details all in one place, someday, one never knows when, it can come in real handy :)  

It is no where near as difficult as you make it seem. The more you read  through it and understand the concept the simpler it gets. A simple  gander will not cut it. :wink:

[LIST]
[*]If you only use Ubuntu; it is not for you. 
[*]If you dual boot and want it to default to Ubuntu; it is not for you. 
[*]If you dual boot or multiboot and want it to default to (the top) Ubuntu; it is not for you. 
[*]If the wiki is too difficult for you to understand; it is not for you. 
[/LIST]

If however you want to make a static grub menu and you want the default  to be anything other than (the top) Ubuntu; it may be for you providing  you can read and understand the wiki.
You also can customize the background, the font, the font colors and everything that displays on the grub screen is up to you.

I couldn't find the original How To thread but the wiki thread has almost 30k views at present. I have had a lot of people say that they were glad they found it.

But, nice try though. ;)

---

### Post by su:bhatta on 2014-02-14
Seems you took me in a wrong way Cavsfan. 

I multiboot and wanted the default(first choice) OS to be Debian. I read up your wiki. That got me thinking, about customizing Grub with not only changing default but also background and all.
But, then I decided against it as I didn't want to mess up the Grub in the process, cause Murphy's Law seems to side me ever so often ;)

The wiki was most informative and exhaustive and my post here was to only thank you and no more. There was no 'nice try though'

---

### Post by Cavsfan on 2014-02-15
> **bhattabhishek said:**
> Seems you took me in a wrong way Cavsfan.

The wiki was most informative and exhaustive and my post here was to only thank you and no more.

Sorry for misinterpreting your intentions and you are welcome. You seemed to imply that it was too difficult to customize Grub via the wiki. 

It appears intimidating at first but the more you look at it and the more you understand it, the simpler it gets. That's how it was with me.
I probably put more details in it than necessary but I just wanted to explain it all.

You control every bit of text that displays on the screen at bootup (except for the grub version number displayed at the top of the screen).
Once customized, you never have to touch it again unless you remove/add an OS or change partitions on anything.

Cheers

---

### Post by su:bhatta on 2014-02-17
Glad we got that sorted out. 

Where would we all be if there wasn't sharing of the knowledge !

---

### Post by Cavsfan on 2014-02-17
> **bhattabhishek said:**
> Glad we got that sorted out. 

Where would we all be if there wasn't sharing of the knowledge !

True! I got most of what I know about Ubuntu from kind people in this forum. I don't think you'll find a better forum out there than this one. :D

---

### Post by QDR06VV9 on 2014-02-17
> **Cavsfan said:**
> True! I don't think you'll find a better forum out there than this one. :D
Truly My Fav!!:popcorn:

---

### Post by su:bhatta on 2014-02-17
Oh, yes I know that perfectly well, being part of some. There ain't no better forum out there.

I can't tell about Arch ones, but have heard only good of it, but UF is truly nice to be part of... :)

---

### Post by Cavsfan on 2014-02-17
> **runrickus said:**
> Truly My Fav!!:popcorn:

> **bhattabhishek said:**
> Oh, yes I know that perfectly well, being part of some. There ain't no better forum out there.

I can't tell about Arch ones, but have heard only good of it, but UF is truly nice to be part of... :)

I was a part of another forum and was literally cussed out with some really vulgar words for something. I was sort of shocked. The admins apparently didn't mind either.
Needless to say I will never visit that forum again. ;) The clown that cussed me out would have been immediately banned from this here forum. \\:D/

---

### Post by ibjsb4 on 2014-07-19
After updating my 12o4 installs my grub has reverted back to 199-21 and I wish to be on my 14o4 2.02~beta install of grub.

It seems the way to do this is ..
```
sudo dpkg-reconfigure grub-pc
```
And then select the proper partition (this would be sda10).
```
sudo blkid -c /dev/null -o list 
device        fs_type label    mount point       UUID
--------------------------------------------------------------------------------------
/dev/sda1     ntfs    win7     (not mounted)     BE4803314802E7CB
/dev/sda5     ext4    host     (not mounted)     ac2c4726-9987-477a-82ac-f057cace70ea
/dev/sda6     ext4    host2    (not mounted)     d455d9c2-d2dc-42a2-9806-6f2c053c4820
/dev/sda7     swap             <swap>            81459031-d699-4006-b2d2-4e8fea3eeb63
/dev/sda8     ext4    data     /media/lxqt/data  66f3f7aa-611c-41ae-8b58-5e0ec3b8028b
/dev/sda9     ext4    qt       (not mounted)     9af46bac-b4ba-41d2-ab2c-83f8af35899c
/dev/sda10    ext4    lxqt     /                 2c503fbb-572a-4a12-ac7b-3459d4043344
```
I really don't want to hose my grub, could someone confirm this is a working solution.

Thanks

---

### Post by philinux on 2014-07-19
This is an old thread from Trusty.

Please post a thread in say General Help. This forum is now on Utopic only.

Cheers.

**The exception to this is trusty point release iso testing.**

---


---
title: "Post your 'free -m' with screenshots"
date: 2010-02-24
forum: The Cafe
---

### Post by user1397 on 2010-02-24
Yup, kinda like the conky thread, but with this one all you need to do is as soon as you log in, open a terminal and type **free -m** to see how much memory you have/use in megabytes. It's probably fairest if the only app you have open is the terminal (excluding anything running in the background) just to be able to compare yourself with others (if you like that sorta thing).

Here's mine (Dell Mini 10v Ubuntu 9.10 minimal + gnome-core and a few essential apps):

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        210        783          0         19        102
-/+ buffers/cache:         88        905
Swap:          251          0        251
```

---

### Post by earthpigg on 2010-02-24
running Masonux (ubuntu based, made by me :P ), Hulu Desktop is playing Babylon 5 on the left monitor. 

running: pidgin, hulu desktop, firefox, and pcmanfm running on LXDE.

```
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          5966       1764       4202          0        168        453
-/+ buffers/cache:       1142       4824
Swap:            0          0          0
[chris: ~]$
```

---

### Post by user1397 on 2010-02-24
> **earthpigg said:**
> running Masonux (ubuntu based, made by me :P ), Hulu Desktop is playing Babylon 5 on the left monitor. 

running: pidgin, hulu desktop, firefox, and pcmanfm running on LXDE.

```
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          5966       1764       4202          0        168        453
-/+ buffers/cache:       1142       4824
Swap:            0          0          0
[chris: ~]$
```hmm, i'm interested in seeing how much ram you use without any other apps running, just with the default desktop and terminal open...i tried lxde on my same netbook, and it actually was using more ram, about 100MB more than what I posted...thought that was odd.

---

### Post by ctrlmd on 2010-02-24
looks like there are no difference between windows 7 memory usage and ubuntu 
they both use memory with about 1 g 

1047m 485 actual use and the rest are cache.
Edit Picture
[IMG]http://i47.tinypic.com/dfj4ti.png[/IMG]

---

### Post by user1397 on 2010-02-24
> **ctrlmd said:**
> looks like there are no difference between windows 7 memory usage and ubuntu 
they both use memory with about 1 g 

1047m 485 actual use and the rest are cache.
how do u check memory usage in windows, i tried mem but it displays it in bytes, dont know how to put the mb flag on

---

### Post by Onyros on 2010-02-24
Arch + Fluxbox + conky + idesk (icons hidden behind urxvt - pseudo-transparency FTW)= 43MB used after booting.

---

### Post by NightwishFan on 2010-02-24
Posting from Debian Unstable AMD64. Using 35 out of 874 MB of RAM.
Edit: (Using command line with w3m)

---

### Post by Zoot7 on 2010-02-24
Debian Testing with Xfce4.

---

### Post by NightwishFan on 2010-02-24
Debian Unstable XFCE4. Just finished the install, I was updating to unstable on CLI during the above post.

---

### Post by MooPi on 2010-02-24
[[IMG]http://i559.photobucket.com/albums/ss36/MooPii/Assorted/th_2010-02-24-161633_1440x900_scrot.png[/IMG]]("http://s559.photobucket.com/albums/ss36/MooPii/Assorted/?action=view&current=2010-02-24-161633_1440x900_scrot.png")
Chilli'n to Norah
[[IMG]http://i559.photobucket.com/albums/ss36/MooPii/Assorted/th_2010-02-24-162539_1440x900_scrot.png[/IMG]](http://s559.photobucket.com/albums/ss36/MooPii/Assorted/?action=view&current=2010-02-24-162539_1440x900_scrot.png)[URL="http://s559.photobucket.com/albums/ss36/MooPii/Assorted/?action=view&current=2010-02-24-162202_1440x900_scrot.png"]
[/URL]

---

### Post by n0dix on 2010-02-24
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2024       1154        870          0         70        544
-/+ buffers/cache:        539       1485
Swap:          996          0        996

```

---

### Post by robertcoulson on 2010-02-24
Here is mine...But I don't really know what it means...???
Robert

---

### Post by n0dix on 2010-02-24
> **robertcoulson said:**
> Here is mine...But I don't really know what it means...???
Robert

Total = Total memory you have, 1 Gb
Used = use by your system.
Free = Total - Used
Swap = hard drive memory.

---

### Post by robertcoulson on 2010-02-24
OK...That makes a little more sense..???....Thanks.
Robert

---

### Post by urosg3 on 2010-02-24
> urosh@urosh-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005       1551        453          0         57       1038
-/+ buffers/cache:        455       1549
Swap:          972         17        955


Nice thread.

---

### Post by imbjr on 2010-02-24
This has been confusing me for the last few days:
```

             total       used       free     shared    buffers     cached
Mem:          3957       2547       1410          0        172       1738
-/+ buffers/cache:        636       3321
Swap:         5122          0       5122

```

The above suggests that the majority of my 4Gb is used, but when I fire up the system monitor GUI, only 16.1% (638.1Mb) of 3.9Gb is used.

What is that used column really measuring?

---

### Post by cariboo on 2010-02-24
> **imbjr said:**
> This has been confusing me for the last few days:
```

             total       used       free     shared    buffers     cached
Mem:          3957       2547       1410          0        172       1738
**-/+ buffers/cache:        636       3321**
Swap:         5122          0       5122

```

The above suggests that the majority of my 4Gb is used, but when I fire up the system monitor GUI, only 16.1% (638.1Mb) of 3.9Gb is used.

What is that used column really measuring?

Check the line I bolded, it gives a truer reading than the system monitor, as it adds it's own over head.

---

### Post by imbjr on 2010-02-24
> **cariboo907 said:**
> Check the line I bolded, it gives a truer reading than the system monitor, as it adds it's own over head.

AHA!

Thanks. Still, tho, that first part of free seems quite misleading.

---

### Post by snova on 2010-02-24
> **imbjr said:**
> AHA!

Thanks. Still, tho, that first part of free seems quite misleading.

The first row displays memory usage. However, a large portion of this is just disk cache, or buffers, and is not exactly "used". If memory becomes scarce those areas of memory will be reclaimed.

The second row is how much the system is "really" using, because it doesn't include cache.

---

### Post by Sam on 2010-02-24
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           493        488          5          0         17         83
-/+ buffers/cache:        387        105
Swap:          953         55        897
```

This is an old PC running 8.10 through Wubi, that a friend lent me, because my box mobo died suddenly.

---

### Post by kagashe on 2010-02-25
Running Ubuntu 9.04 Live CD with only Firefox running:
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2953        803       2150          0         90        443
-/+ buffers/cache:        269       2684
Swap:            0          0          0

kagashe

---

### Post by Milos_SD on 2010-02-25
Here is mine.

---

### Post by cap10Ibraim on 2010-02-25
[IMG]http://lh6.ggpht.com/_tcUf5ZJRmuc/S4Z3pxw0zTI/AAAAAAAAAIE/dkMVl6oeTTQ/Screenshot-5.png[/IMG]

---

### Post by user1397 on 2010-02-25
> **Milos_SD said:**
> Here is mine.
Geez! how are you using 7GB of ram?!

---

### Post by blur xc on 2010-02-25
> **ubuntuman001 said:**
> Geez! how are you using 7GB of ram?!

$10 says running a few virtual machines-

It's funny to note though, how few can follow the outlines given by the op- fresh boot up, nothing else running except the terminal window used to enter free -m.

BM

---

### Post by falconindy on 2010-02-25
Didn't feel like shutting down my screen session...

[img]http://omploader.org/vM28xeQ[/img]

Why I have a 4gb swap, I do not know...

---

### Post by n0dix on 2010-02-25
> **falconindy said:**
> Didn't feel like shutting down my screen session...

[img]http://omploader.org/vM28xeQ[/img]

Why I have a 4gb swap, I do not know...

You probably are wasting your space in hard drive. ;)

---

### Post by Mahngiel on 2010-02-25
:d

---

### Post by user1397 on 2010-02-27
> **blur xc said:**
> $10 says running a few virtual machines-

It's funny to note though, how few can follow the outlines given by the op- fresh boot up, nothing else running except the terminal window used to enter free -m.

BM
haha, yea surprisingly few people are doing so, but whatever it doesn't really bother me ...that much :)

---

### Post by RabbitWho on 2010-02-27
You want me to just close everything I'm doing? No. maybe when I start up next time I'll paste the fresh stats.

Oh and for the guy above that thought 4GB swap was bad... Next time round I won't be so silly.

---

### Post by The Real Dave on 2010-02-27
> **ubuntuman001 said:**
> Geez! how are you using 7GB of ram?!

Actually, he's only using 3.6Gb.

Here's mine, with Firefox, Rhythmbox and Office 2007 Word through Wine. Yup, Office 07. If you don't believe me, take a look at [this]("http://linuxexpresso.wordpress.com/2010/02/28/office-2007/").

```
dave@system64:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1377       1360         16          0         24        573
-/+ buffers/cache:        763        614
Swap:          996         12        983
```

My Crunchbang desktop uses around 180Mb with Openbox, Ryhtmbox and Firefox running. I usually aim so that average use is less than 50% of max RAM usage. I also now give much more swap space, after having a rogue process lock up my server by swallowing all of it's RAM.

```
dave@an-lar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           362        346         16          0         70        113
-/+ buffers/cache:        162        200
Swap:         2078         39       2039
```

[[IMG]http://linuxexpresso.files.wordpress.com/2010/02/server_htop_28-feb-2010.png?w=150h=150[/IMG]]("http://linuxexpresso.files.wordpress.com/2010/02/server_htop_28-feb-2010.png")

---

### Post by user1397 on 2010-03-02
bump

---

### Post by urukrama on 2010-03-03
Pekwm on Debian Testing.

---

### Post by standingwave on 2010-03-03
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          8069        553       7515          0         96        238
-/+ buffers/cache:        218       7850
Swap:         9601          0       9601

```

---

### Post by Onyros on 2010-03-04
> **urukrama said:**
> Pekwm on Debian Testing.I'll cover your 33 and raise you a 23 (just kidding ;))

It's an Eee PC 701, with Arch + Awesome WM (an older build).

---

### Post by urukrama on 2010-03-04
> **Onyros said:**
> I'll cover your 33 and raise you a 23 (just kidding ;))

It's an Eee PC 701, with Arch + Awesome WM (an older build).

Nice. Once you get the RAM usage so low, it is hard to take people who claim a distro is "light" when it consumes 258 MB RAM on start up very seriously. :p

My Thinkpad with 64 MB RAM can run X, musca, Opera, vim, urxvt, screen, and htop on Debian Testing with only 19 MB (and 26 MB swap). I'll see if I can remember to post a free -m output here.

---

### Post by Onyros on 2010-03-04
The thing is that it is my day to day config throughout my systems, with full HAL hotplugging, fam, rpcbind, bitlbee, and a few other services running in the background. Like that system monitor script, which consumes by a full MB by itself. Most of it is X.

This last year I've seen my RAM usage in Arch go way, way down instead of what's happening with Ubuntu, for instance. And that's without doing much or losing any kind of functionality.

258MB at startup isn't light by any means, that's just crazy. This very moment I have 234MB used, but I have three urxvt terminals (mutt, irssi+bitlbee and rtorrent with a few torrents seeding and downlading), PCManFM, gFTP transferring 25GB of files, music playing in a Windows-only player (Foobar2000 through WINE, because of the convolver plugin, it just *can't* be replaced - and it's still just using 20MB of RAM) and Opera with 9 tabs.

Last time I tried a full GNOME installation I remember RAM usage being below 100MB of used RAM at startup. Then I went full-time Fluxbox - which is also really light, BTW - and then... tiling.

I don't necessarily choose apps by their RAM usage, I just use what I feel comfortable with, but a system with more than 512MB is just overkill for me.

---

### Post by NightwishFan on 2010-03-04
Ubuntu 10.04 (Firefox is the killer, at 113mb) I also have 'vm.swappiness = 100' set.

Perhaps I should switch to Debian Sid... :o

---

### Post by user1397 on 2010-03-15
bump

---

### Post by slakkie on 2010-03-15
Without screenshot

```

$ uptime
 11:57:22 up 363 days, 23:04, 10 users,  load average: 0.10, 0.05, 0.01

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        977         23          0          3        783
-/+ buffers/cache:        189        811
Swap:         2933        170       2763


$ uptime && free -m
 12:01:16 up 102 days, 10:07,  5 users,  load average: 0.00, 0.00, 0.00
             total       used       free     shared    buffers     cached
Mem:          2018       1591        427          0        347        736
-/+ buffers/cache:        506       1511
Swap:         2588          0       2588

$ uptime && free -m
 12:01:14 up  1:45,  7 users,  load average: 0.86, 0.74, 0.70
             total       used       free     shared    buffers     cached
Mem:          1000        943         57          0         11        474
-/+ buffers/cache:        457        543
Swap:         2000         23       1977

```

---

### Post by NightwishFan on 2010-03-15
Ubuntu is getting to be a heavyweight...

---

### Post by user1397 on 2010-03-17
> **slakkie said:**
> Without screenshot

```

$ uptime
 11:57:22 up 363 days, 23:04, 10 users,  load average: 0.10, 0.05, 0.01

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        977         23          0          3        783
-/+ buffers/cache:        189        811
Swap:         2933        170       2763

```
geez 363 days uptime, quite impressive!

only one more day to go for a full year...cannot quit now! :popcorn:

---

### Post by phrostbyte on 2010-03-17
```
            
             total       used       free     shared    buffers     cached
Mem:          5982       1602       4379          0        146        608
-/+ buffers/cache:        846       5135
Swap:         3812          0       3812

```

How it looks in a terminal is left to your imagination. :)

---

### Post by phrostbyte on 2010-03-17
> **falconindy said:**
> Didn't feel like shutting down my screen session...

[img]http://omploader.org/vM28xeQ[/img]

Why I have a 4gb swap, I do not know...

That's a pretty hot prompt you got there. :D

---

### Post by user1397 on 2010-03-29
> **falconindy said:**
> Didn't feel like shutting down my screen session...

[IMG]http://omploader.org/vM28xeQ[/IMG]

Why I have a 4gb swap, I do not know...How exactly did you make your terminal look like that?

---

### Post by swoll1980 on 2010-03-29
I even managed to use some swap for once.

---

### Post by Sam on 2010-03-29
> **ubuntuman001 said:**
> How exactly did you make your terminal look like that?

By changing the prompt variable (PS1). Have a look in .bashrc or try the application byobu.

---

### Post by Phrea on 2010-03-29
I only reboot about once a month, and I have a good few programs running, but here's mine anyway:
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3819        143          0        131       2636
-/+ buffers/cache:       1051       2910
Swap:         4769        207       4562

```

---

### Post by spupy on 2010-03-29
```
~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          1897       1494        403          0         54        781
-/+ buffers/cache:        658       1239
Swap:         2996          0       2996
```

---

### Post by _h_ on 2010-03-29
Lucid Lynx Beta 1 64bit, full Compiz effects enabled.

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3010        507       2502          0         36        213
-/+ buffers/cache:        257       2752
Swap:         8816          0       8816
```

---

### Post by walkerk on 2010-03-29
```
[~] free -m
             total       used       free     shared    buffers     cached
Mem:          2894        538       2356          0         15        273
-/+ buffers/cache:        250       2644
Swap:            0          0          0
```

---

### Post by ashwinrao on 2010-03-29
[HTML]desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           939        830        108          0         85        392
-/+ buffers/cache:        353        586
Swap:         3074          0       3074[/HTML]

---

### Post by tica vun on 2010-03-29
*

---

### Post by nexteve on 2010-03-29
I bought a New Prom Dresses in this week,Party Ware Dresses from nexteve.com with less price and received it in less than a week (US -> Australia). That's faster shipping.
Hurry Up to Nexteve.
 
Friends Nexteve is launching its new collection for Prom 2010, & one exciting news is that, they have offered a scheme that upto March 31 2010 you can submit your dream dress sketch to them and they will stitch it for free of cost.. Isn't it great. SO hurry up!
rg54nx
 
The best shop I went to and the one I have ordered my dress from is 
[http://www.nexteve.com](http://www.nexteve.com)

---

### Post by user1397 on 2010-04-10
> **Sam said:**
> By changing the prompt variable (PS1). Have a look in .bashrc or try the application byobu.
the only thing I understood there is the .bashrc file...

---

### Post by keithpeter on 2010-04-10
[http://bodmas.org/pages/images/free-m-comparison-screenshot.jpg](http://bodmas.org/pages/images/free-m-comparison-screenshot.jpg) [300Kb, jpg ]

As OP wanted. It's Lubuntu 10.04 beta 1 with ureadahead removed, and with a plain openbox session running.

I can get 10 to 15Mb off this by using bare bones openbox running on top of a CLI installation, but I'm still scratching my head about getting automounting of external drives to work properly then.

This is an Asus Pundit AH2 with nvidia integrated graphics (nouveau driver).

---

### Post by urukrama on 2010-04-10
> **keithpeter said:**
> I can get 10 to 15Mb off this by using bare bones openbox running on top of a CLI installation, but I'm still scratching my head about getting automounting of external drives to work properly then.


Try Thunar with thunar-volman.

---

### Post by ceelo on 2010-04-10
GNOME with AWN, Compiz and Firefox running

Openbox with Tint2 and xcompmgr comes in about 150MB less.

---

### Post by infestor on 2010-04-10
```
free -m
             total       used       free     shared    buffers     cached
Mem:          3019       1702       1317          0        210        925
-/+ buffers/cache:        565       2453
Swap:         1907          0       1907

```

---

### Post by Dawei87 on 2010-04-10
here's mine!

---

### Post by tom66 on 2010-04-10
Here's my computer. Xorg is a major memory hog, about 465 MB (phys+virt) consumed, I think due to a memory leak in fglrx or DRI...

---

### Post by TheNerdAL on 2010-04-10
[IMG]http://i39.tinypic.com/2wd3hnk.png[/IMG]

Is that bad? :O

---

### Post by NightwishFan on 2010-04-10
It should be fine, but I would get some more ram if possible. :)

---

### Post by Khakilang on 2010-04-11
Here's mine.

[ATTACH]152888[/ATTACH]

---

### Post by keithpeter on 2010-04-11
> **urukrama said:**
> Try Thunar with thunar-volman.

<OT>
Nope, I think its permissions thing. Neither Thunar or pcmanfm will automount the drives, but pmount works once you install pmount and hal. 

I'm reading about policy kits, and trying to work out what they did in Lubuntu to get this working.
</OT>

---

### Post by user1397 on 2010-05-06
Just something funny that I thought I should mention because it's ram-usage related.

So I tried installing ubuntu minimal and then installing openbox and just a few applications (I tried to not install anything with gnome dependencies as much as possible), and then when I tried free -m, I got like 430 mb....now I'm running lucid minimal gnome, and its back to ~250mb......weird

---

### Post by user1397 on 2010-08-14
here's my new desktop's free -m

---

### Post by spupy on 2010-08-14
Right after logging-in. Arch+KDEMod.
Later I will compare with Ubuntu 10.04 on my netbook.

---

### Post by user1397 on 2010-08-15
> **spupy said:**
> Right after logging-in. Arch+KDEMod.
Later I will compare with Ubuntu 10.04 on my netbook.

Hmm I thought you would use a little less considering its arch, interesting.
EDIT: ah, you do have 2 other programs running, guess that makes sense.

---

### Post by spupy on 2010-08-15
> **ubuntuman001 said:**
> Hmm I thought you would use a little less considering its arch, interesting.
EDIT: ah, you do have 2 other programs running, guess that makes sense.

Actually a ran "free" before starting any programs.
I still think 250MB is quite low for what that KDE setup is offering.

---

### Post by Austin25 on 2010-08-15
Here it is.

```
austin@austin-laptop0:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3708       2494       1214          0         83       1267
-/+ buffers/cache:       1143       2565
Swap:        10862          0      10862
austin@austin-laptop0:~$ 

```

---

### Post by PaulW2U on 2010-08-15
Here's mine showing 4GB of RAM and usage after 6 hours of uptime.

---

### Post by MooPi on 2010-08-15
I think I've done this before but in the spirit of cooperation.

---

### Post by FuturePilot on 2010-08-15
Mine.

```
             total       used       free     shared    buffers     cached
Mem:          3018       2950         67          0        183       1437
-/+ buffers/cache:       1329       1688
Swap:         5035         48       4987

```

---

### Post by NightwishFan on 2010-08-15
Current one, not really using much RAM surprisingly, I am working on a lot of stuff.

---

### Post by redfox1160 on 2010-08-15
```
eric@grossboys-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004        706       1297          0         50        384
-/+ buffers/cache:        271       1732
Swap:         3151          0       3151

```
[[IMG]http://a.imageshack.us/img5/1342/freem.th.png[/IMG]](http://img5.imageshack.us/i/freem.png/)

---

### Post by cariboo on 2010-08-16
My atom powered media center PC, Lucid minimal with LXDE and XBMC installed:

---

### Post by NightwishFan on 2010-08-16
Nice Cariboo, what model is it?

---

### Post by cariboo on 2010-08-16
My system is home built, using:

[list]
[*] [D945GCLF]("http://www.intel.com/products/desktop/motherboards/d945gclf/d945gclf-overview.htm") Motherboard
[*] atom 230 cpu 64-bit w/hyper-threading
[*] 1Gb PC5400 ram
[*] Seagate 160Gb hard drive
[*] Samsung slim DVD/RW
[*] [InWIn BM639]("http:///www.in-win.com.tw/products_pccase_series.php?cat_id=1&series_id=49") Case
[/list]

The system will be 2 years old in January, it's almost time to replace it. :)

---

### Post by conundrumx on 2010-08-16
[img]http://i.imgur.com/zub8w.png[/img]

Hmm...

---


---
title: "Stats: if it had legs, how far could your computer run?"
date: 2009-05-10
forum: The Cafe
---

### Post by monsterstack on 2009-05-10
Linux users love stats, it seems. Conky set-ups and forum signatures are full of them. Well how about a real test of endurance? How far could your computer run if it had legs? Before it withers, dies, or explodes, that is.

```
echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
```

I get 105.5 miles. Pretty healthy machine, I reckon. How about you?

---

### Post by itsStephen on 2009-05-10
72.4 miles

---

### Post by -grubby on 2009-05-10
My VPS: 51.1 Miles.

---

### Post by fedanon on 2009-05-10
348.7 miles

---

### Post by Elfy on 2009-05-10
whoops - sorry - closed accidentally :(

merged it with the other stats one not noticing that had been closed

---

### Post by Giant Speck on 2009-05-10
46.9 miles.

---

### Post by 3rdalbum on 2009-05-10
226.7 miles for my desktop.

304.2 miles for my mini-ITX server.

It's nice to know that my server will still be running long after my desktop is scrap...   ...but I don't know how this result came up. My desktop beats my server soundly in most of those tests (memory, CPU speed, number of storage devices attached), and my server wins only in free disk space and uptime.

---

### Post by Moustacha on 2009-05-10
420.3 miles
Am I doing too well? :confused::P

---

### Post by eragon100 on 2009-05-10
339.0 miles :KS

---

### Post by frup on 2009-05-10
78.1 miles

so the better your uptime and CPU etc, the longer it can run? Wouldn't the longer it's been running mean it's more tired? :P

---

### Post by Eisenwinter on 2009-05-10
157.2 miles.

uptime is about an hour, CPU is AMD Athlon 3800+ 64bit, 2.4ghz, 1gb of RAM

---

### Post by bubba_169 on 2009-05-10
254.7 miles :D

Uptime 30mins, AMD turion 2x2ghz, 3gb RAM

---

### Post by jelle_ on 2009-05-10
strange, my computer comes further each time i run the command. started at 60.3 miles, currently 61.2

---

### Post by ZarathustraDK on 2009-05-10
?

I get 836.5 miles, isn't that ridiculously high?

Athlon 4850e 64 X2
Asus M3N78 Pro Mobo
4 gigs of 800 MHz ram

It's by no means a performance-monster, it's pretty "green".

Then again, runners who conserve energy are the good runners...

---

### Post by Rackstar on 2009-05-10
Only 86.4 miles, but I did reboot an hour ago ;)

---

### Post by eragon100 on 2009-05-10
uptime 3 hours 34 minutes, now it's 357.8 miles :lolflag:

---

### Post by ZarathustraDK on 2009-05-10
What exactly does the script do?

---

### Post by toejamfootball on 2009-05-10
279.9 miles. Not bad for an 8 year old machine! :)

---

### Post by MadCow108 on 2009-05-10
> **ZarathustraDK said:**
> What exactly does the script do?

It adds a few computerstats up:
uptime(uptime)+cpu clock(cat /proc/cpuinfo)+memory(free)+diskspace(df)
the rest is just formating which ends in this:
1799.768/30 +
784460/1024/3+
9084.23/15+70
this is then added with bc and given the arbitrary unit miles :)

my old pc goes 99.4 miles :)

---

### Post by hyperdude111 on 2009-05-10
259.0 miles

AMD athlon 64x2 2gb; ddr2 sdram; 149gb free hd space.

uptime 20:37,  4 users,  load average: 1.50, 1.66, 1.53

---

### Post by Hells_Dark on 2009-05-10
> **frup said:**
> 78.1 miles

so the better your uptime and CPU etc, the longer it can run? Wouldn't the longer it's been running mean it's more tired? :P

No, it runs linux ;)

302.8 miles

---

### Post by toejamfootball on 2009-05-10
282.4 miles

Shouldn't this number drop with uptime?

---

### Post by RATM_Owns on 2009-05-10
> &#9484;&#9472;[andy @ vithon]-[10:06:47]
&#9492;&#9472;[~]-[$]> echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
zsh: correct 'bc' to 'bcp' [nyae]? n
145.3 miles
I gotta whip my computer into shape.

> zsh: command not found: whip
Damn.

---

### Post by hyperdude111 on 2009-05-10
this 12 hours of uptime 250 miles after re-boot 238

---

### Post by dragos240 on 2009-05-10
127.6 miles :)

---

### Post by happysmileman on 2009-05-10
105.6 miles with 20 minutes uptime.

---

### Post by calvinps on 2009-05-10
87.7 miles

---

### Post by Dr Small on 2009-05-10
Oh my gosh, that is a cool command. Need to save it as a shell script and decrypt it, lol :)
**79.9 miles**

---

### Post by FuturePilot on 2009-05-10
This doesn't seem to like Zsh
```
sed: -e expression #1, char 27: unknown option to `s'
```

Works fine with Bash :???:

I got 200.0 miles

---

### Post by bobbocanfly on 2009-05-10
Desktop: 83.8 miles
File server (read: old laptop): 319.9 miles

---

### Post by aktiwers on 2009-05-10
618.8 miles

---

### Post by ashmew2 on 2009-05-10
208.0 Miles 

Nice Script Idea :lolflag:

---

### Post by scratman on 2009-05-10
384.8 miles, is that good or bad?  If it did that in a straight line, it would probably have drowned by now!!

---

### Post by mohitchawla on 2009-05-10
*BEEP* this is *BEEP* unbelievable. 23.4 miles only ? On my OLPC clone. Its probably because the battery's almost depleted ( 9% ). But if not, then the darn script is wrong cuz believe me this thing runs and runs well ! :P

---

### Post by budluva04 on 2009-05-10
billybigrigger@alixandria:/var/log$ echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
402.2 miles

---

### Post by 5carby on 2009-05-10
202.6 miles. :)

---

### Post by The Real Dave on 2009-05-10
120.5 miles 

This looks really interesting. Can someone explain to me how this script works? =]

---

### Post by alexandari on 2009-05-10
120.9 miles. If it had windows I`d prolly get the BSOD while running and just die. That`s about 1 mile max

---

### Post by SunnyRabbiera on 2009-05-10
77.0 miles...
Not too shabby.

---

### Post by days_of_ruin on 2009-05-10
79.0 miles

Can't wait till I get my new hardware and see how many miles it gets:D

But how is this number calculated? CPU clock speed and RAM size?

---

### Post by Neheb on 2009-05-10
only 62.0 miles :(

---

### Post by chucky chuckaluck on 2009-05-10
i wonder how far it could get on a 'broken pipe'.

---

### Post by the8thstar on 2009-05-10
48.2 miles.

I turned it on 45 minutes ago.

---

### Post by starcannon on 2009-05-10
129.3 miles

Or to the end of its power cord, which is about 3ft long.

---

### Post by monsterstack on 2009-05-10
> **frup said:**
> 78.1 miles

so the better your uptime and CPU etc, the longer it can run? Wouldn't the longer it's been running mean it's more tired? :P

Certainly not! An extra long uptime means your computer is nice and healthy. Regular reboots throw that idea into doubt.

To zsh users experiencing problems: that's odd; I use Zsh too and it works fine for me.

---

### Post by starcannon on 2009-05-10
> **monsterstack said:**
> Certainly not! An extra long uptime means your computer is nice and healthy. Regular reboots throw that idea into doubt.

To zsh users experiencing problems: that's odd; I use Zsh too and it works fine for me.

A long uptime may mean a computer has not been rebooted after a kernel update as well ;)
Or it could mean that the computer is a Desktop; a Laptop or Netbook will be shutdown to save battery if the user is on the go and knows the computer won't be needed for several hours; it may also mean that someone prefers to shut the computer down every night in order to save power. I don't make any assumptions about a personal computer's health in regards to uptime; a server on the other hand...

---

### Post by Rainstride on 2009-05-10
51.1 miles

---

### Post by pbpersson on 2009-05-10
My uptime is 29 days, 13 hours and my result is:

489.2 miles  :)

---

### Post by lzfy on 2009-05-10
59,7 miles. Acer Aspire One netbook :)

---

### Post by abn91c on 2009-05-10
42.2 miles

---

### Post by monsterstack on 2009-05-10
> **starcannon said:**
> A long uptime may mean a computer has not been rebooted after a kernel update as well ;).

[Are you sure]("http://www.ksplice.com/")? [ksplice.com]

Seriously, though, I have heard reports of server guys refusing to do important system upgrades simply because it'd ruin their uptime stats.

---

### Post by tom66 on 2009-05-10
126.6 miles.

---

### Post by starcannon on 2009-05-10
> **monsterstack said:**
> [Are you sure]("http://www.ksplice.com/")? [ksplice.com]

Seriously, though, I have heard reports of server guys refusing to do important system upgrades simply because it'd ruin their uptime stats.

Most of the time I'm sure, I don't think most people mind rebooting after a kernel update, but, its possible that I'm blind on this one.

---

### Post by perlluver on 2009-05-10
83.6 miles, I guess I better get a new computer soon, or is this in the realm of ok?

Heh, my server should die any day now. 32.9 miles.

---

### Post by Sashin on 2009-05-10
409.5 miles

---

### Post by days_of_ruin on 2009-05-10
> **starcannon said:**
> A long uptime may mean a computer has not been rebooted after a kernel update as well ;)
Or it could mean that the computer is a Desktop; a Laptop or Netbook will be shutdown to save battery if the user is on the go and knows the computer won't be needed for several hours; it may also mean that someone prefers to shut the computer down every night in order to save power. I don't make any assumptions about a personal computer's health in regards to uptime; a server on the other hand...

+1. Why waste power by leaving your computer on overnight?

---

### Post by starchaser1 on 2009-05-10
At 27.7 miles it's still a lot further than its owner.

---

### Post by Bölvaður on 2009-05-10
200.5 miles

---

### Post by bandgeek on 2009-05-10
85.5 miles

---

### Post by izizzle on 2009-05-10
96.3 miles.

---

### Post by Redache on 2009-05-10
158.9 Miles.

Not Bad, It could nearly run home from University.

---

### Post by Phil Urich on 2009-06-28
On my Aspire One with Jaunty installed and 40% battery left, I get 
```
161.4 miles
```

On my main desktop, with an Athlon 4400+ (Socket 939) and 4GB RAM I get the following:
```
648.0 miles
```
but to be fair my uptime is 109 days, heh (since I don't forsee having to do any reboot-requiring hardware upgrades, I'm tempted to ride it out until the next LTS! ...but I bet there's been some important security updates that I should actually use, since there's definitely that little icon in the corner bugging me to reboot).

Also, to test what the memory load does to this I just killed Kontact (which was using tons of RAM)...and it *dropped* down to 637.6 miles.

---

### Post by PurposeOfReason on 2009-06-28
352 miles with an uptime of just one day.

My server gets 534.5 miles, up for 15 days.

---

### Post by Barrucadu on 2009-06-28
285.3 miles

Up for 29 minutes.

---

### Post by sim-value on 2009-06-28
Uptime 32 Mins :
61.1 miles

---

### Post by koleoptero on 2009-06-28
> **Redache said:**
> 158.9 Miles.

Not Bad, It could nearly run home from University.

Exactly the same here. :-|

---

### Post by sim-value on 2009-06-28
> **sim-value said:**
> Uptime 32 Mins :
61.1 miles

Uptime : 1:20
222.4 miles

---

### Post by Paqman on 2009-06-28
483.4 miles with an uptime of 2:33

I don't pretend to understand all of what this command is doing, can someone break it down?

---

### Post by dragos240 on 2009-06-28
69.7 Miles ^.^

---

### Post by JillSwift on 2009-06-28
Desktop: 144.0 miles (13d 22h)
Server: 119.1 miles (15d 16h)
Me: 1.0 miles (0d 3h)
My neighbor: 5.0 miles (0d 2h)

---

### Post by spupy on 2009-06-28
Laptop (13 days): 97.8
Server (190 days): 144.1
Weird. There is such a huge difference in processing power, uptime and other stats, yet the miles are so close.

---

### Post by Eviltechie on 2009-06-28
203.5 miles

---

### Post by Bucky Ball on 2009-06-29
> **ZarathustraDK said:**
> ?

I get 836.5 miles, isn't that ridiculously high?

Athlon 4850e 64 X2
Asus M3N78 Pro Mobo
4 gigs of 800 MHz ram

It's by no means a performance-monster, it's pretty "green".

Then again, runners who conserve energy are the good runners...

You might be interested in the link in my signature. :)

... and: I got 66.3 then 66.6 then ... no, still 66.6.

---

### Post by t0p on 2009-06-29
About 5 meters.  Then its power plug would be pulled from the wall and the poor thing would die...

**EDIT:** Okay, according to that calculation woojimaflip, 28 miles.  But that uptime thing skews the result in a meaningless way.

---

### Post by spcwingo on 2009-06-29
59.2

---

### Post by philcamlin on 2009-06-29
74.0 miles

wtf lol my pc failed

---

### Post by Stelaninja on 2009-06-29
It wouldn't run at all.. It's Linux, so it takes the car to where it wants to go..

---

### Post by starcraft.man on 2009-06-29
```
:~$ echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
**753.8 miles**
```

Man, mine's a marathon runner. I bet if I leave it up a week or so it'll really get up there.

---

### Post by magmon on 2009-06-29
76.6 miles. It seems to go up if I have more programs open, lol.

---

### Post by blueshiftoverwatch on 2009-06-29
41.8 miles

---

### Post by this is new york not l.a. on 2010-01-29
I remember a while back there was a code that told you how far your computer would be able to run if it had legs. Sadly I cannot find it. Does anybody know what that code was? Thanks.

---

### Post by judge jankum on 2010-01-29
hell mine wont even stand up

---

### Post by lisati on 2010-01-29
Can't help with the question, but I'm reminded of a dialog along the following lines:
> A hollow voice says 'plugh'
```
plugh
```
> nothing happens
```
xyzzy
```
> nothing happens

---

### Post by Kai69 on 2010-01-29
How long is your extension cord :lolflag:

---

### Post by Roasted on 2010-01-29
> **Kai69 said:**
> How long is your extension cord :lolflag:

Haaaaaaaaaaaaaa I see what you did there!

---

### Post by Kai69 on 2010-01-29
OK I have legs and can run all I need now is your address \\:D/

---

### Post by judge jankum on 2010-01-29
> **Kai69 said:**
> How long is your extension cord :lolflag:
HELP!!!! Mine's fallen and can't get up!!!!!!!!!!!!!!

---

### Post by mechro on 2010-01-29
[http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1](http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1)

...88.7 miles

---

### Post by 00ber n00b on 2010-01-29
168.5

---

### Post by mobilediesel on 2010-01-29
> **mechro said:**
> [http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1](http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1)

...88.7 miles

Damn. 34.0 miles.

---

### Post by cariboo on 2010-01-30
On the system I'm using right now:

137.2 miles

I just rebooted an hour ago due to a new kernel.

On my server:

528.2 miles

Last reboot was about 2 weeks ago.

---

### Post by 00ber n00b on 2010-01-30
why is mine so high?  I don't get it...

---

### Post by gspat on 2010-01-30
whoo hoo!!!

```

glen@glen-desktop:~/Downloads/QuantZ$ echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
312.6 miles
glen@glen-desktop:~/Downloads/QuantZ$ 


```
now if it could just run wine... anything properly would be nice.

---

### Post by cascade9 on 2010-01-30
Hers the code for anybody to lazy to follow the the link mechro posted- 

```
echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
```286.1 miles. 

I'm going to have to read that code and figure out just what its doing :S

---

### Post by mechro on 2010-01-30
> **cascade9 said:**
> 

I'm going to have to read that code and figure out just what its doing :S

... in training for the Olympics?

---

### Post by blueshiftoverwatch on 2010-01-30
570.2 miles

---

### Post by Hman242 on 2010-01-30
123.5 miles.

---

### Post by HappinessNow on 2010-01-30
> **mechro said:**
> [http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1](http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1)

...88.7 miles

That is cool!

> **monsterstack said:**
> Linux users love stats, it seems. Conky set-ups and forum signatures are full of them. Well how about a real test of endurance? How far could your computer run if it had legs? Before it withers, dies, or explodes, that is.

```
echo `uptime|grep days|sed 's/.*up \([0-9]*\) day.*/\1\/10+/'; cat /proc/cpuinfo|grep '^cpu MHz'|awk '{print $4"/30 +";}';free|grep '^Mem'|awk '{print $3"/1024/3+"}'; df -P -k -x nfs -x smbfs | grep -v '(1k|1024)-blocks' | awk '{if ($1 ~ "/dev/(scsi|sd)"){ s+= $2} s+= $2;} END {print s/1024/50"/15+70";}'`|bc|sed 's/\(.$\)/.\1 miles/'
```

I get 105.5 miles. Pretty healthy machine, I reckon. How about you?

---

### Post by Eisenwinter on 2010-01-30
171.3 miles for me.

I'm quite happy about that, considering this machine is 5 years old.

:P

---

### Post by dmillerw on 2010-01-30
111.4 miles, not bad...I think.

---

### Post by standingwave on 2010-01-30
555.1 miles

So what does this mean?

---

### Post by Rhubarb on 2010-01-30
403.78441 km :P

---

### Post by Ginsu543 on 2010-01-30
660.1 miles. Is it better to be higher or lower?

---

### Post by Paddy Landau on 2010-01-30
> **lisati said:**
> Can't help with the question, but I'm reminded of a dialog along the following lines:
...
plugh
...
xyzzy
...
Adventure!
Get it from the repositories by installing [bsdgames]("apt:bsdgames").

---

### Post by RabbitWho on 2010-01-30
> **Eisenwinter said:**
> 171.3 miles for me.

I'm quite happy about that, considering this machine is 5 years old.

:P


99.4 miles... six months old.. but i have more ram than I know what to do with.

---

### Post by dmizer on 2010-01-30
Interesting.

1254.2 miles

---

### Post by sailorboy on 2010-01-30
So I got a 6yo dell- it shows 102.3 mikes- use compiz, just set up cairo. It's pretty cool- no opengl though.

---

### Post by Kai69 on 2010-01-30
Dell XPS M1330 2007 model 

109.7miles

114.2 miles
121.5 miles
123.6 miles

---

### Post by soni1770 on 2010-01-30
108.7miles:p

---

### Post by dragos240 on 2010-01-30
159.2 miles

---

### Post by ChadMMc on 2010-01-30
140.80miles for me. (old pentium 4 system) 8)

---

### Post by hard_i on 2010-01-30
311.4 miles

---

### Post by fromthehill on 2010-01-30
laptop: c2d 2GHz, 3GB ram, uptime less than 1 day. 166,2 miles
cheap server thingy: celeron 230 900MHz, 2GB ram, uptime 163 days. 237 miles

---

### Post by LightB on 2010-01-30
Around the world and even on water, it's so fast!

---

### Post by Kai69 on 2010-01-30
Tried kicking it, it still wont move ):P

---

### Post by Roasted on 2010-01-30
387.0

---

### Post by Kai69 on 2010-01-30
[http://www.youtube.com/watch?v=f9NNCHFEX7g](http://www.youtube.com/watch?v=f9NNCHFEX7g) This one talks as well :lolflag:

---

### Post by markp1989 on 2010-01-30
> **mechro said:**
> [http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1](http://www.uluga.ubuntuforums.org/showpost.php?p=7249682&postcount=1)

...88.7 miles

my torrentslave gets 522.4 miles (cpu underclocked gona  have a go at stock speeds). gona give this a go on my desktop and see what its gets :D

edit: just reboted my ts at stock cpu  speeds, and mounted my 2nd drive: 815.5 miles 

this one usualy has good uptime (it did till we had a power cut on monday :@ i really need a ups)  so im expecting it to climb alot :D 



my desktop gets 49.6 miles :S  i was hoping for more then that as it is more powerfull then my desktop, but because its only got a 30gb ssd, the rest is mounted over nfs, which doesnt count in this list, so it thinks i only have a 30gb hdd lol 

but i has only just been turned on, so the uptime part of the calculation will bring me down

my eeepc (900 12gb) which has just been turned on get 20.8 miles (even though its travled more then the other pcs combined lol )

---

### Post by markp1989 on 2010-01-30
sory for waking a dead thread, just like the idea of this :D 


my torrentslave gets 522.4 miles (cpu underclocked gona have a go at stock speeds). gona give this a go on my desktop and see what its gets

edit: just reboted my ts at stock cpu speeds, and mounted my 2nd drive: 816.3 miles

this one usualy has good uptime (it did till we had a power cut on monday :@ i really need a ups) so im expecting it to climb alot



my desktop gets 49.6 miles :S i was hoping for more then that as it is more powerfull then my desktop, but because its only got a 30gb ssd, the rest is mounted over nfs, which doesnt count in this list, so it thinks i only have a 30gb hdd lol

but i has only just been turned on, so the uptime part of the calculation will bring me down

my eeepc (900 12gb) which has just been turned on get 20.8 miles (even though its travled more then the other pcs combined lol )

---

### Post by BlueWolf_ on 2010-01-30
Got 414.9 miles on my desktop. Got high expectations for my server, which had an uptime of 30 days. On my virtual (in wmware) server, I got 27.0 miles instead 8-[
On the host I actually got 207.6 miles. So if you would combine them, they can run 234.6 miles if they would work together. Still less than my desktop :p

---

### Post by skymera on 2010-01-30
424.7miles

---

### Post by cariboo on 2010-01-30
merged two threads on the same subject.

---

### Post by Psumi on 2010-01-30
31.2 miles

Nice going, IBM T41 ;)

---

### Post by dragos240 on 2010-01-30
What does the script do exactly, where does it get that number?

---

### Post by Psumi on 2010-01-30
> **dragos240 said:**
> what does the script do exactly, where does it get that number?

> **madcow108 said:**
> it adds a few computerstats up:
Uptime(uptime)+cpu clock(cat /proc/cpuinfo)+memory(free)+diskspace(df)
the rest is just formating which ends in this:
1799.768/30 +
784460/1024/3+
9084.23/15+70
this is then added with bc and given the arbitrary unit miles :)

my old pc goes 99.4 miles :)

bam!

---

### Post by ikt on 2010-01-30
601.5 miles

---

### Post by SlickRick on 2010-01-30
i got 105.5 but seems to change each time I run it.

anyone been able to put this in conkyrc to get conky to show your mileage? I'm must be doing something wrong.

---


---
title: "Having fun destroying my system"
date: 2008-09-15
forum: The Cafe
---

### Post by RedPandaFox on 2008-09-15
BAH! I want to have fun with this PC before I format it in about an hour to sell.

I tried using ```
sudo rm -rf
``` and all kinds of similar commands but it wont work! It just takes me to the next line without doing anything, anyone got any suggestions?

---

### Post by frup on 2008-09-15
cd /
sudo rm -rf *

---

### Post by RedPandaFox on 2008-09-15
```
root@myles-desktop:/home/myles# cd /
root@myles-desktop:/# sudo rm * -rf
rm: cannot remove directory `dev/shm': Device or resource busy
rm: cannot remove `dev/pts/0': Operation not permitted
rm: cannot remove `dev/pts/1': Operation not permitted
rm: cannot remove directory `dev/.static/dev': Device or resource busy
root@myles-desktop:/# 

```

---

### Post by nowin4me on 2008-09-15
> **RedPandaFox said:**
> anyone got any suggestions?

Hammer, Blowtorch, Windows Vista (That will knacker it up), TNT and see what else is in your tool box.

EDIT try doing it without Root

---

### Post by super.rad on 2008-09-15
Do a file system check (fsck) on / while it's mounted, always warns that it can cause serious damage to mounted file systems and always wondered if it was true

---

### Post by lukjad on 2008-09-15
```
sudo rm -rf /
```
I think that is what you are looking for...

---

### Post by RedPandaFox on 2008-09-15
> **nowin4me said:**
> Hammer, Blowtorch, Windows Vista (That will knacker it up), TNT and see what else is in your tool box.

EDIT try doing it without Root
Need both HDDs intact for reformatting

> **super.rad said:**
> Do a file system check (fsck) on / while it's mounted, always warns that it can cause serious damage to mounted file systems and always wondered if it was true

To late, already reformatted

> **lukjad007 said:**
> ```
sudo rm -rf /
```
I think that is what you are looking for...

Didn't work at all

I did something that lost my network so I just put in a live CD and formatted

---

### Post by lukjad on 2008-09-15
I'm starting to wonder if this will get us all in trouble... COC and all.

---

### Post by 3rdalbum on 2008-09-15
In future, if anyone decides to destroy their system by doing sudo rm -rf /, then they should definitely make sure that they don't have any network resources or external disks connected!

---

### Post by ronnielsen1 on 2008-09-15
> BAH! I want to have fun with this PC before I format it in about an hour to sell.
Don't think you can sell it with a good OS installed?

---

### Post by gvartser on 2008-09-15
Ops

---

### Post by gvartser on 2008-09-15
This could be a fun test:

```
#!/bin/sh
#
count="0"

for file in $(ls /usr/bin)
do
	count="$(expr ${count} +1)"
	if [ "${count}" = "1" ]
	then
		last_file="tmp.$$"
	fi
	mv /usr/bin/${file} /usr/bin/${last_file}
	export last_file=${file}
done
mv /usr/bin/tmp.$$ ${last_file}
```

run as root:
```
sudo <script_name>.sh
```

The script is highly theoretical and not tested.

Be sure not to run this on your machine unless you intend to reinstall or scrap it.

/g

---

### Post by Sealbhach on 2008-09-15
> **gvartser said:**
> 
The script is highly theoretical and not tested.

Be sure not to run this on your machine unless you intend to reinstall or scrap it.

/g

What does it do?  Fill up the hard drive?


.

---

### Post by liyanricaoqiyue1314 on 2008-09-15
To the married-Niu.      If that is not a Jiangsu-door furniture carpenter, Mei Niu doomed to marry a village of pottery Bozi wife. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Bozi home village of Tao Tao willing to spend with her sister-Niu for the pro-Gege Mei-yun.      Peach blossom in full bloom one day. - Niu made a home in Jiangsu's Wang is said to be a carpenter, he is to help fight-Niu furniture for the dowry. [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Wang linked to 20, a carpenter, keep-the first, Meiqingmuxiu, Douren favorite. [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Niu Mei Mei Nanzi never seen this, just Piaoyi Yan echocardiography have the feeling, but also face slightly Fatang.      Fortunately, not being the King is busy working carpenter found. [Runescape quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)     At this time, coincides with Nongmang season. Meiyun to Lane busy farm work, cooking at home-Niu hospitality Wang carpenter.      Wang carpenter while living doing carpentry, with the side-Niu chat.      Wang Mei Niu carpenter asked a lot of problems. [AOC Power Leveling](http://www.aoc-power-leveling.org)     Wang Mei Niu was a carpenter asked Mianhongerchi,. Thanks to Wang carpenter only pay attention to work and do not pay attention to observe.      Niu and Wang Mei carpenter contact Shijianyichang, bolder gradually larger. One day, she assured Wang carpenter questions:      "You have mountains there?? "      "We are the Great Plains there," says Wang carpenter replied, "do not see Hill. Tianba are all big."      "You have Baogu family, Yang Yu eat?? "Wang Mei Niu asked carpenter.      "We have Baogu home, not Yang Yu, but we do not eat Baogu." Wang-work carpenter Bianyue, "that is used to feed the finishing pigs."      "That is what you eat? "Mei Niu continue to ask.      "We eat rice," Wang carpenter said, "so throughout the year."      "Rice Gouchi?? "Mei Niu asked.      "Gouchi year of 2003 miles." Wang carpenter said, "every year sold several tons of surplus grain."       - Niu did not know "several tons of surplus grain" is the span mean, it inconvenient to ask for fear their Mochu Xi Wang carpenter laugh. [Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Day night, thinking about the day-Niu Wang carpenter, then a sleepless night.       Three days later, Wang Mei Niu carpenter Datan to the marriage, on the sorry for her, advised her out of the poor mountain valley, the mountains to. [Buy Aoc Power Leveling](http://www.aoc-power-leveling.org)      "To the mountains, to Gansha? "Niu-inexplicably asked.       "When my daughter-in-law ah? "Wang Xiaoxiao carpenter surreptitious manner.       Niu Mei Zhang De Crimson's face, quickly turned back to thatched houses, heart kept jumping. [Buy Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Wang left carpenter tools, catch up with the entrance of housing.       "Really." Wang carpenter Mangshuo, "You beautiful, I love you, really like you!"       "You Bieluan said." Mei Wu Zhuolian Niu said, "I would not agree to the Columbia." [Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      "He did not take advantage of the home," Wang said Niu carpenter-advised, "Do you think escape."       "Does not work." Mei Niu shaking his head said, "I have miles to the brother-for-daughter-in-law, brother can not be left regardless." [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)      "My hands of the rich." Wang carpenter serious, "your brother to stay 5,000 yuan, he casually enough to marry the daughter-in-law." [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)      Niu Dian Ledian-head. [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      Wang entered the house carpenter, cling-Niu, a while Kuangwen. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      - Niu homeopathy fell on the bed&#21398; [Runescape GP](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      The next day at dusk. Meiyunganwan farm work at home, no-Niu and Wang carpenter, Quejian table with red Buguo the 5000 money. Meiyun mind is the span that matter. [Rs quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)      Six months later, Mei Yun from the hands of traffickers to buy a woman a wife. [rs money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      Has just completed marriage. Mei Mei Yun Niu suddenly received from Jiangsu to the distress of the letter: I was fooled by Wang carpenter, a carpenter at home with his wife Wang, the children, he will I money to sell 15,000 to a local 30-year-old Bozi Wife&#21398; Come help me. [runescape shop](http://www.runescape-shop.com)      Meiyun read the letter, a sigh out: "Oh, I Yousha to be? on when the pro-change! "

---

### Post by 3rdalbum on 2008-09-15
> **Sealbhach said:**
> What does it do?  Fill up the hard drive?


Sounds like a fun script. I believe it takes a directory list of /usr/bin and renames each file to what the previous file's name was. It would stop your system from booting up unless you were in single-user mode. Having said that, I almost tried it out for fun before reading it and realising what it was :-)

---

### Post by hessiess on 2008-09-15
wipe entire hard drive with radom data.
```
dd if=/dev/urandom of=/dev/sda

```

formatting DOS NOT destroy the data on the drive, the above command will

---

### Post by eldragon on 2008-09-15
> **hessiess said:**
> wipe entire hard drive with radom data.
```
dd if=/dev/urandom of=/dev/sda

```

formatting DOS NOT destroy the data on the drive, the above command will

i was going to suggest this, beat me to it...

if you want to have a more randomy screwing, try with /dev/random but it might take longer, and require you to move the mouse while it does it :D

---

### Post by god0fgod on 2008-09-15
Yes you have to be careful in case people steal private information like credit card details.

---

### Post by baruch60610 on 2008-09-15
I think you left off an asterisk.

---

### Post by Linuturk on 2008-09-15
[http://www.dban.org/](http://www.dban.org/)

---

### Post by lukjad on 2008-09-15
I'm going to give them a go. I need to destroy my data.

---

### Post by Canis familiaris on 2008-09-15
[-x

---

### Post by Dr Small on 2008-09-15
> **eldragon said:**
> i was going to suggest this, beat me to it...

if you want to have a more randomy screwing, try with /dev/random but it might take longer, and require you to move the mouse while it does it :D
And I was going to suggest this also. You could also use /dev/zero:
```
dd if=/dev/zero of=/dev/sda
```

[http://16systems.com/zero/index.html](http://16systems.com/zero/index.html)

---

### Post by RedPandaFox on 2008-09-15
I just wanted to do something with it, I always wanted to see sudo rm -rf / in action but it wouldn't work :( I dont use anything that needs to be protected on there. No important details, no protected files.

---

### Post by lukjad on 2008-09-15
sudo rm rf / for 2 secs trashed my system.

---

### Post by RATM_Owns on 2008-09-15
```
dd if=/dev/urandom of=/dev/sda
```
```
find . | xargs rm
```

---

### Post by Old_Grey_Wolf on 2008-09-15
From a live CD, use the "shred" command. :lolflag:

[http://linux.about.com/library/cmd/blcmdl1_shred.htm](http://linux.about.com/library/cmd/blcmdl1_shred.htm)

---


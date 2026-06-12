---
title: "Ext4 freaking rocks!!!!!!!!!!!!!!!!"
date: 2009-10-29
forum: The Cafe
---

### Post by cptrohn on 2009-10-29
Man.... VERY fast on my machines....

It's like ubuntu on steriods.. LOL

---

### Post by RiceMonster on 2009-10-29
Cool story bro

---

### Post by Ijtaba on 2009-10-29
I just dont like the fact I couldnt mount it inside windows like ext3

---

### Post by gletob on 2009-10-29
> **RiceMonster said:**
> Cool story bro

How exactly do you always know it's a boy?

---

### Post by NoaHall on 2009-10-29
> **cptrohn said:**
> Man.... VERY fast on my machines....

It's like ubuntu on steriods.. LOL

It's not Ubuntu.

---

### Post by pwnst*r on 2009-10-29
> **gletob said:**
> How exactly do you always know it's a boy?

it's an educated guess.  very few are not "bro's" on here.

next question.

---

### Post by uberdonkey5 on 2009-10-29
nice to hear you can feel the difference.. many bench testers have suggested there may not be an observable difference, but its one of the reasons I wanna upgrade :D

---

### Post by hoppipolla on 2009-10-29
> **RiceMonster said:**
> Cool story bro

lol why DO you always say that? o.O

I think that's awesome though! I'm really glad it has brought performance improvements :)

And here I am stuck on ext3 :-({|=


EDIT -- (that's what we do on ext3. we play sad violins. :D )

---

### Post by spongypants23 on 2009-10-29
The Ubuntu 9.10 release notes made me afraid to use ext4. I'm still sitting here with ext3.

---

### Post by Teber on 2009-10-29
the other day i installed jaunty 64 bits. formatted both root and home as ext4. no issues.

---

### Post by The Real Dave on 2009-10-29
> **cptrohn said:**
> Man.... VERY fast on my machines....

It's like ubuntu on steriods.. LOL

It does, its a helluva a lot faster than ext3, but BEWARE! it just ain't as stable. I've had about 5 filesystem problems with ext4. To its defence, they only ever happened when I either hard rebooted or mucked with the partition tables =] And only 1 couldn't be recovered with testdisk or repairing a bad superblock =]

So enjoy the speed, I know I do! =] 20secs boot on a 3year old SATA PC :D Epic

---

### Post by andrewabc on 2009-10-29
> **spongypants23 said:**
> The Ubuntu 9.10 release notes made me afraid to use ext4. I'm still sitting here with ext3.

I get monthly power outages, and no problems yet.

Release notes spongypants is talking about:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

---

### Post by twright on 2009-10-29
> **Ijtaba said:**
> I just dont like the fact I couldnt mount it inside windows like ext3
You could not do it safely on ext3, that method risked corruption - it is a bad idea in any case :-)

---

### Post by BuffaloX on 2009-10-29
I've been very happy with Ext4 on my old install, so now I'm going for a complete wipe of all my drives, making them all Ext4 for Karmic. :D

---

### Post by JillSwift on 2009-10-29
I chose EXT4 for my / and kept EXT3 for /home.

This allows me the efficiency boost on loading the OS and programs, while making me feel safe about writing large data files, like my videos. (Despite having a good UPS and fairly reliable power, as well as the fact that the data loss problem has become significantly rarer since EXT4 first hit the scene, I'm still worried about it.)

I expect it won't be long before I can use EXT4 all around, however.

---

### Post by twright on 2009-10-29
> **JillSwift said:**
> I chose EXT4 for my / and kept EXT3 for /home.

This allows me the efficiency boost on loading the OS and programs, while making me feel safe about writing large data files, like my videos. (Despite having a good UPS and fairly reliable power, as well as the fact that the data loss problem has become significantly rarer since EXT4 first hit the scene, I'm still worried about it.)

I expect it won't be long before I can use EXT4 all around, however.
The ext4 issues only applied to small system/config file being overwritten in a non safe way and this has been officially fixed btw. :-)

Hopefully everything should be fine now...

---

### Post by HappyFeet on 2009-10-29
> **spongypants23 said:**
> The Ubuntu 9.10 release notes made me afraid to use ext4. I'm still sitting here with ext3.

No need to be afraid. I've been using it since March with no issues.

---

### Post by HappyFeet on 2009-10-29
> **andrewabc said:**
> I get monthly power outages, and no problems yet.

Release notes spongypants is talking about:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

You don't have a UPS? (uninterruptible power supply)

---

### Post by JillSwift on 2009-10-29
> **twright said:**
> The ext4 issues only applied to small system/config file being overwritten in a non safe way and this has been officially fixed btw. :-)

Hopefully everything should be fine now...
O,RLY?

There seems to be rather a great deal of misinformation about EXT4 floating around.

---

### Post by wootah on 2009-10-29
> **JillSwift said:**
> O,RLY?

There seems to be rather a great deal of misinformation about EXT4 floating around.

I was under the impression, according the the release notes, that this issue actually applied to larges files > 500 MB.

I believe your setup seems to be quite ideal until there is definite proof as to the filesystem stablity.

Side note: I thought I briefly read a discussion saying that the developers were considering defaulting back to EXT3 until the issue is conclusively disproved or fixed. (Grain of salt)

---

### Post by JillSwift on 2009-10-29
> **wootah said:**
> I was under the impression, according the the release notes, that this issue actually applied to larges files > 500 MB.

I believe your setup seems to be quite ideal until there is definite proof as to the filesystem stablity.

Side note: I thought I briefly read a discussion saying that the developers were considering defaulting back to EXT3 until the issue is conclusively disproved or fixed. (Grain of salt)
Me too.

Oh, the uncertainty! Oh, the huge manatee! :D

---

### Post by hellmet on 2009-10-29
> **HappyFeet said:**
> You don't have a UPS? (uninterruptible power supply)
Not everyone can afford one. Not me, for sure.

---

### Post by RichardLinx on 2009-10-29
> **hellmet said:**
> Not everyone can afford one. Not me, for sure.

When I was saving for a new graphics card, I ate my breakfast cereal with a fork to save the milk.:p

---

### Post by pwnst*r on 2009-10-29
> **hellmet said:**
> Not everyone can afford one. Not me, for sure.

<$100 US.  not expensive.

---

### Post by pwnst*r on 2009-10-29
> **RichardLinx said:**
> When I was saving for a new graphics card, I ate my breakfast cereal with a fork to save the milk.:p

lol

---

### Post by Icehuck on 2009-10-30
> **pwnst*r said:**
> <$100 US.  not expensive.

It is if you are married, have children, with various bills, and are on a budget.

---

### Post by pwnst*r on 2009-10-30
> **Icehuck said:**
> It is if you are married, have children, with various bills, and are on a budget.

you probably spend that going out in one month or wasting $ on other things.  so, no, for most it's not expensive.

---

### Post by JDShu on 2009-10-30
> **hoppipolla said:**
> lol why DO you always say that? o.O



[http://knowyourmeme.com/memes/cool-story-bro](http://knowyourmeme.com/memes/cool-story-bro)

His usage was pretty fail though.

---

### Post by renkinjutsu on 2009-10-30
> **RiceMonster said:**
> Cool story bro

hmm.. =\
[http://knowyourmeme.com/photos/23547]("http://knowyourmeme.com/photos/23547")


Are the upstream kernels affected by the ext4 corruptions or is it just the kernels that come with karmic?

---

### Post by Teber on 2009-10-30
i just installed karmic. i hate to tell you there are some major issues:

- the install and the follow ups went ever so smoothly
- i too think ext4 is *FAST*
- i love the greatly improved sound quality

woot! i love karmic! :D

---

### Post by twright on 2009-10-30
> **pwnst*r said:**
> you probably spend that going out in one month or wasting $ on other things.  so, no, for most it's not expensive.
Ok then, for this month I will not go out as I am saving up for a USP... (actually I have a laptop anyway so it does not matter)

---

### Post by claymater on 2009-10-30
9.10 was the only release that I used EXT4, and I have had no problems! ;) 

Its nice and fast!!!!

---

### Post by forrestcupp on 2009-10-30
> **RiceMonster said:**
> Cool story broYes!  I always look for the obligatory "cool story bro" from RiceMonster.

> **gletob said:**
> How exactly do you always know it's a boy?What?  Everyone on the internet is a boy.

> **hoppipolla said:**
> lol why DO you always say that? o.O
It's involuntary.  He *has* to say it; just like you always have to say "lol".  :)

---

### Post by JBAlaska on 2009-10-30
I've been using XFS on 2 Mythbuntu boxes for over a year without a hickup, So I did not hesitate to install EXT4 on my main box.

After several hard resets due mainly to me messing aboot, not one problem yet.

And Yes 9.10 is FAST, not just normal fast..but uber L337 karmic fast..

---

### Post by murderslastcrow on 2009-10-30
Yeah, I thought Linux was fast before. Ubuntu, moving at the speed of thought.

---

### Post by stinger30au on 2009-10-30
> **Ijtaba said:**
> I just dont like the fact I couldnt mount it inside windows like ext3

give it time and some clever person will make a driver for this to happen

---

### Post by irishbreakfast on 2009-10-31
I am pleased that ext4 is working well for some of us. For me, I had to revert to ext3 to get rid of segementation faults when attempting to use ndiswrapper (a desktop).

---

### Post by mkendall on 2009-10-31
> **forrestcupp said:**
> What?  Everyone on the internet is a boy.

You LIE! Some are 42-year old men pretending to be 14-year old girls.

---

### Post by Icehuck on 2009-10-31
> **mkendall said:**
> You LIE! Some are 42-year old men pretending to be 14-year old girls.

These people are known as the FBI.

---

### Post by UKBB on 2009-10-31
> **pwnst*r said:**
> it's an educated guess.  very few are not "bro's" on here.

next question.

What is the airspeed velocity of an unladen swallow?

---

### Post by UKBB on 2009-10-31
> **Teber said:**
> - i love the greatly improved sound quality

I noticed that the volume level has improved too.

---

### Post by Viva on 2009-10-31
Yep, it is extremely fast with ext4.

---

### Post by hellmet on 2009-11-02
> **pwnst*r said:**
> <$100 US.  not expensive.
$100 US is half the monthly salary for many, in my country. Think out of the USA.

---

### Post by rifak on 2009-11-02
the other day i was copying about 600 mb's of data from my friend's macbook running osx to a flash drive and it took about 5 minutes (maybe a little more). i then plugged it into my macbook, running 9.10 with ext4, and it literally took about 50-60 seconds. i then tried it in reverse, copying the data from my computer to the flashdrive, then putting it on his computer, and same thing....about 45-60 seconds from my computer to flash drive with ext4, and about 5 minutes from the flash drive to his comp running osx....i was really amazed

---

### Post by forrestcupp on 2009-11-02
> **mkendall said:**
> You LIE! Some are 42-year old men pretending to be 14-year old girls.

Others are 14-year old girls pretending to be 42-year old men because they're too chicken to let people know they are 14-year old girls.  ;)

---


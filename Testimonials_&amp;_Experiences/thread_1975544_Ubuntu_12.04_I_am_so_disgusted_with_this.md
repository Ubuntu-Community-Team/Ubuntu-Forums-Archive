---
title: "Ubuntu 12.04 I am so disgusted with this"
date: 2012-05-07
forum: Testimonials &amp; Experiences
---

### Post by Ridgerunrbunny on 2012-05-07
I am about ready to go back to windows. First I upgraded to 11 and started to get black screens, so I uninstalled the Nvida and that worked, then I got bold and upgraded to 12.04 now, , NOTHING WORKS. I am not a programer geek.  When I install something or upgrade something I THINK IT SHOULD WORK! Gimp is screwed up and I don't know sudo talk or gimp talk to talk to it.  The boot loader is gone, GONE.

I have tried reinstalling itself over itself and the install disc crashes mid way.  I really am here to complain about Ubuntu and think it should get its act together for normal users to use.

Bunny

---

### Post by craig10x on 2012-05-07
if you upgraded, the chance of failure is fairly high...but if you do a fresh install the chance of success is very high...why not do a fresh install?
That is what i always do, and ubuntu always runs great...

---

### Post by goldshirt9 on 2012-05-07
instead of griping, what are your pc spec's and what exactly doesn't work :confused:
i have installed 12.04 on laptop and desktops and all is fine .

---

### Post by Version Dependency on 2012-05-07
Sounds like an upgrade gone bad...or two upgrades gone bad.  You probably should backup all your important documents and do a fresh install.

---

### Post by 3Miro on 2012-05-07
Backup and make a fresh install. Then post threads with questions with your specs and specific issues. Otherwise, this is just a pointless rant.

A new release always comes with problems. If you are not willing to deal with those, wait couple of months before upgrading or making a clean install. If you want to play really safe, you can even wait for 12.04.1 (12.04 with many bug-fixes), which will come within the next 6 months or so.

---

### Post by Tamlynmac on 2012-05-08
> goldshirt9
instead of griping, what are your pc spec's and what exactly doesn't work :confused:

Since  the OP placed their thread in the T&E, one must assume their not  looking for assistance. Considering the T&E is not a support  section.


> 3Miro
Otherwise, this is just a pointless rant.

Where  should the OP rant? After all this is the T&E. Historically, this  is even where the staff moves threads that are testimonials. There's no  reason to be defensive, it's up to the OP if they wish to rant or praise  in this section.

I just don't see any value in defensive  responses that attempt to minimize another's feedback. If one just stops  to think about it for moment, they might understand the OP's  frustration. The OP did mention they weren't a "programer geek". :wink:


> Ridgerunrbunny

Sorry  you had problems. Putting aside all the posturing, I know it's never  pleasant when an install or upgrade fails. Regardless, of which OS it  is. Not all users are familiar enough to diagnosis issues. Nor, might  they have the time to invest in doing so. It's been written here  (T&E) numerous times - Ubuntu/Linux may not be for everyone. 

If your of the nature to seek assistance, you might try starting a  thread in the support sections requesting help. But what ever decision  you make - I wish you the best of luck.

Just my $0.02

---

### Post by mastablasta on 2012-05-08
good to test it live before doing an upgrade or install.
 
you would find that nvidia has some bugs, but are working on it. not really ubuntu's fault....
also if you use proprietary drivers they need to be uninstalled and purged before doing the upgrade. i am not sure why the os doens't do this automaticly or at least ignore the old ones (like Windows does it). but i guess that is not how linux works. and linux will use bits form the old drivers and combine them with new making a mess.

---

### Post by 3rdalbum on 2012-05-08
I usually fresh-install, unless I can't be bothered to and am sure that everything on my computer is fairly well "stock".

With today's Ubuntu installer preserving the /home directories even when they're on the / partition, it's almost as easy to do a fresh install (preserving your home folder and all settings) as it is to do a dist-upgrade.

---

### Post by Ridgerunrbunny on 2012-05-09
I have a triple boot computer, ah, had a triple boot computer with two hard drives. One partition houses a Hackintosh, another windows, and two house Ubuntu. I also have several storage partitions.  I reinstalled a second ubuntu in one of the smaller partitions. The Ubuntu partition I want to work houses all the stuff I want to work with. They are still in that partition. I have tried to install back into that partition only to have the installer tell me that there is a problem with the boot loader. It does not work When I try to load that hard drive all I get is Grub Rescue>. I don't know how to write code for grub rescue, much less in a terminal.  I thought about backing up the 12.04 partition but do not know how to that from a 11.?? partition. Explain please.

---

### Post by geekydownloads on 2012-05-09
I have used ubuntu for some time, started with 8. Last was 10.10 which I am very pleased with. I have websites and photography plus need to mess with various windows so use virtual box. I wouldn't say I was an expert on Ubuntu etc but I expect I am more wised up than some 'computer users'. I have never had any problems loading Ubuntu on to various computers and can usually figure out problems.

I have just wasted hours putting Ubuntu 12 on a laptop which I had hoped would retire my old set up. Why have all the places/settings changed? It takes a little while to find your way around a new operating system but I had done so and saw no reason to change. But if I stay with Ubuntu I have to learn it all again! I have no reason to stay with Ubuntu, I may just as well try something alse which I will have to learn.

I cannot see the point in changing things that were working and that people were used to, it wasn't broken so why the attempt to fix it. I retro fitted gnome but whats the piont? I can spend the rest of the day poncing about or go somewhere else! I used to be able to say it was quicker and easier to load an Ubuntu OS than windows but not anymore!
GGRrrrrrrrrr

---

### Post by Version Dependency on 2012-05-09
> **geekydownloads said:**
> I cannot see the point in changing things that were working and that people were used to

If we refuse to embrace change, our desktops would still look like this:

[IMG]http://toastytech.com/guis/win31progman2.png[/IMG]

P.S.  You don't have to relearn anything in 12.04.  Install Gnome Fallback (takes a few seconds) and you will get the old Gnome-2 style desktop as a login option.

---

### Post by Shadius on 2012-05-09
> **Version Dependency said:**
>  P.S.  You don't have to relearn anything in 12.04.  Install Gnome Fallback (takes a few seconds) and you will get the old Gnome-2 style desktop as a login option.

As Version Dependency stated, you could get back to the familiar Gnome 2 environment. I think there are a few ways of doing this, I used the Gnome Tweak Tool application and chose Gnome Classic from the login menu. I think you can also do it in Terminal by running: 

```
sudo apt-get install gnome-session-fallback
```

Correct me if I'm wrong about the command.

---

### Post by Ridgerunrbunny on 2012-05-09
well, that didn't work.

---

### Post by Shadius on 2012-05-09
> **Ridgerunrbunny said:**
> well, that didn't work.

When you're at the login screen, select the Ubuntu Logo and choose the session you'd like to log into. It should give you with option such as Gnome, Gnome Classic, etc..

---

### Post by cariboo on 2012-05-09
@Ridgerunrbunny, if you want to solve your problem, I'd suggest you start a thread in the support section, as this isn't the right place for solving problems. 

Please provide us with a link when you've done so.

---

### Post by iMurshaq on 2012-05-09
And this is why I'm clinging desperately to my 10.04 Lucid.

---

### Post by Antman on 2012-05-09
> **Ridgerunrbunny said:**
> I am not a programer geek.

Really?!? :-k
> **Ridgerunrbunny said:**
> I have a **triple boot computer**, ah, had a triple boot computer with **two hard drives**. **One partition houses a Hackintosh**, another **windows**, and **two house Ubuntu**. I also have **several storage partitions**. I reinstalled a second ubuntu in one of the smaller partitions. 

:-k
 ok, the verdict is in... you ARE a programmer geek. :lolflag:

> **Ridgerunrbunny said:**
> I really am here to complain about Ubuntu and think it should get its act together for **normal users** to use.


---

### Post by |{urse on 2012-05-09
> **iMurshaq said:**
> And this is why I'm clinging desperately to my 10.04 Lucid.

I personally think Lucid was the sweet spot also ;) I still run it on a couple critical systems. I'm beginning to love natty. You should have seen the rash of "Omg upgrade killed my stuffs" and "What the heck happened to my gui?" then.

Industry marches forward. lol

---

### Post by Morbius1 on 2012-05-09
> **Antman said:**
> Really?!? :-k

> Originally Posted by **Ridgerunrbunny**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11914832#post11914832")                 
                 *I have a **triple boot computer**, ah, had a triple boot computer with **two hard drives**. **One partition houses a Hackintosh**, another **windows**, and **two house Ubuntu**. I also have **several storage partitions**. I reinstalled a second ubuntu in one of the smaller partitions. *
 ok, the verdict is in... you ARE a programmer geek. :lolflag:
There seems to be a misconception about being a programmer and maintaining or troubleshooting an operation system.

Some of you might not know this but humans have a techweenie gene. It has 3 states:

Off - this is the state that it's in in the vast majority of humans.
System Admin
Programmer

Sometime because of excessive radiation or because of a mating between a Sys Admin and a Programmer ( almost never happens ) a person is born with with the last 2 states enabled at the same time. Usually though it's either one or the other. Most of us here have the Sys Admin state enabled. I can tell you from personal experience that those folks that have the Programmer state enabled become lousy Linux ( or any OS that's acting up ) users because they are much like small children expecting the platform that they use to do their thing to just work. In the real world programmers - especially those in product development - are under incredible pressure to meet deliverable dates so paying customers won't leave. If there is a problem with their system they escalate the problem until the Sys Admin just comes in and re-images their system.

---

### Post by Antman on 2012-05-09
> **Morbius1 said:**
> 
Sometime because of excessive radiation or because of a mating between a Sys Admin and a Programmer ( almost never happens ) a person is born with with the last 2 states enabled at the same time. Usually though it's either one or the other. Most of us here have the Sys Admin state enabled. I can tell you from personal experience that those folks that have the Programmer state enabled become lousy Linux ( or any OS that's acting up ) users because they are much like small children expecting the platform that they use to do their thing to just work. In the real world programmers - especially those in product development - are under incredible pressure to meet deliverable dates so paying customers won't leave. If there is a problem with their system they escalate the problem until the Sys Admin just comes in and re-images their system.

yEAH... I see that at my job everyday.

---

### Post by arunb on 2012-05-10
12.04 is definitely much better than the previous versions.

I could transfer files to my ipad using 12.04, this is really surprising

---

### Post by technomooney on 2012-05-10
> **Ridgerunrbunny said:**
> I have a triple boot computer, ah, had a triple boot computer with two hard drives. One partition houses a Hackintosh, another windows, and two house Ubuntu. I also have several storage partitions.  I reinstalled a second ubuntu in one of the smaller partitions. The Ubuntu partition I want to work houses all the stuff I want to work with. They are still in that partition. I have tried to install back into that partition only to have the installer tell me that there is a problem with the boot loader. It does not work When I try to load that hard drive all I get is Grub Rescue>. I don't know how to write code for grub rescue, much less in a terminal.  I thought about backing up the 12.04 partition but do not know how to that from a 11.?? partition. Explain please.

the really interesting thing about any mixed *intosh system is that Darwin is a REALLY finicky boot loader and if the *insosh sees there ANY issue with any of the boot configs that is not a apple stock config, then it throughs a fit... 

anyway if u had tryed to install the latest kernel and grub release on your previous Ubuntu installation u sould beable to use that version of grub to "look" at the other partition and boot the vmlinuz file and initrd.img from that installation.... at least that is my understanding for booting from grub rescue

this might help too [ Grub rescue from live Ubuntu CD]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html") :idea:

---

### Post by pete04 on 2012-05-10
> **technomooney said:**
> the really interesting thing about any mixed *intosh system is that Darwin is a REALLY finicky boot loader and if the *insosh sees there ANY issue with any of the boot configs that is not a apple stock config, then it throughs a fit... 

anyway if u had tryed to install the latest kernel and grub release on your previous Ubuntu installation u sould beable to use that version of grub to "look" at the other partition and boot the vmlinuz file and initrd.img from that installation.... at least that is my understanding for booting from grub rescue

this might help too [ Grub rescue from live Ubuntu CD]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html") :idea:

Only time I ever had a boot issue with ubuntu involved a dual boot with OSX.

---

### Post by Ridgerunrbunny on 2012-05-10
Sorry, Grub is not working A Tall. I go from the on button right into 12.04, no log on screen. If I want to go into Windows I have to change my bios to get there, if I want to go back to linux I have to go into them again. I have not even tried getting into my mac partition but I have a mac startup disc, hopefully it would work if I wanted to go there. I have no idea how to get grub started its there. The only thing I can think of is that the windows mbr is screwed and preventing bootup. But I don't remember where the dammed thing is located or how to rewrite it. Grub recognized all three of my drives for years now it's gone and refuses to come back. I even formatted the partition I thought was the culpert. Lost all my programming, pass words, everything, it's all gone. I put 12.04 in another partition and am sorely disgusted with it.  There is no start up manager like the old version. gawd. At least I was able to move my precious file folders around before dumping 11.

---

### Post by johnnybgoode83 on 2012-05-11
Nothing works, OP?  I must be a genius because everything works for me :lolflag:

---

### Post by Tamlynmac on 2012-05-11
> johnnybgoode83
Nothing works, OP?  I must be a genius because everything works for me 

I seriously doubt this will improve the OP's experience. Ask yourself, if you had a car accident and a bystander says "to bad, I've never wrecked my car" then laughs - how would you react? I know my reaction would consist of a few expletives that were focused directly at the bystander.

Just because something worked for me, doesn't necessarily apply to everyone else. Joking at other users issues might suggest we can't relate. As a community, I think we should make a conscious effort to understand and show some concern. It's my opinion that when we defensively posture or laugh at those who struggle, all we're doing is acting in an elitist manner.


> Ridgerunrbunny

If you need assistance, I strongly suggest you heed the advice of[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") cariboo907:
> @Ridgerunrbunny, if you want to solve your problem, I'd suggest you  start a thread in the support section, as this isn't the right place for  solving problems. 

Please provide us with a link when you've done so.

It's quite possible, if you continue seeking assistance or implying that your seeking assistance in this section - the staff may close this thread.

As for the defensive posturing, IMHO it's just part of the T&E experience. If one would simply ignore the posturing and heed the advice, they might find a solution. If your just ranting, then I doubt you'll find much sympathy here. I really do wish you the best of luck with whatever decision/choice you make.

Just my $0.02

---

### Post by Luxx on 2012-05-12
> **Morbius1 said:**
> There seems to be a misconception about being a programmer and maintaining or troubleshooting an operation system.

Some of you might not know this but humans have a techweenie gene. It has 3 states:

Off - this is the state that it's in in the vast majority of humans.
System Admin
Programmer

Sometime because of excessive radiation or because of a mating between a Sys Admin and a Programmer ( almost never happens ) a person is born with with the last 2 states enabled at the same time. Usually though it's either one or the other. Most of us here have the Sys Admin state enabled. I can tell you from personal experience that those folks that have the Programmer state enabled become lousy Linux ( or any OS that's acting up ) users because they are much like small children expecting the platform that they use to do their thing to just work. In the real world programmers - especially those in product development - are under incredible pressure to meet deliverable dates so paying customers won't leave. If there is a problem with their system they escalate the problem until the Sys Admin just comes in and re-images their system.

I am so adding this to my signature in my emails. :p

---

### Post by SeijiSensei on 2012-05-12
> **Ridgerunrbunny said:**
> Sorry, Grub is not working A Tall. I go from the on button right into 12.04, no log on screen.

Try holding down the Shift key while booting.

---

### Post by kohoutek1 on 2012-05-12
>  If we refuse to embrace change, our desktops would still look like this:

[IMG]http://toastytech.com/guis/win31progman2.png[/IMG]


Cute, quaint. What OS is that? Amiga? ;)

>  P.S.  You don't have to relearn anything in 12.04.  Install Gnome Fallback (takes a few seconds) and you will get the old Gnome-2 style desktop as a login option.No, you won't. You'll have to start...all...over...again. (Really... Fallback is GNOME 3, not 2, just not "shell")

---

### Post by Tamlynmac on 2012-05-12
> kohoutek1
Cute, quaint. What OS is that? Amiga?

No, it's definitely Windows. Looks like maybe 3.0 or 3.1

When put in perspective (if it is 3.0/3.1), it was a significant  improvement over 2.03 and a welcomed upgrade. If I recall correctly,  seems most of my configuring time in early Windows was spent setting up  com ports - IRQ's and hardware addresses.

The good old days weren't always that good. As in "Blue Screen" (which I  believe started with 3.0 or 3.1), to this day I refuse to use blue on  my desktop. Gee, I wonder why. :lolflag:
* I'm not bashing Windows, as in it's time it was quite unique and attracted many to PCs. The GUI (no matter how unstable) was something many non-tech users back then could adopt. For those who didn't understand DOS, the graphic user interface helped them to accept and make use of a PC. Regardless of present opinion, Windows did help many a user accept and adopt computer technology.

Just my $0.02

---

### Post by Deadman390 on 2012-05-12
i honestly am not sure if this is where this problem belongs but it involves 12.04 lol.....i upgraded and got everything done HOORAY!!!!! and as expected my wireless card did not work (wna3100 Netgear N330) so i went back to the last time this happened (after 1k posts and very helpful ppl i finally understood enough to get it to work lol) and now it has went to **** again.....i checked with ndiswrapper if the driver was there it is there and present and installed and all that lovely stuff but apparently it will not work......i am confused on the next step

sorry bout everything but i am slowly understanding linux 1 frustrated evening at a time lol

---

### Post by Version Dependency on 2012-05-12
> **Deadman390 said:**
> i honestly am not sure if this is where this problem belongs...

No, the Testimonials forum is not where to post threads for help.  You want to post in one of the support forums for that, where it will receive alot more attention.

---


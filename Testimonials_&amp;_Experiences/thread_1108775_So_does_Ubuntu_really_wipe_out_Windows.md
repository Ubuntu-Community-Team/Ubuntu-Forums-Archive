---
title: "So does Ubuntu really wipe out Windows"
date: 2009-03-28
forum: Testimonials &amp; Experiences
---

### Post by windows22 on 2009-03-28
Hi 

I chose to install Ubuntu 8.04 when running the Live CD. The CD autoplay said this would let me choose to install Ubuntu to run alongside Windows. 

When I installed there was of course no help. A partition program started and I left the default on (guided). I assumed I as going to choose to install alongside Windows but instead got a warning that partitioning could delete data. There was no choice but to go ahead or abort. Went ahead, install failed at 24% so started again, chose single guided partition , install "worked" but zero about Windows. Both times I installed Ubuntu on same drive as Windows C:...

So Windows was wiped out and so was the data on C.  At least I think so. Windows sees a residual 1.24 GB partition that I had to create to install Windows on D:... Gparted sees only the Ubuntu partition that I suppose does not have the old files on C: from when Windows was installed. 

So I think you d agree Ubuntu is simply too dangerous too install with Windows, and could learn from Windows in helping users set up. Correct?        
 

Thanks

---

### Post by tuskenraider on 2009-03-28
if you were looking for an easy way to install ubuntu without all the hassle of gparted.  just use wubi and install it in windows.  It acts just like a dual boot setup and when your done with ubuntu go to add/remove programs in windows and uninstall it.  

For new peoples being exposed to ubuntu thats the best way to handle it  IMO.

Tusken.

---

### Post by lisati on 2009-03-28
I think you might have used "Guided - use entire disk". If that is the case, then Windows would truly be gone. One of the "correct" ways of installing Ubuntu along side Windows is to use the "Guided - resize partition" option.

Edit: As Tuskenraider has observed, using "Wubi" is often a safer method while you're finding your way around.

---

### Post by anon642 on 2009-03-28
I chose 8.10 and used the Live CD and just chose to install Ubuntu inside Windows (the wubi way).  Whenever I start my computer it lets me choose Windows or Ubuntu. Looks like a partition but not really. If I add/remove programs in Windows I can see 15GB of Ubuntu ready to be uninstalled.  However, I've only used Ubuntu for a few days and love it. I'm about ready to completely wipe windows and do a complete install of Ubuntu.

---

### Post by Elfy on 2009-03-28
> There was no choice but to go ahead or abort.  When I first installed, I wasn't too sure about the choices - so I aborted, twice, while I checked on the internet.

If you weren't sure why did you go ahead?

As above wubi can be a simple introduction, but that said why didn't you look for some confirmation before you proceeded.

> could learn from Windows in helping users set up. Correct? Not in my opinion - I've never had a ny help from windows when I've set it up.

---

### Post by starcannon on 2009-03-28
My response to these tragedies is, and be sure I am sympathetic, but...

[LIST=1]
[*]One should never fiddle with ones HDD unless one has backed up anything important.
[*]One should read all dialogue boxes thoroughly, move forward only when one understands what the dialogue boxes mean.
[*]One must be responsible for ones own clicking.
[*]Ubuntu does not "wipe out Windows"; however, it is sometimes possible that people who are very excited about trying a new OS may click through a dialogue box without having thoroughly read, or completely comprehended what its meaning is.
[/LIST]
There are remedies to the situation of having accidentally chosen the wrong partition scheme when installing Ubuntu, my personal favorite being [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk"); and, while being an excellent utility for recovering lost data, it will take more time to do so than reading a dialogue box or asking a question or 2 before proceeding.

Best of Luck.

---

### Post by Sef on 2009-03-28
There are a number of tutorials on how to dual boot.   As has been stated, it is best to ask to make sure you understand before dual booting.

---

### Post by 3rdalbum on 2009-03-28
> **windows22 said:**
> 

So I think you d agree Ubuntu is simply too dangerous too install with Windows, and could learn from Windows in helping users set up. Correct?

Not correct, not correct at all. I've set up dual-boots without data loss just by using the ordinary installer. The difference is, I chose the right options.

What could Ubuntu learn from Windows in this regard? Windows Vista's installer has a partitioner, but Windows will not set up a dual-boot no matter what buttons you press.

---

### Post by WatchingThePain on 2009-03-28
Both can be on the same disc with no problems if you know how to partition properly.
The WUBI would definitely have been a better option for you.

---

### Post by t0p on 2009-03-28
> **windows22 said:**
> There was no choice but to go ahead or abort. Went ahead...

...okay

> **windows22 said:**
> So I think you d agree Ubuntu is simply too dangerous too install with Windows, and could learn from Windows in helping users set up. Correct?        
 
...okay

> **windows22 said:**
> 
Thanks

No, thank *you*! (troll)

:p

---

### Post by xpod on 2009-03-28
> Re: So does Ubuntu really wipe out Windows

Yes,of course.
If the user instructs it to do so.

---

### Post by Tony Flury on 2009-03-28
Clearly - if you look at the thousands (or more) people who have installed dual boot Unbuntu with windows without a single hiccup, it is not the case that Ubuntu is "too dangerous".

What is dangerous (as people have said) is moving forwards, without actually understand what you are doing.

Bear in mind that a large number of OEM Windows Disks will simply just wipe the entire HDD and start again (and if it doesn't it will wipe any non Windows boot loader) - so it might actually be that Windows is "too dangerous" to install along side Ubuntu.

> 
There was no choice but to go ahead or abort. Went ahead...

You had a choice - you could have aborted ... gone back to previous Dialog and read it fully.

Even using the Guided partition option it would have preserved your Windows partition and set up a lovely dual boot system.

---

### Post by presence1960 on 2009-03-28
Ubuntu is not dangerous, it is the operators of the computers who are dangerous. 
My first try at Ubuntu I did no prep work. I did not read any of the excellent tutorials on how to install and set up a dual boot. So I did what you did, I used the guided install-use entire disk. Ubuntu installed ok, but then I didn't like it or so I thought. So I removed Ubuntu with gparted and at that point I still didn't realize Windows was written over. I restarted my machine and boy was I mad. Initially I was mad at Ubuntu but after a while reality settled in. When I finally decided to give Ubuntu another try I did a lot of reading to make sure I knew what I was doing. The result was a successful dual boot installation with no data loss. Like me you are going to have to chalk it up to experience. It is not Ubuntu's fault, as there is more than ample documentation on the matter. The problem is we don't bother to read it.

---

### Post by bapoumba on 2009-03-28
Moved to Ubuntu Testimonials & Experiences.

---

### Post by Yownanymous on 2009-03-28
Note how the OP has never replied again. They're most probably a troll...

---

### Post by Mr. Picklesworth on 2009-03-28
This did make me realize that Ubiquity at the moment lacks a Help button on the bottom left for quick access to the detailed documentation. (You'll notice many other applications do). I wonder if there's a wishlish item filed for that?...

Aha! [https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/114521](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/114521)

---

### Post by Tamlynmac on 2009-03-28
> Mr. Picklesworth
This did make me realize that Ubiquity at the moment lacks a Help button on the bottom left for quick access to the detailed documentation. (You'll notice many other applications do). I wonder if there's a wishlish item filed for that?...

Logic might suggest when installing a new operating system that one investigate said system prior to installation. As many have pointed out "why push the button if you don't know what you're doing?". Then complain after it doesn't do exactly what you want. I don't understand why Ubuntu can't read peoples mind.

If the OP really did experience this issue, it again exemplifies the lack of time invested in learning the OS prior to install. I can't imagine how dysfunctional the system would quickly become, if the OP continues **not** learning the new OS and expects it to be just like Windows.

I would recommend to all that wish to install Ubuntu - Please learn about the OS prior to making a decision. Don't just assume it's a Windows clone. I believe to many think that changing their OS is a slam dunk, only to find out later that they have issues.

---

### Post by Chemical Imbalance on 2009-03-28
Troll Detector 2000 going off!

---

### Post by caravel on 2009-03-28
Labelling people as "trolls" is not helpful.  He may or may not be, though giving the benefit of the doubt is probably the best policy to avoid offending.

Personally I think installing an OS is a serious matter and if you're installing one then you need to be sure of what you're doing.  For example if you have a nice Linux setup and you decide to install Windows alongside it, don't count on Windows to install a nice bootloader and leave your Linux partition untouched.

The same goes for those installing a Linux distribution.  Ubuntu is not a program that you're trying out, it's a whole different OS.  If you wanted to try Ubuntu then the best way is to use the liveCD or install it on another PC that does not contain any important data.  Do not simply trust the software to do the right thing for you and your particular setup when using the default settings, as that way leads to big disappointent.  You as the user are responsible for your PC and what gets installed and run on it.

---

### Post by Bios Element on 2009-03-28
> **caravel said:**
> Labelling people as "trolls" is not helpful.  He may or may not be, though giving the benefit of the doubt is probably the best policy to avoid offending.

The OP is just a troll. Now with that in mind, I'm more then happy to apologize for calling the OP a troll if he actually comes back and responds. But making a one shot post and running off never to return is just being a troll. No one gains anything and everyone wastes their time trying to help someone who won't be back.

---

### Post by Chemical Imbalance on 2009-03-28
My reasons for thinking he is a troll is

+this is his/her only post
+the name includes "windows"
+no replies
+states linux is "dangerous"
+the post is inflammatory

What else do you want?  Its my strong suspicion.

My apologies if the poster is in fact not a troll.  It just seems highly likely to me.  This is a public forum, subject to human behaviour.  I have the bad habit of blurting out stuff before I think sometimes. :)

---

### Post by betrunkenaffe on 2009-03-28
Mod lock thread now yes?

---

### Post by presence1960 on 2009-03-28
> **Bios Element said:**
> The OP is just a troll. Now with that in mind, I'm more then happy to apologize for calling the OP a troll if he actually comes back and responds. But making a one shot post and running off never to return is just being a troll. No one gains anything and everyone wastes their time trying to help someone who won't be back.

If that qualifies one as a troll then maybe I am a troll also. I have solved all my problems by reading through the forums. How do we know this person is or is not reading our responses. I have never had to create a thread to find an answer to my problems, and Lord knows I have had them. Besides even if the OP is not for real at least our ideas and advice are now on the forum available to others who may need the help in this area. There is one thing about helping people - you never really know who it is that you are going to help. So be helpful as much as possible even to those you may not like.

---

### Post by ugm6hr on 2009-03-28
> **Mr. Picklesworth said:**
> This did make me realize that Ubiquity at the moment lacks a Help button on the bottom left for quick access to the detailed documentation. (You'll notice many other applications do). I wonder if there's a wishlish item filed for that?...

I suspect if someone fails to read the:
**Guided - Use Entire Disk**

They are equally unlikely to use a help page.

This does appear to be a problem for a few people, judging by the "Ubuntu erased my Windows" posts we see from time to time.

Perhaps it would be best if the default was "Guided - Resize xxx and use freed space" since most people who intend to install Ubuntu as a sole OS will likely know what they are doing.

---

### Post by caravel on 2009-03-28
> **Bios Element said:**
> The OP is just a troll. Now with that in mind, I'm more then happy to apologize for calling the OP a troll if he actually comes back and responds. But making a one shot post and running off never to return is just being a troll. No one gains anything and everyone wastes their time trying to help someone who won't be back.
Though perhaps he now has no inclination to return after seeing some of the hostility here?

---

### Post by Hobgoblin on 2009-03-28
Bitching aside....

> **windows22 said:**
> 
When I installed there was of course no help. A partition program started and I left the default on (guided). I assumed I as going to choose to install alongside Windows but instead got a warning that partitioning could delete data. There was no choice but to go ahead or abort. Went ahead, install failed at 24%
It sounds like you took the right option but the repartition failed.  Most of the time this works fine but there is always a chance it won't hence the warning, which you should have heeded and gone back to Windows and backed up your data.

>  so started again, chose single guided partition , install "worked" but zero about Windows. Both times I installed Ubuntu on same drive as Windows C:...


By this point I think your Windows partition may have been unusable anyway due to the failed repartition.  So Ubuntu did what Windows would do in the same situation, and wiped the whole lot.

---

### Post by skintythe1andonly on 2009-03-28
I have a friend who did the same. He just clicked Next->Next....->Next as windows teaches you. The thing is I think is that the Ubuntu installer makes it nearly too easy to install, some just do not pay enough attention. 

One possible remedy to this is to not have the "Guided-Use entire disk" as the default highlighted when people come to this section. Those who have done this loads of times before know what they are doing and prob already have done a manual partition. 

Have none highlighted to start with, so they cannot just click next.... force the noobs to make a decision and not have their hand held at this section as it is better in the long run,

---

### Post by windows22 on 2009-03-28
No I am not a troll, just need some time to reply.

Actually I am fairly savvy - everything was backed up and Windows was due for reinstall. I tried live CD beforehand. Best would have been to install Ubuntu on D:\ and leave C:\ to Windows, but I did not believe Ubuntu would really make it easy to install alongside Windows on the same disk, for a casual user who did not do the homework, and I thought "let's just see". Sadly I was proved right.

Two people suggested it would be best if the default was "Guided - Resize xxx and use freed space" since most people who intend to install Ubuntu as a sole OS will likely know what they are doing. Totally agree - is not the most important "market" converts from WIndows? Also agree about no help button, and I did not see what a "guided" install meant. Surely the expectation is that Ubuntu is going to partition the free space, and if you have that preconception "use entire disk" is pretty ambiguous - does it mean it will make a partition for Windows? Likewise the "you will lose data warning". 

And yes when I reinstalled Windows I believe it was far more transparent about what partitions were where, where free space was, and that some partitions contained other operating systems. 

Was there a specific help link when you autoplay the Ubuntu CD for each of the different types of install? 

I'll certainly be keeping Ubuntu (alongside Windows) - could I have a link on how to upgrade to 9.04? I think I need that to run later versions of some software I like.   

I will say the major impression I get of Ubuntu so far is how visually ugly it is compared to Windows and Mac. Is this the fault of GNOME (if it should be described as a fault?)  


Thanks, all

---

### Post by Chemical Imbalance on 2009-03-28
You can get Jaunty here:

[http://mirrors.gigenet.com/ubuntu/9.04/](http://mirrors.gigenet.com/ubuntu/9.04/)
You will probably want the 1386 desktop .iso or the amd64 desktop .iso if you have a 64bit capable processor.

Be careful with the partitioning! 

Here's a guide on partitioning in Ubuntu:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Mr. Picklesworth on 2009-03-28
Thanks for your interest, win22!

One thing you should be aware of is that drive letters are a horrible Windows thing which must be forgotten immediately. Typically, Windows's main partition (with C:\) is sda1 (maybe hda1), then subsequent partitions (in order) on the disk are numbered from there, eg: sda3 is the partition I mount as /home. In Linux, there is just one root directory (/) and any disks appear mounted within that instead of getting some global letter designated to it. For example, /home is actually a completely different disk and a flash drive I insert appears in /media/disk1.
My external hard drive is referred to as sdb, again with two partitions: sdb1 and sdb2.
You'll notice that instead of LETTER: before every file path, we have stuff like file:, ftp: and http:

Another thing Ubiquity *could* do is autodetect what the drive letters for partitions are under Windows' perspective. I've added to my "things to pester developers to make" list :)


As for ugliness, try playing with it. You can get it to look quite beautiful with some playing, and the end result is quite satisfying since it can easily fit how you want to work!

Personally, I don't think GNOME is at fault there at all. It's just that Ubuntu's default theme so far (and often its desktop background, 8.04's being a nice exception) tends to be fairly basic. Check out the options (in main menu) under System Preferences -> Appearance. The appearance is super customizable right out of the box. And no, not just the colours. You can change fonts (and font SIZE) however you please, you can change toolbar styles to have just icons or just text, you can have configurable menu accelerators (shortcut hotkeys) - super cool... all sorts of awesome stuff.

There are lots of themes over at [http://www.gnome-look.org](http://www.gnome-look.org)
"Shiki Colors" is a popular one.


One thing I'm going to mention, which I try to do all the time for new users (just to be safe): Check out Applications -> Add / Remove if you want to install any software (or look in System Administration -> Synaptic Package Manager).


For upgrading to 9.04, the updater will let you know as soon as 9.04 comes out and offer to upgrade. If you want to upgrade early, to the beta, run "update-manager -d" (which you can do in the Run Program dialog, easiest opened by pressing Alt F2). 
Or, you can take a look here! [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by betrunkenaffe on 2009-03-28
fyi. 

Windows XP installer is very clear, you can delete partitions (without knowing what they are, just their size) in order to install. No resize option to confuse, no option except delete and go (because no one ever needs more than 2 options for any choice).

Windows Vista was too complex, it let me specify the size of the partition I am making for Windows as well as delete.

Given the above 2 options, seems like you are comparing apples to oranges. Microsoft doesn't give you any choices on how you want to set up your hard drive. Their partitioner is NOT robust at all, the Linux installer isn't perfect but at least you can customize things.

---

### Post by presence1960 on 2009-03-28
>    

I will say the major impression I get of Ubuntu so far is how visually ugly it is compared to Windows and Mac. Is this the fault of GNOME (if it should be described as a fault?)  


Thanks, all

The default theme is very customizable unlike Windows. I was tired of the blue thing so I chose this theme. I hate the default Ubuntu theme also. But it's distaste to me forced me to look into ways to customize my look. There are so many wallpapers, themes, icons etc on [http://www.gnome-look.org/](http://www.gnome-look.org/)

BTW, this screenshot is from Linux Mint 5, because that's what I am logged into right now.

---

### Post by Hobgoblin on 2009-03-28
> **windows22 said:**
> 
I did not believe Ubuntu would really make it easy to install alongside Windows on the same disk, for a casual user who did not do the homework, and I thought "let's just see". Sadly I was proved right.

I have given a few not too tech savvy people an ubuntu boot disk and they have installed it alongside Windows with no problems.

> Two people suggested it would be best if the default was "Guided - Resize xxx and use freed space" 

That has been the default for the Ubuntu installer on every dual boot system I have set up.  Even where a current install of Ubuntu has existed it has offered to resize the Windows partition.

I think there may have been an issue with your Windows partition which caused the resize to fail and leave the partition unusable.

Try installing XP on a system with only Linux installed and see how much of a "better" job that does. :lolflag:

---

### Post by hyper_ch on 2009-03-29
> **betrunkenaffe said:**
> Windows XP installer is very clear, you can delete partitions (without knowing what they are, just their size) in order to install. No resize option to confuse, no option except delete and go (because no one ever needs more than 2 options for any choice).

But then, how many people have ever installed windows from scratch. If one did I don't think they would have trouble with ubuntu installer.

Just my 2 cents.

---

### Post by SonicSteve on 2009-03-29
> **windows22 said:**
> Hi 

So I think you d agree Ubuntu is simply too dangerous too install with Windows, and could learn from Windows in helping users set up. Correct?        
 
Thanks

1. Wubi makes it nearly brainless.

2. Installing any OS can be dangerous if your understanding of partitioning is in doubt. Installing multiple windows OS's is possible but if you don't really understand partitioning you'll be more likely to blowup all previous installations and end up with only the most current OS you installed.

Installing Ubuntu along side windows is in no way dangerous, you do need to have a firm grasp of Windows and Linux partitioning to do it safely though.

Lastly I don't understand the last part of this question. My experience is that a Windows OS installer offers absolutely no help at all to someone who needs it. If you don't know what your doing before you start you won't get any help at all from the installer.

---

### Post by brayden13 on 2009-03-29
I see a massive sign saying "DO NOT FEED THE TROLL" maybe i should follow what it says :P

Haha anyway what that person did was common human stupidity. I was lucky i didn't flick through. I was so nervous i was reading through every dialogue box 30 times until i fully understood it. and i didn't mess up once. anyway but htis guy rushed. he thought no matter what i do i will not bugger up. and guess what happened.

---

### Post by windows22 on 2009-04-03
Thanks Mr Picklesworth. When installing Ubuntu I gathered which disk was which by the size. Like I said what really would have helped is links in the CD autoplay to the different types of install that are mentioned there. I would have read those even though I was deliberately seeing if Ubuntu would let me easily mess up. 

I redid Windows install on C:\ (as Windows calls it) and Ubuntu on D:\ and dual boot works fine. First job was to install Flash player in Firefox. It seemed to need Terminal, so dunno how easy that would be for some Windows users. Generally, installing apps (via the menus) is more pleasant than on Windows, I think.

May be back with some more questions if I can't find the answers elsewhere. Next task is compiling a program called Audacity (there is an rpm but I like to have the latest changes). 
Succeded in compiling dev version of wxGTK which is a necessary precursor.

Thanks

---

### Post by Mr. Picklesworth on 2009-04-03
Flash player can be done in Add / Remove Applications (or Synaptic package manager) as well. People often give directions with the terminal since it's easier to copy and paste to get things done quickly. Handy thing to use, anyway; the Bash shell used for the terminal is, to this day, one of the most pure and flexible user interfaces out there. Play with the Tab key (don't be afraid to autocomplete anything!) and you'll learn to love it as well ;)

Glad it works! I had trouble getting Feisty alongside Windows Vista; it would kill the filesystem when it resized, so I had to go in the same order you did. (Could never decide whose fault that was). I learnt then that it's best to never, ever trust a filesystem operation by anything but its 'home' OS.

---

### Post by betrunkenaffe on 2009-04-03
I think someone believes my post to be a serious statement of my English skills.

I was more pointing out the lack of functionality in the Windows installers (and thereby the only way it could be clearer is by giving you no option)

---

### Post by ubuntu27 on 2009-04-03
> **windows22 said:**
> 

First job was to install Flash player in Firefox. It seemed to need Terminal, so dunno how easy that would be for some Windows users. 

Thanks

You can just visit a site that requires Flash and Mozilla Firefox will prompt you to install Flash plug-in if you don't have it installed.

---

### Post by brayden13 on 2009-04-03
or you could just go to [http://www.adobe.com/flashplayer/]("http://www.adobe.com/flashplayer/")

You will be redirected to the page to install flash player and the site should detect you are using linux and install the appropriate flash player for it.

---

### Post by skintythe1andonly on 2009-04-04
you can install pretty much everything you need in the add-remove programs including flash. This is better than the windows version which doesnt have the add functionality.

The reason you are going to get terminal commands when you google these sort of things as its a lot harder to go wrong when you type something into the command line. it looks a little harder but is more direct and gives more feedback if there is problems

---

### Post by Naz_Farooq on 2009-04-04
If you had some suspects in your mind, you should have consulted before you went ahead or you could have saved your data from c:/ or d:/ before doing anything to your PC.
I am running 3 boots; Ubuntu 8.10, WindowsXP and Kubuntu 8.10 within WindowsXP. And there is no problem at all. It awesome as three are working properly.
:guitar:

---

### Post by stalkingwolf on 2009-04-04
When i did my first dual boot ( RH8 & Win98SE) i spent 6 months checking and rechecking compatibility, and then it was much more critical than now.
There was no live CD, it was possible that everything from the monitor back
would not work.  In those days of dialup it was the exception if your internal modem worked.  In that time there were few if any forums like this.
If you did find one the most common reply was RTFM.  Of course before you could do that you had to be conversant in at least 2 other dialects of computerese.  and proficient with CLI.

Now onward,
> And yes when I reinstalled Windows I believe it was far more transparent about what partitions were where, where free space was, and that some partitions contained other operating systems.

as far as my experience goes win will not even read a linux drive with out the installation of a special application. In fact if you pre partition a drive with a linux partition win will tell you that the drive is bad and abort the install.  all partitions must be win partitions or no install.

> Typically, Windows's main partition (with C:\) is sda1 (maybe hda1), then subsequent partitions (in order) on the disk are numbered from there,
I believe this is wrong.  In my experience all linux distros begin numbering with 0, the first bootable partition on the first drive would be HDA0, the second **drive** would be HDB0.  The SDA designation refers as i recall to a SATA drive.  The second partition on any drive
would be HDA (or what ever type drive and position)1  and so on.

> I would have read those even though I was deliberately seeing if Ubuntu would let me easily mess up. 


Ubuntu like the 249 other linux distros, the various win distros,and the various mac distros, is an operating system.  It is an inaniment object
and remains so until animated by a sentient being.  Ubuntu for all its
greatness does not ( as yet anyway) have consious thought. you push the buttons. It depends on you to make reasonable and considered decisions.  If you dont it is on you not the OS.

> I will say the major impression I get of Ubuntu so far is how visually ugly it is compared to Windows and Mac. Is this the fault of GNOME (if it should be described as a fault?) 


I really take exception to this comment.  If your desktop and/or theme is ugly, that is on you.  that is your choice.  One of the first things i do after install is change my wall paper.

I truly wish i could show all my desktop.  I am however bound by honor and a promise never to show it outside my home.

---

### Post by Ms_Angel_D on 2009-04-04
> **windows22 said:**
> First job was to install Flash player in Firefox. It seemed to need Terminal, so dunno how easy that would be for some Windows users. Generally, installing apps (via the menus) is more pleasant than on Windows, I think.

May be back with some more questions if I can't find the answers elsewhere. Next task is compiling a program called Audacity (there is an rpm but I like to have the latest changes). 
Succeded in compiling dev version of wxGTK which is a necessary precursor.

Thanks

You might want to check out [Ubuntu tweak]("http://ubuntu-tweak.com/") it will let you install those programs (Audacity is included) without compilation as well as adding there ppa's to your sources list so that it stays updated to the latest version.

---

### Post by Chemical Imbalance on 2009-04-04
> **stalkingwolf said:**
> 

I truly wish i could show all my desktop.  I am however bound by honor and a promise never to show it outside my home.

Hmmm...top secret desktops...interesting ;)

---

### Post by stalkingwolf on 2009-04-05
> **Chemical Imbalance said:**
> Hmmm...top secret desktops...interesting ;)

not top secret.  Just a promise given to a very special Lady.  A gift received is something to be honored.

---

### Post by sprezzatura on 2009-04-05
Unless you really need both OS on the same PC (vg. traveling laptop), and until you have tested Ubuntu, why not consider a second PC? A used one can be had dirt cheap. Get a KVM (Keyboard-Video-Mouse) switch to share between the two PCs, and you can install Ubuntu on your second PC. You can surf the Internet with complete peace of mind, and learn to appreciate Linux.

Surely, protecting your photos, documents and data is worth a couple of hundred bucks?

You might find that you are turning on your Windows PC less and less...

---


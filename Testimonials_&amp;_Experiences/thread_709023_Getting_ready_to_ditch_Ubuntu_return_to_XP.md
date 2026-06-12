---
title: "Getting ready to ditch Ubuntu return to XP"
date: 2008-02-27
forum: Testimonials &amp; Experiences
---

### Post by sattruckmark on 2008-02-27
Ok guys... I haven't pulled the trigger yet but it's loaded.  

So you understand the type of guy I am:  I started with PCs in the days when a 386Mhz PC cost 5k.  I used Prodigy when it was spanking new.  I beta tested AOL before it had a version # (1.0).  I never played with Unix, Linux, or Macs.  It was DOS to Win 3.1 and till now, XP and Vista.  I hate Vista so spite drove me to look for something different...  I decided on Ubuntu at the end of my search.

I decided to switch to Ubuntu in summer of '07.  Loaded it on a old lap to play with for a few months.  I was a religious daily reader on this and other related forums.  I took lots of notes.  When I finally decided I was command-line savvy enough, I  made the switch in December '07 on my XP laptop.  I added another HDD, made it dual boot with GRUB.  Took a while, but with help from here, I figured it out.  

Let me say to everyone moderating this site:  You do a heck of a good job.  

So.  Ubuntu was up an running.  Now to make it work with my existing files and find suitable replacement opensouce programs, and spice up the desktop a bit.  

Long story(s) short, here's the list of why i'm about to go back to XP.

- I have to sudo and remodify config files after most autoupdates to get my system to work right again.  Recently, some things I can't get to work now at all.  

-I understand why the group permissions are in place, but I have to change many of these after autoupdates as well.  Things like virtualbox and my display settings.  

- I still cannot get it to keep my display settings as I set them.  They default after every reboot.  Attempts to correct have not succeeded.  

- In contrast to the "It's so stable" hype, My multiple installs of Ubuntu on my NEW  business PCs, suffer lockups, freeze ups, pointless-unprovoked crashes.  Sometimes the desktop will disappear.  Sometimes the audio will not work.  I have two local guys that are Linux geeks and even they are getting ticked off.  

-All these file premissions...  It's like Vista, only more subtle.  

My company is a major media outlet and we've been wanting to push Ubuntu as a tool, but we can't now because most of our installs are too flaky.  

My equipment requires PC's to interact with them, Ubuntu (with some of my own programs) works with everything I need it to.  But it's NOT stable enough to be reliable.  My XP NEVER CRASHES ON THE JOB.    

I love opensouce and contribute my own programs on a few sites as well.  I know it's a huge undertaking. 

My request to those who run this wonderful idea is:  Cover ALL the basics first, then worry about making my desktop split into a cube.  I need functionality before glamor.  I need it start up the way I want it every time, I need it to run for a week without my interaction, I need my printer to work.  Prove to me that it can do this, and I'll market Ubuntu myself.  

-recent autoupdate made my printer quit as well.  

Help guys... I'm drowning here.

---

### Post by croto on 2008-02-27
Hi, let me say I understand your frustration. It happens, especially with laptops, that there are some hardware incompatibilities. I have seen many crashes due to video card problems. Probably the hardware manufacturers are the ones to blame here for not providing either open source drivers or specifications so that someone else could make the drivers. It's their choice. But I know that knowing that doesn't solve your problem, you want a functioning machine.

Ubuntu is what I would call a bleeding edge distribution. It's aimed to utilize every single hardware functionality. I believe that's great of course, but I also believe there are some things not really working yet. That situation is very likely to change in the future, if there's more collaboration from the hardware manufacturers. So if your computer is not working, it's a no brainer - you should change the OS (maybe some problems could be solved as now, but I don't know how much time you really want to invest in that). So you can go back to XP. Or, if you want to stay in the open source camp, you can try out another linux distribution. I suggest trying OpenSuse, or Fedora. They are really user friendly - alla ubuntu - and you may not have the same hardware problems with them. There are many other distros, I wouldn't say there's one that's the best. I personally  like Slackware, but it's not so user friendly as ubuntu or opensuse, it expects the user to know a bit more of the internals of the operating system in terms of configuration and maintenance. 

Anyway, that's my 2 cents. Good luck!

---

### Post by Lucretius on 2008-02-27
Ubuntu's future is looking bright... there is far more collaboration these days with manufacturer's so many of these hardware issues will fade away.

I would suggest waiting until Hardy Heron 8.04 is released

 It is a long term supported release and is specifically geared towards stability.

Of course if you find ubuntu does not provide the environment your business needs than don't feel obliged to stay. 

Just pop back from time to time :guitar:

---

### Post by dasunst3r on 2008-02-27
Tell us a little bit more about your platform.  For example, I am running 6.10 with an nVidia graphics card and Compiz Fusion.

I know how frustrating crashes and stuff can be.  I dealt with 3/4 of a year of my computer randomly locking up and turning off at random intervals.  It turns out that it was the graphics card driver at fault.  Indeed, I updated my graphics card driver as soon as a new one came out in December and my computer has been more reliable ever since.

Before going back to XP, please try out other distributions.  But if you do decide to go back to Windows, thanks for giving Linux a fair shot and come back every six months to see how we're doing.

---

### Post by eye208 on 2008-02-27
> **sattruckmark said:**
> My request to those who run this wonderful idea is:  Cover ALL the basics first, then worry about making my desktop split into a cube.  I need functionality before glamor.  I need it start up the way I want it every time, I need it to run for a week without my interaction
Thanks for your advice, but there is no way to fix the issues you are experiencing with Linux.

Why? Because we have no clue what's going on there. Flaky installs on most of your PCs? Since I ditched Windows in '06, I've been using Linux 100% of the time, on various PCs, including laptops. I have not yet seen a flaky install anywhere.

But we're talking about software here, so I am well aware that sometimes a single bug can make an entire system fail. In your case it must be something that all of your PCs have in common. Unfortunately you're not telling us what that may be.

This means your advice is pretty much useless. There's no magic crystal ball. It's _your_ job to investigate and find out what component is causing the failure and file a bug report so that the developers know where to look in the code. That would be much more useful than advising them to "cover the basics first". What the hell do you think they are doing?

---

### Post by hyper_ch on 2008-02-27
> **sattruckmark said:**
> - I have to sudo and remodify config files after most autoupdates to get my system to work right again.  Recently, some things I can't get to work now at all.  
If you have to do that, then your install is seriously flawed...

> **sattruckmark said:**
> 
-I understand why the group permissions are in place, but I have to change many of these after autoupdates as well.  Things like virtualbox and my display settings.
(1) do not auto-update and verify the updates
(2) updates should not reset permissions/config files... something's seriously flawed there...

> **sattruckmark said:**
> 
- In contrast to the "It's so stable" hype

It's not a hype, it is stable - if supported hardware is used.

> **sattruckmark said:**
> 
-All these file premissions...  It's like Vista, only more subtle.
The file permissions haven been there long before Vista. If you worked a little bit on them, you'll start appreciating them. Normally, if you don't have access to a file/dir then you should not have access to it as normal user.

---

### Post by dstew on 2008-02-27
> I understand why the group permissions are in place, but I have to change many of these after autoupdates as well.That seems strange to me. I have never had to do that on any of my Ubuntu installations. Maybe the OP accidentally enabled the root account.

---

### Post by wolfen69 on 2008-02-27
> My multiple installs of Ubuntu on my NEW business PCs, suffer lockups, freeze ups, pointless-unprovoked crashes
sounds like my windows customers. second, if you really wanted ubuntu to work on new pc's, you could have bought pc's with ubuntu pre-installed, just like windows. new pc's are locked into windows, in case you havnt noticed. THEY ARE MADE FOR WINDOWS. BUY A MACHINE MADE FOR LINUX! is that concept hard to understand?

---

### Post by iheartubuntu on 2008-02-27
Im still fairly new to Ubuntu (6 months in) and one thing I notice is you only have 3 forum posts? My first step in all of this was to join the forum here and ask questions and learn from my mistakes (and others mistakes and their knowledge).

In saying that, I found out my Ubuntu install discs I burned all sucked. The solution?  I ordered a FREE install disc. It came from the Netherlands and it worked very well and was very stable and Ive never looked back! I suggest before giving up completely to order that FREE install disc and re-install Ubuntu and go from there. It took about a week for them to ship me a disc and Im in California. 

Order a free disc here... [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by sattruckmark on 2008-02-28
Ok guys, let me say i'm sorry for posting my testimonial & Experience on the "Ubuntu Testimonials & Experiences" forum.  I didn't mean to offend you guys here and I did thank the site admins for doing such a good job.  This is my experience with it.  I did not simply install it and start yelling "why don't this thing work right?"

I also mentioned that I read, studied, tested, played, learned, for close to 6 months before pulling the trigger.  On many occasions, I worked with some of my employee's personal Ubuntu based pcs for a while as well.  Like I said, I evaluated several distros before choosing Ubuntu.  With _4344034_ posts on this forum alone, it was rather easy to find support for most of the problems we ran into.  We consider it to be pointlessly redundant to ask the same question that hundreds of others have already asked that have been answered.  

My two linux gurus also nudged me towards Ubuntu because it was a very stable, user friendly OS.  I agreed.  Yes, a learning curve was involved, but I was willing to jump into it.  

I should have worded my original post a little differently, being that the freeze ups and crashes are mainly related to applications we have running.  Most of these are opensource that we need to do our job.  I just posted two patches on another forum to fix some of the problems that others like myself have been experiencing.  As for our flaky installations, it's true.  On three of our desktops, including my HP lap, the desktops just disappear.  We've reinstalled.  We've rolled-back drivers.  All the desktops are identical in every way.  The short remedy is always a reboot, loosing our work.    

The problem with some of my config files come with regular updates.  One constant irritant is my grub config file.  I have a simple dual boot on my HP lap with two drives.  I wrote the menu1st.conf file to have two options:  1. Ubuntu; 2. XP.  Simple.  Easy.  Get an update, my config file is replaced with the original default file.  We don't know why it does this.  My config file problems are all similar to this issue.  

Guided by the forums and compatibility lists, our 6 work pc were purchased and built with Linux/Ubuntu supported hardware.  My HP laptop is also supported.  We have compatible Nivida video cards in all setups.  Audio hardware is generic and supported.  

We invested hundreds of man hours and around $15k in hardware purchases, all with Ubuntu at the core.  We ordered our install disks via snail-mail, even though we had burned a couple of ISO install disks. 

My statement about functionality before glamor still sticks.  Just like MS, "some" updates get released before all variables are tested.  It is of course impossible to foresee all variables when patches are released and newer drivers are made available.  But.. a lot of the issues we see are due to a lack of proper planning.  We've seen a surprising amount of updates that work for only 80% of end users, while the remaining 20% get the stick until the next patch.  Yes, this success rate is WAY better than MS, but has this become an acceptable release standards policy for Ubuntu?

I've posted my technical issues on other forums, including this one.  There are three of us who are members here.  My two gurus are always asking questions and getting a load of help form everybody here.  

I posted here to share my experience and much of the response was negative to what I said.  As I stated in my open, I did not mean to offend, but this is what is happening to us.  My original post was after 15 hours of non stop frustration simply trying to get my Epson R320 to print.  It worked when I installed Ubuntu.  It does not now (again... after updates).

---

### Post by erginemr on 2008-02-28
You have made yourself clear now, and I believe other forum members will now understand you better.

Although you are not asking for help, I have something to say about grub-update. The fact that menu.lst is rewritten from scratch was also bothering me, but the following links:
[https://bugs.launchpad.net/ubuntu/+bug/136621](https://bugs.launchpad.net/ubuntu/+bug/136621)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=383282](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=383282)
suggest that the update is controlled by the following chunk in your /boot/grub/menu.lst file:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=175c9eff-2398-4c66-84b8-e13b8e8aaf62 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)
......
......
## ## End Default Options ##
```
where the lines with a single comment (#) are put into effect. I haven't tried it yet either, but I believe double-commenting them (##) should end your troubles.

On a final note, it is a pity that you have been experiencing problems of instability, after having invested so much money and manpower to it. My Ubuntu box is rock solid, but with a myriad of hardware range, and many hardware manufacturers providing support to Windoze only, it is like throwing dices. However, one of the biggest assets of Ubuntu is the incredible community here, and the confidence that there will be someone here to help with your problem. 

My experience is that a good share of the instability comes from enabling Compiz and incompatible hardware with a close second. Apparently, you have already made your decision, but considering the effort you have made, I would suggest you to try PCLinuxOS as a last resort (if you haven't done already), which I know, is also very good at user-friendliness and recognizing hardware. 

Take care.

---

### Post by dstew on 2008-02-28
> One constant irritant is my grub config file. I have a simple dual boot on my HP lap with two drives. I wrote the menu1st.conf file to have two options: 1. Ubuntu; 2. XP. Simple. Easy. Get an update, my config file is replaced with the original default file. We don't know why it does this.Can you post your /boot/grub/menu.lst file? There are a lot of configuration statements at the top, that start with #. These are not comments (the comments start with ##). Maybe there is a problem there. Whenever a kernel update is done, the program [update-grub]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz") is run, and if the configuration statements in /boot/grub/menu.lst are off, there can be problems. One common one is with the #groot value.

---

### Post by ]Nbx*cmD[ on 2008-03-01
What's the matter? I think nobody reads the "Ubuntu comes with absolutely NO WARRANTY" message...

This forums are full of "back to windows" posts, I'm kinda fed up with it. You don't like it, you don't use it. If you don't believe in free sotware, that's your choice.

You should check the forums of less popular (but not worse at all) distros. Nobody at all would write such a post, cos people bothered learning a little about what's all this free software stuff about. Ubuntu is nice cos there's a lot of people working on it, and it's giving gnu/linux a big boost, but in the other hand it's selling an image of the free software community which is not real.

This is something people does together, there's no company telling you "oh that's gonna work for sure", there's no room for complaints in this community. If you got a problem you can, of course, ask for help, but nobody should come after you begging you to stay with the community if you don't have the will to.

Sorry if I've been a bit rude, it's just that whenever I search for anything in this forums I have to surf over thousands of posts of people complaining and threatening with going back to propietary systems. So, if somebody here doesn't stick to ubuntu's free software ideals... let 'em go.

---

### Post by hyper_ch on 2008-03-03
> **']Nbx*cmD[ said:**
> but in the other hand it's selling an image of the free software community which is not real.

What image is that?

---

### Post by ]Nbx*cmD[ on 2008-03-03
Well, it's an "easy operating system" image, which leads to frustration to some users who can't get things to work properly easily.

---

### Post by erginemr on 2008-03-03
> **']Nbx*cmD[ said:**
> Well, it's an "easy operating system" image, which leads to frustration to some users who can't get things to work properly easily.

I partially agree with you. Using Ubuntu effectively requires some CLI knowledge.

But it is also true that when things go wrong in Windows, it will be a nightmare for the same uneducated computer user, resulting in a format and complete reinstall in many cases.

---

### Post by steveneddy on 2008-03-03
I use my laptop daily for work and have never experienced any anomalies.

Your best bet would be to purchase laptops from System76 that have Ubuntu preinstalled. If I were a professional that needed Ubuntu in the workplace, I wouldn't install an OS that I knew very little about and absolutely no experience with on machines that may not be compatible with said OS.

I would buy hardware with the OS already installed so that the hardware compatibility issue would not be there.

---

### Post by rphil2008 on 2008-03-03
I am really sorry to hear about the unpleasant experience of the origianl poster. It must have been a really frustrting experience trying to fix all those troubles in his Ubuntu computers. To the original poster, I understand your frustration...

My advice to fellow newbs (not necessarily to the OP).. try and relax. This is Linux we are trying to master. The rewards are great but there's a price to pay. Do not be carried away by all the hype. Do your homework, accept the OS's eccentricities and work with it. Get angry, smash your keyboard and do it all over again... *just kidding*

The forums are a big help, but if I depend on them alone, I'd go insane! Look at all the subjects and topics! How to sort them out? Plus I have no one to ask around. All are Windows users. I am on an island here myself. I know if I dive right in without some sort of preparation and forethought I'd give up easily. Just the mere sight of those long command line/scripts initially got me an allergy.

Perhaps one way to avoid all these frustration is to know the OS more intimately? Maybe a good guide book can be of great help. As my primary source of learning (I cant attend a class yet) I ordered another book called a Practicel Guide to Linux Ubuntu (soemthing like that) This is for an organized approach to something I am totally ignorant about and for my own er... sanity=) 

The cost of Ubuntu Linux reference materials I have ordered are already more than the cost of a licenced Windows XP. But I am not giving up. This is for real.

Good luck to the original posted. Hope you can sort things out.

---

### Post by jrusso2 on 2008-03-03
Instead of going back to windows I suggest trying a more stable distro.  Ubuntu as late has give up the stability and gone the flash route because this is what people want compiz fusion and all the eye candy enabled.


This is the first thing I disable.  But there are distros that are very stable and I recommend Debian.

However there are others that love Red Hat, SLED, Slackware and ArchLinux.

---

### Post by hyper_ch on 2008-03-04
> **']Nbx*cmD[ said:**
> Well, it's an "easy operating system" image, which leads to frustration to some users who can't get things to work properly easily.

It is an easy operating system....

I bet that most people will have equal problems setting up windows and ubuntu... probably windows even more.

---

### Post by ]Nbx*cmD[ on 2008-03-04
I agree windows is more difficult, but you must also agree that microsoft lies when they say "windows is easy".

Besides, ubuntu is not that easy, it's becoming easy but can't be compared with mac os, for example. Saying that it's as easy as windows is not exactly saying that it's easy... we all must agree that windows is only easy if you are a computer geek or have a neighbour, a friend or a relative who fixes it every now and then.

Anyhow, the purpose of my post was complaining about people threatening to go back to other OSes, as well as about Ubuntu experienced users begging them to stay.

Cheers,

nabax.

---

### Post by starcannon on 2008-03-05
Some things I've learned that make my Linux Experience Blissful.
#1 and most important, when buying or building a PC check compatibility, check what video, sound, motherboard, monitor, cpu, nic, wireless, modem works perfectly with it. If your buying prebuilts go to dell, they sell them ready to roll right outta the box.

#2 problems arise, when they do, take a deep breath, and never do any kind of updating during the work week. Set aside time each month or week for you or your tech guy to do that, in other words, plan for a day or 2 to deal with problems that might arise (should be practiced regardless of what OS you finally decide on)

#3 Trim the fat, work machines don't need compiz, they need to be ultra stable, remove the glam, keep that for your personal tuner. Let work machines be a bit cleaner and meaner, also removes the need for certain updates (no update if its not installed right?) so ditch all non mission critical junk.

I have other things that I keep in mind, but those are some major steps you can take to make your work environment smooth, and painless.

Good Luck which ever way you decide to go.

~Rob

---

### Post by RawMustard on 2008-03-05
Your problems are not with linux, your problems are with Ubuntu.
I wish I could say otherwise, but the sad reality is, Ubuntu is very unstable.  If you want any hope of having a rock solid Ubuntu system throughout two release schedules then don't update at all, your system will break :(

If Ubuntu wants to attract more users, then they need to pay more attention to detail.  I don't think I will be upgrading to Hardy as Feisty has broken too many times for me and Gutsy is worse.  I'll try Hardy out when it's released, but if it's anything like Gutsy, then bye, bye Ubuntu for me and off to CentOS.

---

### Post by jeffus_il on 2008-03-05
Ah! these tough separations from Ubuntu. Unbelievable, almost as bad as divorce. At least there is no problem with custody of the kids. Such strong emotions, such heated discussions, such jealousy! it must have been[SIZE=4][COLOR=Red] love[/COLOR][/SIZE]!

---


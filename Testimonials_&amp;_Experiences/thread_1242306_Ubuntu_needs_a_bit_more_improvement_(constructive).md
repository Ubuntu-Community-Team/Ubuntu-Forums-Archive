---
title: "Ubuntu needs a bit more improvement (constructive)"
date: 2009-08-17
forum: Testimonials &amp; Experiences
---

### Post by prizrak on 2009-08-17
Preface:
First of all, as you can see I have been a member of the community for years. Also I know my way around *nix and have no problem with finding solutions to my issues. However, recent developments at Redmond (Win 7) prompted me to abandon my beloved OS on my main machine in favor of the latest from MS. 

I will try to keep this post as constructive as possible. Also I would like to point out that I am not looking for help with any problems I had as I have already carried out the switch on my main machine. 

Hardware specs:
XPS M1330n - this machine came with Ubuntu out of the box and has not been changed in any way during it's lifetime. There have been 2 releases since I purchased it. Also hardware diagnostics were performed on the machine, courtesy of Dell's own utility, and no issues were found.

Release cycle:
There has been quite a bit of controversy about this in the past and I used to think that it is great. A new OS every 6 months! All the bells and whistles, kernel improvements, new drivers and so on. However, the more I use the OS the more I think that the 6 month release cycle is a mistake. 

For one the upgrade mechanism is still far from perfect (as it is on any OS), however with releases following each other so closely it has to be absolutely perfect. Reinstalling the entire OS and any software that one is accustomed to as well as redoing all the customization every 6 months is just not practical for people who have jobs and significant others as it takes too much time. 

A longer release cycle would also allow more room for testing. For instance a large part of the below list suggests that developers did not do much testing with Dell, which is strange considering that Dell is the only big consumer oriented OEM that offers Ubuntu as a choice. 

As a corollary to this, lack of availability of new software. Firefox 3.5 has been out for months and as of last week was still not available in Ubuntu. Yes it is very easy to install it into your /home directory or wherever but Ubuntu has a very powerful repository system, which is not being used to its full potential.

I would suggest an 18month release cycle with all major applications being available in the repositories shortly after the release. Mind you I'm not talking about Gnome here, but things like Pidgin and Firefox SHOULD be available ASAP as opposed to months after. 

Hardware:
Fingerprint reader - when I got the originally including OS my fingerprint reader worked absolutely fine. Once I installed the next version I had to search for guides on how to get it to work, and even then there were some stupid quirks.

Latest release completely broke the functionality, I had been unable to find any guide that would work and while I had heard that Gnome now has support for fingerprint recognition as part of the login process I was unable to find any information on how to actually enable it. 

Windows 7 installed the driver through the Windows Update service. It also added an entry into the Control Panel for biometric devices and had a very easy to use utility that allowed me to enroll the fingers I wanted to use for login. 

USB: 
This deserves its own section because its idiotic. Any transfer of files over USB took forever. It took me 4 hours to transfer 6GBs of data from my laptop to my USB flash drive. Operation that I repeated on the same machine after installing Win7 and it took about 10 minutes.... A friend of mine had the same issue...

I'm sure there is some solution to this but frankly I didn't want to bother this is entirely too basic to require digging around for a fix...

Bluetooth: 
Works fine out of the box, unless you want to use it.... A2DP (BT Stereo) support is atrocious... The included utility could not pair my headphones and in order for me to even get BT audio working I had to write a shell script that would connect to my headphones and enable BT. To make matters worse I had to install a separate utility to force audio streams to BT in order to use it. When BT was disconnected sound would still be sent to it unless I go to the utility AGAIN and change it.

Just as a contrast to this, on Win7 I paired my headphones and set them as the default device for any audio playback. Anytime they are connected all the audio is rerouted properly. Upon disconnect audio is rerouted over to the built in speakers. As a bonus this works on the fly no restarting applications.

HDMI:
This particular machine comes with an HDMI out that carries a/v data (as opposed to just video as most video cards). Ubuntu thought my 42" TV was a 7" inch monitor with a 1920x1080 resolution. I won't even mention [lack of] sound.

Again to contrast Win7 changed resolution to 720p, cloned the screens and rerouted all the audio via HDMI. All I had to do was plug the cable in, nothing else.

Speed:
One of the biggest reasons why I originally went to Linux in general and Ubuntu in particular was efficiency/speed of the OS. Somehow it is now gone. Granted I did not do a fresh install and there is a possibility that it would have worked better if I did but going back to my original point if releases are to be kept this short the upgrade mechanism MUST be perfect. 

I experienced random lock ups that would last for a few seconds. Random lock ups that required a hard power down. Random lock ups that resulted in the machine not shutting down completely. Random lock ups on wake up from suspend. This is ALL on a machine that was designed for Ubuntu. 

I have also had Firefox randomly lock up on me and mess up formatting of one specific site. Issue I did not experience with the same version on my office PC running XP Pro. 

I suspect that an upgrade to 3.5 might have fixed that particular issue, however that goes back to locked down repositories. I do not want to go outside of the repositories this makes the entire idea of them obsolete.

As a contrast Win7 ran faster than both Ubuntu and XP on my 4 year tablet PC. It is also noticeably faster on my main machine.

Looks:
We can deny it all we want but looks are important. Composited desktop looks good but it falls a bit short. Windows' Aero interface uses the GPU for everything including font smoothing making it look very very good. Ubuntu on the other hand seems to only use the GPU for special effects and the rest *looks* like it is software rendered.

I remember when compositing first came out and there was XGL, which was a fully GPU based X server. Even w/o special effects it looked better than AIGLX extensions. Linux was always about being on the cutting edge, it needs to let go of the old X server. 

Conclusion:
I understand that none of the above issues are necessary show stoppers by themselves or even in conjunction with each other. However as someone who has to figure out computer problems all day at work I don't particularly want to bring them home.

---

### Post by running_rabbit07 on 2009-08-17
Glad to hear Windows 7 is stepping up a bit. I think gates realized his people needed to make a better system than Vista. 

I am glad to say I have had few problem thus far with Ubuntu.

It would be nice to see new programs hit the repositories sooner, but I am not really complaining because there isn't much difference in the functionality from what I have seen using FF3.5 with Karmic and Fedora.

Hopefully when you get to try Karmic or Lusty you will be as impressed as you have with Windows 7.

May the Schwartz be with you.

---

### Post by HappyFeet on 2009-08-17
It was too long for me too read, but ubuntu is perfect for me, and people I know. 

I try not to take compting so seriously as *you* seem to, and *I* have my own repair business. I don't worry about much anymore and just do some bug reporting and enjoy ubuntu for what it is: The best OS *I* have ever used. Use what works for you, and be happy you have a choice.

As far as I'm concerned, there is no debating what you had to say, as respectful as it probably is. Those days are over for me, as I have more important things in life to worry about. Ubuntu is an OS, not life and death. Lighten up and tell someone you love them. ;)

---

### Post by mdsmedia on 2009-08-17
> **prizrak said:**
> 
Conclusion:
I understand that none of the above issues are necessary show stoppers by themselves or even in conjunction with each other. However as someone who has to figure out computer problems all day at work I don't particularly want to bring them home.
As someone who has to use Windows all day at work, I don't particularly want to come home to it, either.

I accept that Ubuntu/Linux isn't perfect, and some of the problems you're having ARE hardware related, and I accept that it's not perfect for you.

I don't expect as much from any OS as you do, so I'm not saying that my computing experience is anything like yours. I remember when Windows didn't do a lot of what it does today. 

I forget about what Windows can handle which might be problematic in Linux and just accept what Linux is capable of and am thankful for the things that Linux does so much better than Windows.

I certainly wouldn't be switching to Windows for the reasons you've given, but that's your choice.

---

### Post by lancest on 2009-08-17
Just some points: 

Firefox 3.5 has been in the repositories for some time. 

My 43" LCD TV has a great picture just using pc VGA with Nvidia. (I'm going to be using HDMI soon and I predict no problems) 

I have Ubuntu Juanty on more than 5 machines (with Ext 4) and have not seen many lockups including on netbooks.

I seriously doubt Windows has anything to match the file copy speed of Ext 4. (Blazing).

Ubuntu is fine looking. Avoids the plastic look. Fonts are excellent, better than what I've seen elsewhere. 

Good luck with Windows.

*From what I've seen about the newer kernels- Ext 4 file transfer performance will be enhanced.
This is of great benefit to me since like others I do a lot of video file copying (for instance I often copy to a NTFS formatted Seagate which burns rubber)

---

### Post by 3rdalbum on 2009-08-17
> Firefox 3.5 has been out for months and as of last week was still not available in Ubuntu.

Err... yes it is. Do a search in Synaptic.

> USB: 
This deserves its own section because its idiotic. Any transfer of files over USB took forever. It took me 4 hours to transfer 6GBs of data from my laptop to my USB flash drive. Operation that I repeated on the same machine after installing Win7 and it took about 10 minutes.... A friend of mine had the same issue...

Your USB flash drive is formatted as NTFS.

NTFS is slow to write to on Linux until the developers optimise it. They are not currently optimising it, because NTFS writing support is new (comparatively) and reverse-engineered, and at the moment the developers are improving reliability and implementing things like file recovery.

When going to fat32-formatted devices, or native Linux filesystems, Ubuntu is as fast as anything else.

---

### Post by MaxCarnage on 2009-08-17
I do a lot of DVD-ripping and transferring (to a 500GB USB drive) and I have always found that 9.04 beats Windows in moving files. I also have my notebook dual-booted with Windows XP and 9.04 and I can tell you the performance difference is notable, particularly using ext4. I've never had Ubuntu lock-up on my Acer, and believe me I abuse this thing pretty regularly.

Windows 7 is definitely a step up from Vista (and maybe even XP). I was using the Beta on a VirtualMachine on my desktop for a while, and it performed pretty admirably. Still, I am not ready to abandon Ubuntu. There are too many things that it does well (like, for instance, ripping DVDs) for me to go back to Windows on an everyday basis.

---

### Post by armandh on 2009-08-17
got as far as the release cycle issue and had to post.

no matter ms or nix, the real testing comes after the release.
there are too many details to be perfect OOTB.
can you say XP SR1,2,3 

at least with ubuntu you can stick to the LTS releases if you want a longer cycle 

The OOTB finish varies with distro and release, even with win.
Vista was a great boon to nix, 7 may be less so [TBD]

over lapping 18 month cycles of long term support every 6 months.
that would be an improvement! [IMHO]

---

### Post by prizrak on 2009-08-17
> As far as I'm concerned, there is no debating what you had to say, as respectful as it probably is. Those days are over for me, as I have more important things in life to worry about. Ubuntu is an OS, not life and death. Lighten up and tell someone you love them.
I love you man :D If you read my post you would see that I'm not taking it all that seriously.
> Firefox 3.5 has been in the repositories for some time. 
Well this is embaracing, how the hell did I not see it? 
> have Ubuntu Juanty on more than 5 machines (with Ext 4) and have not seen many lockups including on netbooks.

I seriously doubt Windows has anything to match the file copy speed of Ext 4. (Blazing).
It was USB transfers specifically not HDD. 
> I accept that Ubuntu/Linux isn't perfect, and some of the problems you're having ARE hardware related, and I accept that it's not perfect for you.
I only mentioned hardware related issues, there are certain issues that have to do with availability of software but these cannot be helped by the community so I left them out. The biggest issue here is that hardware I bought CAME with Ubuntu out of the box. I got the laptop from Dell with a preinstall of Ubuntu so I didn't expect issues with hardware. 
> My 43" LCD TV has a great picture just using pc VGA with Nvidia. (I'm going to be using HDMI soon and I predict no problems) 
It is an Intel card not nVidia. Perhaps nVidia would do a better job, I wish you luck. 
> Your USB flash drive is formatted as NTFS.
No both my flash drive and my external HDD are Fat 32, I reformatted both of them myself when I got them. 

Just to be clear I'm not switching to Windows completely. I am switching my main machine to Win 7 my desktop will be getting Ubuntized when I get around to it.

---

### Post by solwic on 2009-08-17
> **prizrak said:**
> Preface:
First of all, as you can see I have been a member of the community for years. Also I know my way around *nix and have no problem with finding solutions to my issues. However, recent developments at Redmond (Win 7) prompted me to abandon my beloved OS on my main machine in favor of the latest from MS. 

...

USB: 
This deserves its own section because its idiotic. Any transfer of files over USB took forever. It took me 4 hours to transfer 6GBs of data from my laptop to my USB flash drive. Operation that I repeated on the same machine after installing Win7 and it took about 10 minutes.... A friend of mine had the same issue...

I'm sure there is some solution to this but frankly I didn't want to bother this is entirely too basic to require digging around for a fix...


I think this is the biggest issue in your post.  You say you've been around the community for years, and that you know your way around *nix, but then you give us that last paragraph, about how you don't want to dig around to fix a problem.  Thus the contradiction.

To me, this is like finding a flat tire on your car.  It's a TIRE!  It's BASIC to the functioning of the car.  But if you find that flat tire, you don't go buy a new car.  You fix the tire.  

I'm surprised to see this attitude from someone who has spent "years" in the community.  I'm not saying it's wrong, or that you're wrong, just that it's surprising.  If you really were here in '05, you'd know that tinkering is almost hand in hand with Ubuntu; sometimes, the devs just get it wrong.  

Personally, it sounds like you're trying to justify your desire to try Windows 7.  If you like W7, use it.  We don't mind.  This post just makes me wonder who you're trying to convince:  us or yourself.

Just my take, though.  Nothing personal.  :biggrin:

---

### Post by ukripper on 2009-08-17
> **iRun said:**
> 
To me, this is like finding a flat tire on your car.  It's a TIRE!  It's BASIC to the functioning of the car.  But if you find that flat tire, you don't go buy a new car.  You fix the tire.  

  :biggrin:

Fully agree with this analogy.

---

### Post by solwic on 2009-08-17
> **ukripper said:**
> Fully agree with this analogy.

Thanks, mate.  :biggrin:

---

### Post by HappyFeet on 2009-08-17
And btw, I don't use NTFS partitions, so I can't comment on the file transfer issue. I can however, comment on file transfers between linux and fat32. ( I use fat32 on my storage partitions) It is *very* fast and efficient.

---

### Post by solwic on 2009-08-17
> **HappyFeet said:**
> And btw, I don't use NTFS partitions, so I can't comment on the file transfer issue. I can however, comment on file transfers between linux and fat32. ( I use fat32 on my storage partitions) It is *very* fast and efficient.

I took the effort to format my external backup drive to ext3.  Yet another reason to never touch Windows again.  :)

I'll move it to ext4 once its fixed in Ubuntu.  Question, though:  is there any reason to use FAT32 on a storage drive other than for compatibility with Windows?  I'm wondering if there's some technical aspect that I just don't know about.  

:biggrin:

---

### Post by HappyFeet on 2009-08-17
> **iRun said:**
> I'm wondering if there's some technical aspect that I just don't know about.  

:biggrin:

I'm not really sure, but it's just something I did. To me, it does not matter too much.

---

### Post by running_rabbit07 on 2009-08-17
> **iRun said:**
> To me, this is like finding a flat tire on your car. It's a TIRE! It's BASIC to the functioning of the car. But if you find that flat tire, you don't go buy a new car. You fix the tire. 

It seems he was having multiple flat tires and the intake was cracked and there was sugar in he gas tank. Not to mention the spun bearings. 

After a while the repairs just do not appear to be worth it.

---

### Post by mdsmedia on 2009-08-17
> **running_rabbit07 said:**
> It seems he was having multiple flat tires and the intake was cracked and there was sugar in he gas tank. Not to mention the spun bearings. 

After a while the repairs just do not appear to be worth it.
No, he was talking about Ubuntu, not Windows ;) (kidding).

---

### Post by prizrak on 2009-08-17
> **iRun said:**
> I think this is the biggest issue in your post.  You say you've been around the community for years, and that you know your way around *nix, but then you give us that last paragraph, about how you don't want to dig around to fix a problem.  Thus the contradiction.

To me, this is like finding a flat tire on your car.  It's a TIRE!  It's BASIC to the functioning of the car.  But if you find that flat tire, you don't go buy a new car.  You fix the tire.  

I'm surprised to see this attitude from someone who has spent "years" in the community.  I'm not saying it's wrong, or that you're wrong, just that it's surprising.  If you really were here in '05, you'd know that tinkering is almost hand in hand with Ubuntu; sometimes, the devs just get it wrong.  

Personally, it sounds like you're trying to justify your desire to try Windows 7.  If you like W7, use it.  We don't mind.  This post just makes me wonder who you're trying to convince:  us or yourself.

Just my take, though.  Nothing personal.  :biggrin:

It would be more akin to buying a Ferrari that comes with H rated all season tires instead of summer performance tires. 

I support *nix servers for a living I'm somewhat tired of supporting my own machines. 

Funnily enough I got into Ubuntu specifically because it was less problems than Windows. It was faster, it didn't require constant upkeep, I set it up once and it worked forever. Right now Win 7 is doing a good job of that :)

> I'll move it to ext4 once its fixed in Ubuntu. Question, though: is there any reason to use FAT32 on a storage drive other than for compatibility with Windows? I'm wondering if there's some technical aspect that I just don't know about.

In my case it was so that I can watch videos on my 360 :D
[QUOTE=running_rabbit07]It seems he was having multiple flat tires and the intake was cracked and there was sugar in he gas tank. Not to mention the spun bearings.

After a while the repairs just do not appear to be worth it. [/QUOTE]
ROFL! Thanks for the car analogies dude!!! I'm a car geek first and computer geek second so I'm loving this. 

I limited my OP to only issues that could be addressed by the community. I had some other issues, which were more software availability than anything else.

I am not switching all the way to Windows I am keeping an Ubuntu machine for all the fun server related stuff. More than anything I got bored of Ubuntu and wanted something new :P

---

### Post by cariboo on 2009-08-17
The usb transfer speed has to be file system related. I have xfs partions on my server as well as the usb backup drive, when I recently rebuilt my server I transfered about 500Gb to the usb drive and back after formatting all the partitions in about 6.5 hours.

---

### Post by prizrak on 2009-08-17
> **cariboo907 said:**
> The usb transfer speed has to be file system related. I have xfs partions on my server as well as the usb backup drive, when I recently rebuilt my server I transfered about 500Gb to the usb drive and back after formatting all the partitions in about 6.5 hours.
I actually found something that appears to be the culprit. Aparently you can either have the drive mounted in synchronous or asynchronous mode. In sync mode removing the drive w/o ejecting it will not cause loss of data but will make it as slow as I described.

---

### Post by HappyFeet on 2009-08-17
> **prizrak said:**
> 
I support *nix servers for a living I'm somewhat tired of **supporting my own machines**. 


I'm not sure what you mean by "supporting" my own machines. The reason *I* use linux, is because it needs *no* support. It always "just works". I am truly sorry if that is not your experience. To *me*, it was windows that always needed "supporting". Anyway, have fun with win7, as I know I won't.

---

### Post by Tamlynmac on 2009-08-17
[> ]("http://ubuntuforums.org/member.php?u=604568")[iRun]("http://ubuntuforums.org/member.php?u=604568")
Personally, it sounds like you're trying to justify your desire to try Windows 7. If you like W7, use it. We don't mind. This post just makes me wonder who you're trying to convince: us or yourself.

The need to justify a decision of which OS to use and feel compiled to do so on a forum, is IMHO "sad". I believe your assessment is on target, my friend.

The only additional note I'd make, is that one shouldn't feel the need to justify their decision/choice to others. IMHO, your absolutely correct when stating that "We won't mind". As a matter of fact, I doubt many of us even care - as it's a personal choice. Few Ubuntu users I know would feel compelled to interfere.

Again, you point out the obvious. Unfortunately, there will always be those that exploit every opportunity to bash the OS.

Which OS one uses is generally not a life threatening decision. When put in perspective and considering all of life's problems. If a choice regarding which OS to use reflects a major decision in one's life, I believe one should be thankful that life has been extremely good to them. ;-)

---

### Post by running_rabbit07 on 2009-08-17
My opinion is that the OP brought up a few issues that should be addressed. I really don't think he is trying to convince himself he did or didn't do the right thing. He made it quite obvious that he had to make too many adjustments to a machine that should have just worked being that it came with Ubuntu installed.

One of his issues that I agreed was was that FF3.5 isn't fully supported for Jaunty when it should have been within a reasonable amount of time. I tried every way there is to install FF3.5 and the only OSes I could get it to work on were Windows XP, Fedora11, and Ubuntu Karmic. Every time I installed it in Jaunty it crashed my GUI and I had to reinstall Ubuntu because nobody could help me with the crash. 

Like the OP's title implied, he meant for it to be constructive criticism, yet it seems that the people saying they don't care are the ones that are getting defensive. I really don't believe he was trying to bash Ubuntu.

I do find it funny that people are quick to bash Windows. I used Windows for more than 10 years and have never seen the BSOD on my own system. 99.9 percent of the people who I know of that have ever had problems with their system malfunctioning was from operator error.

---

### Post by steveneddy on 2009-08-17
Try System76 hardware next time.

Hope you like Windows. Personally I only use it when I have to.

---

### Post by HappyFeet on 2009-08-17
> **steveneddy said:**
> Try System76 hardware next time.


Or better yet, build your own. :P

---

### Post by Tamlynmac on 2009-08-18
> running_rabbit07
I do find it funny that people are quick to bash Windows. I used Windows for more than 10 years and have never seen the BSOD on my own system. 99.9 percent of the people who I know of that have ever had problems with their system malfunctioning was from operator error.

You forced me to re-read my own post, as I didn't recall bashing Windows or any other OS. After review - I hadn't. Obviously, you weren't referring to me.

I've used windows for a little longer than 10 years. Both in my personal and professional life. I must wonder if you or your friends ever used Windows ME. If I recall correctly the BSOD on ME was part of the startup procedure. :lol:

It's still my opinion that some will always find a way to bash Ubuntu/Linux, directly or indirectly. I've even witnessed individuals doing so while pretending to be Ubuntu/Linux fans.

My objection to those that bash the OS is simple - Why? What is the objective and why bash something that requires no investment, beyond a little time. If your dissatisfied, why not simply uninstall the offending free software and move on? Seems illogical to waste time complaining about that which you have no investment in. When downloading freeware for Windows, I didn't bother wasting time if it didn't perform as expected. I just uninstalled it.

As I indicated in my post, with all the other issues in life, seems a decision regarding which OS to use is rather minuscule - when put in perspective.

When reading any post in this forum, I believe it's apparent that individuals can and often do interrupt the post differently. Resulting in differences of opinion based solely on perception.

---

### Post by solwic on 2009-08-18
> **Tamlynmac said:**
> It's still my opinion that some will always find a way to bash Ubuntu/Linux, directly or indirectly. I've even witnessed individuals doing so while pretending to be Ubuntu/Linux fans.


The truth of the matter is that no product/OS will make *everybody* happy, and there are a lot of people in this world who like to complain.  Give them the internet - the perfect medium for complaining to lots of people - and you get such posts.  

I say, let 'em bash Ubuntu.  They can bash Windows, Mac, Ford, Velveeta, Hair Club For Men, Gilette, Charmin, ReNu, and Playtex...ultimately it's all personal preference.  I've had people tell me certain programs/products are garbage and it turns out that, for what I wanted it for, it was perfect.

If you don't like something, don't use it.  Why complain?  I mean, I can only speak for myself here, but I don't give a rat's fart if someone likes Ubuntu or not.  **_*I*_** like it for **_*me*_**; beyond that, why should I/we care?  

:biggrin:

---

### Post by bg_izrod on 2009-08-18
Constructive critisism is not a complain. It actually stands for improvments in status quo. Maybe the right word for that "complain" is "feedback"

---

### Post by mdsmedia on 2009-08-18
I've looked to the web for review of many things before I acquired them....or decided not to. If someone wants to complain/provide testimony about a product, for the sake of other users, that is their right, and it's there for everyone else to Google and take as they see fit.

I was interested in Linux since the late 90s. I toyed with Red Hat then, and in 2001. When my new notebook became relatively unusable with XP, in 2005, I asked the question of my local LUG. Ubuntu was suggested/recommended, and I gave it a try. It was the best thing I have ever done as far as my computing experience.

I used DOS from 4.X to 6.X and Windows 3.1 through XP and now Vista. I have some experience as an "average user". I'm not an IT professional. I'm just an interested enthusiast. Linux is the best thing I could have done and Ubuntu was the gateway.

I don't particularly care about Windows 7. Linux isn't perfect, but gee the positives outweigh the negatives. I'm forced to use Windows, because the software my (accounting) profession uses is Windows only. I'm hoping to be rid of the profession in the next year or so. Then Windows will have no excuse.

---

### Post by running_rabbit07 on 2009-08-18
> **Tamlynmac said:**
> You forced me to re-read my own post, as I didn't recall bashing Windows or any other OS. After review - I hadn't. Obviously, you weren't referring to me.

Nope, didn't say you were bashing Windows and no I was not bashing Ubuntu. Yeah, I would have liked to have seen FF3.5 work on my Jaunty, but after seeing FF3.5, it isn't all that much better than 3.0 anyway. The upgrade made a difference on Windows but it is too late for that being I already recycled the glass.

I personally didn't think the OP was trying to bash Ubuntu.

> **iRun said:**
>   **_*I*_** like it for **_*me*_**; beyond that, why should I/we care?

Exactly. Can i really bash Charmin?

---

### Post by prizrak on 2009-08-18
> I'm not sure what you mean by "supporting" my own machines. The reason I use linux, is because it needs no support. It always "just works". I am truly sorry if that is not your experience. To me, it was windows that always needed "supporting".
I got the machine a month or so before 8.10 came out, timing was due to Dell's limited time discounts and a $300 difference was not something I could afford to pass up. 
The machine came with 4GB of RAM yet had a 32bit OS (Dell's fault not Ubuntu's) As such when 8.10 came out I did a clean reinstall (including my /home) with the x64 version. As a result fingerprint reader didn't work and needed some tweaking. In fact there was a strange issue where you had to hit the return key after swiping your finger because new version broke auto return on swipe. Annoying but fine and was fixed quickly enough. So I install all my favorite programs, set up my wireless and so on. 6 months down the line 9.04 comes out, not wanting to reinstall all my software I did a dist-upgrade. Again fingerprint reader didn't work and I was not able to find ANY guides that helped as think-finger was depricated. The rest of the issues are in the OP. 

I fully suspect that if I did a clean reinstall I would not have as many issues as I did with upgrade. The problem is that with a 6 month release cycle it is not feasible for me to customize the hell out of my OS just to have to redo it for the next version. To make matters worse config files do change from release to release so I couldn't even script it. 
> Again, you point out the obvious. Unfortunately, there will always be those that exploit every opportunity to bash the OS.
Running_rabit07 got it.
I did not bash the OS. I have pointed out issues that I have personally encountered on hardware that was "designed for Ubuntu". If I was going to bash the OS I would say that it sux because iTunes doesn't work, or that I can't play StarCraft on it. While both are true these issues are down to third party efforts and as such I left them out of my post. 
> Try System76 hardware next time.
Dell was a better choice because of discounts I have through work. 3
> Hope you like Windows. Personally I only use it when I have to.
7 is actually very nice seems as though MS really tried this time around. 
> Constructive critisism is not a complain. It actually stands for improvments in status quo. Maybe the right word for that "complain" is "feedback"
Thank you. I attempted to make my post as constructive and non-bashing as possible, however it seems some people are bit sensitive as Linux does get alot of heat.

---

### Post by Syirrus on 2009-08-18
Some things mention by the above author of this thread do resonate with me.  I think Windows 7 is a show stopper in terms of performance and stability.  I don't think it will disrupt the free software movement though.  In all fairness (this is in response to some of the comments above) any computer can lock up for any number of reasons.  I don't think it is fair to knock Ubuntu for that.  As far as the release cycle, I think Canonical has done a good job in this dept. If you need the support and stability, go LTS.  The interim builds I think help linux advance while preparing the next LTS version of ubuntu for changes... if that makes sense.

Syirrus

---

### Post by prizrak on 2009-08-18
> **Syirrus said:**
> Some things mention by the above author of this thread do resonate with me.  I think Windows 7 is a show stopper in terms of performance and stability.  I don't think it will disrupt the free software movement though.  In all fairness (this is in response to some of the comments above) any computer can lock up for any number of reasons. I don't think it is fair to knock Ubuntu for that.
I am not talking once a month or so. Random lock ups for a few seconds were daily occurence, bigger lock ups were every other week or so. 
 >  As far as the release cycle, I think Canonical has done a good job in this dept. If you need the support and stability, go LTS.  The interim builds I think help linux advance while preparing the next LTS version of ubuntu for changes... if that makes sense.
The problem with this is that repositories are generally locked save for security updates so installing newer software is a pain. 

So it would make sense either do nothing but LTS every 18months or so while making new software available in the repositories in the interim. (realistic)

OR 


Need to make the upgrade system absolutely flawless so silly things like random lock ups don't happen. (unrealistic)

Otherwise redoing your system every 6 months is just not feasible...

---

### Post by HappyFeet on 2009-08-18
> **prizrak said:**
> 
Otherwise redoing your system every 6 months is just not feasible...

In *your* opinion. Many people do not mind doing so. I actually enjoy it. But those that *do* mind can just not upgrade until a later date. No one is forcing you to upgrade. Simple.

---

### Post by running_rabbit07 on 2009-08-18
> **prizrak said:**
> So it would make sense either do nothing but LTS every 18months or so while making new software available in the repositories in the interim. (realistic)

I think that would be great. Originally I had 8.04 on my system because it was the LTS, but then when FF3.5 came out everybody was saying that I had to get 9.10 to get the new FF. About a week ago I saw where they were debating making it available for the LTS. I am going to be running 8.04 in my Virtual box just to see if that happens, if it does, I'll revert back to the LTS.

---

### Post by fela on 2009-08-18
What could someone enjoy more than fixing computer problems. I'm not being sarcastic. If I get a problem with my computer and fix it it gives me adrenaline and great joy :)

I understand that this isn't applicable to people who need a system that 'just works' - in that case don't use the latest version of Ubuntu. Use the version before and a clean install (NEVER use the upgrade utility). Or if you really can't deal with Ubuntu's quirks, use another Linux distro or Windows if you must. But how is going to windows gonna fix any of Linux/Ubuntu's problems.

I do completely agree that the release cycle is way too short. I prefer debian's one, although that's a bit extreme on the other end where there's no set release date (I don't think). But yeah, there are alot of bugs in Ubuntu mainly due to the ridiculously short release cycle.

---

### Post by lykwydchykyn on 2009-08-18
I don't know what you expect to be done about the hardware issues, especially if you're posting feedback to a user forum rather than a bug tracker; I mean, come on, what do you expect from a non-windows OS?  The whole of the technology industry is geared towards supporting Win32 and very little else.  I look at things like the Linux Driver Project and wonder what else "the community" is supposed to do?

But I can understand it putting a damper on using Linux.  Just saying, you should know by now that's just part of the game, and it is improving slowly but surely.  You either accept that, or you accept the fact that the industry has decided for you that you will use Windows.

As for the release cycle, I would agree that the formula needs to be tweaked somehow.  There are trade-offs any way you go with something like that; I think the best approach is that there needs to be a way to get a good, fresh selection of backports for LTS.  The current backports repo is really only marginally helpful in keeping an LTS up to speed on the apps front.

But looking at the bigger picture, most of the "average users" in my life are just happy using WinXP and Office 2000.  How big of a deal is it for them to have a year-old version of OpenOffice?

---

### Post by fela on 2009-08-18
What could someone enjoy more than fixing computer problems. I'm not being sarcastic. If I get a problem with my computer and fix it it gives me adrenaline and great joy :)

I understand that this isn't applicable to people who need a system that 'just works' - in that case don't use the latest version of Ubuntu. Use the version before and a clean install (NEVER use the upgrade utility). Or if you really can't deal with Ubuntu's quirks, use another Linux distro or Windows if you must. But how is going to windows gonna fix any of Linux/Ubuntu's problems.

I do completely agree that the release cycle is way too short. I prefer debian's one, although that's a bit extreme on the other end where there's no set release date (I don't think). But yeah, there are alot of bugs in Ubuntu mainly due to the ridiculously short release cycle.

---

### Post by prizrak on 2009-08-18
> In your opinion. Many people do not mind doing so. I actually enjoy it. But those that do mind can just not upgrade until a later date. No one is forcing you to upgrade. Simple.
There are currently two successful (commercially) OS's on the desktop market. Neither of them has a brand new release every 6 months. I really don't understand why there are so many people who seem to be against extra testing time. Even an extra week or two of testing would help greatly. 
> I don't know what you expect to be done about the hardware issues, especially if you're posting feedback to a user forum rather than a bug tracker; I mean, come on, what do you expect from a non-windows OS? The whole of the technology industry is geared towards supporting Win32 and very little else. I look at things like the Linux Driver Project and wonder what else "the community" is supposed to do?
Not sure if you missed this. 
Machine in question is a Dell XPS M1330n, which was ORIGINALLY shipped with Ubuntu (7.10 I think at the time) by Dell. The system uses Intel CPU, chipset, video and wi-fi. I do not expect to have hardware problems with something that came as an Ubuntu. 

I fully understand that with the amount of hardware that Ubuntu has to deal with it is a miracle that it works as well as it does. However it seems to me as if there is a disconnect between the OEM's and Canonical at the moment. Dell is the only large OEM offering Ubuntu as a preinstall and yet it seems that Canonical did not test their releases properly with them. 

Considering that Dell only offers a couple of configurations with Ubuntu I would expect better out of the box functionality.
> What could someone enjoy more than fixing computer problems. I'm not being sarcastic. If I get a problem with my computer and fix it it gives me adrenaline and great joy
I could be way off but I would suspect that you are either very young or don't work in IT :)

---

### Post by Tamlynmac on 2009-08-18
> prizrak
There are currently two successful (commercially) OS's on the desktop market. Neither of them has a brand new release every 6 months. I really don't understand why there are so many people who seem to be against extra testing time. Even an extra week or two of testing would help greatly.

Amazing, I'm certain that Canonical is in a big hurry to emulate those two alternative OS's. They've always shown a propensity to identify with both of them. :)

Nothing mandates anyone upgrade. I don't recall reading anything in the Ubuntu acceptance dialog that states one must upgrade immediately upon release of a new version. Correct me if I wrong, but upgrading is a choice, similar to using Ubuntu/Linux. Complaining about a six moth release date seems non-productive when considering it's optional.

Many are still using 8.04 (LTS) or even earlier versions as they don't require upgrading. If one's seeking stability and longevity why upgrade at all?

> I fully understand that with the amount of hardware that Ubuntu has to deal with it is a miracle that it works as well as it does. However it seems to me as if there is a disconnect between the OEM's and Canonical at the moment. Dell is the only large OEM offering Ubuntu as a preinstall and yet it seems that Canonical did not test their releases properly with them.

Excuse me. I believe you have the process backwards. It's Dell's responsibility to assure that their product is sold fully functional, not Canonical's responsibility to test Dell's product releases. If your dissatisfied with Dell's products seek alternatives (System 76 or Zareason) or build your own.

> I could be way off but I would suspect that you are either very young or don't work in IT :smile:

I disagree with your assessment of fela. I also enjoy hands on (bare bones or self built) and have been in the electronics diagnosis field for decades. Suggesting fela is young or immature - is demeaning and unnecessary. Perhaps, you chose the wrong field of endeavor, if you don't enjoy your profession.

---

### Post by lykwydchykyn on 2009-08-18
> **prizrak said:**
> 
Not sure if you missed this. 
Machine in question is a Dell XPS M1330n, which was ORIGINALLY shipped with Ubuntu (7.10 I think at the time) by Dell. The system uses Intel CPU, chipset, video and wi-fi. I do not expect to have hardware problems with something that came as an Ubuntu. 

I did miss that.  Fair enough, though it doesn't really change the point.  Dell ought to stand behind what they ship on their computers, but they obviously don't (enough), because supporting Windows takes priority.  Did you complain to Dell?

---

### Post by vedek on 2009-08-18
whilst i don't speak for the whole community i think its relatively save to say that people who use linux are technically minded and we have not only moved from windows because its crap but because it allows us more flexiblity in what we can do, to say that you are an experienced linux user and have been a member since linux was a unknown quantity and the support wasn't nearly as good as it is now. i find it strange that you do not like fixing issues yourself because it seems highly likely that you have had to fix issues.

>   			 				I could be way off but I would suspect that you are either very young or don't work in IT :smile: 			 		

i think that is a little below the belt. 

i feel great when i make a fix or even better if i develop the fix.

Windows and Mac i presume that's the 2 your talking about they may not release as often as we do but have you considered why - and i am sure it ain't for testing reasons. money is the key thing for them if they released a major operating system every 6mths then the business would collapse and leaving Linux to rule the world {naive i know but i live in hope} ubuntu and Linux overall is a collaboration millions of people driving towards different goals with different directions this is our greatest strength and perhaps weakness because of the ever changing way of Linux a release a year or 2 isn't enough as tamlynmac said you don't have to update if you don't want its choice you installed this because you wanted to not because someone twisted your arm, things need to be improved i am not denying that but the problems will get fixed.

If you want to go to windows 7 i wont twist your arm but you will in all likelihood be back

---

### Post by fela on 2009-08-18
What alot of people don't understand is that the reason hardware is so well supported on windows is not because of Microsoft, but because of the hardware vendors. Until hardware vendors start to support Linux it'll never have nearly as good support as windows, and I think that considering this Linux distros have done an incredible feat in supporting the amount of hardware that they do. Remember that with Linux it's the developers of the OS, and to a certain extent only them (with a small minority of hardware vendors that make Linux drivers - not many at all really) - that make the drivers. Anyone that's tried installing windows on their OEM box (or custom build) from an OEM installation CD will know what I'm talking about.

I think you should only compare Linux hardware support to out of the box windows hardware support. Windows vista had a bit better hardware support on my computer OOTB - either that or it just had a better graphics tablet driver. OTOH windows XP x64 - not much older than my hardware - didn't even detect my network card let alone audio, graphics etc etc. The only driver I had to download to get full support in Linux was the graphics driver from nvidia - but you should do that anyway as they're constantly being updated.

About the case with Dell - as someone pointed out, Dell obviously have higher priorities with their Windows hardware support and should make Linux drivers for their hardware if they're gonna put Linux on it. I bet you 10 to 1 that they made their driver originally for the fingerprint reader on that XPS.

So to the OP, what are you saying? Linux or Ubuntu devs should bribe OEMs to develop drivers for Linux? I'm not a developer but I know that it's incredibly hard (and sometimes literally impossible) to code drivers for a product you don't even know the design specifications of. Again, the Linux devs have done a marvellous job at this thus far and I can't believe people are expecting anything more.

---

### Post by lukeiamyourfather on 2009-08-18
I totally agree about the fingerprint authentication in the first post, its a big time saver for mobile users and I really miss it in Linux. Only other thing that ***really*** bothers me is the hit and miss video driver releases (from both AMD and nVidia) but this is due to the manufacturer drivers not the operating system. Cheers!

---

### Post by solwic on 2009-08-18
> **bg_izrod said:**
> Constructive critisism is not a complain. It actually stands for improvments in status quo. Maybe the right word for that "complain" is "feedback"

You can call crap fertilizer, too...but ultimately, it's still crap.  

Of course, I'm being optimistic.  :biggrin:

---

### Post by solwic on 2009-08-18
> **running_rabbit07 said:**
> Exactly. Can i really bash Charmin?

Absolutely not!  :biggrin:

---

### Post by Chronon on 2009-08-18
> **iRun said:**
>  Question, though:  is there any reason to use FAT32 on a storage drive other than for compatibility with Windows?  I'm wondering if there's some technical aspect that I just don't know about.  

:biggrin:

FAT32 is basically a failsafe format.  If it's a device that will only be mounted on your linux box then there's no advantage.  If it's a flash drive you will use as portable storage when connecting to various other boxes, then it pays to use a portable format.

---

### Post by running_rabbit07 on 2009-08-18
> **iRun said:**
> Absolutely not!  :biggrin:

That's ok, because I do unspeakable things to Charmin.:-$

---

### Post by prizrak on 2009-08-18
> Amazing, I'm certain that Canonical is in a big hurry to emulate those two alternative OS's. They've always shown a propensity to identify with both of them.

How is taking a good idea and emulating it a bad thing? Linux/Ubuntu has a composited desktop (Apple first), Has a GUI (Xerox, Apple and MS beat them to it), powerful CLI with remote access and ability to run as a terminal server (Unix/Minix). Should I keep listing things that have appeared in other OS's first? Remember Linux has only been around since '91 there have been countless OS's before then many had features that Linux did not have and many Linux specifically emulated. 
> Nothing mandates anyone upgrade. I don't recall reading anything in the Ubuntu acceptance dialog that states one must upgrade immediately upon release of a new version. Correct me if I wrong, but upgrading is a choice, similar to using Ubuntu/Linux. Complaining about a six moth release date seems non-productive when considering it's optional.

Many are still using 8.04 (LTS) or even earlier versions as they don't require upgrading. If one's seeking stability and longevity why upgrade at all?

I have explained it already. Feel free to read back. 
> Excuse me. I believe you have the process backwards. It's Dell's responsibility to assure that their product is sold fully functional, not Canonical's responsibility to test Dell's product releases. If your dissatisfied with Dell's products seek alternatives (System 76 or Zareason) or build your own.
Currently Dell does not need Ubuntu but Ubuntu does need Dell. 
Since I like cars... 
Say I just came up with a new engine design, its better than other engines for some reason, not important why. However most big companies have their own engine designs and don't want to buy mine. So say Audi comes to me and says we want your engine in some of our models. Do you expect Audi to redesign their line up and design engine mounts and bell housings to fit my motor? No, it is up to me to make sure that the product I'm trying to sell works with my main partner. 
> I disagree with your assessment of fela. I also enjoy hands on (bare bones or self built) and have been in the electronics diagnosis field for decades. Suggesting fela is young or immature - is demeaning and unnecessary. Perhaps, you chose the wrong field of endeavor, if you don't enjoy your profession.
I did not say he was immature, I said he was young (possibly). Two do not necessarily go hand in hand. The reason I said that when one gets older one generally has more demands on one's time. For instance with commute I have 11 hours a day that do not belong to me. When I get home there are errands to run, time I want to spend with g/f, things around the house that need taking care of.
> to say that you are an experienced linux user and have been a member since linux was a unknown quantity and the support wasn't nearly as good as it is now. i find it strange that you do not like fixing issues yourself because it seems highly likely that you have had to fix issues.

One gets tired :)
> So to the OP, what are you saying? Linux or Ubuntu devs should bribe OEMs to develop drivers for Linux? I'm not a developer but I know that it's incredibly hard (and sometimes literally impossible) to code drivers for a product you don't even know the design specifications of. Again, the Linux devs have done a marvellous job at this thus far and I can't believe people are expecting anything more.
The fingerprint reader is the same one that ThinkPads use and has Linux drivers. The problem is not the drivers the problem is hardware that can use those drivers. On 8.10 I had to change config files and had to more or less guess some of the options. For instance it matters WHERE in the file you put the config line you might end up with it requiring BOTH a password and a fingerprint (very secure though). On 9.04 I was unable to get it to work at all despite Gnome allegedly having built in support for fingerprint authentication.

All the drivers on this laptop were found in both Ubuntu and Win 7 out of the box. However my video car was blacklisted for Compiz for unknown reason (it was not in a previous release). Considering that Dell has only a couple of laptops Canonical should have purchased the hardware for testing.

I've had alot of issues on the software side, like I mentioned BT Audio is damn near impossible. Network Manager although supposedly allows for setting up a BT DUN connection that works with smart phones doesn't seem to have a mechanism to actually start it. There is absolutely no easy way to recode videos, Avidemux is great but it requires quite a bit more knowledge about A/V encoding than I have or care to get as I only do it for recreation.

For some reason the 9.04 release was very bad to me even though I had Ubuntu as my main OS for 3 years. 

I noticed an interesting thing. It seems most of you compare Ubuntu to XP, which is very interesting considering that XP is something like 7-8 years old at this point. 

I am wondering if any of you had a chance to check out Win 7 RTM yet and give an honest opinion. I didn't make my decision overnight. I installed it on my old tablet and was very impressed with how well the OS was made. I also read reviews from my peers who have tried. On another site that I frequent (car forum) there are countless people who have OS X and various flavors of Linux both of the sides have good things to say.

iRun, 
Taking it a bit personal aren't you?

---

### Post by running_rabbit07 on 2009-08-18
> **prizrak said:**
> When I get home there are errands to run, time I want to spend with g/f, things around the house that need taking care of.

One gets tired :)

You forget that most of these guys sit at home and do nothing while their parents or spouses take care of things. I know quite a few people that sit in front of their system all day and contribute nothing to their household. I would hope this doesn't apply to anyone here, but it is likely.

And yes, my house is spotless.

---

### Post by Tamlynmac on 2009-08-18
prizrak

> How is taking a good idea and emulating it a bad thing?

your interruption of a good idea. Let's keep in mind, when making statement such as this - your assuming everyone else agrees.

> Currently Dell does not need Ubuntu but Ubuntu does need Dell. 

Again your interruption of what you consider a reality. I disagree and don't believe Ubuntu/Linux needs Dell.

> 
I did not say he was immature, I said he was young (possibly). Two do not necessarily go hand in hand. The reason I said that when one gets older one generally has more demands on one's time. For instance with commute I have 11 hours a day that do not belong to me. When I get home there are errands to run, time I want to spend with g/f, things around the house that need taking care of.

Again, another assumption based on your own beliefs. How would you know how much free time fela has available. Perhaps fela's schedule may make yours appear mundane. I've learned never to assume anything.

You implying that simply by getting older the time demands on one's life increase. I know a number of young people who might argue that statement. When considering a young person may have comments to sports, a job, school, a GF and of possibly parents, It's realistic to believe that their daily schedules may make yours appear to be walk in the park.

---

### Post by fela on 2009-08-18
> **Tamlynmac said:**
> Again, another assumption based on your own beliefs. How would you know how much free time fela has available. Perhaps fela's schedule may make yours appear mundane. I've learned never to assume anything.

Good philosophy, but he's right: I'm 13 and home educated, and loving it!

---

### Post by prizrak on 2009-08-18
> You forget that most of these guys sit at home and do nothing while their parents or spouses take care of things. I know quite a few people that sit in front of their system all day and contribute nothing to their household. I would hope this doesn't apply to anyone here, but it is likely.

And yes, my house is spotless. 
Hehe my house is spotless as well and so is my car :D 
> your interruption of a good idea. Let's keep in mind, when making statement such as this - your assuming everyone else agrees.
I believe the word you are looking for is interpretation. Interruption is a synonym for interference. 

fela,

I hope you understand I meant no offense just making an educated guess :D I am glad to see that your generation is embracing FLOSS and perhaps you can make Ubuntu what it should be :D

There doesn't seem to be anything constructive going on in this discussion anymore. Those who disagree with me will not see my point no matter how much I explain it. Anyway my thoughts on the subject are clear, at present MS has the upper hand I guess billions of dollars in R&D funds and a 95% userbase count for something :lolflag:

---

### Post by Tamlynmac on 2009-08-18
> fela
Good philosophy, but he's right: I'm 13 and home educated, and loving it! 	

My point was and still is that one should not make assumptions. We all have the potential of a busy schedules (except for iRun :P) and to assume that my schedule is more hectic than others, is foolish.

I've worked many a sixty and seventy hour work week when I was young and doubt that's anything special.

Just my $0.02

---

### Post by dtoronto on 2009-08-18
I still have yet to be really impressed by Windows 7, It still seems like a re-hash of Vista.  It seems to me that MS is going a different route anyway now that they're pouring money into their new pet project to compete with Yahoo.

---

### Post by mdsmedia on 2009-08-18
> **prizrak said:**
> I got the machine a month or so before 8.10 came out, timing was due to Dell's limited time discounts and a $300 difference was not something I could afford to pass up. 
The machine came with 4GB of RAM yet had a 32bit OS (Dell's fault not Ubuntu's) As such when 8.10 came out I did a clean reinstall (including my /home) with the x64 version. As a result fingerprint reader didn't work and needed some tweaking. In fact there was a strange issue where you had to hit the return key after swiping your finger because new version broke auto return on swipe. Annoying but fine and was fixed quickly enough. So I install all my favorite programs, set up my wireless and so on. 6 months down the line 9.04 comes out, not wanting to reinstall all my software I did a dist-upgrade. Again fingerprint reader didn't work and I was not able to find ANY guides that helped as think-finger was depricated. The rest of the issues are in the OP. 

I fully suspect that if I did a clean reinstall I would not have as many issues as I did with upgrade. The problem is that with a 6 month release cycle it is not feasible for me to customize the hell out of my OS just to have to redo it for the next version. To make matters worse config files do change from release to release so I couldn't even script it. 

Running_rabit07 got it.
I did not bash the OS. I have pointed out issues that I have personally encountered on hardware that was "designed for Ubuntu". If I was going to bash the OS I would say that it sux because iTunes doesn't work, or that I can't play StarCraft on it. While both are true these issues are down to third party efforts and as such I left them out of my post. 

Dell was a better choice because of discounts I have through work. 3

7 is actually very nice seems as though MS really tried this time around. 

Thank you. I attempted to make my post as constructive and non-bashing as possible, however it seems some people are bit sensitive as Linux does get alot of heat.
Personally, I didn't think your OP was bashing Linux/Ubuntu.

Personally, it would take a hell of a lot to get me to use Windows (by choice) rather than Linux. As I said, earlier, I don't have the same hardware demands that you have and any shortcomings in Linux/Ubuntu, I work around or live with, rather than returning to Windows by choice.

To me it's not pragmatism as much as expedience which draws people back to Windows from Linux, but that's just my personal opinion. I'm in no way criticising your decision, just expressing my position on your decision.

---

### Post by mdsmedia on 2009-08-19
> **prizrak said:**
> There are currently two successful (commercially) OS's on the desktop market. Neither of them has a brand new release every 6 months. I really don't understand why there are so many people who seem to be against extra testing time. Even an extra week or two of testing would help greatly. 

Not sure if you missed this. 
Machine in question is a Dell XPS M1330n, which was ORIGINALLY shipped with Ubuntu (7.10 I think at the time) by Dell. The system uses Intel CPU, chipset, video and wi-fi. I do not expect to have hardware problems with something that came as an Ubuntu. 

I fully understand that with the amount of hardware that Ubuntu has to deal with it is a miracle that it works as well as it does. However it seems to me as if there is a disconnect between the OEM's and Canonical at the moment. Dell is the only large OEM offering Ubuntu as a preinstall and yet it seems that Canonical did not test their releases properly with them. 

Considering that Dell only offers a couple of configurations with Ubuntu I would expect better out of the box functionality.

I could be way off but I would suspect that you are either very young or don't work in IT :)
Just a thought, but if you bought a machine with XP on it, and Vista came out, would you expect the machine to run flawlessly with Vista> Would you expect to just wipe XP and install Vista and have everything run like roses, simply because you bought the machine with Windows pre-installed?

---

### Post by mdsmedia on 2009-08-19
> **running_rabbit07 said:**
> You forget that **_most of these_** guys sit at home and do nothing while their parents or spouses take care of things. I know quite a few people that sit in front of their system all day and contribute nothing to their household. **_I would hope this doesn't apply to anyone here, but it is likely_**.

And yes, my house is spotless.
Interesting contradiction there.

---

### Post by running_rabbit07 on 2009-08-19
> **mdsmedia said:**
> Interesting contradiction there.

Philosophy 102, easy explanation, it is, I hope it isn't , most likely it is 

Not a contradiction. My argument never changed, just added that I hope I am wrong.

---

### Post by mdsmedia on 2009-08-19
> **running_rabbit07 said:**
> Philosophy 102, easy explanation, it is, I hope it isn't , most likely it is 

Not a contradiction. My argument never changed, just added that I hope I am wrong.
You stated it as being the case, then said you hoped it wasn't. That's the contradiction.

---

### Post by running_rabbit07 on 2009-08-19
> **mdsmedia said:**
> You stated it as being the case, then said you hoped it wasn't. That's the contradiction.
It would be a contradiction if I said, "it was," but then said, "it wasn't." Saying, "I hope," isn't changing the possibility of the facts stated.

---

### Post by mdsmedia on 2009-08-19
What does "you forget most of these guys sit around" mean other than that most of these guys sit around?

Then you said "I hope this isn't the case" which basically says, "this **_is_** the case but _**I hope it's not**_", therefore a contradiction.

Anyway, I've explained it. I'm not going to argue about it. It may not have been what you meant, but it is what you said.

---

### Post by Tamlynmac on 2009-08-19
> mdsmedia
What does "you forget most of these guys sit around" mean other than that most of these guys sit around?

Then you said "I hope this isn't the case" which basically says, "this **_is_** the case but _**I hope it's not**_", therefore a contradiction.

Anyway, I've explained it. I'm not going to argue about it. It may not have been what you meant, but it is what you said. 	

Plus, it's offensive and in my opinion meant to be. I'm disabled and some of the meds I take are extremely unpleasant. I can only assist my working wife with household tasks that I'm capable of. So I guess I fit running_rabbit07's definition.

However, I worked for over 40 years of my life supporting my wife and children. Fortunately, my disability occurred late in life. As a productive tax paying head of household for 40 years, should I now apologize for becoming disabled and enjoying what's left of my life by communicating with others in this forum? I'm offended every time someone suggests that because my disability impacts my ability to be productive, that I'm one of those people who sit around and do nothing but type on my puter. Might I suggest before commenting on others - one walk in their shoes.

I forget (probably the meds) what one terms individuals who target others with innuendo and assumptions without any knowledge of their situation. Perhaps mdsmedia, you could refresh my memory.

I wish to take a moment and "THANK" mdsmedia for challenging those that feel it's necessary to ridicule others (others fitting that category - may also be disabled) only to enhance their own ego or prove a point. One can only hope they are never placed in a position of compromise based on a disability and find out just how offensive their words may have been.

---

### Post by mdsmedia on 2009-08-19
> **Tamlynmac said:**
> Plus, it's offensive and in my opinion meant to be. I'm disabled and some of the meds I take are extremely unpleasant. I can only assist my working wife with household tasks that I'm capable of. So I guess I fit running_rabbit07's definition.

However, I worked for over 40 years of my life supporting my wife and children. Fortunately, my disability occurred late in life. As a productive tax paying head of household for 40 years, should I now apologize for becoming disabled and enjoying what's left of my life by communicating with others in this forum? I'm offended every time someone suggests that because my disability impacts my ability to be productive, that I'm one of those people who sit around and do nothing but type on my puter. Might I suggest before commenting on others - one walk in their shoes.

I forget (probably the meds) what one terms individuals who target others with innuendo and assumptions without any knowledge of their situation. Perhaps mdsmedia, you could refresh my memory.

I wish to take a moment and "THANK" mdsmedia for challenging those that feel it's necessary to ridicule others (others fitting that category - may also be disabled) only to enhance their own ego or prove a point. One can only hope they are never placed in a position of compromise based on a disability and find out just how offensive their words may have been.
While I sympathise, I'm sure there were no aspersions meant to be cast at anyone on here, particularly since running_rabbit did not know your situation or that of others.

I really think he said what he said in a way that was not meant to be offensive. Sometimes the typed word can be misinterpreted, and for that reason alone we should be very careful what we say in typing.

BTW, was "casting aspersions" what you meant?

---

### Post by prizrak on 2009-08-19
> **mdsmedia said:**
> Just a thought, but if you bought a machine with XP on it, and Vista came out, would you expect the machine to run flawlessly with Vista> Would you expect to just wipe XP and install Vista and have everything run like roses, simply because you bought the machine with Windows pre-installed?

I thought I was done with this but you brought up a good point. I would not necessarily expect XP hardware to work with Vista. 

However there are two things that are very different in this particular case. 
1) XP to Vista took about 6 years IIRC that is a very long time in IT world as you know :)
2) Windows uses a modified microkernel design, meaning that the kernel hardware drivers are installed separately and are not integrated into the kernel. Linux is a monolithic kernel, which means that all the drivers for all the hardware are part of the kernel. Considering that 9.04 was only a year from 8.04 that the laptop came with I doubt hardware support was dropped from the kernel as the hardware is very far from being deprecated. 

The problems I had were not actually hardware/drivers related. All of my hardware is very generic and is picked up by Ubuntu just fine. The issues were software, thinkfinger got deprecated because of Gnome's built in support for fingerprints and PAM could no longer be used with the fingerprint reader. TF utility however had no problem recognizing my input from the fingerprint reader. 

Another strange thing was wireless. For some reason it would take a full minutes for Ubuntu to authenticate to my AP while OS X and Windows did the same thing in like 10 seconds. 

Then of course there is ACPI. Win 7 takes under a minute to wake up from suspend. Ubuntu took 2-3 minutes. I understand that ACPI is a huge pain to begin with but still its annoying :D

Tamlynmac,

I am sorry to hear about your situation. I don't believe that rabbit was trying to insult anyone. I believe his point was more along the lines that some people have more time to deal with their own PC issues than others and that having a job and family responsibilities tends to decrease the amount of time available to find workarounds and solutions for issues that are only specific to a certain OS. It doesn't necessarily have to be Ubuntu that requires tweaking, it's just that in my case on my main computer it was.

---

### Post by running_rabbit07 on 2009-08-19
> **Tamlynmac said:**
> Plus, it's offensive and in my opinion meant to be. I'm disabled and some of the meds I take are extremely unpleasant. I can only assist my working wife with household tasks that I'm capable of. So I guess I fit running_rabbit07's definition.

I apologize for offending you. What I said was directed to those are voluntarily lazy, which you are not.

---

### Post by K.Y.A on 2009-08-19
I used to have lots of lockups. Sometimes my panels would disappear... Gnome or Nautilus would fail to start. Firefox would grey-out. 

The problem boiled down to my brand-new seagate drive. I sent it back to seagate, and they sent it back with a green sticker on it saying that it was fixed.

I paid $13 for a green sticker. :( It was not fixed. I installed Leopard on it and now Leopard crashes constantly because of the drive failing. Every week I have to run fsck.hfsplus or Apple's Disk-Utility on it. It was a pretty nice sticker though.
Thanks Seagate!!!

I put Ubuntu on my new $30 WD drive. Works like a charm. Only prob is that after installing Nvidia drivers, I can't start Gnome. If I start it, Gnome will not have window boarders, and if I run metacity --replace then the window boarders appear, but the panel crashes. Then the screen fills with dots and symbols. 

KDE4.2 and all my games work fine, though. The drivers installed fine. KDE doesn't lock up for me like Gnome, and it feels much more profesional. I have no idea what happened to Gnome... I just know I'm not using it anymore :P.

My point is, Lockups can occur because of anything. Bad hard drive, corrupted partitions, missing libraries or dependencies, Kernel-to-hardware issues, you name it.
Someday perhaps Ubuntu will be the perfect operating system everyone claims it is, but right now, it's not. Windows 7 worked okay for me, but I missed knowing how the roots of the system worked. If something breaks in Ubuntu or NetBSD, I know how to fix it. In Windows, I go strait to Google. With all of MS's resources, they should be able to beat Ubuntu in security or stability, but they can't. They don't want to, they just want the customers to choke up the cash for it and be happy.

Ubuntu ftw! :popcorn:

---

### Post by HappyFeet on 2009-08-19
> **K.Y.A said:**
> I have no idea what happened to Gnome... I just know I'm not using it anymore :P.


It's OK if you no longer like gnome, and prefer KDE, but don't be so quick to rush to judgment. After all, there are many more people using gnome than kde (at least in ubuntu). And in my 40+ installs of ubuntu (gnome) I have never had the problem you speak of. Chalk it up to bad luck and nothing more. Good luck and enjoy Kubuntu.

---

### Post by K.Y.A on 2009-08-19
> **HappyFeet said:**
> It's OK if you no longer like gnome, and prefer KDE, but don't be so quick to rush to judgment. After all, there are many more people using gnome than kde (at least in ubuntu). And in my 40+ installs of ubuntu (gnome) I have never had the problem you speak of. Chalk it up to bad luck and nothing more. Good luck and enjoy Kubuntu.

KDE isn't the only interface I use. And I really don't use Kubuntu, I just use KDE4.2. I use almost all my Gnome apps instead of the K* ones. The naming of Kde apps is just silly. 
Kalculator
Konqueror (although an awesome file manager)
Krap

Who takes that seriously? Bad luck, eh? I have this issue on several Gnome installs. I'm no n00b at user interfaces and such. I got Gnome running on NetBSD (before the bootmanager crashed and I haven't gotten around to reinstalling it) and it ran great. I use Fluxbox on Ubuntu sometimes.

I really don't understand your harsh reaction to my post. . . It's just a user envoironment. I was making the point that it doesn't matter what OS you use, you will always have issues. Windows has it's faults, and so does Mac and Linux. That's what my point was.

---

### Post by HappyFeet on 2009-08-19
> **K.Y.A said:**
> 

I really don't understand your **harsh reaction** to my post. . . 

Harsh reaction? Where did that come from? I was being calm, collected, civil, and with no ill feelings whatsoever. Why you thought my reaction was harsh is beyond me.

Oh well, time to move on. Have a nice day everyone. :P

---

### Post by K.Y.A on 2009-08-19
> **HappyFeet said:**
> Harsh reaction? Where did that come from? I was being calm, collected, civil, and with no ill feelings whatsoever. Why you thought my reaction was harsh is beyond me.

Oh well, time to move on. Have a nice day everyone. :P

You too. :)

---

### Post by Tamlynmac on 2009-08-21
> mdsmedia
BTW, was "casting aspersions" what you meant? 	

:rolleyes: No I don't think so, but close enough. 

I guess one should never generalize as it can potentially be misinterpreted. The fact is, this statement could apply to others in a similar situation. I must assume based on all the responses, that it was not a deliberate attempt to demean anyone.

Perhaps, just a misunderstanding. :-k

---

### Post by HappyFeet on 2009-08-21
> **Tamlynmac said:**
> :rolleyes: No I don't think so, but close enough. 

I guess one should never generalize as it can potentially be misinterpreted. The fact is, this statement could apply to others in a similar situation. I must assume based on all the responses, that it was not a deliberate attempt to demean anyone.

Perhaps, just a misunderstanding. :-k

Perhaps people like us are becoming dinosaurs. 

I no longer feel the need to defend my choice of OS. It is the most perfect thing I've ever used. Yeah, I realize that a lot of people come from windows, and are happy in their fragmented, virus ridden, "live in fear" mentality. Oh well. I'm just glad I'm not one of them. There's a reason people call me to fix their computers. Windows is FAR from perfect. If it was closer to perfect, I'd be out of a job.

---

### Post by Tamlynmac on 2009-08-21
> HappyFeet
Perhaps people like us are becoming dinosaurs. (I'm sick of young punks with nothing to show)

You may be right. As you know I've been Windows free for >3 years and don't understand all the bloat idealists. As you, I have no desire for Ubuntu/Linux to ever emulate Windows. Once an individual adapts to the Ubuntu/Linux train of thought, it's much more intuitive that Windows IMHO.

Being a dinosaur has it's advantages. You and I have been around the block a few times and already know many of the pitfalls. Education comes in multiple forms (books, teaching, etc.). However, experience only comes in one, the actual process of hands on task completion. Education can never replace hands on experience IMO. Until one actually experiences something, everything else is just a belief founded in information shared by others.

Please don't misunderstand, I'm a big fan of education - I'm also a big fan of experience, as it's the link that integrates education with reality. As a ex-SEM and Process Controls Eng. I've found education extremely valuable, but I've found experience to be essential.

You choice of career provides you with the opportunity to witness the plight of Windows users on a regular basis. Thus, I must defer to your experience when considering said plight. All I can comment on is myself and those ex-Windows users that I've assisted in installing/running Ubuntu.

Have a good day my friend.

---

### Post by mdsmedia on 2009-08-21
I'm going out to do my first Ubuntu installation for a friend replacing Windows, today.

Her computer is virus-ridden, she has basic PC needs, and she can't find her Windows installation disk.

I'll back up her beloved photos and anything else she wants to keep, and clean install Ubuntu on the entire disk.

My first real convert :).

The beauty of it is, she is a computer newb and it won't make any difference to her what OS she's using.....As I said, basic needs, and Ubuntu should shine for her. Her daughter has a new EeePC with Linux (701 version), so they'll be a 100% Linux family :). No indoctrination required. Same assistance as if she had any other OS. Her daughter won't be brought up thinking that there is only one OS. Hopefully the ridiculous education system won't demand that she use Windows for some assignment down the road.

---

### Post by Old_Grey_Wolf on 2009-08-21
> **mdsmedia said:**
> Hopefully the ridiculous education system won't demand that she use Windows for some assignment down the road.

I wish them luck with the education system. It is not only a Microsoft vs Linux issue.

My daughter took classes in graphic design. The University required that the students us a MAC even though programs like Photoshop run on a PC. I had to buy a MAC and MAC compatible peripherals; such as, printer and scanner. The cost of this stuff, we never used after she completed her education, was outrageous. 

There are some good teachers; however, the "ridiculous education system" can get in the way.

---

### Post by solwic on 2009-08-21
> **Tamlynmac said:**
> You may be right. As you know I've been Windows free for >3 years and don't understand all the bloat idealists. As you, I have no desire for Ubuntu/Linux to ever emulate Windows. Once an individual adapts to the Ubuntu/Linux train of thought, it's much more intuitive that Windows IMHO.

Being a dinosaur has it's advantages. You and I have been around the block a few times and already know many of the pitfalls. Education comes in multiple forms (books, teaching, etc.). However, experience only comes in one, the actual process of hands on task completion. Education can never replace hands on experience IMO. Until one actually experiences something, everything else is just a belief founded in information shared by others.

Please don't misunderstand, I'm a big fan of education - I'm also a big fan of experience, as it's the link that integrates education with reality. As a ex-SEM and Process Controls Eng. I've found education extremely valuable, but I've found experience to be essential.

You choice of career provides you with the opportunity to witness the plight of Windows users on a regular basis. Thus, I must defer to your experience when considering said plight. All I can comment on is myself and those ex-Windows users that I've assisted in installing/running Ubuntu.

Have a good day my friend.

Have we become dinosaurs?  I'd hate to think that the current trend has become the norm.  

Scary, innit?  

Still, I'm with you guys.  I don't give a rat's fart what OS someone uses.  They can use what they like.  The thing with all this "choice" we all talk about is that it cuts both ways.  Anybody at all is perfectly free to choose Windows over Ubuntu if they like.   

Me, I'll stick with my 'buntu and be happy that there are still a few "dinosaurs" around here to talk to.  :biggrin:

---

### Post by vedek on 2009-08-22
> **iRun said:**
> Have we become dinosaurs?  I'd hate to think that the current trend has become the norm.  

Scary, innit?  

Still, I'm with you guys.  I don't give a rat's fart what OS someone uses.  They can use what they like.  The thing with all this "choice" we all talk about is that it cuts both ways.  Anybody at all is perfectly free to choose Windows over Ubuntu if they like.   

Me, I'll stick with my 'buntu and be happy that there are still a few "dinosaurs" around here to talk to.  :biggrin:

+1

Everybody needs a dinosaur

---

### Post by SunnyRabbiera on 2009-08-23
> **prizrak said:**
> 

> Release cycle:
There has been quite a bit of controversy about this in the past and I used to think that it is great. A new OS every 6 months! All the bells and whistles, kernel improvements, new drivers and so on. However, the more I use the OS the more I think that the 6 month release cycle is a mistake.


For one the upgrade mechanism is still far from perfect (as it is on any OS), however with releases following each other so closely it has to be absolutely perfect. Reinstalling the entire OS and any software that one is accustomed to as well as redoing all the customization every 6 months is just not practical for people who have jobs and significant others as it takes too much time. 

A longer release cycle would also allow more room for testing. For instance a large part of the below list suggests that developers did not do much testing with Dell, which is strange considering that Dell is the only big consumer oriented OEM that offers Ubuntu as a choice. 

As a corollary to this, lack of availability of new software. Firefox 3.5 has been out for months and as of last week was still not available in Ubuntu. Yes it is very easy to install it into your /home directory or wherever but Ubuntu has a very powerful repository system, which is not being used to its full potential.

I would suggest an 18month release cycle with all major applications being available in the repositories shortly after the release. Mind you I'm not talking about Gnome here, but things like Pidgin and Firefox SHOULD be available ASAP as opposed to months after.

Well even though I agree that the updater can be improved a little and the release cycle slowed down the Firefox 3.5 issue is something more debatable.
The reason being is that Firefox 3.5 was not a mission critical update, 3.0 is still supported and 3.5 was not a major security update.
Ubuntu does not focus on the "latest and greatest", it focuses on what is last known to be relatively stable.

[QUOTE]
Hardware:
Fingerprint reader - when I got the originally including OS my fingerprint reader worked absolutely fine. Once I installed the next version I had to search for guides on how to get it to work, and even then there were some stupid quirks.

Latest release completely broke the functionality, I had been unable to find any guide that would work and while I had heard that Gnome now has support for fingerprint recognition as part of the login process I was unable to find any information on how to actually enable it.

This might be more of a hardware issue

> 
USB: 
This deserves its own section because its idiotic. Any transfer of files over USB took forever. It took me 4 hours to transfer 6GBs of data from my laptop to my USB flash drive. Operation that I repeated on the same machine after installing Win7 and it took about 10 minutes.... A friend of mine had the same issue...

I'm sure there is some solution to this but frankly I didn't want to bother this is entirely too basic to require digging around for a fix...

I never had an issue with file transfer.

> Bluetooth: 
Works fine out of the box, unless you want to use it.... A2DP (BT Stereo) support is atrocious... The included utility could not pair my headphones and in order for me to even get BT audio working I had to write a shell script that would connect to my headphones and enable BT. To make matters worse I had to install a separate utility to force audio streams to BT in order to use it. When BT was disconnected sound would still be sent to it unless I go to the utility AGAIN and change it.

Just as a contrast to this, on Win7 I paired my headphones and set them as the default device for any audio playback. Anytime they are connected all the audio is rerouted properly. Upon disconnect audio is rerouted over to the built in speakers. As a bonus this works on the fly no restarting applications.

Sigh, now you are nitpicking.
Ubuntu is not windows, so obviously not all hardware will work 100% in it

> 
HDMI:
This particular machine comes with an HDMI out that carries a/v data (as opposed to just video as most video cards). Ubuntu thought my 42" TV was a 7" inch monitor with a 1920x1080 resolution. I won't even mention [lack of] sound.

Again to contrast Win7 changed resolution to 720p, cloned the screens and rerouted all the audio via HDMI. All I had to do was plug the cable in, nothing else.

Again hardware related

> Speed:
One of the biggest reasons why I originally went to Linux in general and Ubuntu in particular was efficiency/speed of the OS. Somehow it is now gone. Granted I did not do a fresh install and there is a possibility that it would have worked better if I did but going back to my original point if releases are to be kept this short the upgrade mechanism MUST be perfect. 

I experienced random lock ups that would last for a few seconds. Random lock ups that required a hard power down. Random lock ups that resulted in the machine not shutting down completely. Random lock ups on wake up from suspend. This is ALL on a machine that was designed for Ubuntu. 

I have also had Firefox randomly lock up on me and mess up formatting of one specific site. Issue I did not experience with the same version on my office PC running XP Pro. 

I suspect that an upgrade to 3.5 might have fixed that particular issue, however that goes back to locked down repositories. I do not want to go outside of the repositories this makes the entire idea of them obsolete.

As a contrast Win7 ran faster than both Ubuntu and XP on my 4 year tablet PC. It is also noticeably faster on my main machine.

I never had issues with speed in linux

> 
Looks:
We can deny it all we want but looks are important. Composited desktop looks good but it falls a bit short. Windows' Aero interface uses the GPU for everything including font smoothing making it look very very good. Ubuntu on the other hand seems to only use the GPU for special effects and the rest *looks* like it is software rendered.

Now you are asking for it, look the world is not all ab \out crystalline interfaces, fancy effects and all that.
I like functionality and so far Aero has failed me on that respect.
Look windows 7 is a beta, once the full version comes out I bet in the first 3 months it will face the same issues windows always had:
Viruses, adware, spyware, junkware, security bugs that wont be fixed for 50 years.
And now I hear Win7 will be subscription based if you dont do one of the bloody "premium" versions starting at $119.99 USD.
I mean come on I can get a copy of Ubuntu for free or buy something from the ubuntu store to support the improvement of the OS.
Just wait Win7 will falter...

---

### Post by Stavro on 2009-08-25
> **prizrak said:**
> USB: 
This deserves its own section because its idiotic. Any transfer of files over USB took forever. It took me 4 hours to transfer 6GBs of data from my laptop to my USB flash drive. Operation that I repeated on the same machine after installing Win7 and it took about 10 minutes.... A friend of mine had the same issue...

Hi there, I do tend to agree with you. I find that Ubuntu doesn&#8217;t handle external hard disks very well, the speed is abysmal... seemingly being even slower than USB 1.1 specification. Perhaps this is related to bad motherboard drivers or something, the USB stack might be fine but different motherboard drivers will yield different results for some people.

Finally, I have to agree with you about the upgrader, my experience with it has been exceedingly dangerous. I remember upgrading an early distribution, perhaps 6.10 to 7.04 and it failed half-way through. Afterwards, I could still boot the previous version but many files were damaged. Maybe this was a corrupted file-system or the kernel code to access the disk was affected detrimentally. Jpg pictures partially loaded stopping with that classic grey which often resembles corruption, some mp3s played just a little.

---

### Post by Methuselah on 2009-08-25
Wow, so many sentiments on this page match mine.
I don't care what OS people use and I'm not intent on converting them.
I'm just mildly amused when I hear people talking about things that don't affect me in the least.

---

### Post by Dullstar on 2009-08-26
> **running_rabbit07 said:**
> Glad to hear Windows 7 is stepping up a bit. I think gates realized his people needed to make a better system than Vista.

Didn't Bill Gates retire?  Now Steve Ballmer, the chair tossing potty mouth is in "Rich Bill's" place.

---


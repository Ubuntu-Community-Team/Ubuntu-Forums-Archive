---
title: "I give up"
date: 2009-11-24
forum: Testimonials &amp; Experiences
---

### Post by nancy143 on 2009-11-24
[SIZE=3]Ok I give up after two weeks of trying I am done. [/SIZE]
[SIZE=3]Does anyone know how I uninstall Ubuntu and get rid of the dual boot. I will try it again when I learn more about computing but for now I'm done[/SIZE]

---

### Post by scorp123 on 2009-11-24
[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by Muskegman on 2009-11-24
If you gave a few details as to what problems you were having someone may have been able to help. nobody can help unless you ask

---

### Post by Lvcoyote on 2009-11-24
Man, I know how you feel.  When I first started with Linux I was so frustrated and confused that it seemed it wasnt worth it.

I will tell you to stick with it and post your questions here and the fine folks here will help, lord know they helped me many times.  I also used the crap out of google to find solutions.  I figured when most of my google searches pointed to a thread on these forums, I'd better join up......LOL

---

### Post by goldshirt9 on 2009-11-24
> **Lvcoyote said:**
> Man, I know how you feel.  When I first started with Linux I was so frustrated and confused that it seemed it wasnt worth it.

I will tell you to stick with it and post your questions here and the fine folks here will help, lord know they helped me many times.  I also used the crap out of google to find solutions.  I figured when most of my google searches pointed to a thread on these forums, I'd better join up......LOL

this is so true :)

---

### Post by kansasnoob on 2009-11-24
> **nancy143 said:**
> [SIZE=3]Ok I give up after two weeks of trying I am done. [/SIZE]
[SIZE=3]Does anyone know how I uninstall Ubuntu and get rid of the dual boot. I will try it again when I learn more about computing but for now I'm done[/SIZE]

Four beans and you're ready to give up?

Are you still able to boot into your Windows?

What version of Windows?

Are you sure you want to just ditch Ubuntu?

We'll be glad to help but we need more info.

---

### Post by Lvcoyote on 2009-11-24
Yea, just leave the dual boot thing going and take it step by step with Ubuntu, keep trying and ask questions, eventually you'll get a handle on it.

---

### Post by kansasnoob on 2009-11-24
I see from one of your posts that you had a dual boot and ditched it.

Is that true?

Why?

After 22 months I still have my Windows. I don't use it but it's there!

---

### Post by lisati on 2009-11-24
Hang in there! When I first looked into Linux I found it a little bit daunting. Then I eventually discovered Ubuntu and these forums. Two years later, I'm still here!

---

### Post by UnknownFear on 2009-11-24
Don't ditch Ubuntu. Tell us what the problems are and we will try to help you. In all seriousness, when I first started, like many users here have said, I had a hard time with it and said screw it, and went back to Windows. I know a lot more about it than I did when I first tried it and joined these forums. This place has help me a countless number of times, and I encourage you to please, stick with it and give it a fair shot. Leave the dual-boot and see what Linux really has to offer.

---

### Post by coffeecat on 2009-11-24
While I can understand everyone urging the OP to hang in there with Ubuntu, it seems discourteous not to answer the OP's question.

**nancy143**, it's a fairly simple two-step process.

1 - repair the Windows mbr so that you can boot into Windows without grub.

2 - delete the Ubuntu partitions and reuse the space.

You probably don't have a Microsoft Windows install disc, so the best way to repair the mbr is to download [SuperGrubDisk]("http://www.supergrubdisk.org/"). Boot up with it. There are two Windows options in the rather obscure menu - one to simply boot up Windows, the other to repair the mbr and then boot up Windows.

Once you've got Windows booting up without the grub menu, it's time to delete the Ubuntu partitions.

Boot up with the Ubuntu live CD (yes, that's right) and go to System > Administration > Gparted (Partition Editor). Delete the two Ubuntu partitions. You can now either expand your Windows partition into the freed space, or you could make another NTFS partition, which will be seen by Windows as E:\ or F:\ or whatever.

**Edit:** if you decide to expand the Windows partition using Gparted, make sure that you have a CD/DVD or recovery partition to be able to reinstall Windows if something goes wrong. It probably won't, but occasionally something can go wrong when editing a partition.

---

### Post by presence1960 on 2009-11-24
> **coffeecat said:**
> **_While I can understand everyone urging the OP to hang in there with Ubuntu, it seems discourteous not to answer the OP's question._**

**nancy143**, it's a fairly simple two-step process.

1 - repair the Windows mbr so that you can boot into Windows without grub.

2 - delete the Ubuntu partitions and reuse the space.

You probably don't have a Microsoft Windows install disc, so the best way to repair the mbr is to download [SuperGrubDisk]("http://www.supergrubdisk.org/"). Boot up with it. There are two Windows options in the rather obscure menu - one to simply boot up Windows, the other to repair the mbr and then boot up Windows.

Once you've got Windows booting up without the grub menu, it's time to delete the Ubuntu partitions.

Boot up with the Ubuntu live CD (yes, that's right) and go to System > Administration > Gparted (Partition Editor). Delete the two Ubuntu partitions. You can now either expand your Windows partition into the freed space, or you could make another NTFS partition, which will be seen by Windows as E:\ or F:\ or whatever.

**Edit:** if you decide to expand the Windows partition using Gparted, make sure that you have a CD/DVD or recovery partition to be able to reinstall Windows if something goes wrong. It probably won't, but occasionally something can go wrong when editing a partition.

+1 

Coffecat, I agree 100%. If someone does not want Ubuntu for whatever reason, let them be. If they need help removing Ubuntu then help them. To do otherwise may spoil a later opportunity to help. I encourage people to stick with it, but only if they display the desire and/or willingness to do so. *_Personally it does not matter to me if another person uses Linux. But if someone wants help I gladly try to help._*

---

### Post by coffeecat on 2009-11-24
**presence1960**, thanks for that.

> **presence1960 said:**
> If they need help removing Ubuntu then help them. To do otherwise may spoil a later opportunity to help.

And a +1 from me.

By the way - with regard to your sig and your thoughts...

*I have no neutral thoughts.*

---

### Post by Chris Edgell on 2009-11-24
Hi Nancy,
I've been around this Linux/Ubuntu for a year and a half.  But I am SUCH a beginner, I seem to be coming to this forum for help very frequently.  I just want to let you see where I am coming from.  

If I were you, I would not even know how to proceed with those instructions that coffeecat gave you.  I was totally daunted and wondered if that's how you felt.  (Although you may have been able to follow what that person was saying.

If you can follow those instructions, and want to...well, thre you go.  But I'm with those first responses you received.  If you have the time and patience, hang in here.  Feel free to state, if you need to, as I do:  I have NO idea what you just said, you're going to have to take me through it step by step.  As so many said, just state what you need and you'll receive so much help.

BTW [by the way] what version did you install?  Did anybody help you?  Did you say if you used a CD for the download?

Best wishes

You can click on anyones name, there on the left and find their profile and their posts, if you're interested.  I've forgotten what you can and can't do and how much time you have to solve your problems.  Again, good luck

---

### Post by presence1960 on 2009-11-25
> **coffeecat said:**
> **presence1960**, thanks for that.



And a +1 from me.

By the way - with regard to your sig and your thoughts...

*I have no neutral thoughts.*

I see you are familiar with ACIM. It is my path, though sometimes I wish I never encountered it's teachings :D. Old habits are sometimes very entrenched and I go to great lengths to defend them!

---

### Post by presence1960 on 2009-11-25
> **Chris Edgell said:**
> Hi Nancy,
I've been around this Linux/Ubuntu for a year and a half.  But I am SUCH a beginner, I seem to be coming to this forum for help very frequently.  I just want to let you see where I am coming from.  

If I were you, I would not even know how to proceed with those instructions that coffeecat gave you.  I was totally daunted and wondered if that's how you felt.  (Although you may have been able to follow what that person was saying.



Well whether you could follow them or not is not the issue. nancy asked how to remove ubuntu and restore windows as sole OS. That is how you do it if you wish to do so.

Actually coffecat is the only poster here who actually answered her question! If she wanted to keep using linux she would have said so. her request was to get her machine back to windows. Coffecat fulfilled that request instead of trying to defend why she should keep using Linux. Now if she changes her mind and decides to stick with linux- great. but that was not the purpose of her asking for help.

---

### Post by suiwo on 2009-11-25
Hi,
Maybe we can be friends,OK?
I am Chinese,and I am new to ubuntu.Don't give up.Let us Common Progress in Linux.
I know that we can!!![http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by presence1960 on 2009-11-25
> **suiwo said:**
> Hi,
Maybe we can be friends,OK?
I am Chinese,and I am new to ubuntu.Don't give up.Let us Common Progress in Linux.
I know that we can!!![http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

The best way to make friends & acquaintances is to become active in this community. Writing your first post was a decent start. The only way people will get to know you is for you to be active in here. This community has afforded me the opportunity to learn more about Linux & computing in general than I ever could have learned on my own. In the process I have made a few friends in here also. Jump in & get involved!

---

### Post by SoapySam on 2009-11-25
Nancy, if you have a single OS - ie Linux only, not a dual boot- and if you are moving to Windows 7 it's easy. Boot from the Windows DVD. Select the custom install (not upgrade). This lets you into a very simple partition editor which you can use to delete the Linux partitions. It will reformat them as NTFS by default.
Make sure you copy any files you want to an external drive beforehand,  as this install will wipe the lot. 
The same may apply to Vista- I don't know, as I never installed it. Windows 7 is a better OS anyway (than Vista)- as a recent convert from my XP holdout position, I recommend Win 7.

It is easier to dual install Linux with Windows installed than to install Windows alongside Linux, so you can always reinstall Linux when you feel like it.



  I do feel it's vital when asking someone to try a new OS that there should be a clear and easy way back if things go wrong- or for whatever reason they choose to revert.

I just looked in Mark Sobell's "Practical Guide to Ubuntu Linux". The word "Uninstall" does not appear in the appendix. [I]This is an 1140 page book. 
[/I] 
That's not user friendly.

I'm currently installing Windows 7 on an ASUS Eee901. As I'm doing this *precisely to compare performance with Ubuntu "Easy Peasy",* the Linux distro had to come off as the mere presence of one OS will affect the other.   Now-I've had 4 different Operating Systems on this ASUS, not counting the Linux Lite version it came with. 
While Ubuntu *installed* easily  (and I'm generally impressed by it) - it has proved the trickiest to [I]uninstall.

[/I]This is an Ubuntu forum and The enthusiasm of the posters is predictable and  laudable, but people do swap OS for many reasons and should be* encouraged to do so*. The more they try, the more confident they get in trying others. Ability to uninstall is a big part of that and should (IMO) be stressed more prior to installing.

---

### Post by coffeecat on 2009-11-25
I'm puzzled....

> **SoapySam said:**
> While Ubuntu *installed* easily  (and I'm generally impressed by it) - it has proved the trickiest to *uninstall.*

If I'm reading you correctly you are saying that you are replacing Ubuntu with Windows 7, yet in your first paragraph you told us how easy this was. :-k

---

### Post by SoapySam on 2009-11-25
Correct. 
 The way I mention is easy if you have a basic knowledge of partition editors and don't mind wiping everything on the drive- which is what I want to do anyway. So it's easy to that extent- but getting Linux off a dual boot machine can be a lot harder. 
As a Windows user, I'm in the habit of doing "Clean installs" anyway, but it may not be what Nancy needs.
Kudos for your reply to her, by the way. You answered her query instead of advising her to hang in there (which can, at times, be as annoying as "Buy a Mac") . She aims to try again when she feels ready , which is great.
I'm a noob to Linux too, by the way. I've tried it a couple of times, never had the time to get to grips and -yes- I've found it hard to get back. The clean install route is always best I reckon.

---

### Post by bodhi.zazen on 2009-11-25
> **nancy143 said:**
> [SIZE=3]Ok I give up after two weeks of trying I am done. [/SIZE]
[SIZE=3]Does anyone know how I uninstall Ubuntu and get rid of the dual boot. I will try it again when I learn more about computing but for now I'm done[/SIZE]

Moved to T&E ;)

You have been advised already on how to remove Ubuntu, the hardest part really is restoring the Windows MBR, you need a windows disk to do this.

If you do not have a windows install disk, just post back, there are work arounds for that as well.

I understand how you feel, I had the same experience the first time I installed Linux, it is frustrating to learn a new OS.

Good luck with Windows.

If you ever wish to try Linux again, keep a few things in mind :

1. Learning a new OS can take time. I would say it takes up to 3 months.

2. IMO 99.9 % of bad experiences comes form hardware incompatibility, so do your research first. This is true of any OS, try running windows on a ppc (mac).

3. You can try Linux without rebooting if you use somethign like VirtualBox or VMWare.

4. Most people dual boot at least until they are comfortable enough to use Ubuntu full time.

5. Last, Linux is not a drop in replacement for windows. There is a long list of windows applications that either run poorly or not at all on Linux. So it helps if you are familiar with the Open Source applications before you transfer. You can run many of these apps on windows and examples include Firefox, Thunderbird, and Open Office. Running these applications in Windows often has additional security advantages as well.

So good luck and come on back when you are ready.

---

### Post by a_z1_9scores on 2009-11-25
> **Lvcoyote said:**
>  I also used the crap out of google to find solutions. I figured when most of my google searches pointed to a thread on these forums, I'd better join up......LOL
 
Same here. When you're learning to ride a bike, you'll mess up...alot. You'll fall a couple of time and contemplate going back to walking, but sooner or later, you'll learn to ride that bike, and when you do, you'll see it's faster, better, and more fun than walking.

---

### Post by SoapySam on 2009-11-25
> **a_z1_9scores said:**
> Same here. When you're learning to ride a bike, you'll mess up...alot. You'll fall a couple of time and contemplate going back to walking, but sooner or later, you'll learn to ride that bike, and when you do, you'll see it's faster, better, and more fun than walking.

True- but if you have been *driving* competently for a few years, you need a different reason to learn to *cycle*.
The reasons are there;- cost , environment, fitness - and good reasons they are, but on a wet and windy day, it takes dedication to get the bike out of the garage and leave the motor at home! (Even if the bike is faster in traffic.)

---

### Post by Chris Edgell on 2009-11-25
BUT ... where is Nancy?

---

### Post by bruno9779 on 2009-11-25
> **Chris Edgell said:**
> BUT ... where is Nancy?

This is the typical hit and run rant from someone with less than 10 posts.

Do you really expect nancy to be back?

---

### Post by thiebaude on 2009-11-25
To the OP: why not just wipe the whole drive and install windows and be with it.

---

### Post by gdonwallace on 2009-11-25
Without having more information about the problem, the only thing I can suggest is to boot up with the LiveCD, and choose the first option Install Ubuntu.

However; this will wipe out everything on your computer.  Any windows files any Ubuntu files, everything.  You will be starting over from scratch.

Give a little more information on the problems your having and we'll be happy to help.

---

### Post by mivo on 2009-11-25
> **bruno9779 said:**
> This is the typical hit and run rant from someone with less than 10 posts.

Ubuntu didn't work for her, she probably managed to uninstall it, and she moved on. Why would she still be posting? It didn't work for her.

For most people, computers are like TVs, toasters, etc. They want their devices to work without any tweaking or dealing with problems. It is reasonable. No single OS is for everyone.

---

### Post by aysiu on 2009-11-25
This is why I recommend Wubi for dual-boots.

How do you remove it? Just as you would any Windows program. No repartitioning. No fixing the MBR.

---

### Post by Jazzy_Jeff on 2009-11-25
> **presence1960 said:**
> Well whether you could follow them or not is not the issue. nancy asked how to remove ubuntu and restore windows as sole OS. That is how you do it if you wish to do so.

Actually coffecat is the only poster here who actually answered her question! If she wanted to keep using linux she would have said so. her request was to get her machine back to windows. Coffecat fulfilled that request instead of trying to defend why she should keep using Linux. Now if she changes her mind and decides to stick with linux- great. but that was not the purpose of her asking for help.

I believe someone left a link that tells them how to do it. Maybe I missed something.

---

### Post by Tamlynmac on 2009-11-25
> bodhi.zazen
Moved to T&E :wink:

I don't understand why you moved this thread to the T&E, when the OP never responded after the original post?

I would think this thread should have remained where it was until the OP responded. The OP may still have questions regarding their original post and might need additional support with regards to the procedure.

Simply because other members added their two cents, doesn't change the fact that this is a help request.

Just a thought. :-k

---

### Post by aysiu on 2009-11-25
> **Tamlynmac said:**
> I don't understand why you moved this thread to the T&E, when the OP never responded after the original post?

I would think this thread should have remained where it was until the OP responded. The OP may still have questions regarding their original post and might need additional support with regards to the procedure.

Simply because other members added their two cents, doesn't change the fact that this is a help request.

Just a thought. :-k
It isn't really a technical support thread. "I give up" is about a bad experience with Ubuntu.

---

### Post by Tamlynmac on 2009-11-25
I must have misinterpreted the thread. I thought the OP was specifically asking for assistance (help) to remove Ubuntu from dual boot.

Based on that perspective, it was unclear why the mod moved the thread. Perhaps, I was wrong in questioning.

I will unsubscribe and not post any further questions on the forum regarding relocating of threads. I respect aysiu's opinion and had no ulterior motive(s) for asking the question.

Thank You aysiu, for taking the time to respond.

---

### Post by aysiu on 2009-11-25
> **Tamlynmac said:**
> I must have misinterpreted the thread. I thought the OP was specifically asking for assistance (help) to remove Ubuntu from dual boot.

Based on that perspective, it was unclear why the mod moved the thread. Perhaps, I was wrong in questioning.

I will unsubscribe and not post any further questions on the forum regarding relocating of threads. I respect aysiu's opinion and had no ulterior motive(s) for asking the question.

Thank You aysiu, for taking the time to respond.
Then thread should be titled "Help me remove a dual boot" and not "I give up."

"I give up" threads always end up as pointless discussions about experiences. "Help me do X" threads end up with technical support.

---

### Post by solwic on 2009-11-25
> **aysiu said:**
> Then thread should be titled "Help me remove a dual boot" and not "I give up."

"I give up" threads always end up as pointless discussions about experiences. "Help me do X" threads end up with technical support.

Well, it seems to me that judging a post by its title is akin to judging a book by the cover, or a person by their clothing, or whatever.  

But whatever.  Just throwin in my 2 cents.  I agree with Tamlynmac.

---

### Post by bodhi.zazen on 2009-11-25
> **Tamlynmac said:**
> I must have misinterpreted the thread. I thought the OP was specifically asking for assistance (help) to remove Ubuntu from dual boot.

Based on that perspective, it was unclear why the mod moved the thread. Perhaps, I was wrong in questioning.

I will unsubscribe and not post any further questions on the forum regarding relocating of threads. I respect aysiu's opinion and had no ulterior motive(s) for asking the question.

Thank You aysiu, for taking the time to respond.

What [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") said.

If you look at this thread, it is not really a support thread any longer.

The OP question was asked and answered long ago (see post #2) and now we just have the lingering cometary.

The OP has not posted back.

So, first I left this thread for over a day in the support section to see if support was needed. 

 T&E is the best location for this thread now as there is no indication to suggest the discussion beyond the first two posts has much to do with technical support.

---

### Post by SoapySam on 2009-11-25
> **aysiu said:**
> This is why I recommend Wubi for dual-boots.

How do you remove it? Just as you would any Windows program. No repartitioning. No fixing the MBR.

 
Aha! This is what's great about forums. Nuggets of information just pop up.  I had not heard of WUBI - I only ever encountered GRUB. 
I presume you mean this-  [http://wubi-installer.org/](http://wubi-installer.org/)   ?

It looks interesting both for noobs like me and experimenters.
Anyone else care to comment or expand on it? Any downside?

++++++++++++++++++++++++++++++++++++++++

As a Windows user and noob to Linux,  I feel this ability to "back out gracefully" is more important than seems to be believed in the Linux-familiar community.

The total beginner to computers may find Linux no more confusing than Windows - but how many such people still exist? Kids learn on Windows boxes at home and in school. Oldsters like me (my first OS was 8bit CP/M) have been forced to learn  DOS and then Windows skills (to whatever level) at work. All of us have invested time and  money in that process. We need incentives to switch.

For some, that's simple curiosity. For others it's resistance (however futile) to assimilation by the Redmond Collective. But that won't do for the majority; they need to be offered something in Linux that M$ doesn't give them.  
I don't know what that is. (But I'm here to learn).
But in the absence of a magnet, there must at least be an open door - and it has to be open in both directions. I'd really urge anyone involved in releasing distributions of Linux to ensure that right up front is a friendly uninstaller, with the words "Don't Panic" in LARGE, friendly letters.

---

### Post by craig10x on 2009-11-25
Wubi is fine and works well..i used it for my first ubuntu (8.10) until i decided to go 9.04 with a hard drive install and wiping windows out completely.....

To me it's only drawback is that it is limited to a maximum of 30 gb.....so if you would be comfortable with that...no problem....it creates a dual boot using windows own boot system and works very well....

---

### Post by Eisenwinter on 2009-11-26
> **bruno9779 said:**
> This is the typical hit and run rant from someone with less than 10 posts.

Do you really expect nancy to be back?
I see no rant in the OP.

But I do see people pointlessly, and even stupidly, trying to convince someone else to stick with Ubuntu, even though that person has made it clear he/she does not want to use Ubuntu any longer.

From all the Linux communities I've been exposed to, this only happens on the Ubuntu community.

This whole "Must gain more users at all costs" approach.

Sure, not everyone here is like that, but the vast majority is, and you can't deny it.

The fact there was no rant, and the post was actually quite polite, is the only reason the OP was not seriously flamed by almost everyone in this thread.

---

### Post by nancy143 on 2009-11-26
[SIZE=4]After reading the replies I did some more checking This is what I figured out my proplem was my, one inexerpirence with the OS and the fact that I had Windows 7 installed it was the beta, I removed windows 7 and reinstalled Vista then booted from the Ubuntu live cd now everthing works like it should after the holiday I am going to install Ubuntu along side vista and see how it works ,I think I won't have a problem I think maby Ubuntu did not reconize Windows 7 drivers and since I am new to Ubuntu I did not know how to fix the problem. I will post my results when I get it done Have a happy holiday[/SIZE]

---

### Post by bodhi.zazen on 2009-11-26
welcome back =)

If you have problems feel free to post questions.

FYI: Please use the normal default size font for your posts. If you are having problems reading the default font, increase the size of your font on your browser (I assume firefox).

Posting in such a large font is considered poor netiquette ;)

---

### Post by Wiebelhaus on 2009-11-26
Only option , Format and reinstall. Good luck.

---

### Post by jdrodrig on 2009-11-26
> **bodhi.zazen said:**
> Moved to T&E ;)

You have been advised already on how to remove Ubuntu, the hardest part really is restoring the Windows MBR, you need a windows disk to do this.

If you do not have a windows install disk, just post back, there are work arounds for that as well.

I understand how you feel, I had the same experience the first time I installed Linux, it is frustrating to learn a new OS.

Good luck with Windows.

If you ever wish to try Linux again, keep a few things in mind :

1. Learning a new OS can take time. I would say it takes up to 3 months.

2. IMO 99.9 % of bad experiences comes form hardware incompatibility, so do your research first. This is true of any OS, try running windows on a ppc (mac).

3. You can try Linux without rebooting if you use somethign like VirtualBox or VMWare.

4. Most people dual boot at least until they are comfortable enough to use Ubuntu full time.

5. Last, Linux is not a drop in replacement for windows. There is a long list of windows applications that either run poorly or not at all on Linux. So it helps if you are familiar with the Open Source applications before you transfer. You can run many of these apps on windows and examples include Firefox, Thunderbird, and Open Office. Running these applications in Windows often has additional security advantages as well.

So good luck and come on back when you are ready.

I am sure you mean well, but I must take a stand...the attitude "come on back when you are ready" is not the most appropriate here....I will say "we hope to see you back when ubuntu is ready for your hardware".... 

Also the "do your research" is I think out of place, if I remember correctly the Ubuntu's official system requirements say, "Ubuntu is available for PC, 64-Bit PC and Intel-based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space".....is this the research you had in mind?

your example of Windows on a PPC is pointless, Windows will say in its requirements that PPC is not fair game...wouldn't ?

---

### Post by lisati on 2009-11-26
> **nancy143 said:**
> After reading the replies I did some more checking This is what I figured out my proplem was my, one inexerpirence with the OS and the fact that I had Windows 7 installed it was the beta, I removed windows 7 and reinstalled Vista then booted from the Ubuntu live cd now everthing works like it should after the holiday I am going to install Ubuntu along side vista and see how it works ,I think I won't have a problem I think maby Ubuntu did not reconize Windows 7 drivers and since I am new to Ubuntu I did not know how to fix the problem. I will post my results when I get it done Have a happy holiday

Welcome back! Feel free to continue with the questions.

---

### Post by bodhi.zazen on 2009-11-26
> **jdrodrig said:**
> I am sure you mean well, but I must take a stand...the attitude "come on back when you are ready" is not the most appropriate here....I will say "we hope to see you back when ubuntu is ready for your hardware".... 

The OP indicated s/he wanted to go back to windows.

The entirety of the rest of your post is assuming it is due to hardware.

And I would strongly disagree with your examples of hardware. There are many types of hardware, from nvidia to ati cards to wireless to intel. It is these third parities that are responsible for providing drivers, not the Ubuntu developers.

It is just poor advice on any OS not to check hardware compatibility. This applies to windows, OSX, BSD, Linux, etc.

---

### Post by jdrodrig on 2009-11-26
> **bodhi.zazen said:**
> The OP indicated s/he wanted to go back to windows.

The entirety of the rest of your post is assuming it is due to hardware.

And I would strongly disagree with your examples of hardware. There are many types of hardware, from nvidia to ati cards to wireless to intel. It is these third parities that are responsible for providing drivers, not the Ubuntu developers.

It is just poor advice on any OS not to check hardware compatibility. This applies to windows, OSX, BSD, Linux, etc.

You are right, I got distracted by your quote of 99% of problems being due to hardware......I agree that checking hardware compatibility list is a must, but I would argue that the sooo vague system requirements list for ubuntu is part of the problem...that page should have a link to hardware config tested to work out of the box..IMHO..

---

### Post by Irihapeti on 2009-11-26
Sun/OpenSolaris has an online Java applet that investigates your PC hardware and then tells you if it is suitable for running OpenSolaris.

Perhaps something of the kind could be made available for Ubuntu?

I see one of the problems being that there is no definitive list of hardware that does and doesn't work. Sure, there are various wikis around, but these are often out of date, refer to earlier versions of Ubuntu and so on.

Now what to actually do about this is another story, and I don't have any easy answers to that.

---

### Post by presence1960 on 2009-11-26
Please close this thread!!

---

### Post by Eisenwinter on 2009-11-27
> **presence1960 said:**
> Please close this thread!!
Any reason for that?

---

### Post by presence1960 on 2009-11-27
> **Eisenwinter said:**
> Any reason for that?

The OP got what she needed, now it is a debate of how we should help.

---

### Post by BaBz:) on 2009-11-27
im keeping mine like that for now. im sure once ive learned more, there will eventually be no need for it. im keeping it until im more confident and have some idea of what im doing :)

---

### Post by SoapySam on 2009-11-27
> **aysiu said:**
> This is why I recommend Wubi for dual-boots.
 
How do you remove it? Just as you would any Windows program. No repartitioning. No fixing the MBR.
 
That's a nice bit of kit. 
I tried it on a Win7 PC after seeing your post. It's working nicely. I chose the Netbook install version to see how it compared with the Easy Peasy I just replaced with Win 7 on the ASUS901. Looks good on a 22" monitor!
I have yet to see how easily it uninstalls, which was my purpose after all...but I kind of *like it!*
 
Incidentally, for any ASUS users, the 901 seems to be handling Win7 with no problems whatever, though it's slightly slower at most things than with Easy Peasy. As I only have one Win7 licence (not registered yet), I'll go back to Linux on the ASUS and keep the Win / Lin dual boot on the PC.

---


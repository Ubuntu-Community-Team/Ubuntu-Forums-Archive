---
title: "Grub Beta freakout"
date: 2010-01-21
forum: The Cafe
---

### Post by tom.swartz07 on 2010-01-21
Ive noticed something, to be honest, quite funny over the past few weeks, and Im curious as to why.

Why is it that majority of the beginner's users here flip a brain when they see that Grub is a beta? Ive seen some users actually demand that other forum members help them remove grub completely- they would be more pleased NOT HAVING A BOOTLOADER on their computer at all than having a beta version.

I understand some left over confusion coming from the Windows world, but is it really that big of a deal? 

Its my understanding that grub is built on top of the original framework from grub legacy- so wouldnt that make it all the more stable?


Im just confused as to why users put up such a huge fight over seeing the word 'beta' on anything on their system.

Comments?

---

### Post by 23meg on 2010-01-21
[QUOTE=tom.swartz07]Why is it that majority of the beginner's users here flip a brain when they see that Grub is a beta?[/QUOTE]

Probably because they don't know [that the word "Beta" does not point to a specific, universal degree of release quality, and has to be understood as per the terms of each project that uses it to label their releases]("http://ubuntuforums.org/showpost.php?p=8635553&postcount=19").

---

### Post by tom.swartz07 on 2010-01-21
> **23meg said:**
> Probably because they don't know [that the word "Beta" does not point to a specific, universal degree of release quality, and has to be understood as per the terms of each project that uses it to label their releases]("http://ubuntuforums.org/showpost.php?p=8635553&postcount=19").

Thats exactly the point im trying to get at- people see 'beta' and it instantly snaps in their brain that it means 'less than good'

For pete's sake- GMail was in 'Beta' for nearly 3 years!

---

### Post by 23meg on 2010-01-21
> **tom.swartz07 said:**
> Thats exactly the point im trying to get at- people see 'beta' and it instantly snaps in their brain that it means 'less than good'

Right; I'd prefer it if people trusted the judgement of the those who found it suitable to include it in an Ubuntu release despite that "less than good" label, at least initially.

---

### Post by Techsnap on 2010-01-21
Sensible devs don't put in software which doesn't work, there are plenty of reasons why they shouldn't have used GRUB2. On my system it takes 25-30 seconds to load the menu because the I'm installing to the MBR of a different drive, thats inexcusable for a distro such as Ubuntu which is supposed  to be "Beginner Friendly". Please don't tell me to configure GRUB differently or install it to the same drive because I will be pissed. LILO has worked fine on this configuration for years yet GRUB2, in 2009 can't do the same thing.

This is not Arch, this is not Debian Sid, this is not Fedora. This is UBUNTU, a distro which if people haven't noticed a lot of first time Linux users are going to switch to, do you think they're going to be pleased with it if the bootloader cannot perform basic tasks to a high standard.

I don't care it's got the ******* word beta slapped on it, I care because it doesn't ******* work.

---

### Post by tom.swartz07 on 2010-01-21
> **Techsnap said:**
> Sensible devs don't put in software which doesn't work, there are plenty of reasons why they shouldn't have used GRUB2. On my system it takes 25-30 seconds to load the menu because the I'm installing to the MBR of a different drive, thats inexcusable for a distro such as Ubuntu which is supposed  to be "Beginner Friendly". Please don't tell me to configure GRUB differently or install it to the same drive because I will be pissed. LILO has worked fine on this configuration for years yet GRUB2, in 2009 can't do the same thing.

This is not Arch, this is not Debian Sid, this is not Fedora. This is UBUNTU, a distro which if people haven't noticed a lot of first time Linux users are going to switch to, do you think they're going to be pleased with it if the bootloader cannot perform basic tasks to a high standard.

I don't care it's got the ******* word beta slapped on it, I care because it doesn't ******* work.

Id say your case is one of the outlying 'special' cases.
If your computer is set up in such a way that it isnt just 1 or 2 hdds and a few OSs, youre bound to run into problems.

Quite frankly, Id be willing to say that if youre creating a computer with that advanced of a setup, youre probably better off using a more 'advanced' bootloader.

My point is that for the general user- the person who has 1 to 4 os's on their system, Grub is MORE than capable of doing the job with little to no configuration. It just seems to me that people are just snapping out because it 'might break for no reason'.

---

### Post by SilverDragon on 2010-01-21
> **Techsnap said:**
> On my system it takes 25-30 seconds to load the menu because the I'm installing to the MBR of a different drive, 

I agree that is definitely a problem.

> **Techsnap said:**
> lease don't tell me to configure GRUB differently or install it to the same drive because I will be pissed. 

May I ask why you must install it on a different drive?

> **Techsnap said:**
>  do you think they're going to be pleased with it if the bootloader cannot perform basic tasks to a high standard. 

I would think that most people would just install it on the same drive and for most people it performs that basic task to a high standard, in my opinion/on all of the computers I have installed Ubuntu on.


And to the OP, I have had family members ask/worry about GRUB saying that is in Beta but usually explaining to them that it is similar to when Google has products that are in Beta for a while too eases the "freakout"

---

### Post by Techsnap on 2010-01-21
> May I ask why you must install it on a different drive?Because I do, because I use my system how I want to, not how people THINK I should use it. As I say I've been booting it with lilo for 8 years this way. 

Actually taking all your replies into consideration just shows none of you know what you're talking about. So people with advanced set ups (which aren't actually advanced) shouldn't be installing things differently.

>  If your computer is set up in such a way that it isnt just 1 or 2 hdds and a few OSs, youre bound to run into problems.

No you're not, this is garbage.

---

### Post by SilverDragon on 2010-01-21
> **Techsnap said:**
> Because I do, because I use my system how I want to, not how people THINK I should use it. As I say I've been booting it with lilo for 8 years this way. 

That's perfectly fine. I was just wondering if there was a benefit to it or a disadvantage to installing in on the same drive.

> If your computer is set up in such a way that it isnt just 1 or 2 hdds and a few OSs, youre bound to run into problems. 

> No you're not, this is garbage.

I agree. It should work just fine if you set it properly which it seems like you do.

Is the main reason you use Lilo over Grub the fact Grub takes forever to load or are there even more advantages?

---

### Post by Techsnap on 2010-01-21
I'm familiar with LILO and it's less likely to leave me with an unbootable system. The old version of GRUB works for the most part but not all the time. Obviously GRUB2 is going to be fine eventually but until it's released it's ridiculous to put it in a distribution such as Ubuntu. 

Though I don't use Ubuntu myself stuff like this annoys me because most people who switch to Linux go to Ubuntu first and it just gives Linux a shoddy image to be honest. Especially when there is software like that included.

Take a look at [This Post]("http://ubuntuforums.org/showpost.php?p=8700477&postcount=7") too.

---

### Post by tom.swartz07 on 2010-01-21
> **Techsnap said:**
> Because I do, because I use my system how I want to, not how people THINK I should use it....
No you're not, this is garbage.

I appreciate your 'whatever, Eff you- ill do it my way' view on things. To be honest, sure- youre bound to learn things 10x faster than most others because you sit and fight with it to get it to work EXACTLY how you want it.

What I would like to know is; whats garbage about my statement?
Am I not correct in stating that, beyond a generally simple setup, you will have to delve deeper into the programming and code to get harddrives that are attached in non-traditional ways?

Grub CAN handle booting from external drives, networked drives, etc. You just have to tell it how to do so. THATS what Im trying to say.

---

### Post by Techsnap on 2010-01-21
Because having a few OS's installed with a bootloader booting systems from other drives on a desktop computer is not advanced that's why. Also my point is, LILO and GRUB have been able to do this absolutely fine for years, so why in 2009/10 do we have a new version which can't do it anymore?.

---

### Post by tom.swartz07 on 2010-01-21
> **Techsnap said:**
> Because having a few OS's installed with a bootloader booting systems from other drives on a desktop computer is not advanced that's why. Also my point is, LILO and GRUB have been able to do this absolutely fine for years, so why in 2009/10 do we have a new version which can't do it anymore?.

Its not that it *cant* do it anymore, its just that its being upgraded. Sure, you could still get it to work- granted, itll take a few more steps because its different than the old version, but itll be better.

As the dev comes along, it will eventually be better than anything out there. 

I mean, come on- look at some of the mockups for Grub 2 [http://www.youtube.com/watch?v=zBCR0jVzMFs](http://www.youtube.com/watch?v=zBCR0jVzMFs)

---

### Post by Techsnap on 2010-01-21
Oh my... you can't seem to realise that I'm fully aware of that. GRUB2 is fine in it's place in a cutting edge distro such as Arch or Fedora (It wasn't even present in F12!) But giving it to Ubuntu is out of place.

What good are GRUB themes without it being able to boot the system properly anyways.

---

### Post by liamnixon on 2010-01-21
My first impression for Grub2 (which I didn't use much) is that it seems overly complicated.  I tried to install it, but it didn't detect my Windows partition, and I couldn't figure out at all how to fix it (with the aid of Google), now that the menu.lst file is gone and there are forty different commands you can issue.

Wow, I need to learn how to organize my thoughts.  At any rate, I'm with Techsnap.  Lilo is much simpler and better for my needs.

---

### Post by Queue29 on 2010-01-21
My experience with Grub 2 is that it takes *over 2 minutes* to load the OS option list. That's just ridiculous when any of the actual OS's boot in under 45 seconds.

---

### Post by Ji Ruo on 2010-01-21
> **tom.swartz07 said:**
> Id say your case is one of the outlying 'special' cases.
If your computer is set up in such a way that it isnt just 1 or 2 hdds and a few OSs, youre bound to run into problems.

Quite frankly, Id be willing to say that if youre creating a computer with that advanced of a setup, youre probably better off using a more 'advanced' bootloader.


I have to agree, this is garbage. The system they described fits exactly what you've described, it's not true at all that you're bound to run into problems with it, their setup is no more advanced than any other multiboot setup and good luck finding a more 'advanced' bootloader than GRUB 2 or legacy. Besides which they are a LILO user which predates GRUB, so why would they need a more advanced bootloader? The problem isn't the setup, it's the performance of GRUB 2. My own experience is a wait of around 10-15 seconds between stage 1 and the boot menu. Compared to any other bootloader that's a terrible performance.

---

### Post by Frak on 2010-01-22
My problem is that it takes a ***minute and a half*** to load the OS selection menu. That's not forgivable.

---

### Post by Techsnap on 2010-01-22
You know what, I'm trying to explain to you people that Ubuntu shouldn't have this by default because it's not stable yet but you seem to still be saying about my configuration. I Don't use Ubuntu I don't care a crap about Ubuntu. But when I suggest things which quite rightfully are true that a beginner distro should not include such a broken BOOTLOADER by default, yes this is BOOTLOADER it's not a toy. 

Screw Ubuntu, it will continue to make people pissed off with Linux for many years to come with software like this in by default but who cares :). 

I like the way that people are saying about LILO predating GRUB and stuff, well shouldn't that give you a hint? How comes a bootloader which hasn't been updated since 2007 can do a better job than GRUB2 released in 2009? How? Explain that one to me come on?

> My problem is that it takes a minute and a half to load the OS selection menu.

But Frak look at all the excellent themes you can have :D.

---

### Post by cariboo on 2010-01-22
@Techsnap

I'm sorry Ubuntu didn't work out for you, I hope whatever OS you decide to use, it does what you need.

---

### Post by dragos240 on 2010-01-22
I think it's because they may be worried about the stability of grub, as we know, that's nothing to worry about.
I'm sure that newbies could get around just fine without a bootloader </sarcasm>

---

### Post by Techsnap on 2010-01-22
> I'm sorry Ubuntu didn't work out for you, I hope whatever OS you decide to use, it does what you need.

Hey I've never really used Ubuntu much anyway so no problem :P, I use Slackware, Fedora & Windows mainly. But is anyone actually following that Ubuntu marketed as a beginner friendly distro has stuff like this in? Obviously not and this is why a lot of people aren't going to switch to it.

---

### Post by Malakai on 2010-01-22
I just came back to linux so I needed to learn how to configure grub basically from scratch anyway.

So I learned on grub2 instead of old grub. Its actually very simple to configure. You just remove the executable bit from files in the grub folder that you dont want showing up in the loader, instead of manually editing them out of the menu.lst file.

Except now you dont need to add a separate entry for your other operating systems, grub probes them itself. People who are upset either use a very esoteric setup that Grub2 is having a hard time with, or (much more likely) people are trying to set it up the way they would have set the old grub up and its causing problems.

But if you just forget what you knew about the old grub and learn grub2 from scratch, I assure you it is quite simple and offers superior functionality compared to the old version. Personally I very much like that, in grub2, its basically not possible to make a little mistake in the grub config/menu file that causes you to be unable to boot into any os. Very nice IMO

---

### Post by Techsnap on 2010-01-22
While I agree there are some nice features with GRUB2 it still doesn't justify putting it in a beginner friendly distribution which a lot of first time Linux users will use when it's clearly not ready.

---

### Post by Ji Ruo on 2010-01-22
> **Techsnap said:**
> You know what, I'm trying to explain to you people that Ubuntu shouldn't have this by default because it's not stable yet but you seem to still be saying about my configuration. I Don't use Ubuntu I don't care a crap about Ubuntu. But when I suggest things which quite rightfully are true that a beginner distro should not include such a broken BOOTLOADER by default, yes this is BOOTLOADER it's not a toy. 

Screw Ubuntu, it will continue to make people pissed off with Linux for many years to come with software like this in by default but who cares :). 

I like the way that people are saying about LILO predating GRUB and stuff, well shouldn't that give you a hint? How comes a bootloader which hasn't been updated since 2007 can do a better job than GRUB2 released in 2009? How? Explain that one to me come on?



But Frak look at all the excellent themes you can have :D.

Learn to read

---

### Post by liamnixon on 2010-01-22
What actual functionality (not GUI's) does Grub2 provide that legacy Grub and LILO don't, anyway?  Why does anyone need a new bootloader when the old one works fine?

I'm not trying to be snide, either, I really want to know.

---

### Post by 23meg on 2010-01-22
> **liamnixon said:**
> What actual functionality (not GUI's) does Grub2 provide that legacy Grub and LILO don't, anyway?  Why does anyone need a new bootloader when the old one works fine?

I'm not trying to be snide, either, I really want to know.

It boots EXT4, and is supported upstream.

---


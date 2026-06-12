---
title: "Plan: Keep Linux Users by fixing the following issues..."
date: 2009-02-05
forum: The Cafe
---

### Post by bxcrx on 2009-02-05
Ubuntu is great, it's moving Linux into average Joe's hands and I'd love to see what Ubuntu is like in another five years.  The reality of Linux, as Mark Shuttleworth has recognized, is that it's obviously not fully baked and that the terminal geek portion image needs to be swept underneath the rug for it to be successful. 

I see the bug reports, I browse Ubuntu brainstorm, but I have a few big problems that should be addressed first before anything.  

My theory is that if you can make Linux an enjoyable experience by not having problems dealing with basic, very basic media, then we might be able to keep more users while we figuring out all the other hardware issues (Printers, iPods, Cell Phones, etc...)

**1.  Get the CPU Flash bug fixed -- Period**

I understand this is a problem that plague's almost every Linux Distribution.  

If I can't browse the web which has Flash everywhere without slowing/locking up my system then I'm limited to doing things that aren't as entertaining -- I'm contained, surfing the internet is a bare essential of most folks.  If you can't get that right then stick a fork in the steak its done son.
[B]


2. Sound mixing -- Get it working out of the box.[/B]

When I tell my friends hey you have to just stop a program that is using sound before you can use something else that needs sound.. I get the WTF look like ... Are you kidding me?

At that point I have to do some more tweaking, which is past the average users knowledge, and it to this day still isn't working correctly

**3. Networking speed -- Make the packets flow right like a router would handle them**

When my browser isn't hanging up occupationally due to flash, it doesn't load as crisply as a windows machine.  This made me tinker with my sysctl.conf file -- I shouldn't have to do this because Ubuntu , if doing things the right way , should make the system completely dumb for a broad audience and cover as much ground as possible without the need to tweak.

I'll tweak it because I have a general idea of what I'm doing but as one of my buddies told me 

"How am I suppose to fix these things if your never here?"

This is 100% true and this type of guy, the average user, will not due this and go right back to Windows or to something that works without him thinking.
[B]
4.  Quicktime plugin[/B] -- Holy Geebus, the amount of hacking I had to do was annoying even for me ... I do understand its an Apple product and its not supported on Linux, but average Joe isn't going to be suffice with that excuse even though it is reality..

Bottom line is no one wants to hear any excuses, valid or not, especially if they know of a better way to do the following (above)

This system in question is running Ubuntu 8.10 Intrepid Ibex

Nvidia XFX 7600 GT 256 running 180.xx (From mediabuntu)
2 GB DDR RAM
AMD PROC (Who knows the speed but its fast)
IDE HD

Previously running XP with no issues.

---

### Post by SunnyRabbiera on 2009-02-05
Sigh...
Look the flash plugin issue is probably an ADOBE issue, complain to them.
The quicktime issue is an APPLE issue as well, its not our fault they hate us.

---

### Post by kk0sse54 on 2009-02-05
> 1.  **Get the CPU Flash bug fixed -- Period**

I understand this is a problem that plague's almost every Linux Distribution.  

If I can't browse the web which has Flash everywhere without slowing/locking up my system then I'm limited to doing things that aren't as entertaining -- I'm contained, surfing the internet is a bare essential of most folks.  If you can't get that right then stick a fork in the steak its done son.

In all the linux distros that I've tried I have never experienced any problems with flash, not to say that problems don't happen but I think the flash situation has been definitely improving especially with the fantastic release of the 64 bit flash for linux.


> **2. Sound mixing -- Get it working out of the box.**

When I tell my friends hey you have to just stop a program that is using sound before you can use something else that needs sound.. I get the WTF look like ... Are you kidding me?
This isn't Ubuntu, this is caused by Pulseaudio which is why imo they should have stuck with Alsa

---

### Post by Skripka on 2009-02-05
1.  In the 1st case-Flash is an Adobe problem, there's nothing *Buntu can do about it.  In the 2nd case the 64-bit Flash Alpha works like a charm here.  No issues.

2.  My sound works out of the box with ALSA.  Mixer and all.

3.  Never seen this behavior.  Never needed to do any "tinkering".

4.  1st case, not a Ubuntu problem that Apple hates Linux.  2nd case, there is NO "hacking" needed.  You only need to install the VLC plugin package in Synaptic.  That is as hard as it is.  If you look there-there is support for Qucktime files.

---

### Post by ibutho on 2009-02-05
> **C!oud said:**
> In all the linux distros that I've tried I have never experienced any problems with flash, not to say that problems don't happen but I think the flash situation has been definitely improving especially with the fantastic release of the 64 bit flash for linux.



This isn't Ubuntu, this is caused by Pulseaudio which is why imo they should have stuck with Alsa
Even with Pulseaudio I have never experienced such problems and multiple apps can use the sound card at the same time. What I suspect is that his system or apps maybe using OSS instead of ALSA or pulsaudio. If I remember correctly, the old OSS versions were problematic when two or more apps tried to use the sound card at the same time.

His other points are mute though. Flash works fine for me on every single Linux distro I have ever used. I have never experienced any slow downs or hanging. As for quicktime, VLC should be able to play it and so can totem and other multimedia apps as long as you have the right codecs.

---

### Post by Bölvaður on 2009-02-05
I suspect the OP is using Warty.... these are old problems and saying flash is a problem just says too much about how new the plugin is.

1.flash is maintained by adobe
2.flash is bloated and runs badly, not only on linux
3.linux has 64 bit version which other oses does not, so you could say it runs better....


the sound problem is from OSS which was solved with PULSE, as with PULSE you have absolute control over the sound. You can have multiple outputs each playing different audio. Like I used usb headset to listen to classical music  and in the sterio I had some game + Death metal.

---

### Post by mihai.ile on 2009-02-05
well you can't say that flash is as fast as on windows but on my laptop it quite works, on my girlfriend's laptop it slows the whole laptop...

But what can I say... this is a Flash problem.

About the other things i'm sure that there are people working on it. I can assure you that isn't anyone out there that wants to make things worse than they are now, when the pulseaudio guys. Everything has a purpose.

You know what if your friends do the WTF face when you tell them about those things maybe Ubuntu it's just not for them, let them stick with what they like.
This is a free open source OS, everyone is doing his best in making it better, topics like this would not make it better for sure!

If you don't like something help out, maybe it will get fixed. No need to know how to code.
I solved some rhythmbox forgotten bugs just by talking to the right people and giving them the support they needed to make things work.

---

### Post by kk0sse54 on 2009-02-05
> **ibutho said:**
> Even with Pulseaudio I have never experienced such problems and multiple apps can use the sound card at the same time. What I suspect is that his system or apps maybe using OSS instead of ALSA or pulsaudio. If I remember correctly, the old OSS versions were problematic when two or more apps tried to use the sound card at the same time.


When I used to use Ubuntu which was many 8.04 Hardy I had the exact problem with pulseaudio as the OP so I understand the complaint. There was a work around but it's definitely not something a new user coming to linux would enjoy.

---

### Post by ibutho on 2009-02-05
> **C!oud said:**
> When I used to use Ubuntu which was many 8.04 Hardy I had the exact problem with pulseaudio as the OP so I understand the complaint. There was a work around but it's definitely not something a new user coming to linux would enjoy.

I see. I only use/d Hardy on clients servers. I never had that problem with Fedora or openSUSE using pulseaudio although I do admit that pulseaudio was buggy when it was initially released.

---

### Post by bxcrx on 2009-02-05
> **C!oud said:**
> In all the linux distros that I've tried I have never experienced any problems with flash, not to say that problems don't happen but I think the flash situation has been definitely improving especially with the fantastic release of the 64 bit flash for linux.



This isn't Ubuntu, this is caused by Pulseaudio which is why imo they should have stuck with Alsa


Glad to hear you've had better CPU usage with your system and flash.

In my tinkering uninstalled Pulseaudio completely from the system installed Alsamixer, alsa-oss, esound etc...

I've done way to much work to get sound working properly...

Come on, its sound, for someone's sake it shouldn't be this convoluted.

---

### Post by dwatson636 on 2009-02-05
If they could just get the bluetooth stereo audio to work out of the box, I would completely switch.

---

### Post by sydbat on 2009-02-05
The great thing about Linux is that you can tweak it. The (sometimes) bad thing about Linux is that you can tweak it to the point of breaking things. Is it possible that some of the problems the OP has is due to this?

---

### Post by bigbrovar on 2009-02-05
> 
My theory is that if you can make Linux an enjoyable experience by not having problems dealing with basic, very basic media, then we might be able to keep more users while we figuring out all the other hardware issues (Printers, iPods, Cell Phones, etc...) support has to come from the hardware make windows work better with ipod and some phones because the hardware makers supports it.. and make softwares to interface between their product and windows.. there dont make such for linux.. so put the blame were it belongs.. 

[QUOTE]**1.  Get the CPU Flash bug fixed -- Period**
again nothing the Linux community could do .. adobe flash player is a closed plugin that can that can only be updated and fixed by adobe .. go to them and ask for better plugin for linux. 




2. Sound mixing -- Get it working out of the box.[/B]
gotta agree with u on that one .. the implementation of pulse audio on ubuntu leave less to be desired.. i feel a lot could have been done to improve the over all performance of PA on ubuntu .. better still stick with alsa..




> **3. Networking speed -- Make the packets flow right like a router would handle them** never had this problem on ubuntu. .. on the contrary i think networking has gotten really good with network manager 0.7.. never had a problem with it.. and surfing the net on ubuntu is IMHO faster than on windows




> 4.  Quicktime plugin[/B] -- Holy Geebus, the amount of hacking I had to do was annoying even for me ... I do understand its an Apple product and its not supported on Linux, but average Joe isn't going to be suffice with that excuse even though it is reality..
again why would u blame ubuntu for this .. or expect the community to do something about it.. but the blame to Apple .. complain to them, write them (good luck with that)

---

### Post by Polygon on 2009-02-05
so almost all of your problems your wanting ubuntu to fix them when they have absolutely no control it. nice.

and the network thing: packets flowing? lol. Anyway, linux has a much better network stack then windows from what i hear, and i get faster download/upload speeds in linux then i do in windows xp and vista.

your title is misleading. its "please keep me using linux", not everyone has your problems.

---

### Post by mihai.ile on 2009-02-05
my networking speed is way better in ubuntu than when I used XP some years ago...

---

### Post by Keyper7 on 2009-02-05
Hey, let's make a deal: you won't transform the sentence "I had problem X" into "everyone has problem X" and I won't transform the sentence "I didn't have problem X" into "no one has problem X".

Over-generalizations are the cancer of this board.

---

### Post by bxcrx on 2009-02-05
> **bigbrovar said:**
> [QUOTE]
My theory is that if you can make Linux an enjoyable experience by not having problems dealing with basic, very basic media, then we might be able to keep more users while we figuring out all the other hardware issues (Printers, iPods, Cell Phones, etc...) support has to come from the hardware make windows work better with ipod and some phones because the hardware makers supports it.. and make softwares to interface between their product and windows.. there dont make such for linux.. so put the blame were it belongs.. 


again nothing the Linux community could do .. adobe flash player is a closed plugin that can that can only be updated and fixed by adobe .. go to them and ask for better plugin for linux. 




2. Sound mixing -- Get it working out of the box.[/B]
gotta agree with u on that one .. the implementation of pulse audio on ubuntu leave less to be desired.. i feel a lot could have been done to improve the over all performance of PA on ubuntu .. better still stick with alsa..




 never had this problem on ubuntu. .. on the contrary i think networking has gotten really good with network manager 0.7.. never had a problem with it.. and surfing the net on ubuntu is IMHO faster than on windows





again why would u blame ubuntu for this .. or expect the community to do something about it.. but the blame to Apple .. complain to them, write them (good luck with that)


Average Joe does not care as to why Apple doesn't support Ubuntu; 

Solution - Get it working easily with minimal hassle so that maybe when they hit a Quicktime site its not a circus act.

Strike up meetings with Apple

Get iTunes working nativily (That would come with native iPod support)  Then maybe you can even get native Quicktime support too!

Even the devil, Microsoft, has a relationship with Apple and they are more of a threat than lets say Linux


Remember there are technicial, and political excuses, but, again when average joe is using Linux he won't care as to why it's not working and just wants it working period.

---

### Post by wolfen69 on 2009-02-05
> **bxcrx said:**
> [QUOTE=bigbrovar;6681913]



Strike up meetings with Apple

Get iTunes working nativily

you're funny! :lolflag:

---

### Post by mihai.ile on 2009-02-05
> **bxcrx said:**
> 
Remember there are technicial, and political excuses, but, again when average joe is using Linux he won't care as to why it's not working and just wants it working period.

Well... if you look at the first Ubuntu released, then the Dapper and now 8.10 you can see that there are many many improvements being done, it's just that no one get's payed for this it's not that easy to find time to do more.
Help out, send an email to adobe/apple and request for better suport linux...

Oh and by the way the average joe doesen't mind if there are differences in networking speed (in my opinion also linux default is better than windows), doesen't mind if the cpu is loaded at 30% or 70% while he is watching a youtube video (he won't even know about the cpu monitor applet), the average joe will blame apple because their website is not starting the movies as it does on windows without the quicktime which maybe don't even know how to install it.

You see there are also many types of "average joe", this was my type and he didn't have the problems your "average joe" has...

You need to be more specific to make a point, can't generalize so much.

---

### Post by Keyper7 on 2009-02-05
My personal theory: most world problems are caused by poverty.

Plan: solve world problems by eliminating poverty.

Am I not a genius?

Now roll up your sleeves and do it! Yes, there are some technical and political problems, but the average hungry kid in Africa doesn't care about excuses, he just wants to eat. It's simple, there's food and there's hungry people, you just need to get a bunch of food and give to them.

What? The US had money but didn't want to give? Well, I'm sure no one tried to have a meeting with George W. and ask him politely. Maybe you can try this with Obama!

Anyway, sounds easy, huh? Now just do something quickly, while I sit here, watch and do nothing myself. Where did I left that beer?

---

### Post by koenn on 2009-02-05
> **bxcrx said:**
> Plan: Keep Linux Users by fixing the following issues...
A plan, you say ? all I see is a list of issues that might need some attention, without any indication of who's gonna address them, how, when, with who'se help, or any other resources that might be required. Not much of a plan, imo.

Ah, gotta love those "what linux needs to win is (solve my list of problems)" threads. Here's more : [http://ubuntuforums.org/showthread.php?t=219243](http://ubuntuforums.org/showthread.php?t=219243)
Funny how they always have this "somebody (else) should fix this, cause I say so" ring to them.

---

### Post by Skripka on 2009-02-05
> **bxcrx said:**
> 

Remember there are technicial, and political excuses, but, again when average joe is using Linux he won't care as to why it's not working and just wants it working period.

"Average Joe" doesn't use Linux.  "Average Joe" barely knows how to turn his computer on.  "Average Joe" kills his computer on a weekly basis because he clicks on everything that says "Click HERE!".  "Average Joe" doesn't want to learn anything more than he already.  "Average Joe" wants a freebee WindowsXP clone that will run all his pirated software and music.


Why do I care about "Average Joe" using Linux?  Tell me again?

---

### Post by steveneddy on 2009-02-05
> **bxcrx said:**
> Ubuntu is great, it's moving Linux into average Joe's hands and I'd love to see what Ubuntu is like in another five years.  The reality of Linux, as Mark Shuttleworth has recognized, is that it's obviously not fully baked and that the terminal geek portion image needs to be swept underneath the rug for it to be successful. 

I see the bug reports, I browse Ubuntu brainstorm, but I have a few big problems that should be addressed first before anything.  

My theory is that if you can make Linux an enjoyable experience by not having problems dealing with basic, very basic media, then we might be able to keep more users while we figuring out all the other hardware issues (Printers, iPods, Cell Phones, etc...)

**1.  Get the CPU Flash bug fixed -- Period**

I understand this is a problem that plague's almost every Linux Distribution.  

If I can't browse the web which has Flash everywhere without slowing/locking up my system then I'm limited to doing things that aren't as entertaining -- I'm contained, surfing the internet is a bare essential of most folks.  If you can't get that right then stick a fork in the steak its done son.

I am using Flash 10 on my 64 bit laptop and two other desktops in the house and it seems to be working fine. Even the version in the repos is a good version.
Maybe a memory issue? [B]

> 
2. Sound mixing -- Get it working out of the box.[/B]> 

When I tell my friends hey you have to just stop a program that is using sound before you can use something else that needs sound.. I get the WTF look like ... Are you kidding me?

At that point I have to do some more tweaking, which is past the average users knowledge, and it to this day still isn't working correctly

I use ALSA on all of the previously mention machines and again, no issues. Sound will play from a messenger and the web browser at the same time. Or listen to mp3's while watching the news.
> 

**3. Networking speed -- Make the packets flow right like a router would handle them**

When my browser isn't hanging up occupationally due to flash, it doesn't load as crisply as a windows machine.  This made me tinker with my sysctl.conf file -- I shouldn't have to do this because Ubuntu , if doing things the right way , should make the system completely dumb for a broad audience and cover as much ground as possible without the need to tweak.

I'll tweak it because I have a general idea of what I'm doing but as one of my buddies told me 

"How am I suppose to fix these things if your never here?"

This is 100% true and this type of guy, the average user, will not due this and go right back to Windows or to something that works without him thinking.
So have you done the standard Firefox tweaks for faster browsing?> [B]

4.  Quicktime plugin[/B] -- Holy Geebus, the amount of hacking I had to do was annoying even for me ... I do understand its an Apple product and its not supported on Linux, but average Joe isn't going to be suffice with that excuse even though it is reality..

Bottom line is no one wants to hear any excuses, valid or not, especially if they know of a better way to do the following (above)

This system in question is running Ubuntu 8.10 Intrepid Ibex

Nvidia XFX 7600 GT 256 running 180.xx (From mediabuntu)
2 GB DDR RAM
AMD PROC (Who knows the speed but its fast)
IDE HD

Previously running XP with no issues.I just installed VLC and everything is good. I think I had to install the medibuntu repos also, but no big deal.

These are actually very old issues. 

What version of Ubuntu are you using?

Are you sure that you aren't holding your mouth right?

---

### Post by MickS on 2009-02-05
Got to laugh at the flash reference, I've got Adblock and NoScript to stop the bugger.
Don't have the other probs either.

Mick

---

### Post by Nepherte on 2009-02-05
> **bxcrx said:**
> Average Joe does not care as to why Apple doesn't support Ubuntu; 

Solution - Get it working easily with minimal hassle so that maybe when they hit a Quicktime site its not a circus act.

Strike up meetings with Apple

Get iTunes working nativily (That would come with native iPod support)  Then maybe you can even get native Quicktime support too!

As if the linux community didn't want to "strike up meetings with apple and get it working"...You make it sound very easy. You see, there are two sides and Apple doesn't want to. It's as easy as that. It's their right to refuse releasing iTunes on Linux and that's exactly what they do.

---

### Post by Vince4Amy on 2009-02-05
> 2. Sound mixing -- Get it working out of the box.

When I tell my friends hey you have to just stop a program that is using sound before you can use something else that needs sound.. I get the WTF look like ... Are you kidding me?

At that point I have to do some more tweaking, which is past the average users knowledge, and it to this day still isn't working correctly

I think that's the only valid point you brought up, the others are third party and cannot be fixed by anyone here, your best option would be to contact Adobe for example. I agree, in most current distros Sound mixing is terrible, it works flawlessly for me in Fedora & Slackware but ever other distro has been a complete joke for me.

---


---
title: "32-bit OS on 64-bit computer?"
date: 2009-10-15
forum: The Cafe
---

### Post by armageddon08 on 2009-10-15
How much does it affect performance? Are there any visible differences in the performance of 32-bit and 64-bit operating systems on common applications like firefox, amarok, openoffice etc ?

---

### Post by Bachstelze on 2009-10-15
Nope. Mind, there isn't any drawback either, so if you don't have a reason to stick with 32bit, install 64bit.

---

### Post by Screwdriver0815 on 2009-10-15
> **armageddon08 said:**
> How much does it affect performance? Are there any visible differences in the performance of 32-bit and 64-bit operating systems on common applications like firefox, amarok, openoffice etc ?
everything is faster in 64 bit. And I really mean EVERYTHING. No matter how much RAM you have (because I know that sooner or later the statement will come "64 bit is only better for computers with more than 4 GB RAM" - which is not true)

---

### Post by earthpigg on 2009-10-15
> **Screwdriver0815 said:**
> everything is faster in 64 bit. And I really mean EVERYTHING. No matter how much RAM you have (because I know that sooner or later the statement will come "64 bit is only better for computers with more than 4 GB RAM" - which is not true)

everything that is ***compiled*** for 64-bit, that is.

32-bit non-free apps that require 32-bit compatibility dependencies be installed will not experience greater performance.

based on my basic and potentially flawed understanding, that is.

---

### Post by Bachstelze on 2009-10-15
> **Screwdriver0815 said:**
> everything is faster in 64 bit. And I really mean EVERYTHING. No matter how much RAM you have (because I know that sooner or later the statement will come "64 bit is only better for computers with more than 4 GB RAM" - which is not true)

Source, please.

---

### Post by Screwdriver0815 on 2009-10-15
> **earthpigg said:**
> everything that is ***compiled*** for 64-bit, that is.

32-bit non-free apps that require 32-bit compatibility dependencies be installed will not experience greater performance.

based on my basic and potentially flawed understanding, that is.
okay, thats true. I forgot about the 32 bit programms as they work flawless in my 64 bit system.

> **Bachstelze said:**
> Source, please.

experience? and technological consistency, maybe?

technological wise: one just has to look up Wikipedia to understand what the difference between a 32 bit and a 64 bit system is.
Technological wise it is a fact that a 64 bit system on a 64 bit processor allows the processor to calculate 64 bit long words with one operation.
A 32 bit system on a 64 bit processor does what? Ah! it allows the processor to calculate 32 bit long words with one operation... the difference is: surprise, surprise! 32 bit which is 100%, correlated to the 32 bit system. 
The RAM does not do anything to the "calculation of xy bit long words" story.

But I have to admit: when you use 32 bit programms in a 64 bit system, it has the same speed as in a 32 bit system. But as in the 64 bit Linuxsystems, nearly everything is also compiled for 64 bit, it is really rare that one has to use 32 bit programms. One is of course the flashplugin.

---

### Post by Hallvor on 2009-10-15
> **armageddon08 said:**
> How much does it affect performance? Are there any visible differences in the performance of 32-bit and 64-bit operating systems on common applications like firefox, amarok, openoffice etc ?

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

There is little difference when it comes to regular desktop use, but multimedia processing and number crunching is much faster on 64 bit.

---

### Post by Bachstelze on 2009-10-15
> **Screwdriver0815 said:**
> 
Technological wise it is a fact that a 64 bit system on a 64 bit processor allows the processor to calculate 64 bit long words with one operation.

Provided that you give it 64bit words in the first place, which most desktop programs do not do. Compiling programs on a 64 bit system won't magically change ints to longs in the source.

```
firas@iori ~ % cat int.c
#include <stdio.h>

int main(void)
{
        printf("%d\n", sizeof(int));
        return 0;
}

firas@iori ~ % uname -a
Linux iori.fkraiem.org 2.6.30-1-amd64 #1 SMP Sat Aug 15 18:09:19 UTC 2009 x86_64 GNU/Linux
firas@iori ~ % cc -o int int.c
firas@iori ~ % ./int
4
```

Yup. ints are still 32 bit, even on a 64 bit system.

---

### Post by NoaHall on 2009-10-15
Still, it's nice to know in theory it can process twice as much bits in the same amount of time. It just turns me on.

---

### Post by keiichidono on 2009-10-15
As said above, video stuff will be a lot better. I watch a lot of 720p HD Anime and it plays a lot smoother on 64bit.

---

### Post by Exodist on 2009-10-15
What Screwdriver, Earthpig and Hallvor stated is all true.

Mind you many distros like Ubuntus 64bit is a Hybrid 32/64bit system possessing both 32bit and 64bit libs to get you the best from both worlds. Compatibility and Performance. 
Currently most of the multimedia applications are compiled for 64bit instructions and SMP. But some of your older legacy crud isnt just yet. Some not even for SMP yet.

I recommend the 64bit version if you can run it. But if you cant its not a game ender.

---

### Post by kpholmes on 2009-10-15
> **Screwdriver0815 said:**
> One is of course the flashplugin.

thats why i chose 32 bit, i have way to many "projects" that im working on to worry about installing the right dependencies for 64bit, i dont do any video editing, or compiling, on my desktop that has a 32/64 bit cpu so i dont see a huge performance increase. ive actuially heard that you can see performance decrease in running a 32bit program in a 64bit os (sometimes), so i wouldnt go so far as saying that "everything is faster"

plus i like to watch hulu desktop through my tv, and you need flash. =D

i heard that they were releasing a 64 bit flash plugin but it was beta and after tinkering around with it i decided to call it quites and reload a 32bit os. 


p.s. theres a whole section of 64bit threads in the support area and you might be able to find some good info.

but i recommend try the 64bit, if you like it, stick with it. if its not for you, then try it again in a year or 2 when it might be more supported/tailored for your needs. 

just my 2cents

---

### Post by ~sHyLoCk~ on 2009-10-15
> **CalvinB said:**
> As said above, video stuff will be a lot better. I watch a lot of 720p HD Anime and it plays a lot smoother on 64bit.

Really? I didn't notice much difference in HD video playback. I don't use 64bit for a lot of reasons, mainly due to size issues, 64bit occupies quite a lot of space.

---

### Post by NoaHall on 2009-10-15
Ehm. In my sig, there is a link to a tutorial on how to install 64 bit flash. It works better than 32 bit one. Even than the 32 bit one on a 32 bit os.

---

### Post by forrestcupp on 2009-10-15
> **Hallvor said:**
> [http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

There is little difference when it comes to regular desktop use, but multimedia processing and number crunching is much faster on 64 bit.

+1

That's the answer.  You won't see any difference with things like Firefox, OpenOffice.org, etc.  If you work with things like compression, and video/audio editing, that's where you'll see the difference.

But like earthpigg said, you have to be using apps that are compiled for 64-bit.  Using a 32-bit app in a 64-bit OS doesn't do you any more good.

---

### Post by Skripka on 2009-10-15
> **kpholmes said:**
> 
i heard that they were releasing a 64 bit flash plugin but it was beta and after tinkering around with it i decided to call it quites and reload a 32bit os. 


p.s. theres a whole section of 64bit threads in the support area and you might be able to find some good info.

but i recommend try the 64bit, if you like it, stick with it. if its not for you, then try it again in a year or 2 when it might be more supported/tailored for your needs. 

just my 2cents

I've been running the 64bit native Flash plugin since it was released as "alpha".  The 64bit Linux native Flash "Alpha" works as good or better than the Windows plugin.

There really is next to NO reason NOT to take advantage of your 64bit CPU.

---

### Post by Exodist on 2009-10-15
> **kpholmes said:**
> thats why i chose 32 bit, i have way to many "projects" that im working on to worry about installing the right dependencies for 64bit, i dont do any video editing, or compiling, on my desktop that has a 32/64 bit cpu so i dont see a huge performance increase. ive actuially heard that you can see performance decrease in running a 32bit program in a 64bit os (sometimes), so i wouldnt go so far as saying that "everything is faster"

plus i like to watch hulu desktop through my tv, and you need flash. =D

i heard that they were releasing a 64 bit flash plugin but it was beta and after tinkering around with it i decided to call it quites and reload a 32bit os. 


p.s. theres a whole section of 64bit threads in the support area and you might be able to find some good info.

but i recommend try the 64bit, if you like it, stick with it. if its not for you, then try it again in a year or 2 when it might be more supported/tailored for your needs. 

just my 2cents

Installing Flash is easy. All you have to do is drop the plugin in the plugin directory or use the one in the repositories. There is no dependency issue.



I am totally amazed at the user base that is scared of using the 64bit system. Guys/Gals.. Its safe to use now!!  Yes a few years ago I compiled many of the 64bit programs for the Ubuntu community when 64bit was taboo. But its a mainstay now and common. You all dont have to be worried about using it anymore. Take  your hair down relax and when 9.10 comes out download the 64bit versions enjoy a slightly faster over all system. :)

---

### Post by Skripka on 2009-10-15
> **forrestcupp said:**
> +1
But like earthpigg said, you have to be using apps that are compiled for 64-bit.  Using a 32-bit app in a 64-bit OS doesn't do you any more good.

I can't think of that many.  As a matter of fact, I can't think of any apart from Google Earth or Adobe Reader.

---

### Post by kpholmes on 2009-10-15
> **NoaHall said:**
> Ehm. In my sig, there is a link to a tutorial on how to install 64 bit flash. It works better than 32 bit one. Even than the 32 bit one on a 32 bit os.

ya i saw and checked it out. ima book mark it for next time i upgrade. 


anyone know if theres a performance on networking (like for server and stuff) when running at 64bit?

---

### Post by Xbehave on 2009-10-15
There are parts of systems that are less tested/optimised under 64bit (for example you cant there is no 64bit physco (fast python interpretter)), but generally there is very little disadvantage to 64bit, but multimedia processing and number crunching is more efficient (to the point that the factor command can handle 64bit ints not just 32bit ints)

---

### Post by gan1708 on 2009-10-15
I use 32bit (Ubuntu Studio) for my graphic work and 64bit (Debian) for home/play.

Just wanted to ask:
I used to get all sorts of weirdness on Inkscape (my primary open source work app) when on 64bit around 18 months (+/-) ago.... any issues these days?

---

### Post by toupeiro on 2009-10-15
man, everyone complains about the flash plugin on 64-bit but for the last two versions of ubuntu, arguably even longer than that, I've been running 64-bit with 0% issues.  Flash has worked WONDERFULLY.  I've been using Karmic for a while now and its still working wonderfully. 


I seriously have no showstoppers at all on 64-bit.  Im curious, for those who have had negative experiences with 64-bit, how long ago was that?

---

### Post by JDShu on 2009-10-15
Blender renders at amazing speeds in 64-bit

---

### Post by Frak on 2009-10-15
With the exception of number crunching apps, a good amount (around 95%) of regular desktop apps will see no performance increase. Even if you compile it for 64-bit, you won't see an increase from it.

As for whoever said "32-bit apps run flawlessly under 64-bit", not all 32-bit apps run flawlessly under 64-bit.

---

### Post by Screwdriver0815 on 2009-10-15
> **kpholmes said:**
> ya i saw and checked it out. ima book mark it for next time i upgrade. 


anyone know if theres a performance on networking (like for server and stuff) when running at 64bit?
in 64 bit it is faster. Although if someone pops up and asks for sources, tells everybody that it can not be like that... and so on: it is faster.
Almost all the servers run on 64 bit ... guess why? ... and on the Ubuntu homepage they state in the server section that the 32 bit version is for the EXCEPTIONAL case if your processor can not handle 64 bit

> **Exodist said:**
> 
I am totally amazed at the user base that is scared of using the 64bit system. Guys/Gals.. Its safe to use now!!  Yes a few years ago I compiled many of the 64bit programs for the Ubuntu community when 64bit was taboo. But its a mainstay now and common. You all dont have to be worried about using it anymore. Take  your hair down relax and when 9.10 comes out download the 64bit versions enjoy a slightly faster over all system. :)
+1000 and full agreement

I also can not understand 

1. why I have waited so long to switch to 64 bit 

2. why so many people are scared to use it. The developers do a lot of work to get 64 bit done and then there people sit and are scared...

:confused:

---

### Post by NoaHall on 2009-10-15
Come on people, you're meant to love your computers, and to try and get to perform a million times faster. Or at least, that's how I see it, and since I like performance, I always go with 64 bit.

---

### Post by Frak on 2009-10-15
> **Screwdriver0815 said:**
> in 64 bit it is faster. Although if someone pops up and asks for sources, tells everybody that it can not be like that... and so on: it is faster.
Almost all the servers run on 64 bit ... guess why? ... and on the Ubuntu homepage they state in the server section that the 32 bit version is for the EXCEPTIONAL case if your processor can not handle 64 bit


+1000 and full agreement

I also can not understand 

1. why I have waited so long to switch to 64 bit 

2. why so many people are scared to use it. The developers do a lot of work to get 64 bit done and then there people sit and are scared...

:confused:
Only reason: Flash doesn't work in 64-bit Karmic.

Fix that, I *may* come back.

---

### Post by Xbehave on 2009-10-15
> **Frak said:**
> Only reason: Flash doesn't work in 64-bit Karmic.

Fix that, I *may* come back.

wait so because it doesn't work on a beta, you have given up completely?

[this]("http://labs.adobe.com/downloads/flashplayer10.html") is what you need, then you copy the .so into /usr/[lib,lib64]/[mozilla,firefox]/plugins/ it depends on your distro, but it will be an existing folder (especially if you have mozplugger installed) on fedora11 its /usr/lib64/mozilla/plugins/

---

### Post by Frak on 2009-10-15
> **Xbehave said:**
> wait so because it doesn't work on a beta, you have given up completely?

[this]("http://labs.adobe.com/downloads/flashplayer10.html") is what you need, then you copy the .so into /usr/[lib,lib64]/[mozilla,firefox]/plugins/ it depends on your distro, but it will be an existing folder (especially if you have mozplugger installed) on fedora11 its /usr/lib64/mozilla/plugins/
No, the flash for 64-bit Karmic is broken. Flat, that's it. It is broken.

And yes I gave up, there are more distros than Ubuntu. Why should I stick to one and fix it when there are others that work fine.

---

### Post by Crunchy the Headcrab on 2009-10-15
> **Frak said:**
> No, the flash for 64-bit Karmic is broken. Flat, that's it. It is broken.

And yes I gave up, there are more distros than Ubuntu. Why should I stick to one and fix it when there are others that work fine.
I'm using 64bit flash in Karmic and it works great...fantastic...amazing.  :guitar:  Also keep in mind that Karmic is still beta.  I've seen dramatic bug fixes just in the last couple of weeks.  So, you might be surprised when the "stable" version hits.

---

### Post by Exodist on 2009-10-15
> **Frak said:**
> No, the flash for 64-bit Karmic is broken. Flat, that's it. It is broken.

And yes I gave up, there are more distros than Ubuntu. Why should I stick to one and fix it when there are others that work fine.


Beta = broken.. damn never would have thought of that..


So is it really non fixable, or are you just amiss about correcting it.
You know you could prob just download the bin from Fxs website and manually drop the plugin in the .firefox/plugin directory. Of course if you still want the 64bit compiled browser I would recommend purging Fx and then reinstalling it. Sounds like your just a victim of a corrupted directory. "sudo apt-get purge firefox(whatever the rest of the new name)"
That will remove EVERYTHING and give you a clean slate to reinstall upon.

- Exo

---

### Post by Skripka on 2009-10-15
> **Frak said:**
> Only reason: Flash doesn't work in 64-bit Karmic.

Fix that, I *may* come back.

That is NOT Adobe's problem-that is something on Ubuntu's end.

---

### Post by Frak on 2009-10-15
OK, nobody's really paying attention. Flash on 64-bit Ubuntu doesn't work Out of the box on my computer, on Karmic. I'm not going to sit and sort it out, I have other things to get done.

I'm not going to protect Ubuntu. Ubuntu needs to protect itself. As for "It's a beta, you shouldn't bash it on that."

1. Quit advertising it on the Ubuntu home page.
2. Quit recommending it to new users so much.

---

### Post by blur xc on 2009-10-15
> **Frak said:**
>  1. Quit advertising it on the Ubuntu home page.

:confused:

It's not ok to say a new release is coming soon?  How long has MS been touting the arrival of Win 7?  The Ubuntu home page isn't telling everyone to download 9.10...  It says if you can't wait *DOWNLOAD THE BETA* and *TEST IT.*

How is it Cannonical's fault that you didn't read that, and when you TESTED IT (although likely without realizing you signed up as a beta tester) and found a problem?

I just don't understand your reasoning.

As for me, I'm happily on 9.04, and keeping my computer working properly is more important to me (since I'm not even the primary user), I choose wait a few months after the official release of software before I upgrade.

BM

---

### Post by Xbehave on 2009-10-15
> **Frak said:**
> ...I'm not going to sit and sort it out, I have other things to get done.Like install other **betas**? Or post complaints about how **betas** contain bugs on forums? Installing 64bit flash manually takes **A LOT** less time than installing any distro

---

### Post by JDShu on 2009-10-15
> **Xbehave said:**
> Like install other **betas**? Or post complaints about how **betas** contain bugs on forums? Installing 64bit flash manually takes **A LOT** less time than installing any distro

:lolflag:

---

### Post by Crunchy the Headcrab on 2009-10-15
> **Xbehave said:**
> Like install other **betas**? Or post complaints about how **betas** contain bugs on forums? Installing 64bit flash manually takes **A LOT** less time than installing any distro
I bet it takes me less than a minute to install the latest 64bit flash beta.  Go [here]("http://labs.adobe.com/downloads/flashplayer10.html") download tar file.  Open tar file (double click in nautilus, not hard) and paste the file included into /home/user_name/.mozilla/plugins

Honestly.  If you can't do that much for yourself...maybe linux isn't your cup of tea anyway.  BTW, this is the process I use for Fedora, Ubuntu, and various other distros I've tried.  It works great on all of them.

---

### Post by Paqman on 2009-10-15
> **Frak said:**
> No, the flash for 64-bit Karmic is broken. Flat, that's it. It is broken.


:confused:

Works fine for me, with the version from Adobe. Never had so much as a hiccup from it.

---

### Post by djbon2112 on 2009-10-15
I don't know about here, but on the computer hardware sites this has been done to death :p

The consensus is: 64-bit, for normal computing tasks, is identical to 32-bit in performance. For some floating-point intensive applications, there may be an slight performance boost from 64-bit, but it's basically irrelevant. However, remember that if you want to use >3 GB of RAM, you need a 64-bit OS to properly address it all, or you'll get cut off at about 3.6 GB (less if you have video cards with lots of RAM on them too).

HOWEVER, I'm of the mindset that if you can use it, you should. If your processor is 64-bit, go ahead and run the 64-bit version of whatever OS you choose. Most of the issues have been resolved (the last one I can think of was Flash) with 64-bit support, so it should be seamless.

---

### Post by siimo on 2009-10-15
I refuse to switch to 64bit on my desktop / laptop systems.  Yes there may be slight performance improvements but they aren't big enough to justify the upgrade.  Most of the desktop machines are still running 32bit.  

I will only upgrade when either of the following happens:
1. I get > 4GB RAM
2. When 32bit stops being mainstream (ie. Majority of desktops are 64bit OS'd) which will probably happen when Windows goes 64bit only.   Windows is probably going to be 32bit for Windows 8 still so it is unlikely for a very long time.

---

### Post by Xbehave on 2009-10-15
for the record, a 32bit processors can handle >4GB of ram with PAE (apparent the default ubuntu kernel doesn't have PAE due to the overhead, but the server one does)

BTW does address space randomisation work better (thus making you more secure) on a 64bit os?

---

### Post by Warpnow on 2009-10-15
> **Screwdriver0815 said:**
> everything is faster in 64 bit. And I really mean EVERYTHING. No matter how much RAM you have (because I know that sooner or later the statement will come "64 bit is only better for computers with more than 4 GB RAM" - which is not true)

A 64 bit system -does- use more ram than a 32 one. Fact.

If you have less ram, less than your selected applications require to run, then you would be **better off with 32 bit** and running in Ram than using swap with 64 bit. Hardly even arguable.

---

### Post by djbon2112 on 2009-10-15
> **Warpnow said:**
> A 64 bit system -does- use more ram than a 32 one. Fact.

If you have less ram, less than your selected applications require to run, then you would be **better off with 32 bit** and running in Ram than using swap with 64 bit. Hardly even arguable.

I've never seen this. However, if RAM is such a limiting factor that a few MB matter, in a 64-bit capable system, then there are other issues at hand...

---

### Post by Warpnow on 2009-10-15
> **djbon2112 said:**
> I've never seen this. However, if RAM is the limiting factor in a 64-bit capable system, then there are other issues at hand...

But that is where the argument comes from, mostly during the Vista era when 64 bit machines were being released with Vista and 1gb of ram. Running the 64 bit made your system noticably slower.

---

### Post by Xbehave on 2009-10-15
> **Warpnow said:**
> A 64 bit system -does- use more ram than a 32 one. Fact.

If you have less ram, less than your selected applications require to run, then you would be **better off with 32 bit** and running in Ram than using swap with 64 bit. Hardly even arguable.
Why? I've heard this but never heard it backed up. That it's a significant difference (are we talking 1Mb, 1Kb)?

---

### Post by djbon2112 on 2009-10-15
> **Warpnow said:**
> But that is where the argument comes from, mostly during the Vista era when 64 bit machines were being released with Vista and 1gb of ram. Running the 64 bit made your system noticably slower.

I used Vista for a solid year, both 32- and 64- bit, and I never saw any difference in RAM usage between the two. 64-bit was faster and more stable though.

---

### Post by Hallvor on 2009-10-16
> **djbon2112 said:**
> I've never seen this. However, if RAM is such a limiting factor that a few MB matter, in a 64-bit capable system, then there are other issues at hand...

"*The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization*."

[http://en.wikipedia.org/wiki/64-bit#Pros_and_cons](http://en.wikipedia.org/wiki/64-bit#Pros_and_cons)

---

### Post by Nerd King on 2009-10-16
I've generally found 64-bit to be stable, fast and yes an improvement over 32-bit.

---

### Post by ~sHyLoCk~ on 2009-10-16
> **Nerd King said:**
> I've generally found 64-bit to be stable, fast and yes an improvement over 32-bit.

False claims, specially the stability part.

---

### Post by Nerd King on 2009-10-16
Ah so you've used my computer then? No? "I've generally found" means personal experience. Unless you think I'm lying there's nothing to disagree with there.

---

### Post by Crunchy the Headcrab on 2009-10-16
> **~sHyLoCk~ said:**
> False claims, specially the stability part.Really?  Because I've found the same thing.

---

### Post by Screwdriver0815 on 2009-10-16
> **Warpnow said:**
> A 64 bit system -does- use more ram than a 32 one. Fact.

If you have less ram, less than your selected applications require to run, then you would be **better off with 32 bit** and running in Ram than using swap with 64 bit. Hardly even arguable.

but this I did NOT mean. I mean that no matter if you have 2 gb RAM or 4 GB RAM, the 64-bit runs faster in some cases (for the record: my opinion is that it not only runs faster in some cases - it runs faster everytime but I yield into the common opinion of this forum). Kubuntu Jaunty 64 bit is also noticable more stable than 32 bit on my machine.

Anyway, if 64-bit uses more RAM, then it will be fine. Why is the RAM in the machine? To get bored? Or for work?
I have 2 GB in my computer and in 32 bit it never was used to the max. Now, with 64 bit, it also is not used to the max. Maybe I don't do enough challenging things but I don't see the point, why I shouldn't use all the computing power of my processor anyway. 

Especially when it does not require any extra work. 

This is another story: all the statements about 64 bit sound like that: "ah I do not use it and it does not pay off"... and so on. Like as it was a horrible amount of work to get a 64 bit system working.
But it isn't. Its just like installing a 32 bit system. Everything is the same. 
Its the same as using Linux. You can use it on an old 500MHZ, 128MB RAM, 10 GB HDD machine. Why do some people have more computing power in their machines? Why? You don't need it as it runs on this old/crappy hardware. More power does not make sense. 
This does no matter to some people. But when it comes to 32 bit or 64 bit... uhh huh uhh... no way! "No progress please"... 

really, I don't get it.

:confused:

---

### Post by forrestcupp on 2009-10-16
> **kpholmes said:**
> 
i heard that they were releasing a 64 bit flash plugin but it was beta and after tinkering around with it i decided to call it quites and reload a 32bit os.

Why go to that trouble when you could just run the 32-bit version of Flash?

---

### Post by NoaHall on 2009-10-16
It's a soild alpha, and it runs much much better than the 32 bit one. If you're still using the 32 bit flash on a 64 bit OS, I pity you. Get with the times, and upgrade it.

---

### Post by Xbehave on 2009-10-16
> **forrestcupp said:**
> Why go to that trouble when you could just run the 32-bit version of Flash?
TBF nspluginwrapper does majorly suck

> Anyway, if 64-bit uses more RAM, then it will be fine. Why is the RAM in the machine? To get bored? Or for work?
Using more ram, because it's there isn't a great argument. [http://en.wikipedia.org/wiki/64-bit#Pros_and_cons](http://en.wikipedia.org/wiki/64-bit#Pros_and_cons) is worth a read but tbh I wish somebody would just give real world numbers for the difference in ram usage on a modern linux distro, am i loosing 1kb or 10mb?

---

### Post by NoaHall on 2009-10-16
I'm currently using 873MB with aMSN, Songbird, Chromium with 5 tabs, two AWN docks, compiz, World of Goo, and Opera using the Flash plugin to watch the Peep show. 
Is that what you wanted?

---

### Post by sdlynx on 2009-10-16
If you don't need the supposedly gained speed, I would stick with x86.  I have x86_64 on my laptop and its great aside from the fact that 32-bit applications that require dependencies are a huge pain to install correctly.

SDLynx

---

### Post by Bachstelze on 2009-10-16
> **Xbehave said:**
> I wish somebody would just give real world numbers for the difference in ram usage on a modern linux distro, am i loosing 1kb or 10mb?

What does it matter? 10 MB is 1% on a machine with 1 GB RAM, and most machines recent enough to have a 64-bit processor have 1 GB of RAM or more.

---

### Post by bhishan on 2009-10-16
> **armageddon08 said:**
> How much does it affect performance? Are there any visible differences in the performance of 32-bit and 64-bit operating systems on common applications like firefox, amarok, openoffice etc ?

I couldn't feel much difference.

---

### Post by Screwdriver0815 on 2009-10-16
> **Xbehave said:**
> TBF nspluginwrapper does majorly suck


Using more ram, because it's there isn't a great argument. [http://en.wikipedia.org/wiki/64-bit#Pros_and_cons](http://en.wikipedia.org/wiki/64-bit#Pros_and_cons) is worth a read but tbh I wish somebody would just give real world numbers for the difference in ram usage on a modern linux distro, am i loosing 1kb or 10mb?
I have read this and also the same in a german Linux-computer magazine, where they have tested the newest Quad-core  processors: AMD Phenom II, Intel Core 7i. They have tested them in 32 bit and in 64 bit... result: 64 bit was overall (with allprocessors) 14% faster. In some operations it was more than 50% faster.... 

anyway, my understanding is: you have the RAM in the machine. Its there and it waits for work. Now you have a 32 bit system which uses for example 500 MB out of 2 Gb. 
Now you take a 64 bit system and it takes 750 MB... 

whats the problem in this case? :confused: You still have more than 1 GB free memory.  
Why buying gigabytes of RAM and then watching all the time, that for heavens sake, most of it is idleing around? :confused:

---

### Post by Skripka on 2009-10-16
> **sdlynx said:**
> If you don't need the supposedly gained speed, I would stick with x86.  I have x86_64 on my laptop and its great aside from the fact that 32-bit applications that require dependencies are a huge pain to install correctly.

SDLynx

People keep posting this...I don't get why????  There are virtually NO apps on linux that are not available as native 64bit.

---

### Post by maflynn on 2009-10-16
I run into a number of issues with the 64bit vs. 32bit argument.
First people blatenly state that its faster w/o providing any proof - other then their experience and second 64bit is better

while many apps can and will benefit from a 64bit OS they have to coded/compiled that way and even when they do, the memory overhead increases as the data structures are now larger to handle them.  The plus side is that the apps can take advantage of the 64bit registers.

Bigger isn't better, just because and until applications are coded to best take advantage of 64bit, there's little reason to useit, other then if you have >4 gig of ram.

---

### Post by Xbehave on 2009-10-16
> **NoaHall said:**
> I'm currently using 873MB with ...Is that what you wanted? I was more looking for a the difference, under controlled conditions to know what sort of memory usage just using 64bit causes.

> **Screwdriver0815 said:**
> I have read this... result: 64 bit was overall (with allprocessors) 14% faster. In some operations it was more than 50% faster.... 
Do you have a link, I can't read german but google can :D

> anyway, my understanding is: you have the RAM in the machine. Its there and it waits for work. Now you have a 32 bit system which uses for example 500 MB out of 2 Gb. 
My understanding is that "unused" ram is used for buffers/caches/tmpfs/etc, e.g
```
free -m
             total       used       free     shared    buffers     cached
Mem:          1363       1311         **52**          0         59        328
-/+ buffers/cache:        923        439
Swap:         1255         30       1225

```
of 1363mb of ram i only have 54 completely free.
now that's probably a bit atypical because I mount my /tmp to my ram, but generally Linux will try to use "unused" ram to cache files,etc (that is my understanding anyway)

---

### Post by Screwdriver0815 on 2009-10-16
so, now lets have a look at the apps:

all apps in my packagemanager are for AMD_X64. So they are compiled for 64 bit. I do not use any 32 Bit app, with one exception: flashplugin, because it works for me. If it wouldn't, I would download the Alpha from Adobe.

So what is, when an app is compiled for 64 Bit? Does it use 64 Bit registers or not? If not, why?

My assumption is: of course it does. Thats why it is faster. Thats why I use it.

But anyway: even if it was not faster: whats the problem anyway? A 64 Bit system is as flawless as a 32 bit system. 

Why shouldn't I use the computing power of my processor to 100%? Why should I want to leave it at 32 bit? Why? There is no disadvantage in using a 64 bit system. 

What is a really serious reason AGAINST a 64 Bit system? That it **may be** not faster than 32 Bit?? Come on, this is just lame.

```
 free -m
             total       used       free     shared    buffers     cached
Mem:          1986        966       1020          0         28        406
-/+ buffers/cache:        531       1455
Swap:         5820          0       5820 
```

---

### Post by forrestcupp on 2009-10-17
> **Xbehave said:**
> TBF nspluginwrapper does majorly suck

My post was a typo.  I meant run the 32-bit version of Firefox with Flash.  That's what I did, and I don't remember having to go through nspluginwrapper.  It's been a while, though, but I didn't have any trouble with it.

A web browser is not one of the things you'll see a benefit from using 64-bit.

---

### Post by gjoellee on 2009-10-17
Everything that is compiled for 64 bit should be double as fast as what's compiled in 32 bit.

---

### Post by Bachstelze on 2009-10-17
> **gjoellee said:**
> Everything that is compiled for 64 bit should be double as fast as what's compiled in 32 bit.

Lol.

---

### Post by Xbehave on 2009-10-17
> **forrestcupp said:**
> My post was a typo.  I meant run the 32-bit version of Firefox with Flash.  That's what I did, and I don't remember having to go through nspluginwrapper.  It's been a while, though, but I didn't have any trouble with it.

A web browser is not one of the things you'll see a benefit from using 64-bit.
A good point, the only thing to look out for if you go down this path is that all plugins will have to be 32bit (can mozplugger work around this?), so you may need 32bit mplayer/pdf reader (unless mozplugger can work with your 64bit one)/etc

---

### Post by SomeGuyDude on 2009-10-17
Been using 64-bit for a while now. No reason not to. The only app (and you're an Archer, I see) that I had to install 32-bit libraries for was Skype.

---

### Post by forrestcupp on 2009-10-17
> **Xbehave said:**
> so you may need 32bit mplayer/pdf reader (unless mozplugger can work with your 64bit one)/etc

Yeah, I don't know about that.  I guess I had a big enough hard drive that I just let it do its thing, and I didn't care if it had to also install the 32-bit versions of everything it uses.  But it has been a while, so I don't really remember what all I did.  It seemed much easier that way, though.

---

### Post by armageddon08 on 2009-10-17
Wow, there's been quite a discussion. I think I should move to x64, at least I can test it for myself. So my question is do all the commonly used apps(like I've stated previously) have their x64 versions?

---

### Post by Bachstelze on 2009-10-17
> **armageddon08 said:**
> Wow, there's been quite a discussion. I think I should move to x64, at least I can test it for myself. So my question is do all the commonly used apps(like I've stated previously) have their x64 versions?

Yes.

---

### Post by NoaHall on 2009-10-17
> **Bachstelze said:**
> Yes.

+1

I don't use anything 32 bit.

---

### Post by shafin on 2009-10-17
I follow logic of the stupid. 64 bit is newer than 32 bit and hence should be better :)
Have been using 64 bit since feisty fawn. Once 64 bit Flash landed, there are no major issues remaining for me.

---

### Post by Bachstelze on 2009-10-17
> **shafin said:**
> I follow logic of the stupid. 64 bit is newer than 32 bit and hence should be better :)
Have been using 64 bit since feisty fawn. Once 64 bit Flash landed, there are no major issues remaining for me.

"should be" is the keyword here. As Ambrose Bierce said: "The truth is what is. What should be is a dirty lie." 64 bit might be better for you and me, but it's not better for everyone.

---


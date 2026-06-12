---
title: "[idea] replace usplash with splashy"
date: 2007-06-18
forum: Ubuntu Brainstorm
---

### Post by foerdi on 2007-06-18
What about using "splashy" [http://splashy.alioth.debian.org/wiki/doku.php](http://splashy.alioth.debian.org/wiki/doku.php) instead of usplash?

From the wiki:

"Require zero kernel patches/full functionality in user-space "

"Full LSB support "

"Splashy is easier to install than bootsplash because you don't have to patch the kernel! It gives the same resolution as bootsplash and is themeable! Try it!"

---

### Post by el_itur on 2007-06-18
[edit] I found this thread [http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy](http://ubuntuforums.org/showthread.php?t=41709&highlight=splashy) , I will try it and came back to tell you how it plays :)

---

### Post by mostwanted on 2007-06-18
+ 1

---

### Post by el_itur on 2007-06-18
I've managed to install it but I can't make it work properly. Anyway I can't see any advantage in comparison with usplash (remember that they pointed at bootsplash and it's not the same thing).

---

### Post by cjwatson on 2007-06-19
usplash has all the same properties that you cite for splashy here. I think we've put enough work into usplash that replacing it with something else now would be busy-work ...

---

### Post by el_itur on 2007-06-19
that's what I thought . So. thread closed. :)

---

### Post by Jimmy_r on 2007-07-05
> **cjwatson said:**
> usplash has all the same properties that you cite for splashy here. I think we've put enough work into usplash that replacing it with something else now would be busy-work ...

What about these:

Verbose mode (with F2/ESC keys)

Configuration file in XML

It supports millions of colors as well as alpha channels (transparency)

Video mode detection

Really easy to create new themes

Fade in/out effects


Especially the "Easy to create themes" part.
When making a theme requires a makefile and a .c file, you know something is darn wrong.

But of course, keep reinventing the wheel.

And [keep putting more work]("https://wiki.ubuntu.com/UsplashPolishSpec") into Usplash.

Who knows, maybe one day you will have easy to create themes, that can be used on different platforms without recompiling.
Support for more than 256 colors(I do not know much about BOGL: is that possible?)
No need for a usplash.conf with screen resolutions defined.

And then you will be up to speed with Usplash, and we will have another incompatible theme format.

Just one question: If it was not for the work you have put into Usplash, what are the technical reasons for not using Splashy? Is there anything in Usplash that splashy does not have?
Anything Usplash does better?

---

### Post by AlexenderReez on 2007-07-05
> **Jimmy_r said:**
> What about these:

Verbose mode (with F2/ESC keys)

Configuration file in XML

It supports millions of colors as well as alpha channels (transparency)

Video mode detection

Really easy to create new themes

Fade in/out effects


Especially the "Easy to create themes" part.
When making a theme requires a makefile and a .c file, you know something is darn wrong.

But of course, keep reinventing the wheel.

And [keep putting more work]("https://wiki.ubuntu.com/UsplashPolishSpec") into Usplash.

Who knows, maybe one day you will have easy to create themes, that can be used on different platforms without recompiling.
Support for more than 256 colors(I do not know much about BOGL: is that possible?)
No need for a usplash.conf with screen resolutions defined.

And then you will be up to speed with Usplash, and we will have another incompatible theme format.

Just one question: If it was not for the work you have put into Usplash, what are the technical reasons for not using Splashy? Is there anything in Usplash that splashy does not have?
Anything Usplash does better?

it is sound a little bit cruel .... but from my point of view....i agree with dev .....i believe that we need to concentrate more on creating new creative environment .... and improving what we have now...not to replace it.....i think busy-work that had been mention by dev is add more unnecessary work to ubuntu community especially to developers ....cause this package may bring bug and problem ,and need time to correct it.... and a lot of time had been spend for improving usplash ..... i think spashy is in universal repository right now...so if anybody want it....use it....but don't expect won't get any problem...

---

### Post by Jimmy_r on 2007-07-05
> **reez0105 said:**
> it is sound a little bit cruel .... but from my point of view....i agree with dev .....i believe that we need to concentrate more on creating new creative environment .... and improving what we have now...not to replace it.....i think busy-work that had been mention by dev is add more unnecessary work to ubuntu community especially to developers ....cause this package may bring bug and problem ,and need time to correct it.... and a lot of time had been spend for improving usplash ..... i think spashy is in universal repository right now...so if anybody want it....use it....but don't expect won't get any problem...

Well, that is my concern.

Improving usplash to the point where it will be possible for non-programmers to create themes for it, and where it will have the features offered by splashy, will be a lot of busy-work.
Integrating and fixing a few bugs in splashy should not be nearly as much work, provided that I have not missed any great technological advantage of Usplash.

Edit: I will attach a tarball containing a few files to demonstrate why I consider Usplash theme creating currently for programmers only. Makefile and eft-theme.c could be considered the "Theme files" for a Usplash theme.
theme.xml is for a Splashy theme.
Which wold you rather create a theme for?
And besides that, you will not have to manually write the splashy xml file, there is a command-line tool to do that for you.

Edit 2: Sorry if I sound a bit grumpy, but the duplication of efforts all around linuxland is pissing me off, plus I have an annoying cold.

---

### Post by Shin_Gouki2501 on 2007-07-05
> **Jimmy_r said:**
> 
Edit 2: Sorry if I sound a bit grumpy, but the duplication of efforts all around linuxland is pissing me off, plus I have an annoying cold.
I agree with on that but since people are free to choose , they often choose heterogene solutions over homogene ya know :)
( Thats a reason why many peopl stick with windows and like it so much, its not a free unity but atleast it is A unity :) )


wbr Shin Gouki

---

### Post by brim4brim on 2007-07-05
I like the idea of Splashy replacing usplash.

---

### Post by Cirrocco on 2007-07-05
Didn't Linus once say that if a process can be done outside of the Kernel it WILL be done outside of the kernel?

splash should just be an app sitting in /boot
fully configurable by the root user.
the kernel should just call the spash function and move on.
that way if the spash is broken or doesn't exist it doesn't matter.

/my 2cents

---

### Post by justinjstark on 2007-07-07
+1 for splashy.  It is definitely the better solution.

While it would create some work for the devs, it will prove beneficial in the long run.

---

### Post by Nukeador on 2007-07-19
+1 for splashy :)

---

### Post by fenrig on 2007-07-20
Splashy is the way to go +1 for splashy

---

### Post by Iandefor on 2007-07-20
+1 for splashy. Usplash just doesn't cut it.

---

### Post by JockeTF on 2007-07-22
+ 1 for Splashy, it looks easier to configure and customise.

---

### Post by el_itur on 2007-07-22
> **justinjstark said:**
> +1 for splashy.  It is definitely the better solution.

While it would create some work for the devs, it will prove beneficial in the long run.

> **Nukeador said:**
> +1 for splashy :)

> **fenrig said:**
> Splashy is the way to go +1 for splashy

> **Iandefor said:**
> +1 for splashy. Usplash just doesn't cut it.

> **JockeTF said:**
> + 1 for Splashy, it looks easier to configure and customise.


Have anyone of you tried it?. I dind't see any difference with usplash. Also it's not a voting, giving +1 to something won't just make it happen.

---

### Post by dschaefer79 on 2007-07-22
Hi,

Why not integrate UVESAFB and gensplash in ubuntu ?  
[http://dev.gentoo.org/~spock/projects/uvesafb/](http://dev.gentoo.org/~spock/projects/uvesafb/)

It's much better, on my pc I boot in 1920x1200 !

Dominique Schaefer

---

### Post by Iandefor on 2007-07-22
> **el_itur said:**
> Have anyone of you tried it?. I dind't see any difference with usplash. I've used it before.

The reason we're for it is because it's more flexible than usplash (you can do more with it) and it's easier to do a custom theme with it- right now, if you want to do a custom theme in usplash, you have to make indexed .pngs of no more than 256 colors, and the progressbar foreground/background .pngs needs to use the* same* index as the background. Then you have to compile it into a library and make a link at /usr/lib/usplash/usplash-artwork.so to your newly compiled library.

With splashy, you just have to make a few screens (a startup screen and a shutdown screen, and maybe a "dropping into error console" screen), edit a theme configuration file (in XML, no less), and point the splashy configuration file to your new theme. No recompiling needed.

You also have the option of dropping into a console showing you what's happening at any time. Try that with usplash.

Usplash has basically been written from the ground up for Ubuntu and is nowhere near as advanced as other solutions. In other circles, duplication of effort to achieve results inferior to preexisting solutions that *work *is considered of questionable value.> Also it's not a voting, giving +1 to something won't just make it happen.This* is *the ideas pool. The general idea is to flesh out ideas and see what other people think of them. +1 is a quick way to show support. I like the idea, it makes sense, sounds good, +1. It ain't making it's way into Gutsy, but there's no harm in discussing Gutsy+1.> Why not integrate UVESAFB and gensplash in ubuntu ?  
[http://dev.gentoo.org/~spock/projects/uvesafb/]("http://dev.gentoo.org/%7Espock/projects/uvesafb/")

It's much better, on my pc I boot in 1920x1200 ! Looks cool; checking it out now.

---

### Post by Buffalo Soldier on 2007-07-24
+1 vote too. a lot easier and cooler :D

---

### Post by delfick on 2007-07-24
how do we install this ourselves?

---

### Post by destructchaos on 2007-07-25
i personally don't care what splash app is used, so long as it's just a single edit in /boot/grub/menu.lst to turn it off.  i'll stick to watching the text scroll instead of guessing what's going on in the background.  not to mention, any kind of splash is a pointless waste of resources, but by all means, continue to enjoy your slower boot times.  i think the text is prettier anyways.

---

### Post by smartboyathome on 2007-07-25
Actually, I thought the TEXT made it boot slower. Not sure though.

---

### Post by Iandefor on 2007-07-25
> **delfick said:**
> how do we install this ourselves?It's currrently broken in Feisty for various reasons (for some reason, when /etc/inittab was ripped out of Ubuntu, the various splashy scripts that depended on it were never updated to reflect the change, for instance, and it doesn't seem to want to work with Ubuntu's framebuffer). I haven't tested it in Gutsy, but I have a feeling that the changes necessary to make it functional again (it was *just* working in Dapper) are smaller than the changes necessary to make usplash anywhere near as trivial to use.

---

### Post by delfick on 2007-07-25
> **Iandefor said:**
> It's currrently broken in Feisty for various reasons (for some reason, when /etc/inittab was ripped out of Ubuntu, the various splashy scripts that depended on it were never updated to reflect the change, for instance, and it doesn't seem to want to work with Ubuntu's framebuffer). I haven't tested it in Gutsy, but I have a feeling that the changes necessary to make it functional again (it was *just* working in Dapper) are smaller than the changes necessary to make usplash anywhere near as trivial to use.

so is it possible to fix in feisty, or as i interpret from that, it isn't??

---

### Post by Iandefor on 2007-07-25
> **delfick said:**
> so is it possible to fix in feisty, or as i interpret from that, it isn't??Actually, I just managed to make it work on Feisty. The problem is mostly that splashy's configuration has been poorly maintained, so you have to hack one or two things to make it work.

In case you're curious, here's what I did:

Set ENABLE_INITRAMFS to equal 1 in /etc/default/splashy, and then rebuilt initramfs with  > sudo update-initramfs -u -t -k `uname -r`  Those last two steps aren't necessary, but apparently incorporating it into initramfs makes it come up faster. I didn't actually notice any difference when it came up, though.
I made line 68 of /etc/init.d/splashy read
> RLVL=2As opposed to > RLVL=`sed -n 's/id:\([2345]\):initdefault:/\1/ p' /etc/inittab`It's a dirty hack but it will work for the moment. Then I added vga=792 to the kernel options for my default Ubuntu entry in /boot/grub/menu.lst.

without vga=792, splashy absolutely will not work. It will just break in the lamest of ways. vga=791 will work, too, but vga=792 gives you a much higher color index. Right now I haven't worked out a way to make it track boot progress accurately. Will come up with something.

---

### Post by delfick on 2007-07-25
is splashy itself already installed?

---

### Post by Iandefor on 2007-07-25
> **delfick said:**
> is splashy itself already installed?No, but it's in Universe. It apparently conflicts with usplash, so you'll have to remove usplash, too.
> 
sudo apt-get --purge remove usplash*
sudo apt-get install splashy splashy-themes Should do the trick.

Looking at it some more, I think it may need a little more tweaking than I've already given it to really work correctly. It doesn't accurately keep track of the bootup process, even when the correct default runlevel is given and it doesn't quit when GDM starts. If it's not dead when GDM starts then it interferes a wee bit with the screen (little green cursor on top of the screen).
 I'll rewrite my process with some more info.

---

### Post by delfick on 2007-07-25
> **Iandefor said:**
> No, but it's in Universe. It apparently conflicts with usplash, so you'll have to remove usplash, too.
 Should do the trick.

Looking at it some more, I think it may need a little more tweaking than I've already given it to really work correctly. It doesn't accurately keep track of the bootup process, even when the correct default runlevel is given and it doesn't quit when GDM starts. If it's not dead when GDM starts then it interferes a wee bit with the screen (little green cursor on top of the screen).
 I'll rewrite my process with some more info.

ok then........

i'll think i'll wait untill someone (you ? :D) come up with a sure way of installing it....i only recently reinstalled linux because my tinkering was starting to cause some problems....

---

### Post by amano on 2007-08-26
Since I didn't get the impression that usplash development was either high priority nor very ambitious, I would vote to scrap it and move to a more ambitious existing solution.

See [https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish](https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish) : 'Priority: Low". 
And Low priority things don't tend to increase priority over time. At least this is my experience with software projects.

The only change within the last year was from the verbose way in dapper to the Windows-XP-a-like in efty, feisty and gutsy (so far).

Most other distributions have at least a bootsplash which can switch between Quiet and verbose.

---

### Post by xopher on 2007-08-27
I totally agree with amano, and the starter of this thread.

USplash isn't enough for us. It's not simple enough either.

Why not replace it with something better?

Oh, and why did we 'copy' the loading screen (layout) from Windows XP? A full screen, high resolution screen would look better -- and if we'd replace the useless progress bar with eg. icons for what it's actually loading, then it'd even make more sense.

And the inability to switch to verbose isn't a positive mark either -- oh, and when eg. fsck runs in the middle of the boot process -- usplash gets turned off, and we see the raw verbose mode. That's not what we want right? People who don't know what fsck is might see it as an error, or as a sign of instability and inconsistency..

Just my 20 cents :rolleyes:

---

### Post by oomingmak on 2007-09-02
> **xopher said:**
> I totally agree with amano, and the starter of this thread. USplash isn't enough for us. It's not simple enough either.

Why not replace it with something better?
Indeed.


> **amano said:**
> Since I didn't get the impression that usplash development was either high priority nor very ambitious, I would vote to scrap it and move to a more ambitious existing solution.
I agree. 

Given that other more important features get pushed back due to time constraints, then I don't see how a low priority 'cosmetic' issue like this will get attended to any time soon. Why continue with this situation when a simpler and more flexible alternative is *already *available?

I understand that a significant amount of work has been done on Usplash, but if that's the sole reason for sticking with it, then it sounds like a case of throwing good money after bad to me.

---

### Post by Regenwald on 2007-09-02
yeah, i read the splashy's doc and i have to say that i'm very impressed. i can just quote this blueprint ([https://wiki.ubuntu.com/SlickBoot):](https://wiki.ubuntu.com/SlickBoot):)

      Simon's computer rapidly switches between the splash screen, a black screen, a flashing cursor, a brown screen and finally the login screen on boot. This makes him feel that the operating system is unprofessional.
    *

      Matthew's monitor takes a couple of seconds to switch between different modes. The multiple mode switches in the current boot sequence make him nervous.
    *

      When Rodger shuts down his machine, the progress bar appears to stop and then the screen goes blank. He panics and believes the machine has crashed, when in fact this is normal.

think about it, according to their website, you need not to change soo much..

---

### Post by m10 on 2007-09-13
+1
the ubuntu team is reinventing the weel with uspalsh
who had the stupid idea to start working on it?
we're in the open source community(and not in the closed source were everything has to be reinvented)  aren't we?
sorry for the rude tone but i just can't understand...

---

### Post by smartboyathome on 2007-09-13
> **m10 said:**
> +1
the ubuntu team is reinventing the weel with uspalsh
who had the stupid idea to start working on it?
we're in the open source community(and not in the closed source were everything has to be reinvented)  aren't we?
sorry for the rude tone but i just can't understand...

My guess is that the reason they are doing this is because they want something that will better integrate with Ubuntu.

---

### Post by FuturePilot on 2007-09-13
> **smartboyathome said:**
> My guess is that the reason they are doing this is because they want something that will better integrate with Ubuntu.

True, Usplash is very integrated into the system.

---

### Post by n00bWillingToLearn on 2007-09-26
Is there any official project page for usplash? Any official reason why it was even started in the first place? Has anyone found even one advantage to usplash over splashy? 

This is incredably confusing to me. Is it reasonable to contact the package maintainer ( Matthew Garrett? ) to inquire about this? I have a bad feeling that Ubuntu will continue to use Usplash for years to come and that nobody ( not even the developers? ) knows quite why other seemingly better alternatives are not being used.

---

### Post by lemsx1 on 2007-09-28
Hello,

I'm the Splashy main devel (so my opinion is biased).

A bit of history for you guys:

* We created the debsplash port of bootsplash on Alioth so that Debian can have a native boot splash package. That project was quickly replaced with gensplash's patch (gentoo for those of you who don't know). And we abandon that as well

* Ubuntu and the now Splashy developers started working together on usplash. Back then it was a C++ program that people liked, but needed improvement. We switched the code to C and the project developers split (creating other forks like upower)

* Ubuntu devels took the bogl (blotch) code and rename it "usplash" and asked us to switch the name from usplash to something else. We chose "Splashy" (my inspiration). And we went our separate ways.

* Usplash, because of the library is built on, requires a bit more knowledge from the developers in order to do simple things as change themes or add new features. Splashy is fully configurable from 2 XML files and mostly all features can be turn on or off at will.

Now, with that in mind. I don't think it makes sense for Ubuntu developers to replace usplash with Splashy. Not yet at least. People who want Splashy on their systems can simply do: apt-get install splashy. And they will get a program that replaces usplash and works out-of-the-box.

Other major Linux distributions are using, or have plans to use, Splashy as their  main boot splash system. To name a few: OpenSuSE, Xandros, SuSE, Fedora, and of course, Debian. All have shown interest in making Splashy their boot splash system of choice.

The only reason why I think it's better to simply use Splashy for Ubuntu and not any other system, is for the same reason that Beryl and Compiz projects got united into one: avoid wasting resources. All Linux distros use the same kernel (modified a bit), so Splashy will work correctly for all of them without the need to modifying any other part of the OS. To do the same with Usplash requires a bit more effort and testing from them. So, if we can get all the developers to unite under one umbrella, Splashy bugs will be iron out in days instead of weeks or months, and new features will find their way onto the product faster; which will benefit everybody, end-users, developers and the like.

So there you have it. Usplash is a subset of Splashy that works well for Ubuntu. However, Splashy is a more feature rich, elegantly coded app, with a very well organized team of developers, that works for ALL Linux distros with minimal changes from the distro (a few scripts to calculate progress steps and you are done, or simply support LSB and you are done).

Hope that helps put an end to this thread...

You can join Splashy and find out more about it from:

[http://splashy.alioth.debian.org](http://splashy.alioth.debian.org)
#splashy on irc.freenode.net

Ubuntu Gutsy (test) packages:
[http://splashy.alioth.debian.org/wiki/ubuntu](http://splashy.alioth.debian.org/wiki/ubuntu)

---

### Post by veratyr on 2007-10-01
+1

I remember saying this exact same thing back when we first got usplash. I always thought splashy themes were much nicer and they at least gave me the option for verbose. I can remember most people in the ubuntu community were divided over if there should be text or no text at boot. A perfect option was available all along in other distros. F2 for verbose please.

---

### Post by moritz on 2007-10-07
+1 

because usplash is too hard to configure

---

### Post by smartboyathome on 2007-10-07
I am using Splashy now (the debs from the site), and it is great!

---

### Post by derrywang on 2007-10-11
&#65291;1

---

### Post by hexion on 2007-10-12
I've read the whole thread, and I want to contribute with my point of view.

It seems obvious for me that, given those facts described in this thread, Ubuntu should drop usplash and install splashy.

But there's something no one said..
Correct me if I'm wrong, but aren't the Ubuntu devs themselves the developers of usplash?
So, we have a simpler and working solution out there, with its own devel team... planned to be used widely for several other distros.... and Ubuntu keeps on WASTING efforts in programming an alternative application which is currenly less advanced than the other out there and that will be used only by Ubuntu????

Well, I think Ubuntu devs have better things to do than reinventing the wheel.

---

### Post by smartboyathome on 2007-10-12
> **hexion said:**
> I've read the whole thread, and I want to contribute with my point of view.

It seems obvious for me that, given those facts described in this thread, Ubuntu should drop usplash and install splashy.

But there's something no one said..
Correct me if I'm wrong, but aren't the Ubuntu devs themselves the developers of usplash?
So, we have a simpler and working solution out there, with its own devel team... planned to be used widely for several other distros.... and Ubuntu keeps on WASTING efforts in programming an alternative application which is currenly less advanced than the other out there and that will be used only by Ubuntu????

Well, I think Ubuntu devs have better things to do than reinventing the wheel.

Splashy is now offering packages for Gutsy, so you can install it and remove usplash until Ubuntu does replace Usplash and/or works on it to make it more feature rich than Splashy.

---

### Post by hexion on 2007-10-12
> **smartboyathome said:**
> Splashy is now offering packages for Gutsy, so you can install it and remove usplash until Ubuntu does replace Usplash and/or works on it to make it more feature rich than Splashy.

The main point of my post was not the software I have or haven't installed in my box. Fortunatelly my newbie times are far and I know how to do it ;)
An example in this line is that I compile and use my own kernel (after testing Ubuntu's one to file bugs), but that doesn't mean I'm not interested in what decisions Ubuntu devs take about the kernel policy.

What I was trying to say is that there's a huge amount of work to do in Ubuntu to make things work together... so spending part of that time in developing usplash is a waste of resources, giving the fact that the developers of usplash are Ubuntu devs themselves.

---

### Post by amano on 2007-10-16
The latest news from the Splashy homepage sound interesting: 
> Sep 28, 2007 Usplash or Splashy on Ubuntu? Follow this[ thread]("http://ubuntuforums.org/showthread.php?p=3440101#post3440101")

Sep 24, 2007 Splashy works from initramfs on Ubuntu Gutsy. Now we have a page dedicated to Splashy on [Ubuntu ]("http://splashy.alioth.debian.org/wiki/ubuntu")


This very thread is the one being referenced :popcorn:

---

### Post by amano on 2007-10-18
Spec Proposal:

**Summary:**
Move from usplash to splashy

**Scope and Use cases:**
Gustl experiences a boot problem. But he cannot see the error message because he cannot turn on verbose mode on the fly.

**Rationale:**
Splashy is actively developed and maintained. It has more features than its ancestor usplash. And maintaining an own splash system means doubling open source development resources which could be spent in better ways. Better help the splashy people.

**Implementation Plan:**
Make the splashy packages the default and integrate them tightly with upstart.

---

### Post by DizzyTech on 2007-10-18
Perfect stuff.  Glad I got it moved, I think it's an important issue.

---

### Post by brickbat on 2007-10-18
+1 Eye candy and outside the kernel - a no-brainer

---

### Post by Zdravko on 2007-10-19
I don't see why would we ever need to change something working with this ?

---

### Post by DizzyTech on 2007-10-19
USplash has always been reinvention of the wheel.  Now the team wants to put even more work into it to add verbose mode and whatnot... all stuff Splashy already has, and has had.

---

### Post by smartboyathome on 2007-10-19
I have been using splashy's experimental packages, and I think that it is WAY better than Usplash and WAY easier to theme (all it needs is a GUI >.<).

---

### Post by Zdravko on 2007-10-20
Okay.

---

### Post by amano on 2007-10-21
I don't even get the impression that there is much development done with usplash. There has been a spec assigned to Dennis Kaarsemaker but none of the goals of this "usplash polish" spec went into gutsy.

[https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish](https://blueprints.launchpad.net/ubuntu/+spec/usplash-polish)

Note that spashy is already mentioned in the spec. Maybe they told Dennis to stop his work due to a potential splashy inclusion.

---

### Post by screaminj3sus on 2007-10-21
> **Zdravko said:**
> Okay.

Holy one word post batman!

---

### Post by veratyr on 2007-10-22
ignore this...double post

---

### Post by Xbehave on 2007-10-22
will either ever support encrypted root prompts?

---

### Post by smartboyathome on 2007-10-22
> **Xbehave said:**
> will either ever support encrypted root prompts?

I don't know, but splashy SHOULD allow for a prompt to be built in to the splash where specified.

---

### Post by theparag0n on 2007-10-23
+1 

I spent the whole of yesterday trying to make a custom usplash theme work, today i found splashy, read around their wiki, installed it, made my theme and had it running within an hour!

---

### Post by delfick on 2007-10-23
^ cool :D

wanna share ? :D

---

### Post by theparag0n on 2007-10-23
Its for a work project, so i cant give you the actual files, but i can give you a run through.

install splashy from apt 
```
apt-get install splashy splashy-themes
```

test it works with the default theme:
```
splashy test
```

Make your bootup / shutdown / standby / resume / error images.
mine are 1024x768 RGB PNG files. (default GIMP settings)

Grab the font you want to use for your text (i used splashy's default FreeSans.ttf font) and put it in the same folder as your images.

run the theme creation wizard:
```
splashy_config -c
```

And give it the information it asks for.

then just tell splashy to use your new theme:
```
splashy_config -s your_theme_name
```

and test it!
```
splashy test
```

Hopefully this should help!

If you want to edit your theme, it can be found in /etc/splashy/themes/YOURTHEMENAME/

---

### Post by amano on 2007-10-24
Since the splashy developers are monitoring this thread:

Could  you please update the roadmap on your website?

What are the current changes and what are the things that need to be fixed next?

---

### Post by amano on 2007-10-28
Reading this spec which is scheduled for Boston tomorrow, it doesn't seem that they are even considering splashy: [https://blueprints.launchpad.net/ubuntu/+spec/boot-messages](https://blueprints.launchpad.net/ubuntu/+spec/boot-messages)

:(

At least the boot process will probably be investigate on the summit, eg: [https://blueprints.launchpad.net/ubuntu/+spec/hardy-boot-process](https://blueprints.launchpad.net/ubuntu/+spec/hardy-boot-process), maybe they change their minds when doing that.

---

### Post by BlueSkyNIS on 2007-10-29
+1 for splashy, usplash just doesn't cut it. :(

---

### Post by foerdi on 2007-10-29
> **lemsx1 said:**
> 
The only reason why I think it's better to simply use Splashy for Ubuntu and not any other system, is for the same reason that Beryl and Compiz projects got united into one: avoid wasting resources. 

Perhaps you guys should unite, too.

---

### Post by lemsx1 on 2007-10-29
Ok. I'll update our roadmap; however, you can quickly see what we are doing from here:

TODO:

[http://git.debian.org/?p=splashy/splashy.git;a=blob;f=TODO;h=1810ebafc68e4d98d8c5ce23d409d7f639ac95f2;hb=HEAD](http://git.debian.org/?p=splashy/splashy.git;a=blob;f=TODO;h=1810ebafc68e4d98d8c5ce23d409d7f639ac95f2;hb=HEAD)

NEWS:

[http://git.debian.org/?p=splashy/splashy.git;a=blob;f=NEWS;h=c65ad5cc6e0792bb3e89b05d362c1944b42bf9e6;hb=HEAD](http://git.debian.org/?p=splashy/splashy.git;a=blob;f=NEWS;h=c65ad5cc6e0792bb3e89b05d362c1944b42bf9e6;hb=HEAD)

I had to move the GL stuff to 0.4 ;-) I still want to see a fire-breathing Penguin in 3D when I boot my system. I might even put a M$ logo being blasted with flames, just for fun.

---

### Post by lemsx1 on 2007-10-29
A nice list of why Splashy exists (old but good):

[http://splashy.alioth.debian.org/wiki/about](http://splashy.alioth.debian.org/wiki/about)

Splashy is a next generation boot splashing system for Linux systems. Unlike other splashing systems, it needs no patches to the kernel and it's installed like a normal package. Make your boot process eye-candy with Splashy!

Some of Splashy's most noticable features include:

    * Require zero kernel patches/full functionality in user-space
    * Boot/halt/reboot/runlevel-switch support
    * Progressbar support (with optional border)
    * Verbose mode (with F2/ESC keys)
    * Configuration file in XML
    * Cope with any video-mode resolution/size
    * Cope with 8, 16, and 24 bit framebuffers
    * Alpha channel (transparency) support
    * Video mode detection
    * Initramfs support
    * TrueType2 fonts support
    * Lots of image/animation file formats supported: jpg, png, gif, mpg, swf
    * Low dependencies and code in C to best perform
    * Full LSB support
    * Multiple themes support
    * Really easy to create new themes
    * X detection on exit
    * Smooth progressbar movement
    * Animations support
    *  Fade in/out effects
    * Totally configurable

---

### Post by smartboyathome on 2007-10-30
There is also a splashy theme creator being developed now, so no more buggy Usplash theme creation!
[http://opendesktop.org/content/show.php/SplashyCreator?content=67621](http://opendesktop.org/content/show.php/SplashyCreator?content=67621)

---

### Post by Progressive on 2007-10-30
Splashy sounds like a great idea for Hardy. Modularity is key, and all the other features of splashy are just icing on the cake.

All the proposals to "polish" usplash are just re-inventing the wheel. I thought the great thing about open source was that is no longer necessary!

---

### Post by mysticmatrix on 2007-10-30
I just installed Splashy and said
"OMG IS booting up such a fun !!"

Hey, I would like upsplash to work but why reinvent the wheel if something out there already exists.

May be developers know better why Splashy is not a good alternative....

+1 for Splashy (Can we have a poll?)

---

### Post by tubasoldier on 2007-10-31
I read this whole thread.

First of all to the developer who commented in the beginning: We obviously would like splashy. At least consider it. 

To the splashy developers: Thank You.

I have always thought USplash Sucked! I would rather use the old bootsplash that ran in the kernel. I have spent days trying to make custom Usplash themes for myself and for my wife. It just plain blows.

Splashy is great. Themes are easy to make and install. More importantly splashy gives users more choice about what they see when they boot up, which is why I vote yes for it. I also think verbose mode is important. It is hard to know what is going on with USplash putting its ugly A$$ in the way.

---

### Post by timbobsteve on 2007-10-31
Honestly, after spending 2 weeks trying to get a usplash theme to work, I have given up completely on usplash. Any beautifying system that requires a theme developre to understand the actual code itself is just plain rediculous. If you stand back and look at what usplash is supposed to achieve (friendly interface for bootup) you would see that it fails miserably. Usplash really shoots itself in the foot by making it so hard to theme. 

Also the lack of high-resolution/bitsperpixel is really a let down. I have heard the argument that it is to keep backwards compatibility with older systems (or something like that) and it is BS. Splashy/Bootsplash/Gensplash/uboot all work on older systems. So I don't think that is a good enough reason.

If the devs think that usplash is something they don't want to let go of, fine, but please, please, if you are going to keep it then DEVELOP IT! Don't just leave it as is, because right now it is not cutting the mustard!


With all that said... I am off to install Splashy and finally get my Custom boot-splashscreen working!
[/rant]

---

### Post by smartboyathome on 2007-10-31
> **timbobsteve said:**
> If the devs think that usplash is something they don't want to let go of, fine, but please, please, if you are going to keep it then DEVELOP IT! Don't just leave it as is, because right now it is not cutting the mustard!

This is a statement I don't agree with. Usplash is trying to reinvent the wheel (like many have said) and it is doing no good. I have used the Ubuntu splashy theme, and it is 10x better than the usplash one. Please, don't keep it when there is a better alternative.

---

### Post by bash on 2007-10-31
+1 for splashy as default

---

### Post by ssokolow on 2007-11-02
+1 for splashy as default. 

Not every *buntu user (my mother, brother, and a friend use Kubuntu without dual-booting) has a Gentoo user (me) who can discover and install Splashy for them.

---

### Post by kragen on 2007-11-02
I havent had a chance to try it out yet (I've installed it from the repositories, and added vga=791 or whatever to my kernel, but for some reasons nada happens - usplash just comes up instead). However my comments are:

1) What about compatability? Does splashy work on all systems that usplash works on?

2) I'd prefer to see a more seamless version of usplash (ala the Seamless Boot blueprint - [https://blueprints.launchpad.net/ubuntu/+spec/slick-boot](https://blueprints.launchpad.net/ubuntu/+spec/slick-boot)) than I would see a slightly more customisable version of what we already have.

3) Finally, as is the case with all customisation - if your interested in customisation enough, then you can install the alternative packages yourself anyway - the default package should be the one which is most suitable for people who dont want to customise as much. (Dont change to usplash just because its more customisable)

---

### Post by quidpro on 2007-11-05
I also tried several times last night to get Splashy working in Gutsy. No joy. usplash doesn't want to let go, and I'm afraid to get too aggressive as I like a booting system :)  I'm still very interested, though.

Smartboy, you seem to have it working, yes? Any chance you could post your procedure? Did you remove usplash and ubuntu-usplash-theme in order for Splashy to work?

Splashy is much more appealing to me in that the resolutions are there, and the simplicity seems to be there (xml).

I don't understand...some posters think if it is easily customized then it should NOT be the default? That doesn't make sense to me. Most of the system is easily customized...

---

### Post by foerdi on 2007-11-05
I tried to get attention of devs for this thread, but it seems they don't want to change it...

Additionally, when discussing with a dev, he told me that it's better for him when he can hack the usplash-stuff in C.. he says, he doesn't need xml.. 

I think it would be the best idea to unite both, splashy and usplash - but the guys don't want to simplify their work.
They still want to do some more work on usplash: fsck, verbose mode, encryption key, etc.. "polish" :lolflag:

A real programmers guide...
no docs, no simple stuff, just programming to the bare metal

---

### Post by smartboyathome on 2007-11-05
> **quidpro said:**
> Smartboy, you seem to have it working, yes? Any chance you could post your procedure? Did you remove usplash and ubuntu-usplash-theme in order for Splashy to work?

I did get it to work, though not with the packages in the repository. I will post the procedure here:

1. Download the packages from [here]("http://splashy.alioth.debian.org/ubuntu/").
2. Remove Usplash using Synaptic (Splashy cannot be installed with Usplash on the system, unfortunately :().
3. Install Splashy using the package you downloaded.
4. Enjoy!

---

### Post by sicofante on 2007-11-05
+1

---

### Post by quidpro on 2007-11-06
> 2. Remove Usplash using Synaptic (Splashy cannot be installed with Usplash on the system, unfortunately ).

My only prob here is that Synaptic wants to remove the ubuntu-desktop package. :(

---

### Post by smartboyathome on 2007-11-06
Its OK for now to remove ubuntu-desktop, just remember to reinstall it before you upgrade to hardy.

---

### Post by foerdi on 2007-11-16
46 to 7... nice votes

---

### Post by jaybombalous on 2007-11-19
as far as I can tell usplash doesn't even work on my computer. :frown:


not real impressed with usplash at all. That is ubuntu's lowest point. Makes it look second quality at best when I have to fiddle around just to get it to print something to the screen. Black screen is just as annoying as a blue screen...

---

### Post by jaybombalous on 2007-11-19
wtf, now I am pissed. Why can't I un-install usplash and keep my ubuntu-desktop? Or vice versa, why can't I install ubuntu-desktop and not un-install usplash?

I wanna use splashy so whats the fix?

---

### Post by smartboyathome on 2007-11-19
You can always apt-get source ubuntu desktop, change it so usplash isn't a dependancy, and then package it again. Check out Ubuntu's packaging guide (section 2.2) for more tips on how to edit it.

This would only be a temporary fix, though, so I would recommend uninstalling Ubuntu-desktop (its only a meta-package anyway).

---

### Post by ingo on 2007-11-22
I installed splashy 0.3.7 (running on Kubuntu 7.10) and created a theme called test. I set it as the standard and rebooted, taking care to add vga=791 to the grub kernel line.

After having pressed b to boot the selected kernel the default penguin flickers on the screen, disappears and the orange progress bar appears instead.

I'm a bit flummoxed 'cos I didn't expect to see the penguin but my test scheme and secondly because he flickers uncertainly before he makes way to the progress bar.

Am I doing something stupid?

Any help much appreciated!

---

### Post by drf_av on 2007-11-23
Note: when you change theme to splashy, you need to update your initramfs.
After issuing "sudo update-initramfs -u" new themes work for me. I'm quite pleased with Splashy, but I prefer having usplash and new killer features in Hardy :D.

Anyway remember you can always test your current splashy theme by issuing "splashy test" from command line.

---

### Post by ingo on 2007-11-23
Thanks for your reply.

I've done all that but no joy. The splashy test  works fine. Amazing considering that splashy doesn't want to know me otherwise...

Will try usplash over the weekend. Not as pretty, not as flexible but who knows, it may work...

---

### Post by smartboyathome on 2007-11-23
> **drf_av said:**
> Note: when you change theme to splashy, you need to update your initramfs.
After issuing "sudo update-initramfs -u" new themes work for me. I'm quite pleased with Splashy, but I prefer having usplash and new killer features in Hardy :D.

Anyway remember you can always test your current splashy theme by issuing "splashy test" from command line.

What features are you talking about? I didn't know many features were going into it at all in hardy.

---

### Post by drf_av on 2007-11-24
You misunderstood my answer. I meant that ok, splash boot screen might be important, but I think that main focus should be on some more important features. I wasn't talking about new features in usplash, but in the whole distro :D

---

### Post by smartboyathome on 2007-11-24
It wouldn't take much time to do, but I agree that this shouldn't be on the top of the priority list for hardy, or even the middle of it. ;)

---

### Post by lemsx1 on 2007-11-27
Well,

We have good news for you guys.

Splashy 0.3.7 is around the corner and it will have a ton of new things. Our goal has been to be as flexible (and bug free) as possible. And to give you the most features that you can get in a single (small) binary.

Splashy is now being used by many of the big distros (Xandros, Mandriva, SuSE etc... are just a few) and bootsplash(.org) was deprecated in favor of Splashy.

Among the things that you will see in upcoming 0.3.7 are:

- international support (translations are here!)
- initramfs out-of-the-box (directfb bugs iron-out and submitted upstream)
- graphical configuration tool (gsplashy rocks)

We also added support for all the commands supported by usplash. Which means that you can save "splashy_update" as "usplash-update" and be done with "integration". In other words, Splashy is a drop-in replacement for usplash. However, I won't advise people to do that (just yet).

We do want people who are interested in testing to drop by #splashy on irc.freenode.net and provide some feedback.

A good place to start is:
[http://splashy.alioth.debian.org/wiki/developers#notes_on_operating_systems](http://splashy.alioth.debian.org/wiki/developers#notes_on_operating_systems)

I've been doing some Ubuntu testing packages and putting them on our Alioth project page. These are NOT production packages, just for people who like to test things first and don't mind the occasional breakage... Now, I do use these packages myself on all my Ubuntu Gutsy systems (without modifying any of the initrc scripts or anything else from Ubuntu). So, you can be assure that they work as promised.

Hope to see you on #splashy then!

---

### Post by ingo on 2007-11-27
hope you keep us updated and send a link (perhaps already now if you are using it successfully) to the deb file...

---

### Post by sicofante on 2007-11-27
> **smartboyathome said:**
> It wouldn't take much time to do, but I agree that this shouldn't be on the top of the priority list for hardy, or even the middle of it. ;)
That depends only on what are the priorities of the Ubuntu team. If polishing the OS to gain significant market share is one of them, this should be at the top of the list.

---

### Post by drf_av on 2007-11-27
> **sicofante said:**
> That depends only on what are the priorities of the Ubuntu team. If polishing the OS to gain significant market share is one of them, this should be at the top of the list.

I have to disagree here. Mac OSX, which I think is the state of the art in Desktop beauty, has a splash screen that is just as odd as the actual usplash. Win XP, same thing. After all, is something you just have to see for a bunch of seconds. While you see all the time your theme, now that should be really polished... :roll:

---

### Post by ingo on 2007-11-28
> **lemsx1 said:**
> So, you can be assure that they work as promised.

Hope to see you on #splashy then!Well, just come from there and installed the 0.3.7 packages (first the lib, then the programme, then the lib dev) onto a pristine 10.07 kubuntu gutsy setup which had usplash removed first. Unfortunately I still get ```
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```when I want to test splashy. I feel like I am just missing something...

---

### Post by ingo on 2007-11-28
Having said that, splashy worked!!! :lolflag::guitar::lolflag:

All I did was put vga=791 at the end of the kernel line and removed the fourth line saying "quiet" so that my kubuntu entry looks as follows```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,9)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxthisstupidbloodylongcodeinsteadof/dev/sdb10xx ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.22-14-generic
```Now for some serious tweaking...
                                 

Interesting fact: on first boot I had a time out and CTRL ALT DEL brough up kdm - on second boot straight into kdm

---

### Post by smartboyathome on 2007-11-28
By the way, remember to update your initramfs before changing themes, otherwise it will act a little buggy. You can update it by running the following command:

update-initramfs -u -t -k `uname -r`

---

### Post by ingo on 2007-11-28
> **drf_av said:**
> Mac OSX, which I think is the state of the art in Desktop beauty, has a splash screen that is just as odd as the actual usplash. Win XP, same thing.And it so happens they are both proprietary and nothing can be changed. One aspect of Linux is about fun, about being able to change things yourself. 

Also, together with splashy and remastersys anybody can make their own distro!!! Now that is exciting...

BTW, remastersys also obliviates the need for backups 'cos it enables you to back up your _whole system_ in the form of an installable live CD!!!

---

### Post by smartboyathome on 2007-11-28
[off-topic]In reply to your statement about remastersys, I find that if you have a lot of stuff on your disk (like I do) you won't be able to back it up to a CD or even a DVD. So that can't be the "perfect" solution, but it is one of them[/off-topic]

Splashy does make it easier to change stuff, but until the GUI is released, it is just as good as usplash to a newb (as a newb wouldn't want to touch a terminal anyway).

---

### Post by drf_av on 2007-11-29
> **ingo said:**
> And it so happens they are both proprietary and nothing can be changed. One aspect of Linux is about fun, about being able to change things yourself. 

Also, together with splashy and remastersys anybody can make their own distro!!! Now that is exciting...

BTW, remastersys also obliviates the need for backups 'cos it enables you to back up your _whole system_ in the form of an installable live CD!!!

Yes, after all, installing splashy isn't that hard, and anyone can have what he likes. So it's not a matter of what will be default, because remember that beauty is a really subjective topic. Most of my friends still prefer usplash instead of my new shiny splashy. But, you know, this is the beauty of open source software, and this beauty is not subjective :guitar:

---

### Post by lemsx1 on 2007-11-29
> **smartboyathome said:**
> [off-topic]In reply to your statement about remastersys, I find that if you have a lot of stuff on your disk (like I do) you won't be able to back it up to a CD or even a DVD. So that can't be the "perfect" solution, but it is one of them[/off-topic]

Splashy does make it easier to change stuff, but until the GUI is released, it is just as good as usplash to a newb (as a newb wouldn't want to touch a terminal anyway).

Gsplashy and a new Qsplashy are in the works and will be released with 0.3.7.

Gsplashy is more mature and it just works. It's based on GTK library.

Qsplashy is a project that spawn out of the jealousy of having Gsplashy, and I have to say I'm very impressed on how it looks and the fact that it just works!

[http://splashy.alioth.debian.org/wiki/developers#subprojects](http://splashy.alioth.debian.org/wiki/developers#subprojects) for those of you interested in reading about it ... (and experimenting with it before release).

---

### Post by ingo on 2007-11-30
So far those links do not contain an awful log :D But you lot are doing great work! Any ideas on the release date?

---

### Post by 23meg on 2007-11-30
Matthew Garrett has a comment:

[http://mjg59.livejournal.com/78284.html](http://mjg59.livejournal.com/78284.html)

---

### Post by smartboyathome on 2007-12-01
Break Suspend/Hibernate? I thought it was already broken on a lot of systems. :p

Anyway, I haven't experienced any "major" problems with Splashy yet (though I haven't tried suspending or hibernating since i am on an external hard drive), but as soon as I get my new internal drive into my lappy, I will try it and see if it works (heck, I may try it with the external drive just to see if it works).

---

### Post by 23meg on 2007-12-01
Breaking it on even more systems wouldn't be desirable, would it?

---

### Post by smartboyathome on 2007-12-01
Probably not ;)

---

### Post by stoffe on 2007-12-01
> **23meg said:**
> Matthew Garrett has a comment:

[http://mjg59.livejournal.com/78284.html](http://mjg59.livejournal.com/78284.html)

IMO that makes Splashy a non-option until it behaves at least as well as Usplash. But since Usplash manages to behave (although via hackish methods) the Splashy devs could do the same and then ask again.

---

### Post by lemsx1 on 2007-12-03
> **23meg said:**
> Breaking it on even more systems wouldn't be desirable, would it?

Umm... I don't use suspend/hibernate myself, but Tim, one of the Splashy devels, does. And he's the package maintainer for both Splashy and Uswsusp (aka suspend).

[http://packages.debian.org/sid/uswsusp](http://packages.debian.org/sid/uswsusp)

As you can see, suspend calls functions from libsplashy1 directly, so it can show a progressbar when going into suspend and coming out of suspend. Splashy themes already supports images for this.

I'm not sure what's broken about that (or if it works for most/all people). But, if i breaks for some of you, just file bugs against Splashy and/or Uswsusp. We don't ignore bugs.

I'm one of those people who don't reboot often, but when I do, I dislike seeing ugly text while the system boots. We started the usplash project to solve this issue and we yield the name "usplash" to Ubuntu to avoid confusing users (In fact, usplash was supposed to be the name of the specification, not the binary itself, but... now it's done). (See more about this here [http://splashy.alioth.debian.org/wiki/history](http://splashy.alioth.debian.org/wiki/history)). To me it does not matter which option is chosen, for as long as it works.  (I use usplash on some of my ubuntu systems)

Now, we continue with Splashy because it's more feature rich (and flexible) and it does a better job at presenting the users with a better booting/shutting down experience. Splashy is also distro agnostic. So, it matters to us when the ArchLinux, RPath (1 devel is part of splashy), SuSE, Mandriva, Xandros (1 devel constantly send patches to splashy), Mepis, Gentoo (1 devel part of splashy), Slackware (1 devel part of splashy), plus other distros, write to us saying that they just love the elegance of Splashy :-)

At some point we'll attempt  to merge both projects. For now, Splashy just does everything usplash does (with the same commands) and it does so while giving you full resolution support, XML configuration files, easier theme management, and a lot of other things.

We are getting closer to release 0.3.7, which will bring a lot of things to the table. Sorry that I don't have a timeline at the moment, but we are just waiting for a single package to be uploaded to Debian Sid so we can move forward with packages. (Sources are release no matter what to the Alioth project, but, Splashy is developed mainly on Debian/Ubuntu and patches we submit upstream to directfb need to be digested by the debian developers so we can compile against the patched directfb libs).

Hope that keeps things clear... As far as I know, Splashy works with suspend.

---

### Post by ingo on 2007-12-04
Glad you put the record straight again, lmsx1

---

### Post by 23meg on 2007-12-04
[QUOTE=lemsx1]As you can see, suspend calls functions from libsplashy1 directly, so it can show a progressbar when going into suspend and coming out of suspend. Splashy themes already supports images for this.

I'm not sure what's broken about that (or if it works for most/all people).[/QUOTE]

As I understand, uswsusp is for userspace software suspend, and isn't even installed by default in Ubuntu, so it doesn't have anything to do with Splashy (allegedly) breaking suspend. 

[QUOTE=lemsx1]Hope that keeps things clear... As far as I know, Splashy works with suspend.[/QUOTE]

I wasn't making a case against or for Splashy myself; my post was in response to smartboyathome's "I thought it was already broken on a lot of systems" comment, and based on Garrett's comment which I linked to, which was written in repsonse to [a blog post by a Splashy developer.]("http://fboudra.free.fr/wordpress/?p=7")

If you argue that his comment is not entirely true, you should perhaps get your argument across to him directly, maybe by posting a comment on the blog post. And if or when it's your intention to push Splashy as a replacement, in case you don't know (you probably do), you should write a blueprint and/or start a discussion on the ups and downs of using Splashy in one of the development mailing lists; discussing it on the forums won't really accomplish anything.

---

### Post by sicofante on 2007-12-04
> **23meg said:**
> discussing it on the forums won't really accomplish anything.
Wrong. Discussing it in the forums will make users aware of what's going on and what they can demand from the developers. It's the developers fault not to watch these forums, not the other way round. Ubuntu is a privately sponsored endeavour. If it wants to succeed they better listen to their users where their users want to speak, which happen to be these forums. (This has been discussed ad nauseam and I don't want to start a flame over the issue.)

I thank you, lemsx1, not only for being part of the Splashy initiative but also for descending to these forums where mere mortals talk about their issues with Ubuntu and explain what Splashy can do that Usplash can't. Thank you very much and please keep us posted.

---

### Post by 23meg on 2007-12-04
[QUOTE=sicofante]Wrong. Discussing it in the forums will make users aware of what's going on and what they can demand from the developers.[/QUOTE]

Sure, that's what it will do, so let me apologize and correct my wording: you can't possibly include Splashy in Ubuntu by just discussing the ups and downs of it on the forums; you'll have to post to an über-secret mailing list and some obscure website called Launchpad where an elite clan of developers hold secret rituals in which they sacrifice forum users before discussing new features.

---

### Post by sicofante on 2007-12-04
I see you're an Ubuntu Member, 23meg. While I don't know exactly what that means, I sincerely hope people paid by Mr. Shuttleworth know what I'm talking about. If you believe ordinary users should be forced to use the developers tools and not the other way round and you have any serious responsibility in the development or marketing of Ubuntu, then I'm very sorry for this project.

---

### Post by 23meg on 2007-12-04
My post was in reply to lemsx1, who's a *developer* for an upstream project, not an ordinary user, and my intention was to inform them on what they should to as an upstream developer if they intend to have their software integrated. Every distro has different policies, processes and venues of communication for this kind of thing, and I don't expect every upstream developer to be 100% sure of what exactly to do for every distro, so I thought it might be useful. I was a bit off with the wording, and I corrected that.

---

### Post by Spacebaboon on 2007-12-04
> **ingo said:**
> Having said that, splashy worked!!! :lolflag::guitar::lolflag:

All I did was put vga=791 at the end of the kernel line and removed the fourth line saying "quiet" so that my kubuntu entry looks as follows```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,9)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxthisstupidbloodylongcodeinsteadof/dev/sdb10xx ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.22-14-generic
```Now for some serious tweaking...
                                 

Interesting fact: on first boot I had a time out and CTRL ALT DEL brough up kdm - on second boot straight into kdm

I'm in the same boat, but with fewer paddles, or something!

on a cleanish Gutsy Kubuntu, used Adept to remove usplash before adding Splashy, Splashy Themes, and splashyl or whatever the library is called.

I've added the fingerprint theme, and set the config to use that. and I've updated my menu.lst to have exactly the same options as your example. 

But I just get a black screen when booting up / shutting down. and the same error message when I try running sudo splashy test in a terminal.
which is 'Splashy ERROR: Couldn't splashy_start_splashy(). Error -2'

Any ideas, anyone?

---

### Post by smartboyathome on 2007-12-04
> **smartboyathome said:**
> By the way, remember to update your initramfs before changing themes, otherwise it will act a little buggy. You can update it by running the following command:

update-initramfs -u -t -k `uname -r`

Try the terminal command in this comment, spacebaboon.

---

### Post by ingo on 2007-12-04
> **Spacebaboon said:**
> I'm in the same boat, but with fewer paddles, or something!Which paddles did you use? The ones that came with the (K)Ubuntu boat (don't ask me why they put them in there 'cos they've got holes in them) or the extra special fast 0.3.7 ones?

---

### Post by Jimmy_r on 2007-12-09
For those of you having problems, here are the exact steps I used to get a working splashy installed under 32-bit Ubuntu Gutsy:

[LIST=1]
[*]Open Synaptic. Remove the package 'usplash'.
[*]Go to [http://splashy.alioth.debian.org/ubuntu/](http://splashy.alioth.debian.org/ubuntu/), download and install the packages 'libsplashy1_0.3.7-2_i386.deb' and 'splashy_0.3.7-2_i386.deb'.
[*]Open /boot/grub/menu.lst, find the line that looks like this(could look slightly different):
```
# defoptions=quiet splash locale=sv_SE
```
add vga=791 at the end:
```
# defoptions=quiet splash locale=sv_SE vga=791
```
[*]Run the command ```
sudo update-grub
```
[*]Run the command ```
sudo update-initramfs -uk all
[*]Reboot and test

```[/LIST]

Step 3 and 4 above could alternatively be done by using StartUp-Manager(see signature) and change the resolution and color depth options.
SUM can also install/set splashy themes.

For the record, both my desktop(tyan tomcat k8e-sli, nvidia 6600gt with proprietary drivers) and my laptop(Zepto znote, intel 965) suspends/hibernates fine using splashy.

---

### Post by lemsx1 on 2007-12-09
Excellent!

I just uploaded those 0.3.7 packages to /wiki/ubuntu as we released that new version of Splashy yesterday.

Can you post your suspend/hibernate setup using such a simple mini-howto style?

---

### Post by lemsx1 on 2007-12-09
> **Spacebaboon said:**
> I'm in the same boat, but with fewer paddles, or something!

on a cleanish Gutsy Kubuntu, used Adept to remove usplash before adding Splashy, Splashy Themes, and splashyl or whatever the library is called.

I've added the fingerprint theme, and set the config to use that. and I've updated my menu.lst to have exactly the same options as your example. 

But I just get a black screen when booting up / shutting down. and the same error message when I try running sudo splashy test in a terminal.
which is 'Splashy ERROR: Couldn't splashy_start_splashy(). Error -2'

Any ideas, anyone?

Error -2 means "splashy could not open a framebuffer" (directfb really). The way to fix this is to make sure that vesafb was used:

cat /proc/fb
ls -l /dev/fb0

Check Splashy's FAQ on the wiki (Google is your friend).

---

### Post by lemsx1 on 2007-12-09
> **23meg said:**
> My post was in reply to lemsx1, who's a *developer* for an upstream project, not an ordinary user, and my intention was to inform them on what they should to as an upstream developer if they intend to have their software integrated. Every distro has different policies, processes and venues of communication for this kind of thing, and I don't expect every upstream developer to be 100% sure of what exactly to do for every distro, so I thought it might be useful. I was a bit off with the wording, and I corrected that.

Thanks for the information. I have a Launchpad account myself, but I have not gone that deep into understanding how Ubuntu works.

We have mostly Debian Developers in our team (out of all distros). So, our releases are usually biased in favor of Debian Sid. My hope is that if Splashy becomes good enough in Sid, it will eventually be used by other distros, includng Ubuntu. Perhaps it will not replace Usplash, but... It's an alternative to it. Just like Ubuntu is not meant to replace Windows, but be an alternative to it. Same idea.

We will continue to grow in experience as Splashy matures. The team is growing (fast) and since bootsplash was abandoned in favor of Splashy, all sorts of people have come to help us get whatever they need for their own custom distros (or personal desktops).

Usually people's choice decides the outcome of a project. Splashy has a lot to offer with it's very simple design and XML-based configuration and themes. Very modular, very flexible, and it just works. 

Perhaps I'll advocate for Usplash being replace by Splashy when Splashy 0.3.10 comes out (2 more revisions. Another 4 months or so). By then we will do the blue prints and whatever is needed to get Ubuntu's devel attention (or I can just talk directly to Sladen, since we worked together when our usplash branch started (now known as Splashy)).

Thanks again for the information. Ubuntu's policies are not as hard to follow (like other distros).

---

### Post by bash on 2007-12-10
I am running 64bit Gutsy, so those .debs don't work for me. Tried compiled it. Worked all good. Checkinstalled it. But then splashy complained about a missing libsplashy. Anyone got current .debs for 64? Because the official ubuntu splashy packages are quite outdated.

---

### Post by smartboyathome on 2007-12-10
If I had a 64 bit machine, I would try my hand at making one (have been trying to learn packaging lately). I don't have one, though. :(

---

### Post by g2g591 on 2007-12-10
look at a bit of history i got from the splashy wiki. Usplash is a fork of splashy that was formed (by ubuntu) when during discussion of changing to splashy and having a virtual package called usplash that would be satisfied by splashy (and some other, can't remember). I tried out Splashy  in Debian unstable and it worked very well (incredibly easy to change splash screens too)

---

### Post by lemsx1 on 2007-12-11
> **bash said:**
> I am running 64bit Gutsy, so those .debs don't work for me. Tried compiled it. Worked all good. Checkinstalled it. But then splashy complained about a missing libsplashy. Anyone got current .debs for 64? Because the official ubuntu splashy packages are quite outdated.

You can do 1 of 2 things:

1. add deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) main to your /etc/sources.list file and then do: apt-get update; cd /tmp; apt-get source splashy; cd splashy-0.3.7; debuild -uc -us; dpkg -i ../splashy_*.deb ../libsplash1*.deb

# Note, because of a mistake by the debian maintainer that will actually give you an error. They know about this issue and they will fix it ASAP

2. get the source from [http://splashy.alioth.debian.org/ubuntu/](http://splashy.alioth.debian.org/ubuntu/) (everything that's not a .deb) and do: dpkg-source -x splashy*.dsc; cd splashy-0.3.7; debuild -uc -us

This will work on any system.

---

### Post by John Jason Jordan on 2007-12-15
I heard about splashy in another thread on the x86_64 forum. I found it in Synaptic on my Gutsy x86_64 installation and installed it, together with splashy-themes. However, it doesn't work. That is, I restarted the computer, but no splashy. From the command line I get:

jjj@Devil7:~$ splashy test
jjj@Devil7:~$ Splashy ERROR: Couldn't splashy_start_splashy(). Error -2

What does Error -2 mean?

---

### Post by smartboyathome on 2007-12-15
You are using an older version of splashy (which doesn't work very well imo). I would suggest that you download the source from [here]("https://alioth.debian.org/frs/download.php/2218/splashy-0.3.7.tar.gz") and extract it, then open a terminal in the extracted folder and type compile, then type make, then type sudo make install.

---

### Post by amano on 2007-12-25
BTW, a new version of splashy is out since Dec. 18th.

Changes between 0.3.7 and 0.3.8
-------------------------------
 * Bug fixes: 
   - /etc/lsb-base-logging.sh now checks whether it should unmount $STEPS_DIR before doing so
   - /etc/lsb-base-logging.sh now checks whether it should start keymap.sh/console-screen.sh on
     debian systems
   - console-tools/config.d/splashy touches /dev/shm/splashy* files to signal lsb-base-loggin.sh
     that it needs to start a process like keymap.sh/console-screen.sh

In the repos is still 0.3.7 available.

---

### Post by John Jason Jordan on 2007-12-25
> **amano said:**
> BTW, a new version of splashy is out since Dec. 18th.
Changes between 0.3.7 and 0.3.8 ...
In the repos is still 0.3.7 available.
Synaptic on my Gutsy x86_64 computer shows only 3.3, which is what I have installed, and I have all the repositories enabled. Never figured out how to make it work anyway, though.

---

### Post by smartboyathome on 2007-12-25
> **John Jason Jordan said:**
> Synaptic on my Gutsy x86_64 computer shows only 3.3, which is what I have installed, and I have all the repositories enabled. Never figured out how to make it work anyway, though.

You need to install the packages from the site ([http://splashy.alioth.debian.org/ubuntu/](http://splashy.alioth.debian.org/ubuntu/)), and it should work fine. Remember to uninstall Usplash before installing.

---

### Post by John Jason Jordan on 2007-12-25
> **smartboyathome said:**
> You need to install the packages from the site ([http://splashy.alioth.debian.org/ubuntu/](http://splashy.alioth.debian.org/ubuntu/)), and it should work fine. Remember to uninstall Usplash before installing.
When I went to uninstall usplash it also wanted to uninstall:

debian-edu-artwork-usplash
ubuntu-desktop
usplash-theme-ubuntu

Uninstalling ubuntu-desktop scares me. I can't figure out what exactly it does. All it says about it is:

The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system
It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

---

### Post by Jimmy_r on 2007-12-25
Removing ubuntu-desktop will not cause any harm to your system.
It contains nothing, it is just used to tell the package manager what other packages make up a complete Ubuntu desktop system.
Since you already have those other components installed, you can safely remove ubuntu-desktop.

Then just reinstall it later if you upgrade when a new version of Ubuntu is released.

---

### Post by John Jason Jordan on 2007-12-25
> **Jimmy_r said:**
> Removing ubuntu-desktop will not cause any harm to your system.
It contains nothing, it is just used to tell the package manager what other packages make up a complete Ubuntu desktop system.
Since you already have those other components installed, you can safely remove ubuntu-desktop.
Then just reinstall it later if you upgrade when a new version of Ubuntu is released.


OK, I did a complete removal of usplash. Since I had splashy 3.3 installed from Synaptic, I also did a complete uninstall of that as well. Then I downloaded splashy-0.3.8.tar.gz and extracted it to ~/Software. It made a folder there and I navigated to the folder with a terminal window. Looking  back in this thread, smartboyathome said to type compile, then make, then sudo make install. Unfortunately, this is what I got:

jjj@Devil7:~/Software/splashy-0.3.8$ compile
bash: compile: command not found

I think I installed a package from source only once, a long time ago, and I am not familiar with the procedure. What do I do next? Oh, and bear in mind that I have Gutsy x86_64.

---

### Post by smartboyathome on 2007-12-25
It is a debian package, you can just double click to install it.

---

### Post by John Jason Jordan on 2007-12-25
> **smartboyathome said:**
> It is a debian package, you can just double click to install it.
Sorry, I wasn't clear. It is not a package. It is the source file. I have to use the source because the only .deb files on the FTP site are 1386 and my Gutsy is x86_64. I downloaded splashy-0.3.8.tar.gz and extracted it. But when I follow the instructions for compile, make and make install they do not work (see error posted above).

---

### Post by delfick on 2007-12-25
that's because "compile" isn't a program :D

"make" is the program that compiles the source for you :D

though usually, there's a ./configure or ./autogen.sh that you have to do before that.....

---

### Post by John Jason Jordan on 2007-12-25
> **delfick said:**
> that's because "compile" isn't a program :D

"make" is the program that compiles the source for you :D

though usually, there's a ./configure or ./autogen.sh that you have to do before that.....
OK, I tried ./configure and it complained:

checking for splashy... configure: error: Package requirements (glib-2.0, directfb >= 0.9.22) were not met:
No package 'glib-2.0' found
No package 'directfb' found

And then:

jjj@Devil7:~/Software/splashy-0.3.8$ sudo apt-get install directfb
[sudo] password for jjj:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package directfb
jjj@Devil7:~/Software/splashy-0.3.8$ sudo apt-get install glib-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-2.0
jjj@Devil7:~/Software/splashy-0.3.8$ 

I have all the repositories enabled. I tried adding the repository suggested by lemsx1 above:

add deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) main to your /etc/sources.list file 

But after adding it I could not update my sources.list file. There is something wrong with that repository.

---

### Post by smartboyathome on 2007-12-25
Take that repo off then, and then search synaptic for that stuff.

---

### Post by delfick on 2007-12-25
try 

sudo apt-get install libglib2.0-dev libdirectfb-dev 

:D

---

### Post by John Jason Jordan on 2007-12-25
> **John Jason Jordan said:**
> OK, I tried ./configure and it complained:

checking for splashy... configure: error: Package requirements (glib-2.0, directfb >= 0.9.22) were not met:
No package 'glib-2.0' found
No package 'directfb' found

OK, finally got the right libraries installed. It turns out that ./configure reports the incorrect missing component. It needs libgl-2.0-dev, not glib-2.0 and it  needs libdirectfb-dev, not directfb. I installed those with Synaptic, after which ./configure was happy. However, the make command gave me another whole list of errors:

```
configure complete, now type 'make'

jjj@Devil7:~/Software/splashy-0.3.8$ make
make  all-recursive
make[1]: Entering directory `/home/jjj/Software/splashy-0.3.8'
Making all in po
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/po'
Making all in doc
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/doc'
Making all in src
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-splashy_config-functions.o -MD -MP -MF ".deps/splashy_config-splashy_config-functions.Tpo" -c -o splashy_config-splashy_config-functions.o `test -f 'splashy_config-functions.c' || echo './'`splashy_config-functions.c; \
        then mv -f ".deps/splashy_config-splashy_config-functions.Tpo" ".deps/splashy_config-splashy_config-functions.Po"; else rm -f ".deps/splashy_config-splashy_config-functions.Tpo"; exit 1; fi
splashy_config-functions.c:40:71: error: magic.h: No such file or directory
splashy_config-functions.c: In function ‘install_theme’:
splashy_config-functions.c:126: error: ‘magic_t’ undeclared (first use in this function)
splashy_config-functions.c:126: error: (Each undeclared identifier is reported only once
splashy_config-functions.c:126: error: for each function it appears in.)
splashy_config-functions.c:126: error: expected ‘;’ before ‘cookie’
splashy_config-functions.c:127: error: ‘cookie’ undeclared (first use in this function)
cc1: warnings being treated as errors
splashy_config-functions.c:133: warning: implicit declaration of function ‘magic_load’
splashy_config-functions.c:135: warning: implicit declaration of function ‘magic_error’
splashy_config-functions.c:135: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
splashy_config-functions.c:139: warning: implicit declaration of function ‘magic_file’
splashy_config-functions.c:139: warning: assignment makes pointer from integer without a cast
splashy_config-functions.c:161: warning: implicit declaration of function ‘magic_close’
splashy_config-functions.c: In function ‘check_image’:
splashy_config-functions.c:1288: error: ‘magic_t’ undeclared (first use in this function)
splashy_config-functions.c:1288: error: expected ‘;’ before ‘cookie’
splashy_config-functions.c:1289: error: ‘cookie’ undeclared (first use in this function)
splashy_config-functions.c:1297: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
splashy_config-functions.c:1301: warning: assignment makes pointer from integer without a cast
make[2]: *** [splashy_config-splashy_config-functions.o] Error 1
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jjj/Software/splashy-0.3.8'
make: *** [all] Error 2
jjj@Devil7:~/Software/splashy-0.3.8$ 
```
I think the above requires the attention of the developers, so I am going to abandon the effort to install splashy on x86_64 Gutsy for the time being. I wish I knew how to make a .deb file from the source, because a 64-bit .deb would have eliminated hours of time I have spent trying to install it. Maybe someone who knows how can create one for 64-bit Ubuntu users.

---

### Post by smartboyathome on 2007-12-25
> **John Jason Jordan said:**
> OK, finally got the right libraries installed. It turns out that ./configure reports the incorrect missing component. It needs libgl-2.0-dev, not glib-2.0 and it  needs libdirectfb-dev, not directfb. I installed those with Synaptic, after which ./configure was happy. However, the make command gave me another whole list of errors:

```
configure complete, now type 'make'

jjj@Devil7:~/Software/splashy-0.3.8$ make
make  all-recursive
make[1]: Entering directory `/home/jjj/Software/splashy-0.3.8'
Making all in po
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/po'
Making all in doc
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/doc'
Making all in src
make[2]: Entering directory `/home/jjj/Software/splashy-0.3.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-splashy_config-functions.o -MD -MP -MF ".deps/splashy_config-splashy_config-functions.Tpo" -c -o splashy_config-splashy_config-functions.o `test -f 'splashy_config-functions.c' || echo './'`splashy_config-functions.c; \
        then mv -f ".deps/splashy_config-splashy_config-functions.Tpo" ".deps/splashy_config-splashy_config-functions.Po"; else rm -f ".deps/splashy_config-splashy_config-functions.Tpo"; exit 1; fi
splashy_config-functions.c:40:71: error: magic.h: No such file or directory
splashy_config-functions.c: In function &#8216;install_theme&#8217;:
splashy_config-functions.c:126: error: &#8216;magic_t&#8217; undeclared (first use in this function)
splashy_config-functions.c:126: error: (Each undeclared identifier is reported only once
splashy_config-functions.c:126: error: for each function it appears in.)
splashy_config-functions.c:126: error: expected &#8216;;&#8217; before &#8216;cookie&#8217;
splashy_config-functions.c:127: error: &#8216;cookie&#8217; undeclared (first use in this function)
cc1: warnings being treated as errors
splashy_config-functions.c:133: warning: implicit declaration of function &#8216;magic_load&#8217;
splashy_config-functions.c:135: warning: implicit declaration of function &#8216;magic_error&#8217;
splashy_config-functions.c:135: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
splashy_config-functions.c:139: warning: implicit declaration of function &#8216;magic_file&#8217;
splashy_config-functions.c:139: warning: assignment makes pointer from integer without a cast
splashy_config-functions.c:161: warning: implicit declaration of function &#8216;magic_close&#8217;
splashy_config-functions.c: In function &#8216;check_image&#8217;:
splashy_config-functions.c:1288: error: &#8216;magic_t&#8217; undeclared (first use in this function)
splashy_config-functions.c:1288: error: expected &#8216;;&#8217; before &#8216;cookie&#8217;
splashy_config-functions.c:1289: error: &#8216;cookie&#8217; undeclared (first use in this function)
splashy_config-functions.c:1297: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
splashy_config-functions.c:1301: warning: assignment makes pointer from integer without a cast
make[2]: *** [splashy_config-splashy_config-functions.o] Error 1
make[2]: Leaving directory `/home/jjj/Software/splashy-0.3.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jjj/Software/splashy-0.3.8'
make: *** [all] Error 2
jjj@Devil7:~/Software/splashy-0.3.8$ 
```
I think the above requires the attention of the developers, so I am going to abandon the effort to install splashy on x86_64 Gutsy for the time being. I wish I knew how to make a .deb file from the source, because a 64-bit .deb would have eliminated hours of time I have spent trying to install it. Maybe someone who knows how can create one for 64-bit Ubuntu users.

There are instructions on how to make a package for it, so maybe if you get it compiled you can create the package for them. :)

---

### Post by John Jason Jordan on 2007-12-26
> **smartboyathome said:**
> There are instructions on how to make a package for it, so maybe if you get it compiled you can create the package for them. :)
I could probably find instructions and eventually figure it out. However, the errors I got when I tried to install it lead me to suspect that I wouldn't be successful creating a .deb out of the source either. 

Meantime I discovered the splashy forums at alioth. I posted the problems with make there. We'll see if anyone can point me in the right direction for fixing it.

---

### Post by lemsx1 on 2007-12-26
Ummm... there is extensive documentation on how to install Splashy from our wiki page:

[http://splashy.alioth.debian.org/wiki/installation](http://splashy.alioth.debian.org/wiki/installation)

Most people can simply get Splashy from the Debian repository (note that 0.3.8 was uploaded a few minutes ago and it's still in incoming.debian.org):

[http://packages.debian.org/splashy](http://packages.debian.org/splashy)

Ubuntu users are better off using my Gutsy packages from:

[http://splashy.alioth.debian.org/ubuntu](http://splashy.alioth.debian.org/ubuntu)

I posted instructions on how to compile them by yourself, for Ubuntu, here:

[http://splashy.alioth.debian.org/wiki/ubuntu](http://splashy.alioth.debian.org/wiki/ubuntu)

To save you some time:

0. apt-get install libdirectfb-dev  libglib2.0-dev build-essential
1. mkdir /tmp/splashy; cd /tmp/splashy
2. wget [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.diff.gz](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.diff.gz) [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.dsc](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.dsc) [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8.orig.tar.gz](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8.orig.tar.gz)
3. dpkg-source -x splashy_0.3.8-2.dsc
4. cd splashy-0.3.8
5. debuild -uc -us

When done, packages will be in the previous directory (/tmp/splashy*.deb, /tmp/libsplashy*.deb)

You might also want to install gsplashy, a graphical configuration tool that was release as well:

[http://alioth.debian.org/frs/?group_id=30657](http://alioth.debian.org/frs/?group_id=30657)

---

### Post by John Jason Jordan on 2007-12-26
> **lemsx1 said:**
>  Ummm... there is extensive documentation on how to install Splashy from our wiki page:

[http://splashy.alioth.debian.org/wiki/installation](http://splashy.alioth.debian.org/wiki/installation)
Still didn't work. I used the ./configure ... command from the above page, but got basically the same errors as above.

> **lemsx1 said:**
>  Most people can simply get Splashy from the Debian repository (note that 0.3.8 was uploaded a few minutes ago and it's still in incoming.debian.org):

[http://packages.debian.org/splashy](http://packages.debian.org/splashy)
I also tried adding the debian repository listed on the wiki page, but my Synaptic (Software Sources) locked up when I tried to update. I killed it, then launched Synaptic, which seemed to be fine with the new repository. However, while Synaptic showed me 3.5 as the latest version (regular Gutsy repositories show 3.3), Synaptic also showed hundreds and hundreds of upgrades available. I like to keep my system upgraded to the latest and greatest, but only to what is in the Ubuntu repositories. Else I might end up running Debuntu Etchgutsy.

> **lemsx1 said:**
>  Ubuntu users are better off using my Gutsy packages from:

[http://splashy.alioth.debian.org/ubuntu](http://splashy.alioth.debian.org/ubuntu) 
Only i386 .deb files there. I keep having to remind everyone participating in this thread that I am on Gutsy x86_64.

> **lemsx1 said:**
>  I posted instructions on how to compile them by yourself, for Ubuntu, here:

[http://splashy.alioth.debian.org/wiki/ubuntu](http://splashy.alioth.debian.org/wiki/ubuntu) 
That page suggests the FTP site but, again, no x86_64 debs.

> **lemsx1 said:**
>  To save you some time:

0. apt-get install libdirectfb-dev  libglib2.0-dev build-essential
1. mkdir /tmp/splashy; cd /tmp/splashy
2. wget [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.diff.gz](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.diff.gz) [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.dsc](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8-2.dsc) [http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8.orig.tar.gz](http://splashy.alioth.debian.org/ubuntu/splashy_0.3.8.orig.tar.gz)
3. dpkg-source -x splashy_0.3.8-2.dsc
4. cd splashy-0.3.8
5. debuild -uc -us

When done, packages will be in the previous directory (/tmp/splashy*.deb, /tmp/libsplashy*.deb) 
Failed with a 404 on the wget line.

> **lemsx1 said:**
>  You might also want to install gsplashy, a graphical configuration tool that was release as well:

[http://alioth.debian.org/frs/?group_id=30657](http://alioth.debian.org/frs/?group_id=30657) 
I'll do that after I finally get splashy installed.

---

### Post by John Jason Jordan on 2007-12-27
> **John Jason Jordan said:**
> Failed with a 404 on the wget line. 
I finally got it installed, I think. Eventually I noticed that the wget line in lemsx1's post had ellipses in it. Using the complete URL made the wget line work. The rest of it also worked, although I had to stop several times to add more dependencies. 

However, now what I get is:

jjj@Devil7:~$ splashy test
The program 'splashy' is currently not installed.  You can install it by typing:
sudo apt-get install splashy
bash: splashy: command not found

Using the apt-get install command will install 0.3.3, because that is what is in the Ubuntu x86_64 repositories. And 0.3.3 will give me the Error 2 message mentioned previously in this thread. I never found a fix for the Error 2 message that worked, which is why I have been trying to install 0.3.8.

So now I don't get the Error 2 message, except that now it can't even find splashy, even though the make and make install seemed to go OK. I also checked to make sure the menu.lst file had the vga=791 line in it correctly, did update-grub, and also updated intramfs per the instructions previously in this thread. Rebooting I have no splash screen at all.

I know there must exist a 64-bit .deb for 0.3.5, because when I added the Debian repository that one showed up in Synaptic. I don't want to add that repository, but I'd like to try installing 0.3.5 if I could download the 64-bit .deb for it from somewhere. Anyone know where I can find it? Does anyone have any further suggestions?

---

### Post by John Jason Jordan on 2007-12-27
Omigod, I finally got it installed. For other 64-bit Ubuntu users, here is what I did:

After unsuccessfully googling looking for 64-bit .deb of 0.3.5, I did a search of my hard drive just to see what I had. I discovered that I had the following:

splashy_0.3.8-2_amd64.deb

Somehow in all my attempts at compiling from source I must have created it. (If anyone wants it, holler at me and I'll send it to you.)

So I double-clicked on it, knowing that it would launch gDebi package installer. gDebi bitched that there was an older version in the repositories and it was generally better to install the older version than an untested version. I told gDebi to shut up and install it anyway. gDebi did so without error.

Then I did "update-initramfs -u -t -k `uname -r`" (thanks smartboyathome), and tried "sudo splashy test." That still gave me the famous Error 2 message, so I rebooted. And right after the Grub menu, there was splashy!!!

Splashy wasn't terribly clean - lots of messages popping up that I didn't like seeing, but the progress bar worked fine. Now I need to go figure out how to configure it to my liking. I think I'll see if I can get gsplashy installed next.

Thanks to all for the tips and patience.

---

### Post by John Jason Jordan on 2007-12-27
> **John Jason Jordan said:**
> Splashy wasn't terribly clean - lots of messages popping up that I didn't like seeing, but the progress bar worked fine. Now I need to go figure out how to configure it to my liking. I think I'll see if I can get gsplashy installed next.
Well, installing gsplashy did not go well. The ./configure command went OK, but make did not:

```
jjj@Devil7:/tmp/gsplashy-0.1$ sudo make
[sudo] password for jjj:
make  all-recursive
make[1]: Entering directory `/tmp/gsplashy-0.1'
Making all in po
make[2]: Entering directory `/tmp/gsplashy-0.1/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/gsplashy-0.1/po'
Making all in src
make[2]: Entering directory `/tmp/gsplashy-0.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2     -Wall -g -g -O2 -MT functions.o -MD -MP -MF ".deps/functions.Tpo" -c -o functions.o functions.c; \
        then mv -f ".deps/functions.Tpo" ".deps/functions.Po"; else rm -f ".deps/functions.Tpo"; exit 1; fi
functions.c:14:24: error: splashycnf.h: No such file or directory
functions.c: In function ‘initialise_parser’:
functions.c:38: warning: implicit declaration of function ‘splashy_init_config’
functions.c:38: error: ‘SPL_CONFIG_DIR’ undeclared (first use in this function)
functions.c:38: error: (Each undeclared identifier is reported only once
functions.c:38: error: for each function it appears in.)
functions.c:38: error: expected ‘)’ before string constant
functions.c: In function ‘get_list_of_themes’:
functions.c:74: warning: implicit declaration of function ‘splashy_get_config_string’
functions.c:74: error: ‘SPL_THEMES_DIR’ undeclared (first use in this function)
functions.c:74: warning: assignment makes pointer from integer without a cast
functions.c:81: error: ‘SPL_THEME_CONFIG_FILE_NAME’ undeclared (first use in this function)
functions.c: In function ‘draw_theme_list’:
functions.c:117: error: ‘SPL_CURRENT_THEME’ undeclared (first use in this function)
functions.c:117: warning: assignment makes pointer from integer without a cast
functions.c:124: warning: implicit declaration of function ‘splashy_change_config_file’
functions.c:124: error: ‘SPL_THEMES_DIR’ undeclared (first use in this function)
functions.c:125: error: ‘SPL_THEME_CONFIG_FILE_NAME’ undeclared (first use in this function)
functions.c:126: warning: passing argument 1 of ‘g_build_filename’ makes pointer from integer without a cast
functions.c:129: warning: passing argument 1 of ‘g_basename’ makes pointer from integer without a cast
functions.c:129: warning: passing argument 1 of ‘g_build_filename’ makes pointer from integer without a cast
functions.c:139: warning: passing argument 1 of ‘g_markup_escape_text’ makes pointer from integer without a cast
functions.c:141: warning: passing argument 1 of ‘g_markup_escape_text’ makes pointer from integer without a cast
functions.c:159: warning: passing argument 1 of ‘g_build_filename’ makes pointer from integer without a cast
make[2]: *** [functions.o] Error 1
make[2]: Leaving directory `/tmp/gsplashy-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/gsplashy-0.1'
make: *** [all] Error 2
jjj@Devil7:/tmp/gsplashy-0.1$ 
```

Sadly, I don't know enough to understand what the error messages mean or how to fix them. Any suggestions?

---

### Post by smartboyathome on 2007-12-28
John Jason Jordan, I can host that package for you if you want on my server. Check your PMs for my e-mail.

EDIT: 64-bit packages now hosted on [this page]("http://smartboy.salocinlinux.org/db/Debs/").

---

### Post by lemsx1 on 2007-12-28
There is no need for that. Debian already has packages for amd64:

[http://packages.debian.org/sid/splashy](http://packages.debian.org/sid/splashy)

Here is the direct link:
[http://packages.debian.org/sid/amd64/splashy/download](http://packages.debian.org/sid/amd64/splashy/download)

To install Gsplashy you will need libsplashy1-dev. That's why you got all those errors.

In short, this is what you will need to do:

(open a terminal)
wget [http://http.us.debian.org/debian/pool/main/s/splashy/splashy_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/splashy_0.3.8-1_amd64.deb) [http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1_0.3.8-1_amd64.deb)  [http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1-dev_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1-dev_0.3.8-1_amd64.deb) 

Now, Debian Sid has a newer version of Directfb (which is a lot better), and you will need this as well:

wget [http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-1.0-0_1.0.1-5_amd64.deb](http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-1.0-0_1.0.1-5_amd64.deb)  [http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-extra_1.0.1-5_amd64.deb](http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-extra_1.0.1-5_amd64.deb) 

You might need other directfb components...

After you download all of those, you can simply do:

sudo dpkg -i *splashy*.deb *directfb*.deb

And you should be up-and-running.

If you want to be sure that you are getting all the dependencies, you might want to temporarily add "Sid" to your repositories, download splashy, and then remove it. Example:

sudo -i
echo 'deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sid main ' > /etc/apt/sources.list.d/sid.list
apt-get update
apt-get install splashy
# then remove sid.list (or keep it on /root/ for the future ;-))
mv /etc/apt/sources.list.d/sid.list /root/

In my case, I just backport the sources from Sid and compile my packages locally:

sudo -i
# notice 'deb-src'
echo 'deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sid main ' > /etc/apt/sources.list.d/sid.list
apt-get update
apt-get source -b libdirectfb-dev
apt-get source -b splashy

That will ensure that your system stays running smoothly.
If you need more help, please join #splashy on irc.freenode.net

Regards,

---

### Post by John Jason Jordan on 2007-12-28
> **lemsx1 said:**
> To install Gsplashy you will need libsplashy1-dev. That's why you got all those errors.

In short, this is what you will need to do:

(open a terminal)
wget [http://http.us.debian.org/debian/pool/main/s/splashy/splashy_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/splashy_0.3.8-1_amd64.deb) [http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1_0.3.8-1_amd64.deb)  [http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1-dev_0.3.8-1_amd64.deb](http://http.us.debian.org/debian/pool/main/s/splashy/libsplashy1-dev_0.3.8-1_amd64.deb) 

Now, Debian Sid has a newer version of Directfb (which is a lot better), and you will need this as well:

wget [http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-1.0-0_1.0.1-5_amd64.deb](http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-1.0-0_1.0.1-5_amd64.deb)  [http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-extra_1.0.1-5_amd64.deb](http://http.us.debian.org/debian/pool/main/d/directfb/libdirectfb-extra_1.0.1-5_amd64.deb) 

You might need other directfb components...

After you download all of those, you can simply do:

sudo dpkg -i *splashy*.deb *directfb*.deb 
Thanks for the additional suggestions. Unfortunately, doing the above totally hosed splashy. I had to do "sudo apt-get install -f" and then reinstall from my 64-bit .deb. And gsplashy still failed on the make command with Error 2 (same list as previously posted).

However, I fixed it just by installing libslpashy1-dev from the Ubuntu repositories (sudo apt-get install libsplashy1-dev). Thereafter the make and make install commands worked, and gsplashy is up and running.

Thanks for the assist.

---

### Post by smartboyathome on 2007-12-28
Because of your your error, John, I am leaving the package up. I will be getting a new desktop today (64 bit, at last!), so I should be able to test this in the near future.

---

### Post by John Jason Jordan on 2007-12-29
> **smartboyathome said:**
> Because of your your error, John, I am leaving the package up. I will be getting a new desktop today (64 bit, at last!), so I should be able to test this in the near future.
Yay for you! Congrats on the new desktop! As for the .deb - as long as you have the space, leaving it up can't hurt. I hope it helps people.

---

### Post by smartboyathome on 2007-12-29
> **John Jason Jordan said:**
> Yay for you! Congrats on the new desktop! As for the .deb - as long as you have the space, leaving it up can't hurt. I hope it helps people.

There is plenty of space for it. My friend and I have been running a few websites off of it and using it as each of our FTP servers, and it still isn't past 1% usage yet. :)

---

### Post by mjg59 on 2007-12-30
The reason we don't use splashy is that it requires a framebuffer, which reduces the probability of working suspend/resume. Usplash handles vesa modesetting itself, avoiding the problem. Splashy's dependency on directfb makes it difficult to implement the same functionality - I'd quite happily switch if that weren't the case.

---

### Post by amano on 2007-12-30
Well. I don't have the technical insights, but that sounds somewhat strange to me. We are talking about a bootsplash. Using a framebuffer once during bootup can prevent hibernate/resume later on during the desktop use?

Or do we talk about suspending/resuming during bootup time?

Just wondering...

On the other side this would make the decision much more understandable. Sacrificing some eye candy during bootup for saving some power functionality sounds reasonable.

Can someone share some technical details on the negative aspects of framebuffer usage?

And are there some ways to work around that?

---

### Post by mjg59 on 2007-12-30
Yes, because we have no way of returning from framebuffer mode to text mode at present.

---

### Post by smartboyathome on 2007-12-30
I thought splashy incorperated text into the splash. If so, then how would that be a problem?

---

### Post by mjg59 on 2007-12-30
It's not about being able to print text - it's about being in VGA text mode.

---

### Post by gnomeuser on 2007-12-31
> **mjg59 said:**
> The reason we don't use splashy is that it requires a framebuffer, which reduces the probability of working suspend/resume. Usplash handles vesa modesetting itself, avoiding the problem. Splashy's dependency on directfb makes it difficult to implement the same functionality - I'd quite happily switch if that weren't the case.

Correct me if I'm wrong here but once we get kernel modesetting working, all this should not be a problem?

---

### Post by mjg59 on 2007-12-31
Yes, once kernel modesetting works properly a large number of problems become easier (especially since a proper implementation of kernel modesetting implies being able to resume the video hardware without resorting to the hacks that break if you have a framebuffer)

---

### Post by sicofante on 2007-12-31
Interesting stuff. What do the Splashy devs have to say about this issue?

---

### Post by smartboyathome on 2007-12-31
> **mjg59 said:**
> Yes, once kernel modesetting works properly a large number of problems become easier (especially since a proper implementation of kernel modesetting implies being able to resume the video hardware without resorting to the hacks that break if you have a framebuffer)

Just wondering, when would this possibly become available?

---

### Post by 23meg on 2007-12-31
That was answered in mjg59's blog post that I had [linked to]("http://ubuntuforums.org/showpost.php?p=3869861&postcount=106") earlier.

---

### Post by OliW on 2008-01-02
So it looks like we've got two things.

[LIST=1]
[*]Splashy that is beautiful and makes modding your boot-up screen a joy, and makes booting a lot more interactive... With the oversight (maybe?) that it doesn't do something with the framebuffer-gizmo-majigger.
[*]USplash that is ugly as sin to try and build a splash screen for, let alone apply said damned theme  to your system... Yet it does adhere to ye olde lore of framebuffers.
[/LIST]

I realise they're different at a more fundamental level, but **is it not conceivable that you could merge** the framebuffer-handling of awesomeness +5 into splashy, as in return gain a useful tool _that your users can actually use_?!

---

### Post by mjg59 on 2008-01-02
It's conceivable, but not straightforward.

---

### Post by lemsx1 on 2008-01-02
> **OliW said:**
> So it looks like we've got two things.

[LIST=1]
[*]Splashy that is beautiful and makes modding your boot-up screen a joy, and makes booting a lot more interactive... With the oversight (maybe?) that it doesn't do something with the framebuffer-gizmo-majigger.
[*]USplash that is ugly as sin to try and build a splash screen for, let alone apply said damned theme  to your system... Yet it does adhere to ye olde lore of framebuffers.
[/LIST]

I realise they're different at a more fundamental level, but **is it not conceivable that you could merge** the framebuffer-handling of awesomeness +5 into splashy, as in return gain a useful tool _that your users can actually use_?!

I could not have put it any better. That was exactly what I was planning to do. They are both GPL apps after all...

On the other hand, I do remember reading something from Linus about suspend being broken and people should just use hibernate. (thought I might be wrong). I don't recall the last computer I had (not being a Mac) that correctly suspend (i.e. went to sleep mode) without it crashing badly. No matter the OS (windows too. I used to work at CompUSA in the tech dept fixing PCs)

Oh well, I'll look into the source and patch Splashy to do what's needed. And if changes are needed to directfb itself, then I'll just submit the patches upstream. (If anybody wants to help and make things simpler, just send me the patches and I'll commit it in Splashy's source. #splashy on irc.freenode.net for those who don't know)

---

### Post by sicofante on 2008-01-03
That sounds great lemsx1. Please let us know how we can help other than programming.

---

### Post by red_team316 on 2008-01-13
[quote=OliW]
USplash that is ugly as sin to try and build a splash screen for, let alone apply said damned theme to your system... Yet it does adhere to ye olde lore of framebuffers.
[/quote]
TheeMahn has made some nice progress on a Usplash Maker. It as it's not perfect and will be developed some more, but anyone who can properly palette the required images should have no problem.
[Usplash Maker](http://forumubuntusoftware.info/viewtopic.php?f=23&t=60)

I'm all for a better bootsplash and all this forking is just crazy. I infact prefer Usplash over Splashy currently because splashy cannot make custom progressbar animations like usplash can. I noticed splashy 0.4.0 is supposed to address this. Imo this functionality is the real meat and potatoes of an awesome bootsplash.

Hopefully sometime in the future, the usplash and splashy devs can reunite to make something that is truely user friendly.

---

### Post by cb951303 on 2008-01-14
splashy is definitly my choice. it has >256 colors + transparency and it doesn't need a kernel patch (user-space). I'm actually suprised to see dev members being fanatic about usplash. I'm sure they made a lot of effort and usplash is a great piece of software but splashy seems better now, there is no shame in accepting that. After all that's what open-source  is all about ;)

---

### Post by 23meg on 2008-01-14
Did you *read* the posts about Splashy breaking suspend?

---

### Post by cb951303 on 2008-01-14
> **23meg said:**
> Did you *read* the posts about Splashy breaking suspend?

well 18 page is hard to read :) I've stated my thoughts based on **my** experiance with splashy. But I agree it's a nasty bug. In the other hand, suspend doesn't work half of the time anyway. By the time hardware providers give better suspend/hibernate for linux I'm sure splashy team would do something about it :lolflag:

---

### Post by smartboyathome on 2008-01-14
> **cb951303 said:**
> well 18 page is hard to read :) I've stated my thoughts based on **my** experiance with splashy. But I agree it's a nasty bug. In the other hand, suspend doesn't work half of the time anyway. By the time hardware providers give better suspend/hibernate for linux I'm sure splashy team would do something about it :lolflag:

I thought they already were by trying to create modesetting for it...

---

### Post by 23meg on 2008-01-14
*sigh*

I see.

---

### Post by mjg59 on 2008-01-14
> **cb951303 said:**
> well 18 page is hard to read :) I've stated my thoughts based on **my** experiance with splashy. But I agree it's a nasty bug. In the other hand, suspend doesn't work half of the time anyway. By the time hardware providers give better suspend/hibernate for linux I'm sure splashy team would do something about it :lolflag:

That doesn't mean that we break suspend even more by pushing out a replacement bootsplash application that interacts badly with it. While splashy requires a framebuffer (and until the kernel provides native modesetting for all the hardware we care about), splashy will not be part of the default install. This isn't a criticism of splashy - it just doesn't meet our needs, in much the same way that saying I need a car that can fit in a small parking space doesn't mean that I'm criticising Hummers.

---

### Post by sicofante on 2008-01-15
> **23meg said:**
> Did you *read* the posts about Splashy breaking suspend?

> **smartboyathome said:**
> I thought they already were by trying to create modesetting for it...

> **mjg59 said:**
> That doesn't mean that we break suspend even more by pushing out a replacement bootsplash application that interacts badly with it.

Did *you* read this post? > **lemsx1 said:**
> ... I'm truly amazed by the lack of support this guy is receiving by official Ubuntu members. It's like they're so proud of Usplash while it's pretty obvious for everyone else (check the poll in this very thread) that Splashy should be pushed and use the computing force behind Usplash to fix that single suspend issue. But no, we'll put more efforts in the wrong thing only because *it was invented here*... (NIH again)

Jeez!

---

### Post by mjg59 on 2008-01-15
> **sicofante said:**
> Did *you* read this post?  I'm truly amazed by the lack of support this guy is receiving by official Ubuntu members. It's like they're so proud of Usplash while it's pretty obvious for everyone else (check the poll in this very thread) that Splashy should be pushed and use the computing force behind Usplash to fix that single suspend issue. But no, we'll put more efforts in the wrong thing only because *it was invented here*... (NIH again)

Jeez!

No. We'll use usplash because it's written and works. I haven't put any development into it for some time because it's adequate (though not exceptional) at what it does, and I'm busy working on other things. If Splashy loses the framebuffer dependency, then great - but it's not worth me working on it when I can be fixing other things instead. I would actually be thrilled to have Splashy gain this support (it would mean I could stop caring about Usplash), but right now the amount of work I'd have to do to implement it myself is more than I want to spend on a bootsplash.

---

### Post by 23meg on 2008-01-15
[QUOTE=sicofante]Did *you* read this post?[/QUOTE]

Yes, I read all posts, and I don't see anyone advocating blindly sticking with Usplash forever no matter what. I see people citing factual reasons, providing technical arguments and and engaging in a mostly healthy discussion, which it seems can lead to a merge of the two projects, or Splashy being favoured. The upstream developer has said that they'll work on Splashy so that it will no longer break suspend, which is great. If that actually happens, it seems it can be included.

That's my interpretation of what I've read. If your interpretation is that a few people are so proud of Usplash that they'll blindly argue against any alternative regardless of the technical facts, the problem is on your side.

---

### Post by mjg59 on 2008-01-15
On the other hand, if anyone's looking at this, then the right place to start is in directfb. You'll want to add a new system (in the systems directory) that uses svgalib. Grab the svgalib from usplash rather than using your own - it's been fixed up so it integrates correctly with libx86. You'll need to implement ScreenFuncs and DisplayLayerFuncs, and then figure out a way of building a directfb that'll switch between different systems depending on whether there's a framebuffer available or not (this has to be a runtime rather than build-time thing, otherwise everything will break depending on whether the user has a framebuffer configured or not). It's probably only a few hours of work for someone who knows what they're doing.

---

### Post by sicofante on 2008-01-15
I see. We, the voters above (who's needs are not met), love your stance.

:(

Go **lemsx1!!!!**

---

### Post by 23meg on 2008-01-15
> **sicofante said:**
> I see. We, the voters above (who's needs are not met), love your stance.

:(

Go **lemsx1!!!!**

Speak in your own name, and stop trying to make this look like a fight, with Splashy developers and a group of vocal users on one side and Ubuntu members and developers on the other side. That's simply not the situation, as you can see in mjg59's posts as well.

---

### Post by mjg59 on 2008-01-15
> **sicofante said:**
> I see. We, the voters above (who's needs are not met), love your stance.

:(

Go **lemsx1!!!!**

Then help contribute to improving Splashy to the point where it's acceptable. It's clearly better than Usplash in almost every way - there's just a single fundamental issue that means we can't use it, and it's not a sufficiently important issue that I'm going to prioritise it above fixing kernel issues, suspend support or my ongoing mobile edition work.

---

### Post by sicofante on 2008-01-15
As usual 23meg: Stop lecturing people.  If you have an interpretation and I have another, the problem might be on either side. Some humility is a good advice, especially if you are an Ubuntu member.

@mj59: you made it sound like you were part of the development of Usplash, that it would take just a few hours to fix Splashy and that you wouldn't spend any time on it. In other words, that you don't care. When it's so obvious for anyone who has read the full thread that Splashy is so much better than Usplash, it's just surprising, to say the least, that you choose to ignore it and devote any efforts to other areas.

Before telling anyone to help with a thing like this, it would be wise to ask if that one is a developer. (I'm not.)

Again:  Go [B]lemsx1!!!!
[/B]

---

### Post by mjg59 on 2008-01-15
> **sicofante said:**
> 
@mj59: you made it sound like you were part of the development of Usplash, that it would take just a few hours to fix Splashy and that you wouldn't spend any time on it. In other words, that you don't care. When it's so obvious for anyone who has read the full thread that Splashy is so much better than Usplash, it's just surprising, to say the least, that you choose to ignore it and devote any efforts to other areas.

Before telling anyone to help with a thing like this, it would be wise to ask if that one is a developer. (I'm not.)


Yes, I wrote Usplash in a few hours (most of which was in a departure lounge in Helsinki airport) back in 2005. Since then it's had bugfixes and a small number of additional features added. At the time, Splashy wasn't useful for different reasons (lack of support for vga16fb) and the amount of work to add that support would actually have been significantly greater than just writing usplash (especially since, at the time, splashy had very few features). Now that vga16fb isn't an issue, and now that splashy has many more features, if I had the time to work on it then I'd modify Splashy rather than writing Usplash. But I don't. That doesn't mean I don't care - it just means that there are other things I care about more. 

The primary purpose of a bootsplash is to indicate to the user that the system is booting, ideally in a reasonably graphically pleasing manner. Themability is much less of a concern. The Usplash theme support is designed to allow different themes for different Ubuntu derivatives, and from that point of view it works fine - it's poor at allowing users to design their own splashes, and that's somewhere below "Let people use their laptops properly" as far as I'm concerned. If other people feel differently, they're free to spend their time on it.

(It's not like I'm spending time on Usplash that could be spent on Splashy. I haven't touched Usplash in over a year, and the changes there are changes to the svgalib code that Splashy will need to use if it's going to be the default. If I had 20 hours to spend on Usplash, I'd probably spend them on porting directfb to use svgalib instead. But I don't, so I won't)

---

### Post by sicofante on 2008-01-15
Thanks for explaining. I understand your point.

---

### Post by 23meg on 2008-01-15
[QUOTE=sicofante]As usual 23meg: Stop lecturing people. If you have an interpretation and I have another, the problem might be on either side. Some humility is a good advice, especially if you are an Ubuntu member.[/QUOTE]

Sorry for the "lecture", but I insist (and originally meant) that your interpretation is factually problematic, in that there's simply no proof that you can cite in favor of it. If you'd like to argue that it's not, you're welcome to do so.

---

### Post by John Jason Jordan on 2008-01-15
I have been using Splashy now for some time on my Gutsy x86_64 Thinkpad because none of the many fixes for Usplash can get it working. I am satisfied with Splashy but I have no axes to grind and I know nothing of programming. I just want a splash screen that works.

Today, however, Splashy let me down. I was at the university trying to boot and Splashy hung at about 15%. After a long wait I was dumped to a text screen. I waited a bit and it appeared hung so I rebooted. The same thing happened. But then I noticed that the hard drive light was running constantly. "Aha," I thought. "I know what happened - I've been bit by the famous 30-boots forced fsck thing and Splashy timed out waiting for it to finish. I sat and let it work and eventually the computer booted normally, albeit without Splashy.

I just thought I'd mention that Splashy's timeout is not long enough for the forced fsck.

---

### Post by lemsx1 on 2008-01-16
ideally Splashy should be told by whatever runs fsck to increase its timeout. or splashy itself should somehow know when a process like fsck is running and alert the user somehow.

we (splashy developers) will probably do the latter. however, at this moment, we are working on bug fixes and getting the initramfs stuff ironed out and working for all major distros.

as more and more developers from different distributions of Linux continue to use splashy, it will stabilize the code to the point that the transition from usplash to splashy will happen in a natural way.

---

### Post by John Jason Jordan on 2008-01-16
> **lemsx1 said:**
> ideally Splashy should be told by whatever runs fsck to increase its timeout. or splashy itself should somehow know when a process like fsck is running and alert the user somehow.

we (splashy developers) will probably do the latter. however, at this moment, we are working on bug fixes and getting the initramfs stuff ironed out and working for all major distros.

as more and more developers from different distributions of Linux continue to use splashy, it will stabilize the code to the point that the transition from usplash to splashy will happen in a natural way.
Thanks for the reply. It is not an important issue, now that I realize what is happening. I just wanted to document it on the net somewhere so if it happens to someone else a google search will turn up this thread and they can rest easy.

As for fixing it, I'm sure y'all will get to it now that you developers are aware of the issue. All in good time. I certainly understand that you have more important fish to fry.

---

### Post by theemahn on 2008-01-22
> **red_team316 said:**
> TheeMahn has made some nice progress on a Usplash Maker. It as it's not perfect and will be developed some more, but anyone who can properly palette the required images should have no problem.
[Usplash Maker](http://forumubuntusoftware.info/viewtopic.php?f=23&t=60)

I'm all for a better bootsplash and all this forking is just crazy. I infact prefer Usplash over Splashy currently because splashy cannot make custom progressbar animations like usplash can. I noticed splashy 0.4.0 is supposed to address this. Imo this functionality is the real meat and potatoes of an awesome bootsplash.

Hopefully sometime in the future, the usplash and splashy devs can reunite to make something that is truely user friendly.

Thanks red_team for bring my software to attention.  I am sorry I am so hard to get a hold of (I got your email along with probably 500 others), I have not had time to dabble anymore with the Usplash Maker, I am sure it is a simple solution the usplash progressbar I make for Ultimate Edition will be done by hand until I have time to address this issue.  You are a good man and I do enjoy your blog when you take the time to update it hint hint ;)  Try updating 6 websites ;)  I have a few days coming off from work for my birthday which I took unpaid vacation to get, After I get 1.7 up & going I will look into the USplash maker.

Thanks again,

TheeMahn

---

### Post by ilovenicotine on 2008-02-18
+1

Ubuntu can be customized 100 times more and 100 times easier than Windows or Mac OS X.  Switching to Splashy would make customizing the boot splash way easier and way more powerful for everyone.

---

### Post by smartboyathome on 2008-02-28
Just to let you all know, I made an idea for splashy on Ubuntu's brainstorm site [here]("http://brainstorm.ubuntu.com/idea/269/").

---

### Post by elamericano on 2008-03-28
+1 for Splashy

I was shocked that I still couldn't invoke verbose mode during boot, and I'm sad to hear that there hasn't been any work on it. Breezy's Ubuntu graphic with scrolling text below it was a better solution than graphic + progress bar only. I do not see OpenSUSE and Fedora with this same limitation. Do those distros not suspend? Yes they do?

This discussion does not make sense.

Here's hoping we don't go another three Ubuntu releases without a verbose option.

---

### Post by moore.bryan on 2008-03-29
hopefully someone can help me... no matter which "trick" i use, i can't get splashy to start in heron. all i ever get is the ```
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```

---

### Post by Twitch6000 on 2008-03-29
> **cjwatson said:**
> usplash has all the same properties that you cite for splashy here. I think we've put enough work into usplash that replacing it with something else now would be busy-work ...

I agree

---

### Post by smartboyathome on 2008-03-29
> **moore.bryan said:**
> hopefully someone can help me... no matter which "trick" i use, i can't get splashy to start in heron. all i ever get is the ```
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```

Try asking on Splashy's irc channel on freenode.net.

> **Twitch6000 said:**
> I agree

Though it isn't the same level anymore, Splashy is way easier to make themes for and a GUI for making themes is being made now. Also, 0.4 should have custom progress bars and modsetting (which is why ubuntu really doesn't accept it).

---

### Post by moore.bryan on 2008-03-29
> **smartboyathome said:**
> Try asking on Splashy's irc channel on freenode.net.
tried that one, no one was taking the bait... even tried the ubuntu irc. is there a decent webpage to start troubleshooting i may have missed? i've changed all the /etc/rcS.d things as suggested by the dozen-or-so forum suggestions i've already found, but beyond that i'm at wit's-end.

---

### Post by smartboyathome on 2008-03-30
The only other thing I can think of is to check splashy's site, especially [the faq]("http://splashy.alioth.debian.org/wiki/faq").

---

### Post by moore.bryan on 2008-03-30
> **smartboyathome said:**
> The only other thing I can think of is to check splashy's site, especially [the faq]("http://splashy.alioth.debian.org/wiki/faq").
yeah, tried there; no dice. alas, i think i may need to live without prettiness.
:-)

---

### Post by altonbr on 2008-05-05
How is splashy looking for 8.10 (Intrepid Ibex)?

I'm really sick of not having a splash screen on my widescreen monitor.

---

### Post by mjg59 on 2008-05-05
Ubuntu can switch to Splashy in two cases:

(1) Splashy no longer requires a framebuffer, or
(2) We have stable framebuffer drivers which support suspend/resume for every major graphics card manufacturer

Neither of those looks likely for 8.10.

---

### Post by smartboyathome on 2008-05-05
How does OpenSuSE get around this? And what about fedora? As far as I know, they both use Splashy.

---

### Post by mjg59 on 2008-05-05
Fedora uses RHGB, which is an X-based solution and so doesn't need a framebuffer. OpenSuse uses bootsplash, which requires a framebuffer and results in worse suspend/resume support.

---

### Post by TheForkOfJustice on 2008-05-05
I'm making my own distro out of Ubuntu and I have to mention that getting my custom usplash to work has been the most troublesome part. I'm not even certain 

I say if splashy is simpler than usplash then make the change.  I think I'll give it a try to see how it works.  I may change from usplash to splashy if I like it more.

EDIT 

I've tested it out.  My thoughts:

usplash = quickly appears, low resolution, better/more accurate throbber
splashy = takes longer to appear, high resolution, throbber cuts out early.

The fact that splashy's high res images needs more resources to work likely explains its appearing speed and throbber behaviour.

If we could get usplash to look as well as splashy without losing speed we'd be set.

---

### Post by sicofante on 2008-05-06
> **mjg59 said:**
> Fedora uses RHGB, which is an X-based solution and so doesn't need a framebuffer. OpenSuse uses bootsplash, which requires a framebuffer and results in worse suspend/resume support.
Just for non-programmers to understand this, could you elaborate on how a bootsplash software affects resume/suspend support once the OS has booted, you have logged in and usplash/splashy isn't working any more?

---

### Post by mjg59 on 2008-05-06
splashy can't do mode setup itself, so requires you to be using vesafb. When you resume your system, the kernel will attempt to write to the framebuffer at various points. At this point, your graphics haven't been reinitialised and the system may behave in unpredictable ways - including hanging. In VGA text mode, this isn't a problem as the writing is all port i/o based rather than memory mapped, and in the worst case the card simply doesn't respond. Usplash restores VGA text mode after it's finished booting, whereas splashy doesn't (and can't in any straightforward way)

---

### Post by sicofante on 2008-05-06
Still too technical to me, sorry. Wouldn't it be reasonable to have graphics "initialised" at one point and never go back until shutdown? How does Windows solve this?

---

### Post by mjg59 on 2008-05-06
It would, yes. But in order to allow that to happen, we need in-kernel graphics drivers that know how to program your graphics card into the correct mode. We currently don't have those.

---

### Post by smartboyathome on 2008-05-06
> **TheForkOfJustice said:**
> I'm making my own distro out of Ubuntu and I have to mention that getting my custom usplash to work has been the most troublesome part. I'm not even certain 

I say if splashy is simpler than usplash then make the change.  I think I'll give it a try to see how it works.  I may change from usplash to splashy if I like it more.

EDIT 

I've tested it out.  My thoughts:

usplash = quickly appears, low resolution, better/more accurate throbber
splashy = takes longer to appear, high resolution, throbber cuts out early.

The fact that splashy's high res images needs more resources to work likely explains its appearing speed and throbber behaviour.

If we could get usplash to look as well as splashy without losing speed we'd be set.

We wouldn't be set. It is almost murderous for me to try to make a usplash theme. I can make a splashy theme WAY betterm and it doesn't take as many resources as this post leads to believe. With Splashy 0.4, they will have a new throbber which can be customized and modesetting, so it might be ready for 9.04 at the earliest. :(

---

### Post by BlueSkyNIS on 2008-05-06
> **altonbr said:**
> How is splashy looking for 8.10 (Intrepid Ibex)?

I'm really sick of not having a splash screen on my widescreen monitor.

I don't know why you don't have a splash screen, but I think the problem isn't in your widescreen monitor, but the problem is in your graphics card.


Cheers

---

### Post by Josh04 on 2008-05-06
Splashy in Hardy is considerably poorer than splashy in Gutsy. Anyone else noticed this?

---

### Post by smartboyathome on 2008-05-06
> **Josh04 said:**
> Splashy in Hardy is considerably poorer than splashy in Gutsy. Anyone else noticed this?

What do you mean by "poorer"? It works fine for me.

---

### Post by Josh04 on 2008-05-07
It doesn't appear with hibernate and resume like it did, and is tempermental on shutdown. Maybe it's just mine.

---

### Post by sicofante on 2008-05-07
> **mjg59 said:**
> It would, yes. But in order to allow that to happen, we need in-kernel graphics drivers that know how to program your graphics card into the correct mode. We currently don't have those.
Now I get it, thanks!

Just to go a bit further: what if we knew the graphics card was ALWAYS an Nvidia card, for instance. Would it be possible then?

I'm asking this because I build workstations for 3D and animation and nobody uses anything but Nvidia cards in that industry, so a special solution would make sense to me and I might hire someone to do it.

Or is there already any solution for specific drivers like Nvidia's?

Or is there no way to put those drivers into the kernel no matter how specific I am about the graphics card?

---

### Post by mjg59 on 2008-05-07
> **sicofante said:**
> Just to go a bit further: what if we knew the graphics card was ALWAYS an Nvidia card, for instance. Would it be possible then?

At the moment, no. There's no reliable framebuffer driver for any recent nvidia cards. People are working on this, but it's not going to be ready for a while yet.

---

### Post by webceo on 2008-05-08
Splashy wouldn't work for me, it doesn't start and it says "connection refused"

I voted for Splashy, but I'm sticking with usplash until a stable release is out

---

### Post by smartboyathome on 2008-05-08
Did you add the vga=791 line to your grub menu.lst? That should do it for you.

---

### Post by webceo on 2008-05-08
Yes that actually fixed the issue for me. Thank you

Now I'll probably spend the next couple hours looking for splashy themes or even creating one :D

---

### Post by webceo on 2008-05-08
Ok now I'm facing another issue.

No matter what theme I set in the config.xml file, it works in the shutdown splash, but the start up splash is always the default theme. 

I even tried renaming the theme I want to use to "default", but it didn't work.

Maybe the location of the default theme is hard coded into splashy.

Anyone knows a fix for this ?

---

### Post by smartboyathome on 2008-05-08
Run update-initramfs -u -t -k `uname -r` after you change the theme. It will refresh everything.

---

### Post by webceo on 2008-05-08
Yes, that did it. Thank you

---

### Post by brandon30x on 2008-05-09
I'm not a programmer, but will the up-comming kernel based mode setting patches help with Splashy and suspend?

[http://linux.slashdot.org/article.pl?sid=08/04/19/2314219]("http://linux.slashdot.org/article.pl?sid=08/04/19/2314219")
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1]("http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1")

Seamless boot from splash to X with no flickering or resolution changes sounds awesome! :guitar:
And better suspend resume as stated from the article.
-Brandon

---

### Post by altonbr on 2008-05-09
> **brandon30x said:**
> I'm not a programmer, but will the up-comming kernel based mode setting patches help with Splashy and suspend?

[http://linux.slashdot.org/article.pl?sid=08/04/19/2314219]("http://linux.slashdot.org/article.pl?sid=08/04/19/2314219")
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1]("http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1")

Seamless boot from splash to X with no flickering or resolution changes sounds awesome! :guitar:
And better suspend resume as stated from the article.
-Brandon

I don't know, but thank you for the links!

---

### Post by smartboyathome on 2008-05-09
> **brandon30x said:**
> I'm not a programmer, but will the up-comming kernel based mode setting patches help with Splashy and suspend?

[http://linux.slashdot.org/article.pl?sid=08/04/19/2314219]("http://linux.slashdot.org/article.pl?sid=08/04/19/2314219")
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1]("http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1")

Seamless boot from splash to X with no flickering or resolution changes sounds awesome! :guitar:
And better suspend resume as stated from the article.
-Brandon

Thanks for the links! This is EXACTLY what Ubuntu needed to get splashy in! It will help splashy, because that is its biggest bug (modesetting). It will be able to change to X for splashy after a suspend or resume (from what I understand).

---

### Post by webceo on 2008-05-09
Thanks for the links.

I hope this will be available for Intrepid Ibex, though I highly doubt it.

---

### Post by sicofante on 2008-05-09
If it'll be ready for Fedora next month, why wouldn't it be for Intrepid Ibex six months from now?

---

### Post by smartboyathome on 2008-05-10
> **sicofante said:**
> If it'll be ready for Fedora next month, why wouldn't it be for Intrepid Ibex six months from now?

Because it won't be "officially" supported until the 2.6.27 kernel, and they don't like applying 3rd party patches.

---

### Post by angry_johnnie on 2008-05-10
I rather like usplash... and I already got a [script]("http://forumubuntusoftware.info/viewtopic.php?f=23&t=60") from the people at UUE to automate the process of creating one (although Hardy doesn't like it very much).  I wouldn't know what to do with splashy.

---

### Post by sicofante on 2008-05-10
> **smartboyathome said:**
> Because it won't be "officially" supported until the 2.6.27 kernel, and they don't like applying 3rd party patches.
And that kernel version is due when?

---

### Post by webceo on 2008-05-10
I believe it's due late autumn. Chances are that would be way past the kernel freeze date for Intrepid Ibex.

---

### Post by sicofante on 2008-05-10
Do you have any links? I can't find any info about the 2.6.27 kernel, but the timing of previous versions suggests it should be here much earlier than late autumn.

---

### Post by smartboyathome on 2008-05-10
I couldn't find any links either, but I think it should be here before late Autumn.

> **angry_johnnie said:**
> I rather like usplash... and I already got a [script]("http://forumubuntusoftware.info/viewtopic.php?f=23&t=60") from the people at UUE to automate the process of creating one (although Hardy doesn't like it very much).  I wouldn't know what to do with splashy.

Just type splashy_config -c and it will ask you a few questions about which pictures you want to use, and where you want the scroll bar to be (in percent). I find it very easy, and it doesn't make the picture look horrible like Usplash (which only uses 256 colors).

---

### Post by webceo on 2008-05-10
The linux kernel has been released lately every 3 months (more or less).
Kernel 2.6.26 will be released (hopefully) early july according to the linux foundation

[http://www.linux-foundation.org/en/Linux_Weather_Forecast](http://www.linux-foundation.org/en/Linux_Weather_Forecast)

Do the math... Kernel 2.6.27 should be released by mid October

---

### Post by smartboyathome on 2008-05-10
> **webceo said:**
> The linux kernel has been released lately every 3 months (more or less).
Kernel 2.6.26 will be released (hopefully) early july according to the linux foundation

[http://www.linux-foundation.org/en/Linux_Weather_Forecast](http://www.linux-foundation.org/en/Linux_Weather_Forecast)

Do the math... Kernel 2.6.27 should be released by mid October

If it is released in october, it would be too late for Intrepid, but they could at least upload it to the repos for people to use and test. :)

---

### Post by sicofante on 2008-05-10
> **webceo said:**
> The linux kernel has been released lately every 3 months (more or less).
Kernel 2.6.26 will be released (hopefully) early july according to the linux foundation

[http://www.linux-foundation.org/en/Linux_Weather_Forecast](http://www.linux-foundation.org/en/Linux_Weather_Forecast)

Do the math... Kernel 2.6.27 should be released by mid October
Sorry, you're right. I made a mistake and thought we were already at 2.6.26.

---

### Post by webceo on 2008-05-11
There is nothing to be sorry about mate. We are here to share information :)

---

### Post by 23meg on 2008-05-11
Modesetting support in the kernel wouldn't be enough by itself; drivers also need to support it. And while Intel users will, as usual, reap the benefits first, we know that especially proprietary driver vendors aren't very quick in adopting such changes, and can argue against supporting them altogether. Remember NVIDIA's dislike of XRandR.

---

### Post by smartboyathome on 2008-05-11
> **23meg said:**
> Modesetting support in the kernel wouldn't be enough by itself; drivers also need to support it. And while Intel users will, as usual, reap the benefits first, we know that especially proprietary driver vendors aren't very quick in adopting such changes, and can argue against supporting them altogether. Remember NVIDIA's dislike of XRandR.

Right. I guess my desktop won't get this then. :( My laptop will though. :D

---

### Post by kwilliam on 2008-06-09
> **stoffe said:**
> IMO that makes Splashy a non-option until it behaves at least as well as Usplash. But since Usplash manages to behave (although via hackish methods) the Splashy devs could do the same and then ask again.

Hah! I vote Splashy. USplash stopped working when I upgraded from Gutsy to Hardy. Just installed Splashy and it looks amazing - far higher resolution and way more colors than the default Kubuntu USplash had. Suspend has always been iffy on my laptop, and was destroyed completely during the upgrade; I think it's the proprietary NVidia driver. (Idiots, why don't they release the source!?)

But now that I've laughed at "Usplash manages to behave", I agree with you. Except I think the Ubuntu devs should work with the Splashy devs to get their suspend hack into the Splashy code. Having read about both projects, I prefer Splashy's XML theme format to USplash's theme format that requires compiling with gcc! That just seems messed up.

---

### Post by altonbr on 2008-06-09
> **kwilliam said:**
> Hah! I vote Splashy. USplash stopped working when I upgraded from Gutsy to Hardy. Just installed Splashy and it looks amazing - far higher resolution and way more colors than the default Kubuntu USplash had. Suspend has always been iffy on my laptop, and was destroyed completely during the upgrade; I think it's the proprietary NVidia driver. (Idiots, why don't they release the source!?)

But now that I've laughed at "Usplash manages to behave", I agree with you. Except I think the Ubuntu devs should work with the Splashy devs to get their suspend hack into the Splashy code. Having read about both projects, I prefer Splashy's XML theme format to USplash's theme format that requires compiling with gcc! That just seems messed up.

Really? splashy doesn't work for me out-of-the-box in Hardy.

---

### Post by smartboyathome on 2008-06-09
Did you add "vga=791 splash" to the end of your grub line? Because that is the most common reason I have seen why it doesn't work, and that would be added automatically anyway if it becomes default.

---

### Post by altonbr on 2008-06-09
> **smartboyathome said:**
> Did you add "vga=791 splash" to the end of your grub line? Because that is the most common reason I have seen why it doesn't work, and that would be added automatically anyway if it becomes default.

No, it doesn't even install. I'll show you the error next time I'm home.

---

### Post by smartboyathome on 2008-06-09
Ok, that could help filter out bugs.

---

### Post by lemsx1 on 2008-06-10
> **altonbr said:**
> Really? splashy doesn't work for me out-of-the-box in Hardy.

Are you using Splashy 0.3.10? I develop Splashy on Hardy. And in fact, for the next 3 years or so (the life of Hardy), we will always support Hardy ;-)

Just make sure that you are using libdirectfb 1.0.1-7ubuntu3 (and up) and upstart. People using the old init stuff will have problems unless they use libdirectfb 1.0.1-9 (Debian Sid and will be in Lenny). This is because of patches we submitted upstream to fix keyboard event thread looping when the /dev special devices changed from initramfs to the real root tree.

Splashy 0.3.10 is rock solid.

[http://splashy.alioth.debian.org/wiki](http://splashy.alioth.debian.org/wiki)

---

### Post by altonbr on 2008-06-10
> **lemsx1 said:**
> Are you using Splashy 0.3.10? I develop Splashy on Hardy. And in fact, for the next 3 years or so (the life of Hardy), we will always support Hardy ;-)

Just make sure that you are using libdirectfb 1.0.1-7ubuntu3 (and up) and upstart. People using the old init stuff will have problems unless they use libdirectfb 1.0.1-9 (Debian Sid and will be in Lenny). This is because of patches we submitted upstream to fix keyboard event thread looping when the /dev special devices changed from initramfs to the real root tree.

Splashy 0.3.10 is rock solid.

[http://splashy.alioth.debian.org/wiki](http://splashy.alioth.debian.org/wiki)

It seemed to install fine, let me test rebooting.

> $ sudo aptitude install splashy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  gobuntu-artwork-usplash ubuntu-desktop usplash-theme-ubuntu 
  usplash-theme-ubuntustudio 
The following NEW packages will be automatically installed:
  libdirectfb-extra libsplashy1 
The following packages will be automatically REMOVED:
  usplash 
The following NEW packages will be installed:
  libdirectfb-extra libsplashy1 splashy 
The following packages will be REMOVED:
  usplash 
0 packages upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 1227kB of archives. After unpacking 1819kB will be used.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: usplash but it is not installable
  gobuntu-artwork-usplash: Depends: usplash (>= 0.4-21) but it is not installable
  usplash-theme-ubuntu: Depends: usplash (>= 0.4-21) but it is not installable
  usplash-theme-ubuntustudio: Depends: usplash (>= 0.4-21) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gobuntu-artwork-usplash
ubuntu-desktop
usplash-theme-ubuntu
usplash-theme-ubuntustudio

Score is 326

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libdirectfb-extra libsplashy1 
The following packages will be automatically REMOVED:
  gobuntu-artwork-usplash ubuntu-desktop usplash usplash-theme-ubuntu 
  usplash-theme-ubuntustudio 
The following NEW packages will be installed:
  libdirectfb-extra libsplashy1 splashy 
The following packages will be REMOVED:
  gobuntu-artwork-usplash ubuntu-desktop usplash usplash-theme-ubuntu 
  usplash-theme-ubuntustudio 
0 packages upgraded, 3 newly installed, 5 to remove and 0 not upgraded.
Need to get 1227kB of archives. After unpacking 6504kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libdirectfb-extra 1.0.1-7ubuntu3 [29.6kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libsplashy1 0.3.8-1 [27.3kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe splashy 0.3.8-1 [1170kB]
Fetched 1227kB in 3s (389kB/s)    
(Reading database ... 154780 files and directories currently installed.)
Removing gobuntu-artwork-usplash ...
update-initramfs: deferring update (trigger activated)
Removing ubuntu-desktop ...
Removing usplash-theme-ubuntustudio ...
update-initramfs: deferring update (trigger activated)
Removing usplash-theme-ubuntu ...
update-initramfs: deferring update (trigger activated)
Removing usplash ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Selecting previously deselected package libdirectfb-extra.
(Reading database ... 154751 files and directories currently installed.)
Unpacking libdirectfb-extra (from .../libdirectfb-extra_1.0.1-7ubuntu3_i386.deb) ...
Selecting previously deselected package libsplashy1.
Unpacking libsplashy1 (from .../libsplashy1_0.3.8-1_i386.deb) ...
Selecting previously deselected package splashy.
Unpacking splashy (from .../splashy_0.3.8-1_i386.deb) ...
Setting up libdirectfb-extra (1.0.1-7ubuntu3) ...
Setting up libsplashy1 (0.3.8-1) ...

Setting up splashy (0.3.8-1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done   

---

### Post by altonbr on 2008-06-10
Yup, this is the same error I had last time (I wrote it down quickly, sorry):
> Splashy ERROR: Connection Refused
Splashy ERROR: splashy_start_splashy()
> $ apt-cache policy splashy && lsb_release -c
splashy:
  Installed: 0.3.8-1
  Candidate: 0.3.8-1
  Version table:
 *** 0.3.8-1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status
Codename:	hardy

---

### Post by smartboyathome on 2008-06-10
You need to add vga=791 splash to the end of your kernel lines in grub. That is why you get that error.

---

### Post by altonbr on 2008-06-10
> **smartboyathome said:**
> You need to add vga=791 splash to the end of your kernel lines in grub. That is why you get that error.

Why doesn't splashy do that automatically?

---

### Post by smartboyathome on 2008-06-10
> **altonbr said:**
> Why doesn't splashy do that automatically?

Because debian packages can't modify system files like that one (security measure).

---

### Post by altonbr on 2008-06-10
> **smartboyathome said:**
> Because debian packages can't modify system files like that one (security measure).

So only when Ubuntu switches to splashy, only then they can support it? Seems sort of silly, but from a security standpoint it makes sense.

---

### Post by smartboyathome on 2008-06-10
> **altonbr said:**
> So only when Ubuntu switches to splashy, only then they can support it? Seems sort of silly, but from a security standpoint it makes sense.

Yeah, but it is better this way imo, if files could modify stuff like the menu.lst, they could wipe it or fill it with gibberish, which would be bad. :(

---

### Post by Inteluxe on 2008-10-03
HI, I am using Ubuntu hardy with Splashy 0.3.8-1 (even i upgraded later with splashy 0.3.10 debian package) and i have this prob. Splashy gets this error: "Splashy ERROR: Timeout (120 sec) occurred while waiting for a message on the Splashy socket"

I recieve this beacuse i have to run a service during boot up sequence of a dd copy that takes 3 mins. but after 120secs splashy image disappears and this error message comes out. i have googled this error, but the "possibles fixes" i have found are not correct (like block keymap service, upgrade to newer splashy).

I wonder if we can bypass this 120 timeout or any other fix you guys know.

thanks

---

### Post by smartboyathome on 2008-10-03
I haven't experienced this error, but to be honest I haven't used Splashy on Ubuntu in a while (I use splashy on Arch, which is a little different I think).

---

### Post by lemsx1 on 2008-10-04
> **Inteluxe said:**
> HI, I am using Ubuntu hardy with Splashy 0.3.8-1 (even i upgraded later with splashy 0.3.10 debian package) and i have this prob. Splashy gets this error: "Splashy ERROR: Timeout (120 sec) occurred while waiting for a message on the Splashy socket"

I recieve this beacuse i have to run a service during boot up sequence of a dd copy that takes 3 mins. but after 120secs splashy image disappears and this error message comes out. i have googled this error, but the "possibles fixes" i have found are not correct (like block keymap service, upgrade to newer splashy).

I wonder if we can bypass this 120 timeout or any other fix you guys know.

thanks

From Splashy's source code HACKING file:

splashy_update 'timeout 180'

That gives you 3 minutes before Splashy times out.

---

### Post by Inteluxe on 2008-10-06
Wow really, that will be great. But sorry, what do you mean by HACKING file?? do i have to edit a special file and include the 180 secs timeout. Is there a special HOWTO? :) sorry for the stupid question, but i need to know where specifically i have to source code this, because by command line execution it tells connection refused, i believe i have to source code it somewhere. Appreciate your help.

thanks!!

David A

---

### Post by lemsx1 on 2008-10-31
Splashy 0.3.12 has been released and it supports suspend again (uswsusp):

[http://alioth.debian.org/frs/shownotes.php?release_id=1251](http://alioth.debian.org/frs/shownotes.php?release_id=1251)

We made complimentary packages for Ubuntu Hardy and they can be downloaded from here:

[http://alioth.debian.org/frs/?group_id=30657](http://alioth.debian.org/frs/?group_id=30657)

Hopefully this will help a lot of you.

Enjoy!

---

### Post by lemsx1 on 2008-10-31
> **Inteluxe said:**
> Wow really, that will be great. But sorry, what do you mean by HACKING file?? do i have to edit a special file and include the 180 secs timeout. Is there a special HOWTO? :) sorry for the stupid question, but i need to know where specifically i have to source code this, because by command line execution it tells connection refused, i believe i have to source code it somewhere. Appreciate your help.

thanks!!

David A

Take a look at: [http://splashy.alioth.debian.org/wiki/developers](http://splashy.alioth.debian.org/wiki/developers)

It tells you how to get the source code for Splashy. Here is a direct link to the HACKING file:

[http://git.debian.org/?p=splashy/splashy.git;a=blob;f=HACKING;h=b9a4798db82aee6575d5c5f7fb76d38cc5268d02;hb=HEAD](http://git.debian.org/?p=splashy/splashy.git;a=blob;f=HACKING;h=b9a4798db82aee6575d5c5f7fb76d38cc5268d02;hb=HEAD)

```

31 SPLASHY_UPDATE COMMANDS

  32 =======================

  33 

  34 When talking to the Splashy server you can use the following commands:

  35   ------------+----------+----------------------------------------------------------

  36   COMMAND       ARGS      NOTE

  37   ------------+----------+----------------------------------------------------------

  38   chroot        <string>  <string> is a valid path to which Splashy will be chroot'd

  39   chvt          <number>  Switch to vt <number>. See "allowchvt".

  40   clear                   Clears the text box area.

  41   CLEAR                   Same as "clrprint". For compatibility with usplash.

  42   exit                    Exits Splashy server.

  43   getstring     <string>  Makes splashy prompt for a string. The first argument will

  44                           be the prompt displayed.

  45   getpass       <string>  Same as getstring except that the characters typed will no

  46                           be shown, like in a password box.

  47   progress      <number>  Updates the progress bar to <number>%, where N is a number

  48                           between 0 and 100.

  49   PROGRESS      <number>  Same as "progress". For compatibility with usplash

  50   print         <string>  Print <string> in the text box.

  51   scroll        <string>  Print <string> in the text box and scroll down.

  52   repaint                 Redraw the background image.

  53   TEXT          <string>  Same as "print". For compatibility with usplash.

  54   SCROLL        <string>  Same as "scroll".

  55   timeout       <number>  Sets the amount of seconds splashy waits for new commands

  56                           in the fifo file. If that time is exceeded, it exits.

  57   QUIT                    Same as "exit". For compatibility with usplash.

  58   ------------+----------+----------------------------------------------------------

```

---

### Post by Neon Lights on 2008-10-31
To be honest, Plymouth looks WAY more advanced than either of them. ;)

---

### Post by smartboyathome on 2008-10-31
> **Neon Lights said:**
> To be honest, Plymouth looks WAY more advanced than either of them. ;)

Nice find! I may try that to see how well it works when compared to Splashy (if it is available for Ubuntu, of course ;)).

---

### Post by zombiepig on 2008-10-31
> **smartboyathome said:**
> Nice find! I may try that to see how well it works when compared to Splashy (if it is available for Ubuntu, of course ;)).

Plymouth requires kernel-mode-setting support, so it'd be impossible to get running on top of intrepid without building your own kernel! 

I'm really hoping ubuntu moves to plymouth though. It looks amazing, especially the nice fades from bootup->login prompt->desktop.

---

### Post by smartboyathome on 2008-10-31
> **zombiepig said:**
> Plymouth requires kernel-mode-setting support, so it'd be impossible to get running on top of intrepid without building your own kernel! 

I'm really hoping ubuntu moves to plymouth though. It looks amazing, especially the nice fades from bootup->login prompt->desktop.

I found that out. But Ubuntu won't until the modesetting patches get adopted into the kernel, and it works for most major video cards (it only works with intel now).

I'm still gonna try this though, since my laptop runs an Intel video card.

---

### Post by gnomeuser on 2008-10-31
> **smartboyathome said:**
> I found that out. But Ubuntu won't until the modesetting patches get adopted into the kernel, and it works for most major video cards (it only works with intel now).

I'm still gonna try this though, since my laptop runs an Intel video card.

No.. it also works for most ATI cards, at least for those we have specifications currently.

The required some kernel changes (the GEM memory manager) made it into 2.6.27 before the merge window closed, with the remaining big push coming in 2.6.28 (modesetting). The code is being put through the final clean up and is likely to be put into Fedora for testing along side adoption in upstream. Ubuntu should be able to adopt the work in Jaunty  or Jaunty+1 depending on their freezes as getting 2.6.28 or backporting to 2.6.27 will be required - additionally coverage of nvidia cards since the propriatary driver will not support this stack is a problem, nouveau might have something for us by then, they might not, if not then nvidia users are forced back to the ASCII or framebuffer fallback.

Upstream is going this way, Ubuntu will very likely follow one way other another, maybe not with plymouth but then with a remodelling of usplash to use KMS. It's just a matter of their willingness to help do the work and aid in the initial testing that determines when it get into the hands of users. I would hope it would be adopted early in Jaunty, while that might be painful, the extended testing would likely end up speeding up the process of getting everything in place.

If you want to see plymouth now, on supported cards use a bog standard Fedora 10 snapshot 3 live CD of your choice and boot it. On unsupported cards you can invoke the framebuffer fallback by adding vga=0x316 (or some other vesafb setting for your resolution and color depth) to the boot settings. Otherwise you will get the rather dull ASCII fallback progress bar. Alternatively if all you want to see is the graphics and not the whole experience the following article has details and low res vidieos: [http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1)

I am happily using Plymouth on my main box, it is solid and the whole experience is very pleasant.

---

### Post by sicofante on 2008-11-01
I build only Nvidia based workstations. If/when Plymouth is ready to go with them, I'll be willing to compile the kernel in Ubuntu to run with Plymouth (I've never done that before, so it'll be a long learning before I actually do it).

Plymouth or any other KMS based boot is the definite way to go.

---

### Post by red_team316 on 2008-11-01
> **sicofante said:**
> I build only Nvidia based workstations. If/when Plymouth is ready to go with them, I'll be willing to compile the kernel in Ubuntu to run with Plymouth (I've never done that before, so it'll be a long learning before I actually do it).

Plymouth or any other KMS based boot is the definite way to go.

Yea, I'm excited about it too. The flickering is horrid in it's current state. The videos I've seen of Plymouth look very promising.

Splashy, Usplash devs, any comment on whats going to happen when KMS lands? It kinds of looks like Plymouth is going to steal the show on the technical side as well as the bling.

---

### Post by smartboyathome on 2008-11-01
> **red_team316 said:**
> Yea, I'm excited about it too. The flickering is horrid in it's current state. The videos I've seen of Plymouth look very promising.

Splashy, Usplash devs, any comment on whats going to happen when KMS lands? It kinds of looks like Plymouth is going to steal the show on the technical side as well as the bling.

No, Plymouth won't steal the show. Nvidia cards won't be supported outside of possibly the nv/nouveau drivers. In addition, the proprietary ATI driver won't be supported.

---

### Post by gnomeuser on 2008-11-01
> **smartboyathome said:**
> No, Plymouth won't steal the show. Nvidia cards won't be supported outside of possibly the nv/nouveau drivers. In addition, the proprietary ATI driver won't be supported.

till such a time as nvidia play ball with the free software community, nvidia owners could use the vesafb fallback or rely on the simple ASCII progress bar. So I fail to see the problem with plymouth, from a technical stance it does what we have now, plus more and it's easy to theme. The code is sane and maintained.

My laptop due to no fault of my own, has an nvidia card in it (was supposed to be an intel one but they send me the wrong laptop then refused to exchange it). I used the vesafb fallback by simply adding vga=0x318 (the suitable setting for my resolution and color depth) and voila, pretty high resolution bootsplash.

One could consider a solution where we default to using the vesa framebuffer for all machines, then whitelist known working videocards to go on the KMS fasttrack. Since we know what resolution and color depth a given videocard and monitor is capable off we can also set that parameter automatically (or simply do a default 800x600 like usplash does for maximum compatibility). As the ultimate fallback, we have the none framebuffer ascii progressbar, it's not as pretty as the graphical one but we have it as the last resort and it will always work.

It seems to me that plymouth has far more fallback than usplash plus capabilities to embrace the next generation. Making it all in all an appealing choice, so.. no reason why it shouldn't steal the show.

---

### Post by smartboyathome on 2008-11-01
@Gnomeuser:
Cool, I think that the usplash team should definately replace their own program with this. Usplash was always a pain to look at and try to write themes for, so the sooner we get this, the better.

---

### Post by red_team316 on 2008-11-02
gnomeuser: sure the high res bootsplash isn't a problem, but what about the flickering? I would assume that is still present since you are using vesafb fallback.

smartboyathome: Well the great thing about usplash themes is the fact that they are written in C, which gives the creator unlimited potential on what can be done with a little ingenuity. Splashy hasn't got animation support, which is really the only reason why I prefer usplash so far. Plymouth's developer documentation is nonexistant at this point but I hope it's similar to usplash and doesn't tie your hands about what you can do. 

[quote=Phoronix-A closer look at Red Hat's Plymouth]
Plymouth has an extensive API that allows artists and programmers to develop graphically rich Plymouth plug-ins. Plymouth is, however, compiled into the system's initial RAM disk (initrd) so there are some limitations. Plug-ins though can rely on loading PNG images as libpng is linked to Plymouth. The plug-ins currently available through the project's git repository currently include details, fade-in, pulser, solar, spinfinity, and text. These plug-ins are also packaged in RPM form on Fedora 10. The Fedora 10 RPMs include plymouth (the main graphical boot package), plymouth-devel (the libraries and headers), plymouth-gdm-hooks (provides integrated with GDM), plymouth-libs (the Plymouth libraries), plymouth-plugin-fade-in, plymouth-plugin-label, plymouth-plugin-pulser, plymouth-plugin-solar, plymouth-plugin-spinfinity, plymouth-scripts (scripts to assist in configuring Plymouth), plymouth-text-and-details-only (intended for those not interested in a rich boot experience), and plymouth-utils (utilities related to Plymouth).
[/quote]

gnomeuser: is there a plymouth-plugin-dev package or something similar to libusplash-dev that you can find to examine these plugins or is the source also included in the actual plugin packages. Or is there an example somewhere in plymouth-devel?

---

### Post by mjg59 on 2008-11-02
> **red_team316 said:**
> Splashy, Usplash devs, any comment on whats going to happen when KMS lands? It kinds of looks like Plymouth is going to steal the show on the technical side as well as the bling.

KMS exposes a standard framebuffer interface, so Usplash and Splashy will both be able to take advantage of that without any code modification. The reason for Usplash's existence was always to deal with vga16fb (which Splashy can't cope with) and do its own VESA modesetting in order to let suspend and resume work more reliably. Once there's pervasive support for KMS there's no real need for Usplash.

---

### Post by gnomeuser on 2008-11-02
> **red_team316 said:**
> gnomeuser: sure the high res bootsplash isn't a problem, but what about the flickering? I would assume that is still present since you are using vesafb fallback.

[snip]

gnomeuser: is there a plymouth-plugin-dev package or something similar to libusplash-dev that you can find to examine these plugins or is the source also included in the actual plugin packages. Or is there an example somewhere in plymouth-devel?

Flickering is pretty minimal still present when not using KMS. You cannot get to zero flickering without KMS, it's technically impossible. Vesa framebuffers are a fallback, but it is exactly the same technology you have now with usplash (as well as splashy) so in terms of the visual experience it's not a regression. One cool thing about plymouth is that it also extends backwards to nont vesa capable setups with the ascii mode and forwards to the KMS enabled setups. So you get a very wide range of support now and extendable in te future.

As for the structure of the code, I have not looked at it extensively but it is very powerful from what I have heard and can tell. In plymouth everything is a plugin, you change your splash by setting a plugin as the default e.g.. Making new ones appears quite easy. For examples you can look at the various plugins like spinfinity or solar. 

Here's the spinifinty plugin.
[http://gitweb.freedesktop.org/?p=plymouth;a=tree;h=31490b8ff7d4d8df8a87018367a85e809b2215ee;hb=be225ddfe06214e18084054b677e5517cfe22eef;f=src/plugins/splash/spinfinity](http://gitweb.freedesktop.org/?p=plymouth;a=tree;h=31490b8ff7d4d8df8a87018367a85e809b2215ee;hb=be225ddfe06214e18084054b677e5517cfe22eef;f=src/plugins/splash/spinfinity)

As you can see, it's basically a bunch of images and tiny bit of c (much of which we can probably break into seperate little reusable libraries. But you cleanly separate out your art task and your code tasks. Your artists can deliver a concept movie which can then very easily be translated into the actual splash. So power for artists to concentrate on their area and power to the theme coder who has a rich C experience to make it all work just right.

---

### Post by red_team316 on 2008-11-02
> **mjg59 said:**
> KMS exposes a standard framebuffer interface, so Usplash and Splashy will both be able to take advantage of that without any code modification. The reason for Usplash's existence was always to deal with vga16fb (which Splashy can't cope with) and do its own VESA modesetting in order to let suspend and resume work more reliably. Once there's pervasive support for KMS there's no real need for Usplash.
Okay, I understood that first part. I dont understand what you mean by that there will be no need for usplash though. How will the bootsplash be drawn?

> **gnomeuser said:**
> Flickering is pretty minimal still present when not using KMS. You cannot get to zero flickering without KMS, it's technically impossible. Vesa framebuffers are a fallback, but it is exactly the same technology you have now with usplash (as well as splashy) so in terms of the visual experience it's not a regression. One cool thing about plymouth is that it also extends backwards to nont vesa capable setups with the ascii mode and forwards to the KMS enabled setups. So you get a very wide range of support now and extendable in te future.

As for the structure of the code, I have not looked at it extensively but it is very powerful from what I have heard and can tell. In plymouth everything is a plugin, you change your splash by setting a plugin as the default e.g.. Making new ones appears quite easy. For examples you can look at the various plugins like spinfinity or solar. 

Here's the spinifinty plugin.
[http://gitweb.freedesktop.org/?p=plymouth;a=tree;h=31490b8ff7d4d8df8a87018367a85e809b2215ee;hb=be225ddfe06214e18084054b677e5517cfe22eef;f=src/plugins/splash/spinfinity](http://gitweb.freedesktop.org/?p=plymouth;a=tree;h=31490b8ff7d4d8df8a87018367a85e809b2215ee;hb=be225ddfe06214e18084054b677e5517cfe22eef;f=src/plugins/splash/spinfinity)

As you can see, it's basically a bunch of images and tiny bit of c (much of which we can probably break into seperate little reusable libraries. But you cleanly separate out your art task and your code tasks. Your artists can deliver a concept movie which can then very easily be translated into the actual splash. So power for artists to concentrate on their area and power to the theme coder who has a rich C experience to make it all work just right.
Thanks for the link, it's really refreshing to see the c code :D great post.

As for the flickering, I must disagree. The flickering is a huge issue and not minimal. The standard ubuntu usplashes only flicker at the progressbar because the images overlap. I have been working on a usplash that the progressbar(a round 8x8pixel ball) moves in a circular motion(approx 50pixel radius). When testing it, the graphics flicker almost if not every frame. It looks crappy due to the flickering and has been the only reason I have not worked on it further. Now that I am aware it has nothing to do with usplash, but the fb, I may finish it and release it for testing purposes.

If you take a look at my parallax usplash ( [http://www.kde-look.org/content/show.php/Parallax+Usplash?content=89780](http://www.kde-look.org/content/show.php/Parallax+Usplash?content=89780) ) , the code was optimized so that none of the layers were overlapping other than the standard progressbar(you can also see that from the preview). This eliminated the flicker from the parallax layers but prevented me from making the parallax layers and other shape than rectangles. If I had been able to overlap the layers, it would have been much more intricate and unique.

[IMG]http://www.kde-look.org/CONTENT/content-pre1/89780-1.png[/IMG]

---

### Post by smartboyathome on 2008-11-02
> **red_team316 said:**
> Okay, I understood that first part. I dont understand what you mean by that there will be no need for usplash though. How will the bootsplash be drawn?

Through Plymouth (more likely) or a modified Splashy to take advantage of modesetting (less likely).

---

### Post by Progressive on 2008-11-18
So can this make it into Jaunty or what?

---

### Post by mjg59 on 2008-11-18
> **Progressive said:**
> So can this make it into Jaunty or what?

KMS is still something of a work in progress. It's getting stable on more recent Radeons, but needs to be reimplemented for Intel again.

---

### Post by Progressive on 2008-11-18
Thank you for the quick reply! 

I haven't read this thread in awhile, but I am assuming we are talking about KMS because it is now required in Splashy? Can it be disabled?

I believe Nouveau is based on Gallium3D... doesn't that mean it has KMS by default? If intel works again soon, which is likely, and if Nouveau or nv receive KMS support soon, then could splashy be implemented in Jaunty?

What is the difference between Plymouth and Splashy? Are they competitors or do they work together?

---

### Post by mjg59 on 2008-11-18
> **Progressive said:**
> I haven't read this thread in awhile, but I am assuming we are talking about KMS because it is now required in Splashy? Can it be disabled?

Splashy requires a framebuffer console, which KMS supplies. It will also work with non-KMS based framebuffers such as vesafb.

> I believe Nouveau is based on Gallium3D... doesn't that mean it has KMS by default? If intel works again soon, which is likely, and if Nouveau or nv receive KMS support soon, then could splashy be implemented in Jaunty?

Gallium and KMS are unrelated. Gallium is a framework for writing 3D drivers and can be implemented without KMS. KMS is a framework for configuring the video mode in-kernel rather than leaving it up to X.

Whether it's ready for Jaunty really depends on how quickly the code stabalises. Fedora 10 is going to release with KMS for Radeon, but only for r300 and later chipsets. It's not clear how long Intel will take to reimplement, and it's anyone's guess how long before nouveau gains support and works well enough to be used by default.

> What is the difference between Plymouth and Splashy? Are they competitors or do they work together?

They're two different bootsplash implementations. You'd use one or the other.

---

### Post by amiller2571 on 2008-11-28
Hello. I install and setup splashy on my Desktop Ubuntu 8.10. Everything is working except the shutdown image. Whenever I shutdown it just show the text and not the image I have set for it. The startup image works great.

also for some reason my computer shuting down very fast now it used to shutdown in the expect amount of time now I can't even count to 3 before it's done.

---

### Post by red_team316 on 2008-11-28
I just tried the Fedora 10 KDE Live CD, and I got a 3-color progressbar at the bottom of the screen. I'm running a NVIDIA 8800GTS. Is the boot screen more elegant for ATI users and thats the fallback? Can someone shed some light on this possibly.

---

### Post by smartboyathome on 2008-11-28
> **red_team316 said:**
> I just tried the Fedora 10 KDE Live CD, and I got a 3-color progressbar at the bottom of the screen. I'm running a NVIDIA 8800GTS. Is the boot screen more elegant for ATI users and thats the fallback? Can someone shed some light on this possibly.

ATI is the only supported driver right now for Plymouth. Intel needs to rewrite their cards, and since NVidia's are proprietary, they need to implement support.

---

### Post by red_team316 on 2008-12-17
**Plymouth Planned For Ubuntu 9.10 Integration**
[http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ)

---

### Post by ubersolid on 2008-12-17
[QUOTE=red_team316]I just tried the Fedora 10 KDE Live CD, and I got a 3-color progressbar at the bottom of the screen. I'm running a NVIDIA 8800GTS. Is the boot screen more elegant for ATI users and thats the fallback? Can someone shed some light on this possibly.[/QUOTE]
Add vga=0x318 to the kernel line in /boot/grub/menu.lst. Works with that on an 7600gt and an 6200, + an ATI radeon xpress 1100.

---

### Post by smartboyathome on 2008-12-17
> **red_team316 said:**
> **Plymouth Planned For Ubuntu 9.10 Integration**
[http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkzNQ)

All right! Now if only the Intel drivers were updated and KMS and Plymouth were available in Arch Linux. ;)

---

### Post by Lukasz Tarkowski on 2009-02-12
Hi people
I already started making themes for Splashy.  My nickname on Gnome-Look is Rukasuzu :D

---

### Post by meeples on 2009-04-22
I tried Linux Mint last week and loved they're boot screen/login  :)


i dont know whether they use spashy, but its sexy.

i would love to see something similiar in ubuntu.:eek:

---


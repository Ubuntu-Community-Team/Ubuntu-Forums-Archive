---
title: "Trying Linux: an average user's perspective (and methods for improvement)"
date: 2008-09-12
forum: Ubuntu Brainstorm
---

### Post by Mazza558 on 2008-09-12
I've compiled a list of things that, from the perspective of a new user, might put them off from Linux. Some are small things, others are bigger and more complex to solve...

First of all, let's imagine someone called George (he doesn't exist). He has an Ubuntu-using friend (who posts on the forums) and has been recommended to try Ubuntu out. He gets a LiveCD to test. 

Let's assume he's installing on a laptop with pretty good support overall, except it uses an Nvidia card and has a Broadcom wireless card. This means no 3D/Wireless out of the box. He has been using Windows Vista beforehand, and plays a few games.


> Let's put the LiveCD in the drive. So far so good - a menu pops up, with options to "try Ubuntu without making any changes". Nothing too difficult so far - it's pretty self-explanatory.
**Suggestion: None. Nothing confusing at all here. **

> The choice of language is a bit confusing. I'm not comfortable with the size of the text, and there's obviously no mouse control. This is archaic...
**Suggestion: Change the layout a bit, making the text smaller. Make the whole language selection menu appear to look like a basic window. Maybe there could be some way to show how to select an option, but without using language...**

> Okay, now I'm at the CD menu. What's "memtest"?! What's "check for defects"? Either way, the first option seems to the right one to choose. 
**Suggestion: Make the text smaller again, and hide the options that most users don't need in an "advanced options" menu - Only "try ubuntu" and "install should be options. Perhaps clarify what the difference between "try" and "install" is?**
> 
Ubuntu's loading now. Yay! Very nice and simple screen, with a single progress bar and nothing more. Perfect. 
**Suggestion: None!**

> A cursor! A black screen with a cursor! A beige screen with a cursor!
**Suggestion: What happened to the splash screen? It would be good to reassure the user in plain english that Ubuntu's still loading and hasn't crashed.**

> A bit of an interface. Another bit. A background! Nothing's clickable yet though. 
**Suggestion: Make Gnome appear on the user screen when it's actually possible to use, as opposed to bits of interface appearing. It would be nice to see a welcome screen here, giving a short rundown (with a skip button obviously).**

> Aha! Everything's loaded. Now to try some programs. "Applications" must be the right button ... yep. This is quite simple - a little too simple. 
**Suggestion: The current gnome menus need beefing up a bit. Make it easier for users to open programs (without using menus).**

> I use Firefox on my Windows PC, nice. *firefox opens* No internet connection. Hm. That little icon in the corner might be what I'm looking for. *clicks*. Where's the wireless network?! 
**Suggestion: There's no indication at this point that George's wireless card won't work straight away. A notification at this point would be very useful. Something like "No connection - click here for more information" would be good.**

____________________

That'll do for now. Thoughts?

---

### Post by chris4585 on 2008-09-12
Very nicely written, little things like this needs to be fixed.. +1

---

### Post by SunnyRabbiera on 2008-09-12
what is a liveCS? ;)

---

### Post by smartboyathome on 2008-09-12
> Suggestion: What happened to the splash screen? It would be good to reassure the user in plain english that Ubuntu's still loading and hasn't crashed.
The splash screen was disabled by default in Ubuntu because it actually worsened startup times.

> Suggestion: Make Gnome appear on the user screen when it's actually possible to use, as opposed to bits of interface appearing. It would be nice to see a welcome screen here, giving a short rundown (with a skip button obviously).
I think if someone could port something like the XFCE splash which covers everything until the desktop is fully loaded would help, but that isn't available as of now.

> Suggestion: The current gnome menus need beefing up a bit. Make it easier for users to open programs (without using menus).
I think that it would get more confusing to let users open programs without using menus. I assume you mean using keyboard shortcuts/mouse gestures.

> Suggestion: There's no indication at this point that George's wireless card won't work straight away. A notification at this point would be very useful. Something like "No connection - click here for more information" would be good.
I think just a "Blah hardware not supported" popup should come up when the computer starts, but that may be a while in development, since it could be hard(ish?) to find what has drivers for it, and what doesn't.

---

### Post by Stefanie on 2008-09-12
> **Mazza558 said:**
> 

**Suggestion: Change the layout a bit, making the text smaller. Make the whole language selection menu appear to look like a basic window. Maybe there could be some way to show how to select an option, but without using language...**



True. I showed my brother the Ubuntu Live CD (Satanic Edition :-) ) and he was like "wtf?" when saw the language selection screen. It looks like you're back in Windows 3.1 :-) It really put him off.

---

### Post by Mazza558 on 2008-09-12
> **smartboyathome said:**
> 

I think that it would get more confusing to let users open programs without using menus. I assume you mean using keyboard shortcuts/mouse gestures.



Well, I actually meant something like a full-fledged program menu, with the most used programs/recent documents, and a search bar.

---

### Post by Lord Xeb on 2008-09-12
I personally like the suggestions. This would make things a whole lot easier for newbies :D

---

### Post by smartboyathome on 2008-09-12
> **Mazza558 said:**
> Well, I actually meant something like a full-fledged program menu, with the most used programs/recent documents, and a search bar.

A la Ubuntu System Panel, perhaps? I like the simplicity Ubuntu's menus offer, though others like extensibility over simplicity. The main drawback from this, though, is that Ubuntu System Panel takes a whole lot of memory and a noticeable amount of time longer to load than Ubuntu's menu.

---

### Post by chris4585 on 2008-09-12
> **Mazza558 said:**
> Well, I actually meant something like a full-fledged program menu, with the most used programs/recent documents, and a search bar.

I personally can't stand menus for most used programs, and recent documents.  They seem to clutter up and make the desktop not feel or even look clean. I'm not exactly crazy about a seardh bar, maybe one in the top panel?

If someone wants the most used applications and recent documents they want KDE then.

---

### Post by Mazza558 on 2008-09-12
> **chris4585 said:**
> I personally can't stand menus for most used programs, and recent documents.  They seem to clutter up and make the desktop not feel or even look clean. I'm not exactly crazy about a seardh bar, maybe one in the top panel?

If someone wants the most used applications and recent documents they want KDE then.

I have a partial solution...

---

### Post by clanky on 2008-09-12
Apart from the menus I would have to agree with almost everything else.

Looking through these forums the hardware issue seems to be the biggest issue which causes problems for new users, it was certainly the biggest problem that I had.

I can understand all the reasons why Ubuntu can't ship wth drivers for everything, but how hard would it be to detect the particular hardware and display the appropriate HOW TO for new users to get there stuff to work (with appropriate warnings about the drivers being proprietary etc.)

Or even better, say Ubuntu detects a certain wireless card which requires a firmware cutter to be installed from a 3rd party site, what about a simple wizard which will install it, again with all the warnings about the legalities, support issues etc.

As I see it this is the major obstacle which holds back the development of Ubuntu and Linux in general, most people install a Linux OS themselves rather than buy a pre-installed system where everything works and getting at least the major things (graphics, sound, wireless etc.) should be easier.

---

### Post by tom66 on 2008-09-12
^I think I am suggesting a very similar idea:

[http://ubuntuforums.org/showthread.php?t=918170](http://ubuntuforums.org/showthread.php?t=918170)

---

### Post by aysiu on 2008-09-12
These are all valid observations and suggestions, but...

1. The developers don't really work this way. They want to get many isolated ideas instead of a string of observations. You can go to [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) to make several separate suggestions.

2. I like how the installer has improved gradually over the years (you should have seen what it looked like in Ubuntu 5.04), but I do think that the scenario is a bit contrived in this thread. I'd love for the installer to be as simple to use as possible. Nevertheless, "average users" do not install operating systems themselves.

For Ubuntu to gain momentum amongst "average users" (i.e., self-professed "computer illiterates"), its focus should be on being preinstalled on more major OEMs' computers *and* on the user experience once it is already installed and configured.

Focusing installer usability on "average users" is like translating Rachmaninoff sheet music to pictures of piano keys to help beginning pianists. If you're a beginner pianist, you're not going to be playing Rachmaninoff, so what's the point? Likewise, if you're a self-professed computer illiterate, you won't be installing and configuring an operating system (yes, not even Windows).

---

### Post by Mazza558 on 2008-09-12
> **aysiu said:**
> 

Focusing installer usability on "average users" is like translating Rachmaninoff sheet music to pictures of piano keys to help beginning pianists. If you're a beginner pianist, you're not going to be playing Rachmaninoff, so what's the point? Likewise, if you're a self-professed computer illiterate, you won't be installing and configuring an operating system (yes, not even Windows).

Some people who don't quite know what they're getting themselves into might be curious to try Ubuntu out as if it was a program. If you told them they were going to "install and configure an operating system", they'd probably respond with a blank expression. Treat it as a piece of software that's easy to set up (it would be even easier if these steps were taken), and they will probably have no problems.

---

### Post by aysiu on 2008-09-12
> **Mazza558 said:**
> Some people who don't quite know what they're getting themselves into might be curious to try Ubuntu out as if it was a program. If you told them they were going to "install and configure an operating system", they'd probably respond with a blank expression. Treat it as a piece of software that's easy to set up (it would be even easier if these steps were taken), and they will probably have no problems.
I don't think tricking users into ignoring the ramifications of their actions is the way to go either.

I've already seen enough "I accidentally deleted Windows. Help!" threads.

Whether you call it "installing and configuring an operating system" or not, it still is doing that, and I would leave that to power users and OEMs.

---

### Post by gnomeuser on 2008-09-13
> **Mazza558 said:**
> 

**Suggestion: What happened to the splash screen? It would be good to reassure the user in plain english that Ubuntu's still loading and hasn't crashed.**


This is actually one of the issues the Kernel Modesetting work is intended to fix. However George is still out of luck as he has an nvidia chip in his machine, mostly since nvidia refuse to provide specifications but also because they won't be employing the technic in their own propritary driver offering.

More information on these projects and their development:
[https://fedoraproject.org/wiki/Features/KernelModesetting](https://fedoraproject.org/wiki/Features/KernelModesetting)
[https://fedoraproject.org/wiki/Features/BetterStartup](https://fedoraproject.org/wiki/Features/BetterStartup)

While this is being done upstream and piped through Fedora you should see it in an upcoming Ubuntu release as well, likely Ibex+1.

So this is something we know about and are working on fixing, it is however a hard narly little technical issue that requires a lot of work on the underlying components to be right so give us a little time.

---

### Post by Casper Hansen on 2008-09-14
Nice suggestions though I don't think they will improve anything.

I installed Ubuntu on one of my classmates laptop. He's not at all a computer geek, but he seems to like Ubuntu and he's able to use the basic programs. He also managed to install Ubuntu by himself.

It's not that the installationproces is difficult it's just because begginers get scared because they're trying something new.

---

### Post by cardinals_fan on 2008-09-14
> **Mazza558 said:**
> Well, I actually meant something like a full-fledged program menu, with the most used programs/recent documents, and a search bar.
I think that would make it harder.  Fewer clicks == good.

---

### Post by scratman on 2008-09-18
I'm sorry if this is in the wrong place or reiterating anything that has been noted already.

Networking with Windows is still a dark art with Ubuntu.  If you really want to get people to switch, this needs to be simplified to the point of being idiot proof, or at least as good as Windows!!!

Networked drives need to be easily accessible, for read and write access in both directions.

Network needs to be set up and tested at install/first login.

Programme to enable far easier creation and implementation of scripts.

update manager needs to have toe ability to perform a sudo apt-get update && apt-get replace && apt-get upgrade

Can we get some software that will record the desktop, thus enabling everyone to post video tutorials to Youtube?

---

### Post by cardinals_fan on 2008-09-19
> **aysiu said:**
> 
Focusing installer usability on "average users" is like translating Rachmaninoff sheet music to pictures of piano keys to help beginning pianists. If you're a beginner pianist, you're not going to be playing Rachmaninoff, so what's the point? Likewise, if you're a self-professed computer illiterate, you won't be installing and configuring an operating system (yes, not even Windows).
Pure brilliance :)

---

### Post by Canis familiaris on 2008-09-20
> **Mazza558 said:**
> I have a partial solution...

That's a good idea. Retaining the menu sturucture along with addition of new features...

---


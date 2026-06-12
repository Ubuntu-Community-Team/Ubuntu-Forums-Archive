---
title: "Position of Unity launcher: any chance it will be configurable in 12.04?"
date: 2011-10-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wgarcia on 2011-10-29
There is already a patch but with bugs to move the Unity launcher to the bottom of the screen:

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

But it seems that there is no a lot of chances this will make it into official Unity:

[https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415)

On my exchange with sabdfl, I summarize:

In my opinion the issue of the launcher movable is getting sort of ridiculous, both from the point of users that say that they move away from Unity because they can't move the launcher (I'm sure most of them would also move away even with a movable launcher) or from the point of view of the Unity design team not willing to introduce such a simple an obvious feature present in any other dock application (avant, docky, other OS such as MAC OS or Windows). sabdfl claims the equivalent of the launcher is not movable in the IPAD (springboard) and the Android (favourites).

---

### Post by lucazade on 2011-10-29
for unity-2d there is already a bzr branch with rtl support, so all the interface is mirrored, including the launcher.

if there is a good patch also for unity-3d I don't think there are problems to merge it, probably this patch won't come from ubuntu devs.

---

### Post by philinux on 2011-10-29
It's only a matter of time. We will be seeing more of this. For 32 bit see this.

 [http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

---

### Post by moldaviax on 2011-10-29
lets hope for an official option! oh and menus too in 12.04 :)

M.

---

### Post by cariboo on 2011-10-30
For all your hopes and wishes, I'd suggest you check Mark's keynote speech on Monday, links will be available.

---

### Post by reduz on 2011-11-01
> **wgarcia said:**
>   sabdfl claims the equivalent of the launcher is not movable in the IPAD (springboard) and the Android (favourites).

Since when did my desktop and laptop computers become tablets?
Is this really the reasoning of the design team?

What's the problem if users decide for themselves where do they want the launcher? If they so believe that launcher on the left is superior, then they have nothing to worry because users will leave it like that. If they are wrong, then users will have it their way anyway.

I think most users i talked to feel the same as I do, they got used to the launcher on the left but still miss it on the bottom. Maybe this way is better, but we clearly can't tell if we can't compare..

---

### Post by effenberg0x0 on 2011-11-01
Unlike Windows and MacOS, Linux distros, being so many and with so many available packages that customize the desktop looks, lack a unified appearance. 

Forget for a moment about Linux and Ubuntu. How harder would it be for you to sell a product that has no recognizable appearance, that people couldn't look at it and identify it? I can't imagine a single product I can sell that has this characteristics. Imagine yourself selling a car that might or not have a powerful engine, that has no specific color. The number of doors is not clear too. It's impossible.

Another point is support. It is virtually impossible to provide support for Linux users considering they may be running just about anything: Any desktop, any program, any interface, customized in n different ways. Unless you support contact center hires very expensive people - which is not the reality.

So, from a marketing point of view, I can understand the attempt to standardize Ubuntu desktop via Unity. At least for the LTS, that is the one that go business, in theory. It does make branding efforts easier. 

Most distros are a bunch of people running a lot of different stuff. There's no "unity".
I'd like Ubuntu to detach from the sea of other distros, so I support the idea, as controversial as it seems. I think it empowers Ubuntu in the long run.

And I have no doubt the launcher will eventually be customizable... If they don't do it, people will anyway. But I wouldn't expect official customization stuff for the LTS.

---

### Post by Merk42 on 2011-11-01
> **reduz said:**
> Since when did my desktop and laptop computers become tablets?
Is this really the reasoning of the design team?

What's the problem if users decide for themselves where do they want the launcher? If they so believe that launcher on the left is superior, then they have nothing to worry because users will leave it like that. If they are wrong, then users will have it their way anyway.

I think most users i talked to feel the same as I do, they got used to the launcher on the left but still miss it on the bottom. Maybe this way is better, but we clearly can't tell if we can't compare..
One wouldn't just have to code the position of the launcher though.

If it were on the right, then it would interfere with NotifyOSD. 
At the bottom it becomes a question of moving the elements in the dash since the mouse is now in a completely different position.

Granted, it seems Ayatana just says "nope it'll cause these problems", rather than telling the community about these problems and asking if they have solutions.

---

### Post by gsmanners on 2011-11-01
> **effenberg0x0 said:**
> Unlike Windows and MacOS, Linux distros, being so many and with so many available packages that customize the desktop looks, lack a unified appearance. 

Forget for a moment about Linux and Ubuntu. How harder would it be for you to sell a product that has no recognizable appearance, that people couldn't look at it and identify it? I can't imagine a single product I can sell that has this characteristics. Imagine yourself selling a car that might or not have a powerful engine, that has no specific color. The number of doors is not clear too. It's impossible.

[quizzical_dog.jpg]

Umm... Isn't that what trademarks and logos are for? (Not that I actually care about any of that nonsense, but that is its alleged purpose.)

> Another point is support. It is virtually impossible to provide support for Linux users considering they may be running just about anything: Any desktop, any program, any interface, customized in n different ways. Unless you support contact center hires very expensive people - which is not the reality.

So, people call customer support to... figure out their GUI? Que?

> So, from a marketing point of view, I can understand the attempt to standardize Ubuntu desktop via Unity. At least for the LTS, that is the one that go business, in theory. It does make branding efforts easier. 

Okay, fair enough. From a marketing point of view, it makes sense (but then, so did New Coke).

> Most distros are a bunch of people running a lot of different stuff. There's no "unity".

Most personal computers are exactly that way. That's why they're called PCs and not an electric appliance of some other kind.

> I'd like Ubuntu to detach from the sea of other distros, so I support the idea, as controversial as it seems. I think it empowers Ubuntu in the long run.

And I have no doubt the launcher will eventually be customizable... If they don't do it, people will anyway. But I wouldn't expect official customization stuff for the LTS.

(sigh) How I wish you were wrong about that, but...

[QUOTE=sabdfl]I don't get everything I want with Ubuntu. Neither will you, or anybody else. That's the nature of it. To make this into a celebrity issue is simply wasteful. It really isn't worth it.

This is not a contest of wills. This is not about forcing one persons idea over another. This is about measuring what works for people off the street, just as you describe, and deciding to focus on those things done that way. For every option we add, we add a burden for every single user. The bar is high, and this issue simply does not get over the bar.[/QUOTE]

[https://bugs.launchpad.net/unity/+bug/668415/comments/153](https://bugs.launchpad.net/unity/+bug/668415/comments/153)

Am I reading this correctly? He didn't just write that, did he? I mean, there must be some misunderstanding going on here, because it's starting to sound to me like he's preaching a rigid kind of electronic socialism. But that can't be right. Can it?

---

### Post by cbowman57 on 2011-11-01
> **wgarcia said:**
> 
On my exchange with sabdfl, I summarize:

In my opinion the issue of the launcher movable is getting sort of ridiculous, both from the point of users that say that they move away from Unity because they can't move the launcher (I'm sure most of them would also move away even with a movable launcher) or from the point of view of the Unity design team not willing to introduce such a simple an obvious feature present in any other dock application (avant, docky, other OS such as MAC OS or Windows). sabdfl claims the equivalent of the launcher is not movable in the IPAD (springboard) and the Android (favourites).

On an Android isn't it just a matter of flicking your finger across a 3" screen?  iPad a couple inches larger?

Personally I like the majority of my docks, menus & apps on the right, that feels more natural to me, but that's just personal preference.

I guess what surprises me is that  no thought seems to go into how some concepts scale up when more screen real estate is involved.

---

### Post by effenberg0x0 on 2011-11-01
> **gsmanners said:**
> 
Umm... Isn't that what trademarks and logos are for? (Not that I actually care about any of that nonsense, but that is its alleged purpose.)
Yes, that too of course... But in IT/gadgets, the interface is part of what's being sold. So much that proprietary brands register rights over developed / implemented features. It's how the market works, not that I agree with it.

> **gsmanners said:**
> 
So, people call customer support to... figure out their GUI? Que?
People call support for mostly everything. You would either laugh or cry if I show you some tapes. But generally, the employee on the other side of the line has to be able to follow a script, like: Click here, click there, etc. He can't if he receives 100 calls in 100 different DEs, customizations, etc.
 
> **gsmanners said:**
> 
Okay, fair enough. From a marketing point of view, it makes sense (but then, so did New Coke).
LOL :) Yea, there's good and bad marketing... But they try to apply the basic principles. Sometimes it will work, sometimes it won't.

> **gsmanners said:**
> 
Most personal computers are exactly that way. That's why they're called PCs and not an electric appliance of some other kind.
Nope... Seriously man, think of this support situation: "-Sir, please click your start menu on the left, now go to programs, Microsoft Office, There it is, Microsoft Excel. Now inside Excel, go to options. The menu is on the left, yes." or "-Sir, please click your start menu on the left, now type regedit in the run box and press OK.". Try with Unknown Linux user & customization. "-Are you running a custom kernel? We need to restart a service. Are you using upstart or systemd?" You'll need a much more expensive employee in the support line, a guy who can help at any distro/de, which is very rare.

As harsh as it may sound, and I know this is controversial, but I'm gonna say it. Ubuntu is not for me, or for most of the people that read this forum section. From the beginning, it was about making Linux usable, easy and popular for people that had never used Linux, that have absolutely no skill in Operating Systems or programming, for those that sometimes never had the opportunity to even get close to a PC, much less use it. I know there are many large scale social projects (digital inclusion) that have adopted Ubuntu with incredible success. 

But people like us, discussing kernel stuff, bugs in daemons, etc, come'on...We're not the public. We can download a kernel, whatever DE we want, compile and run it, name the distro after our mothers, whatever. Or we can get packages for other DEs, install them, customize the distro, etc. We do it our way, we always will. We cannot be the target of the distro evolution. The real target for IT these days is the rest of the world. Ubuntu plays wonderfully in this new users context.

---

### Post by effenberg0x0 on 2011-11-01
I have a question to people that dislike that fact that Unity can't, so far, be customized to great extents. I'm definitely curious about it. 

For me it is clear they knew that Unity might not be immediately adopted by all current users of Ubuntu. There's some change in paradigm, etc. I always though that's why they added the gnome-shell session.

Considering the gnome-shell session is very customizable, can be lighter or heavier, depending on each one's customizations, can be made to look very much like old Ubuntu versions, etc, why do people want to customize Unity in specific? Why is it so important? Why not use gnome-shell? Is there something wrong with it, that people dislike too?

---

### Post by gsmanners on 2011-11-01
I think we all know the story about the guy who calls tech support to complain about their "drink coaster" not functioning because they accidentally hit the eject button and broke the tray. :D  I also think that this isn't the usual case.

Just because tech support managers are obsessed with replacing their underlings with robots doesn't mean Ubuntu needs to change to accommodate that madness. People should know how to navigate their menus/launchers. That shouldn't even require explanation, and if it does then I think there are plenty of tutorials and Youtube videos that already do a good job of covering that.

(You are right about Ubuntu not being for me. This whole situation is making me appreciate what a true work of genius Xfce is.)

As for people who have "no skill" with computers, well that's what user groups or similar types of contacts are for. They aren't going to hire professional support, are they?

---

### Post by effenberg0x0 on 2011-11-01
> **gsmanners said:**
> I think we all know the story about the guy who calls tech support to complain about their "drink coaster" not functioning because they accidentally hit the eject button and broke the tray. :D  I also think that this isn't the usual case.

Just because tech support managers are obsessed with replacing their underlings with robots doesn't mean Ubuntu needs to change to accommodate that madness. People should know how to navigate their menus/launchers. That shouldn't even require explanation, and if it does then I think there are plenty of tutorials and Youtube videos that already do a good job of covering that.

(You are right about Ubuntu not being for me. This whole situation is making me appreciate what a true work of genius Xfce is.)

As for people who have "no skill" with computers, well that's what user groups or similar types of contacts are for. They aren't going to hire professional support, are they?

@gsmanners See, I'm not saying you're wrong, and in fact I tend to agree with most of what you're saying. But I'm giving you the point of view of the market, from companies that do Linux implementations / customization / support for other large corps and public/third sector, desktop outsourcing, OEMs, etc. It's a known business principle that if you to put a product in the market that is likely to be usable for the largest possible audience, you have to make some choices. These choices won't make niche-users, like me and mostly anyone here, happy. Yet, for the product, it is the right choice, considering the niche users know enough to find their way around any "imposed" limitation. They even provided an additional, fully customizable DE, to be selected at login. And Xfce is really great, totally agree.

---

### Post by reduz on 2011-11-01
> **Merk42 said:**
> At the bottom it becomes a question of moving the elements in the dash since the mouse is now in a completely different position. 

Dash? What's that? 
I've been using Unity for about an year and I could never get used to it. Thanks heavens i can just alt-f2 and search for wathever i want to launch... so i guess it needs a redesign anyway.

---

### Post by reduz on 2011-11-01
> **effenberg0x0 said:**
> I have a question to people that dislike that fact that Unity can't, so far, be customized to great extents. I'm definitely curious about it. 


No one wants to customize Unity to great extents. At least, moving the launcher to the bottom of the screen seems like very basic customization that is not even present.

I've been working on usability design in interfaces for probably much longer than most in the Ubuntu design team.

Nowadays, there's a huge debate in usability design, customization vs no customization and most designers don't seem to get it.  

Customization, in reality, is sort of like a curve where you have to find the sweet spot to please the most users. That spot, in my experience, is not in the "zero configuration", because we are all different. It's also not in the "high customiation" side, because too many options also become confusing to most users.  

The pleasantness curve peaks somewhere between the "little to  medium customization". Gnome 2 developers learned that the hard way and there were many years where most of their users flocked to KDE. They didn't seem to learn and are now repeating history with Gnome 3. 

Ubuntu Unity will, without a doubt, go through that process too, and I guess they will start adding options when they get fed up of user requests like this, or when they realize they need to please their users to a certain extent to achieve the desired amount of acceptance by the community, or at least recover the level of acceptance they had prior to  introducing Unity.

> **effenberg0x0 said:**
> I have a question to people that 
Why not use gnome-shell? Is there something wrong with it, that people dislike too?

Yes, Gnome Shell is also zero configuration. Expose style window switching only works depending on the type and amount of applications you use. If you are like me and uses several text-over-white background applications at the same time (like gnome terminal, chrome, nautilus, gedit, xchat, empathy, etc), then the zoomed out apps become several and all look like the same. Unity uses icons, and icons are much easier to distinguish at a glance than zoomed out windows.

And while it's true that Gnome Shell has extensions, my experience is that they are poorly maintained, difficult to install and break between releases. 

Also, at this point in my life as linux-desktop user, I know very well that most "extensions" that are not official break often and die soon and you can be left with a non functioning setup when you less expect it.
That's why Gnome Shell is a no go.

---

### Post by effenberg0x0 on 2011-11-01
@reduz I see your point. I have zero experience with gnome-shell, I expected it to be more fulfilling for users in terms of maturity and customizations. I liked your point of view about this theme and, seeing that you have experience in such subject, you should express it to the people currently working on the Unity design. They sure could use good insights and guidance. I believe you could go to and contact the rpoject leaders/maintainers through here: [https://launchpad.net/ayatana](https://launchpad.net/ayatana) . At least leave a Blueprint idea to them.

---

### Post by philinux on 2011-11-01
After not liking unity at all I now really like it. I can understand wanting a right or left option. But having it on the bottom just wastes screen height to me. Just a personal observation.

I guesses all options will eventually exist one way or another.

---

### Post by keithpeter on 2011-11-01
Hello All

I'm running 11.10 off a USB stick with Unity for at least one hour per day to evaluate the way it works and to learn some new tricks. Laptop, trackpad and IBM trackpoint.

I can overshoot the 'back' button in the web browser and trigger the launcher - quite often, one of those annoying things.

If I install [smartboard interactive white-board software]("http://smarttech.com/us/Support/Browse+Support/Product+Index/Software+Products/SMART+Notebook/Version+10+for+Linux"), then I'll have the whiteboard tool pane (default left but drag-gable), to cope with as well.

Choice of position would be good! As per Windows 7 and Mac OS (I've only used up to Panther).

---

### Post by gsmanners on 2011-11-01
> **keithpeter said:**
> I can overshoot the 'back' button in the web browser and trigger the launcher - quite often, one of those annoying things.

You know, the cool thing about Firefox is that you can customize all that. I just stick the buttons, the address box and everything else right next to the menu. I'll bet I save a lot of vertical space doing that, but then if I wanted vertical space, I'd just hit F11.

---

### Post by reduz on 2011-11-01
> **philinux said:**
>  But having it on the bottom just wastes screen height to me. Just a personal observation.


There's nothing wrong with wasting screen height, Mac users don't complain, Windows users don't complain, it obviously makes no difference to most people at this point, specially on medium to large screens.

If you use a 24" monitor, you have to literally tilt your head to see the icons on the launcher and switch application. this does not happen on the bottom. It's like Ubuntu design team belives we all use Ubuntu on a 10 inch tablet.

---

### Post by lswb on 2011-11-01
> **effenberg0x0 said:**
> ...
 Imagine yourself selling a car that might or not have a powerful engine, that has no specific color. The number of doors is not clear too. It's impossible.
...

But that is precisely how most cars *are* sold. The buyer can choose the color, engine size, 2 door, 4 door, or in some cases station wagon, automatic or manual transmission, and dozens of other options.

---

### Post by cbowman57 on 2011-11-01
Some of you might find this interesting, it's about the future of Unity & customisation. [http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/](http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/)

---

### Post by gsmanners on 2011-11-01
> **cbowman57 said:**
> Some of you might find this interesting, it's about the future of Unity & customisation. [http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/](http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/)

No mention of the launcher position, though.

---

### Post by reduz on 2011-11-01
> **cbowman57 said:**
> Some of you might find this interesting, it's about the future of Unity & customisation. [http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/](http://www.omgubuntu.co.uk/2011/11/ubuntu-desktop-designers-clarify-on-configurability/)

I don't mind them stabilizing unity, but at this point and given how unity even has a unity 2D counterpart, it seems like a several years span project..

---

### Post by cbowman57 on 2011-11-01
> **gsmanners said:**
> No mention of the launcher position, though.

I'm sure that's the code they will leave untouched.  :lol:

---

### Post by cariboo on 2011-11-01
> **reduz said:**
> Dash? What's that? 
I've been using Unity for about an year and I could never get used to it. Thanks heavens i can just alt-f2 and search for wathever i want to launch... so i guess it needs a redesign anyway.

If you're using Alt-F2 to search, you're doing it wrong. Alt-F2 brings up a run dialogue box, not a search box. You'll find if you click the BFB, and type the first three letters of what you are searching for, you'll get much better results.

I really don't understand why people spend time running something they don't like. There are so many different Desktop Environments, if you can't find one that suits you you haven't look hard enough.

---

### Post by reduz on 2011-11-02
> **cariboo907 said:**
> If you're using Alt-F2 to search, you're doing it wrong. Alt-F2 brings up a run dialogue box, not a search box. You'll find if you click the BFB, and type the first three letters of what you are searching for, you'll get much better results.


Thanks! though I wonder why they can't be combined, like in Windows 7.

> **cariboo907 said:**
> If you're using Alt-F2 to search, 
I really don't understand why people spend time running something they don't like. There are so many different Desktop Environments, if you can't find one that suits you you haven't look hard enough.

I'm sorry but that's a mediocre argument, and in the same line as whatever the unity design team tries to impose users. I mean, this is not facebook where you "like" or "dislike" something. I actually *do* like Ubuntu Unity, much more than Gnome 3, KDE or Xfce. I just dislike the lack of even the minimum ability to customize something as basic as moving the launcher to the bottom, like in any other desktop envieronment, and I find looking for apps in menus to be more cumbersome than just searching for them, just like in Windows 7 and OSX. But that's just my personal taste.

This is why "zero configuration" is a failed concept, it's been proven to have failed again and again over time, because it relies on the idea that users will just "get used to it". 

In reality, the more you take away a feature (and don't even offer a replacement), the more most users will miss it, and the more important that feeling of lacking will become over time. Obviously, you can't please everyone, which is why offering a minimum to medium degree of configuration (without going overboard) is vital to please the largest chunk of users. See how now iOS is taking features from Android, becauses users got used to stuff such as global notifications, voice commands, etc.

Been there 10 years ago when Gnome 2 was out. This is just history repeating itself..

---

### Post by wgarcia on 2011-11-03
> **philinux said:**
> After not liking unity at all I now really like it. I can understand wanting a right or left option. But having it on the bottom just wastes screen height to me.

This is also my opinion now, but before 11.04 I was working with an avant window navigator dock at the bottom of the screen set to autohide and I never felt loosing vertical space, the dock would just pop up when I needed it. 

But now I got used to having the launcher at the left of the screen and even always visible. 

In any case, even if I probably will not move the launcher from the left, I still believe the position of the launcher has become a matter of stubbornness, both from the point of users crying for being able to move it and from the point of view of the Unity design team refusing to introduce just an obvious issue present in all known application docks.

---

### Post by jerrylamos on 2011-11-03
> **gsmanners said:**
> No mention of the launcher position, though.

Well, my netbook, my tower, and my notebook, all relatively recent, are short and wide.  I've got the most space on the end(s).  

What I would like configurable is replace the low information content "icons" with high information content aphameric text.  Same complaint I've got with apple.  

Somehow Unity designers think that users will remember a peculiar picture faster than reading text.

Perhaps the Unity developers are more interested in their concept of eye candy than in being useful.  

So when I'm doing mucking around with partitions, downloading, building bootable iso's, etc. I fire up Lynx LTS.  Faster and easier.

Problem is, Lynx LTS works so I don't have any bugs to report.

Jerry

---

### Post by lswb on 2011-11-03
> **reduz said:**
> Thanks! though I wonder why they can't be combined, like in Windows 7.

...

You know, there was a gnome applet at least as far back as dapper (6.06) that did exactly that. Not sure when it was dropped, maybe around 8.10 or 9.04.

---

### Post by cariboo on 2011-11-03
If you click on the desktop and start typing a textbox opens in the lower right of the desktop. I have know idea what it's supposed to do, as typing anything and pressing enter doesn't do anything..

See the screenshot.

---

### Post by effenberg0x0 on 2011-11-03
> **cariboo907 said:**
> If you click on the desktop and start typing a textbox opens in the lower right of the desktop. I have know idea what it's supposed to do, as typing anything and pressing enter doesn't do anything..

See the screenshot.

I've seen that too and found no possible use, despite the fact that it will select the desktop icon that has the text you type in. It seems to be just a left over from Nautilus and probably and undesired behavior / bug of minor relevance as there's no detectable side effect.

Example: Create two icons in desktop: abc and def. Click anywhere on desktop, type abc: abc icon is selected. Type def: def icon is selected. But it doesn't look like a feature.

---

### Post by seeker5528 on 2011-11-03
> **reduz said:**
> Thanks! though I wonder why they can't be combined, like in Windows 7.

Search in the dash is as almost as much of a combined search/run as it is in Windows 7, relative to what people want the larger part of the time, the search in the dash shows you programs that show in the menu, but you can't supply arguments the way you can in Windows 7.

People expect 'Alt'+'F2' to be a run box, and that's what you get, it seems to have some quirks. What you get when you hit 'Alt'+'F2' one ups Windows 7 in the sense that if you choose to display 'run...' on the Windows 7 menu, you get a run box with zero search capability, it will try to match what you type in to stuff it has in history, but you don't get any match-ups that will show you the available commands that are not in the history, when you use 'Alt'+'F2' to bring up the run box in Unity you get matches to both history and commands that show in the menu.

To me the question is not 'Why doesn't 'Alt'+'F2' bring up a search dialog?', the question is 'Why is there no number/letter on the dash icon in the launcher when you hit the <super> key>?', seems inconsistent.

But if you look up the keyboard shortcuts you do find out that if you tap the <super> key instead of holding it down, it does bring up the dash.

Yeah, I know that doesn't answer the question about why 'Search' doesn't have better run capability, but when 'Search' and 'Run' are as quickly accessible as they are, does it *really* matter that much? ;)

Later, Seeker

P.S. I didn't know some of this stuff either before doing some investigation while writing this post.

---

### Post by seeker5528 on 2011-11-03
> **cariboo907 said:**
> If you click on the desktop and start typing a textbox opens in the lower right of the desktop. I have know idea what it's supposed to do, as typing anything and pressing enter doesn't do anything..

If you have launchers on the desktop, type enough to be unambiguous, then hit the enter key, it will bring up the target of the launcher.

I have a 'Terminal' icon on my desktop and being the only thing on the desktop that starts with 'T', when I type 'T' and hit 'Enter' it launches the Terminal.

As research for this post, I browsed to '/usr/share/applications/' in Nautilus, right clicked 'Firefox', chose ''Copy To...' --> Desktop', to get Firefox to show on my Desktop, then typed 'F', since Firefox is the only thing on my Desktop that starts with 'F', hit 'Enter', and it opened a new Firefox window.

Later, Seeker

---

### Post by linuxuser12345 on 2011-11-03
I don't just want to see position changing for the Unity launcher: I want to see fully customizable themes for it, I want to see icon theme changeability, and I want to see the option to disable the launcher completely.

---

### Post by cariboo on 2011-11-03
All that is already possible, check the [screenshot thread ]("http://ubuntuforums.org/showthread.php?t=1873091")to see what others are doing with Untiy.

---

### Post by effenberg0x0 on 2011-11-03
The claims for disabling the launcher, restoring traditional panels, changing icons, yada yada are incredibly dumb. They can be done. They have been done. There is information showing people how to do it. There are many ways to do it. One can even choose what fits better.

They sadly prove that not only Ubuntu users have learned nothing about Linux yet (otherwise they would at least imagine that, in some magic and complex way, things can be changed in a Linux OS) but also that they can't read (or even look at images!?). In this very section of the forum there are pictures of desktops with no Launcher Bar and with traditional panels. A couple minutes of search will find pictures of a movable launcher and much more. Googling one can find in the first hit icons sets and instructions on how to install them.  

And the only really important thing, the only one that no one can easily work around, and that is the topic of serious discussion by users and devs is not mentioned anywhere: The global panel, it's ergonomic factors, etc. 

I find it amazing how people are lazy to the point of choosing ignorance versus wasting 5 minutes reading / learning / knowing what they are talking about. 

By the way, I DEMAND an Open Source version of Microsoft Bob in PP.

---

### Post by cariboo on 2011-11-03
> By the way, I DEMAND an Open Source version of Microsoft Bob in PP.

MS BOb runs in a vm, if you ran it in seamless mode, it would look like its running in PP. :) :) :)

---

### Post by gsmanners on 2011-11-03
> **effenberg0x0 said:**
> I find it amazing how people are lazy to the point of choosing ignorance versus wasting 5 minutes reading / learning / knowing what they are talking about.

It's isn't true till clippy says so. \\:D/

---

### Post by effenberg0x0 on 2011-11-03
[I]It looks like you are trying to move the 
launcher? You can't. Ubuntu betrayed 
you. Do you prefer to:

- Post a threat to move to Mint?
- Post a demand in Ubuntu+1?[/I]

[ATTACH]206252[/ATTACH]

---

### Post by effenberg0x0 on 2011-11-03
> **cariboo907 said:**
> MS BOb runs in a vm, if you ran it in seamless mode, it would look like its running in PP. :) :) :)

Nice idea lol, gonna try it :P

---

### Post by keithpeter on 2011-11-04
> **gsmanners said:**
> You know, the cool thing about Firefox is that you can customize all that. I just stick the buttons, the address box and everything else right next to the menu. I'll bet I save a lot of vertical space doing that, but then if I wanted vertical space, I'd just hit F11.

Well, good heavens, that worked nicely, but I had to go to View | Toolbars and untick the navigation bar to get the extra pixels.

Thanks

---

### Post by reduz on 2011-11-05
> **effenberg0x0 said:**
> [I]It looks like you are trying to 
- Post a threat to move to Mint?
[ATTACH]206252[/ATTACH]

I wonder if Ubuntu developers really don't care about users moving largely to another distro. The Mint guys just announced that they are working on creating extensions to make Gnome 3 more usable, combined with the fact that they are having a great momentum because plenty of Ubuntu users are announcing their switch.

I mean, users are not just moving, they are disappointed and sharing their frustration with the rest of the community. Most of the comments I hear about Ubuntu recently are negative and can be resumed to "Unity Sucks". If you talk to them, the first thing they mention is "lack of customization". 

Yet Ubuntu developers don't seem to care, and don't announce anything relevant except "12.04 will be faster, more stable and use less memory". I don't think users who left even care about that..

---

### Post by PRC09 on 2011-11-05
Looks like Ubuntu is really a moving target.Who knows what is coming next,considering it will be for 5 years.....


[http://www.omgubuntu.co.uk/2011/11/banshee-tomboy-and-mono-dropped-from-ubuntu-12-04-cd/](http://www.omgubuntu.co.uk/2011/11/banshee-tomboy-and-mono-dropped-from-ubuntu-12-04-cd/)

---

### Post by graphius on 2011-11-06
> Forget for a moment about Linux and Ubuntu. How harder would it be for you to sell a product that has no recognizable appearance, that people couldn't look at it and identify it? I can't imagine a single product I can sell that has this characteristics. Imagine yourself selling a car that might or not have a powerful engine, that has no specific color. The number of doors is not clear too. It's impossible.
You can order a custom house. Many clothes from the same designer don't look similar. But lets look at your car analogy. You can choose your colour, you can often choose your engine, in fact, there are cars where you can choose a coupe, sedan or convertible. Sorry, if I had to buy a car where I had no choice in colour etc, I would go down the road to the next dealer.....

---

### Post by cariboo on 2011-11-06
> **graphius said:**
> You can order a custom house. Many clothes from the same designer don't look similar. But lets look at your car analogy. You can choose your colour, you can often choose your engine, in fact, there are cars where you can choose a coupe, sedan or convertible. Sorry, if I had to buy a car where I had no choice in colour etc, I would go down the road to the next dealer.....

This is as about as silly as people using being right-handed as an excuse for moving the launcher to the right side of the screen. The only real right-handed system I've seen is OS X, Windows certainly isn't, all the menus are on the left side of the screen, and most windows menus are moved to the left.

IF you actually watch how you work, you'll find that your mouse cursor spends the majority of the time on the left side of the screen.

As far as your car and colour analogy goes, you can change colours, themes, icons and fonts, it just isn't as easy yet as it was with GTK-2. Check the [screen shot thread ]("http://ubuntuforums.org/showthread.php?t=1873091")in the Cafe to see what some users are doing with Unity and Gnome-shell

---

### Post by agillator on 2011-11-06
In this discussion of Unity, etc., you might remember that at one time Henry Ford said people could have their cars any color they wanted as long as it was black. It seems to me we are in danger of returning to that way of thinking. Having said that, I understand that Ubuntu and Unity and the rest are someone's brainchild, it is theirs and they have the right to make it look like or do anything they want. I wouldn't change that for the world. End of story. However, there is a footnote: I am not a captive audience, nor are any of your other users/customers. Personally, I moved to Xubuntu, not because I don't like Unity, which I definitely and strongly don't, but because I was being placed well down the road of having no choice - in other words I could not change it into something I did like, or at least could put up with. That, in my eyes, is the mistake that has been made. Now I am getting hints that perhaps things are changeable after all, or are to some extent (shades of Bill Gates and Microsoft!). Maybe someday I will come back and look at it to see, but I have become happy where I am so why should I bother? The true power and lure of Linux, for me at least, is that it can be anything I want it to be if I am willing to put in the effort. I am not subject to someone's whims unless I choose to be. So can Ubuntu, at least so far. So make the basic look and act any way you as the developers wish. That is certainly your right. But, if you are wise, you will leave me the option to change all of that. Having said that, I fully realize that the different versions of Ubuntu (Xubuntu in my case) allow me to do just that. If that is what you intend then you might make that clear and point people in the various directions.

---

### Post by effenberg0x0 on 2011-11-07
I don't think people understand that making something show on screen, react to the mouse, start procedures, move, go to one side, go to another, dance the hula, etc demands thousand of programming lines and many hours from programmers, designers, etc. Sometimes hundred or thousand of hours until a feature is ready. 

This ain't Microsoft: We can't demand the developers team to make something work flawlessly and in the most complete possible way by friday or fire everyone. Look at the developers and contributors: Many are just contributors with real jobs, that help in their spare time. This is Free Software.

If it was possible to have all bug reports solved, all requests fulfilled, all features coded and tested tomorrow, do you think someone would be against that? Of course not, it would be just wonderful. I would love to have the Unity bar movable, stretchable, totally configurable, etc. But this is the real world, it won't happen soon. There are priorities in front of aesthetics right now, things that have to be fixed as fast as possible regarding its workings. 

So, either you use it and follow its development until product maturity, or you help develop it, or you don't use it and use something else. Those are the only options right now. No one can turn Unity into mature code, which fulfill all customizations  requests by user, in the upcoming days or until the release of next  version. There's no magic solution. There are many possibilities as to what one can inside or outside Ubuntu besides Unity and you should choose whatever makes you happy.

---

### Post by vasa1 on 2011-11-07
> **agillator said:**
> ... you will leave me the option to change all of that...

Providing options may not be as easy as we think.

Also, Canonical maybe thinking ahead of how to handle subsequent help queries. Having most people on exactly the same set-up would be easier to handle for the support staff.

---

### Post by robert shearer on 2011-11-07
> **cariboo907 said:**
> 
IF you actually watch how you work, you'll find that your mouse cursor spends the majority of the time on the left side of the screen.

I watched as requested and my mouse cursor spends the majority of the time on the right side of the screen. Guess I must be odd...?

On my dual monitor set up I have to move all the way from the right of the right-most screen across vast oceans of screen real estate to the left and to the launcher.
Sabdfl has said that this is how it is meant to be by design.

"Mediocrity is achievable !, this explains its popularity"  is this is how Ubuntu gets 180 million new users...? ;)
Well, it works for other operating systems...

---

### Post by agillator on 2011-11-07
Effenberg0x0: As a matter of fact I am well aware of the effort required and am often astounded by what is being accomplished in and by open source software. Maybe there is some hope for this species after all. Having said that, my remarks were directed at an attitude I ran into when Unity first came out. There were things I didn't like, I strongly didn't like. I didn't understand why this direction had been chosen. So, I investigated. I found out that Gnome was also changing, that there were other problems with gnome, etc. Now I understood a little more. The problem was that I then ran into a brick wall - this is our decision and it is the way things are going to be. No, you are not going to be able to change things. No, there will not be other options (Gnome2). There was, at that time, no hint of "We're working to develop these things but it isn't there yet." There was also no hint of "The differences are too great so we are selecting this route. Other routes are available in . . . ." All I was left with was the Henry Ford attitude. So, I found another route on my own. This was where my comment was directed. I would hate to see the entire Ubuntu movement die because of that attitude, which it might. And if it were to do so, it would be because of the attitude, not because of Unity.

---

### Post by effenberg0x0 on 2011-11-07
This makes no sense. We have previous versions of Ubuntu being normally used, which is totally acceptable, we have Ubuntu customized by users to run whatever DE they like (lxde, xfce, etc), we have people running gnome-shell, we have people happily running Unity, there's Ubuntu server, in many versions, being normally used everywhere, there's Lubuntu, Jubuntu, Xubuntu, Edubuntu, etc. 

As I always say: Most distros are a bunch of guys running a bunch of packages. The distro managers just chooses some packages, puts them together in a CD, that's it. Ubuntu detaches from the majority by actually having a community, some coherent long-term plan, some professional operations and management, it's own development (for some packages), etc. 

Ubuntu got the point in which it could wait and see what other distros would do or go head and do something. They chose to do something, which is very complex, involves a lot of people, resources, coding time, etc. Yes, it's not perfect and it won't suit all users needs so soon. But still, they are doing something, which is not so common as people might think in the Linux arena. 

The idea that Ubuntu will die is just ridiculous. It's simply the opposite: It now is stronger than ever, it detaches from other distros by having the guts to play its own strategy, go on with its own development, etc.

---

### Post by 23dornot23d on 2011-11-07
> 
I watched as requested and my mouse cursor spends the majority of the  time on the right side of the screen. Guess I must be odd...?

On my dual monitor set up I have to move all the way from the right of  the right-most screen across vast oceans of screen real estate to the  left and to the launcher.
Thats not odd at all ...... while mine is resting its in the bottom right - quarter most of the time out of the way of what I am viewing or doing ...... only when I pick something does it
usually move away from there ......

But its not obvious where any studies were carried out or what they were tracking .....
put a trackometer on the mouse it travels more than any long distance runner on my
dual monitor set-up with just UNITY working.

Dual screen ...... even if my mouse was on the left side of the right screen 
the minimum distance to get to the dock is 1920 pixels ...... minus possible the size of the icons ..... that is if they are not hidden .

I use UNITY ...... but not for long periods of time .... the screen soon becomes cluttered
have any studies been done on this ..... for normal users .

As often I have one thing on top of another ....... maybe there is a way to quickly organize all of these windows applications at startup .

I would like to see a video of someone using it - like the ones of gnome-shell ..... it is easy to see the organization of your applications ..... and you do not have to spend lots of time worrying about it ...... or setting it up for a demo ..... it just works.

As the computer is here to get rid of our repetitive tasks ..... supposedly.

But I do like UNITY more now as custom things are coming in ..... moving the dock to the bottom ..... transparency and adding the original drop down menu in the top right of the panel starts to make it more of a useful tool - shame it soon becomes cluttered though.


> 
The idea that Ubuntu will die is just ridiculous.
It will not die - it will start dropping down the [[COLOR=Red]**Distrowatch list though**[/COLOR]]("http://distrowatch.com/") .......

---

### Post by Merk42 on 2011-11-07
> **cariboo907 said:**
> The only real right-handed system I've seen is OS X...
OFF-TOPIC: Why do you think that?

---

### Post by 23dornot23d on 2011-11-07
No matter whether right handed or left handed ..... the desktop should work efficiently 
for all ..... even me but I am ambidextrous ....

Just found out the cardapio extension used on Unity also works in the shell .....

just saw it in the Tweak Tool Extensions as I added it to try out ..... but I also remove
applications menu as they seemed to occupy the same space on the top bar.

[IMG]http://img836.imageshack.us/img836/1916/cardapio.jpg[/IMG]

[[COLOR=Blue]_**a familiar menu for those that want it**_[/COLOR]]("http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html") ........ Updated .. as a link was given by Beew

[IMG]http://img259.imageshack.us/img259/9827/dropdown4.jpg[/IMG]

Helps when the layout suits both though .... :)

---

### Post by cariboo on 2011-11-07
> **Merk42 said:**
> OFF-TOPIC: Why do you think that?

After posting that, I realized I was wrong, The only right handed part about OSX is where it places icons in a default setup, almost everything else is bisaed towards the left.

---

### Post by coffeecat on 2011-11-07
Sorry I'm a bit late (3 days! :() picking this up:

> **cariboo907 said:**
> If you click on the desktop and start typing a textbox opens in the lower right of the desktop. I have know idea what it's supposed to do, as typing anything and pressing enter doesn't do anything..

> **effenberg0x0 said:**
> I've seen that too and found no possible use, despite the fact that it will select the desktop icon that has the text you type in. It seems to be just a left over from Nautilus and probably and undesired behavior / bug of minor relevance as there's no detectable side effect.


I will find it very useful, and thanks for pointing it out. Personally, I hope it's not a bug that will be removed. There are occasions when I need to type out small amounts of text for copying into the clipboard for later pasting. Opening gedit just for that and then dismissing the "save changes" windowlet is irritating. 

Nice find! :)

---

### Post by mc4man on 2011-11-07
> **coffeecat said:**
> Sorry I'm a bit late (3 days! :() picking this up:

I will find it very useful, and thanks for pointing it out. Personally, I hope it's not a bug that will be removed. There are occasions when I need to type out small amounts of text for copying into the clipboard for later pasting. Opening gedit just for that and then dismissing the "save changes" windowlet is irritating. 

Nice find! :)

Can't see that typeahead on the Desktop is a bug, believe it comes from the option 'Have file manager handle the desktop' which is default enabled for unity* & Gs

The currently are some bugs with typeahead, though not when used on the Desktop, only on nautilus windows - a fix there **may** be forthcoming
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879456](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879456)
There was a patch that fixed for the most part, (currently using here),  but apparently not completely

---

### Post by seeker5528 on 2011-11-07
> **cariboo907 said:**
> After posting that, I realized I was wrong, The only right handed part about OSX is where it places icons in a default setup, almost everything else is bisaed towards the left.

This whole 'right handed system'/'left handed system' makes not sense to me.

Maybe I'm taking right/left handed too literally?

Setting the flow relative to the written language would make sense to me.

For default on left to right written languages, putting things on the left and having them flow to the right makes sense and for right to left written languages, putting them on the right and flowing to the left makes sense.

If there was 'right to left'/'left to right' flow based on written language, then it seems like it should be a pretty minor thing to provide a 'reverse flow' option to the user.

As for moving the launcher around independently of that, if there is a non-Canonical supported solution available that allows that, I don't see what the big deal is.

Later, Seeker

---

### Post by coffeecat on 2011-11-07
> **seeker5528 said:**
> 
Setting the flow relative to the written language would make sense to me.


At last! Someone after my own heart. I agree. :)

Where the language reads from left to right, then it makes sense (imo) to have the menus starting from the left and reading from left to right. Launcher and buttons on the left also and there you have it - minimal mouse movement.

Of course, this makes no sense for those people whose written language goes from right to left and I would guess they would want menus, launcher and buttons to be on the right.

---

### Post by reduz on 2011-11-08
Any idea if there has been any comments on this topic from the ubuntu developers, or where should one look for a (more up to date) official answer?

---

### Post by effenberg0x0 on 2011-11-08
> **reduz said:**
> Any idea if there has been any comments on this topic from the ubuntu developers, or where should one look for a (more up to date) official answer?

I think that, in general, it's rare for developers to have the time to  look at the threads at Ubuntu+1 entire forum section, reply, etc. We see jbicha  posting regularly, but that's it AFAIK. 

You have a better chance of expressing your points and getting listened  to if you go to Ayatana/Unity launchpad and post there.

---

### Post by robert shearer on 2011-11-08
> **reduz said:**
> Any idea if there has been any comments on this topic from the ubuntu developers, or where should one look for a (more up to date) official answer?

Yes, comprehensively commented by Mark Shuttleworth here....
[https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415)

Basically, = won't fix, (that's **"Won't"** not "can't", not maybe, not "we will think about it", not now, probably not ever, and looks like never.)

@effenberg  > You have a better chance of expressing your points and getting listened to if you go to Ayatana/Unity launchpad and post there.

Unfortunately, on this issue Shuttleworth has advised that any further discussion should be on the Forums.(post #213 2011-11-06 in the above bug) 
(presumably as he considers it a bug that will not be progressed/addressed and people should "move on".)

---

### Post by effenberg0x0 on 2011-11-08
> **robert shearer said:**
> Yes, comprehensively commented by Mark Shuttleworth here....
[https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415)

Basically, = won't fix, (that's **"Won't"** not "can't", not maybe, not "we will think about it", not now, probably not ever, and looks like never.)

@effenberg  

Unfortunately, on this issue Shuttleworth has advised that any further discussion should be on the Forums.(post #213 2011-11-06 in the above bug) 
(presumably as he considers it a bug that will not be progressed/addressed and people should "move on".)

Hi Robert, I think they probably overlook at some threads here, but presumably not with the same dedication and thoroughness than the forum regulars. Working with software development takes a great amount of time and, IMHO, it's sort of a lone activity that one enjoys doing uninterruptedly, with increased concentration and focus. That's at least how I and other people at work that code something get, in sort of a "leave me alone / not talking / zen state" while coding. Mark is probably very busy with all the management and business activities related to Ubuntu. He probably has very little free time to exhaustively read all the forum threads, etc. It's comprehensible.

My opinion: PPAs will be filled with non-official Ubuntu/Unity customization packages in no time. There already are some. I am working on some customization, many others are. These will be disregarded for this cycle and merges will be refused. Eventually, one (or a few) of these PPAs will reach such popularity with end-users, join efforts, etc, that developers will either embrace their code or partially duplicate its functionality (next cycle, PP+1).

See my case right now: I'm working on a couple of Ubuntu things (for work and personal):
- Customizing dash home shortcuts via Interface on settings panel - done, testing.
- Moving the launcher (easy) without breaking the dash (hard) - ongoing.
- Move ccsm plugins and prefs to settings panel - ongoing.
- Customizing the greeter to provide: More information regarding available sessions, session options/customization prior to login, etc - planned, not started.
- Safer partitioning / install tool (auto move grub to 1MB partition, copies latest ISO to unmounted partition, allow to create system restore point, easy reinstall/recovery procedure) - planned, not started.
- Proactive system maintenance tool: Idea / code samples specified at work, currently negotiating to make it open source.
 
Eventually, as I get the time to, I'll publish some of these stuff, as soon as the code gets mature and safe enough. Other guys will too. Someone already published something to move the launcher, etc. 

What I am saying is that you can rest assured that, being it official or non-official, you'll soon see  a growing number of options to increase the configurability of many Ubuntu aspects. It's unavoidable.

---

### Post by reduz on 2011-11-09
> **robert shearer said:**
> Yes, comprehensively commented by 
(presumably as he considers it a bug that will not be progressed/addressed and people should "move on".)

Yes, people is moving on.. to other distros, as can be seen here: [http://distrowatch.com/](http://distrowatch.com/)
Fedora and Mint are becoming much more popular.

Ubuntu is very clearly becoming a negative brand for a lot of users. This is extremely dangerous to any kind of business, and will definitely affect future products (phone or wathever).
The more time it goes on, the more irreversible it becomes.

Users feel like Ubuntu developers are not listening, that Ubuntu devs do not care about them and that becomes a grudge. That leads to looking for alternatives instead of exploring kubuntu or ubuntu. If you look at distrowatch, anything ubuntu related is going down, while Mint is growing a lot.

And you guys in the forum should worry about it, even if you are fine with the current direction of events, because at the end Ubuntu is a business, and if it does not generate revenue in the long term, it will simply go away.

---

### Post by effenberg0x0 on 2011-11-09
> **reduz said:**
> Yes, people is moving on.. to other distros, as can be seen here: [http://distrowatch.com/](http://distrowatch.com/)
Fedora and Mint are becoming much more popular.

Ubuntu is very clearly becoming a negative brand for a lot of users. This is extremely dangerous to any kind of business, and will definitely affect future products (phone or wathever).
The more time it goes on, the more irreversible it becomes.

Users feel like Ubuntu developers are not listening, that Ubuntu devs do not care about them and that becomes a grudge. That leads to looking for alternatives instead of exploring kubuntu or ubuntu. If you look at distrowatch, anything ubuntu related is going down, while Mint is growing a lot.

**And you guys in the forum should worry about it, even if you are fine with the current direction of events, because at the end Ubuntu is a business, and if it does not generate revenue in the long term, it will simply go away.**

Ubuntu has not generated revenue for Canonical for a long time and I'm not even sure if it already does. I'm not making a cent out of it (pretty much the opposite lol) and doubt anyone here does get a salary from Canonical. 

Current moves that make Ubuntu more acceptable for use by PC OEMs and (likely) other devices might change this scenario thou, driving growth in services revenue for Canonical. I'm cheering for that.

Anyway, it's Open Source. If Canonical go broke, Ubuntu will continue to be used, developers (not Canonical staff) will continue to develop, packages for Grub, Gnome, KDE, and mostly all we use in Ubuntu will continue to exist (as other distros use them too), etc. And even if it didn't: Most normal people will make a switch to Debian in like 1 hour and continue to use the PC the same way. And tell me how Mint will do without Ubuntu?

See, Canonical is a business, Ubuntu is a Linux distro. This is Free and Open Source Software. Your affirmation makes no sense. But thanks for the free terror attempt.

---

### Post by cariboo on 2011-11-09
> **reduz said:**
> Yes, people is moving on.. to other distros, as can be seen here: [http://distrowatch.com/](http://distrowatch.com/)
Fedora and Mint are becoming much more popular.

Ubuntu is very clearly becoming a negative brand for a lot of users. This is extremely dangerous to any kind of business, and will definitely affect future products (phone or wathever).
The more time it goes on, the more irreversible it becomes.

Users feel like Ubuntu developers are not listening, that Ubuntu devs do not care about them and that becomes a grudge. That leads to looking for alternatives instead of exploring kubuntu or ubuntu. If you look at distrowatch, anything ubuntu related is going down, while Mint is growing a lot.

And you guys in the forum should worry about it, even if you are fine with the current direction of events, because at the end Ubuntu is a business, and if it does not generate revenue in the long term, it will simply go away.

I'm getting a little tired of this using distrowatch page hits as a statistic that people are leaving Ubuntu. Show us some numbers other than page hits. If there really is a mass migration we need a little more proof.

Instead of standing on the outside making useless noises, why not join the community and help make things different.

---

### Post by robert shearer on 2011-11-09
> **cariboo907 said:**
> I'm getting a little tired of this using distrowatch page hits as a statistic that people are leaving Ubuntu. Show us some numbers other than page hits. If there really is a mass migration we need a little more proof.

Instead of standing on the outside making useless noises, why not join the community and help make things different.

cariboo907, I endorse your sentiments though feel compelled to bring some balance.

Ubuntu has been at the top of Distrowatch for, oh maybe since about 2005, and people have been quite happily  claiming that as proof of its top spot in the Linux world.

As upsetting as it may be to see and have others claim Mint's rise as being to the detriment of Ubuntu, and due to it's promotion of Unity, those sentiments can't be dismissed using the same reasoning that was previously held up in Ubuntu's favour.

As far as 'joining the community' I was under the impression that forum members **were** part of the community and robust debate was part of the process whereby users could provide feedback on Canonical's development.

Why else have a Ubuntu +1 the testing threads forum or releases other than LTS..?

As a Mod I know you must view endless anti and disgruntled posts but that goes with the territory.
Reflect on the happy users that find no reason to join or post here, they're both very happy.:D

Cheers, Bob.

---

### Post by effenberg0x0 on 2011-11-09
If Ubuntu was ranked last at Distrowatch, would it matter to any of you? Would it be reason for anyone to migrate to other distro? Are any of the efforts each of us did/do/plan on doing for Ubuntu targeted at increasing our Distrowatch ranking? :)

I can't think of anything less important than Distrowatch ranking. If 50% the Ubuntu user base decided to migrate to Mint, Puppy, Fedora, Slack, WhateverOS, it would actually be good to empower Open Source and give these distros a boost they may need.

Now, when a user says he will migrate to Mint because its pissed off with Ubuntu, I find it kind of ridiculous. At least go Debian, or change paradigm and go Arch, etc. But switch from Ubuntu to Ubuntu with a couple different packages is not a real switch, it makes no sense. It's like dropping Windows 7 Ultimate for Windows 7 Enterprise?

---

### Post by robert shearer on 2011-11-09
@effenberg > I can't think of anything less important than Distrowatch ranking.

Yeah, to existing **users** Distrowatch rankings are about as relevant and interesting as porcupine flatulence.

 Canonical,however, probably attaches a great deal more significance to them, as newcomers looking to migrate to Linux are generally inclined to go with a proven and popular distro.

---

### Post by robert shearer on 2011-11-09
Well, this is the most compelling reason I have yet seen for the non-movable launcher....
from [https://bugs.launchpad.net/unity/+bug/882274](https://bugs.launchpad.net/unity/+bug/882274)

> On 08/11/11 19:31, kfsone wrote:
> However: The direction and changes of 11.x *suggest* to us that Ubuntu
> is swapping from desktop to sub-desktop focus for it's primary
> distribution.

> Mark Shuttleworth (sabdfl) wrote 1 hour ago: 	#74
No. What's happening is that the new form factors are being integrated
into Ubuntu, just as they will be integrated into MacOS and Windows.
We'd just like to be ahead of the curve. Some day, you will be able to
carry a phone, and dock it to a keyboard, mouse and display and use it
as a full desktop with all your apps and data. Or use it as a tablet, in
a different dock.

Mark


---

### Post by effenberg0x0 on 2011-11-09
> **robert shearer said:**
> @effenberg 

Yeah, to existing **users** Distrowatch rankings are about as relevant and interesting as porcupine flatulence.

 Canonical,however, probably attaches a great deal more significance to them, as newcomers looking to migrate to Linux are generally inclined to go with a proven and popular distro.

I do IT market analysis and research for large global IT vendors everyday, it's what the company I work for do as its core business. I've been a field consultant in IT for many years. I can assure you no IT company decides a marketing strategy or present its investors with data from Distrowatch.

Besides, Ubuntu has already created, mainly unwillingly, a network of VARs and channels in IT Services that choose this distro when doing large implementations of Linux desktops and/or servers. You can be sure this is where the money is at. Do you think CIOs from large IT-dependent businesses, that manage 3.000 servers and more than 10.000 desktops are gonna make any decision to change distro in all their global sites based in Distrowatch?

The largest Data Center in LATAM offers Cloud and dedicated hosting based in Windows, Ubuntu and CentOS. You think they are gonna put Mint in their 15.000+ servers cloud?

Global, local OEMs targeted at domestic segment products: A local structure was developed at each country they operate, to provide support for Ubuntu. Software was localized, manuals were printed in each language, etc. You really think they'll switch this whole structure to use Mint?

Government implementations: Will use Mint? They already have Desktop and Support Outsourcing from many companies, Managed Security contracts, they invest who knows how many millions in 5-year contracts for these enormous implementations. And then they will switch to Mint?

Ubuntu is already an important part of a whole global business dynamics. You don't change that night to day and with no costs. Canonical is starting to realize they can make as least as much money as some of the companies that globally profit on Ubuntu. Which is good. 

Really man. It makes absolutely no sense. Ubuntu won't die or become less relevant because you don't like a launcher. It won't happen. If me, you and everyone else in this forum moves to Mint, the business part of it, in which the money is at, couldn't care less. We create no revenue at all.

---

### Post by reduz on 2011-11-09
> **effenberg0x0 said:**
> 
Now, when a user says he will migrate to Mint because its pissed off with Ubuntu, I find it kind of ridiculous. At least go Debian, or change paradigm and go Arch


As part of the Ubuntu community, I find your reasoning to be a little disconnected from reality.
If a "user says he will migrate to Mint because its pissed off with Ubuntu" (in your own words, and i guess we both aknowledge that this is a very common case scenario recently) the worst attitude you can do is close your eyes and ignore what's happening, while telling yourself and everyone else that you are fine.

I feel it's the same attitude of people who does not get concerned with politics, war, poverty, aids, etc because it's not affected or feels far from it. While we are talking about operating systems, (something luckily not as relevant or terrible), this is still a community and we should not escape or ignore the problems happening on it.

Reality is that users are pissed and leaving Ubuntu in large numbers. Canonical, still resting on laurels. is being slow to react to this, instead announcing phone and tablet versions of the OS. This seems to have further pissed off the community (read the comments on pretty much any tech site), which seems to believe that Canonical no longer cares about them.

This whole thread is proof of canonical's lack of interest in offering more configuration options to the users, instead trying to evangelize on an one true way. 

Not everyone is fit to be a dictator, and Mark Shuttleworth failed at playing Steve Jobs.

---

### Post by cariboo on 2011-11-09
This thread has drifted so far of topic, it might just as well be closed. We are here to discuss Precise, and solve problems, not what we think of the Unity or gnome shell, or any of the other topics that have been touched on. 

I'll leave this thread open for a couple of hours, so anyone that wants to can get in their final say, and then I'll close it.

---

### Post by reduz on 2011-11-09
> **cariboo907 said:**
>  We are here to discuss Precise, and solve problems

I think we are doing exactly that. Forum description:

> 
This forum is for the discussion of the development of the next version of Ubuntu (Precise Pangolin). Precise is in development and will be released in April 2012.


So far this thread has been about the direction Unity is taking. If you, as a forum admin, believe that some aspects about the future version of Unity can't be discussed, such as political ones, them please specify it in the subforum description, such as:

> 
This forum is for the discussion of the development of the next version of Ubuntu. Please talk about the shinny new art or the packages added or removed. Don't talk about politics or voice your negative opinion or disconformity about the future of Ubuntu (and much less mention Linux Mint, because this is about Ubuntu), else this thread will be closed.


^ That would fit better.

---

### Post by 23dornot23d on 2011-11-09
What the general user have seen as changes done by the developers UNITY

1 no longer crashes
2 is resizeable and transparent
3 text has been added to give visual indications of what they are clicking on.
4 icons drag and dropped into place.

What the general user as asked for

1 Customization and moving of the dock to all 4 places other docks go to
2 an additional icon on application windows to easily switch global menus on in the app window.
3 for dual screen the dropdown on the right

What have the USERS done to try to address their own problems with UNITY

1. made the UNITY dock go to the bottom now
2. also added the cardapio drop down to work on one or both screens ( for dual screen users )
3. turn global menus off completely - to try to overcome a inherent problem for *(dual screen and large screen users)
4. They sometimes resort to using a different Desktop
5. They sometimes resort to moving to a new Distro
6.  One day someone will understand problems from a general users point of view - (instead of thinking its easy for us to do it all)


I see so many USERs wanting to get there points across to the developers and in shear frustration of the threads closing or being moved into the recurring discussions never to be seen again ........

I ask you one question ...... do you believe by sweeping everything under the carpet
and forgetting about users that are trying to help get the best results from this you
are doing UBUNTU any justice as the leading Distro .....

And once you drop lower down the ratings ...... maybe the USERs will start ignoring you.
Closing the other place where they could discuss it in recurring was a real bright move too ... to point them 
to a closed thread ....

---

### Post by Elfy on 2011-11-09
Thread closed.

Thanks for participating.

---


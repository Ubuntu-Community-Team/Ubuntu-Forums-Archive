---
title: "Wine Jargon Regarding Adobe CS4 is Confusing Me"
date: 2009-02-03
forum: Wine
---

### Post by kasperbs on 2009-02-03
Hi,
In my ignorance of serching for the proper forum to post this, I originally posted it in the general help section. I couldn't understand why no one came to back to me, but know I see that I have posted in the wrong forum. But here goes my original question.

I'm currently looking to find a way to use Photoshop CS4 under linux mint. Before using VirtualBox I would like to give Wine a try but have some problems understanding the directions given for a successful install.

I found a few successful attempts on WineHQ but I need someone to explain a few things for me.
First Justin Riley [submitted this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=36559")
> CS4 runs great after being patched. Patching Wine requires compiling Wine from source and applying the patches while doing so (Of course).
[URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=34703"]
Tom said:[/URL]
> I only needed "winetricks gdiplus".

[Mikk Tendermann said]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=33277"):
> After having a problem with AMT subsystem I realized that it was missing a service. I added it manually and BANG works like a charm
does not work until start the service

I have absolutely no idea of what either of these guys talks about. If anyone can offer any help, it would be much appreciated.

I know it's a few questions in the same post, but I thought that an answer to one of them would be enough to get me running.

---

### Post by alex.rayu on 2009-02-03
They guys who make wine are geeks. And they think that if they can easily patch it and get dozen of winetricks stuff in console and then it works so everybody else can and they assign gold to it and it confuses normal people because they think that the wine they get from repository will run fine, which it won't.

Mike Tandermann added a service manually (!) and BANG we all can do it as well. Why not we all just recompile the kernel with wine support in it - everybody knows how to do it! 

It's a shame! No application should be assigned anything else but "CRAP" unless you can install and run it decently in the wine you get from the official web site, without having to do shaman dances around it. And the way it's now it's just a shame and is extremely confusing. 

CS3 is not installable in wine, not even with winetricks and gdiplus and msxml6. I reported it as crap, and the total ratings went to "Silver" . Which tells me it is installable and should actualy run. Which it may, if you manually copy registry and other stuff. It's as if Vista developers said "Vista is stable. Just copy your registry from XP, add a patch or two, and BANG - you will be amazed!" They would be hung the next day.

---

### Post by trishacupra on 2009-02-03
Shaman dances - that is so exactly what it requires.

I am a geek. I love geeks. I understand my fellow geeks. But us geeks need plain normal folks, even Luddites like my poor husband, to test geeky stuff and un-geekify it.

---

### Post by alex.rayu on 2009-02-03
I am not as geeky as other geeks are, though I know C++ syntax well enough to manually apply the git patch to files without making a git repo, and I can (and do) download and use winetricks. But Linux should STOP targeting geeks! It should STOP being a system that thinks of it's potential users as ones who can compile and patch stuff. Actually, it should think of it's users as of people, who have been using Windows, and now have installed Ubuntu with wine and they want to know what will work and what not. And if they read that CS4 is Golden on Ubuntu, and they try to install it in wine and it won't even install without lots of other things, it's a misservice to call it Golden. It turns people away.

---

### Post by Vadi on 2009-02-03
@kasperbs: it seems Tom's solution is the easiest, as that involves running a program that "should make it work". But it might not since others have posted varying solutions of greater difficulty - so unfortunately, for now, I think you should just give skip CS4 in wine and use Virtualbox.

---

### Post by kasperbs on 2009-02-03
> **Vadi said:**
> @kasperbs: it seems Tom's solution is the easiest, as that involves running a program that "should make it work". But it might not since others have posted varying solutions of greater difficulty - so unfortunately, for now, I think you should just give skip CS4 in wine and use Virtualbox.
Yeah I thought about using VirtualBox but I'm just thinking that it won't run properly due to the fact that I can't use my graphics card properly. But I will give it a try Or I will just have to dual boot which would be a pain.

---

### Post by Vadi on 2009-02-03
I don't think CS4 relies on the graphcs card too much, it should work fine.

---

### Post by hikaricore on 2009-02-03
> **alex.rayu said:**
> They guys who make wine are geeks. And they think that if they can easily patch it and get dozen of winetricks stuff in console and then it works so everybody else can and they assign gold to it and it confuses normal people because they think that the wine they get from repository will run fine, which it won't.

You should probably check the chip on your shoulder at the door next time.
If you want to provide others with info I'd much rather you did it without berating WINE users or the WINE development team.

The WINE Application Database is a user run site and prone to human error and oversight.
If you think you can run it better than it currently is, I suggest personally contacting the webmaster there.

---

### Post by trishacupra on 2009-02-03
Why don't they give a 'setup difficulty' rating as well as a rating for whether an app works or not?

---

### Post by gackt on 2009-02-04
here what tom propose

get winetricks "http://wiki.winehq.org/winetricks
type sh winetricks gdiplus "do it at the terminal"
install the CS4 with wine "just double click the installer

---

### Post by jrusso2 on 2009-02-04
> **kasperbs said:**
> Hi,
In my ignorance of serching for the proper forum to post this, I originally posted it in the general help section. I couldn't understand why no one came to back to me, but know I see that I have posted in the wrong forum. But here goes my original question.

I'm currently looking to find a way to use Photoshop CS4 under linux mint. Before using VirtualBox I would like to give Wine a try but have some problems understanding the directions given for a successful install.

I found a few successful attempts on WineHQ but I need someone to explain a few things for me.
First Justin Riley [submitted this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=36559")

[URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=34703"]
Tom said:[/URL]


[Mikk Tendermann said]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318&iTestingId=33277"):


I have absolutely no idea of what either of these guys talks about. If anyone can offer any help, it would be much appreciated.

I know it's a few questions in the same post, but I thought that an answer to one of them would be enough to get me running.

You should really consider running virtual box again if you have Windows you can use.  It runs much better on real Windows that it ever can on WINE.

---

### Post by jrusso2 on 2009-02-04
> **trishacupra said:**
> Why don't they give a 'setup difficulty' rating as well as a rating for whether an app works or not?

My experience is the more complex the app the worse it runs in WINE.  I have been able to get simple things like DVD rippers to run well.  But Office 2000 which is a Platinum rating does not even run.  It starts and asks for registration over and over.

Same with Windows games and Photoshop CS versions.  Lotus Notes 6.5 has a high rating but I could never get it to do more the throw up the splash screen and crash.

---

### Post by alex.rayu on 2009-02-04
> **hikaricore said:**
> You should probably check the chip on your shoulder at the door next time.
If you want to provide others with info I'd much rather you did it without berating WINE users or the WINE development team.

The WINE Application Database is a user run site and prone to human error and oversight.
If you think you can run it better than it currently is, I suggest personally contacting the webmaster there.

While critical, don't see how it was berating, especially to users, whom I actually encouraged to wait and give WINE another try later. But I kinda got the idea. You're the forum authority here and I will take heed.

---

### Post by trishacupra on 2009-02-04
My personal experience:

I was a Windows user. Then I discovered Ubuntu and became a dual-booter. I only used Windows for Photoshop. Then I set up Windows in Virtualbox for Photoshop. I even got CS2 miraculously working in WINE due to 'Shaman Dances'. Though it didn't completely work in Ubuntu, so for anything more than a 5 minute job I'd have to fire up Windows.

Then I got completely sick of Windows so when my laptop died I bought a Mac and I use it for everything, with Photoshop working perfectly.

My Dad and I resurrected my PC laptop a year after it died. I'm now setting up Kubuntu and using it as a media center and for the Internet. And some kiddies games for my daughter.

Ubuntu is great for some things - for using the Internet, for email, for web-based apps, for simple word processing and so on.

I'm a designer. I need to use Photoshop and similar apps. So my work computer is a Mac.

There isn't One OS to Rule Them All. Ubuntu has its strengths. OS X has its strengths. Windows is a pile of garbage in my experience but I can understand people needing it for some things.

It's better to figure out what you need then choose the OS that best supports your needs, rather than trying to make an OS do things it's just not ready or able to do.

Best of luck to you.

---

### Post by alex.rayu on 2009-02-05
You see, I have been in Linux for a few years now. Precisely because I saw  that it was trying to develop from a closed-up red-eyed geek thing into a usable and intuitive OS. Using Photoshop is not about choosing OS. If Linux is just nothing more than internet and word editor OS, then it will never grow.

As you can see, despite all Vista flaws, Linux did not manage to grab the opportunity. Look around - the majority of who uses Linux are kids. When they grow up, they need to do real things, and they need a real OS. 

In all this, WINE is a key element. Wine is looks promising, because it says that Windows apps will be running on Linux. And saves the day for Linux. While there are no funds to sponsor any significant Open Source software, at least Windows proprietary software can run, in most cases. WINE is what has two key groups of people - the youth, who play games, and the serious people who use programs like Photoshop. 

I have been trying to say, that if Linux wants to make it's way up, it can't allow itself to have bad design, or bad functionality, or be misleading, on basis that it's free or that it's human and prone to errors. I saw in Ubuntu understanding of this. Mark Shuttleworth explicitly said, that it will pursue to be modern, usable, and competitive to Mac OS. May be some day, but I see that it's not ready psychologically. It's still too immature, mostly in attitudes towards good ideas and helpful criticism.

---

### Post by trishacupra on 2009-02-05
Okay, here's how I see it.

Windows is probably most popular because of Microsoft Office. It may or may not be the best office software, but it's the most common. Open Office isn't quite there yet.

Mac's are popular with designers like myself because it does design work well. It appeals to others as well, for sure, but this thread is about Photoshop so I won't go into that.

Linux is great for not getting viruses and for it's cost. It may be very suitable for geeks who do coding and stuff like that, as well as for people who just have very simple computing needs.

Linux and Ubuntu need to figure out who exactly they're appealing to, and go in that direction. Not try to be all things to everyone. Nothing wrong with being aimed at geeks.

---

### Post by alex.rayu on 2009-02-06
That's true, except that geek system is what Linux has always been. Nobody needs to do anything for it to remain what it has been. But one day people like Mark Shuttleworth come up and say - "Hey, it's a good alternative. Why not take the basic system, brush it up, make it usable for non-geeks, and change the world for better, break M$ monopoly, get a free and usable system." Mark invests money, and the work begins. 

I would have never used Linux if it still were what it was - a red-eyed geeks os. I have no desire whatsoever to spend time manually tweaking things and doing shaman dances where I could just start Photoshop and do my work. And so majority of people. But when I see people like Mark investing and others inputting to make it a usable good product, I feel cooperative. 

But what I am saying is that since there *are* people who want to do it, there *are* people who want to invest in it, then whoever tries to bring the old red-eyed way of thinking back in it, is actually opposing in essence what they are doing. 

In the case here, I am not berating WINE or it's users. What I am doing is I am pointing out, that the approach taken is in opposition to what Ubuntu project is declared to aspire to. Moreover, it pushes away people who are disappointed, while in fact, human oriented approach should try to heed the complaints and make everything user-friendly, not geek-friendly. 

In our case, the report for WINE 1.1.12 would go like this:

```
Photoshop CS4. Rated: Garbage. Does not install.
Advanced remedy available. Requires: patching the git branch and winetricks. Click here to read more.
```

And this opposition is everywhere. Every time somebody makes excuses that it's ok for the product to be low-class, because... (I am not paid/ It is community supported/ whatever else) - it's a blow to the whole thing.

---

### Post by kasperbs on 2009-02-06
I have now tried to install Photoshop on Virtualbox and it doesnt' run very well actually. I have it installed on WinXP 32bit and given virtualbox 1800MB ram and enabled 3D graphics. Unfortunately it lags quite a lot even with small files, for that's <10MB.

I use PS for web design mockups so the files can get quite large. I think my bet will be to dual boot and leave PS in VirtualBox if I need something done quickly, but I think I will just have to bite it.

I guess the best solution would be to et a second machine with MAC and run the graphical programs there and then do my coding in Linux. But then again, is Linux really worth that then I could as well run Mac only.

Oh boy would I love Photoshop for Linux, why don't Adobe set up a donating program to see if they can raise the cash?

---

### Post by trishacupra on 2009-02-06
Personally, I was exactly in your shoes - PSD mockups for web designs - dual booting.

Getting a Mac was the best decision I ever made. Photoshop runs like it was made for Mac - oh wait, it was. :)

Ubuntu/Kubuntu makes a good second computer, though, if you have an older PC/laptop around.

As a designer, you may like Kubuntu a bit better - just the way it looks.

I prefer coding in Linux, but I don't do that much of it. There are a couple of freebie apps for Mac that are okay, and some heavy-duty paid ones.

If you have enough money to throw around, I would recommend getting a Mac for designing and use the PC with Kubuntu for coding.

---

### Post by kasperbs on 2009-02-07
I have been thinking about getting one for some time, but every time it just feels like too much just for one single program. And really that's the only thing I would get it for, every thing else I can do in Linux.

Anyway this is written from my windows os, the dual boot thing worked great and Photoshop runs perfect. Now I just have to finish that mockup so I can get back into my comfort zone ;)

---

### Post by Bios Element on 2009-02-07
> **trishacupra said:**
> Why don't they give a 'setup difficulty' rating as well as a rating for whether an app works or not?

They do. That's a rating. A gold rating is generally for something that requires some console setup and dll files. A Platinum rating is one that works outta the box. (Or very near so.) The war going on here is stupid. None of that was overly complex to learn from a quick google. So instead of flaming WINE, Linux and everyone you see, Why not just help him figure out what they're talking about so next time he can do it himself.

---


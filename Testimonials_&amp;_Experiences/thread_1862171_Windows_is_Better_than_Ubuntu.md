---
title: "Windows is Better than Ubuntu"
date: 2011-10-16
forum: Testimonials &amp; Experiences
---

### Post by MSklaroff on 2011-10-16
UBUNTU NIGHTMARE:
Why Ubuntu Makes Windows Look Good

I've always hated OS X. In fact, the only thing I've hated more than OS X is Windows. I could ramble on about OS X's poor update schedule and customizability, or Windows' vast security flaws and failures to adopt even the most mundane technological improvements (Why the heck is it still using the same file system after 20 years?), but that would detract from the focus of this essay.

Enter Linux. Reliable. Secure. Customizable. Diverse. Free. And I would be remiss if I didn't mention that it has the greatest tech community in the world. It is the perfect antidote to Windoze or OS eXasperation. The only problem is deciding amongst all of the fantastic distributions. About a month ago, I decided that when my new laptop arrived, I would try Canonical Ltd.'s Ubuntu operating system.

In a million years, I never thought that any Linux distribution could make Windows look good.

….

Using a Windows computer at work, I followed the instructions to make an Ubuntu USB drive. As every potential Ubuntu user should do, I first tested Ubuntu Live on my hardware to make sure it would work. Everything appeared to be alright, superficially. Indeed, many of the problems I would encounter could not be have been discerned from a briefly perusing Ubuntu Live. Even so, any encountered problems would not necessarily be indicative of the full installation experience, since many bugs can be Live-edition specific. There are at least hundreds of such bugs ([https://bugs.launchpad.net/ubuntu/+source/casper](https://bugs.launchpad.net/ubuntu/+source/casper)).

I then decided I would go through with the full installation. Apart from some odd quirks with login name selection (Why on Earth can't I have a login name that begins with a capital letter?), Natty Narwhal's installation on my new laptop went smoothly.

Or, rather, was the only thing that went smoothly.

I decided to watch a YouTube video, and noticed that playback was stuttering a bit at 1080p. I checked the “Additional Drivers” application, and sure enough there was an Nvidia driver for me to download. Why Ubuntu has no feature to notify me of this is beyond me, considering that a nonfunctional graphics card is probably one of those things that should be on a need-to-know basis. Just a little bit.

So I downloaded and activated the driver. Upon the required restart, I got a message saying that my graphics card was not powerful enough to handle the standard graphical interface, Unity 3D. The interface I had just using on my crappier integrated graphics card. On a $1000+ laptop with an Nvidia GT 555m. 

As it turns out, Ubuntu has trouble using any switchable graphics card on the Intel Sandy Bridge platform —which means that Ubuntu doesn't work out-of-the-box for virtually all modern laptops with discrete graphics. Even worse, despite being unable to use modern Nvidia graphics cards, Ubuntu can't turn them off, either! So my brand new Optimus laptop now only gets about half its tested battery life.

Apparently, the only way to get these Nvidia video cards working at all in Ubuntu is to install and configure a hack called Bumblebee, which is only a stopgap measure at best: You still can't turn off the discrete card when you aren't using it, it is far slower than a native driver, and it lacks support for almost all modern features of graphics cards (tessellation, etc.). After much toil and research—and too much time spent in a command prompt—I got Bumblebee working. You still have to manually modify each program's launch command for it to work. I know that Canonical blames the issues on Nvidia keeping its drivers closed-source, but couldn't they have devised some way to turn off the discrete graphics card? Would that have been too much to ask?

Unfortunately, this small victory was short lived. I obliged the pop-up from Ubuntu's X Server application, which instructed me to generate an xorg.conf. Doing so also prevented Ubuntu from booting next restart. And while I was frantically trying to mend things in the command line, red error messages flashed onto the screen: The swap space could not be accessed, “recovery impossible,” So I used my USB drive to wipe everything and go through this process all over again. Once I (sort of) fixed my problems with my graphics card for the second time, I finally got Unity 3D enabled. 

I wish I hadn't. 

Before I decided to install Ubuntu, I had vaguely read about people rabidly complaining about the Unity interface, yet all I could think to myself, was “*Sigh*, there goes that crowd that always overreacts to small changes in free services. How bad could Unity really be?”

The answer happens to be I-want-to-slam-my-head-into-a-wall-until-I-forget-my-frustration bad.

Unity is clunky, buggy, and needfully unintuitive, but you don't have to take my word for it. In fact, Unity failed Canonical's own usability tests! If you are using Unity right now, these grievances should sound awfully familiar ([http://design.canonical.com/2010/11/usability-testing-of-unity/](http://design.canonical.com/2010/11/usability-testing-of-unity/)). Why do they sound familiar? Because most of those usability issues are still present in the final release! I only decided to enable Unity because Canonical announced that it was discontinuing alternative interfaces in future releases. I was also naïve enough to believe that Canonical would address Unity's failures from their own evaluation. How stupid of me.

With Unity, I had the most bizarre issues I have ever had with technology.

Apparently, the Ubuntu 11.04 features list didn't include a gremlin that randomly resets changes you make to Unity's settings every reboot. Shortcuts I had pinned to the sidebar would often disappear, change order, or sometimes remain but lose their icon. Even some of the new applications I installed lost their icons in the quick-search dashboard. 

After giving up on having any semblance of satisfaction with my sidebar, I decided that I would blow off some steam by downloading a few Ubuntu themes. I dragged them over the “Appearances” window to add them as available options, and clicked on each one to try them out. Yet as I tried each theme, the ones I tried previously would disappear from the selection menu. And when I would switch back-and-forth between default Ubuntu themes and downloaded ones, it would sometimes produce some sort of hodgepodge between them. The kicker: Ubuntu wouldn't let me reinstall the deleted themes from the menu.

Even if it weren't buggy, Unity is such a huge step backwards: Why can't I move the Unity panel on the left side of the screen to any another side of the screen, which is as easy as a click-and-drag in Windows and GNOME? Why can't I see a simple list of all my programs if I want to like any other popular interface? Why can't I remove the “Desktop Switcher” icon from the sidebar when I don't ever switch desktops? Why can't I have a simple pop-out application menu by program type? Why can't I see the menu options for each program until I drag my mouse over the bar? Even if the above settings come as the defaults, why is there no way to change these preferences?

Then something unbelievable happened while I was typing a word document: Ubuntu froze. Screen-and-mouse-not-moving frozen.  Now, on any other operating system, this would be a regular, if not mundane occurrence. But Linux is famously stable, which is why the majority of computer servers use Linux. Linux machines can go years without rebooting ([http://counter.li.org/reports/uptimestats.php](http://counter.li.org/reports/uptimestats.php)). After a few seconds of my frozen screen, Ubuntu took the liberty of shutting itself down. I wouldn't have mentioned this if it were a singular occurrence. No, this continued to happen on about a twice-daily basis, even while no applications were running. At least Windows gives you a “Blue Screen of Death” that tells you what happened when it crashed. Ubuntu would just spontaneously shutdown. In retrospect, I should have seen this as the warning sign it was, and immediately switched operating systems.

But hindsight is 20/20.

After giving up on Unity, I decided to set up the Empathy IM client with the only IM service I really use, Google Talk. I decided to make a video call to my friend, but kept getting errors each time: Sometimes it was “Could not link source,” and other times “Call engine failed.” Ditto for incoming calls, and for audio-only calls. You know a piece of software is junk when even the error messages are awful. I scoured the debug script with a fine-toothed comb, and Googled every “tp” error that I had received. I found plenty of bug reports citing the same problems, but no solutions from either Canonical or other users. 

I literally spent hours trying every combination of ports, security settings, installing/disabling/uninstalling codecs and packages, but all to no avail. 

I will only summarize my problems with the default Ubuntu email client, Evolution, as “Satan in software form.” Nothing it it worked. Ever. It was an abortion of a program. Plenty has been written about it, and at this point there is nothing much to say about it that hasn't been said. There was an Ubuntu forum thread discussing Evolution that so violently savaged the software, the forum moderators actually shut down the thread, warning that it was no longer “constructive.” Personally, I think the very fact that this happened at all is quite constructive, especially when considering the thousands of other users who took the time to complain about Evolution on the Ubuntu forums. 

As I continued to clear Ubuntu's swollen temp folders, I noticed that the amount of available space on the partition wouldn't increase. Here is another “feature” I learned about Ubuntu: It doesn't automatically support solid-state drive delete commands (TRIM), which if left unfixed would make SSDs unusable into the long run. Indeed, I had to perform yet another trek through the innards of the operating system (“fstab”) and Internet to figure out how enable/test TRIM commands. Even modern Windows and OS X automatically enable TRIM commands. I am thankfully a bit luckier with technology than the average user, but how are basic users with no programming experience supposed to figure this out? Considering that almost all new netbooks use SSDs and many newer laptops do too, this is a gargantuan problem. Could Ubuntu have at least given me a pop-up warning me to enable TRIM manually? Is that so much to ask?

Like a cultist awaiting his messiah, I yearned for 11.10 to save me from the 11.04 Antichrist. I kept telling myself “Surely the Oneiric Ocelot upgrade would address the bugs and flaws of Natty Narwhal, if only I can just hang in there a few more days” I literally counted the very seconds until version 11.10 would be released. I must have visited the Ubuntu 11.10 countdown website four times each day ([http://thisisthecountdown.com/](http://thisisthecountdown.com/)).

When Oneiric Ocelot was finally released, I almost could have cried for joy. But by the end of the day, I almost could have cried out of frustration. 

Three-quarters of the way through the upgrade, the install wizard quit with errors. Out of the multitude of errors to have occurred, one in particular caught my eye: Apparently, the upgrade wizard didn't seem to like my “fstab” file. You know, the same fstab file I had to modify to be able to use TRIM commands on my SSD?

The botched upgrade bricked my hard drive on reboot. “Bricked” as in “My hard drive now has more in common with a simple red brick than with a computer's data storage device.” I couldn't get to a command prompt at all at this point, and I couldn't even mount the partition when I booted into an operating system on my USB drive. So what else was there to do but to wipe my hard drive and use my Windows computer at work to make an Oneiric Ocelot USB flash drive installer.  

If only my problems ended there.

The first thing I noticed is that my battery life, already halved since Ubuntu is unable to turn off the discrete graphics card it can't even use, was even shorter! Much shorter. Even though Linux kernel 3.1 has been available for months before this Oneiric Ocelot release, the geniuses at Canonical decided to use kernel 3.0 to build their next Ubuntu version—which has a widely known bug where it makes computers consume over 30% more power at idle. This is definitely a problem when the majority of computers sold in the world today are laptops. Between Ubuntu's problems with discrete graphics and a kernel that consumes over 30% more power at idle, any laptop above entry-level will be lucky to endure much beyond the length of a single college lecture, if that. In light of this, why couldn't the 11.10 release have been pushed back? Or perhaps have taken some time to mend any one of the hundreds of flaws in 11.04, still well within Canoncial's alleged “18 month” support window ([https://help.ubuntu.com/10.10/about-ubuntu/C/index.html)?](https://help.ubuntu.com/10.10/about-ubuntu/C/index.html)?) Or maybe have used kernel 2.9 for one last release? Or even have done something special for laptop users? Anything?!

Oh, and I couldn't get the Bumblebee hack to work on 11.10. So now I couldn't use the discrete graphics card at all while it still sucks power. Wonderful.

Filling out system forms for passwords and the like was still error-prone. I often need to restart wizards because they do not detect my entries and kept the “continue” button grayed out. And my problems with Empathy got worse. Before, I could reach the make/receive calls window, but the call would fail; now I couldn't even initiate a Google call with Empathy, receiving the message, “There was an error starting the call.” Can you please be a bit more specific? Because that time the debug log was free of listed errors.

The best “feature” of 11.10 is that it hadn't been freezing like 11.04. Yet. It would seem you can't know for sure with Ubuntu. 

My problems with Empathy aside, I'm sure that gobs of glitches were fixed in the new 11.10 release. It is then such a pity that I cannot tell you about them: The power consumption issue was such a deal-killer that I decided to install a different operating system.

As for my emergency flash drive using 11.04, it failed to boot into Ubuntu after I installed updates and programs on it. Even tinkering with it on another computer could not fix it. So much for being an emergency boot device.

So after my nightmare experience with two consecutive versions of Ubuntu, an old saying comes to mind: “Fool me once, shame on you; fool me twice, shame on me.”

….

How much did I revile my experience with Ubuntu? Enough to spend the time writing this TL;DR essay about it. Yet after reflecting on the above, the first thing that comes to mind is this:
[http://cdn.someecards.com/someecards/usercards/1294528155051_a.png](http://cdn.someecards.com/someecards/usercards/1294528155051_a.png).  

[IMG]http://cdn.someecards.com/someecards/usercards/1294528155051_a.png[/IMG]

This is obviously true to some extent, but I think there is a higher purpose buried in this rant, somewhere. 

If you think I am unfairly singling out Ubuntu and being one-sided in my harsh criticism, it is because I am: Whether you like it or not, Ubuntu is the most prevalent Linux distribution ([http://www.ubuntu.com/news/eWeek_and_DesktopLinux_declare_Ubuntu_the_Champ](http://www.ubuntu.com/news/eWeek_and_DesktopLinux_declare_Ubuntu_the_Champ)), and its dominance makes it the “face” of GNU/Linux.  Clearly, Canonical is aware of this. Odds are, most who will ever know anything of, or do anything with, a Linux operating system, will do it with Ubuntu. As the “gateway drug” to the larger Linux universe, Ubuntu has a responsibility to the Linux community to make a positive impression and set a good example for the OS.

What might be an Ubuntu image problem today could very well be a Linux image problem tomorrow—if not already right now.

How many others, who know nothing about GNU/Linux beyond Ubuntu, could have tried 11.04 and swore never to use Linux again?

There is a strong case to be made that even non-Ubuntu users should care tremendously about Ubuntu's progress and performance. And Canonical should care about user and non-user frustrations, too.

Or, that's what the little Angel on my right shoulder is telling me, anyway. The little Devil on my left shoulder is yelling at me that Canonical is a private, profit-seeking company with no responsibilities to anyone else other than to its shareholders. Normally, I too would agree, and that would be that.  

But I think that's wrong for at least three reasons: 

[INDENT]1. That's not how Canonical is billing themselves to either the Linux community or the public at large. Take a look at the Ubuntu blog ([http://planet.ubuntu.com/](http://planet.ubuntu.com/)) to see what I mean. It isn't scientific, but I think the most-used noun is “community.” Everything from the image and utopian names, to the founder's own aspirations ([http://www.youtube.com/watch?v=eVg6Dsg-L3o](http://www.youtube.com/watch?v=eVg6Dsg-L3o)), it is clear Canonical is endeavoring to live up to lofty, commendable ideals. Ubuntu practically bleeds rainbows and unicorns.

In fact, I can't praise the ideals of both the founder and the company enough. They know that we members of the open software community eat that idealistic crap up, so its perfect marketing on their part. The very name “Ubuntu” means “humanity towards others” ([https://help.ubuntu.com/10.10/about-ubuntu/C/about-ubuntu-name.html](https://help.ubuntu.com/10.10/about-ubuntu/C/about-ubuntu-name.html)). 

It is obvious that fixing its product would better serve Canonical's noble goals, and I think that its ambassadorship of the Linux community is something it wants to take seriously.

2. Regardless of whether the idealism is genuine, Canonical is a private company that needs to make a profit at some point or another. The employees need to be paid, rent needs to be covered, and investors need to get their money back. That profit won't come unless Ubuntu is widely adopted. And that means that non-technical users will have to be able to intuit and use Ubuntu as effortlessly as they use other operating systems.

Fortunately, I was able to power through many of Ubuntu's problems with a little tech savvy and much help from the greatest software community in the world, but the level of technical tinkering and patience cannot be expected of casual adopters (e.g., converts from Windows). From my experience, LibreOffice was the only major application included with Ubuntu that did not  require interaction with a command prompt in order function. Almost every other major application in Ubuntu required tinkering—even its interface! Not in order to function well. Not in order to function customized. But in order to function at all. Again, you can't win people over from Windows, when, at a bare minimum, all of the default programs bundled with Windows function okay out-of-the-box. 

Yet as of right now, Ubuntu is “pricing” itself out of the market—especially out of the fastest-growing PC market, laptops. It has SSD issues that afflict netbook users and high-end laptop users, graphics card issues that afflict all but entry-level laptops, power-drain issues that afflict all laptops, and software usability/reliability issues that afflict all computers. Who else is left?

3. Canonical has made incredible partnerships with some of the largest, most important companies in the world, such as IBM, Dell, and HP ([http://www-03.ibm.com/press/us/en/pressrelease/28649.wss](http://www-03.ibm.com/press/us/en/pressrelease/28649.wss), [http://www.zdnet.com/blog/open-source/canonical-dell-bring-private-ubuntu-clouds-to-servers/8200](http://www.zdnet.com/blog/open-source/canonical-dell-bring-private-ubuntu-clouds-to-servers/8200), [http://h18000.www1.hp.com/products/servers/software/ubuntu/index.html](http://h18000.www1.hp.com/products/servers/software/ubuntu/index.html)). Clearly, Canonical wants to play with the big-boys. But if it wants to successfully play with the big-boys, it needs to start acting accountably like the big-boys. With so many reliability issues, how is Ubuntu supposed to gain a foothold in businesses and universities, or expect to serve any role in a mission-critical context? How is Canonical supposed to convince software developers that it is a platform worth investing it?

Unlike many others, I do not fault Canonical for attempting to transcend beyond GNOME by developing a new interface system. Much of Canonical's frustrations with GNOME were quite legitimate ([http://blogs.gnome.org/bolsh/2011/03/11/lessons-learned/](http://blogs.gnome.org/bolsh/2011/03/11/lessons-learned/)), and given the same situation, I think most would have made the same decision. Granted, there will always be numerous usage issues with the first release of a new interface system, surely as many as there were with the first release of GNOME. That said, this is no excuse for attempting to pass an alpha test as a final release. Only in its infancy, Unity 3D should never have been made the default interface of 11.04.

I can scarcely imagine how the laundry-list of stability/usability issues and bad press could scare away capital investment in Ubuntu-like projects, if not Ubuntu itself.[/INDENT]

….

In sum, the current state of Ubuntu is nothing short of an unmitigated disaster. The development process seemingly neglects the results of its own evaluations, and produces alpha-test results. Lord only knows what damage Ubuntu's stability/usability issues and bad press have done to the reputation of the open software community, and perhaps to Ubuntu-like projects on the whole. I endeavored to try Ubuntu with an open mind, as well as to lend it the maximum benefit of the doubt; all I can say, is that I feel like I've been slapped across the face for the past month. 

Canonical's ideals are quite admirable, but the company is sorely missing its target. For so long as Ubuntu remains hampered by such poor quality, Ubuntu will never sway many casual users from either Windows or OS X. As of right now: Ubuntu might be free, it still isn't worth the expense.

---

### Post by el_koraco on 2011-10-16
Huge wall of text!

---

### Post by fatality_uk on 2011-10-16
Errr... TLDR

Cmon, do you really think that baiting people with that much info will work? You need to be more punchy. Something along the lines of "Ubuntu is only used by people who worship the devil" etc.

I think as we are a nice, helpful community, I suggest any people posting here should provide the OP with good trolling lines to use.

---

### Post by TeoBigusGeekus on 2011-10-16
Linux != Ubuntu.
As a matter of fact, Ubuntu lately is not the most stable and user friendly distro in the linux world.
It's sad you didn't make it with ubuntu; you could perhaps try a different distro - there are hundreds of them: [http://distrowatch.com/]("http://distrowatch.com/")

Linux is a high tech, high performance tool.
As every high tech, high performance tool, it has a steep learning curve: you can't expect the same level of difficulty using a hammer and a car.
I'm sure that if you insist, you'll get a perfectly working system, tailored to your specific needs.

---

### Post by Rubykuby on 2011-10-16
I'm sorry you've had bad experiences with Ubuntu, but you must understand that this is not entirely Canonical's/the community's fault. Hardware suppliers don't contribute drivers and the like upstream to Linux, and thus every piece of software has to be reinvented. Hardware older than a year won't have this issue, as it's given Canonical/the community more than enough time to fix known and major issues. Hardware aged two years runs as smooth as can be.

Ubuntu worked out of the box for me. Hell, the only thing I had to fix was a resolution-related error in the login screen that popped up once in a blue moon. The rest just worked.

I hate to say this, but you shouldn't blame Ubuntu; blame your expensive hardware instead, which I believe is causing many problems for you.

---

### Post by Delever on 2011-10-16
> **MSklaroff said:**
> UBUNTU NIGHTMARE:
Why Ubuntu Makes Windows Look Good

In sum, Ubuntu is short disaster. Lord only knows what  stability/usability have done to Ubuntu-like projects.

You are worried what stories others have about Ubuntu. It is like worrying what others think about you. Usually, others do not give so much thought about you/Ubuntu as you would expect or want to believe.

Sorry about scrambled quote.

---

### Post by nothingspecial on 2011-10-16
Moved to Tesimonials.

---

### Post by Dangertux on 2011-10-16
Honestly, Ubuntu has problems everyone knows it 

That being said I find it highly unlikely that literally everything failed. Which leads me to the conclusion that one or more or the following three are happening. 

- you are trolling
- you have little to no experience with Linux or ubuntu and are wildly copying and pasting commands and changing settings without understanding what you are doing. Thus breaking your installation. 
- you are the least lucky individual I have ever seen.

Whatever the case sorry your experience was so bad , the beautiful thing is we aren't going to hold you prisoner to this OS

---

### Post by galacticaboy on 2011-10-16
You realize that posting like that will not get you answers or help, it will only get you mad people telling you why you should get hit by a truck that has Tux on it.

---

### Post by Thewhistlingwind on 2011-10-16
First of all, let me tell you that I think you hit the mark, in fact, I think you hit the mark SO on target that the target exploded into a cloud of confetti. You've certainly outlined some common problems with Ubuntu. However; I think Canonicals problems are in fact with how they present their product. 

To start, the "Recommended" download is the 10.4 LTS. But this isn't the first option presented to interested users. Instead the latest (Read: Alpha at worst or Beta at best) release is shown to the user for download. Even though the non-LTS releases are in many cases testing releases, they are not billed as such. And end up in the hands of people like yourself, trying to assess the quality of Ubuntu and finding the alpha horrendous. 

There is a new version, 11.10, which is supposed to be more like a beta than the alpha you just went through. There is also the LTS, which you may have more luck with. If Canonical wants to succeed, a simple change like offering users the 10.4 download first would be wise. (Simply to keep their rep up so they can market to OEMs.) I hope that one of those two options suits you better.

Also, for most of the users here. This stuff DOES work. So theres probably some hardware issues involved here too.

EDIT: Oh, you tried 11.10.

---

### Post by nothingspecial on 2011-10-16
And I think we'll leave that here.

Thanks all.

Closed.

---


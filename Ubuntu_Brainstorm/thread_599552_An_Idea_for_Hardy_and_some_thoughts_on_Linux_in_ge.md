---
title: "An Idea for Hardy and some thoughts on Linux in general"
date: 2007-11-01
forum: Ubuntu Brainstorm
---

### Post by Diggs808 on 2007-11-01
[MODS: Please move this if the thread is not the appropriate one to post this to]

One of the things I have been thinking abut lately is why I like Ubuntu and Linux in general and it really comes down to customization.  I like the idea that I can make my desktop my own (it costs money to customize Windows in the way that you want it).  I can make it look and function the way that I want it to...not the way some geek in an underfunded design department in Redmond / Cupertino (sp??)  thinks it should.  I like changing the look and feel of my menus to shape my mood....i think it is just awesome....

My idea is this....why cant we have an application as part of the installer that allows you to do some customization before everything is installed?  You know...change the wallpaper...change the icon scheme...give options to add things like a start menu (if you want it), maybe even change default system fonts.  You don't just stop at look and feel however...you can also choose which things you want to run at startup (such as bluetooth) and if you want to remove certain programs (like the games that I never play) or maybe add programs (stuff like a firewall or even codecs and other goodies).   This app would create a script that would be saved on the users desktop with a set of instructions (in plain english)  to run the script once the system was connected to the internet.  Of course there could be a version that could be run from the desktop (with an icon that maybe says Customize your Installation...or something similar).  Of course, the app could always be skipped by just choosing a check box that says Use Default Options.  

Looking at different distro's accross the web one of the things that just jumps out at me is that distros often end up playing catch-up to  Windows wherever or OS X pretty kitty.  The key to winning over hearts and minds was hit upon by Apple (and that is why they do so well ...in spite of their obvious drawbacks): not merely copying or even making a *nix version of an application or program, Linux needs to be innovating and making the big boys play catch up...not the other way around.  Remember surfing the web on a windows machine after Netscape and before Firefox?  Microsoft was content to push out a bug ridden, security nightmare posing as a web browser.  What Ubuntu/Linux needs to do is to give people a reason to leave windows other than security and the general suckiness of the product.  While security is of the utmost importance, Joe Six-Pack doesn't want to ponder the nuances of information security...he wants to look at his Fantasy Football information or watch stuff on YouTube.  One thing that Apple is proving is that you can sell computers by appealing to someone other than just the techno-savvy.  Make it innovative enough (or just pretend that you innovated it in Apple's case), pretty enough and people will snap it up.  While Ubuntu/Linux does not necessarily try to be Apple...their model works (look at their sales figures...numbers don't lie) Joe Six-Pack wants his friends to look at his laptop and be envious (just show someone your rotating desktop cube sometime...they will be severely impressed like my friends were).  I know that Linux, in its community design and support structure, has that ability ..heck...we have more programmers than Microsoft or Apple working on the code, improving it day by day.  Linux could innovate circles around them.  I mean...tabbed browsing(!!!), until Microsoft noticed that tabbed browsing was causing people to download firefox they rejected the idea.  Now look at them...they are constantly playing catch-up to Mozilla...not the other way around.  Personally I wish I had the ability to code...I really do!  If I could code and write I could take some of the ideas floating around in my head and get them out there...alas I am more of a dreamer than a doer and that means while I have big ideas...I have no way of putting them out there other than a hypothetical. 

Just an idea from a dreamer....

---

### Post by 23meg on 2007-11-01
Moved to Ubuntu Idea Pool.

[QUOTE=Diggs808]My idea is this....why cant we have an application as part of the installer that allows you to do some customization before everything is installed?[/QUOTE]

[http://ubuntuforums.org/showpost.php?p=3582999&postcount=3](http://ubuntuforums.org/showpost.php?p=3582999&postcount=3)

---

### Post by Kow on 2007-11-01
I believe in what you posted and I also do believe it is Ubuntu's primary goal:
Linux for the novice desktop user. This user to me is the one who just wants to browse the net, watch some movies, play a game or two, send out some emails... play some music.

The problem with customizing during installation is this. Lets say John Doe makes a ton of customizations and one of those customizations happens to break X11 or conflicts with another. Whats worse than breaking your OS? The OS being broke from the start. To make matters worse, what if this was his only computer and he has no other resources to utilize to fix the problem. In all likelihood he'll turn away from Ubuntu because it didnt work, and may or may not turn a lot of others away from Ubuntu because it did not work.

The point is, with a set Ubuntu installation the user is almost guaranteed a working Ubuntu environment to begin with because the releases are tested extensively during development. Now that John Doe has a base install he can go ahead and customize. Now, I am not saying there should not be a customization option during install at some point in the future but for Hardy, being a _stability_ release, no.

And with regards to Linux playing catch-up with Windows/Apple I agree to a certain extent. Linux takes some ideas from other OS's but these OS's also take ideas from Linux, so its a trade-off. This is where users ideas come in (such as yours.) Ubuntu is definitely headed in the right direction to give Windows some great competition. The main reason I believe a lot of users do not turn towards Ubuntu from Windows is the lack of support for it (Adobe 64-bit flash = nonexistant, games like bf2142, hl2, etc (wheres the native linux support?)). Now it becomes apparent what the problem is: Windows users do not want to switch to Ubuntu due to the lack of support for certain things they want (such as a game like bf2142), but the software/game/etc developers do not want to waste time on Linux because there is no user base to support the extra resources that would be needed. It took an enormous amount of linux user complaints to get ATI on board with good proprietary drivers for their cards (however, I think AMD had something to do with this after they bought ATI.) Another issue stems from the fact that Linux is open source and games, adobe flash, etc are not. This makes it very difficult for a limited number of developers who work on the closed-source to keep up with the dynamic environment that is Linux. With Windows, developers know once their driver works with XP it will always work with XP because XP is static (i.e., the kernel is always the same). Now in Linux companies such as Intel, ATI, nVidia have to constantly update their drivers as the linux kernel evolves. A great example is that the 8.37 ATI drivers (I believe this is the version) will not compile against a kernel > 2.6.22 due to something as simple as a useless function parameter being removed (I believe it was the kmem_cache_create function which had 6 parameters now only 5.)

---


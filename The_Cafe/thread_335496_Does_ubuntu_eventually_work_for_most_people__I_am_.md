---
title: "Does ubuntu eventually work for most people?  I am feeling a little discouraged."
date: 2007-01-10
forum: The Cafe
---

### Post by tc101 on 2007-01-10
Does ubuntu eventually work for most people?  I am feeling a little discouraged.  

I love the idea of open source free software.  I really want to switch from windows to ubuntu and get involved in the community.  It sure is a lot of work though.  I have been fooling around with this for 3 days.  I get answers to my questions in the beginners forum, but it just seems like it is one thing after another.

My friend who started working with ubuntu the same day I did has still not been able to get his screen resolution to work.  When he goes to System>Preferences>Screen Resolution there is only one resolution available, which is too big.  He has tried lots of things and can't get it to work.  I don't know the details.  He might buy a new video card or he might just go back to windows.  He was like me.  He had an initial enthusiasm but is now getting discouraged.

Is linux and ubuntu still a world only for very technically skilled computer experts?  Does it make sense for the average computer user to try to get into this?  Or have my friend and I just had bad luck and a rocky start?

---

### Post by PapaWiskas on 2007-01-10
I don't know how else to say it.
But here goes...
Don't give up, keep at it.  Keep asking questions here, there are some very good people here who can help both of you.  
I have been Windows free since Dec of 05, just celebrated a year a few weeks ago.

The journey was not easy, but not overwhelming, it just requires patience and fortitude.
If I can do it and keep at it, anyone can, trust me on that.;) 

And by the way, WELCOME ABOARD!!!!

---

### Post by gosh on 2007-01-10
It does work!
And after some fiddling around you feel very satisfied that you've made the switch.
This forum and wiki.ubuntu.com are enourmous helpfull places.
So don't give up just now.

According to that resolution problem, you probabbly have to change your xorg.conf. Search this forum (resolution, xorg)

---

### Post by matthew on 2007-01-10
> **tc101 said:**
> Does ubuntu eventually work for most people?  I am feeling a little discouraged.It does end up working pretty well for most people. Sometimes there are hardware issues that just can't be resolved, but that is becoming less and less common...unfortunately it still happens with some devices where the manufacturer doesn't release drivers for Linux and won't or can't give out the details necessary for others in the open source world to write them. Sometimes figuring out how to do it takes a lot of time. In some cases it never happens. 
> **tc101 said:**
>  Is linux and ubuntu still a world only for very technically skilled computer experts?  Does it make sense for the average computer user to try to get into this?  Or have my friend and I just had bad luck and a rocky start?I don't know your hardware specifics, but I would say it's likely you've just had a rough start. There is a learning curve at the beginning that can be a bit daunting. A lot of people (myself included) begin by dual booting Windows and Linux for a while. My transition period was about 9 months long, but at the end I had found that I hadn't booted into Windows for nearly 3 months so when I had a hard drive die I didn't bother to reinstall it.

Hang in there for a while longer. You will most likely get it up and running!

---

### Post by BarfBag on 2007-01-10
About the resolution issue.  Are his graphics drivers installed?

---

### Post by floke on 2007-01-10
To try and sort your X problem you could try:

sudo dpkg-reconfigure -phigh xserver-xorg

Which will allow you to choose your settings. You might be able to select the right resolution from this. It would also help if you posted your hardware settings.

Many people have glitches getting things set up, so you're not alone.
The forum will try to help you as best we can.

Just to reiterate: Don't give up, you'll be very very glad you didn't. 
And welcome aboard.

BTW: Does the LiveCD work ok or do you have trouble with that as well?

---

### Post by Brunellus on 2007-01-10
What does "too big" mean?  Too many pixels, or too FEW?

Windows boots into 800x600 or 640x480 by default until you install a video driver, so you're not alone.  How many times have you installed Windows from scratch?  

The only reason Windows is easier, in many cases, is because your hardware vendor did all the heavy lifting for you--and there's a fair amount of heavy lifting to do!

---

### Post by jbus on 2007-01-10
Some problems are not as big as they seem and involve just a simple fix. For example the problem your friend is having would likely be fixed by a simple change in his /etc/X11/xorg.conf file or by the installation of the correct driver. Problems like this exist in Windows too. Haven't you ever booted into Windows when Windows doesn't have a driver for your graphics card? The resolution and color are usually sub par until you install the right driver. Same thing with other devices... Until you install the right driver the device will not work properly. In my experience ubuntu has a great out of the box experience. I have yet to run into any show stopper problems on the many systems I've installed it on.

---

### Post by reza81 on 2007-01-10
I Just moved from completely from windowz to ubuntu edgy. I ain't no Linux export, but after 2 weeks of reading articles & learning linux basics it finaly worked great. yesterday I made the mistake to remove pakages in synaptic that where critical & f*ckedup my system. then I had to reinstall my file system. what before had taken me two weeks to fix, I did in 4 hours. (because I didn't have any backup or els it would be fixed in couple of minutes). anyway, you will get the hang of it and there is a lot of info that can help you. when you get everything to work, you will feel very happy that you made that choise. 
down side of using Linux is that when you want to use a adobe/macromedia suite you have to run it with wine or vmware.

resolution problem:(maybe this works!)


install the latest graphic driver look [hier]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") for instructions

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
gksudo gedit /etc/X11/xorg.conf

```


add the resolution you prefer to your screen section
it looks something somthing like this :
```

    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```

&
Disable horizontal & vertical presettings of your monitor 
```


Section "Monitor"
    Identifier     "Generic Monitor"
#    HorizSync       28.0 - 51.0
#    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection


```


This is how I got my resolution higher, notice that this worked on my ASER RC600 With NVidia GForce 4 5200 FX 256MB. 



When everything works you can enjoy FREEDOM !!!

---

### Post by majesticturkey on 2007-01-10
The others here are right. Take things into perspective: You learned Windows by what I call "social inertia" (my sociology teacher is having a stroke if she's reading this :P). Since most people use Windows, you learned it the same way I learned to speak English, by being immersed in it. It's not so easy. Ask a native Spanish speaker how easy it is to learn English as an adult, if you're in the US.

But you learned how to work with Windows, and Linux is just different, but it's no more difficult. Googling problems and diving headfirst into fixing things will really help you learn the OS faster. After a couple weeks I became much more than simply functional, I was customizing everything to fit my needs just right.

It's not slamming your head against a wall. It's just flexing a muscle you've never used before.

---

### Post by doobit on 2007-01-10
I'm not sure about "most people" but it worked for me immediately, and is still working for me.
You may need to learn a few new and different things, but it's worth the small amount of effort, IMHO.

---

### Post by seijuro on 2007-01-10
> **tc101 said:**
> Does ubuntu eventually work for most people?  I am feeling a little discouraged.  

Is linux and ubuntu still a world only for very technically skilled computer experts?  Does it make sense for the average computer user to try to get into this?  Or have my friend and I just had bad luck and a rocky start?

Yes Ubuntu eventually works, I think unfortunately for you and your friend you just got saddled with an unlucky rocky start. I personally have installed Ubuntu on 6+ totally different machines with at least 3 different architectures and the only trouble I ever had was with my dad's scanner which was solved simply by switching him to Edgy instead of Dapper.

Idk if I have seen your friend's thread or not but a lot of times screen resolution problems as described means he simply needs to install the drivers for his video card obviously this isn't always the case but more oft than not.

In truth I'm sure all of us that had a breeze with setups sympathize with you and duely hope you hang in there till your problems are resolved. At least with Linux if there is a problem it CAN be fixed it just depends on how much effort you are willing to put in to it, with windows it either works or it don't end of line.

Hang in there all hope is not lost perhaps you and your friend can post your problems in this thread and we can tackle them together one at a time.

---

### Post by petriomelony on 2007-01-10
I definitely had the same outlook on Ubuntu when I first started (ie: last week).  I installed the 64-bit version of Edgy, and that totally screwed over my first impression of Ubuntu because there was nothing *easily* available for it.  Definitely not for the linux newbie.  I decided to downgrade, and I was thinking Dapper 32-bit, but I asked my friend about it first (who had been using ubuntu for a while) and he recommended Edgy because I would be able to learn better, and it's not really that different.  So i did, and i again had problems, mainly finding drivers for my nvidia video card (which also limited my selection of resolutions to some really crappy ones), but today i managed to fix all that, so i'm happy about that :) you'll get use to it after a while, i'm sure... as a lot of others have pointed out as well.

---

### Post by fuscia on 2007-01-10
you'll get it. it's very different from windows, so it takes a while to get used to. while there is much more configuration to be done, depending on what you're trying to do, linux is simpler than windows.

---

### Post by Kossilar on 2007-01-10
Don't give up! I just installed Ubuntu on both my computers with NO prior linux experience. Its been a challenge. I had to set up my video card, drivers and everything, from the COMMAND LINE. Fortunately, I had a second computer next to me to do the googling and forum delving but I got it all working and I'm very happy to be here.

Keep going. The community will help you and it'll be more then worth the effort.

---

### Post by FuturePilot on 2007-01-10
It is sometimes difficult and you most likely will run into some type of issue at some point. But just keep at it and don't give up. I've had a few issues myself, some I've been able to solve myself, others I've found answers for here. Yes, it can be very discouraging at times. At one point I wanted to throw my computer out the window because I couldn't seem to get the Nvidia driver installed no matter what I did and I kept getting xserver errors. I never gave up though and I eventually got it. So, yeah, don't give. And don't be scared of the command line. Once you use it a few times you can almost feel the power of it. Good luck.:)

---

### Post by venik212 on 2007-01-10
IMHO, Ubuntu/Linux is now where WINDOWS was 5-10 years ago, before they realized that in order to conquer the world they MUST provide drivers for ALL the possible hardware components that users might come up with.  Until then, this usre's complaint will persist.

---

### Post by Brunellus on 2007-01-10
> **venik212 said:**
> IMHO, Ubuntu/Linux is now where WINDOWS was 5-10 years ago, before they realized that in order to conquer the world they MUST provide drivers for ALL the possible hardware components that users might come up with.  Until then, this usre's complaint will persist.
When did Microsoft start supplying such complete drivers in their stock install?

---

### Post by mips on 2007-01-10
> **tc101 said:**
> 
He might buy a new video card or he might just go back to windows.  He was like me.  He had an initial enthusiasm but is now getting discouraged.


He will be wasting his money if he does this.

Easiest way is to edit his xorg.conf file, it's really not hard.

Thing with Linux is that is different and you to change your way of thinking a bit. In the beginning I was lost but now can do most of the things beginners battle with blind folded.

---

### Post by doobit on 2007-01-10
In WindowsXP SP2, I still had to install drivers for my USB memory card reader, my USB webcam, my ipaq cradle, my printer and scanner.

---

### Post by seijuro on 2007-01-10
> **Brunellus said:**
> When did Microsoft start supplying such complete drivers in their stock install?

they didn't, thats a point I made in [[COLOR="Sienna"]another thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=196204&page=3") that some people unfairly expect more from Linux citing things that windows does not do by default either.

---

### Post by Somenoob on 2007-01-10
I had difficulties at first, but now the system is fully operational. I just read the manuals and other online docs and asked if necessary. And of course don't forget the self-confidence :)

---

### Post by macogw on 2007-01-10
> **majesticturkey said:**
> The others here are right. Take things into perspective: You learned Windows by what I call "social inertia" (my sociology teacher is having a stroke if she's reading this :P). Since most people use Windows, you learned it the same way I learned to speak English, by being immersed in it. It's not so easy. Ask a native Spanish speaker how easy it is to learn English as an adult, if you're in the US.

But you learned how to work with Windows, and Linux is just different, but it's no more difficult. Googling problems and diving headfirst into fixing things will really help you learn the OS faster. After a couple weeks I became much more than simply functional, I was customizing everything to fit my needs just right.

It's not slamming your head against a wall. It's just flexing a muscle you've never used before.
Oh, that's a good explanation.  I like it.  Good advice too.  Google is your friend.  Search the forums too.  We reanswer the same questions a LOT.  I learned Windows by having to fix everything that broke (constantly).  Getting Ubuntu set up taught me to use this better than I use Windows, and everything worked out of the box for me.  It was all the customizations that taught me more, but I have no idea what to do about nVidia and ATi drivers and whatnot because I never had to deal with them.  One of my friends who asked me to install it probably has one of those cards and I'll have to learn.  But hey, I went into this wanting to learn something new, so maybe it's a bit of an attitude thing.

---

### Post by macogw on 2007-01-10
> **venik212 said:**
> IMHO, Ubuntu/Linux is now where WINDOWS was 5-10 years ago, before they realized that in order to conquer the world they MUST provide drivers for ALL the possible hardware components that users might come up with.  Until then, this usre's complaint will persist.
hahahaha Microsoft doesn't supply drivers for anything.  The hardware and peripheral companies give you those driver disks BECAUSE Microsoft doesn't have drivers for that stuff in the kernel.   Those restore discs from Gateway or Dell or whatever?  They're not vanilla Windows installs.  They have the drivers slipstreamed by the company.  If you used a plain vanilla Windows install disc, you would have to have the driver discs from the hardware manufacturers.

---

### Post by reza81 on 2007-01-10
> **doobit said:**
> In WindowsXP SP2, I still had to install drivers for my USB memory card reader, my USB webcam, my ipaq cradle, my printer and scanner.

this is a strange thing on XP SP2.It detects most USB devices, but on some of them it doesn't work. mostly mobile phones & camera's with a SD like card in it. and webcams to !!!

M$ introduced XP prising its compatibility ](*,)

---

### Post by farstrider on 2007-01-10
I must admit I am feeling the same about all this! There were updates (Security) I updated and that was that! Nvidia drivers have crashed and burned and I am getting an error that XServer is not working and I do not know what to do! I am pretty good when it comes to XP or Server 2003 but here I am like a new born baby, utterly helpless! ](*,)

---

### Post by macogw on 2007-01-10
> **farstrider said:**
> I must admit I am feeling the same about all this! There were updates (Security) I updated and that was that! Nvidia drivers have crashed and burned and I am getting an error that XServer is not working and I do not know what to do! I am pretty good when it comes to XP or Server 2003 but here I am like a new born baby, utterly helpless! ](*,)
Blame nVidia's drivers.  If you used the open source drivers, you'd have no update problems but no 3D acceleration.  If you want 3D acceleration they make you use the binary ones, but they don't keep track of how the binary ones interact with newer kernels.  You could refuse kernel updates (which is probably what that was) and be fine, but then you might get something that IS Linux supported, but won't work because you have an old kernel.  nVidia's good about fixing their drivers immediately after a kernel update breaks them, though.  It's ATi that you have to look out for.

---

### Post by farstrider on 2007-01-10
Thanks for the reply macogw!

I have a FX 5200 card in the PC and was using beta drivers so that I could get beryl to work! Hells teeth, this gets fustrating!

---

### Post by macogw on 2007-01-10
> **farstrider said:**
> Thanks for the reply macogw!

I have a FX 5200 card in the PC and was using beta drivers so that I could get beryl to work! Hells teeth, this gets fustrating!
Oh, beta?  You know "beta" means "you're testing this, please tell us if something doesn't work so we can fix it," right?  You're supposed to expect it to break so you can submit bug reports and hope it works right by final release.

---

### Post by PartisanEntity on 2007-01-10
It takes some time to learn how to use Linux and Ubuntu, many of the initial problems are due to our newbiness. It took me the good part of a month to get familiar with Ubuntu and to figure out why I was having some issues. I also went through a number of reinstallations to see if new issues arose, whether old issues appeared again and how easily I could solve them the 2nd, 3rd or 4th time around.

Recently I replaced the HDD in my laptop, this time the Ubuntu installation as well as the solving of issues went by in a breeze. The computer was up and running the way I wanted within 2 days. It could have happened faster but I was taking it easy.

I have been a Windows user for many years, and now, since 2-3 months I completely migrated to Ubuntu to the point where I have no Windows partition, not even a 'Wined' version of Windows.

It takes some time and patience.

---

### Post by farstrider on 2007-01-10
Ha Ha! Yes, I get your drift! It's  the only driver that seemed to work so I had no choice in the matter! The security updates broke a few PC today I am sure and not only people using NVidia Drivers.

---

### Post by d_e_monat on 2007-01-10
Just my $0.02 worth...

My wife still insists on WindozeXP.  The other day I installed her DVD burner that did not come with drivers.  Darn!  I almost had to pay $15 - $20 for software to watch DVDs. :evil:  I found a GPL (read free) package for Windoze and the thing works well.

I started with Linux from a Knoppix CD.  Then I tried to install it on my hard drive. :-k 

I then decided to go to pure Debian.  That worked OK, but I was still learning.  I had M$ on another drive in dual boot.

When I first tried Breezy Badger, it installed nearly flawlessly.  :D 

I've done away with M$, completely.  Ubuntu is the best!  Keep at it.  Everybody has a learning curve.

---

### Post by hendoc on 2007-01-10
I've only had Ubuntu for 4 or 5 weeks, and I downloaded lots of PDF's. Most of them assumed that I knew a lot more than I did. But I kept looking and finally found some on my level. Now everything is beginning to make sense to me and I am really excited. Please don't give up.

---

### Post by lyceum on 2007-01-10
I've gotten pretty lucky. I have only ran into one thing myself that didn't work "out of the box" with Ubuntu, but it is my laptop's WiFi card, so I guess that is kind of big. It's funny though, people ask me to work on their PC's all the time and I have started to forget to install drivers for things for Windows. I put a new sound card in my step-mom's PC and it would not work. I was just scratching my head. My dad was like, "there's a disk in here". Then I remembered that I was back in Windows.

---

### Post by Brunellus on 2007-01-10
> **lyceum said:**
> I've gotten pretty lucky. I have only ran into one thing myself that didn't work "out of the box" with Ubuntu, but it is my laptop's WiFi card, so I guess that is kind of big. It's funny though, people ask me to work on their PC's all the time and I have started to forget to install drivers for things for Windows. I put a new sound card in my step-mom's PC and it would not work. I was just scratching my head. My dad was like, "there's a disk in here". Then I remembered that I was back in Windows.
I've had that happen a lot, too.  

There's also the irritation of not having a real shell.  Also, the further irritation of not being able to kill the x-server or go to a TTY console or telnet into your machine when things go wrong.

---

### Post by AndyCooll on 2007-01-10
The simple answer is yes Ubuntu does eventually work for most people. It's all a matter of how motivated the individual is. As is often pointed out on these boards, linux ain't Windoze. It's a whole new learning curve (much as you originally had to learn Windoze, though you've probably forgotten). I had a few things I needed to sort out when I first used Linux. I did a bit of research, asked questions on forums and eventually got everything working to my satisfaction. I learnt loads, to the point that if anything goes wrong now it isn't a great deal. I either know how to resolve the issue myself , or where to find out how to resolve it if I don't.

Hang on in there, it gets easier! And the satisfaction of sorting everything out is priceless

:cool:

---

### Post by euler_fan on 2007-01-10
As a new user, I just want to say my experience has been a little rocky, but if you are getting frustrated the the forums or just want a change of pace/well organized how-to manual, I would suggest **Ubuntu Hacks**, which can be found here: []("http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168477382/ref=pd_bbs_sr_1/002-5623952-5914414?ie=UTF8&s=books")

Probably the sections on dual booting and installing from source alone make the book worth the money.

Good luck!

Euler_fan

---

### Post by euler_fan on 2007-01-10
It looks like the hyperlink I tried to stick in didn't work. I got my copy on amazon.

Euler_fan

---

### Post by macogw on 2007-01-10
> **Brunellus said:**
> I've had that happen a lot, too.  

There's also the irritation of not having a real shell.  Also, the further irritation of not being able to kill the x-server or go to a TTY console or telnet into your machine when things go wrong.
Ugh, yeah.  I was troubleshooting my friend's internet connection issues and he's a modder so he didn't have a start menu anymore and I didn't know how to work the modifications he had.  I told him to give me a command prompt because ping and ipconfig are at least things I can do on Windows.  Even though he's really into Ubuntu and does some ubuntuguide editing, trying to tell him "I don't care about the Network Configurations GUI, just give me a shell" took a while to get an actual response.  And he's an ex-DOS-user.  He should know that shell beats all.

When Windows Update put a bad nVidia driver on a client's box and I was sent to fix it, finding the "roll-back driver" button was annoyingly hard.  Having a xorg.conf-works is much easier.  I think I've started to forget where things are located in Windows.  I really hate the category Control Panel view, and thankfully "classic" view is still available in Vista, but if that goes away...oi, that'll be bad.  One thing about learning to use the shell on Linux that helps me with Windows, though, is that when I need to get rid of a registry file (like from a virus), deleting it from the command line isn't scary.

eulerfan: [http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168478821/ref=pd_bbs_sr_1/104-8684188-6407922?ie=UTF8&s=books](http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168478821/ref=pd_bbs_sr_1/104-8684188-6407922?ie=UTF8&s=books)
did that take?&#12288;It's an O'Reilly book (very awesome series).

---

### Post by Drawstop on 2007-01-11
Please don't give up.  I am 74 and iistalled Ubuntu several months ago.  I dual boot Windows 2000 and Ubuntu 6.10 and only use windows when I need to use my scanner as I cannot find a current sacnner to use with Ubuntu.  But I am using Ubuntu ALL THE TIME and have no grumbles.  People on the Forums are very kind and helpful and I shall NEVER go to XP. Keep trying - you'll never regret it.  Drawstop.

---

### Post by Brunellus on 2007-01-11
> **macogw said:**
> Ugh, yeah.  I was troubleshooting my friend's internet connection issues and he's a modder so he didn't have a start menu anymore and I didn't know how to work the modifications he had.  I told him to give me a command prompt because ping and ipconfig are at least things I can do on Windows.  Even though he's really into Ubuntu and does some ubuntuguide editing, trying to tell him "I don't care about the Network Configurations GUI, just give me a shell" took a while to get an actual response.  And he's an ex-DOS-user.  He should know that shell beats all.

When Windows Update put a bad nVidia driver on a client's box and I was sent to fix it, finding the "roll-back driver" button was annoyingly hard.  Having a xorg.conf-works is much easier.  I think I've started to forget where things are located in Windows.  I really hate the category Control Panel view, and thankfully "classic" view is still available in Vista, but if that goes away...oi, that'll be bad.  One thing about learning to use the shell on Linux that helps me with Windows, though, is that when I need to get rid of a registry file (like from a virus), deleting it from the command line isn't scary.

eulerfan: [http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168478821/ref=pd_bbs_sr_1/104-8684188-6407922?ie=UTF8&s=books](http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168478821/ref=pd_bbs_sr_1/104-8684188-6407922?ie=UTF8&s=books)
did that take?&#12288;It's an O'Reilly book (very awesome series).
Modders should be made to troubleshoot their own **!&!&*! internet connections.

---

### Post by lyceum on 2007-01-11
> **euler_fan said:**
> As a new user, I just want to say my experience has been a little rocky, but if you are getting frustrated the the forums or just want a change of pace/well organized how-to manual, I would suggest **Ubuntu Hacks**, which can be found here: []("http://www.amazon.com/Ubuntu-Hacks-Tools-Exploring-Tuning/dp/0596527209/sr=8-1/qid=1168477382/ref=pd_bbs_sr_1/002-5623952-5914414?ie=UTF8&s=books")

Probably the sections on dual booting and installing from source alone make the book worth the money.

Good luck!

Euler_fan

Ubuntu Hacks is great! It is written as though you know what you are doing, so it may not always be the best for new users, but it is great non the less, and well worth the price, especally if you get it on sale :)

---

### Post by macogw on 2007-01-11
> **Brunellus said:**
> Modders should be made to troubleshoot their own **!&!&*! internet connections.

Yeah, you'd think so.  It wasn't attached to the wall.

---

### Post by tc101 on 2007-01-11
Thanks for all the encouragement everyone.  I plan to stick with this and master it.

My friend spent 5 hours last night trying to get the video to work, using all the advice given in this thread, and he never could get it to work.  He got discouraged and is giving up on ubuntu for now.  I told him to forget about for now and when I had learned more I would help him.

I am motivated to master this and plan to stick with it.  That is at least partially due to all the encouragement I got here.  Thanks again.

---

### Post by tc101 on 2007-01-11
A few more comments.  I think I was trying to do too much all at once.  I am going to tackle just one problem at a time.  I actually have a system that I can work with now, so it is just a matter of refining it.

---

### Post by lyceum on 2007-01-11
> **tc101 said:**
> A few more comments.  I think I was trying to do too much all at once.  I am going to tackle just one problem at a time.  I actually have a system that I can work with now, so it is just a matter of refining it.

That is the key, one thing at a time. Take notes, so you remember what you learn. :)

---

### Post by seijuro on 2007-01-12
> **tc101 said:**
> A few more comments.  I think I was trying to do too much all at once.  I am going to tackle just one problem at a time.  I actually have a system that I can work with now, so it is just a matter of refining it.

Indeed that is how I was taught to troubleshoot in school make a mental checklist starting with the simple most obvious things first then work down the list one at a time till the solution presents itself.

---

### Post by ajm2005 on 2007-01-15
:)

---

### Post by ice60 on 2007-01-15
i have linux working perfectly. really, everything i need works without one problem. 

i started using linux because i like computers, not because of my dislike for MS, or love for free software. i could easily have just said 'this is too difficult, or MS does it this way, so why does linux do it differently? - it makes no sense' but, those thoughts never crossed my mind. 

i just about loved every second of using, and learning about linux (apart from the first few times of compiling programs). one thing that really made things easy for me was this forum - every question i had was answered through searching these forums, or asking if i couldn't find the answer in a search.

for me computers are fun and if i'm not enjoying something like using linux then i'd go back to XP if i thought i'd like using that more. but, as things stand i totally love linux and don't think i could enjoy using XP anymore, i haven't used XP once since i started using linux over a year ago :D . linux, with compiz absolutely pwnz :mrgreen:

---

### Post by ljpm on 2007-01-15
> **tc101 said:**
> Thanks for all the encouragement everyone.  I plan to stick with this and master it.

My friend spent 5 hours last night trying to get the video to work, using all the advice given in this thread, and he never could get it to work.  He got discouraged and is giving up on ubuntu for now.  I told him to forget about for now and when I had learned more I would help him.

I am motivated to master this and plan to stick with it.  That is at least partially due to all the encouragement I got here.  Thanks again.

I have been using Ubuntu since Aug. It took me until Nov. to get my pixma ip 1600 printer to work. I just managed to install ati drivers for my xpress 200 video card (the generic drivers worked fine but I just wanted to get the ati drivers working).

About your friends problem, when I first tried Ubuntu in July I had trouble with the screen res.
 the solution for me was

```
sudo dpkg-reconfigure xserver-xorg
```

The key was to enter my monitors correct hscan and vscan ranges.

I am assuming that the higher resolutions were blocked to prevent damage, based on the wrong hscan and vscan ranges, to the monitor.

---


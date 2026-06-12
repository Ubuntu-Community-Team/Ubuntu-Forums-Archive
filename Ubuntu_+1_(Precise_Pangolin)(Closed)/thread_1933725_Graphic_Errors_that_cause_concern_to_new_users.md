---
title: "Graphic Errors that cause concern to new users"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ruinairas on 2012-02-29
I've noticed computers that have restricted drivers..Nvidia/Ati that when you run Ubuntu for the first time you get some horrible graphical errors before you get the proper drivers installed. For a  serious linux user this isn't a problem, because it's an easy fix, but for new users testing Ubuntu for the first time this can be a quick way for them to think it's not stable, and turn away.


*The text that displays when you log out or shut down the PC also seems to alarm people :P

---

### Post by 23dornot23d on 2012-02-29
What do you believe could be done to change this situation .... ?

I often wonder myself about how many people hit this graphics related issue and run for the hills ....

You could then guess thats why Linux is still low on its 1.6 percentage of total users ......


First impressions do count ....... :confused:

---

### Post by kaldor on 2012-02-29
See here for a little bit of info: [http://www.phoronix.com/scan.php?page=news_item&px=MTAwODk](http://www.phoronix.com/scan.php?page=news_item&px=MTAwODk)

---

### Post by ruinairas on 2012-02-29
> **23dornot23d said:**
> What do you believe could be done to change this situation .... ?

I often wonder myself about how many people hit this graphics related issue and run for the hills ....

You could then guess thats why Linux is still low on its 1.6 percentage of total users ......


First impressions do count ....... :confused:


As what can be done to fix the situation is a difficult one, since the drivers are proprietary and can't be put into the distro by default. I guess the solution would be somewhere in the generic drivers used before the proprietary are installed?

I'm not an extreme expert on this topic, but I'm hoping someone who has the know hows can find this thread and be inspired to find a solution.

---

### Post by ruinairas on 2012-02-29
> **kaldor said:**
> See here for a little bit of info: [http://www.phoronix.com/scan.php?page=news_item&px=MTAwODk](http://www.phoronix.com/scan.php?page=news_item&px=MTAwODk)

Oh, that looks great. It's nice to see that progress has already been made!

---

### Post by 23dornot23d on 2012-02-29
> 
As what can be done to fix the situation is a difficult one, since the  drivers are proprietary and can't be put into the distro by default. I  guess the solution would be somewhere in the generic drivers used before  the proprietary are installed?

I'm not an extreme expert on this topic, but I'm hoping someone who has  the know hows can find this thread and be inspired to find a solution.
Possibly a one off choice ..... at the installation ..... less automatic .... but just one
question ...... 
[B]
ATI or Nvidia or not sure .... ?[/B]

If you are not sure :confused: ...... then it goes with the option it currently runs with.

If the system works out the correct resolutions ... and downloads the drivers and sets them up at the install
stage ...... its a winner ..... almost .....

Problem .... Hybrids .... What to do with these ...... ?

---

### Post by effenberg0x0 on 2012-03-01
IMHO:

**The desktop will go VGA-Mode in most cases**. At most, the user will be in a non-accelerated ridiculously-large and low-res 640x480 desktop until Jockey kicks in. Drivers available in repos for NVidia/ATI/Intel allow for a better/usable desktop and that works reasonably in most cases. Although proprietary drivers and more complex workarounds can be used to improve graphics, the basics/automatically available stuff makes the desktop usable. 

[LIST]
[*]Any normal individual will look at that low-res desktop and think "*OK, I see icons, an interface, etc. The desktop is here, but it is too big. There must be something I should click to configure it. I've seen so many people talking about Linux and Ubuntu, they can't possibly be using this resolution*".
[/LIST]

**Horrible / corrupt graphics at boot are generally Plymouth related**. This is the real problem.

[LIST]
[*]Any average-user will look at a pink-screen with no info or logo, a pink screen with red error messages, a black screen with corrupted video (pink moving squares, lines, etc) and think: *This is a bug. Something went wrong. It can't possibly be normal.*"
[/LIST]
 
So my suggestion continues to be the same: **We don't need Plymouth**. 
Or, at least, we don't need Plymouth:


[LIST]
[*]At a first boot after install/update. Too risky!
[*]As it is right now: Not-configurable, not possible to change/disable it via System Settings.
[/LIST]
But sadly this seems to be a forbidden topic: AFAIK, no request to discuss it has ever been taken under consideration. It's a "wont-fix".

Regards,
Effenberg

**EDIT: **And, as we have talked many times since the OO cycle, a welcome/splash screen with some basic info and links to Ubuntu Wiki, could really help users. Imagine the first thing a user sees after login is this dialog with links like "Click here to learn how to improve your graphics, How to set up a printer, etc**"**

---

### Post by ventrical on 2012-03-01
As they did with Compiz Settings, they should also do here in this situation at install or new_user make. Give the option to  run Normal_User Mode or Power_User Mode, wPlymouth or w/oPlymouth. Otherwise we are splitting hairs because we will always be getting Jill, Jane and John Doe (nee noob) that just wants their PC to be up and running with no verbose nonmenclature and then there will be those that are borderline hacker nouveaus that just have to have some terminal code to get started in the morning.

 It is then not safe to assume that even stumble_upon_Ubuntudoers will all want  a straight  salt and pepper diet. I can see that Canonical is walking the line here .. to reach that 200 mill  number... they got to get the start up even better than before... no .. not just fixed ... but even better that before.

  Fedora 15 for example has a good safety routine .. it will crash and you can close the installer and it will fall you back to the live CD working mode. It doesn't leave one with the impression that they will never try another install again or go running to another OS.

 Keep up the good work effenberg...  we got just better than a month to really ride the devs to get the program right and if we keep at it here  with our invaluable contributions then I am confident that Ubuntu 12.04 LTS will be better than anything out there come release day. As it stands now , with the Ubuntu philosophy ,  there is something there for even older machines with Precise .. well.. at least thats the way I see it going.

---

### Post by 23dornot23d on 2012-03-01
> 
Normal_User Mode or Power_User Mode, wPlymouth or w/oPlymouth


Once we get away from this idea the sooner we can solve the problems ....

[COLOR=Blue]Power User[/COLOR]

[COLOR=Blue]Normal User[/COLOR]

[COLOR=Blue]Noob[/COLOR]

If the install disk was set up for any class of User it should probably be the Normal User
as Noobs will find a friend to install it to their Pc or Laptop or seek help

Power Users .... tend to be able to solve their own problems ...

( Plymouth may be the problem - the only question that needs asking is Nvidia or ATI )

Normal ... the majority the middle ground on the distribution graph these people use
computers to do work .... they need it to work too.

Does a Normal user know ...... what graphics card they have [COLOR=Red]**Nvidia or ATI**[/COLOR]
and if they do not know what graphics card they have - then the system can do
the magic and try to find out for them ......

What really annoys me and many users .... every 6 months .... or so when I install the latest version .....

Even though my graphics ran just fine before .....

Suddenly ....

Its - WTF ...... no graphics - no acceleration .... or worse ..... a black screen greets me with a white flashing cursor.

I know nothing of how clever the system is .....
( is it a Noob system a Power System or a Normal System )

It certainly needs a category like us as USERS ..... as a Noob and a Stumbleuponer ... still know what a Nvidia Graphics Card is ..... or a ATI graphics card.

( many are not aware of plymouth - why because its not a question they need to answer )

Do you want to try for a fancy splash screen or just get to your desktop ..... ?  

Should be the question if any ... 

( my thought is they really want to get their desktop ) 

So its not needed to start making something more complex.

My Power System ..... my OS ..... thinks its better to set my graphics up a different way to the way I ran it for the last 6 months ....

Is it confused .... or really not all that good at working out its Nvidia mmm the info seems to be their when I run lspci it can find it and even gets the model right ....

____________________________________________

Trying to make something complicated is easy ...... 

Look for a simple solution and give the USER a little credit ......

They can read whats on their computer or ask a friend ...... A B C D

[COLOR=Red][B]ATI or Nvidia ..... or something else (can I get my last setup as it worked)
[/B][/COLOR]
Can I phone a friend ..... ( this is not an option and its not  [COLOR=Blue]**I want to be a millionaire**[/COLOR] ) 

but then again it is not the most difficult question in the world even for a Noob :confused:

Are you sure its Nvidia ... the system thinks its this ? and has overidden your Noob idea

Whoops you are now left with a Black Screen and a white flashing cursor.

Your options after the system chose for you are .....

[COLOR=Blue]**Ubuntu Forums ..... hold the shift key down .... or continually press the <ESC> key .... hope you get to grub.**[/COLOR]

Impressed .... then read the forums after the new release ....

If you do not find at least a dozen of these questions I will be very surprised. 
( and they are only from the USERs ( noob - normal - power ) that can be bothered to come onto the forums to let you know )

Many more will have problems and just spread the word ..... that it did not work.

What should happen is .....

Wow it worked ..... and I have Compiz from install ..... on the first boot .....

and second boot up  .... look it still works ...... :D

---

### Post by ventrical on 2012-03-01
Nice write up !  Most of my computer career has been data entry, hardware repair, precious metal recovery and malware removal.  Malware removal and FRU of Microsoft based machines is bread and butter. Instructional Devlopment also ( my forte' / or at least I try real hard ). 90% of the time most Windows users just depend on automatic updates to fix things or  finding out how to download malwarebytes or AVG. Most  application professionals are trained to do just that - work one or two applications and not have to worry one iota about verbose code, terminal emulation or virtual machines. That is not what they are getting paid for, nor were they trained for it. 

 When the stuff hits the fan in the office they usually call the resident or local IT guy  to do the dirty work - but you can bet these Office App Pros want nothing to do with undestanding how a terminal works. In this sense Microsoft has been successful, shielding it's user from the power-rendering-matrixesque dimension of the internet and keeping them focused on a  simple , one idiot, one box type mentality, and I do not use the term *idiot*   in a disparaging tone, only to emphasize that we are not playing a Turing Game here - or are we - or perhaps it is like a player piano , only are you playing the piano or is the piano playing you ! ?

  I admire the Canonical admins and CEOs for taking up this 200 million user_rip  adventure, but , in all honesty (and hopefully said respectfully to all the devs) unless they get the installer or Plymouth or the hardware jockey for that matter, just right, then 200 million users is a long way off. It's just the nature of the buisness. With an IT or even noob who has mouths to feed and bills to pay, that dude is going to look at the down_time it takes to teach somebody Ubuntu. In todays developing and competitive internet you can point noobs ,and others as well, to man pages , patches and tutorials but the bottom line is that the automatic updating process and version updates should be more stable, not obsolete old hardware
 I do hope that I can inspire others to take up that task - to make Ubuntu not just better .. but the best !

---

### Post by 23dornot23d on 2012-03-01
I have read quite a lot of your entries - and admire the work you do .....

The more demanding the problem is .... then the more the people look into ways to
fix them.

You work on a tiny piece in a watch mechanism to get the whole thing  working ..... you sometimes need to step away and look at the display  ..... the clock is no good without the display.

Trying to simplify a problem to the quickest way of finding a solution - at a good
cost ..... and also easy to add to the existing setup may at times mean less code
and the odd question ...... ( pick the one from above in my previous post )

When I look to solve a problem - the first thing I do is to work out  options and then narrow them down until one stands out as being cost  effective - and easy to implement.

Lets say this is the problem .....

We have millions of computers ...... lets make it as complex as we can to start with and then try to focus on a solution.

There are numerous graphics cards there are numerous screens and  resolutions for each - but is there one thing that is common among all  of them ......

Now my job if I accept it ...... is to make a tool that will work on every one of these and never fail ......

The job of this Tool / application ...... is to allow every user the option to see a boot menu.

Ok now we have the very basic idea of what we want to achieve .....

How do I implement it ....... maybe a fallback mode at boot up .... easy to get to.

( why because [_[COLOR=Blue]**vga 640 x 480 **[/COLOR]_]("http://en.wikipedia.org/wiki/Video_Graphics_Array")has been set from the very start )

Will every screen run at 640 x 480 res .....

Can every monitor display at 640 x 480 res ......

This tool / menu does one thing for me .... it allows me to choose my OS and it gets me
there ...... if it fails to do that .... then I as a designer did not understand the aim
and the problem ...... and also failed to do my job.

How easy is it to tell a user to go to fall back mode .....

At the moment .... its not .... because it does not give a solution to get them
to a place where we can help them out .... a console.

___________________________________________________________

Lets now look at whats in place .....

A system that tries to give fancy graphics from the start-up.

A system that is failing to do the job of getting some of the USERs to their Desktops

A system with a aim to impress the USER at boot up with fancy graphics  possibly to compete with MS maybe .... * ( but when it fails it has the  opposite effect )

The one thing that needs meeting is to get the USER into their working  OS ..... using a little input from the USER at the beginning is not a bad thing and most know that they
have a graphics card ...... and the type ATI or Nvidia .... why because they are popular
and the gamers and the ones that want the best go for better graphics .....

_____________________________________________________

  So to giving a better option than holding down the shift key to get to grub ....
adding nomodeset .... that works once and is not easy for the USER to set up
to work more than once ( that is presuming they can get to alter it )  


Feel free to add a solution that meets all the USERs needs to easily get to the 
desktop ...... GRUB 1 was not that bad ..... and I could always alter it to get in
easily.

Now its a chicken egg scenario ..... often needing a liveCD to do anything .....

It gets me the LiveCD works .... yet the installed system now has
less options in fallback mode than ever before .....

Not now a choice for low resolution .... ?

One Search .... [URL="https://www.google.com/search?q=nomodeset#hl=en&q=ubuntu+nomodeset&revid=1977137355&sa=X&ei=ghRQT8vxMoGo8APEwZHvBQ&ved=0CB0Q1QIoAA&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=abb779961339529e&biw=1099&bih=495"][COLOR=Blue]_**nomodeset ubuntu**_[/COLOR]
[/URL] 
42,000 results ..... is it a problem

---

### Post by effenberg0x0 on 2012-03-01
I think one of the problems we face here is that there will always be some conflict between the many parts involved in software engineering. I **completely agree** that despite any auto-detection attempt, the installer should ask the user if he has this or that VGA hardware. The same for the NIC chipset, etc. 

But people behind UX will say it's unacceptable: Users should select their user name, hit install and go have a coffee. Support/Develop people will disagree, as any failed install attempt generates future demand for them. Power-users will agree, but also demand the installation to ask for PCI IDs of the hardware, which in their opinion every user should have memorized. New users will say "I haz setup". 

I've been against it in the past but, lately, I have grown to realize that no Linux OS is viable for different audiences if it chooses one type of user over the other. And the only way to present users with as much info as they are ready to absorb is to offer the choice for different levels of information (in setup, system settings, etc). It's kindda standard in the market for years when you install a program (in the win32 platform), to choose between a "Standard Install", "Complete Install", "Advanced/Customized Install".

But, back to issue at hand here. We have Plymouth, which is incomplete and broken software. It doesn't even have documentation. And we have Jockey, a great idea that works most of the time, but it's handlers for specific hardware need improvement (I've posted an example about it recently, regarding the proper detection and install of Broadcom Chipsets). 

Plymouth: It's a known fact that if you remove it and replace it for a simple black screen (VT Redirection with no Framebuffer/Messages) the user will have a black screen for a couple seconds and then Lightdm. But no risk of seeing broken screen / artifacts. No KMS / DRM, a 100% bullet proof approach.

Jockey: It's handlers (python) are simplistic in comparison to the procedures outlined in the working tutorials for fixing VGA, Modem, Ethernet, Wi-Fi, etc. It's developers are putting their own vision in the handlers, but disregarding what hundreds of tutorial writers have WTAO to test and define as working and secure complete setup methods.

Those two above have been left aside this cycle, in favor of UI/GUI/UX efforts.
Ubuntu has chosen a path of simplification (tthat sometimes may feel exaggerated), in many aspects. Removing customization possibilities, advanced features, etc has been accepted as a step in this path. It's OK but it supposes broad-compatibility and bullet-proof auto-install/auto-setup of every hardware and software available, a situation in which no intervention will be ever needed - which does not exist. I respect Ubuntu too much to go for unreasonable claims and irrational attacks, as many do (i.e. Unity, now HUD, etc). Software engineering and innovation is hard and takes balls. I have been hoping this simplification choice was done as the best option available for these very first phases of it's new desktop paradigms and, most importantly, targeting the LTS. But I really expect the next release (QQ) to be a little bolder in the customization features. I believe QQ should go less UI/GUI and more technical - effectively making this a better Operating System - not only the better looking one. 

Regards,
Effenberg

---

### Post by sdowney717 on 2012-03-01
Certainly is an unknown area and what to do when a new user gets a snafu.
even experienced users have trouble.
Just now upgraded to beta 12.04
Actually worked well, runs nvidia driver ok.
Except the refresh was at 60, which I use CRT monitor. So I look for nvidia settings shortcut and it is not showing up for GUI.

Have to run terminal, then type "nvidia-settings"
then set refresh to 85
then have to save to config

wonder if on a reboot if it will hold the setting.

Who as a newbie is going to know to do that?

---

### Post by jbicha on 2012-03-01
effenberg, if you're a coder, you're welcome to work with pitti on improving jockey; he'd be glad to have some help. Unfortunately, we're in feature freeze so major changes will need a feature freeze exception to land in Precise.

Replacing the bootsplash with a blank screen is a major UI & usability regression. People expect their computer to show something when booting so they know it's working.

---

### Post by effenberg0x0 on 2012-03-01
Hi JBicha, 

> **jbicha said:**
> effenberg, if you're a coder, you're welcome to work with pitti on improving jockey; he'd be glad to have some help. Unfortunately, we're in feature freeze so major changes will need a feature freeze exception to land in Precise.

It's the plan for next cycle. Unfortunately, I've got too much on my hands right now: 2 jobs and working overnight to get things done. But I have planned my schedule to have one free day per week in the next cycle, which I will dedicate to go back to studying, and Ubuntu. The plan is to join the development effort. I've got a lot to learn about developing in Ubuntu, gotta start on small things. But nothing better than learn while doing it. It seems people in Ubuntu are very supportive of new developers.
> **jbicha said:**
> 
Replacing the bootsplash with a blank screen is a major UI & usability regression. People expect their computer to show something when booting so they know it's working.
I agree, I just don't think Plymouth has been successful so far. IMO, things were easier for support with usplash. What's your opinion about current Plymouth implementation? 

Regards,
Effenberg

---

### Post by tista on 2012-03-01
Guys,

I agree with killing plymouth... ;)

Because today we could have some "hi-speed" machine to boot LinuxOS up, for example, my VAIO Z only needs "5 seconds" till killing plymouth daemon from finishing grub, if so, how long time could we show splash on boot? :P

And I suppose plymouth wasting resources and time on especially hybrid-kms features on kernel, drivers-compatibilities of KMS, and in fact we already won't need something like uvesafb for which didn't have any improvements on KMS framebuffer or so...

Finally I'm happy if the devs could improve to enhance the "raw boot speed" than making users be "eye-candy" on splash!

Regards,
Tista

---

### Post by effenberg0x0 on 2012-03-01
> **tista said:**
> Guys,

I agree with killing plymouth... ;)

Because today we could have some "hi-speed" machine to boot LinuxOS up, for example, my VAIO Z only needs "5 seconds" till killing plymouth daemon from finishing grub, if so, how long time could we show splash on boot? :P

And I suppose plymouth wasting resources and time on especially hybrid-kms features on kernel, drivers-compatibilities of KMS, and in fact we already won't need something like uvesafb for which didn't have any improvements on KMS framebuffer or so...

Finally I'm happy if the devs could improve to enhance the "raw boot speed" than making users be "eye-candy" on splash!

Regards,
Tista

Agreed. It goes back to what I've been saying for a while. Right now, it's not easily customizable and you can't enable/disable it via a GUI interface. If it's so important to keep it, I think it would be fair to present users with the option to at least control and configure it somehow. At any rate, and I know this is a tough one to implement, if it was possible to not have it in a first boot after install, or in first boots after updates, it would be nice. It would increase the chances of users having a not-broken VGA experience until desktop, update and Jockey procedures kick in. And would allow for users to eventually read error messages after an unsuccessful update, thus knowing what to report / what to ask support for.  

Regards,
Effenberg

---

### Post by Johnny3 on 2012-03-01
SSD hard drive are getting cheaper. For boot times. Drivers for Linux can be a pain in the rear end video drivers for video have been OK with me over the years just need to look at the reviews to make shore they work with linux. I am an old new bee and use software center and SPM to install most things. Use terminal as last resort and then it is usually copy and paste.
Good Luck and God Bless Johnny3 65++

   

> **tista said:**
> Guys,

I agree with killing plymouth... ;)

Because today we could have some "hi-speed" machine to boot LinuxOS up, for example, my VAIO Z only needs "5 seconds" till killing plymouth daemon from finishing grub, if so, how long time could we show splash on boot? :P

And I suppose plymouth wasting resources and time on especially hybrid-kms features on kernel, drivers-compatibilities of KMS, and in fact we already won't need something like uvesafb for which didn't have any improvements on KMS framebuffer or so...

Finally I'm happy if the devs could improve to enhance the "raw boot speed" than making users be "eye-candy" on splash!

Regards,
Tista

SSD hard drive are getting cheaper. For boot times. Drivers for Linux can be a pain in the rear end video drivers for video have been OK with me over the years just need to look at the reviews to make shore they work with linux. I am an old new bee and use software center and SPM to install most things. Use terminal as last resort and then it is usually copy and paste.
Good Luck and God Bless Johnny3 65++

---

### Post by tista on 2012-03-02
> **effenberg0x0 said:**
> Agreed. It goes back to what I've been saying for a while. Right now, it's not easily customizable and you can't enable/disable it via a GUI interface. If it's so important to keep it, I think it would be fair to present users with the option to at least control and configure it somehow. At any rate, and I know this is a tough one to implement, if it was possible to not have it in a first boot after install, or in first boots after updates, it would be nice. It would increase the chances of users having a not-broken VGA experience until desktop, update and Jockey procedures kick in. And would allow for users to eventually read error messages after an unsuccessful update, thus knowing what to report / what to ask support for.  

Regards,
Effenberg

@Effenberg

Yeah that's right. So if core-system like "update-initramfs", "upstart" and/or "ureadahead" could control the splash automatically, it sounds nice, right? ;)

Well known, those routines are really important to make "stable" boot sequences with what kernel changes and for what daemon changes...

I also think it'd better to disable the splash on "first time boot" after installing to local drives, yep, since it sometimes makes users ugly with "half-baked" proprietary drivers, no-KMS drivers, in the last, damned kernel-panic unfortunately... yeah damned! X(

Then we should carefully concern for "noobs" on that situation than old geeks like us, right? The noobs might be fallen to "The loop of re-install" you know! ;)

Best Regards,
Tista

---

### Post by effenberg0x0 on 2012-03-02
> **tista said:**
> @Effenberg

Yeah that's right. So if core-system like "update-initramfs", "upstart" and/or "ureadahead" could control the splash automatically, it sounds nice, right? ;)

Well known, those routines are really important to make "stable" boot sequences with what kernel changes and for what daemon changes...

I also think it'd better to disable the splash on "first time boot" after installing to local drives, yep, since it sometimes makes users ugly with "half-baked" proprietary drivers, no-KMS drivers, in the last, damned kernel-panic unfortunately... yeah damned! X(

Then we should carefully concern for "noobs" on that situation than old geeks like us, right? The noobs might be fallen to "The loop of re-install" you know! ;)

Best Regards,
Tista

I know it sounds a little crazy, but not totally undoable, right?
You know when you are watching a boot sequence and you're not really reading all that text but, just be seeing how it "Flows" you get a sense that something in wrong (and then you read it, or look at logs as soon as you get a chance)? I miss that after important updates. 

Ok, I respect the average-users right to look at a 5 to 10 seconds Ubuntu-logo (with some luck) or some pink blinking squares in a black background (more likely). 

But how many times do we try to help people in the forums that start threads saying their PC is stuck with a "checking battery" message (or something like it) when the truth is that they have updated and not rebuild their VGA kernel module, so lightdm fails to start and they are seeing the last message in the boot sequence before X kicks in)? 

How many times do we find ourselves in a pink screen for a couple minutes, we sense that something is obviously wrong, and start typing commands blindly (like Ctrl+Alt+Fx, login, password, sudo reboot now, password, enter)? Or even SysRq  RSEIUB ?

Seeing a small text message saying "Loading Ubuntu.................." with increasing dots for 5 to 10 seconds would really make average-users feel like their PC is broken? How do we know that for sure? Have boot usability tests been made?

I don't know.... I feel like there's this strong rejection to anyone that questions Plymouth viability, which I find very odd in Linux and in Ubuntu. We discuss everything in Open Source freely and openly. Apps are excluded for much less trouble. But Plymouth seems to be a forbidden subject. Sure we can all pretend like it's great, reliable, easily maintainable, mature, adequate for a professional distro such as Ubuntu, etc. But I don't feel like doing that is the best for end-users...

Regards,
Effenberg

---

### Post by cariboo on 2012-03-02
I think if you ask around in the other parts of the forum, you'll find that there is a huge bias against having text output at boot. For most users it means absolutely nothing, and if anything it looks a little scary, especially if there is something that failed to start. The majority of users grew up with Windows, and Microsoft made an effort to suppress boot messages, this is what most users are used to, for the average user, this is just to much information for them to process.

For those of us that have used a Linux distribution for a number of years, we are used to  and want to see what is happening at start up, but with the goal to have 200 million users by 2015, we are going to see more and more users that have no interest in the technical side of Ubuntu, all they'll want to do is turn on their system, and log into Facebook, or check their email. 

Plymouth as it is now, works fine on older hardware of the right kind, on my netbook with Intel 945 graphics and my desktop with Nvidia GeForce 210 I have zero problems, it works as it should. 

Personally I'd like to see an improvement in boot time with Plymouth enabled, the devs managed to do it in Lucid, and since them we've seen boot times creep back up to pre-Lucid levels. Hopefully some effort is put into getting boot times back to what they where in Lucid.

---

### Post by ventrical on 2012-03-02
> **cariboo907 said:**
> I think if you ask around in the other parts of the forum, you'll find that there is a huge bias against having text output at boot. For most users it means absolutely nothing, and if anything it looks a little scary, especially if there is something that failed to start. The majority of users grew up with Windows, and Microsoft made an effort to suppress boot messages, this is what most users are used to, for the average user, this is just to much information for them to process.

For those of us that have used a Linux distribution for a number of years, we are used to  and want to see what is happening at start up, but with the goal to have 200 million users by 2015, we are going to see more and more users that have no interest in the technical side of Ubuntu, all they'll want to do is turn on their system, and log into Facebook, or check their email. 

Plymouth as it is now, works fine on older hardware of the right kind, on my netbook with Intel 945 graphics and my desktop with Nvidia GeForce 210 I have zero problems, it works as it should. 

Personally I'd like to see an improvement in boot time with Plymouth enabled, the devs managed to do it in Lucid, and since them we've seen boot times creep back up to pre-Lucid levels. Hopefully some effort is put into getting boot times back to what they where in Lucid.

  I agree somewhat. For the most part it is rock solid. I think it comes down to a nested loop somwhere in the starup routine/flowchart- ie;
(some crappy pseudo code for example)

let a= FUNC get_monitor_type
let b = FUNC get_graphic_id_byte
let c= battery_state
FOR I = 1 to (50)
  FOR J = 0 to (100)

if,if,if
GET c
if c= battery_state  then PRINT 'Checking battery state'

(so at this point it locks right up because it is waiting for a id byte than never seems to come)

(solution is to insert an added if,then else statement to exit to EOF or revert to a ISA standard video mode. I am assuming that when it returns a false value it goes into an infinite loop.)

   then, then, then

else, else, else

NEXT I
NEXT J

---

### Post by VinDSL on 2012-03-02
> **23dornot23d said:**
> What do you believe could be done to change this situation .... ?
Concerning first impressions... I don't think anything can be done (by us).

For the seasoned tester... You can install the mainline Linux 3.3 kernel.

With Linux 3.3-rc4, I get a sleek black screen between grub and unity-greeter.  Dittos on shutdown.

I *assume* this is because the mainline kernel hasn't been patched for Plymouth.

Just saying...  ;)

---

### Post by VinDSL on 2012-03-02
> **effenberg0x0 said:**
> 
**Horrible / corrupt graphics at boot are generally Plymouth related**. This is the real problem.

[LIST]
[*]Any average-user will look at a pink-screen with no info or logo, a pink screen with red error messages, a black screen with corrupted video (pink moving squares, lines, etc) and think: *This is a bug. Something went wrong. It can't possibly be normal.*"
[/LIST]
 
So my suggestion continues to be the same: **[COLOR="DarkRed"]We don't need Plymouth[/COLOR]**. 

There ya go...

You've crystallized my thoughts, exactly!  :D

---

### Post by ventrical on 2012-03-02
> **23dornot23d said:**
> I have read quite a lot of your entries - and admire the work you do .....

The more demanding the problem is .... then the more the people look into ways to
fix them.

You work on a tiny piece in a watch mechanism to get the whole thing  working ..... you sometimes need to step away and look at the display  ..... the clock is no good without the display.

Trying to simplify a problem to the quickest way of finding a solution - at a good
cost ..... and also easy to add to the existing setup may at times mean less code
and the odd question ...... ( pick the one from above in my previous post )

When I look to solve a problem - the first thing I do is to work out  options and then narrow them down until one stands out as being cost  effective - and easy to implement.

Lets say this is the problem .....

We have millions of computers ...... lets make it as complex as we can to start with and then try to focus on a solution.

There are numerous graphics cards there are numerous screens and  resolutions for each - but is there one thing that is common among all  of them ......

Now my job if I accept it ...... is to make a tool that will work on every one of these and never fail ......

The job of this Tool / application ...... is to allow every user the option to see a boot menu.

Ok now we have the very basic idea of what we want to achieve .....

How do I implement it ....... maybe a fallback mode at boot up .... easy to get to.

( why because [_[COLOR=Blue]**vga 640 x 480 **[/COLOR]_]("http://en.wikipedia.org/wiki/Video_Graphics_Array")has been set from the very start )

Will every screen run at 640 x 480 res .....

Can every monitor display at 640 x 480 res ......



  This goes to the crux of this topic and also eludes to the solution. There is a talk-back problem between different monitors and different adapter cards. I have seen it over and over and over again.. where 'checking battery state' will come up with freeze, but, changing the monitor, the system will then recognize the compatible  monitor and kick in.  Therefor there is a sort of 'contradiction_policy' occurring in the startup, install and hardware detection jockey process. The solution does not have to be superfluous or complex. A lot of hackers and modders (like myself) are always trying different experiments and so it is really not fair to Ubuntu to have such high expectations is this area , because a system can be hybrided just by switching PCI cards or other hardware. Some experimenters like to push the envelope with their hardware , old or new alike. We expect crashes and difficulty and verbose code reporting. But there are times when even the smartest of hackers need to retreat to the rest of a stable system and also those in the field of instructional development and education (Edubuntu is just beautiful). If I can't teach Ubuntu or Linux concepts to more senior people. If it seems like I am always having to pull teeth (so to speak) then it becomes very discouraging. There are exceptions to this rule and I have been successful in  some cases. A lot of people catch on real fast. Ubuntu is really a resilient operating system,. It can do things that other OSes can't do. It has amazing recovery abilities and has, at many times, baffled me at how it can come out of seeming complete destruction to complete restoration.!! However , again , the average user , noob or App Pro just really hasn't got the time to fiddle with terminal code It's asking too much  of them.

  Even myself , I must confess, for instance,have  a  really hard time with the linux/Ubuntu directory structure. However  I am wired  to learn it because I have been reading code for years in other languages so , for me , I can tolerate it to a point where it is enjoyable.

  So, more psuedo code and flowcharting and thought experimenting will bring solutions, probably sooner than later.

---

### Post by tista on 2012-03-02
> **cariboo907 said:**
> I think if you ask around in the other parts of the forum, you'll find that there is a huge bias against having text output at boot. For most users it means absolutely nothing, and if anything it looks a little scary, especially if there is something that failed to start. The majority of users grew up with Windows, and Microsoft made an effort to suppress boot messages, this is what most users are used to, for the average user, this is just to much information for them to process.

Hi cariboo. ;)

Yeah I know what they want...
But one thing.
Windowz has "well designed" proprietary drivers for everything to run on it, but us? No... On ubuntu, even if I had sandy-bridge drm/kms, it would "wait" to be loaded drm_kms_helper and hybrid_gfx0 modules on kernel, I experienced it would take 3 or 4 seconds so there might be few time to kick splash till display-manager are loaded and switched framebuffer to Xorg, isn't it?

I suppose we need something new features in while initramfs are extracted/loaded to show splash on very early stage of boot sequence... If not, we should shift our sights from "beautiful graphical splash" to "ultra-fast boot within 3 seconds", I hope..

> For those of us that have used a Linux distribution for a number of years, we are used to  and want to see what is happening at start up, but with the goal to have 200 million users by 2015, we are going to see more and more users that have no interest in the technical side of Ubuntu, all they'll want to do is turn on their system, and log into Facebook, or check their email. 

Right.
As your words, we really want much more "stable" drivers to draw graphics.

> Plymouth as it is now, works fine on older hardware of the right kind, on my netbook with Intel 945 graphics and my desktop with Nvidia GeForce 210 I have zero problems, it works as it should. 

You're so lucky.. ;)
Me? yeah I dreamed damned nightmare with GMA500 Poulsbo chiipset.

> Personally I'd like to see an improvement in boot time with Plymouth enabled, the devs managed to do it in Lucid, and since them we've seen boot times creep back up to pre-Lucid levels. Hopefully some effort is put into getting boot times back to what they where in Lucid.

Agreed.
I could confirm today precise becomes better and better with lots of new features what I really wanted, but on the other hand, its boot time goes slower... yep, precise might forget the "fast-boot"?!

Regards,
Tista

---

### Post by effenberg0x0 on 2012-03-03
I'm gonna settle and never bring this up again. I look forward for the day I turn on my PCs and Plymouth shows the "circle of friends" fighting capoeira in 3D (but it will only work in a Quadro Plex 7000 - other cards display 3 pink squares - but it will be amazing anyway to imagine what the real image should look like).

Regards,
Efenberg

---

### Post by Elfy on 2012-03-03
:)

That made me smile - made me smile more than the couple of lines of artifacts that I assume tell me things when I boot with nouveau.

---

### Post by lucazade on 2012-03-03
Plymouth is pure crap.. it should be wiped out from linux ecosystem.
It will never work well with all the differences in video drivers, I've tried it with every kind of graphic card and its functioning is unpredictable.

Please fix grub resolution detection and let it paint the splash screen until X loads up via vt.handoff.. We can achieve the same plain purple splashscreen with it.
This way we can avoid flicker, artifacts, resolutions switching, useless components to startup like plymouth...

---

### Post by tista on 2012-03-03
> **effenberg0x0 said:**
> I'm gonna settle and never bring this up again. I look forward for the day I turn on my PCs and Plymouth shows the "circle of friends" fighting capoeira in 3D (but it will only work in a Quadro Plex 7000 - other cards display 3 pink squares - but it will be amazing anyway to imagine what the real image should look like).

Regards,
Efenberg

@effenberg

ahahaha! :)
Yeah it's crazy to show 3D "capoeira" ubuntu logo movies!!
Really fantastic!!

I also imagined for the day we all could see beautiful 3D splash within boot...  and hopefully this splash had better to be showed immediately after BIOS logo ended...

Cheers,
Tista

---

### Post by tista on 2012-03-03
> **lucazade said:**
> Plymouth is pure crap.. it should be wiped out from linux ecosystem.
It will never work well with all the differences in video drivers, I've tried it with every kind of graphic card and its functioning is unpredictable.

Please fix grub resolution detection and let it paint the splash screen until X loads up via vt.handoff.. We can achieve the same plain purple splashscreen with it.
This way we can avoid flicker, artifacts, resolutions switching, useless components to startup like plymouth...

Hey Luca!

Yep plymouth is so crappy for us now...
And you're exactly right. grub seems to be the evil causing wrong display setting to pass through to plymouth smoothly especially framebuffer kms modules... and whenever its resolution/vblank settings are changed, we usually saw some ugly flickering, brack-out, and artifacts within boot. Too bad! So now we only have a choice to kill plymouth, right?

Ciao,
Tista

---

### Post by VinDSL on 2012-03-04
> **effenberg0x0 said:**
> I'm gonna settle and never bring this up again. I look forward for the day I turn on my PCs and Plymouth shows the "circle of friends" fighting capoeira [...]
Bwahahaha!  :D

BJ Penn, FTW!

---


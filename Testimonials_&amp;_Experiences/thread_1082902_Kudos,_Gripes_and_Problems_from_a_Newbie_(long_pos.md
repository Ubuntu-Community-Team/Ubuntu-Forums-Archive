---
title: "Kudos, Gripes and Problems from a Newbie (long post)"
date: 2009-02-28
forum: Testimonials &amp; Experiences
---

### Post by rbrauns on 2009-02-28
Hi Ubuntu Users,

Sorry for the long post  but I'm an absolute newbie and tend to ramble.  This is also my first post so I'm packing everything in one post.  Please scroll down to GRIPES and PROBLEMS to skip my Windows rant.

I'm new to Linux and actually came to use Ubuntu while trying to fix Windows 2000 Pro.  A virus did  minor damage to Windows and then I tried to fix it and made it worse.  Windows destroyed all of my files on the second slave drive which had a logical partiton.  Trying to fix that lead me to a forum where someone posted a fix like this: forget all the recovery stuff.  Boot Knoppix from a Live CD and run ntfsfix.  Did that and it worked.  I was very impressed with how fast and easy Knoppix was to use but couldn't get onto the internet to fix Windows so I used the Live Ubuntu CD that the IT guys gave me.  Version 8.10.  It would load off the CD, find the WLAN card and even saw 5 or 6 networks.  Some weren't password protected and I could log onto the net to try to fix my Windows!  While doing this, I began to use Ubuntu more and more and liked it.

Typical for Windows, the more you try to fix it the worse it gets.  I finally ended up with an error: can't find NTDLR, even though that file was there.  So I grabbed my spare 30 GB SATA drive that I couldn't get to work in Windows and decided to load Ubuntu 8.10.

Before installing Ubuntu, I tried Knoppix, Open SUSE and Fedora all from the Live CD.  Knoppix would display a bomb a lot and I didn't like the KDE interface.  Fedora would try to set the monitor frequency too high for my 15” LCD so I couldn't use it all.  SuSe loaded but I couldn't get the WLAN card to work from the live CD.  I recall getting an error message that YaST doesn't control the network, network manager does.  After fiddling with it for a few days, I gave up on SuSe and installed Ubuntu 8.10 onto the SATA hard drive.

Everything worked right out of the box as long as I used safe monitor mode.  Kudos to all the developers for this OS.  Everything works right out of the box.  This is what every OS should do and only Ubuntu does it right.

Then I started to optimize and customize things and here's where my gripes start.

**GRIPES:**

***Gripe 1:***  Trying to get my ATI Radeon 9600 to work was a pain.  I couldn't change the screen resolution without my screen getting fuzzy so I needed to get the proper ATI drivers installed.  I could see that the FGLRX driver wasn't installed according to the hardware driver manager.  Searched the forums and fiddled.  Using the terminal to try to install FGLRX would give me an error about locked something or no permission.  I finally got it to work by using the terminal to install ATI catalyst, then a small GUI appeared which loaded the rest.  Then I had to activate the proprietary driver using the hardware manager which actually downloaded (before that it would just hang) and now FGLRX is activated.  My gripe is that this is very convoluted and hard to do.  Isn't there an easier way?  My next PC will have a NVidea card.

***Gripe 2:*** Trying to change the mouse pointer was VERY hard.  Going to hardware settings, mouse only lets you change the size of the pointer, not try different shapes.  I don't like the arow combined with the ball.  Again searched the Ubuntu forums and downloaded crystalcursors from gnome-look.org. You can't lnstall programs or even icons this way like in Windows.  I had to use the terminal to get the crystalcursors file and use the Synaptic Program Manager to install them.  Fiddled some more and finally that worked but even now, I can't see the cursors before installing them.  I ran the sudo command from the terminal and selected one of the options.  My gripe here is that I'd love to have a GUI app where I can select my pointers and make it easier to change them and have it available under the hardware settings, mouse menu.

I must say that the Synaptic Program Manager is the best piece of software I have ever used.  It is everything Windows should be but isn't.  With Windows, if I want a program to take AVI files from my camera and make a movie out of them. I have to google, download some shareware package that only partially works and then when I remove it, it leaves dlls and bits of itself all over the registry and HD.  Wtih Ubuntu, I searched the forums, found TOVID, installed it and it works great. 

Kudos to all developers for making the Synaptic Program Manager.

***Gripe 3:*** I have to enter my network manager password every time I load Ubuntu. I did search the forum, installed pamkeyring and did edit the GDM file to include command-pamkeyring.  Yes, it is all done correctly.  Unfortunately, the kernel (root) password and network password were different back then because when I installed the network password, I couldn't use my root password unless I added some numbers.  I have since changed the network manager password to match my root password but I still have to enter the password every time Ubuntu loads   My gripe is that I'd like a way to allow certain keyrings (like the WLAN network) to be permanently unlocked with the root password or even disabled but this is not possible.  How can I avoid having to type in my password at every login?  Or how about a MASTER KEY on the keyring that unlocks everything once?  Even running Synaptic PM means entering in the password every time.

***Gripe 4:*** With my 15” LCD and a monitor resolution of 1024X768, some webpages are hard to read.  I enabled the Universal Access (Orca) but it didn't do what I want.  Then I tried XZOOM and it too, doesn't work that way I want.  What I'd like to have is a right click option with “magnify”.  Then a small round magnifying glass appears on the desktop that I drag over the text I want to read just like my Grandpa does when he reads the newspaper.  KMAG sounds like it might work but will it run on gnome?

Please note that my gripes are minor and should be viewed more as suggestions for improvement.  I see a lot of posts on the keyring issue so my suggestion is to fix that one first.

Now that I have Ubuntu running where I want it, I began installing programs and uninstalling them but now I have some real problems.

[B]PROBLEMS:
1. System hangs while trying to import emails from Thunderbird to Evolution.[/B]
I read the forum and downloaded the Thunderbird extension that allowed me to export my Thunderbird emails as XML files.  Did that and then copied these directories to the evolution/mail directory.  I want to use Evolution because it has a calender and contacts, which is missing from Thunderbird.  When I copy the directories to the proper Evolution folder and start Evolution, the screen darkens and NOTHING WORKS.  Only the mouse works but all I can do is move it around.  Aside from fixing this problem, is there any app that works like the Windows Task Manager?  CTRL+ALT+DEL and you get a nice GUI screen that allows you to force stop certain programs?  I did read the forums and may try TOP from the terminal but once my system hangs trying to import the Thunderbird mails I can't use system monitor at all.

Alternatively, I may just keep Thunderbird and add a calendar and contact app?  Any suggestions?
[B]
2. System hangs after an hour of inactivity.[/B]
This one is serious.  I can live with everything except this.  Whenever I leave my computer unattended for about an hour, I come back to see the 2 LEDSs (caps and scroll lock) blinking, the HD light is off and nothing works unless I press the reset button.  At first, I thought this was due to my torrents running overnight (Vuze and Deluge) so I turned them off.  Still my system stops working after an hour and I have no apps open and running.

Is there an error logger somewhere that I can look at and see what the problem is?  Hardware is a P4., Abit IC7, 2GB ram, 3 HDs (1 SATA, 2 IDE),. ATI Radeon 9600 AGP, 15” LCD monitor.  I have Ubuntu 8.10 with the latest updates.

Oh, just for fun I rebooted into Windows today expecting to see the NTDLR error but instead it worked  !!  Microsoft _*must*_ have a secret program that sees that you have NOT reformatted C: as expected and instead installed Linux.  Then and only then does Microsoft fix the problem.  :lolflag:

Sorry for the WOB.

RB

---

### Post by rbrauns on 2009-02-28
Wow, my first post and I get 2 totally helpful answers.  Let me try again:
1. I like Ubuntu.
2. I have never used Ubuntu or Linux before.
3. How do I turn the keyring OFF? I DID install pamkeyring but it doesn't work.
4. How do I force certain applications to quit?
5. Why does my PC hang after an hour of using Ubuntu?
Details in my original post.

---

### Post by MarblePanther on 2009-02-28
Wow you guys, he was not being negative at all.  He was being helpful by laying out his problems and suggestions in a very concise manner.

As for your inactivity after an hour problem, it sounds like you have powermanagement  set to suspend, hibernate, or turn off your display after an hour.  You can configure this in System, Preferences, Power Management.

Kudos to your post btw.

Also, to force apps to quit try ALT + F2 and type xkill.  This will give you a X cursor to click on any misbehaving windows and force-quits them.  Also there is System Monitor in System, Administration that you can use.  Another method is right clicking on your panel and choose add to panel, and add an applet called force quit which you click on anytime you need to force-quit an app.

---

### Post by solwic on 2009-02-28
> **rbrauns said:**
> Wow, my first post and I get 2 totally helpful answers.  Let me try again:
...
3. How do I turn the keyring OFF? I DID install pamkeyring but it doesn't work.
4. How do I force certain applications to quit?
5. Why does my PC hang after an hour of using Ubuntu?
Details in my original post.

No, please.  Let *me* try again:

1.  **_*THIS ISN'T THE HELP SECTION OF THE FORUM!*_**

Phew.  I don't know how that got lost in translation.  

Glad you like Ubuntu.  You must also recognize that many (if not the majority) of posts like yours are whines and complaints.  It's easy to lump them all together.

:biggrin:

EDIT:  Also:

[quote=MarblePanther]Wow you guys, he was not being negative at all. He was being helpful by laying out his problems and suggestions in a very concise manner.[/quote]

[quote=jrock612]Though I do appreciate that you actually laid out specific issues rather than just whining that it didn't work for you and expecting us all to feel bad about it.
[/quote]

I got it the first time, thanks.  :)

---

### Post by rbrauns on 2009-02-28
@MarblePanther,  THANK YOU for reading my original post.  It was long but I'm detailed oriented.  Sorry for ranting but I expected some help not insults.  Maybe mentioning Windows on an Ubuntu forum is a bad idea.

I have the power management to never shut off.  Is there an error logger anywhere or an event tracker somewhere?

Working through these issues slowly.  I'm finding more info by googling so that is helpful.  I will try the xkill command.  Thanks again.

---

### Post by yther on 2009-02-28
**rbrauns**, congratulations.  You've got your system mostly working and have overcome some difficulties through your own efforts.  :)

First lesson:  Ignore anyone who comes in and says basically, "Too long, didn't read, but [flame]..."  Especially if their avatar is wearing a red hat.  ;)

Now, for some actual information:  I have seen reports of other people with your problem of the computer freezing after inactivity.  (The blinking LEDs indicate a "kernel panic" and there may or may not be any helpful information in your system logs (/var/log) because usually the panic itself can't be logged.)  Some of the people with this problem traced it down to a power management issue.  Try checking your settings and see if something is set to hibernate or suspend the system after an hour of idleness.  If so, turn that off and see if the problem persists.

Sorry I can't help with the keyring stuff, but I have no clue there.

Forcing apps to quit may be possible by pressing Ctrl-Alt-Esc.  If your mouse pointer turns into a red X or a skull-and-bones or something, the next thing you click on will (attempt to) be killed.  If you have a terminal/console available, you can try to find the process ID (PID) of the program (check out **top**, **htop**, **ps**, **pgrep**) and then use the "kill" command to stop it.  Kill has different "signals" it can send; normally it uses a "gentle" request to end, but if the program is being unresponsive you can try "kill -9 xxxx" where xxxx is the PID, which will force it to quit, if possible.  The harshest measure, therefore, would be "sudo kill -9 xxxx".

I hope some of this has been helpful.

*Edit:  Ah, I also forgot that this is Testimonials and not Help.  True, if you want actual assistance you should go post in a support area.  :)  In here you may or may not get informative responses.*

---

### Post by kelvin spratt on 2009-02-28
I totally agree they were very hard on you, but saying that your approach was not the best in the world but never mind you have problems you need to take them 1 at a time step by step its better to ask for help with your problems rather than vent.
To shut down stubborn programs front if you right click on the top panel click on add to panel and scroll down you will find a little program to kill stubborn programs highlight and click add, you will then see it on the panel. I think your errors are all logged in var/log?

---

### Post by MarblePanther on 2009-02-28
> **rbrauns said:**
> @MarblePanther,  THANK YOU for reading my original post.  It was long but I'm detailed oriented.  Sorry for ranting but I expected some help not insults.  Maybe mentioning Windows on an Ubuntu forum is a bad idea.

I have the power management to never shut off.  Is there an error logger anywhere or an event tracker somewhere?

Working through these issues slowly.  I'm finding more info by googling so that is helpful.  I will try the xkill command.  Thanks again.

Look in /var/log for all your logging

---

### Post by solwic on 2009-02-28
> **rbrauns said:**
> @MarblePanther,  THANK YOU for reading my original post.  It was long but I'm detailed oriented.  Sorry for ranting but I expected some help not insults.  Maybe mentioning Windows on an Ubuntu forum is a bad idea.


No, expecting help in a non-help section of the forum is a bad idea.

Sorry for not reading your original post...but like I said, they all look the same, anymore.  

Good luck with getting the help you need.  :)

---

### Post by MarblePanther on 2009-02-28
> **jrock612 said:**
> No, expecting help in a non-help section of the forum is a bad idea.

Sorry for not reading your original post...but like I said, they all look the same, anymore.  

Good luck with getting the help you need.  :)

He is a beginner.  If you have a problem with the placement of the thread, ask it to be moved.  That simple.

---

### Post by Therion on 2009-02-28
To change your mouse pointer you simply need to go into System/Preference/Appearance (Theme tab)
Customize button, Pointers tab and pick your new pointer.

Not so hard when you know how, is it?  

See, from what I've read of your post, many of the problems you're experiencing are due to being unfamiliar with how Ubuntu works.  

This ain't Windows, and it's not trying to be, so slow down, take a deep breathe and realize you're on a journey of a thousand miles...

Of which you've taken a few steps.

---

### Post by solwic on 2009-02-28
> **MarblePanther said:**
> He is a beginner.  If you have a problem with the placement of the thread, ask it to be moved.  That simple.

:lolflag:

No, no problem with the placement.  Just stating the obvious.  He didn't get help because he posted in the wrong place.

Besides, how do you miss "General Help", beginner or not?  It's not exactly brain surgery[color="red"]*[/color].

In any case, I'm washing my hands of this thread.  

@OP:  Good luck.  

[size="1"][color="red"]* Remark is not meant to question the OP's intelligence, but rather to assert that the forum is set up very well, even for a beginner.  Nor is it meant as a disrespectful remark to those who have had brain surgery, and does not question their intelligence in any way.  Any inference or implication otherwise is solely the product of the reader's imagination, and does not reflect my intent.[/color][/size]

---

### Post by rbrauns on 2009-02-28
Gee, I picked up my daughter from her lessons and see a lot of responses.  Thanks to everyone for taking the time to respond to me.  The first part of my post was the first impressions about Ubuntu and then I lead into some gripes and then asked for help.  I will poke around some more.  Thanks for the tips.

Seems most of my issues stem from Gnome so I'm going to try Kubuntu.

---

### Post by yeats on 2009-02-28
rbrauns

Abrasive dismissiveness aside, if you are actually looking for help and advice, it is best to break your issues down into separate posts to appropriate parts of the forum.  There are many volunteers (I'm one) who will be happy to jump in and help where we can.  Many topics have been covered ad infinitum, so if your post goes unanswered, that probably means it's been covered before and you'll want to search the forum a little more for responses.

I'll recommend Kubuntu 8.04, though the freezing/blinking lights issue does indicate kernel panic, which can mean that your system is failing.

Good luck with everything.

---

### Post by solwic on 2009-02-28
> **rbrauns said:**
> Gee, I picked up my daughter from her lessons and see a lot of responses.  Thanks to everyone for taking the time to respond to me.  The first part of my post was the first impressions about Ubuntu and then I lead into some gripes and then asked for help.  I will poke around some more.  Thanks for the tips.

Seems most of my issues stem from Gnome so I'm going to try Kubuntu.

> **chrissharp123 said:**
> rbrauns

Abrasive dismissiveness aside, if you are actually looking for help and advice, it is best to break your issues down into separate posts to appropriate parts of the forum.  There are many volunteers (I'm one) who will be happy to jump in and help where we can.  Many topics have been covered ad infinitum, so if your post goes unanswered, that probably means it's been covered before and you'll want to search the forum a little more for responses.

I'll recommend Kubuntu 8.04, though the freezing/blinking lights issue does indicate kernel panic, which can mean that your system is failing.

Good luck with everything.

I'm sure I'm not the only one who would say two things:

1)  If you try Kubuntu you're asking for trouble.

2)  Good luck with Kubuntu, you're going to need it.

In any case, use what works for you. :)

---

### Post by NiklasV on 2009-02-28
Regarding shutting down programs, that's somewhere I think Ubuntu/Gnome should take a page out of KDE's book: Bind xkill to ctrl-alt-esc. It's so useful whenever an application hangs, especially if that application is in full screen mode. KDE has had this default for ages, I'm confounded as to why Gnome would not. There should probably be a default shortcut for the gnome system monitor as well.

---

### Post by mkvnmtr on 2009-02-28
I believe I have a kill icon on my top panel that seem to work every time. I think you can right click on the panel and choose add to panel and then find where to install it.

---

### Post by MarblePanther on 2009-03-01
> **mkvnmtr said:**
> I believe I have a kill icon on my top panel that seem to work every time. I think you can right click on the panel and choose add to panel and then find where to install it.

Its the one called "force quit" just for clarification.

---

### Post by Tamlynmac on 2009-03-01
[> ]("http://ubuntuforums.org/member.php?u=780238")[rbrauns]("http://ubuntuforums.org/member.php?u=780238")
@MarblePanther, THANK YOU for reading my original post. It was long but I'm detailed oriented. Sorry for ranting but I **expected** some help not insults. Maybe mentioning Windows on an Ubuntu forum is a bad idea.

We were all new to the forum at some point, but doubt many posted in this section "expecting" assistance. I have witnessed what I believe were attempts to gain instant assistance/gratification by posting in this section and ranting. However, I doubt that was the intent here.

IMHO The best course of action should have occurred at the onset of this thread. The OP should have been advised to post their problems in the appropriate sections. Thus eliminating the entire issue and providing guidance to a new forum member.

Instead many chose to argue and/or offer assistance. I really believe guidance would have been more appropriate and encouraged the new member to associate asking for help with the [**Main Support Categories**]("http://ubuntuforums.org/forumdisplay.php?f=327") and search functions. Making the excuse that it's a new member will not provide said member with insight into navigating the forum. Guidance would have. 

But of course that's just my opinion.

One Note: I would suggest that the OP not come to the forum **expecting** help, but rather requesting it. As the members that participate in the help sections do so for free. This is not a helpline or tech. support,. It's members helping members by sharing information and experience(s).

---

### Post by solwic on 2009-03-01
> **Tamlynmac said:**
> 
One Note: I would suggest that the OP not come to the forum **expecting** help, but rather requesting it. As the members that participate in the help sections do so for free. This is not a helpline or tech. support,. It's members helping members by sharing information and experience(s).

+1,000,000,000.  

Thou speaketh the truth.

---

### Post by kelvin spratt on 2009-03-02
"Whoever undertakes to set himself up as a judge of Truth and Knowledge is shipwrecked by the laughter of the gods."

---

### Post by solwic on 2009-03-02
> **kelvin spratt said:**
> "Whoever undertakes to set himself up as a judge of Truth and Knowledge is shipwrecked by the laughter of the gods."

:lolflag:  True, true.

---

### Post by stalkingwolf on 2009-03-02
I give my new Ubuntu customers 2 pieces of advice.  The first is if you
have an Issue or Problem Go to either Absolute Beginner or General Help
forums.  If your Issue/problem is not fixed there then try the specific 
area for your issue, IE: sound video etc.

Use the search function.  If you search does not get the results you need,
Change your search terms.  I have found that changing the way I phrase
search terms changes the results.
If you cant find your answer with search on this forum ( or you aare stopped by the 1 search in xx minuites) try Google.  I have found as many
answers using Google as I have here. ( most have been references to this site, but I got them in a few seconds.)


I agree that most of the OP's gripes  can be summed up in 4 words,
" UBUNTU IS NOT WINDOWS".  No anger, No flames, simply the sooner you
forget the Windows mindset and try the Ubuntu way the better you will be.

> My next PC will have a NVidea card


You can also try Envy.  Actually i think it is envyng.

> I totally agree they were very hard on you,

He is a beginner. If you have a problem with the placement of the thread, ask it to be moved

actually what you might find is that several people in this Community,
because of circumstances that have developed recently are now in a
CYA mode.  Unfortunately the entire community will pay for this situation.

---

### Post by Tamlynmac on 2009-03-02
> jrock612
:lolflag:  True, true. 	

Really.

Aristotle wrote:
The high minded man must care more for the truth than for what people think.

---

### Post by Vince4Amy on 2009-03-02
Gripe 1: Don't rely on Ubuntu's crappy hardware manager, download the drivers from the ATI Website to your home directory as ati.sh and do the following:

sudo sh ati.sh

Run through all steps in Automatic when the installer comes up, after it's complete run:

sudo aticonfig initial -f 

and then reboot.

Gripe 2: Your mileage will vary depending on how the cursor is made, if it is not a .deb file then extract it and move it to /usr/share/icons.

Gripe 3: I don't know about this as this doesn't happen with KDE/Fedora 10 with me.

Gripe 4: Not sure.

About the crashing in the second point, that would be a kernel panic and I'm guessing it may be triggered by the bad ATI Graphics install you have when the default screen saver kicks in.

Don't listen to people who slam you for complaining about Ubuntu, it's not the best distro and I don't use it, ignore them. You make valid points.

---

### Post by solwic on 2009-03-02
> **Vince4Amy said:**
> Gripe 1: Don't rely on Ubuntu's crappy hardware manager, download the drivers from the ATI Website to your home directory as ati.sh and do the following:

sudo sh ati.sh

Run through all steps in Automatic when the installer comes up, after it's complete run:

sudo aticonfig initial -f 

and then reboot.

Gripe 2: Your mileage will vary depending on how the cursor is made, if it is not a .deb file then extract it and move it to /usr/share/icons.

Gripe 3: I don't know about this as this doesn't happen with KDE/Fedora 10 with me.

Gripe 4: Not sure.

About the crashing in the second point, that would be a kernel panic and I'm guessing it may be triggered by the bad ATI Graphics install you have when the default screen saver kicks in.

Don't listen to people who slam you for complaining about Ubuntu, it's not the best distro and I don't use it, ignore them. You make valid points.

Were people slamming him?  I didn't notice.

---

### Post by Vince4Amy on 2009-03-02
> Were people slamming him? I didn't notice.

Originally It seems.

---


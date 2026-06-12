---
title: "My new Wild Dog is crashing repeatedly"
date: 2010-08-04
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-08-04
I am a longtime Windows user switching to System76 Ubuntu for my main home desktop. So far I have loved the new system, except that today -- Day 4 of the transition process -- my Wild Dog is crashing repeatedly for no discernible reason. I have only two or three programs open -- the file browser, Thunderbird e-mail and Chrome browser. I get a complete freeze of mouse and keyboard and must do a hard reboot. This has happened three or four times within two or three hours.

I have tried to copy lines from the log viewer, but there seem to be many logs to view and I'm not sure which ones are relevant. I copied lines from sys log, messages, daemon log and maybe one or two others using gedit.

I tried to attach two gedit (text) files with these log entries to this post but was told it was an "invalid file." It seems that my gedit files (about 185kb each) exceeded the maximum lengths for text files of 19.5 kb. My files are the length they are because I just copied all of the lines within a minute of the crash, since I don't know enough to know which lines are relevant.

Any help appreciated!

---

### Post by realzippy on 2010-08-04
Edit:
sorry overread that size limit is hit.So cut the file in 2 files..

---

### Post by oldsoundguy on 2010-08-04
Most of the add-ons for Facebook are CRAP .. not thoroughly tested and most of their testing is done on Windows.

I use NONE of their junk for just that reason.

It is not second party software (such as Firefox)
it is not third party software (such as Facebook)
it is FOURTH party software .. has to rely on the OS/the browser/and Facebook itself to work.

---

### Post by marshmallow1304 on 2010-08-04
The System76 Driver utility can create an archive of common logs.  Immediately after a crash, go to System->Administration->System76 Driver, go to the Support tab, and click Create.

---

### Post by ShowMeGrrl on 2010-08-04
> Most of the add-ons for Facebook are CRAP .. not thoroughly tested and most of their testing is done on Windows.

I use NONE of their junk for just that reason.

It is not second party software (such as Firefox)
it is not third party software (such as Facebook)
it is FOURTH party software .. has to rely on the OS/the browser/and Facebook itself to work.

Huh? I don't have any facebook add-ons. Not sure why you are posting this to this thread -- or did you intend a different thread. I've added hardly any software to my system as yet. Just Thunderbird and Chrome, I believe. I don't believe I've even accessed Facebook from my Wild Dog.

---

### Post by ShowMeGrrl on 2010-08-04
> **realzippy said:**
> Edit:
sorry overread that size limit is hit.So cut the file in 2 files..
I'd have to cut it into a lot more than 2 files. Each file is 185kb; the limit is 19.5kb. So I'd be attaching about 20 files -- I'm sure that would also violate some limit. :-)

---

### Post by ShowMeGrrl on 2010-08-04
> **marshmallow1304 said:**
> The System76 Driver utility can create an archive of common logs.  Immediately after a crash, go to System->Administration->System76 Driver, go to the Support tab, and click Create.
Thanks, marshmellow, for the advice about creating a log using the System76 driver. I just had another crash and I am attaching the log created by the System76 driver.

---

### Post by isantop on 2010-08-04
Marshmallow1304 has it; System > Administration > System76 Driver then click Create under the Support Tab. This will create a .tar.gz file that you should be able to attach.

About how long is the average time between crashes?

---

### Post by ShowMeGrrl on 2010-08-04
> **isantop said:**
> Marshmallow1304 has it; System > Administration > System76 Driver then click Create under the Support Tab. This will create a .tar.gz file that you should be able to attach.

About how long is the average time between crashes?
I think our posts "crossed." You should be able to see a post in which I did attach a logs.tar file after my most recent crash. The crashes seem to be about 30 minutes apart.

---

### Post by isantop on 2010-08-04
I believe you're right. I'll take a look at your logs and see what I can figure out.

---

### Post by ShowMeGrrl on 2010-08-04
My most recent crash came about 5 minutes after the previous crash. Attached is the System76 log.tar file. Sure would be nice to figure this out. Can't really use my computer the way things are going.

Friend of mine seems to think it might have something to do with Nvidia drivers and that I should roll back (not sure how to do that) the Nvidia updates that happened within last few days.

At any rate, would like to get this fixed. Got to get stuff done. Don't like having brand new (expensive) computer crashing all the time.

---

### Post by ShowMeGrrl on 2010-08-05
Dear System76 - I hope you haven't forgotten me. My problems are getting worse. 

Frequent crashes. Now Banshee is acting strangely, and the OS seems to getting worse. In Banshee, when I change from one song to another using the mouse, the program instantly crashes. After that happened several times, I did an orderly shut down of the system and then restarted it but it refused to boot. I just had the Ubuntu logo there refusing to go any further. I then hit the reset button and it rebooted. Attached is the log.tar file for the latest difficulties.

I am dead in the water with this new computer. I hope you aren't going to abandon me. I'm supposed to get 1 year of technical support. It's been 21 hours since my last post and I have heard nothing. Please help.

---

### Post by jbelmonte on 2010-08-05
Hi ShowMeGrrl,

I am sorry that you are having trouble with your new Wild Dog. Since it is very new, there is the possibility that something came loose in shipping. 

Try rebooting and at the Grub menu select the MemTest86 option and let it run the memory tests for a good long time. That may reveal an issue.

Whether you see errors or not, you might want to you open the box and make sure all the cards and memory modules are well seated. 

Good luck,
John

---

### Post by ShowMeGrrl on 2010-08-05
> **jbelmonte said:**
> Hi ShowMeGrrl,

I am sorry that you are having trouble with your new Wild Dog. Since it is very new, there is the possibility that something came loose in shipping. 

Try rebooting and at the Grub menu select the MemTest86 option and let it run the memory tests for a good long time. That may reveal an issue.

Whether you see errors or not, you might want to you open the box and make sure all the cards and memory modules are well seated. 

Good luck,
John
Thanks for the help, John. The boot up is going so fast on my computer that it whizzes by before I am able to see which keys to press to get to the Grub menu. Do you perhaps know?

---

### Post by ShowMeGrrl on 2010-08-06
Things are going from bad to worse. First, I had (and still have) the frequent system freezes requiring hard reboot. 

Then my Banshee program started crashing whenever it shifted from one song to the next. Could not play more than one song without it just shutting itself down and disappearing off the screen.

I was using Audacity to check the ID3 tags on some of my tracks that I had recently added to the library to see if perhaps there was something squirrely going on there. I then found that to save changes to the tags (and export mp3s), I had to download "lame" files. I found the "lame" files Audacity said to install in Synaptic and installed them. Now I find that the sound is not working on my computer. (See update at bottom of this message for the explanation for this.)

My computer is simply not usable. I am beginning to worry that I made a huge mistake switching from Windows to Linux. Things do not seem to be going well. 

It's not as if I've done anything terribly ambitious on my supposedly "high performance" system. I've installed the Chrome browser and the Thunderbird e-mail and copied over music and picture files from my old computer via a wired network. I added a Ubuntu One plugin to Banshee and signed up for Ubuntu One account. That's about it. And my computer is completely a mess.


LATER CORRECTION: Ooops. I found that the reason I had no sound is that the sound cable from computer to speakers was disconnected. However, I still have the repeated system freezes and the Banshee crashes. Is this typical for System76 computers?

---

### Post by jbelmonte on 2010-08-06
> **ShowMeGrrl said:**
> Thanks for the help, John. The boot up is going so fast on my computer that it whizzes by before I am able to see which keys to press to get to the Grub menu. Do you perhaps know?

Just press the arrow keys as the computer is booting up. That should stop Grub from automatically loading the OS. Then you should be able to select MemTest86.

I don't think your experience is common. I bought a Wild Dog (wdp5) for my son and it has been purring along.

---

### Post by gamerchick02 on 2010-08-08
ShowMeGrrl,

You'll probably have to press something like the left shift on your keyboard to actually have grub show up on the screen.

I'm assuming that since you have a single-boot system, grub is hidden on bootup and you go right to Ubuntu.

Run the memtest like jbelmonte suggested and see what it comes up with.

Amy

---

### Post by gamerchick02 on 2010-08-08
> **ShowMeGrrl said:**
> Things are going from bad to worse. First, I had (and still have) the frequent system freezes requiring hard reboot. 

Then my Banshee program started crashing whenever it shifted from one song to the next. Could not play more than one song without it just shutting itself down and disappearing off the screen.

I was using Audacity to check the ID3 tags on some of my tracks that I had recently added to the library to see if perhaps there was something squirrely going on there. I then found that to save changes to the tags (and export mp3s), I had to download "lame" files. I found the "lame" files Audacity said to install in Synaptic and installed them. Now I find that the sound is not working on my computer. (See update at bottom of this message for the explanation for this.)

My computer is simply not usable. I am beginning to worry that I made a huge mistake switching from Windows to Linux. Things do not seem to be going well. 

It's not as if I've done anything terribly ambitious on my supposedly "high performance" system. I've installed the Chrome browser and the Thunderbird e-mail and copied over music and picture files from my old computer via a wired network. I added a Ubuntu One plugin to Banshee and signed up for Ubuntu One account. That's about it. And my computer is completely a mess.


LATER CORRECTION: Ooops. I found that the reason I had no sound is that the sound cable from computer to speakers was disconnected. However, I still have the repeated system freezes and the Banshee crashes. Is this typical for System76 computers?

This is *not* typical of S76 computers.

I'm looking over your logs (and I'm quite a novice, so bear with me) and I notice that in the syslog at 11:03:47 (at the top of the text file) says BUG: soft lockup - CPU #6 stuck for 61s! [Xorg:1352].

I don't know if that means anything or not, but it does seem that it might contribute to your crashes.

If someone else that spends time in the forum could please look at that and see if I'm no the right track, I'd be much obliged.

Amy

---

### Post by ShowMeGrrl on 2010-08-08
Thanks, Amy. I am now working with System76 (Tom Aaron) through e-mail to solve the frequent system freezes of my Wild Dog. 

I solved the Banshee problem on my own through Internet research. I typed some recommended commands into the terminal, which, unfortunately, wiped out my library and all my playlists. But I reinstalled Banshee after that and it no longer is malfunctioning.

EXCEPT that I got this message when reinstalling: 

"The panel encountered a problem while loading 'OAFIID:Gnome_NotificationAreaApplet' Do you want to delte the applet from your configuration?" 

I felt I had no choice but to say delete. Now I do not get the Banshee icon up on the panel bar at the top of the screen, which would allow me to control Banshee even after the app closes down (yet continues playing). There also is no notification of the song that is playing. Also missing: notification of a wired ethernet connection, which is usually there.

Sooo, I would like to have this notification function. Anybody have any ideas how I can get it without reinstalling Banshee? I do NOT want to lose my library and playlists again.

---

### Post by gamerchick02 on 2010-08-08
Re-add your indicator applet.  You probably lost your envelope mail icon and volume indicator as well.

Amy

---

### Post by ShowMeGrrl on 2010-08-08
> **gamerchick02 said:**
> Re-add your indicator applet.  You probably lost your envelope mail icon and volume indicator as well.

Amy

No, that's the odd thing: I still have the envelope mail icon and the volume indicator. Just missing the Banshee and ethernet connection icons. 

How would I re-add the indicator applet?

---

### Post by bk7777` on 2010-08-08
I have to add to the mix.  I posted on the X-reset sticky issue but I am having the same type of issue with my system 76 Lepard which I have had less than 2 months.
 
I have been doing IBM AIX (UNIX) for over 20 years but never Ubuntu.  This is my first stab at it as well coming from Window XP.  I hate the Microsoft Tax that is why I am trying to get away from it as well.
 
Any way I love UNIX, always have, and it is my profession.  I just need help with Ubuntu and Gnome.  We do not use these in the IBM world.
 
Back to the problem.  With all the testing I have been doing over the past 30 days I have come to the conclusion that it is a problem with the Nvidia Driver.  The system just locks up and have to hard power off to get the system restarted.
 
The only packages I have loaded out side of the base install is Miro, VLC and AT&T ksh.
 
In the many repeated OS loads I did everything as plan jane as possible.  I finally came to the conclusion that the nvidia driver was causing the problem and maybe the hard drive.
 
When I receive the system the hard drive came out of it's cage and was banged around during shipping.  I was told by system76 they have had this reported before.  So I took a 320GB drive I already had and loaded the OS and the system worked great for days.  However I had not loaded the Nvidia driver.  After the system ran rock solid for days I decided to load the nvidia driver and within hours the system started locking up again.
 
That to me tells me there is a problem with the Nvidia driver, which got me writting on the other thread about X-resets.
 
As far as the original hard drive is concerned I am working with Ian of system76 to get a replacment cross shipped.
 
The short of it is you are not alone with the system lockup issues
 
Side questions:
 
Since I have been reloading the OS from scratch.  How do I get the system76 driver back so I can send bug reports as well?
 
Also is there a way to set grub to always stop and display options at boot time and maybe time out after 3 to 5 seconds.
 
Thanks,
Brian

---

### Post by thomasaaron on 2010-08-09
bk7777`, I replied to your post in the sticky.

Anyone else having the lockups, please contact us via email. 

support...at...system76...dot...com

---

### Post by gamerchick02 on 2010-08-09
> **ShowMeGrrl said:**
> No, that's the odd thing: I still have the envelope mail icon and the volume indicator. Just missing the Banshee and ethernet connection icons. 

How would I re-add the indicator applet?

To re-add the indicator applet, right click on the panel and pick "indicator applet".  You may need to actually add the notification area.  Right click on your panel and pick notification area.

Either way, that's strange behavior.  I'm actually kinda stumped.

Amy

---

### Post by ShowMeGrrl on 2010-08-09
> **gamerchick02 said:**
> To re-add the indicator applet, right click on the panel and pick "indicator applet".  You may need to actually add the notification area.  Right click on your panel and pick notification area.

Either way, that's strange behavior.  I'm actually kinda stumped.

Amy

Thanks, Amy! Now I've got both my Banshee and ethernet icons back! And I've learned something about how the panel works. I am very ignorant about Linux and have tons to learn. Thanks for your help.

---

### Post by gamerchick02 on 2010-08-09
Sometimes the obvious to one is not obvious to another.

You're coming along nicely. Hope your computer gets sorted out soon.

Any progress on the crashing?

Amy

---

### Post by ShowMeGrrl on 2010-08-09
> **gamerchick02 said:**
> Sometimes the obvious to one is not obvious to another.

You're coming along nicely. Hope your computer gets sorted out soon.

Any progress on the crashing?

Amy

No, still working with Tom on trying to figure that out. Haven't had any crashes in last couple hours, though!

---

### Post by HeadHunter00 on 2010-08-09
hmmm. try to see if your fan is working. trust me, it can stop any time it feels like.

---

### Post by gamerchick02 on 2010-08-09
> **ShowMeGrrl said:**
> No, still working with Tom on trying to figure that out. Haven't had any crashes in last couple hours, though!

Good to hear that it's being worked on and that it's not crashing right now.  :)

Hope it gets sorted soon.

Amy

---

### Post by PabloH on 2010-08-10
I am sorry to hear you have having so many issues with system stability. This is not a normal thing, I can assure you of that. 


Hopefully they get you sorted out soon and we can get back to answering your software and switching questions. :)

---

### Post by bk7777` on 2010-08-12
[[SIZE=2][COLOR=#000000]ShowMeGrrl[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=841532") are you getting any resolution on your wilddog?  My Lepard is getting worse by the hour.  I am in contact with Tom and Ian at system76 but at this point am no further along.
 
I still believe that the problem stems from the nvidia driver however I am now getting Nautilus errors.  I have to believe it is due to so many hard power offs due to the lock ups.
 
Please share with me and I will do the same as to the procdures s76 is having you try.
 
I am beginning to wounder if I have a Lemon.
 
Thanks,
Brian
 
If anyone is interested I am attaching my logs.tar file

---

### Post by thomasaaron on 2010-08-13
Brian, please supply the time on the system clock when the freezes occur. Otherwise it is very difficult for me to isolate the problem in the logs.

Also, I dont' see the same nVidia errors in your logs as I did in ShowMeGrrl's logs. This is making it a bit difficult to be efficient in this thread, as I may be working on two separate problems here, and me may be beneficial to move your issue to another thread or address it via email so that I can keep all the details straight on each machine.

Can you confirm that, after changing your hard drive, the machine will *not* lock up with the nVidia driver disabled but *does* lock up when its enabled?

ShowMeGrrl's machine seemed to be working fine after we had her turn off Desktop Effects. However, she had to leave for a few days and testing will resume when she returns.

---

### Post by bk7777` on 2010-08-14
](*,)
 
Showmegrrl, Check out my thread titled "[[COLOR=#000000]It's offical my Leopard Extreme is a lemon[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1552742")"  I would explain why your system is crashing as well.
 
Tom,  I suggest you walk her thru running MEMTEST86 if that has not been done already.
 
Thanks,
Brian

---


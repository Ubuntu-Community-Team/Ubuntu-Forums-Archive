---
title: "Reflections after 6 months running Ubuntu"
date: 2011-03-12
forum: Testimonials &amp; Experiences
---

### Post by rebootme on 2011-03-12
I am an IT manager at a large university in the United States.  I switch platforms every six months - Linux, Mac, Windows and back again.  I do this to stay current but also because it's fun.  I enjoy the exploration.  

I just completed six months on Ubuntu 10.10 with a few weeks of 11.04 alpha thrown in at the end.  Below are my overall impressions and specifics on what worked and what didn't, the good and the bad.

This is an effort to provide frank feedback for the purpose of improving Ubuntu in the future.  Of all three platforms, my heart is with Linux.    If anything, my remarks will be too forgiving but please where I am critical understand the criticism is there to call out specific opportunities for improvement (or for someone to comment and educate me on something I was doing wrong).

My last desktop Ubuntu experience was on 9.04 (I run ubuntu servers all the time but at the command line only).  As expected, a lot has changed.  To me, this makes Ubuntu much more exciting than running Mac or Windows.  The rate of change is much faster.

What Made Me Happy

*It's fast.  I ran on HP EliteBook 8440p and it smoked.  Especially once I switched to 11.04 with the "J64" patch.
*Built in output to PDF
*An awesome shell to work at the command line
*Tethering my android phone with EasyTether
*Outlook Web App for Exchange 2010 (I'm using this at work, remember?) is fully supported on Firefox for Linux and works great.  It was my primary email client.
*Chatting with every service in one app, Empathy.  It even supports Facebook now.  Note this does have the downside that people think you are on Facebook all the time.
*TuxRacer and TuxCart were great for my kids.
*The Software Center.  It's amazing how much software is out there.  When I knew what app I wanted it was easy to find and when I was hunting for an app to do something I could usually find something to try, like FreeMind for mind mapping.
*With some exceptions noted below most hardware worked just fine.
*Skype
*Banshee loaded about 100GB of music and performed well.
*OpenOffice and later LibreOffice (I think the split is a good idea).  It seemed faster than previous releases (maybe just faster hardware) and generally handled working with MS Office docs just fine.  There were occasional annoying exceptions, especially when it comes to formatting.
*VPNC for connecting to the Cisco ASA firewall at work.  The cisco client on Windows / Mac is a bloated mess.  Even better, vpnc is integrated into netowrk-manager in gnome.
*Docky.  I like the dock interface model to have quick access to the 5-10 apps I use 90% of the time.
*Gnome Do.  All I can say is WOW!  Do introduces a whole new way to interact with your computer from the keyboard to launch programs, search for files, play music and more.  It's extensible so new plugins can do who knows what.  My favorite is awareness of your ssh config file.  I could just hit the key combo to fire up Do then type the name of a host and hit enter to launch a terminal.
*Adobe Air apps work.  I can't live without the Pandora app and twitter addicts can run Tweetdeck (not me!).
*The usb-creator tools is awesome for creating bootable USB drives from ISO files.
*Unity.  I like making better use of the widescreen format and some of the window tricks like dragging a window against the side of the screen to snap it to using half the screen.  Often, Linux on the desktop feels like it's trying to catch up or prove it's as good as OSX or Windows.  Unity is one area where, in my opinion, it's moving ahead (same for Gnome Do).
*The ability to boot the install media as a live CD.  This allows you to see what hardware works, fix stuff and mess around without breaking anything.
*The community.  Real world friends and on the Ubuntu forums, it's great to see so many people participating and helping each other out.
*Crashplan.  AFAIK the only commercial desktop backup solution that works on linux.  It successfully recovered a 400GB virtual disk file after a hard drive crash.
*Virtualbox.  It was very stable and fast.  I ran a VM with Adobe Lightroom and it performed admirably.  I'm also a photographer and Lightroom was the one app I couldn't live without.
*The panopto viewer works using moonlight.  We use it for lecture / desktop capture at work.
*Fast boot and shutdown.
*Support for NTFS.  Used this often for external drives.
*Not able to pop in and out of a docking station without restarting X and all my programs.  This was annoying as I do it several times a day.  There may be some trick to avoid this but I wasn't able to find one.
*vim. Need I say more?
*Scripting languages built in.  Perl, python or bash it was handy when I had to write a script here and there.
*Openssl.  Very helpful from time to time when testing the setup of web and SMTP server for SSL.
*Chromium and Firefox.  The beta of Firefox 4 on Natty looks great.  Chromium is fast.
*Google docs worked extremely well.
*Support for webdav.  Much more solid than Windows and about on par with OSX.
*Tomboy notes.  Simple and handy.

What Made Me Sad

*The panopto recorder doesn't work.  Another out of our control app.
*To setup software RAID0 for the two drives installed on the laptop I had to use the alternate install CD.  It would be nice if that was possible with the desktop CD.
*No Netflix streaming.  I know there is nothing the Ubuntu community can do about this, except put pressure on Netflix.
*No lightroom
*No panopto recorder
*Not supporting my video card at install.  I had to use nomodeset to force VGA at install.
*I wasn't able to get the Gefen USB to DVI adapter I have to work.  I use three monitors and was only able to use two as a result.
*Connecting to projectors.  It works but is more difficult than in Windows or OSX.
*Flash support was good but tended to crash from time to time.
*Support for the more advanced features of Excel, including add-ins and VBA.  Again, caused by a third party but some sophisticated spreadsheets fly around the office from time to time.
*No VMWare vCenter client.  This is especially annoying because VMWare does so much with Linux yet they aren't supporting the Linux desktop.
*Evolution.  Honestly, Evolution has never impressed me.  I've always found it to be unstable and slow with flaky Exchange integration (yes, I know this is largely Microsoft's fault but this is me reporting on just trying to do my job).  There is no support for Exchange 2010 so I couldn't rely on it day to day but I did use IMAP to Exchange for a bit and it was ok.  My mailbox is 4.5GB which it didn't really seem to like.
*Copy and paste between RDP sessions and the desktop didn't work.  I ended up emailing myself large blocks of text sometimes then opening my email on the remote system.


Thanks for reading if you made it this far!

---

### Post by grahammechanical on 2011-03-12
Is Linux/Ubuntu ready or suitable, in your opinion, for managing the IT needs of a large university? How many problems were down to compatibility issues with an existing IT set up? There most probably will never be a year when Linux takes over the world but how would the other operating systems stand up if the roles were reversed?

Regards.

---

### Post by MorleyPotter on 2011-03-12
*No VMWare vCenter client. This is especially annoying because VMWare does so much with Linux yet they aren't supporting the Linux desktop.

In my opinion VMware Server has everything you need really, It's easy to manage lots of VM's running simultaneously.

---

### Post by 3Miro on 2011-03-12
I assume you are aware of Virtual Box? It is probably not as featured as VM ware, but unless you are doing something fancy it should be fine.

Flash and Netflix are beyond Ubuntu's ability to fix. In a way the video drivers are like that too. The problem there is with the licencing of the proprietary drivers, some distributions get a much better video support.

Many people don't use Evolution. I believe Thunderbird is more popular and I personally like the simplicity of Claws-Mail.

Hope this helps you iron out some of the "glitches" that you are experiencing.

---

### Post by rebootme on 2011-03-21
Thanks for reading and taking the time to comment on such a long post.

> Is Linux/Ubuntu ready or suitable, in your opinion, for managing the IT needs of a large university?

In the right roles yes.  Will it wholesale replace the Windows and Mac systems?  Not any time soon but there are opportunities for many roles.  Kiosks, replacing legacy UNIX systems, Web / Database servers, etc.

> In my opinion VMware Server has everything you need really, It's easy to manage lots of VM's running simultaneously.

VM server is a great product but there's a big ESX environment installed that I have to be able to manage with the vCenter client.

> I assume you are aware of Virtual Box?

Yes, and love it!  I used it to run Lightroom.

---

### Post by lancest on 2011-03-22
> **rebootme said:**
> 
*Connecting to projectors.  It works but is more difficult than in Windows or OSX.
*

Connecting to projectors works quite well.  I don't see how it could be any easier.
Especially If you're using stable open source vga drivers- such as from Intel.
(I've used nothing but Linux on projectors since 2008.) 
Boot then auto-connect. 
Nvidia projection was the most difficult, but still really simple.

---

### Post by mastablasta on 2011-03-22
the problem with hardware is that even if manufacturers decide to support it and even if upon install everything works out of the box you still have the chance that system "updates" will mess it all up for you. and things that were working before suddenly dont' work anymore and then you spend time (and time is money) to fix it. while time spent on a home computer might not be such a problem spending time to fix every computer in large company becomes an issue. Especially if you have a number of differently assembled maschines. using different hardware of which each can pop out with a new issue. 
 
My sound card was finnaly working as it should upon fresh install of 10.10 (instead of 10.04 with upgraded sound drivers) - then came updates and now it has issues again.
my graphics card worked nicely with opensource drivers. i had no issue at all with it. came updates suddenly flash doesn't work right on some videos. hardly the Adobe issue if it worked well before...
then jsut a few days ago i found out it won't play CDs - issue is still open if anyone has the time, will and knowledge to have a look at it.
Samba - working nicely in 10.04, upgraded to 10.10 installed it and lost whole sunday afternoon to fix it. the fix being that package was missing in Samba's install. 
 
Perhaps i should lock all updates?! Appart from browser and firewall.

---

### Post by Arthur_D on 2011-03-22
mastablasta: If you're locking updates, you might as well use Debian.
Just sayin'. :)

---

### Post by wgarider on 2011-03-22
Great recap; couldn't agree more with you about the vSphere client. Grrrrr - thanks!

---

### Post by mastablasta on 2011-03-23
> **Arthur_D said:**
> mastablasta: If you're locking updates, you might as well use Debian.
Just sayin'. :)
 
 
Yes i actually downloaded deban live when 6 came out to give it a try but had compatibility issues. this remains an option if updates to 11.04 won't solve the issues. 
 
then it's a separate home and then reisntall of debian.
 
 
Actually Mint KDE behaved better and was instaleld first, but then i saw plenty things didn't work as they should. for example desktop effects were doing something else than i told them (i told explode on close and instead drop down menu exploded which was irritating). there was also something else not working as it was supposed to (forgot what). so i formated and installed Kubuntu. Worked nicely on start everything basically out of the box, then came updates....

---

### Post by realzippy on 2011-03-23
**Connecting to projectors. It works but is more difficult than in Windows or OSX.*

..have a look at [disper]("http://willem.engen.nl/projects/disper/").

---

### Post by Tamlynmac on 2011-03-24
> mastablasta
Perhaps i should lock all updates?! Appart from browser and firewall. 	

Just a thought, I use a separate HDD to test all updates & upgrades.  Should I find that an update or upgrade creates an issue I simply don't  install it on my primary. The used, inexpensive 20 gig sata drive is a  mirror of my primary (when not used for testing an upgrade) and works  great for testing updates.

As a big fan of stability, this solution assures that no update or  upgrade will negatively impact my system. I started this as a defensive  measure to protect against precisely the problem(s) your discussing.  With the six month release cycle and necessary updates, IMHO it's  illogical not to test. Assuming one is concerned about stability &  functionality. :wink:

I often wonder if the problem is directly related to the six month  release cycle. But historically, that topic results in threads being  moved to the RD - so I won't comment.

Just my $0.02

---

### Post by stchman on 2011-03-24
A fairly accurate assessment.

Netflix - On a laptop uses Silverlight.  From what I have read Netflix streaming on OS X id not too good as well.

Video card not supported - what video card do you have.  Ubuntu offers support for many video cards.  My Intel and Nvidia cards work very well.  ATI/AMD video cards are supported as well.

Flash 10.2 runs extremely well under Linux.  I run all 64 bit and Flash videos (YouTube) work, look, and play just as they are supposed to.

VBA in Excel - those are Microsoft things.

Exchange - another Microsoft thing.

So in closing it appears that you are having your most difficulties with Ubuntu doing Microsoft tasks.  The part of using Linux is to find Linux apps that do what you want instead of using WINE or some reverse engineered way to deal with Microsoft stuff.  You would be surprised at what is available to do all the things you have done before with Microsoft stuff.

---

### Post by walt.smith1960 on 2011-03-24
> **stchman said:**
> A fairly accurate assessment.
.....................

VBA in Excel - those are Microsoft things.

Exchange - another Microsoft thing.

So in closing it appears that you are having your most difficulties with Ubuntu doing Microsoft tasks.  The part of using Linux is to find Linux apps that do what you want instead of using WINE or some reverse engineered way to deal with Microsoft stuff.  You would be surprised at what is available to do all the things you have done before with Microsoft stuff.

The problem comes if someone can't operate as part of a group unless they can use Outlook's calendar/scheduling functions for instance.  I've not run into that because I don't work in that type environment but I'm sure many do.

---

### Post by Tamlynmac on 2011-03-24
> stchman
So in closing it appears that you are having your most difficulties with  Ubuntu doing Microsoft tasks.  The part of using Linux is to find Linux  apps that do what you want instead of using WINE or some reverse  engineered way to deal with Microsoft stuff.  You would be surprised at  what is available to do all the things you have done before with  Microsoft stuff. 	

+1 Good Call

My family & I have been Ubuntu/Linux/FOSS "only" for over 3 years. I  agree that one of the most important keys to using the OS, is in learn  to use the available FOSS apps. If one must use Windows apps perhaps  they should remain in that environment. Rather than investing in a new  learning curve, only to realize that Ubuntu/Linux isn't a Windows clone  or that it wasn't designed to run Windows apps.

---

### Post by tgalati4 on 2011-03-24
I think a pretty good assessment overall.  From an IT manager's standpoint that has to work in a multi-platform environment with MS legacy products, there are shortcomings with GNU/Linux.  For viewgraph engineering, you need 3 screens and good projector support.

For smaller, agile companies/groups working with web apps on iPhones and Androids, GNU/Linux can play along without the legacy issues.

If there is an integration issue with GNU/Linux, sure enough a project pops up to fix that issue.  A good example is Conduit:

[http://live.gnome.org/Conduit/Screenshots](http://live.gnome.org/Conduit/Screenshots)

---

### Post by mastablasta on 2011-03-25
> **Tamlynmac said:**
> Just a thought, I use a separate HDD to test all updates & upgrades. Should I find that an update or upgrade creates an issue I simply don't install it on my primary. The used, inexpensive 20 gig sata drive is a mirror of my primary (when not used for testing an upgrade) and works great for testing updates.
 

 
not a bad idea. Except i am already too often fixing that maschine and it's supposed to be a smooth one because it's from my wife. 
 
Actually i planned to go Mint as they have the updates nicely marked. But didnt' go too well with the install. some funcitons didn't work. So it was followed by reformat and Kubuntu install.

---

### Post by mastablasta on 2011-03-25
> **walt.smith1960 said:**
> The problem comes if someone can't operate as part of a group unless they can use Outlook's calendar/scheduling functions for instance. I've not run into that because I don't work in that type environment but I'm sure many do.
 
 
yes because they are locked in MS environment. Same functions can be done in for example google docs, wehre you have colaborative work calendars...
 
calendars and such are probably the least of the problem. Linux has plenty solutions for those.
 
buggest probelm is probably office compatibility.
 
Send someone a complex file and if they open it wiht open office things will be all over the place. My wife made a book in Word 2003 and then wanted to make fixes and add a bit to it on her linux maschine with OOo. And thepics and editing was all over the place and everything was different. file was opened, but compatible with MS2003? no.

---

### Post by obama549 on 2011-03-25
> **wgarider said:**
> Great recap; couldn't agree more with you about the vSphere client. Grrrrr - thanks!
Yes i actually downloaded deban live when 6 came out to give it a try  but had compatibility issues. this remains an option if updates to 11.04  won't solve the issues.

---

### Post by stchman on 2011-03-25
> **Tamlynmac said:**
> +1 Good Call

My family & I have been Ubuntu/Linux/FOSS "only" for over 3 years. I  agree that one of the most important keys to using the OS, is in learn  to use the available FOSS apps. If one must use Windows apps perhaps  they should remain in that environment. Rather than investing in a new  learning curve, only to realize that Ubuntu/Linux isn't a Windows clone  or that it wasn't designed to run Windows apps.

Yes, I get so tired of Ubuntu being judged solely on its ability to run Windows apps.  It's ridiculous.

Man XP can't run K3b, therefore it's junk.

---


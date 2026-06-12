---
title: "Ubuntu for business - my new years resolution"
date: 2010-01-13
forum: Testimonials &amp; Experiences
---

### Post by clarkkentjt on 2010-01-13
Ubuntu 9.04 LTS x64 running on a 1.5yr old Gateway Laptop with 2Gb of RAM, Intel dual-core 1.6Ghz

My news resolution - Ubuntu. I converted my laptop over to Ubuntu.. permanently.  No dual boot.  I had been running Vista x32 Home for everyday business use, Office2007, Webex, Avast.. but got fed up with the WindozeOS getting slower and slower.  Tired of requiring an AV client due to the high amount of Windows malware. Although everything worked fine, no virus, I knew Ubuntu was faster. I had tried a full conversion 1.5 years ago when I first bought my laptop, but 8.04 didn't recognize the video chip (Intel i810 driver wasn't quite there).  A year ago, I set aside my replacement laptop drive (not a 2nd drive) with Ubuntu.

Well I fired it up over Christmas break.  Upgraded from 8.04 -> 8.10 -> 9.04 Jaunty Jackalope LTS.

CONS:
Upgrade from 8.10 Foobar'd during the upgrade process (literally crashed GNOME desktop), but googled how to correct and fixed.  Apparently happens frequently as I found several forum mentions on how to correct this.

Upgrade also broke VMWare 6.5.. but found the fix.

Calendar and Contact syncs to a Windows Mobile phone is not quite there.  Better than it was in 8.04.  SynCE works fine to access the phone data, but syncing the all important sales contacts and calendar.. sorry, not there for a daily sync.  Really hope Opensync comes through.

Evolution does not support calendar ICS or VCS appointments.  Have to save the calendar invitation to a file then import back into Evolution.  Are you kidding me?!?  Come on, this has been a LONG time product request.

SynCE for Evolution as a conduit works (I can transfer files), but Multisync.90-GUI, multisync or msynctools.. they all suck.  Could NOT get consistent data syncs.  Calendar events with an alarm or reminder F up the sync and it fails.  Can transfer data files, but the calendar just will not sync up smoothly.  Something in multisync and the opensync plugin.. not there yet.  Opensync .30 is in final candidate and their work looks promising, but again, not there yet.

I transferred all my Outlook2007 email, calendar and contacts over to Thunderbird/Lightning and Evolution. (5Gb worth.. time consuming process).  Both are great standalone email/contact/calendar clients, but getting that data to sync over to a Windows Mobile phone.. ugh.

As an alternative to Evolution, Thunderbird with Lightning is awesome.  It supports ICS calendar invites. I much prefer Thunderbird. Syncing Thunderbird to a Windows Mobile phone appears to be supported by a few Windows apps, BirdieSync looks the most promising, but they're Windows apps (boooo).  I tried FinchSync.. it needs work.
FinchSync didn't work over wireless or usb data cable.  Modified my local hosts file, can ping my phone as a finchclient.  Promising, but needs more work.  I can't use it.


PROS:
Ubuntu 9.04 Jaunty runs incredibly quick, smooth and it's cheap (free).  So far, nothing I couldn't figure out by looking through these forums and others.. just google it.

I pimped out my Gnome desktop with a MAC theme: buttons (red,yellow,green) icons, fonts, background and launchpad. 

Gnome desktop, visually, the eye candy of Desktop Cube rotation (Compiz) and the AWN launchpad is pretty sweet.  Bouncing launchpad icons on a launchpad glasstop looks slick.  

Figured out how to run Wine for Word, Excel and Powerpoint 2007 natively in Ubuntu. Although OpenOffice works, opening my company powerpoint 2007 files in OpenOffice presentation does not display or align graphics correctly.  So, for work, PowerPoint2007 becomes a must have for sales and webex meetings.

Webex is not supported for Java 64bit. I tried and tried but webex applet tries to fire up a 32bit Java file.  Webex forums have request for applet to check the OS ver before calling a 32 or 64 bit component.  Webex supposedly works fine on Ubuntu x32 so the forums say.  Webex in a virtual OS will have to do.

Learned more than I wanted to on getting Java to play nice with Firefox.  My advice, stick with the official sun-java packages (apt-get) and don't waste your time manually installing a Sun Java download .bin file.

VMWare 6.5 runs WinXP for Webex and Outlook Calendar and Contact syncs to my Windows Mobile.  WMWare CPU Load is FAR better than VirtualBox, far more mature and better integration with USB. 
Note: Back in 8.04, I tried the initial release of VirtualBox, worked but was buggy.  I see now there's a VBox 2.0 in official repos and 3.0 in the medibuntu, but haven't tried these.  Happy with VMWare.


Overall, Ubuntu is rock solid for business.  You can run 2007 versions of Word, Excel and PowerPoint in Wine.  Outlook2007 in Wine is being worked on.  (wonder if ActiveSync runs in Wine...)  For Webex, running a virtual OS inside Ubuntu seems to be the favored way.  Syncing Calendar and Contacts to a Window Mobile phone is damn close with Evolution, SynCE and MultiSync.  Wish someone improved or built a better, stable and easier sync method (maybe opensync or finchsync?)

---


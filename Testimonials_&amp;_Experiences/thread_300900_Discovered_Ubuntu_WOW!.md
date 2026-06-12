---
title: "Discovered Ubuntu WOW!"
date: 2006-11-16
forum: Testimonials &amp; Experiences
---

### Post by FLPCGuy on 2006-11-16
No, I'm not Al Gore and I'm not the inventor or discoverer of the internet or Ubuntu.  I've been interested in UNIX & LINUX for decades and have tried various flavors on extra drives or old PC's including RedHat until they cancelled desktop distros around v8, Mandrake 9, early Knoppix, and lately SuSe 9 to name a few. I really like SuSe 9.1 Personal (the last free single CD version) as a desktop OS on my spare PC I salvaged from a dumpster [Dell 4100 1 GHz, 512MB]. I read Distrowatch and decided to try other popular or highly recommended distros.  I ordered two CD's, PCLinuxOS and Ubuntu 6.10.  I already have too many partitions on the two old drives on this box so I haven't yet tried PCLinuxOS or installed Ubuntu but... 
I was AMAZED at how well Ubuntu runs from the CD! It saw my external modem, pen drive, and all the other hardware perfectly.  With the latest OpenOfc and Firefox 2, Edgy Efy is a real treat. I love the clean pastel desktop and ease of use with only the very best apps included.  The documentation is the best I've ever seen for any OS. I'm eager to get deeper into using Ubuntu.

Having beta tested every major Windows OS since Win95, I'm not thrilled with Vista. While it is the continuation of add-ons to Windows 2000 as XP was, the two most striking features seem to me to be a massive increase in memory demands and lots of copyright protection (DRM) and hidden services to protect big business interests, and govt. spies [oops, real that paranoia back in].  Actually, I wouldn't go out and buy Vista for an existing PC, but I don't mind it being installed on a new one. With free VirtualPC 2007, I'm sure I'll be running Ubuntu most of the time anyway.  

By the way, Firefox 2 just kicks butt over IE7 which was released before it was finished just to keep from being totally embarrassed by the Mozilla folks. I couldn't even resize the main window of IE7. That means Microsoft's new programmers never heard of the MDI/SDI specification so IE7 is not even a valid Windows application, but Firefox2 is.  Don't get me wrong. I don't have any vendetta against M$ and remain a big fan of Bill Gates (never cared for Balmer the bean counter). But objectively, I see Vista as offering end users little more than continued, necessary security patches for a lot of money while Ubuntu offers a great deal for nothing. Don't let anyone kid you, Windows 2000 (...up) is a very advanced operating system.  Active Directory (written by the top three former Novell programmers who developed NDS) is the way to go to manage corporate networks, and Windows is the only OS that supports almost all the hardware and printers ever made. Serious gamers have no better choice. Still, Linux servers remain the backbone of the internet and desktops like Ubuntu make Microsoft stuff seem very over priced. It will be interesting to see what happens in the next decade.  I'm certain Ubuntu will continue to gain followers in record numbers.  Thanks to all who have made Ubuntu the best Linux distro I've seen yet!

---

### Post by s_h_a_d_o_w_s on 2006-11-16
Welcome to the forums!

Yes firefox2 is better than ie, I agree vista has noting over ubuntu. I hope ubuntu continues to grow!

---

### Post by MetalMusicAddict on 2006-11-16
Welcome. Enjoy your stay.

So what are you running Ubuntu on? Specs?

---

### Post by FLPCGuy on 2006-11-16
I've only run Ubuntu from CD on my old Dell (1 GHz, 512MB) so far. Works great. My other PC (Athlon 2500 AsRock mb) has no serial port for my external modem, I don't have broadband.  Not much point in running an OS with no internet access.  

I'm satisfied with almost free dial-up from Level3 (550access.com say referred by STRAPANE) and BellSouth now makes you pay for each nic and installs spyware (a variant of VnC) if you are ignorant enough to let them. Their std. bandwidth is barely 5x dial-up.  AT&T (new owners) will likely be even worse (greedy CEO's).

BTW Vista includes a new "remote help" feature that bypasses firewalls (all port 80?) and lets M$ or Dell watch your desktop.  They claim it requires your permission, but there is a backdoor for govt. use [like CIA's MagicLantern or Dameware(c) but built-in].  Scary. You won't be able to firewall Big Brother from spying on your PC and P&G will be tracking your shaving habits with RFID! Gattica!

Anyway, I'm going to dump an NTFS partition and install Ubuntu 6.10 hopefully without breaking my SuSe 9. I'd like to figure out the various req'd & compatible partitions for SuSe and Ubuntu so I might be able to modify LILO to point to either.

---

### Post by Patrick-Ruff on 2006-11-27
a tip to you good sir. if you want to have internet on the ubuntu . . . run CCProxy on your windows comp. and viola, instant internet sharing. you define all the ports and all that.

also, Windows Vista isn't as bad as a lot of haters proclaim it to be, really. don't listen to just /anyone/ listen to someone who knows what they're talking about. over all, vista is a GREAT general use OS, but you need a lot of ram. the UAC (user account control) is much like the peremissions system in linux, and I highly doubt it would allow anyone to view your screen without premission.

and FYI, what makes you think this is happening in JUST vista? you know, if the CIA wanted, they could straight up view anyones computer, they don't care, linux wouldn't be that much of a challenge to them. I mean seriously, they could just use some advanced password cracker and VNC you, lol.


not to troll or anything but did you know that Linux has a BUILT IN vnc service? seriously, straight out of the box you can use VNC to view that laptop remotely.

either way, good luck to you.

---

### Post by FLPCGuy on 2006-11-28
I'm just ticked that neither Vista beta would do dial-up networking at all.  So I read some reviews and mail ordered CD's for Ubuntu 6/10 and PCLinuxOS.  Both are very nice desktops but I still can't get them to use my external (real) serial modem.
After many, many re-installs and totally separate partitons & swap areas, I haven't been able to get GRUB to run any other Linux distros on my drive with SuSe 9.1 Personal (the last single CD release) which sees my modem and uses it as older Mandrake9 and RedHat 8 versions were able to do.  These days, nobody cares about us poor dial-up folks and leaves that code out or doesn't test it.  PCLinuxOS 0.93a errors out when I try to add any modem and Ubuntu Networking can be set to use a modem only but there is no way to dial (it doesn't connect automatically either).  I've read all I can find in the docs and forums and will spend a few more hours trying to configure and use wvdial or pppconfig. But if that doesn't work, I'm going to go get the six disk set of SuSe. I hope SuSe still programs for dial-up users. If they carry Yast forward and stay with KDE's dialer, I won't have any problems.  Serial ppp communications shouldn't still be an issue with any Linux distro. I'm really bummed and still refuse to cave to the bandwidth Nazis at BellSouth DSL.

---

### Post by FLPCGuy on 2006-11-29
Well, it was an all day affair but I finally got connected to my ISP with my full external serial modem.  I can't believe it was so difficult to force Ubuntu to send AT commands through the serial port.  I tried to setup wvdial config first but finally got something useful from pppconfig. Hint to new users of pppconfig, leave your primary provider name as provider so you can dial without passing the path to the filename. 

I opened an internet connection from a terminal then downloaded the 13 updates for my liveCD 6.10 and the current list of apps including universal (huge pkg list failed at 99%). To my dismay, every app I'd consider says not available for my computer (i386), including Stellarium which I have run for Windows. For the record this is a Dell4100 1 GHz Pentium III with 512 MB of RAM, an i686 at least.  Why is there so little software for this most common PC in the World (Intel PIII)?  Perhaps all the PC programmers are working for For Profit outfits.

It only took about two hours to get up to date.  At least I can still get Edgy up to date with security patches via dial-up...not so with M$ or most other Linux distros.  

But there are no virus apps available in my list. I know there are few Linux viruses, but there are some and no way to check for them. How head-in-the-sand is that? Aside from KPPP the only app I found to download was a DOS emulator for my old DOS and Atari games. There was a feed reader I may go for later, but that's about it.

Bottom line, I'd suggest dial-up users start with Kubuntu because you will need to download a lot of KDE libs to run KPPP which seems to be the only GUI modem dialer that might work in the latest version of Ubuntu. I have no idea why System,Network doesn't work or why there isn't a good GUI property page for dial-up (ppp) settings by now.  

I can't honestly recommend Ubuntu to my kids or my dial-up friends.  They would never be able to follow the instructions necessary to get online. The only good news is that you don't have much competition. PCLinuxOS 0.93a errors out when trying to install any modem (code logic). Only SuSe 9.1 Personal (last single CD distro) sees my external real modem and configures it properly among the liveCD's I've tried lately.  

It seems Linux desktop progress is going backward with regard to dial-up because older distros like Mandrake 9 and RedHat 8 could be configured easily for external serial ppp.  Just my 2 cents worth.

I'm satisifed even though I can only get connected from the command line. I love Firefox2 and the rest of the desktop. 

It would be nice if someone ported the rotating desktop background code from PCLInuxOS/Mandriva. KDE-look.org has some really nice wallpaper photos I like to rotate as my desktop background and screensaver.  

Thanks to the various forum contributors who addressed the dial-up issue with useful information rather than simply assuming all dial-up users have a winmodem. There is enough info in the forums to get connected.  It just takes some patience to read it all and figure out what works.

---

### Post by ocertain on 2006-11-29
Am I missing something here? 

I also use an external modem and dial up Internet access. I have a US Robotics 56K. When I attached the serial cable to my PC, clicked Network in Ubuntu's Admin menu all I had to do was switch the modem on and auto detect it then provide my ISP information. 

Seriously, I was surfing the Internet in less than 5 minutes after plugging in the serial cable.

---

### Post by FLPCGuy on 2006-11-30
Perhaps my problem was having the modem on and connected during the installation, hoping it would be detected and configured by the installer. A modem entry showed up in Network along with the built-in nic but I couldn't find any indication it even saw my modem or a way to make it connect. It was probably just a stub.

I unchecked the nic, checked the modem, configured the properties, saved the setup as a location and made the modem the default internet access. Still, no connection or button to activate it. Opening a browser or entering a web address didn't inititate anything either. I was stumped by this non-intuitive GUI. The documentation says simply select activate/deactivate. OK, where is that?  Filling or clearing the MODEM check box did nothing. There were no other buttons, toggles, or anything. I assume this whole applet must be for an ADSL connection not dial-up. But it could easily be extended by adding a connect/disconnect toggle button and a PPP and Provider tab to properties.  Maybe in the next release.

Now that I've downloaded and installed KPPP, everything is fine. KPPP is an easy, reliable interface for serial ppp.  If they don't fix Networking for dialup, the 646k KPPP and code from the 11 related GNOME & KDE lib functions should be squeezed into the next distro. But, chances are, fixing dial-up will have little priority.

UPDATE SOLUTION
[http://www.markshuttleworth.com/archives/63#comment-10942#](http://www.markshuttleworth.com/archives/63#comment-10942#)  Artson Says:
October 31st, 2006 at 2:49 am

Maybe better than beauty would be to make absolutely sure that Ubuntu will function for people who access the internet by dial-up as well as that fortunate minority who access it by broadband.

At the moment ubuntu/kubuntu is booby-trapped against dial-up users:

dial-up modem users must **comment out the &#8216;auth&#8217; line in /etc/ppp/options** and create an empty /etc/resolv.conf file. Once these two arcane measures are taken, dial-up modems work fine. This problem has been incorporated in every kubuntu since at least 5.04.

---


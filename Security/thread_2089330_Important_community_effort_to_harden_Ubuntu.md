---
title: "Important: community effort to harden Ubuntu"
date: 2012-11-29
forum: Security
---

### Post by Welly Wu on 2012-11-29
I've made a ton of mistakes lately since I got my System76 Lemur Ultra Thin (lemu4) notebook PC back on July 5th, 2012. I have had to re-install Ubuntu, OpenSuSe from scratch repeatedly because I made too many mistakes that locked me out of my PC or made it impossible for me to log in to my PC. This time, I want to try a different approach. I admit that I don't know enough about how to harden and secure GNU/Linux and I am turning to the community for help.

I re-installed Ubuntu 12.10 64 bit from scratch this past Monday. I have done a minimal amount of effort to harden or secure it. 1. I have added, downloaded, installed, and updated BitDefender for Unices Free and it is fully licensed, 2. I have enabled my firewall and I installed GUFW to open up TCP ports 4242 for CrashPlan so my family members and friends can backup to my System76 PC plus I have enabled IPP Port 631 so that I can print to my Canon Pixma MX870 all-in-one printer, 3. I have downloaded and installed my LastPass extension for Mozilla Firefox and I downloaded and execute LastPass Pocket so that I can download my LastPass vault offline. That's it so far.

I have had problems with ninja locking me out of my administrator account when I used Ubuntu 12.10 64 bit Beta 2. I sent a private message to Bohdi Zazen seeking guidance on how to install and setup ninja properly so that this won't happen again. I have also asked if it is even necessary to use ninja when I would rather prefer to restrict access to su and passwd as an alternative. I don't want to install and setup ninja until I receive more feedback from him or other community members regarding Ubuntu 12.10 64 bit or any future versions that I plan to upgrade to every April and October of each year.

I read all of the security sticky threads. I need help choosing among AIDE, Tripwire, or integrit to monitor local folders and files for changes. Which one is easiest and simplest? It seems to be AIDE. However, I have had problems trying to get AIDE to work on Ubuntu 12.10 64 bit Beta 2 and I need more help when I am ready to tackle this mini project.

I need help with OpenVAS. I don't have enough experience to know how to make it work properly. At least I'm being open and honest with the community so I need help when I am ready to download and install and set it up later.

I am skittish about SNORT. I read all the warnings about how it can introduce more vulnerabilities and I have little knowledge about SNORT or postegr and Apache. When I am ready to deal with this, I will need lots of help and support.

I am comfortable with Novell AppArmor and I prefer to use Rookcifer's custom Novell AppArmor profiles for Mozilla Firefox and Google Chrome along with its related software packages. However, I will still need some help from Rookcifer because I use Ubuntu 12.10 64 bit and some of his custom Novell AppArmor profiles clearly indicate it is designed for Ubuntu 12.04. When I am ready, I will need to ask questions and get more help and support.

That should cover it for now. There will undoubtedly be more questions and more need for specific help.

I want help from the said community members in this thread. I want to open it up to the community to reply and contribute for others that may have similar or related questions. Basically, I don't want to repeat the same old mistakes all over again. I don't want to re-install any operating system from scratch all over again. This is why I need my own thread to focus on my issues and to offer help to others that may reply with their own problems, issues, and questions.

The community here is terrific for these kinds of things. Security is a process and staying alert is key. I don't know enough on how to obtain a reasonably safe and secure Ubuntu installation so I am asking for help and support. My GNU/Linux skills are moderate to advanced depending on the topics covered so far. I am strongest in my knowledge about anti-malware, firewalls, cryptography, Novell AppArmor and to a lesser degree file integrity tools. I have to get more help with NIDS and ninja in particular and I need lots of hand holding and support.

Thank you.

---

### Post by Welly Wu on 2012-11-29
Let me be clear: my goal with this thread of mine is to achieve a reasonably strong desktop security that covers most of the bases in the security sticky threads. I need to be told when I am crossing the line and I am going overboard based upon further replies that I make or others contribute in this thread. Thank you.

---

### Post by Welly Wu on 2012-11-29
I sent a PM to rookcifer and I created and enforced his custom Novell AppArmor profiles for Mozilla Firefox, X-Chat, Pidgin, etc. and I noticed that I can not customize my Firefox extensions or add-ons and the Ubuntu Unity web apps desktop integration is broken. Can you please reply with help to fix these problems? I am using Mozilla Firefox 17 and Ubuntu 12.10 64 bit. Thank you.

---

### Post by Bucky Ball on 2012-11-29
> **Welly Wu said:**
> I sent a PM to rookcifer and I created and enforced his custom Novell AppArmor profiles for Mozilla Firefox, X-Chat, Pidgin, etc. and I noticed that I can not customize my Firefox extensions or add-ons and the Ubuntu Unity web apps desktop integration is broken. Can you please reply with help to fix these problems? I am using Mozilla Firefox 17 and Ubuntu 12.10 64 bit. Thank you.

This should be the subject of a new thread as it has little to do with the original post and description of this thread. I advise you post a new thread regarding this issue. You will broaden your chances of getting help with it.

---

### Post by Welly Wu on 2012-11-29
Okay. Will do soon.

---

### Post by Ms. Daisy on 2012-11-29
The OP has all been done already, the result was the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity"). IMO anything past that is overkill for a standard home user.

Honestly it seems like you're trying to tackle the most difficult concepts first. Start simple & start with the big obvious vulnerabilities (like the stuff covered in the basic security wiki).  Once you've mastered that then try deploying apparmor.  If you misconfigure security tools, you might be creating more vulnerabilities than you're fixing. 

You could also watch this:
[http://www.irongeek.com/i.php?page=videos/derbycon2/3-3-4-chris-jenks-intro-to-linux-system-hardening](http://www.irongeek.com/i.php?page=videos/derbycon2/3-3-4-chris-jenks-intro-to-linux-system-hardening)

---

### Post by Welly Wu on 2012-11-29
I read it and I applied most of the guides. I'm looking for more advanced security topics and I need help.

I installed integrit, psacct, rkhunter, chkrootkit, and apparmor-profiles. I was messing around with Rookcifer's custom Novell AppArmor profiles for Mozilla Firefox, but those are for Ubuntu 12.04 LTS. I had some problems with them so I deleted his profiles and I created a new .mozilla folder to get Firefox to start anew again.

I still need help with Novell AppArmor profiles for Google Chromium and Mozilla Firefox that were written for Ubuntu 12.10 64 bit.

I also need guidance on ninja before I even think about trying to install and set it up again. This will be the last thing that I do. I am also thinking about failog, but I have not tried it yet. Basically, I am avoiding security packages and tools that can get me locked out if I make a mistake because I don't know what I'm doing for now. I want to leave that stuff for the very end when I gather enough help and support for failog and and ninja.

I got the basic security down pat. I'm more interested in the advanced security packages and tools that I mentioned earlier.

It's been slow going, but I have not made any terrible mistakes yet. I want to do this piecemeal in stages over a couple of days to test out how everything works under normal conditions.

I need more people to reply with answers and support.

---

### Post by SeijiSensei on 2012-11-29
I'll just say that I've run Linux servers that are exposed to the Internet day in and day out for over fifteen years and never did any of the things you seem to think are important.  Other than a carefully-written set of iptables rules that allow only specific types of connections, there is nothing else running from a security perspective.  I had one hacking incident a decade ago because I failed to keep Apache up to date.  That's it.

Now desktop usage can be more dangerous if you visit dicey sites, but I don't.  I did encounter the Javascript-based phony virus scanner ("Antivirus 2010") while reading an article at the *New York Times*, but it was pretty obviously a scam: the application claimed to be scanning my "C:" drive!

---

### Post by Welly Wu on 2012-11-29
Keep those replies coming because I am gaining valuable knowledge. I plan to work on GUFW and my iptables tomorrow afternoon. I already have a list of iptables connection rules that I need. I do keep my Ubuntu 12.10 64 bit desktop up to date to the second. I did read the basic security guide and I followed most of the recommendations and guidelines. So, I should be very safe and secure right now which I am. I just want to kick it up a notch or two. I want to deepen my knowledge of Ubuntu security packages and tools and I want to harden and lock down my Ubuntu desktop to make it reasonably safe and secure to use on a daily basis. I am willing to trade in convenience for security.

On Saturday, I plan to look for custom Novell AppArmor profiles for Mozilla Firefox and Google Chromium. I will create a new thread for them for Ubuntu 12.10 64 bit.

---

### Post by Hungry Man on 2012-11-30
I'd be willing to work with someone on an 'Advanced Security' wiki for users if that's what's being asked for.

> Let me be clear: my goal with this thread of mine is to achieve a reasonably strong desktop security that covers most of the bases in the security sticky threads. I need to be told when I am crossing the line and I am going overboard based upon further replies that I make or others contribute in this thread. Thank you.
I would say anything beyond the basic security wiki is overboard for a typical user. The wiki explains AppArmor, which will make systems pretty secure with only a bit of effort.

Beyond that I think it ends up recompiling the kernel from source with PaX and Grsecurity. Using a minimal install and manually selecting packages to reduce attack surface. Creating user/group for applications and configuring IP tables to work with it, along with various other ACL functions.

Ninja sounds like a pain in the *** to deal with. I'd rather set up RBAC via Grsecurity as that patch will more completely prevent privilege escalation.

I'd be willing to work on an Advanced Security Wiki that goes in depth into more difficult and time consuming ways to secure a system if there's some demand for that.

---

### Post by Welly Wu on 2012-11-30
I can't help you to author the advanced security guide for Ubuntu.

I do agree that I am going overboard with security again, but this is my nature and I am going to proceed.

I just modified my IP Tables using GUFW so I have all of the ports and protocols configured the way that I need them to work for my specific usage case. This should be the remaining steps that I need to take to harden and secure my Ubuntu 12.10 64 bit installation from the basic security guide. The next thing that I am going to work on is Novell AppArmor profiles on Friday afternoon. I plan to look at Bodhi Zazen's custom Novell AppArmor profiles along with yours and Rookcifer.

Expect a lot of questions and I need lots of help and support.

I know that my Ubuntu 12.10 64 bit installation is very secure right now. I am very safe from most attackers because well nobody is targeting me for an attack to my knowledge. I monitor my logs and my network traffic from my router to my Ubuntu.

Indulge me by continuing to post replies and suggestions. Expect me to continue my hardening process over the next two weeks.

---

### Post by Soul-Sing on 2012-11-30
You'r doing great monitoring your system. Learn to interpret the outcomes.
Do use Wireshark: enable networkname resolution via preferences. Learn to add rules via Wireshark into iptables. That can be done via Wireshark using netfilter/iptables.

---

### Post by Welly Wu on 2012-11-30
Whose custom Novell AppArmor profiles should I go with for Google Chromium, Mozilla Firefox, MPLayer, X-Chat, Open Java, Pidgin, etc.? Rookcifer has the most comprehensive, but they work with Ubuntu 12.04. I have not tried Hungry Man's yet. Bodhi Zazen has some old profiles for Ubuntu 10.04. Who else should I consider? What about the default profiles provided in Ubuntu 12.10 64 bit?

Can someone please tell me what works for Ubuntu 12.10 64 bit?

---

### Post by vasa1 on 2012-11-30
> **Welly Wu said:**
> Whose custom Novell AppArmor profiles should I go with ...
Wouldn't the appropriate "custom" profile be the one you construct yourself, *ab initio*?

---

### Post by Welly Wu on 2012-11-30
I'm going to wind up creating a custom Novell AppArmor profile that is too restrictive and it will break functionality with the said software applications. I've done this before with VM Ware Workstation 9.0.1 64 bit and my guest virtual machine got corrupted. I had to re-install it from scratch.

I would rather look at someone else's custom Novell AppArmor profile and import it and enforce it. It's going to save me time and effort.

---

### Post by Welly Wu on 2012-12-01
I see that Ubuntu 12.10 64 bit ships with basic Mozilla Firefox and Google Chromium Novell AppArmor profiles. I am having problems with the Google Chromium Novell AppArmor profile. Google Chromium won't launch after I enforce it. How do I modify it so that it will launch properly?

---

### Post by Welly Wu on 2012-12-01
I imported and enforced StoneCold1995's Novell AppArmor profile:

[http://ubuntuforums.org/showthread.php?t=2065866&highlight=chromium+apparmor&page=2](http://ubuntuforums.org/showthread.php?t=2065866&highlight=chromium+apparmor&page=2)

It works.

I also installed apparmor-profiles and I enforced smbd, nmbd, evince, xchat, Mozilla Firefox, and StoneCold1995's Google chromium Novell AppArmor profiles.

It works.

I know that these provide only basic protection, but I am quite happy with that for now. I plan to learn more about Novell AppArmor next week so that I can create more custom and powerful AppArmor profiles myself.

---

### Post by KiwiNZ on 2012-12-01
My opinion, if one goes to over kill mode with regards to a home PC you will ruin your computing experience to the point where you might as well turn it off put in a a box and read the newspaper and start playing sports.

I would not recommend 90% of this stuff to home users and 50 % to a security dependant corporate.

If one exercises common sense in "browsing habits" and computer practice you do not need this stuff, after for 95% of home users what is someone going to get, pics of the family and shoe size.

---

### Post by Ms. Daisy on 2012-12-01
Welly Wu, if you're doing all of this strictly to learn, then go for it.  But the whole point of learning is to go through the process. I'd encourage you to build your own profiles, you'll learn more about what apparmor is doing & how it's doing it that way.

If you doing it because you feel you need this much security, then I encourage you to take a step back & identify the actual threats to your system. Once you identify your biggest risks then just defend against those things. There's no point in securing against an attack that will never come.

---

### Post by Welly Wu on 2012-12-01
I got a lot of confidential and critical data on my drives that I can not share with anyone. Thus, I need extra high security. I think that I have mentioned this before in another thread. Basically, my System76 PC is my life and I live on the Internet.

I want to work on fwSnort and PSAD tomorrow afternoon. I am new to these topics so I will do lot of reading and research and I will ask a lot of questions.

I am reading the official Ubuntu Security guide: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security). It's pretty good and it covers a lot of the topics in the security sticky except the documentation is clearer to understand and to implement.

I'll be reading it throughout today.

I installed the libdvdread4 package and I executed the install.sh script. Now, I am able to copy my massive DVD-Video disc library and convert them into tiny compressed .M4V video files. This is good for me.

I am going to finish my CrashPlan+ initial remote data backup by December 16th, 2012 at 11:30 PM EST or much sooner. I'm working on a 64.4 GB VMDK flat file right now and it's about 90 percent done. Hopefully, there won't be a ton of new data on my /home folder to backup and data de-duplication will kick in which will speed up my total backup time quite dramatically. I've been waiting for this to happen all week since I re-installed Ubuntu 12.10 64 bit from scratch this past Monday.

So, I have a comprehensive data backup plan in place for emergencies and disasters.

My Ubuntu 12.10 64 bit installation is quite secure now. I still need to add NIDS using fwSnort and PSAD tomorrow.

I'm looking into Stricter Defaults, Bastille Linux, and MyDLP today. If I have questions, then I will post them here.

---

### Post by KiwiNZ on 2012-12-01
You use a Laptop I assume these are portable drives, disconnect them when not in use or turn off net access when using them. Easy.

To anyone looking at this, excessive security for home use is ill advised, it will bog your PC's down and its a waste of time and or money.

---

### Post by Welly Wu on 2012-12-01
I've been doing a CrashPlan+ initial remote data backup since October 26th, 2012 at 1 AM EST. I expect to be done by Sunday, December 16th, 2012 at 11:30 PM EST. I need to keep my System76 PC and all of my drives mounted and unlocked during this time. Otherwise, it will take much longer to complete the initial remote data backup.

---

### Post by SeijiSensei on 2012-12-01
> **Welly Wu said:**
> I got a lot of confidential and critical data on my drives that I can not share with anyone.

Isn't the solution for this problem simply to use an encrypted disk partition?

I have to second the comments above mine.  If people are reading this thread and thinking this is what is required to have a "secure" version of Ubuntu, it's not.

---

### Post by Bucky Ball on 2012-12-01
> **SeijiSensei said:**
> I have to second the comments above mine.  If people are reading this thread and thinking this is what is required to have a "secure" version of Ubuntu, it's not.

+1. Overkill.

---

### Post by Welly Wu on 2012-12-01
I downgraded to Ubuntu 12.04.1 64 bit LTS. I found a lot of the software packages that I wanted to use and other stuff were designed for it instead of 12.10 64 bit.

I think that I am done with security for now.

---

### Post by Bucky Ball on 2012-12-01
> **Welly Wu said:**
> I think that I am done with security for now.

In that case, could you please mark thread as 'Solved' from Thread Tools. Cheers and good luck. ;)

---

### Post by Stonecold1995 on 2012-12-01
> **SeijiSensei said:**
> Isn't the solution for this problem simply to use an encrypted disk partition?

This is exactly what I'm thinking.  Without encryption most of the security plans you have are rendered useless.  Even with encryption there's still the fact that /boot must remain unencrypted, which opens up the possibility of a kernel rootkit because the kernel is completely unsecured.  To reduce the possibility of this I use a shell script I made based on another already existing (and extremely useful) one that checks to make sure the contents of /boot haven't changed.  I attached the script to this post if you're interested (it currently requires KDE but could be modified for other DEs).  Of course there's also the threat of a cold-boot attack, and only the TRESOR (TRESOR Runs Encryption Securely Outside RAM) kernel patch can prevent that, but it's only for older kernels.

Encryption is everything.  Only encryption (in combination with common sense of course) gives even a remote chance of fending off a physical attack.

---

### Post by Soul-Sing on 2012-12-02
> **kiwinz said:**
> you use a laptop i assume these are portable drives, disconnect them when not in use or turn off net access when using them. Easy.

To anyone looking at this, excessive security for home use is ill advised, it will bog your pc's down and its a waste of time and or money.

+1

---

### Post by Welly Wu on 2012-12-03
I did not like Ubuntu 12.10 64 bit so I decided to re-install Ubuntu 12.04.x 64 bit LTS from scratch bare metal on my System76 Lemur Ultra Thin (lemu4) notebook PC. This time, I followed the basic security guide carefully and I am not doing any of the more advanced security stuff. My Ubuntu desktop is usable now. I have not locked myself out and it does not fail to function properly. This is as far as I am willing to go with security for now. I may decide to import Rookcifer's custom Novell AppArmor profiles later on, but I chose to stick with the default Ubuntu Novell AppArmor profiles provided by the apparmor-profiles package. So far, I have no problems.

If it ain't broke, then don't fix it! It was a particularly hard lesson for me to learn, but I have learned it now.

---

### Post by Welly Wu on 2012-12-07
I changed my mind. I upgraded to Ubuntu 12.10 64 bit again. I wanted to stay up to date with the latest Ubuntu stable version release at this time.

Looking back, I can now see that my biggest mistake is that I am going too overboard with security. Ubuntu is fairly secure after the default installation is done, but the basic security guide hardens it sufficiently for most average home desktop users like myself. I find that the security sticky threads are nice to read and they have value for others, but they don't concern my case usage and my needs or preferences. I really don't want to go back to re-reading those security sticky threads and following the recommendations all over again only to mess up my Ubuntu installation and have to re-install it from scratch again. It's not worth it for the additional security. I'm not running Ubuntu Server. I have no servers installed or running like VNC, Apache, or Samba or VSFTPD. I'm just a casual home user.

I feel comfortable now. I think that I can manage to keep this Ubuntu 64 bit installation and upgrade it smoothly to newer versions every 6 months in April and October of each successive year without having to re-install everything from scratch. That's what I would prefer to do. I like staying up to date with Ubuntu releases because I like new features and capabilities.

The basic security guide is really good enough for me. It's easy to read and to understand and it's easy to implement. I know that my Ubuntu 12.10 64 bit installation is very secure right now without making more compromises in usability. I finally got my GUFW firewall list of rules set and I know how to make modifications based on future needs safely without opening holes. I've got BitDefender for Unices Free anti-virus and I know what sudo is doing all of the time. I limit privileges to the bare minimum for almost everything. I monitor my logs especially my router and network logs daily.

I created a second backup administrator account. The reason why I did this is just in case I run into an emergency or a disaster and I need a second administrator account to do admin stuff if my existing administrator account does not work properly. I'm going to log into it to check that it's working now.

---

### Post by Welly Wu on 2012-12-07
My second administrator account works. I just logged in successfully. I'm going to keep it just in case there's something wrong with my primary administrator account which I am using right now. I've made a ton of mistakes while learning how to use GNU/Linux especially with Ubuntu in the past. I've locked myself out or I've made it impossible for me to login as any user in the past because I've gone way overboard on security.

I've learned some hard lessons as I have gotten older. I'm done with my security hardening process now.

I installed the harden packages from the Ubuntu Software Center. I know that they won't make me invincible, but they do improve the security quite a bit with little to no user intervention. I turned off telnet as an example.

What do you think about the harden packages in the USC?

---

### Post by Jason80513 on 2012-12-07
Missing from the security wiki is the suggestion to turn off most or all browser plugins. Flash is no longer supported in any browser on Linux other than Chrome, where it is being specially installed, just for Chrome, by Google. The other Flash install is not supported and known to be compromised. Also the Java browser plugin, which most people simply don't use for anything, has recently had a bunch of very serious vulnerabilities found and fixed. But it is best to turn it off. 

These things are particularly easy to turn off if you use FireFox for general browsing and Chrome for known safe sites where you need Flash.

...

After reading the 3rd page of messages, yeah, you are looking at the wrong thing. You are trying to harden your laptop like it's a server. You need to harden it like it's a laptop. The biggest threats you face to getting hacked are through your browser and other network connected clients. Mostly the browser, especially if you have scripting turned on and have installed plugins.

---

### Post by Welly Wu on 2012-12-07
I have the QuickJava 1.8.0 extension add-on which allows me to turn on or off Javascript, Java, Flash, Silverlight or Novell Moonlight, images, CSS, and proxies at the touch of a button. I also have the apparmor-profiles package installed and I set both the Google Chromium and Mozilla Firefox Novell AppArmor profiles to enforce mode for extra security.

Here is my list of Mozilla Firefox extension add-ons:

Adblock Plus 2.2.1
BetterPrivacy 1.6.8
Click&Clean 4.0
Delicious Bookmarks 2.3.4
DoNotTrackMe 2.2.5.1205
Evernote Web Clipper 5.4
FEBE 7.0.3.5
Force-TLS 3.0.1
HTTPS Everywhere 3.0.4
Ghostery 2.8.3
Global Menu Bar Integration 3.6.4
LastPass 2.0.0
Malware Search 0.9.4
NoScript 2.6.3
Novell Moonlight 3.99.0.3
QuickJava 1.8.0
Send to Kindle for Mozilla Firefox 1.0.2.54
Test Pilot 1.2.2
Ubuntu Firefox Modifications 2.6
Unity Desktop Integration 2.4.1
Unity Websites integration 2012.10.12 beta
WOT 20120926
Yoono 7.7.17

It's a long list, but it's features rich and I certainly have a very hardened and secure Mozilla Firefox web browser. My NoScript white list is checked daily and I remove unnecessary or unused exceptions daily. I make a full Mozilla user profile backup using FEBE every midnight and I copy that backup to Box.com, Ubuntu One, Google Drive, and Microsoft SkyDrive nightly.

I'm safe and secure.

---

### Post by Welly Wu on 2012-12-07
I also have WiTopia personal VPN PRO and basic subscriptions and I connect to their Washington, DC VPN gateway which features Blowfish CBC mode 256 bits 16 rounds with SHA-512 hash algorithm encryption using SSL certificates and the OpenVPN protocol every single time I use my System76 PC and GNU/Linux.

---

### Post by Welly Wu on 2012-12-07
This is my list of Mozilla Firefox plug-ins:

Shockwave Flash
Skype button for Kopete
IcedTea Web Plug-in
DivX web player
QuickTime Plug-In 7.6.6
VLC Multimedia Plug-in
Windows Media Player Plug-in 10
Google Talk Plug-in Video Accelerator
Google Talk Plug-in
Gnome Shell integration
iTunes Application Detector
Silverlight Plug-in

---

### Post by Jason80513 on 2012-12-08
Yeah, with that list of plugins, you aren't that safe and secure. Every one of those has potential exploitable vulnerabilities, and all can be accessed by any web page you visit.

At the very least, turn off icedtea and flash. I am a Java developer, and I won't even turn on the icedtea plugin. :D

---

### Post by Welly Wu on 2012-12-08
I watch a lot of videos on YouTube and other websites like Vimeo so I need Adobe Flash. I also need IcedTea plug-in because I do business with HD Tracks at [http://www.hdtracks.com](http://www.hdtracks.com) to purchase high resolution music albums at a premium price. They use Java and JavaScript to download the premium content to my PC over the Internet. It's their own custom Java applet named HD Tracks Download Manager.

---

### Post by Welly Wu on 2012-12-08
I also installed OpenJava JDK 7, IcedTea Web Start Plug-in, and IcedTea Web Start. I found out that HD Tracks won't work without these software packages installed in Ubuntu 64 bit GNU/Linux and Mozilla Firefox won't work without them with the HD Tracks website. I plan to do some holiday shopping with AIX Records for more high resolution music albums and they require the same technologies to purchase and download premium content. I do business with these online record stores fairly frequently.

---

### Post by Merisi on 2012-12-09
> **Welly Wu said:**
> I have the QuickJava 1.8.0 extension add-on which allows me to turn on or off Javascript, Java, Flash, Silverlight or Novell Moonlight, images, CSS, and proxies at the touch of a button. I also have the apparmor-profiles package installed and I set both the Google Chromium and Mozilla Firefox Novell AppArmor profiles to enforce mode for extra security.

Here is my list of Mozilla Firefox extension add-ons:

Adblock Plus 2.2.1
BetterPrivacy 1.6.8
Click&Clean 4.0
Delicious Bookmarks 2.3.4
DoNotTrackMe 2.2.5.1205
Evernote Web Clipper 5.4
FEBE 7.0.3.5
Force-TLS 3.0.1
HTTPS Everywhere 3.0.4
Ghostery 2.8.3
Global Menu Bar Integration 3.6.4
LastPass 2.0.0
Malware Search 0.9.4
NoScript 2.6.3
Novell Moonlight 3.99.0.3
QuickJava 1.8.0
Send to Kindle for Mozilla Firefox 1.0.2.54
Test Pilot 1.2.2
Ubuntu Firefox Modifications 2.6
Unity Desktop Integration 2.4.1
Unity Websites integration 2012.10.12 beta
WOT 20120926
Yoono 7.7.17

It's a long list, but it's features rich and I certainly have a very hardened and secure Mozilla Firefox web browser. My NoScript white list is checked daily and I remove unnecessary or unused exceptions daily. I make a full Mozilla user profile backup using FEBE every midnight and I copy that backup to Box.com, Ubuntu One, Google Drive, and Microsoft SkyDrive nightly.

I'm safe and secure.

You might be interested in looking at Request Policy, RefControl, Browser Protect and cookie whitelist with buttons.  They're quite underated addons and  find they help ensure my privacy esp having control over which websites are allowed to add cookies.  I think you'd appreciate at least taking a look at them.

---

### Post by Welly Wu on 2012-12-09
I installed Request Policy and Browser Protect. I set up another white list for Request Policy. So far, it's working properly. Now, I am fully protected and secure using Mozilla Firefox!

---

### Post by Stonecold1995 on 2012-12-09
That's a lot of extensions...  You should know that more extensions just means more surface area for attackers to find exploits, even if you are using a lot of "security enhancing" extensions.  Plus many extensions send information back to the authors/advertising companies and/or insert ads into your browser (which you may not notice if you have AdBlock/ABP).  In addition to that, they can take up a lot of memory and slow down your browser.

I suggest you try using UserScripts.  They are usually very small and open source (you can view the source on the very page you install it from), and also take far less memory, and yet can be extremely useful.

You should also try removing redundant extensions, like "Force TLS" and "HTTPS Everywhere", because they do the same thing, but using both together increases surface area for attack and may slow down browsing.  Just use one or the other (I recommend HTTPS Everywhere).

And never say you're "safe and secure".  A determined hacker will get past those security measures, and a malicious site will be blocked simply with NoScript alone.  You can only enhance security, not make yourself invincible.

---

### Post by Welly Wu on 2012-12-09
I know that I'm not invincible! Where did you ever see me post that I am invincible?

All of these extensions and plug-ins do increase my attack surface, but I have researched each one of them carefully and they are safe to use with one another and they do provide significant privacy and security features that I believe are well worth it. I have a moderately powerful System76 Lemur Ultra Thin (lemu4) notebook PC so it can handle a full featured Mozilla Firefox web browser with these extensions and plug-ins without any problems. I have not had one single instance of Mozilla Firefox crashing so far.

I like these extensions and plug-ins and I will keep them. Thank you.

---

### Post by Welly Wu on 2012-12-09
Force TLS is different from HTTPS Everywhere. They are two different IETF RFC 5246 standards and protocols. HTTP and HTTPS are much more common and frequently used standards and protocols than TLS, but TLS is important for business commerce especially regarding cryptography, message authentication, instant messaging, VOIP, etc. Yoono requires TLS for Yahoo! Instant Messenger, Google Chat, and AOL Instant Messenger. I also use VOIP in Mozilla Firefox with specific colleagues and friends.

There's a reason why I installed these specific extensions and plug-ins in Mozilla Firefox. I may not let on any further.

---

### Post by haqking on 2012-12-09
> **Welly Wu said:**
> Force TLS is different from HTTPS Everywhere. They are two different IETF RFC 5246 standards and protocols. HTTP and HTTPS are much more common and frequently used standards and protocols than TLS, but TLS is important for business commerce especially regarding cryptography, message authentication, instant messaging, VOIP, etc. Yoono requires TLS for Yahoo! Instant Messenger, Google Chat, and AOL Instant Messenger. I also use VOIP in Mozilla Firefox with specific colleagues and friends.

There's a reason why I installed these specific extensions and plug-ins in Mozilla Firefox. I may not let on any further.

They use the same thing (TLS) which superseded SSL, it is just there is a difference between the add-ons in terms of configurability, the protocols used are the same HTTPS

---

### Post by Welly Wu on 2012-12-09
Force TLS does indeed have different configuration options than HTTPS Everywhere. This is true. TLS does replace SSL in terms of functions in many regards and this is also true. However, TLS is not the same as HTTPS. There are overlapping similarities in terms of the specifications and the functions, but they are two distinctly separate network standards and protocols.

Right now, I am using all of these extensions and plug-ins for Mozilla Firefox and I don't have any problems on my Verizon FiOS fiber optic home Internet network. The performance is about the same, but Mozilla Firefox does consume more RAM. The most important security feature is the Novell AppArmor profile for Mozilla Firefox. I am not done configuring it. I may wind up importing Rookcifer's custom Novell AppArmor profiles for Mozilla Firefox and testing them to see if any functions break compatibility, but I will work on that in the near future. Novell AppArmor is my last layer of defense if my Mozilla Firefox web browser is under attack.

---

### Post by haqking on 2012-12-09
> **Welly Wu said:**
> Force TLS does indeed have different configuration options than HTTPS Everywhere. This is true. TLS does replace SSL in terms of functions in many regards and this is also true. However, TLS is not the same as HTTPS. There are overlapping similarities in terms of the specifications and the functions, but they are two distinctly separate network standards and protocols.

.

ForceTLS is an add on which forces connections over HTTPS (the s meaning secure and uses TLS) which is the same function as HTTPS everywhere.

HTTPS uses TLS

Both add-ons use the same protocol (HTTPS) they just provide different configurations.  The difference being the use of STS

From the Author of ForceTLS:

> **Force-TLS **allows web sites to tell Firefox that they should be served via** HTTPS **in the future

---

### Post by Welly Wu on 2012-12-09
Alright. I stand corrected. Forgive me. I'll remove Force TLS now.

---

### Post by haqking on 2012-12-09
> **Welly Wu said:**
> Alright. I stand corrected. Forgive me. I'll remove Force TLS now.

I wasnt telling you to remove it, you do what you like, I was just letting you know that the "protocols" used are the same.

If both are working fine alongside each other then by all means use them, but just remember that both add-ons use HTTPS

---

### Post by Welly Wu on 2012-12-09
I already removed Force TLS extension and I restarted Mozilla Firefox. I just synced my Mozilla account. At midnight tonight, FEBE will do another backup of my complete Mozilla Firefox profile and it will upload it to my Box.com account. Then, Ubuntu One will synchronize the folder where I store my FEBE backup instantly. CrashPlan+ will detect the changes in the folder and files and it will upload the new files to my account soon after midnight. Tomorrow, I will do administrative work on that folder and I will upload it to my Google Drive and Microsoft Sky Drive.

It's a lot of backups, but my data is safe and secure.

Web of Trust is very helpful. WOT tells me which websites are shady and which ones are safe and reputable based on its users feedback that is compiled into their database. If I can get some intelligence about which websites that I want to visit before clicking on urls, then it will help me to avoid websites filled with malware or attack vectors. You should try WOT extension. It's really good and beneficial.

---

### Post by Stonecold1995 on 2012-12-09
> **Welly Wu said:**
> I know that I'm not invincible! Where did you ever see me post that I am invincible?

All of these extensions and plug-ins do increase my attack surface, but I have researched each one of them carefully and they are safe to use with one another and they do provide significant privacy and security features that I believe are well worth it. I have a moderately powerful System76 Lemur Ultra Thin (lemu4) notebook PC so it can handle a full featured Mozilla Firefox web browser with these extensions and plug-ins without any problems. I have not had one single instance of Mozilla Firefox crashing so far.

I like these extensions and plug-ins and I will keep them. Thank you.

I never said you claimed you were invincible, you just said "I am safe and secure" and I replied saying that you are not secure from a determined hacker, but only from some passive threats.  Then I mentioned that you can only enhance, not perfect, your security.

I didn't say they weren't safe to use with each other (although I didn't research their interactions either).  And redundant things like Ghostery and BetterPrivacy add no additional security at all (I use DNT+ for Chrome personally).  Also, if I remember correctly, NoScript can take the place of BetterPrivacy, DoNotTrackMe, and maybe Force TLS/HTTPS Everwhere (I think).  Maybe also others but I don't what your other extensions do.  NoScript is extremely good and really versatile, it can replace many other security extensions.

> **Welly Wu said:**
> Force TLS is different from HTTPS Everywhere. They are two different IETF RFC 5246 standards and protocols. HTTP and HTTPS are much more common and frequently used standards and protocols than TLS, but TLS is important for business commerce especially regarding cryptography, message authentication, instant messaging, VOIP, etc. Yoono requires TLS for Yahoo! Instant Messenger, Google Chat, and AOL Instant Messenger. I also use VOIP in Mozilla Firefox with specific colleagues and friends.

There's a reason why I installed these specific extensions and plug-ins in Mozilla Firefox. I may not let on any further.

HTTPS is just a secure HTTP connection.  During connection, a client may request a secure connection (simply by going to the HTTPS URL), in which case the client tells the server the highest TLS version it supports in a ClientHello message.  The server then sends a ServerHello message with the highest TLS version it also supports.  Then an encrypted connection is made using the highest protocol versions both parties support.

TLS is just an improvement on SSL, they aren't different in terms of purpose (only strength).  So HTTPS Everywhere and Force TLS do the exact same thing, they redirect you to https://example.com from http://example.com if that site supports a secure connection.

HTTPS just means secure connection, SSL and TLS are just protocols that can be used for HTTPS.  So it's TLS vs SSL, not TLS vs HTTPS.

Just a note on secure: You have to be careful with HTTPS because, even if it says it's secure, if it uses the RC4 or DES encryption algorithm with MD5 message authentication, it is really not very secure.  RC4 is the same as what's used in Microsoft Office document encryption, WEP security for routers, and encrypted peer connections in the BitTorrent protocol (which are known to be insecure).  DES was cracked years ago by the EFF due to very short key length, and RC4 is easy to crack both because of short key length (I think) and numerous attacks it is vulnerable to.  Sites that use AES, Triple DES, Camellia, etc are much more secure, and brute forcing would be very infeasible in that case.

---

### Post by Welly Wu on 2012-12-09
Thank you for the lesson. I do know it. I have many IT certifications:

CompTIA A+, Network, Security+, Cloud
(ISC)2 CISSP CBK
CEH
BSD, VM Ware, Ubuntu Certified Professional
MCSA

I admitted that I made a mistake in confusing HTTPS and TLS.

Ghostery and BetterPrivacy do allow me to delete LSOs and Flash cookies on demand or when I quit Mozilla Firefox, but Ghostery has its own online databases for cookies and 3pes which it automatically updates and maintains. This helps me to filter out new elements automatically across a wider expanse of the Internet. Better Privacy allows me to override the default Mozilla Firefox method of handling cookies altogether and it's for this specific reason that I chose to add it and I use it.

I am happy to report that I am not a high value target of an advanced persistent threat by anyone in this world who is trying to attack me. Perhaps that itself is the best security feature in my favor right now.

---

### Post by vasa1 on 2012-12-09
> **Welly Wu said:**
> I know that I'm not invincible! Where did you ever see me post that I am invincible?
...
Post #40 has this:
> Now, I am fully protected and secure using Mozilla Firefox!
That would certainly give the impression the other poster got. And I agree with Stonecold that, after a point, having more extensions becomes meaningless if not detrimental.

---

### Post by Welly Wu on 2012-12-09
So, I take it that my fellow Ubuntu users are telling me that I am going overboard with the security features for Mozilla Firefox with an excessive number of extensions and plug-ins, correct?

Tell me what I should use and why and I will consider it.

---

### Post by haqking on 2012-12-09
> **Welly Wu said:**
> Thank you for the lesson. I do know it. I have many IT certifications:

CompTIA A+, Network, **Security+**, Cloud
**(ISC)2 CISSP CBK**
**CEH**
BSD, VM Ware, Ubuntu Certified Professional
MCSA

I admitted that I made a mistake in confusing HTTPS and TLS.

.

I have seen your previous posts, I would get your money back for the above LOL ;-)

---

### Post by Welly Wu on 2012-12-09
I wish that were possible at this point, but more than 6 months has passed since my last IT certification.

I switched to Ubuntu on January 4th, 2012. Previously, I was using Microsoft Windows XP and 7 for the past 11 years and I used Microsoft Windows 1.0 through ME in the previous decades.

One thing that I noticed is that CompTIA Security+ and (ISC)2 CISSP CBK rarely delved into GNU/Linux or BSD. They would have a scant chapter or none at all. So, I have book knowledge, but I have had to undergo a pretty serious learning curve to acclimate to GNU/Linux.

I don't have any problems with hardening Microsoft Windows and I have Windows 8 Pro 64 bit. However, I rarely use it. I only use Windows when it comes time to do Microsoft Patch Tuesdays.

My biggest problem with GNU/Linux security is trying to find out the context for security tools. I read man pages all of the time, but I am so used to the Microsoft way of managing security tools and I've developed the Windows mindset that it's still difficult for me to get away from it when I use Ubuntu.

I'm much more concerned about crashes and Ubuntu 12.10 64 bit is not the most stable or polished release version yet. I don't plan to downgrade to an earlier version and I don't plan to re-install Ubuntu from scratch bare metal again. I don't plan to switch to another GNU/Linux distribution either. I want to be able to contact System76 to get help and support in the future if I have a problem.

I have a server focused security Windows mindset. I used to be a systems administrator and we had access to multi tens of millions of dollars worth of super computers and servers.

It's not easy getting away from that background because I've been doing it for so long.

Sometimes I think that I'm using Ubuntu Server instead of Desktop.

For now, I think that I'm going to stop adding extensions and plug-ins for Mozilla Firefox. That would be the best next step before I start creating problems for myself. Hell, I'm surprised that my existing list of extensions and plug-ins hasn't caused any major problems so far!

The last thing that I want to do is to invite a penetration tester or cracker to target me. I've got enough problems in my life right now.

---

### Post by Welly Wu on 2012-12-09
I've told enough people about my personal business, but nobody has any business asking me about my career background.

---

### Post by Welly Wu on 2012-12-09
CompTIA Security+ and (ISC)2 CISSP CBK were mandatory and required by my former employer. CEH was optional but recommended to get a glimpse into the other side's mindset, tools, procedures, and gathering intelligence and carefully documenting invaluable data to test systems. It got a bonus and a raise after presenting my IT certifications one at a time especially these three which are still in high demand.

My life is different now. I'm heading in a different educational and career path. I don't want to be held liable in a court of law for my own mistakes or someone else's collateral damage. I can't afford hiring my own legal defense team and litigating in different courts with different jurisdictions and even different laws, rules, and regulations. It's become too charged with defensive litigation and plantiffs launch lawsuits as a weapon of attack without asking questions first. This is what drove many private companies out of business over the years. It also got a lot of people laid off or fired or forced out of work. I lost a lot of friends and colleagues that wound up in those situations. I was next in line over time. It's not worth it any more as a career path. I've become too cynical and jaded.

I'll continue to research, register and enroll, purchase, study, and pay for IT certifications that I think have potential, but I don't plan to submit my former resume to an IT recruiter in the future. I'd rather have the book knowledge without the actual work experience to avoid being implicated in a lawsuit.

That's enough general information for now.

I'm still new to GNU/Linux. My biggest problem is putting my Microsoft mindset behind me, but I find that I can't do this just yet.

---

### Post by KiwiNZ on 2012-12-09
This thread has reached end of life and is rotating, so we all don't get giddy....thread closed

---


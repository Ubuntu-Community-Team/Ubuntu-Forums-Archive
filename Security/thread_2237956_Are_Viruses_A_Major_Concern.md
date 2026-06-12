---
title: "Are Viruses A Major Concern?"
date: 2014-08-04
forum: Security
---

### Post by cedric9 on 2014-08-04
[COLOR=#000000]I'm relatively new to Linux, and right now I'm using Ubuntu 14.04 LTS on my old Pentium 4 with 1.5GB of Ram.  I would like to know [/COLOR]how big of a threat computer viruses are to Ubuntu 14.04?  I generally only use my machine to check my email, read the news, or to modify a few documents.  Is it necessary to install anti-virus software on my machine running Ubuntu?  Any advice appreciated.:-s

---

### Post by QIII on 2014-08-04
Let me preface this by saying that all the talk about Linux being bullet proof are myths.  Linux can be and has been attacked.  Some will say that Linux is too small a part of the market for people to bother with.  Nothing could be further from the truth.  Given that Linux powers the majority of the internet backbone, many Fortune 500 companies, your smart TV, many of the electronic subsystems your car, your cell phone (in the form of Android, which is a fork of Linux) there is a BIG incentive to hack in.  Linux, in some form or another, outnumbers Windows by a great margin.

But the Windows virus is foreign to Linux.  Its method of transmission won't work the same way.  But that doesn't mean that some pimply-faced youth in his mother's basement in Des Moines isn't hatching some Linux killer right now.  Don't get cocky like some people seem to.

But the fact that Windows viruses are generally not a problem for Linux (more on that in a minute) does NOT mean there is no malware out there that can cause you problems.  One of the best ways to get something like that wrapped around you machine is to do the same thing people do with Windows:  get convinced to install something you should not.  Social Engineering is just as dangerous for Linux users as Windows users.  Stick with the Canonical repos for your software to begin with.  If you find something you really want later, ASK FIRST before adding a source, a PPA or just building something from source.

Now, with regard to Windows viruses:  Be aware that you can still unwittingly pass a virus to your Windows friends in an attachement in an email, for instance.  

Don't take security for granted.

---

### Post by mooreted on 2014-08-05
A chain is only as strong as it's weakest link. I can run Windows all day every day and not get infected. It's basically a point of, "don't download crap from the Internet". You can run any operating system safely if you don't let yourself get sucked into anything. I could write a script right now, talk you into downloading and running it and screw up your system. Your best defense is knowledge. Don't run commands, download things, add repos unless you know what you are doing. Choosing to run Linux based on it's resistance to malware is not a very good approach. There are much better reasons to use Linux:

No NSA backdoors
Free as in beer and freedom
Highly configurable
You own it, not some corporation
It's very stable and powerful
It's relatively secure
It uses less resources
It runs faster than Windows or OSX

You could probably think of thousands of good reasons to use Linux. But, as shown above, the days of Linux being a small target are long past.

As to running Antivirus, I don't think there are many solutions right now that look for Linux malware. They will generally look for Windows malware on a Linux machine to prevent infecting your friend's computers. I'm sure someone is working on it.

For more information, check this out:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by claracc on 2014-08-05
I think a good start point to know about security in linux is this sticky:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 3rdalbum on 2014-08-05
QIII and mooreted are essentially correct. Their advice is fairly sound.

But most Linux users have no antivirus or antimalware software and yet there is no plague of Linux viruses. When I started in Linux in 2005 it was predicted that new viruses would soon be written for Linux and cause havoc - people keep predicting it and it keeps not happening.

My father didn't use much computer savvy on Windows and he got viruses twice. None on Linux.

I don't bother with antivirus on Linux, there are so few threats and nearly nobody gets them. I just don't engage in risky behavior online. If you were to do the same as me, I'm sure you would have no regrets.

---

### Post by The Spectre on 2014-08-05
If you really want or need an AntiVirus program ESET NOD32 AntiVirus 4 for Linux Desktop can detect Windows, Linux and Mac OS malware...

[http://www.eset.com/us/home/products/antivirus-linux/](http://www.eset.com/us/home/products/antivirus-linux/)

Unfortunately it isn’t open source or free but you can quite often find it at a great price at Amazon, NewEgg and eBay.
[IMG]http://static5.esetstatic.com/uploads/pics/3D-EAV-Linux_99b252_07.png[/IMG]

---

### Post by whitesmith on 2014-08-05
Protecting your system by using antivirus software is pointless according to the experts at Symantec. Read this piece in Ars before wasting money and CPU cycles on useless junk: [http://arstechnica.com/security/2014/05/antivurus-pioneer-symantec-declares-av-dead-and-doomed-to-failure/](http://arstechnica.com/security/2014/05/antivurus-pioneer-symantec-declares-av-dead-and-doomed-to-failure/). When security experts such as Symantec declare AV “dead” and “doomed to failure” it simply makes no sense to use them. As early postrs to this thread indicate, the best security comes from knowledge of your system. Still, take comfort from the design of *nix that makes attacks from script kiddies almost impossible, but of course the NSA can get into anything, as we have learned from Snowdon.

---

### Post by Rob Sayer on 2014-08-05
> **whitesmith said:**
> ... Read this piece in Ars before wasting money and CPU cycles on useless junk: [http://arstechnica.com/security/2014/05/antivurus-pioneer-symantec-declares-av-dead-and-doomed-to-failure/](http://arstechnica.com/security/2014/05/antivurus-pioneer-symantec-declares-av-dead-and-doomed-to-failure/). ...

Good article.  Surprised I missed that.

I agree with most of the above.  I have ClamTK installed for on demand scanning of dl'ed files because I still have one windows partition.  But I'm not really 100% sure about that because I've heard than clam is really meant for scanning email on servers.

One thing I'll definitely say ... I'm no real linux experts but I know guys who are.  They've used it as their home OS for 20 years, and it definitely wasn't that easy to install back then.  Not one of them uses an AV program in the background like you absolutely have to in windows.

Though I'll have to disagree with the "No NSA backdoors" statement.  There's absolutely no assurance of that whatsoever.  

Serious encryption involves very advanced math, number theory for example.  It doesn't help much if the encryption is open source if there are so few people who can understand it.  You could hide in plain sight, no problem.  That's how Enron cooked their books;).

In fact there was a bug in the Debian SSH encryption library a few years ago.  It took more than 2 years for anyone to find it.

---

### Post by VMC on 2014-08-05
Here's an interesting article from [Dedoimedo]("http://www.dedoimedo.com/computers/linux-av-cd.html") written 2011, but has good links to free LiveCD's

---

### Post by whitesmith on 2014-08-05
Rob Sayer: Heartbleed demonstrated the folly of depending on three PhDs to work on mission-critical *nix components for beer money. I think (repeat, think) that's finally been corrected by a consortium of large companies who now pay serious coin to developers of mission-critical stuff. As for protection against NSA backdoors, there's always some form of hash under which copies are released. If the SW is tampered with in transit, the published and computed hashes wouldn't agree. Hashes, of course, only protect against a man-in-the-middle attack. If someone from the NSA manages to corrupt the source of public builds, then all bets are off, but this seems an unlikely assumption. Still . . .

---

### Post by Elfy on 2014-08-05
*Thread moved to **Security**.*

Before this thread is closed for veering wildly offtopic into anything remotely resembling politics of any kind at all - keep it on topic for the OP. 

In all the time I've been using any sort of not-windows I've not worried about viruses at all in my situation.

---

### Post by bashiergui on 2014-08-05
> **cedric9 said:**
> [COLOR=#000000]I'm relatively new to Linux, and right now I'm using Ubuntu 14.04 LTS on my old Pentium 4 with 1.5GB of Ram.  I would like to know [/COLOR]how big of a threat computer viruses are to Ubuntu 14.04?  I generally only use my machine to check my email, read the news, or to modify a few documents.  Is it necessary to install anti-virus software on my machine running Ubuntu?  Any advice appreciated.:-s
You need to protect yourself, you just don't do that with anti-virus on Linux. If you're just using your computer for email, surfing and document editing, then the best way to protect your computer is:

1. Don't click on links in emails that you weren't expecting. Or if you know you'll have to click on strange links then never EVER enter your username or password on the website you go to.
2. Use an ad blocker and/or a javascript blocker in your browser. That's as simple as installing noscripts in Firefox and notscripts in Chrome. 
3. If you open a document from email or from some other source, even if it's malicious it probably won't affect your Linux computer. The only concern would be if the document asked for permission to do something, in which case you should NOT allow it. In other words, a document will never legitimately ask for your sudo password.
4. If you don't have a router or if you're using public wifi then turn on the ufw firewall to deny all incoming and allow all outgoing. 

That's really all you need to do to protect yourself.

---

### Post by cedric9 on 2014-08-06
Thanks for the great advice everyone.


So...if I understand things correctly, although Linux isn't absolutely "bullet proof" it sounds like I can minimize risk by avoiding software packages from non-Ubuntu repositories?  (I typically try to install only the bare minimum of packages anyway.)


Also, would activities such as reading and commenting on news, posting items for sale, and on line banking be considered risky behavior?  I only visit mainstream sites (no porn stuff) but I'm just wondering if you can pick something up from visiting a site like Craigslist, Yahoo, or ebay?

---

### Post by SeijiSensei on 2014-08-06
The one time I saw a piece of malware on my system was in 2009 when the New York Times was tricked into distributing a Javascript through its advertising channels.  When I closed the browser a window appeared that claimed to be scanning my non-existent "C:" drive for non-existent .dll files.  Naturally it found dozens of such files and offered to sell me an antivirus product to remove them.   I could only laugh. 

I've used Linux for about two decades now, and this was my only experience with malware on the desktop.  I visit the sites you mention fairly regularly and never have problems. I never use anti-virus on Linux desktops.  On servers I use ClamAV to scan incoming email and web objects.  Neither of those situations apply in your case.

---

### Post by mooreted on 2014-08-06
It is not likely that you will get infected by a drive-by install. We just want you to know that no system is perfect. Linux has more layers of security than Windows so you are safer running Linux. There are only 3 or 4 threats running around right now and almost all of them attack servers, not desktops. There are hundreds of thousands of threats attacking Windows desktops. Just from my own personal experience: In 12 years of using Linux I have never been infected with anything.

---

### Post by bashiergui on 2014-08-06
> **cedric9 said:**
> Also, would activities such as reading and commenting on news, posting items for sale, and on line banking be considered risky behavior?  I only visit mainstream sites (no porn stuff) but I'm just wondering if you can pick something up from visiting a site like Craigslist, Yahoo, or ebay?Yes. As seijisensei mentioned, mainstream websites occasionally get hacked, can also serve up malicious ads, can steal your cookies, etc. Hence this advice:

Use an ad blocker and/or a javascript blocker in your browser. That's as simple as installing noscripts in Firefox and notscripts in Chrome.

---

### Post by ventrical on 2014-08-06
> **Elfy said:**
> *Thread moved to **Security**.*

Before this thread is closed for veering wildly offtopic into anything remotely resembling politics of any kind at all - keep it on topic for the OP. 

In all the time I've been using any sort of not-windows I've not worried about viruses at all in my situation.

 I am of the ubuntu 'bulletproof' mindset. I am not saying that it is impossible. Just currently bulletproof.

 4 solid years of *ubuntu* testing, running ubuntu oriented av scanners, etc... and the only thing I got just recently was a fake pop-up on a youtube site and I clicked it just for fun and it did nothing.  The GRuB/Ubuntu kernel is the new UEFI emulator that works and provides honest security.

 Viruses and malware are not a major concern for Ubuntu.  Bugs ? Yes .. :) Virus/malware no.

  Ubuntu  gives cause to have a genuine cyber peace of mind.

  I just updated my AVG-Free  *summer update* on my Windows 7 box and I couldn't help think what jumpers were downloaded along with it.

Thats just me.

Regards..

---

### Post by craig10x on 2014-08-06
I agree with ventrical...been running linux since 2008, so that makes 7 years now...never got a single virus, trojan, malware, whatever...and never have used any kind of anti virus program on it...so, it's still pretty much bullet proof and haven't seen anything yet that would change that...

---

### Post by cedric9 on 2014-08-06
Thanks for the great advice everyone, I now feel like I have a better understanding of things, I think that I will look into installing noscripts in Firefox and notscripts in Chrome, and also using an ad blocker and/or a javascript blocker in browser.

---

### Post by bashiergui on 2014-08-07
[QUOTE=ventrical]Viruses and malware are not a major concern for Ubuntu. Bugs ? Yes ..  Virus/malware no.[/QUOTE]What do you think malware is if not exploits of bugs?

---

### Post by QIII on 2014-08-07
Bulletproof?

Heartbleed?

"The October of Java exploits"?

Virtual Machine sandbox jumping?

Maybe not Ubuntu specific, but they certainly all posed threats to your home Linux machines.

I haven't been compromised myself ... [I]&#8203;yet.  
[/I]
Many, many Windows users, me included, can say the same.
Prudence suggests that things like NoScript, ufw, etc., are good precautions.

---

### Post by ventrical on 2014-08-08
> **bashiergui said:**
> What do you think malware is if not exploits of bugs?

  The exploiters of *Ubuntu bugs* are practically non-existent (or better said , they are certainly not burning the midnight oil.

  I also disagree with your statement about malware.  Malware affects perfectly good lines of code. In fact , even the patches that try to lock down unassuming code is a form of malware. MicroSoft software products  (with it's authentication schemes) is probably the largest script of malware introduced on a system  today. And with Secure Boot and ELAM .. need I say more...yet with Ubuntu ... where .. show me.

Regards..

---

### Post by ventrical on 2014-08-08
> **QIII said:**
> Bulletproof?

Heartbleed?

"The October of Java exploits"?

Virtual Machine sandbox jumping?

Maybe not Ubuntu specific, but they certainly all posed threats to your home Linux machines.

I haven't been compromised myself ... [I]&#8203;yet.  
[/I]
Many, many Windows users, me included, can say the same.
Prudence suggests that things like NoScript, ufw, etc., are good precautions.

  I wouldn't disagree with your last statement - as I said - nothing is impossible but for the most part, in my own Ubuntu Shack, malware has been non-existent . I have used a variety of made-for-ubuntu scanners, Avast, Comodo, AVG  and nothing ever comes up except the EICAR Test. All my service calls are malware removal for Windows machines, not Ubuntu. In fact that is part of the larger reason why I took up Ubuntu. I just got so fatigued  removing malware from other peoples systems .. and that is not what I went to University for.

Regards..

---

### Post by ventrical on 2014-08-08
Just for fun I installed ComodAV on a 12.04.4 release that got a lot of use and abuse and it's still the same olde yawner.....

---

### Post by bashiergui on 2014-08-09
> I also disagree with your statement about malware. Malware affects perfectly good lines of code. Fair point. If you set your password to "password" then I can exploit good lines of code. When you configure your ftp server to allow anonymous logon, again I can exploit good lines of code. If I script those exploits then...ta da! I have written malware to exploit good lines of code.> The exploiters of *Ubuntu bugs* are practically non-existent (or better said , they are certainly not burning the midnight oil.Sure, Windows is far more targeted. Bad actors want to exploit Windows and any kind of server.  So the risk of an Ubuntu desktop running no services getting exploited is pretty low. 

But do not misunderstand: there are plenty of Ubuntu exploits developed and packaged in Metasploit right now. A google search can find them. They definitely exist. It's pretty simple to exploit bugs in Ubuntu using Metasploit. It's also pretty simple to prevent them. Apply updates regularly and those bugs can't be exploited.

Believing no one will exploit a bug in Ubuntu leads you to erroneously believe there's no point in patching. Totally wrong thinking. Keep your system patched and then it never matters if people start exploiting Ubuntu bugs in the wild.

---

### Post by VE6EFR on 2014-08-09
> **bashiergui said:**
>  It's pretty simple to exploit bugs in Ubuntu using Metasploit. It's also pretty simple to prevent them. Apply updates regularly and those bugs can't be exploited.

Believing no one will exploit a bug in Ubuntu leads you to erroneously believe there's no point in patching. Totally wrong thinking. Keep your system patched and then it never matters if people start exploiting Ubuntu bugs in the wild.

I couldn't agree more. This is the main reason I have my system automatically check for security updates daily as well as download and install them automatically. This way my system stays secure without my intervention.

---

### Post by ventrical on 2014-08-09
> **bashiergui said:**
> Fair point. If you set your password to "password" then I can exploit good lines of code. When you configure your ftp server to allow anonymous logon, again I can exploit good lines of code. If I script those exploits then...ta da! I have written malware to exploit good lines of code.Sure, Windows is far more targeted. Bad actors want to exploit Windows and any kind of server.  So the risk of an Ubuntu desktop running no services getting exploited is pretty low. 

But do not misunderstand: there are plenty of Ubuntu exploits developed and packaged in Metasploit right now. A google search can find them. They definitely exist. It's pretty simple to exploit bugs in Ubuntu using Metasploit. It's also pretty simple to prevent them. Apply updates regularly and those bugs can't be exploited.

Believing no one will exploit a bug in Ubuntu leads you to erroneously believe there's no point in patching. Totally wrong thinking. Keep your system patched and then it never matters if people start exploiting Ubuntu bugs in the wild.

  My comments were meant more for MS products, not Ubuntu. However ... we are veering off into other territory here.  It is known fact that Ubuntu updates/upgrades can completely bork a system , in LTS stage as well as development release (so yes .. patches will cause breakage and to a noob that may seem like malware.  Also , at the EOL of a  LTS release the end_user is presented with the option to upgrade to the next LTS milestone which in several cases has out-patched and obsoleted several types of various ATi, nVidia and Intel video drivers - a sure case where patches will do more harm than good.

  Practicing a *patching* concept in Ubuntu takes experience and expertise and those willing to learn this have to have a certain type of stamina and endurance. However , in my own experiences I have had great success with patching (keeping system updated) and have learned to lock down previous versions with older legacy systems that will not patch over successfully to  newer kernels or newer development releases. Simply put .. a lot of older PCs will not meet the specs when convergence in hemmed in.

 I'll look up on your suggest 'Metasploit' and make a comment later but I still think that viruses are not a major concern at this time with Ubuntu.  I'll reserve my reasons why. That does not mean to suggest to keep ones radar down and if that seems  to be what I have implied then I did not mean it in this way. But certainly know this ; that on an Ubuntu system an end_users downtime will be greatly reduced because the the general absence of malware targeted for it and also for the way the policykit is designed.


Regards..

---

### Post by bashiergui on 2014-08-10
> I still think that viruses are not a major concern at this time with Ubuntu. I completely agree. The point I was making was that it's not because exploits don't exist. It's just that no one is using them en masse.

As for patching, yes it can be challenging. I've had my fair share of issues. Kinda reminds me of this
 [ATTACH=CONFIG]255364[/ATTACH]

---

### Post by vasa1 on 2014-08-10
> **bashiergui said:**
> ...
Believing no one will exploit a bug in Ubuntu leads you to erroneously believe there's no point in patching. Totally wrong thinking. ....
Are you referring one rather popular distro that didn't (or doesn't) offer kernel updates at the "default" level?

---

### Post by aaditya2 on 2014-08-10
I've been using ubuntu for the past 3 years and i've never been affected with any virus.

i can only spot a few bugs even in the current version

---

### Post by bashiergui on 2014-08-10
> **aaditya2 said:**
> i can only spot a few bugs even in the current version
You've fuzzed every version and you only found a few bugs? LOL. Here are 6700 bugs currently categorized in 14.04. 
[https://bugs.launchpad.net/ubuntu?field.searchtext=14.04&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu?field.searchtext=14.04&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

To be clear: just because there's a bug doesn't mean there's an exploit for it. So no need to panic about 6700 bugs. To believe there are only a few bugs is just wrong.
> Are you referring one rather popular distro that didn't (or doesn't) offer kernel updates at the "default" level?
No, more of a general apathy or complacency towards patching. As for that distro, it's helpful to remember the old saying "Linux assumes you know exactly what you're doing."

---


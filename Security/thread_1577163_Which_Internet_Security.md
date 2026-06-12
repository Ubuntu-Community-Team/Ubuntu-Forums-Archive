---
title: "Which Internet Security?"
date: 2010-09-18
forum: Security
---

### Post by Bikekid450 on 2010-09-18
Hi can anyone tell me what is the best Internet Security to use with Ubuntu? I mean I can't find any that are compatible with Ubuntu :( I like KIS for Windows but it won't work in Ubuntu so I looked on here and on their website but they don't seem to do anything for it... So any suggestions guys?

Thanks. :)

---

### Post by HermanAB on 2010-09-18
Yes, do nothing.  Linux is not Windows.

Relax and enjoy your system.

---

### Post by Bikekid450 on 2010-09-18
Ooo, okay can I just ask so I can understand lol.

How do I know I have no Viruses Etc? 

I know it's obvious you don't download stuff willynilly but I do use PayPal and stuff on here so I'd just like to know and understand about these things. You have all been very helpful so far. 

Thanks.

---

### Post by amauk on 2010-09-18
[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)

---

### Post by Rubi1200 on 2010-09-18
As HermanAB already said, there is really no need for antivirus on Linux, much less the type of so-called security suites found in Windows.

However, if you are sharing files with Windows users you might want to consider using something.

See here for more information:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

You should be more concerned about securing your web browser. If you are using Firefox, I suggest the Mozilla addons NoScript and BetterPrivacy as a start.

---

### Post by Bikekid450 on 2010-09-18
Thanks :)

---

### Post by OpSecShellshock on 2010-09-18
Malicious code that is meant to run or install locally needs to be written specifically for whatever OS it's been designed to run on. It must then also get installed. As far as I know, there's not very much of that stuff designed to run on a Linux desktop, and consequently there are no tools for detecting such things. Stick to installing things from the official repositories, and if you must search out and use custom look and feel types of things (as we all must, from time to time), make sure that you only use folders in your home directory rather than dropping them into system directories, which requires privilege escalation. I know that some tutorials say you should put, for example, themes and icons in system folders, but that's really only necessary if you want them to be available to all users (and even that's unnecessary on a single-user system). Please note that the overwhelming majority of look and feel customizations are perfectly fine regardless of where they reside on the system. It's just good practice to not exceed what's necessary.

That leaves us with the browser, which would be the point of origin for malicious scripts that don't reside on the system, but that get rendered locally (in the same way that legitimate web content does). For that, there are browser add-ons (assuming that you're using Firefox). I'd recommend NoScript, BetterPrivacy, and AdBlock Plus. I would also suggest configuring the browser preferences to clear the private data when the browser is closed, and to at most allow cookies for the session, rather than permanently. All of these configurations will cause slight inconveniences while you're getting used to them, but they'll keep the ulcers at bay.

---

### Post by serverfarm on 2010-09-19
Take a look at ClamAV "Virus Scanner" in the software center.   Also, I would get a Firefox addon that shows reports about the webpage, something like "link extend", even thought it tests for windows viruses it probably means you shouldn't be visiting the site!

---

### Post by Bikekid450 on 2010-09-19
Thanks everyone, you're all very helpful :)

---

### Post by OpSecShellshock on 2010-09-19
To be honest, most of the link-checking and reputation tools aren't very reliable. The ones made by AV vendors might run some static analysis on the source code of pages when a subscriber submits them for review, but there's going to be a tremendous lag there given that content on the web (not to mention on a given site itself) is so dynamic. The rest of those tools rely on user reports, which in addition to meaning that users have to encounter them in the first place, also means that the information is only as reliable as those reporting it. Considering that so many people immediately leap from a page loading slowly to high malware alert status, that can cause panic where it isn't warranted when the little red dot shows up next to links.

Firefox already makes use of Google's safe browsing feature, so in the event that a site has been identified as dangerous,  by default you won't be able to get to it without having to pass through a warning page. Again, that only helps in the event of known issues, but the chances of anything outside of your home directory's .mozilla folder being affected are slim on this OS even if a page turns out to have bad stuff on it.

---

### Post by Bikekid450 on 2010-09-19
Thanks mate I'm taking all this info on board! :D

---

### Post by mr-woof on 2010-09-19
Personally I have clam av installed on this machine, privoxy is good for removing ad's etc. I also use Firefox with no script, adblocker, flash block :) 

Just randomly, I saw some stats the other day regarding viruses etc, apparently they say there will be 2 million pieces of spy/mal/virus ware by the end of the year and 99.6 of this is designed for windows machines!

---

### Post by OpSecShellshock on 2010-09-19
> **mr-woof said:**
> Personally I have clam av installed on this machine, privoxy is good for removing ad's etc. I also use Firefox with no script, adblocker, flash block :) 

Just randomly, I saw some stats the other day regarding viruses etc, apparently they say there will be 2 million pieces of spy/mal/virus ware by the end of the year and 99.6 of this is designed for windows machines!

Quite true (though different vendors count variants in different ways). By the middle of the second quarter this year there had already been as many samples submitted to AV vendors as in all of last year. What's particularly interesting is that it's kind of an evil mirror universe version of legitimate software development, except without the restrictions and legal frameworks that the legit side has to fall back on. Competition is quite fierce, certain code platforms fork and branch by the hour, some malware provides for technical support complete with call centers, and the interfaces are being designed so they can be used by low-level (cheap) operators. It's nothing to panic about, though.

---

### Post by adn258 on 2010-09-23
You don't need internet security.  I do get tired of people talking about viruses for linux and ubuntu in fact I think I will make a video of using the supposed linux viruses on my system as a virtual machine.  

You can download malware from a site called vxheavens.  (malware analysis - usually for windows is a little hobby of mine anyway) by looking at it's behavior.  

So anyway people are always thinking you can write a virus for mac linux etc. and it's just not done as much because they don't have nearly as much OS market share.  This is partially true but only about half true..

The operating system architecture of Ubuntu, Linux, Unix and Freebsd are by design much harder to write really good viruses or hacking tools trojans etc. for compared to WINDOWS.  This is true even of windows 7 because it's STILL WINDOWS.  This goes for Mac OSX which I use and like as well;  Mac osx is still MUCH MUCH SAFER BY DESIGN THAN WINDOWS.

I have been all over the internet not a virus yet on my mac that has affected it (some windows ones).  

Why is this?

OSX based on Freebsd and Ubuntu Linux have a harder architecture to puncture through, whilst windows based on MS-DOS never really has, and probably never will be very secure; it's dangerous BY IT'S VERY NATURE: windows is a dangerous OS.  

The reason windows is such a dangerous OS is because of things like the registry which are very easy for attackers to write viruses for and exploit.  I mean a kid could practically study some code and write a simple virus that edits some registry keys to probably hack there way into a windows machine.

Based on my assertion above I have two theories which we shall see if they come to light.  


Mac OSX and other fringe operating systems like Linux will become significantly MORE POPULAR as time goes on against windows.  

Linux and OSX included will have WAY LESS problems with malware EVEN AS THEY GAIN MARKET share compared to their counter part windows.

That all being said some "PROGRAMS" like browsers especially can be taken advantage of. IT would behoove you especially if you are going to seedy places online "porn", "downloading" "File Sharing" etc. to CLEAR YOUR BROWSING history and don't have browsers store passwords as I believe there are elite ways of stealing them.  This is a fault having nothing to do with Ubuntu though.  The odds of you running into malware specifically designed for linux and ubuntu in the wild though is so remote it's frankly not worth talking about AT THIS POINT.  I think you might have a better chance of winning the lottery then getting a virus from browsing the net and actually working to any significant degree for infecting your linux/ubuntu system.



Peace

---

### Post by dino99 on 2010-09-23
you seem to simply dont understand what "security" mean ADN...

if / is protected by design (cant modify files), its not the same story for data into /home. So why encryption, proxy, tunneling, and many progs around in the linux world ? Your post talk about your experience :mad:

---

### Post by Bikekid450 on 2010-09-23
Thanks guys and ADN. I have gave up on my Ubuntu system now though as it kept failing and corrupting, 4 times I installed it with 3 different CD's and 2 downloads, 2 different partitions and a new Hard Drive. However Win7 and XP work fine in the same pc and same partitions as I tried to install Ubuntu. 

Don't know what to do =/

---

### Post by MortenA on 2010-09-23
> **OpSecShellshock said:**
> Firefox already makes use of Google's safe browsing feature, so in the event that a site has been identified as dangerous,  by default you won't be able to get to it without having to pass through a warning page. Again, that only helps in the event of known issues, but the chances of anything outside of your home directory's .mozilla folder being affected are slim on this OS even if a page turns out to have bad stuff on it.

It does not stop everything, but that is not an argument for not using it :)
... it has warned me several times, and gives a good report of why the warning appears.

---

### Post by bodhi.zazen on 2010-09-23
I believe you need to secure firefox (or whatever browser you use).

See :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

On Ubuntu I use NoScript + Privoxy + Apparmor profiles for both Firefox and Privoxy.

The main thing I restrict with apparmor is files in $HOME. There is no reason firefox need access to things in .ssh or much of anything in $HOME outside of .mozilla and Downolads or Desktop.

---

### Post by adn258 on 2010-09-23
> **dino99 said:**
> you seem to simply dont understand what "security" mean ADN...

if / is protected by design (cant modify files), its not the same story for data into /home. So why encryption, proxy, tunneling, and many progs around in the linux world ? Your post talk about your experience :mad:

Yes of course there are there are other threats as I stated such as with the browser but I don't really conclude these as the fault of ubuntu.  There would be weaknesses in firefox or other software that may be taken over to read your /home.

Or other security issues on a network etc. etc.  This is still a lot different then just browsing some sites and all of a sudden you have fake AV's popping up everything DOWNLOAD ME DOWNLOAD ME.


My experience well I love linux but I hate to say I know more about windows for the fact that one of the things that I do is fix computers for  $$$ they are windows computers.




At least for the time being the most frequent problems I fix are malware related and the #1 malware problem I see these days are fake av's which install themselves and then you see threatening messages constantly you have a virus please upgrade now etc. etc.  You can't get rid of these with standard anti virus as they are designed to re-write themselves once deleted and windows lets it happen (even windows 7).



They are a huge pain in the %$#@^&* @## !!!  These are the types of things I never see happen on linux machines or mac's for that matter.  Everytime I get done fixing one I think god it's nice having a mac and ubuntu on my other machine.

These type of things while people claim they are possible just NEVER seem to happen for linux and my Mac OSX.


As a hobby I will use some handy windows malware analysis programs on my virtual such as 

1.Regshot
2.capturebat.
3.wireshark.
4.processmonitor 

and others and get a behavioral analysis of the malware that I run into.  Some good decompilers would also be sound but code analysis is harder and takes more time.  That's really all I can say :).

---


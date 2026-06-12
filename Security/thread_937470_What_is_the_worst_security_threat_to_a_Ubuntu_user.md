---
title: "What is the worst security threat to a Ubuntu user?"
date: 2008-10-03
forum: Security
---

### Post by askyourpc.com on 2008-10-03
What is the worst security threat to a Ubuntu user? If viruses are not so much of a problem what about cookies and stuff. Are there things done to improve security in other aspects? Should I setup a firewall?

---

### Post by RFXCasey on 2008-10-03
To be quite honest with you I have been researching security on Ubuntu lately as I am a fairly new user (less than a year). After extensive reading I have come to the conclusion that the number one threat to Ubuntu security is the user themselves. Basically people not knowing what they are doing or doing something stupid is probably the biggest security hole out there. That being said run a firewall for sure, Ubuntu comes with one by default called iptables you can fine info here [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo). There is a graphic front end that you can use to make configuring easier called firestarter you can find info on that here [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter). I have also hear good things about UFW (Uncomplicated Fire Wall) just do a google for it. Some will say you don't need to run an antivirus for ubuntu. Apparently there are no active viruses for Ubuntu (out in the wild) so to speak however from what I've read not running a virus scanner is just plain stupid. Even though Linux is writen in a way that makes it very hard for viruses to mess with the more people that start using it the bigger a target it becomes. And nothing can guard against uneducated users that install things themselve because someone told them it would help their system. For instance if you ever see anyone tell you to type "rm -rf" or something like that in console "Don't do it!" It will wipe out your root directory or something like that. It's not good I can tell you that. Some that come to mind are ClamAV and Avast. Avast has it&#8217;s own GUI and ClamAV you have to install the GUI. Really you just need to search the forums as this subject has an unlimited amount of information pertaining to it. Hope this gets you started. Feel free to use the Thanks Button.

---

### Post by RFXCasey on 2008-10-03
Double post

---

### Post by jerome1232 on 2008-10-04
That was my first thought as well, 'the user'

Ubuntu comes with iptables. ufw is a frontend to configure it, also installed by defualt. By default no services listen for connections on Ubuntu so a firewall won't do anything that's not already being done.

Your browser is probably the biggest window code has to your computer, via flash and javascript. Alot of people including myself recomend using firefox addons like noscript, addblockplus, and flashblock. These prevent flash/java/javacript from automatically running when you visit a site.

---

### Post by Vivaldi Gloria on 2008-10-04
> **jerome1232 said:**
> That was my first thought as well, 'the user'

Ubuntu comes with iptables. ufw is a frontend to configure it, also installed by defualt. By default no services listen for connections on Ubuntu so a firewall won't do anything that's not already being done.

Your browser is probably the biggest window code has to your computer, via flash and javascript. Alot of people including myself recomend using firefox addons like noscript, addblockplus, and flashblock. These prevent flash/java/javacript from automatically running when you visit a site.


+1

Exactly my thoughts on all three points. Learn more. No change in the firewall settings needed if you are using a default ubuntu desktop system. Yes, use noscript.

---

### Post by davidryder on 2008-10-04
As long as you only install items from trusted sources and never click "Yes" to any dialog that you don't fully understand you will stay safe. 

And I agree with the above, most vulnerabilites are aimed towards a silly user.

---

### Post by cariboo on 2008-10-04
There is really no need to install a virus scanner, as there are no virus scanners that scan for Linux viruses, the only reason you would use a scanner is if you are running a mail servers that include windows users on your network. Otherwise forget it. If you accidentally pass a virus on to windows users, it's their problem if they don't have there computers properly protected, they will have a lot more problems then the virus you just sent them.

Jim

---

### Post by PocketDog on 2008-10-04
The biggest risk while using a computer is the nut on the swivel chair.

---

### Post by Dr Small on 2008-10-04
The biggest potential threat to your security, is yourself.

---

### Post by PocketDog on 2008-10-04
Hence the nut.

---

### Post by Patb on 2008-10-04
The User +1.

Yesterday, my workmate muttered: "Ach! This confounded computer! That's the third time today it has suddenly asked for my password!"

It was only when I said: "You're not going to put it in, are you! How do you know that's not a phishing scam?" that he stopped typing... and thought.

Cheers, Pat

---

### Post by Mulenmar on 2008-10-04
Doesn't matter whether you're talking about just in Ubuntu or in real life: on statistical average, the user is always the user's own worse enemy.

---

### Post by nubdora on 2008-10-05
"A machine is only as intelligent as the user" - *Unknown Sumerian, concerning the abacus ~ 2700 BC. *

---

### Post by kevdog on 2008-10-05
I'll take a different approach -- I think its the internet and its misinformation.  Leads people to do stupid things.  That and trying to download xxx and pirated mp3's -- trying to get something for nothing usually gets a lot of people in trouble.

---

### Post by cariboo on 2008-10-05
Nope it's still the user, it is the user that is responsible for for what they see and try to download. The internet doesn't do anything for you, you have to click on links to do anything.

Jim

---

### Post by AgainstTheDarkArts on 2008-10-06
> people not knowing what they are doing or doing something stupid is probably the biggest security hole out there. 

Again, the problem is that I'm stupid?  Why does it always come down to that?!!?  :lolflag:

---

### Post by hyper_ch on 2008-10-06
> **AgainstTheDarkArts said:**
> Why does it always come down to that?!!?  :lolflag:
You really want an answer? :biggrin:

---

### Post by WaNaBePi on 2008-11-14
what about the virus files them self? while they are malignant for the most part in unubtu, etc... systems, they still take up space on your hard drive. however trivial there size, i still don't want them there. so is there a list that i can use to search my hd to simply do a file search and find them that way?

you see what i'm getting at right, yea i'm that anal about my hard drive.

---

### Post by cariboo on 2008-11-14
How do they get saved to the hard drive? There has to be some user intervention.

I don't know why people have a hard time understanding that a computer can't do anything on it's own, you have to tell it what to do. As easy as it is to blame someone or something else, in the end it is alwaus the user that is the biggest threat to a computer no matter what OS you are using.

To answer the pp's question, there is no list you can consult, but normally windows viruses are in email, or files downloaded form not so secure web sites. Check you email storage and where ever it is that you store your downloaded files.

Jim

---

### Post by WaNaBePi on 2008-11-14
no i understand that i am ultimately the cause of any virus on my system. i'm asking if i have a virus on my hard drive, hypotheticaly

#1 how would i know if i have a virus on my system/hard drive? (since they don't "cause" any changes in a linix ubuntu etc. environment)

#2 if they are malignant(don't cause any damage or make any changes, by something i do (since i'm the one initiating the program on some level) to my system, i still don't want them taking up space, however small the files are.

#3 so, how do i find and remove them? (if im not using some kind of anti virus software that everyone seems to assert is a non-necessity) my sences tell me i cant, i must use a scanner of some kind, which in my case makes an antivirus a nesessity? 

i hope i have brought clarity to my original question

thank you

---

### Post by lisati on 2008-11-14
> **askyourpc.com said:**
> What is the worst security threat to a Ubuntu user? If viruses are not so much of a problem what about cookies and stuff. Are there things done to improve security in other aspects? Should I setup a firewall?

I havne't read the whole threat yet.
In my opionion, the biggest security threat to any OS is the people who use it.

Way back in the 1980s when I worked as a programmer, the company I worked for was nervous about who got access to what, because they processed a lot of confidential financial informaiton. In common with other users of the OS they used, they'd set things up so that interavtive users of their mainframes would automatically get booted off the system after a set period of inactivity. One part of my job was writing programs that reported on certain kinds of activity that had been recorded in the system logs: it was surprising how often this automatic boot-off process got invoked - and often for people who should have known better.

---

### Post by Skilleto on 2008-11-14
> **WaNaBePi said:**
> 
#3 so, how do i find and remove them? (if im not using some kind of anti virus software that everyone seems to assert is a non-necessity) my sences tell me i cant, i must use a scanner of some kind, which in my case makes an antivirus a nesessity? 

thank you

Surely, all an anti virus program does on a basic level is stop processes running and then remove the virus files. 

Therefore, with a decent technical knowledge you can stop the process and remove infected files.

Regarding the topic question, I would say the user is only a part of the issue. E.g If you get a popup saying do you want to run computer ruiner.exe and you click yes, **you** are only **replying** to the question. 

The program most likely to ask these kinds of questions are **probably** your web browser.

---

### Post by lisati on 2008-11-14
> **kevdog said:**
> I'll take a different approach -- I think its the internet and its misinformation.  Leads people to do stupid things.  That and trying to download xxx and pirated mp3's -- trying to get something for nothing usually gets a lot of people in trouble.

It's not just the potential legal hassles: I've encountered malware masquearding as MP3 files.

---

### Post by 73ckn797 on 2008-11-14
If I could kick, in the seat of the pants, the one person who has caused me more troubles, I wouldn't be able to sit down for a week!

---

### Post by aysiu on 2008-11-14
> **WaNaBePi said:**
> no i understand that i am ultimately the cause of any virus on my system. i'm asking if i have a virus on my hard drive, hypotheticaly

#1 how would i know if i have a virus on my system/hard drive? (since they don't "cause" any changes in a linix ubuntu etc. environment) I don't think you do understand if you're still asking these questions.

If a virus is on your hard drive, it had to have a way to get there. It doesn't just magically appear.

There are only a handful of ways a virus could end up on your hard drive: [list][*]**Social Engineering**. Some website, email, or other program tricked you into installing it or downloading it. [*]**Unpatched flaw in a program**. Some program you're running allows access to your drive or arbitrary code executation.[*]**Brute-force infiltration**. You're running some service that allows people to remotely log into your computer, and someone has cracked your password.[/list] So the question you should be asking isn't > What do I do if a virus happens to appear on my hard drive? but > How would a virus appear on my hard drive, and how do I prevent that? So the answers are: [list][*]Educate yourself on social engineering and how to avoid it[*]Make sure you install security updates regularly[*]Don't turn on additional networking services unless you know how to secure them properly, and make sure you use strong passwords.[/list]

---

### Post by WaNaBePi on 2008-11-14
OK, so i think that aysiu answered my question best. for clarification, say i go to a torrent site, the most malicious one out there (hypothetical) downlaod a torrent, for the say, next ubuntu version.(perhaps this is a bad example, because there is probably a lot of security involved, but hypothetically) 

to get a virus as I'm understanding aysiu.(ive successfully downloaded the ubuntu file and in the process of installing or updating) some dialog window would come up at some point in time (or some other indicator, say a process notification warning...I'm coming from a windows background so bare with me) asking me if i wanted to do some thing (most likely, right?). let's say that is in fact a malicious program trying to gain access to my computer. if i click "OK" or "cancel"(for example in a dialog box that comes up while installing) will be the determining factor in this case, whether or not i get the virus? 

this would be a case of: social engineering, yes?

due to a "tainted" file in the mix or the whole thing is a virus just with the file named in this case, ubuntu.iso, or whatever sorry about my non standard vocabulary/terminology. 

so say i click "OK" by ACCIDENT, knowing that that would install a virus so i now HAVE a virus on my hard drive.

i don't know what type of virus it is, or where it went. how would i find out this information? IF ubuntu is not affected by the virus, giving me no indication of a problem, BUT i know i have a virus (hypothetical). SO if want it off of my system for the sake of having a "PERFECTLY" clean hard drive. 

how would i find it? 

i understand its not magic (getting a virus) i Never thought is was. I'm just trying to understand how this awesome beast(ubuntu) works

i hope i'm making sense, sorry for being dense. 

thanks!

---

### Post by aysiu on 2008-11-14
Well, if you're downloading something fishy, you could be compromised even before the OK and Cancel. If you don't trust the source you're downloading from, the "ubuntu.iso" file itself might be malware.

But if the OK or Cancel button isn't OK or Cancel really but is a hidden script that executes, then you can have no idea what it might have installed on your computer or deleted from your computer. That script you were tricked into executing could have done anything your user account has permission to do.

Once you've been the victim of social engineering, you're done for.

---

### Post by WaNaBePi on 2008-11-14
ok 

what are the ways i could find a virus on my computer?

what are the ways to remove said virus?

ALOMST THERE........

---

### Post by aysiu on 2008-11-14
> **WaNaBePi said:**
> ok 

what are the ways i could find a virus on my computer?

what are the ways to remove said virus?

ALOMST THERE........
Well, as I said before, you can find a virus on your computer if you allowed your computer to be compromised. That's the bottom line.

You either let it in (by being the victim of social engineering), it exploited some software flaw you didn't patch, or someone cracked your user account and put it there.

Again, you *say* you understand that files don't magically appear on your computer. I don't think you do, though.

Your computer is either compromised or it's not. If it's not compromised, there's no way for an unwanted file to just appear. If it is compromised, you could have unwanted files all over the place.

And no virus scanner (for Windows or otherwise) perpetually has updated definitions on every single virus in existence. It's always an arms race. Even if you're updated to today, you might miss the new virus that came into being tonight or tomorrow.

So the answer is: if your computer isn't compromised, there's no virus on your computer. If it is compromised, there's no way to be 100% certain you've found and/or removed all malware unless you reinstall.

---

### Post by WaNaBePi on 2008-11-14
OK, thank you so much, ill give you a second thanks medal aysiu (is that Japanese, or some abrivation...you don't have to answer that) to add to your hundreds of thanks...perhaps only time and wisdom will answer my question fully. i think you are right, I'm just not ready to hear the answer, sorry for being a pain.

THANK YOU!

---

### Post by Kinstonian on 2008-11-14
> **WaNaBePi said:**
> ok 

what are the ways i could find a virus on my computer?

what are the ways to remove said virus?

ALOMST THERE........

The easiest way to detect viruses is with anti-virus software.  However, you should take a step back and be asking how do I detect if I've been hacked, and not focus on one type of incident such as getting a virus.  Nearly every intrusion involve placing malware on the system.  Fortunately you can detect that in many ways, but the signs of an incident depend on the type of incident.

Some brief but good guides as to what to look for are:

1. [CERT's Intruder Detection Checklist](http://www.cert.org/tech_tips/intruder_detection_checklist.html)

2.  [Detecting and Removing Malicious Code](http://www.securityfocus.com/infocus/1610)

However, all of the books, articles, white papers, etc that I have read that deal with intrusion detection can be summarized as detecting anomalies.  To spot what is abnormal, you have to have a good understanding of what is normal.  Both what is normal for your computer (processes, logs, user accounts, files, network connections, etc) and what is normal for attacks (how attackers gain access, and what they do once they gain access).

Understanding what is normal enables you to detect not just viruses, but all incidents.

---

### Post by mssever on 2008-11-15
It bears repeating that the antivirus software for Linux scans for and detects **Windows** viruses, which can't infect Linux. If you got done in by some malware that attacks your Linux system, antivirus software won't help you.

---

### Post by Kinstonian on 2008-11-15
> **mssever said:**
> It bears repeating that the antivirus software for Linux scans for and detects **Windows** viruses, which can't infect Linux. If you got done in by some malware that attacks your Linux system, antivirus software won't help you.

That's actually not true.  They may detect more Windows viruses, but they also detect Linux malware.  For example, ClamAV detects Linux viruses, bots, rootkits, and other malware.

---

### Post by merlia1 on 2008-11-15
That is really cool about the virus. Thanks for the infoshare.

---

### Post by bodhi.zazen on 2008-11-15
I would also like to point out that servers are a big risk.

By default there are no servers listening, but if you install a server, ssh, FTP, apache, samba, NFS, PHP, MySQL, etc you really need to take the time to read at least the basic background information and learn how to secure the server.

The ssh port, for example, gets hammered (check you logs). FTP can also be quite problematic.

Apache itself is reasonalby secure, but take care with your php code and also with he apache modules (if you use them).

Well, you get the idea.

With that said, a default installation of Ubuntu is, IMO, much more secure then a default Windows install. Just do not inactivate security features (like setting a root password, etc) and do not run code or install applications from untrusted sources.

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

This is why everyone is telling you the user is the biggest threat, the OS by default is relativly secure, just do not get lazy and inactivate security or install servers without learning what you are doing.

---

### Post by WaNaBePi on 2008-11-26
Ah! i see i was talking about malignant WINDOWS viruses that may end up on my ubuntu hd. malignant because they do not affect ubuntu but they would, the data of the virus, would still be on my hd

i want to be able to find/delete, that malignant windows virus, if there ever was one on my system. however, i understand that i probably would still need some kind of ant virus software on my comp do do this easily.

!!!!random!!!!!

WHY is there soooo little support, or specifically no support or functionality for .wav files in rythmbox im trying to get a cd that i bought on to my ipod and its just not cooperating.... that is the end of that tangent.


just trying to spare my self from looking like a complete ubuntu moron

im beginning to think more and more that i might "need" windows on my comp becuse there is just so many holes/bugs in the free/share environment that it makes ubuntu non functional to the more routine  tasks of say all the flxability that floola.exe gave me for my ipod in a windows envionment (dosent work well in wine) and playing games like civilization 4...

ok enough w/the tangents sorry don't ban me...im gonna go sleep now.

thanks....

---

### Post by Nosophorus on 2008-11-26
Even though I Use Ubuntu (7.10 Gutsy Gibbon), the AV (ClamAV) I often run in my machine once found what it classified as malware, see below the scan log:

//home/marcelo/.opera/cache4/opr0EPHM: JS.Agent-29 FOUND

The malware was in one of the Opera Browser subdirectories (cache4).

ClamAV says the file opr0EPHM is a JS.Agent (likely a JavaScript). I have already removed it from my machine.

For more details about that malware:

[http://www.viruslist.com/en/viruses/encyclopedia?virusid=109333](http://www.viruslist.com/en/viruses/encyclopedia?virusid=109333)

If someone wanna see the malware source code, you can download it from the link below
:
[http://www.quickfilepost.com/download.do?get=7d97a210b2b00bf0cfde013a190ce7cb](http://www.quickfilepost.com/download.do?get=7d97a210b2b00bf0cfde013a190ce7cb)

**WARNING:**

I put it as .txt file, BUT, despite that, ClamAV detected it as a malware

A friend of mine said that so-called malware is nothing more than a script to track website traffic.

I hope this post may help someone.

---

### Post by stmurray on 2008-11-26
> **bodhi.zazen said:**
> I would also like to point out that servers are a big risk.

By default there are no servers listening, 


I always seem to repeat this, but on all my Ubuntu installations there are no TCP servers listening.  However both Avahi and dhclient3 have open UDP ports.  If a vulnerability was discovered in either of those, then (non-firewalled) Ubuntu machines would be vulnerable to any exploits that use that vulnerability, until that vulnerability is patched.  I believe that risk is quite low, but I still use a firewall (for other reasons as well).  I just want to make sure people have the information, so they can make their own decision whether or not to install a firewall.  

Also, to add my two cents worth to this discussion, I believe the biggest security risk to Ubuntu installations (and to Windows for that matter) is the browser. (Malware is making the move from email spreading to spreading via hacked websites). That's why I run NoScript.  I believe a workstation running Ubuntu, with a firewall and NoScript has the lowest risk of security issues than any other main-stream Operating System.

---

### Post by Nyas on 2009-02-02
[COLOR="DarkGreen"]**EDIT: I created a [[COLOR="DarkRed"]new thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6667373#post6667373") about this**[/COLOR]

I am sorry if my post will be slightly off-topic. Could not find any thread about this in the forum.

While browsing some simple guides about security I saw almost never-ending lists of software that should make the computer a safer place. 
Even reading their wiki pages, etc. I still can not always understand which does what and more less if I really need them.

If I am the only user of my laptop, have Ubuntu Desktop and not planning to set up a server, which of these are really useful?

For example:
# grsecurity (Kernel protection)
# Rootkit Hunter (Rootkit protection)
# Nagios (Network monitoring)
# Snort (Intrusion detection)
# OpenSSH (Secure remote access client)

Changing the default not-so-secure settings and using NoSctipt with Firefox are relatively simple tasks but installing and configuring these might be more of a challenge to me. 
Also, every additional program uses resources and theoretically might create more problems than solve. So just wanted to make sure before installing any of these..

Any links about security software for beginners would also be appreciated.

Thanks.

---

### Post by cariboo on 2009-02-02
Instead of bringing this necrothreads back to life, why not start a new one, your bound to get more answers, then posting at the end of a thread that has nothing to do with the questions you are asking.

Jim

---

### Post by listerdl on 2009-02-03
> **davidryder said:**
> As long as you only install items from trusted sources and never click "Yes" to any dialog that you don't fully understand you will stay safe. 

By dialog - do you mean terminal dialog?

---

### Post by aysiu on 2009-02-03
> **listerdl said:**
> By dialog - do you mean terminal dialog?
No. It could be any dialog. Terminal or otherwise.

Here's an example of a GUI (non-terminal) dialog.

---

### Post by paddydd on 2009-02-07
Hi,
  I'm just curious...and maybe this feature is in UBUNTU...
  But if you didn't know your computer was invaded or you had suspicions... Would not a comparison of the list of files that are supposed to be in the OS combined with a CRC/MD5 validation for each file give you some sort of idea where an issue might be. I realize that conf files change but it seems to be that to know if something is not supposed to be there, don't you have to essentially have to have something like a Known Good List of software?

  Any comments and replies are appreciated.

thanks
Paddy

---

### Post by bodhi.zazen on 2009-02-09
> **paddydd said:**
> Hi,
  I'm just curious...and maybe this feature is in UBUNTU...
  But if you didn't know your computer was invaded or you had suspicions... Would not a comparison of the list of files that are supposed to be in the OS combined with a CRC/MD5 validation for each file give you some sort of idea where an issue might be. I realize that conf files change but it seems to be that to know if something is not supposed to be there, don't you have to essentially have to have something like a Known Good List of software?

  Any comments and replies are appreciated.

thanks
Paddy

You have several options and what you ar asking about is called "HIDS"

[http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system](http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system)

There are several options for Linux including Tripwire :

[http://www.linuxjournal.com/article/8758](http://www.linuxjournal.com/article/8758)

[http://sourceforge.net/projects/tripwire/](http://sourceforge.net/projects/tripwire/)

and OSSEC

[http://www.ossec.net/](http://www.ossec.net/)

There are many other options and a google search should give you other choices.

---

### Post by zerofool2005 on 2009-02-09
The biggest security risk is running applications in root.

---

### Post by hyper_ch on 2009-02-09
> **zerofool2005 said:**
> The biggest security risk is running applications in root.
Why? Certain stuff must be run in root... but it is the USER that finally decides what is run where ;)

---

### Post by paddydd on 2009-02-12
bodhi.zazen,

  Thanks for your reply. I will look over the materials soon.

Paddy

---


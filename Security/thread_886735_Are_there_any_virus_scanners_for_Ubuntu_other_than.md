---
title: "Are there any virus scanners for Ubuntu other than email ones?"
date: 2008-08-11
forum: Security
---

### Post by thrasher6900 on 2008-08-11
I find a lot of scanners in synaptic, but they are all geared toward email.

Is there anything out there that actually scans my hd for viruses?

What's the best one?

Links and install instruction please.

Thanks

---

### Post by hyper_ch on 2008-08-11
there are some... but they don't look for linux viruses... are you sure you need an av?

---

### Post by PCessna on 2008-08-11
> **thrasher6900 said:**
> I find a lot of scanners in synaptic, but they are all geared toward email.

Is there anything out there that actually scans my hd for viruses?

What's the best one?

Links and install instruction please.

Thanks

It is kind of stupid for a virus scanner when there is virtually no virus' for Linux, only do this if you feel suspicious, or you also have window xp or vista, etc. installed, otherwise, I just find it unneeded.

---

### Post by OutOfReach on 2008-08-11
It is not really necessary to have a Virus Scanner, since there are no viruses for Linux. And like hyper_ch said most of the virus scanners available for Linux scan for Windows viruses, which cannot infect you...

---

### Post by sandysandy on 2008-08-11
[http://free.avg.com/ww.4040](http://free.avg.com/ww.4040)

[http://www.clamav.net/](http://www.clamav.net/)

regards

---

### Post by HermanAB on 2008-08-11
Well, if you really feel a burning desire to waste money, McAffee makes a Linux based virus scanner.  Otherwise, everybody uses ClamAV to scan for Windows viruses on file and email servers.

If you need to scan for Linux viruses, then the following script will do the trick:
#! /bin/bash
echo "Linux virus scanner"
echo "Copyright reserved FSF, 2008, GPL"
sleep 10
echo "Scanning..."
sleep 300
echo "Thinking..."
sleep 30
echo "Scanning some more..."
sleep 120
echo "No viruses found!"
exit 0

The above scanner is very efficient and doesn't require significant computing resources...

Cheers,

Herman

---

### Post by mardawi on 2008-08-11
> **hermanab said:**
> 
if you need to scan for linux viruses, then the following script will do the trick:
#! /bin/bash
echo "linux virus scanner"
echo "copyright reserved fsf, 2008, gpl"
sleep 10
echo "scanning..."
sleep 300
echo "thinking..."
sleep 30
echo "scanning some more..."
sleep 120
echo "no viruses found!"
exit 
lmao!!!!!

---

### Post by hyper_ch on 2008-08-11
but it runs for almost 8 minutes ;)

---

### Post by thrasher6900 on 2008-08-11
> **PCessna said:**
> It is kind of stupid for a virus scanner when there is virtually no virus' for Linux, only do this if you feel suspicious, or you also have window xp or vista, etc. installed, otherwise, I just find it unneeded.
I know about the rarity of viruses on linux.

However, I do suspect something or I wouldn't have asked.

I have run into some crazy person who is kinda psycho who knows how to make such and somethings have been acting fishy.

---

### Post by thrasher6900 on 2008-08-11
> **mardawi said:**
> lmao!!!!!

> **HermanAB said:**
> Well, if you really feel a burning desire to waste money, McAffee makes a Linux based virus scanner.  Otherwise, everybody uses ClamAV to scan for Windows viruses on file and email servers.

If you need to scan for Linux viruses, then the following script will do the trick:
#! /bin/bash
echo "Linux virus scanner"
echo "Copyright reserved FSF, 2008, GPL"
sleep 10
echo "Scanning..."
sleep 300
echo "Thinking..."
sleep 30
echo "Scanning some more..."
sleep 120
echo "No viruses found!"
exit 0

The above scanner is very efficient and doesn't require significant computing resources...

Cheers,

Herman



Why do you find it funny to pic on someone who is new and is trying to learn?

You all act as if you were never new at this.

---

### Post by lisati on 2008-08-11
> **sandysandy said:**
> [http://free.avg.com/ww.4040](http://free.avg.com/ww.4040)

[http://www.clamav.net/](http://www.clamav.net/)

regards

also [http://free.grisoft.com](http://free.grisoft.com)
If you choose the linux version, don't forget to add your user name to the avg group (it's in the documentation)

---

### Post by EnGorDiaz on 2008-08-11
> **mardawi said:**
> lmao!!!!!

i agree lmmfao

---

### Post by thrasher6900 on 2008-08-11
> **lisati said:**
> also [http://free.grisoft.com](http://free.grisoft.com)
If you choose the linux version, don't forget to add your user name to the avg group (it's in the documentation)

> **sandysandy said:**
> [http://free.avg.com/ww.4040](http://free.avg.com/ww.4040)

[http://www.clamav.net/](http://www.clamav.net/)

regardsThank you for helping me and being respectful.

---

### Post by thrasher6900 on 2008-08-11
> **mardawi said:**
> lmao!!!!!

> **HermanAB said:**
> Well, if you really feel a burning desire to waste money, McAffee makes a Linux based virus scanner.  Otherwise, everybody uses ClamAV to scan for Windows viruses on file and email servers.

If you need to scan for Linux viruses, then the following script will do the trick:
#! /bin/bash
echo "Linux virus scanner"
echo "Copyright reserved FSF, 2008, GPL"
sleep 10
echo "Scanning..."
sleep 300
echo "Thinking..."
sleep 30
echo "Scanning some more..."
sleep 120
echo "No viruses found!"
exit 0

The above scanner is very efficient and doesn't require significant computing resources...

Cheers,

Herman

> **EnGorDiaz said:**
> i agree lmmfaoAnd once again another rude, immature comment with no intelligence what so ever.

Any more jerks wanna **** on my thread?

---

### Post by jpeddicord on 2008-08-11
> **thrasher6900 said:**
> And once again another rude, immature comment with no intelligence what so ever.

Any more jerks wanna **** on my thread?

Your responses aren't helping. Let's get this thread back on topic please.

---

### Post by jerome1232 on 2008-08-11
I thought it was good natured humor but at any rate as has been mentioned virus scanners for linux scan for windows viruses, so they are really there for servers which share files with windows computers.

My desktop is setup as a samba server and does exchange files with windows computers so I do scan one folder that I have set apart for files I have downloaded off of untrusted websites before I slap them into a shared folder. Viruses are not a real threat to the linux box itself though.
Just a little reading about linux and viruses
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

Just don't go running random scripts you find on joe-bobs website as super user without knowing what said script does and you'll be fine. :)

---

### Post by ELMIT on 2008-08-12
I am now also in the need for such thing, ...

I used my external USB hard disk to connect to a Windows computer, and afterwards I found that this computer had a virus. 

I used at Ubuntu Hardy:
  sudo apt-get install clamav

How do I use it? How can I scan the USB hard disk?
How will the database be updated?

Thanks for your answer.

bye

R.

---

### Post by Flag on 2008-08-12
Agreed there is not yet a virus for linux found, but you can pass them on.

rgds

---

### Post by hyper_ch on 2008-08-12
so it should not your responisibility to protect non-secure computers but those who run them.

---

### Post by lisati on 2008-08-12
> **ELMIT said:**
> I am now also in the need for such thing, ...

I used my external USB hard disk to connect to a Windows computer, and afterwards I found that this computer had a virus. 

I used at Ubuntu Hardy:
  sudo apt-get install clamav

How do I use it? How can I scan the USB hard disk?
How will the database be updated?

Thanks for your answer.

bye

R.

A similar thing happened with my nephew's mp3 player (since lost) - I connected it to a Windows machine to put some music on it for him, and AVG had a field day straight away: almost all the files then on it had some kind of infection. I quickly put the word out to his parents and other rellies who might have helped him to check their machines.

---

### Post by ELMIT on 2008-08-12
While my system may not be affected from the virus, but the data I pass on to other people my spread a virus from one computer to the next. 

I would therefore like to make sure that I am not a source of viruses. Although they have already the biggest virus and are not willing to remove it: WINDOWS!!!!

---

### Post by lisati on 2008-08-12
> **Flag said:**
> Agreed there is not yet a virus for linux found, but you can pass them on.

rgds

Reminds me of a situation a year or two back when I received a nasty little attachment by email. I contacted the owner of the email address (which, as can be expected, was forged) whose attitude was, "It's not my problem, I use Linux". I find that a little surprising, since his email address was being fraudulently used.

---

### Post by hyper_ch on 2008-08-12
> **ELMIT said:**
> I would therefore like to make sure that I am not a source of viruses. Although they have already the biggest virus and are not willing to remove it: WINDOWS!!!!
Windows is NOT a virus.
Virus is malware that is written to be small, efficient and it works...
Windows is the opposite of that ;)

---

### Post by jerome1232 on 2008-08-12
> **ELMIT said:**
> I am now also in the need for such thing, ...

I used my external USB hard disk to connect to a Windows computer, and afterwards I found that this computer had a virus. 

I used at Ubuntu Hardy:
  sudo apt-get install clamav

How do I use it? How can I scan the USB hard disk?
How will the database be updated?

Thanks for your answer.

bye

R.

take a  look at the man page to learn how to use it
```
man clamscan
```

there's also a gui for it but I don't remember the package name off hand.

I agree with hyper except that in my case it's my own computers on the lan, so I like to scan them before they touch the windows computers (it's a simple script I just made that executes everyday  and then puts infect files in one spot and non-infected into another so no thought involved on my part)

---

### Post by ELMIT on 2008-08-12
> I upgraded to the latest stable version but I still get the message Your ClamAV installation is OUTDATED, why?

    * Make sure there is really only one version of ClamAV installed on your system:

         $ whereis freshclam 
         $ whereis clamscan



That is not clear for me, should only FRESHCLAM or CLAMSCAN exist or does it mean each of them only once?

bye

R.

---

### Post by ELMIT on 2008-08-12
Jerome:

> man clamscan

Just tell me how did you come to the idea to add a "scan" to "clam"

You do have some insider knowledge, .... ;-)

---

### Post by jerome1232 on 2008-08-12
Well first time I ran man clamav, that didn't bring anything up, so I typed man clam and hit tab twice, that listed clamscan, which turns out to be what you use to scan. Tab completion is the only way I find my way around :)

freshclam is the updater it has it's own manpage

clam will always tell you about the engine being out of date, that's because the version in the repos IS a little out of date, if you REALLY want to go through the hassle I'm sure you can google clamav and get the freshest version of their site.

This is how I run it (I any files I don't trust I stick in ~/Downloads/unscanned)

what it does is clamscan scans recursivly (-r) moves infected files to ~/Downloads/infected, then once the command completes move all the leftover files (scanned and shown to be clean) into a different directory ~/Downloads/clean
```
clamscan -r ~/Downloads/unscanned --move=~/Downloads/infected && mv ~/Downloads/unscanned/* ~/Downloads/clean
```

---

### Post by ksbalaji on 2008-08-14
> **thrasher6900 said:**
> I find a lot of scanners in synaptic, but they are all geared toward email.

Is there anything out there that actually scans my hd for viruses?

What's the best one?

Links and install instruction please.

Thanks

Probably you are right in insisting for an anti virus.  I also doubt that something fishy is going on in my hardy box which I have been using for many months now (earlier -gutsy). I find the application launchers which I had earlier locked in a specified place in my panel displaced mysteriously. I find that my Xchat does not open at all now-a-days. What could be the reason? I cannot discount  virus since I use sudo code often when I am still online.  Using sudo is not a sin and sometimes would let others peep into your system. Hence the need for anti virus. Tell me more.
balaji

---

### Post by jerome1232 on 2008-08-14
The panels moving around I find is caused by certain full screen apps that bring you into a low resolution, I had this problem and it stopped when I stopped using wine with full screen games. But this is really all material for a different thread and none of it virus related. Running as root while online isn't going to bork your system, running random programs as root might, but that's not a virus.

---

### Post by Vishal Agarwal on 2008-08-14
I never heard about any virus for Linux, it is a totally secured system. It dose not have security issues like M$. U need not to install any anti virus for Linux, but if u have a dual boot with windows then u will need a virus scanner for windows.

---

### Post by Camilia on 2008-09-01
> **sandysandy said:**
> [http://free.avg.com/ww.4040](http://free.avg.com/ww.4040)

[http://www.clamav.net/](http://www.clamav.net/)

regards
 
I dowloaded clamav , clicked open with archives, and don't see any changes. What do I do next?

---

### Post by rogeriopvl on 2008-09-02
What do you suspect? I really doubt that it's a virus. But it could be a rootkit, in that case use rkhunter to scan your system.

```
sudo apt-get install rkhunter
```

---

### Post by rogeriopvl on 2008-09-02
> **Camilia said:**
> I dowloaded clamav , clicked open with archives, and don't see any changes. What do I do next?

Did you downloaded from the website? It's available in the Ubuntu repositories. just apt-get install clamav.

---

### Post by matchstich on 2008-09-03
> **rogeriopvl said:**
> What do you suspect? I really doubt that it's a virus. But it could be a rootkit, in that case use rkhunter to scan your system.

```
sudo apt-get install rkhunter
```


and get chkrootkit

run them both

---

### Post by thesurgeon on 2008-09-03
I wouldn't listen to any of those guys, they are clearly fat guys and skinny nerds with glasses who hover round the coke machine on there lunch brake. Doesn't matter what OS you use always have an antivirus and a firewall. Those guys clearly think they know more than they really do.

---

### Post by jerome1232 on 2008-09-03
Out of curiosity why do I need an anti-virus that scans my computer for viruses that can cripple an OS I'm not using? (Linux anti-virus programs scan for Windows viruses)

And what's the firewall for, what is it protecting me from?

I'm already behind a router, so connections don't make it to my computer in the first place, there are no programs listening for connections from the internet on my computer (a vanilla Ubuntu install), so there is nothing to even attempt to connect to.

So how do these program make my computer more secure?

Did you know that in some cases the anti-virus program is the attack vector... the program that gets exploited by a virus and uses it to spread through your system.

Okay I'm off to go hover over the coke machine again.

---

### Post by fballem on 2008-09-03
> **hyper_ch said:**
> so it should not your responisibility to protect non-secure computers but those who run them.

Not sure that I would agree with that sentiment. If someone gives me a file that has a virus, even if I don't know about it, and I pass it on because I'm too lazy to check it - or it isn't my responsibility - then that says a lot of things about me - none of which are flattering.

Just because I am using Linux doesn't give me the right to be smug or irresponsible.

---

### Post by Oldsoldier2003 on 2008-09-03
> **thesurgeon said:**
> I wouldn't listen to any of those guys, they are clearly fat guys and skinny nerds with glasses who hover round the coke machine on there lunch brake. 

Trolling doesn't raise your credibility on this forum. Consider this a "free warning". In the future try to contribute to, rather than detract from discussions.

---

### Post by thesurgeon on 2008-09-04
For a start did you know tht alot of routers come out the box unsecure with access to port 21, 23 and 80 open with access from the internet. Also they have default passwords which can be obtained from websites with a list of all default usernames and passwords. Once your into the router you can then port forward and DMZ. Once you DMZ a node it bypasses the security on the router so its on the internet side. Also I wouldn't just depend on NAT for your security as thats the bigest joke I've heard in a long time. As for antivirus, hackers don't just want access to your machine, they want access to any machine. So to stop the chance of passing on a virus, trojan, spyware etc to other users machines or other machines on your network I would recommend antivirus. And you clearly need to read more books and read up more about keeping access once access has been gained. Maybe look at programs like metasploit and learn how easy it is to infect machines. Your also wrong about Linux not haveing viruses etc made for them 

Some trojans, viruses, and worms are as follows:-

Trojans

Kaiten - Linux.Backdoor.Kaiten trojan horse
Rexob - Linux.Backdoor.Rexob trojan

Viruses

Alaeda - Virus.Linux.Alaeda
Bad Bunny - Perl.Badbunny 
Binom - Linux/Binom
Bliss 
Brundle
Bukowski
Diesel - Virus.Linux.Diesel.962
Kagob a - Virus.Linux.Kagob.a
Kagob b - Virus.Linux.Kagob.b
MetaPHOR (also known as Simile) 
Nuxbee - Virus.Linux.Nuxbee.1403
OSF.8759 
Podloso - Linux.Podloso (The iPod virus)
Rike - Virus.Linux.Rike.1627
RST - Virus.Linux.RST.a
Satyr - Virus.Linux.Satyr.a
Staog 
Vit - Virus.Linux.Vit.4096
Winter - Virus.Linux.Winter.341 
Winux (also known as Lindose and PEElf)
ZipWorm - Virus.Linux.ZipWorm 

Worms

Adm - Net-Worm.Linux.Adm
Adore
Cheese - Net-Worm.Linux.Cheese 
Devnull 
Kork
Linux/Lion (also known as Ramen) 
Mighty - Net-Worm.Linux.Mighty
Millen - Linux.Millen.Worm
Slapper
SSH Bruteforce

So what I was saying was once access to a router is gained you can do alot of things, all it takes is time and the knowledge to do it. Please don't try and put me down and make yourself look good because we are adults here not children.

also firewall software because if your using a modem you are in full display of the internet. Any scan gos directly to your machine. any attack gos directly to your machine. If your using a wireless router, you have a wireless network enabled, once your in its time to scan the machines and find ways in. I know it because I've done it. If theres windows machines on the network and you access those machines, you can use those to attack the Linux box. Also did you know that most attacks come from inside the network. REF:- ethical hackers handbook, hacking the art of exploitation....

One other thing, have you used Metasploit framework? have you seen this site [http://www.milw0rm.com/](http://www.milw0rm.com/) have you ever infected a machine, maybe sat and used trojans or tested things out in a lab?

And with comments like "So how do these program make my computer more secure? me thinks a little less comic reading and more time reading manuals...maybe its time for you to give up WOW :?)

---

### Post by jerome1232 on 2008-09-04
I still don't agree at all, even if I was stupid enough to use a default password on a router, I suppose if I had wep security or wpa with a easy/short passphrase my malicious neighbor could crack it, log in and forward whatever port he wanted, big whoop no listening services so he did nothing, the very worst thing he could do is screw up my dns and redirect me to phishing sites, then still my passwords as I log in and he's capturing the packets, or maybe it's his own web server I'm logging in to.

a: They would have to gain access to my LAN to log into my router. So must be some local guy willing to crack wpa with a really long passphrase, good luck. Unless of course you are so ignorant of security you turned on remote management and still have a default password, I really hope that router at least warns you.

b: If my computer is in DMZ mode, or had it's own public ip it still has zero listening services so once again nothing to attack. Let me repeat this no services to exploit.

c: I didn't say there were no viruses for linux, they exist, but not sure how you expect the average user to get one they install software from the repos, and hopefully don't go running around downloading scripts and typing sudo sh free-screensaver-here.bin

As far as the "we are all adults here" I was asking you why you feel it necessary to have a firewall and anti-virus and pointing out the reasons I think you do not. You are the one tossing out insults my friend.

If you want to run a firewall I can see using it as as a catch my mistakes in other places type of thing, "oops didn't configure my ssh server to only allow 192.168.1.0/24 in, that's okay my firewall and router are making up for my configuration mistake"

If you want to prevent contaminating other machines you will probably want to scan files before sharing them I do agree with you on that.

---

### Post by ksbalaji on 2008-09-04
> **matchstich said:**
> and get chkrootkit

run them both

Thanks ! I have installed and found no infection. Also, I have installed clamav (klamav) using which I rectified some errors.
ksbalaji

---

### Post by thesurgeon on 2008-09-05
Ill stick to my way and you can stick to yours. I really don't care what you do. 

:lolflag:

---

### Post by croissants on 2008-11-25
Hi everyone,

Are you sure Linux is not susceptible to viruses????

I'm with Intrepid which is fantastic, except that these last few days, every time I open my firefox browser it completely covers my desktop toolbars (you know, the upper one with with applications, places etc, and the lower one with bin, desktop switch options etc) and it's really weird I feel a bit vulnerable and don't know how to feel more trusting of my machine.

I worked out that I could go on to firefox and view>full screen and press this until it went back to normal, but I have never had to do this in the past.

What's going on?

Croissants :confused:

---

### Post by Chayak on 2008-11-25
I really should write up an FAQ on this but here it goes again.

Just because an AV engine tells you it doesn't detect anything doesn't mean your computer isn't infected.  AV scanners use defined signatures that must match in a file for it to detect anything.  It's trivial to take a binary that's being detected and repack or armor it to prevent it from being detected by anything save the few engines that do behavioral monitoring (Kaspersky and Symantic's recent SONAR).  Signature based AV engines can only detect malware that's been around long enough to be looked at.  I see a varying amount of samples every day and most get past the guantlet of AV scanners we have without detection.  Anti-virus only protects you against *old known threats* not new ones or an old one that the creator repacks to change the signature.

Everyone seems to suggest clamav for linux.  It has the worst detection rate of any engine I've seen.  It'll only give you a very small margin of protection against old threats if any and worst of all give you a false sense of security.  The same for rootkit scanners.  You don't think the creators of rootkits can get that software and make their tool invisible to it?  If you get in with the right people (generally defined as the wrong crowd) you can see some pretty elite rootkits for linux that are very tightly controlled by the groups who created them.  I've personally never seen a linux virus in the wild so in all there is a very minimal threat if any.

I'm a malware and security researcher by trade.  I keep seeing threads where people seem to think running AV will create some kind of magic shield to protect them from everything.  AV won't protect you from much in all honesty.  The best you can do is actually pay for Kaspersky 2009 or Norton Security 2009 as each have behavioral monitoring that does a decent job of catching things that get past the signature based scans.  It doesn't catch everything but it does catch a high percentage.

Security is a process.  One program won't protect you.  The best firewall software ever to be theoretically created won't help you at all if you leave your ssh port open and use a weak password on your account or fail to update your ssh server against a new exploit.  The best you can do is educate yourself from reputable sources, assess your level of threat and tailor your security to meet it, and don't download files from untrusted sources. (I get a good number of those undetected malware samples off of warez and pirate sites, a good number from keygens) The last is to keep your computer updated.  It's still possible to expoit it with something that isn't patched yet but the goal is to minimize your risk profile to reasonable levels.  The cost/time curve goes up rapidly for small increases in security after a certain point.

---

### Post by nubdora on 2008-11-25
> **croissants said:**
> Hi everyone,

Are you sure Linux is not susceptible to viruses????

I'm with Intrepid which is fantastic, except that these last few days, every time I open my firefox browser it completely covers my desktop toolbars (you know, the upper one with with applications, places etc, and the lower one with bin, desktop switch options etc) and it's really weird I feel a bit vulnerable and don't know how to feel more trusting of my machine.

I worked out that I could go on to firefox and view>full screen and press this until it went back to normal, but I have never had to do this in the past.

What's going on?

Croissants :confused:

Is this a serious post?

---

### Post by cariboo on 2008-11-25
I have the same probleem occasionaly, it only started after the update to Firefox 3.0.4, I hit F11 a couple of times and things are back to normal. It's more like a bug than a virus.

Jim

---

### Post by croissants on 2008-11-27
Nobdora: of course it's a serious post. The ubuntu forum is for EVERYONE (ie that is why it is called The Ubuntu Forum Community), techs and non-techs alike. 

Thanks Cariboo for the F11 - it worked!

:)
Croissants

---

### Post by vaseycorp on 2009-01-04
I thought I might join an existing thread, rather than start a new one.
Tonight I'm hunting down a bit of php code on emails with attachment and one of the links does a scan of my machine and reels off a host of infected files which took me back a bit. I'm running Ubuntu Studio with not a Windows page in site (apart from Wine and a basic Music editting program).

Also a few days back I got a message from Google telling me one of my websites is passing malware, so I closed it down, downloaded the entire site to check it out and posted a single index file. Getting Google to review the site is like pulling teeth, so even though there's one page saying the sites down, I keep getting the blocking message. I haven't been able to find any compromised code, which is a bit of a mystery.

I've read this thread and many others and just want to be reassured that things are not becoming unstable without my knowledge. 

Thank you

Keith, Bargara, Queensland, Australia

---

### Post by cariboo on 2009-01-04
You will get answers if you start a new thread, instead of burying it deep in an old thread.

Jim

---

### Post by bodhi.zazen on 2009-01-04
> **vaseycorp said:**
> I thought I might join an existing thread, rather than start a new one.
Tonight I'm hunting down a bit of php code on emails with attachment and one of the links does a scan of my machine and reels off a host of infected files which took me back a bit. I'm running Ubuntu Studio with not a Windows page in site (apart from Wine and a basic Music editting program).

Also a few days back I got a message from Google telling me one of my websites is passing malware, so I closed it down, downloaded the entire site to check it out and posted a single index file. Getting Google to review the site is like pulling teeth, so even though there's one page saying the sites down, I keep getting the blocking message. I haven't been able to find any compromised code, which is a bit of a mystery.

I've read this thread and many others and just want to be reassured that things are not becoming unstable without my knowledge. 

Thank you

Keith, Bargara, Queensland, Australia

Well you are talking apples and oranges.

Viruses are a specific type of malware / crack and Linux is not vulnerable to this type of attack.

It is possible, and given what your are saying, that someone exploited php code. I have seen this type of crack before but I am not good enough with PHP to be able to offer much assistance.

Are you running any other type of server ? ssh ? ftp ?

Check your logs.

Check your php code to see if it has been altered.

---

### Post by Vantrax on 2009-01-04
> **lisati said:**
> Reminds me of a situation a year or two back when I received a nasty little attachment by email. I contacted the owner of the email address (which, as can be expected, was forged) whose attitude was, "It's not my problem, I use Linux". I find that a little surprising, since his email address was being fraudulently used.

May be a little bit of a thread hijacking but this is actually a common problem. The emails arent actually being sent by the machine, or even from whoever is hosting the mail server. 99 times out of 100 they are spoofing the address. I have found myself spamming mail to myself once before through a work address and after tracing the email back found it originated in Romania. While thats a bad attitude the fellow took he is right, its not his problem, there is nothing he can do about it, and using Linux means that his computer is not the source of the email.

Its just a crappy situation all round. The guy is probably pissed as hell from all the mailing router rejection emails he gets. The last person I know that had that happen was getting around 450 bounce back emails a day for three weeks before it stopped.

---


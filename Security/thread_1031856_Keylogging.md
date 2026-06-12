---
title: "Keylogging"
date: 2009-01-05
forum: Security
---

### Post by vastpast on 2009-01-05
Is Ubuntu less vulnerable to keylogging than Windows XP?

I currently use Windows XP Pro (SP3) and I am seriously considering trying out Mint or Ubuntu. One of the most important things to me is security as I do a lot of internet banking.

One of my favourite security programmes is Keyscrambler by QFX. This programme is an anti keylogging programme which randomly scrambles your keystrokes so if you typed, for example: **government**, it might appear as** d%vp*22z-e** to a keylogger.
Well keyscrambler cannot be used with Linux, so are there any other keyscrambling programmes (preferably free) which are Linux friendly?
[B]
THANKS[/B]

---

### Post by Bachstelze on 2009-01-05
In Linux, if you don't do stupid things like installing programs from untrusted sources or randomy running commands, you won't have to worry about such thinks as keyloggers.

---

### Post by skizeee on 2009-01-05
Dont know about key scramblers but you could always try a graphical keyboard (on screen) search for it in Add/Remove couple there. Some bank websites use these although they often appear with the keys all jumbled up, so assuming there maybe a vulnerability there...

(I'll try to allay your fears) Otherwise consider this, Windows is targeted by hackers because it has such a large market, therefore hackers target windows machines because there is a lot more to gain,  potentially anyway. Its a bit like blindly shooting into a barrel of fish. I believe a hacker has to specifically target your machine and then know the holes to go through.

Linux I think only has one outward facing port instead of the many that windows uses often without your permission. 

There is a really good open source free ubuntu magazine called full circle magazine ([www.fullcirclemagazine.org](www.fullcirclemagazine.org)) it had an article on a program called truecrypt (makes an encrypted volume) for on the fly encryption/decryption, cant remember which issue, and look up tripwire, think it helps you determin if someone has hacked your system.

If none of this adequate see the Security discussions forum.

Otherwise you are a lot safer now then you ever have been in terms of security vulnerabilities...

PS I dont use Truecrypt or tripwire or a graphical keyboard and HymnToLife said it all..

---

### Post by bodhi.zazen on 2009-01-05
> **vastpast said:**
> Is Ubuntu less vulnerable to keylogging than Windows XP?

I currently use Windows XP Pro (SP3) and I am seriously considering trying out Mint or Ubuntu. One of the most important things to me is security as I do a lot of internet banking.

One of my favourite security programmes is Keyscrambler by QFX. This programme is an anti keylogging programme which randomly scrambles your keystrokes so if you typed, for example: **government**, it might appear as** d%vp*22z-e** to a keylogger.
Well keyscrambler cannot be used with Linux, so are there any other keyscrambling programmes (preferably free) which are Linux friendly?
[B]
THANKS[/B]

In general, yes Linux is less vulnerable to (software) key loggers. It is likely just as susceptible to physically attached key loggers (I do not know for certain).

See : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by some_random_noob on 2009-01-05
Maybe if you had a live cd then security would be good, because the disk can't get infected? (expert opinion needed here!)

Or you could use Ubuntu/Windows. Just block all ports but the following: 80, 443, 110, 25. And change your SSH port (if using Ubuntu).

---

### Post by Paqman on 2009-01-05
> **vastpast said:**
> Is Ubuntu less vulnerable to keylogging than Windows XP?


Considerably, yes. XP is a bit of a malware magnet.

On Linux, you can get all your software from centralised software libraries called repositories. That means that all your software is guaranteed 100% spyware/malware/adware free. We also have a permissions system that means malicious software can't install itself without you knowing. On top of this, the system can update _all_ your software automatically, so if any vulnerabilities are found they get automatically patched to keep you safe. Open source software in general has an excellent track record for security (eg: Firefox, Apache)

---

### Post by Paqman on 2009-01-05
> **skizeee said:**
> 
Linux I think only has one outward facing port instead of the many that windows uses often without your permission. 


Ubuntu has just as many ports as Windows, but by default they aren't available to an attacker. The default Ubuntu install has no services listening on any ports, so there's nothing there for an attack to exploit.

Windows has a ton of open ports and services, which is why you have to install firewalls to try and control the traffic.

---

### Post by lovinglinux on 2009-01-05
Don't forget to check if your web banking has support for Linux. I recall seeing a thread here about Citibank launching a new web banking system without Linux support a few months ago.

---

### Post by hyper_ch on 2009-01-06
linux is equal vulnerable to hardware keyloggers...

---

### Post by Unparallelogram on 2009-01-06
It's rather hard to stop an attacker with physical access to your machine. If nothing else, they're free to take a sledgehammer to it, or more reasonably boot from their own media etc. Most of your concerns should be about remote attackers. Installing bad stuff will get you in trouble on any system, but at least with Ubuntu, you can trust the official repositories. Also, Ubuntu has had a better history with remote vulnerabilities compared with Windows. Of course you won't be completely safe, but if anything you'll be relatively safer.

PS: I don't quite see how the key scrambling thing you mentioned works. Whatever the keylogger reads in, so does your intended target application.

---

### Post by hyper_ch on 2009-01-06
you can protect yourself against people getting access to your data through physical access ;)

---

### Post by scorp123 on 2009-01-06
> **skizeee said:**
>  Windows is targeted by hackers because it has such a large market, therefore hackers target windows machines because there is a lot more to gain You're totally ignoring the fact that Linux **_[COLOR="Red"]servers[/COLOR]_** are _absolutely_ on every respectable hacker's target list!! One of my customers is a financial institute and they transfer 1.7 billion Swiss Francs (= 1.52 billion US Dollars!) _every day_ over their wires. The majority of the 4000+ servers involved in this are Linux-based! You can't tell me that a hacker --or rather:-- cracker won't find such a target "highly interesting" ... :D  Then let's mention all those ISP's, all those Web-, DNS- and mail servers. All those e-Shops, web-shops, auction sites, and so on. Nowadays they all run some Unix-like OS. You can't tell me that these targets are "not interesting" for a hacker? :D

Your claim above is only true for Linux **[COLOR="Red"]desktops[/COLOR]** ... If we are talking about Linux desktops then I agree with your claim above. Trying to attack a Linux desktop installation is way too much of a hassle: per default there are most likely no interesting services running, there is hardly any way by which one might gain access, no high-volume network traffic to snoop, no daemons to crack, no remote exploits that would work because most likely there isn't even any network service running in the first place ... Yes, Linux desktops are so totally uninteresting for a hacker. He has nothing to gain here and he'd just be wasting his time.

But trust me ... Servers are a very different story! You want a hacker's attention? Pretend to be a big multi-billion dollar company and have a web server running 24x7. Add a few web based apps for good measure, e.g. a web forum, a web-shop with a SQL database backend ... and then pretend to be a lazy system administrator and leave your server totally unpatched for a month or so ... Trust me, sooner or later you will get their fullest attention and they will devote lots of time to get to know your precious little server better than you would like ... :twisted:

---

### Post by vastpast on 2009-01-06
> **Unparallelogram said:**
> It's rather hard to stop an attacker with physical access to your machine. If nothing else, they're free to take a sledgehammer to it, or more reasonably boot from their own media etc. Most of your concerns should be about remote attackers. Installing bad stuff will get you in trouble on any system, but at least with Ubuntu, you can trust the official repositories. Also, Ubuntu has had a better history with remote vulnerabilities compared with Windows. Of course you won't be completely safe, but if anything you'll be relatively safer.

PS: I don't quite see how the key scrambling thing you mentioned works. Whatever the keylogger reads in, so does your intended target application.


KeyScrambler encrypts your keystrokes in the kernel and decrypts it at the destination application, leaving Keyloggers with indecipherable keys to record. [http://www.qfxsoftware.com/]("http://www.qfxsoftware.com/")

---

### Post by scorp123 on 2009-01-06
> **vastpast said:**
> KeyScrambler encrypts your keystrokes in the kernel and decrypts it at the destination application, leaving Keyloggers with indecipherable keys to record. It is a keylogger itself!! :lolflag:

---

### Post by vastpast on 2009-01-06
> **scorp123 said:**
> It is a keylogger itself!! :lolflag:

:shock: #-o

---

### Post by scorp123 on 2009-01-07
> **vastpast said:**
> :shock: #-o If you look at their video it's obvious: If the application is able to intercept keystrokes at the device driver level and then process the keystrokes and afterwards paste the keystrokes into a target application ... then per definition it is a keylogger too. And best of all: it appears to be closed source??? So you can't really be sure what the application does with the keystrokes it intercepted.

I am sorry to say but using such a program appears very much downright stupid to me (no insult intended here!). I'd rather invest some time and secure my Windows OS (... if I were using Windows at all, that is ...) and make sure there is no malware _AT ALL_ rather than trust such an application which very easily *could* be malware itself.

Also: Fact is that there are many keyloggers which also work on the device driver level or which even replace the keyboard driver outright. I have had to use such programs myself. The claims of this program that they can "encrypt" keystrokes before any keylogger can get them is therefore a bit dubious.

And obviously this program does not help one little bit with hardware keyloggers. Anyone who has physical access to a computer could rig the keyboard and plant a hardware keylogger, either between the keyboard and the PC or in the inside of the keyboard itself. Been there, done that too. :D

---

### Post by vastpast on 2009-01-07
> **scorp123 said:**
> If you look at their video it's obvious: If the application is able to intercept keystrokes at the device driver level and then process the keystrokes and afterwards paste the keystrokes into a target application ... then per definition it is a keylogger too. And best of all: it appears to be closed source??? So you can't really be sure what the application does with the keystrokes it intercepted.

I am sorry to say but using such a program appears very much downright stupid to me (no insult intended here!). I'd rather invest some time and secure my Windows OS (... if I were using Windows at all, that is ...) and make sure there is no malware _AT ALL_ rather than trust such an application which very easily *could* be malware itself.

Also: Fact is that there are many keyloggers which also work on the device driver level or which even replace the keyboard driver outright. I have had to use such programs myself. The claims of this program that they can "encrypt" keystrokes before any keylogger can get them is therefore a bit dubious.

And obviously this program does not help one little bit with hardware keyloggers. Anyone who has physical access to a computer could rig the keyboard and plant a hardware keylogger, either between the keyboard and the PC or in the inside of the keyboard itself. Been there, done that too. :D

I do use other protection on my PC, the usual stuff for Windows. 

I have been using Keyscrambler  for well over a year, and I have logged into a number of bank accounts (my own) with it to access considerable amounts of money. I am happy to report I have not lost a single penny/cent so I fully trust Keyscrambler. 
It is recommended by a number of organisations such as PC World and Mozilla (FireFox: 

[http://www.pcworld.com/article/149399/15_great_free_privacy_downloads.html]("http://www.pcworld.com/article/149399/15_great_free_privacy_downloads.html")

[https://addons.mozilla.org/en-US/firefox/addon/3383]("https://addons.mozilla.org/en-US/firefox/addon/3383")


[http://www.qfxsoftware.com/press_makingnews.htm#in_media]("http://www.qfxsoftware.com/press_makingnews.htm#in_media")

---

### Post by scorp123 on 2009-01-07
> **vastpast said:**
> It is recommended by a number of organisations ...  Were they given the chance to inspect that program's source code?? I guess not. So what value does their recommendation have? **NONE.**

BTW, I too use telebanking since 1995 when I got my first dial-up access. And I use Linux since 1996. And so? Does this prove anything? Nope, it doesn't. Neither does your blind trust into that program. It just proves that Windows users like you (no insult intended!) can be tricked into installing **_anything_** for as long as a program promises to produce some "magic miracles" .... and you haven't even seen the source code of that thing, so you **_don't really know_** ***anything*** about that program and what it really does behind your back.

If you're serious about wanting to try Ubuntu (or any Linux for that matter) then I kindly suggest you let go of your "Windows-thinking". You don't need such programs here. Here on Linux people devote their time making sure that this OS is extremely hard to infect with anything in the first place rather than producing programs that by some miracle promises things which by my professional opinion cannot be 100% true.

I know a few keylogger programs (professional stuff not available to the general public ...) that work on the kernel level too and I am perfectly sure your "magic program" would fail if such keyloggers were to be used against you.

The state of Windows-based computing is really a sad one if users are being "educated" to regard the need of having such programs as being in any way "normal" ... ](*,)

---


---
title: "Viruses"
date: 2012-05-12
forum: Security
---

### Post by machdohvah on 2012-05-12
I have looked at a lot of the forums and would really like to know if viruses were actually detected on Ubuntu especially if one updates to the latest and greatest as they come along as I do. I mean do I have to worry about virus protextion?

---

### Post by wilee-nilee on 2012-05-12
No known viri on the web for a linux setup. Rootkits are your only worry, a strong password and the basic design makes it highly unlikely you will see one.

---

### Post by WorMzy on 2012-05-12
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

There are currently no known viruses for Linux in the wild. If you want to run antivirus software just in case, feel free.

---

### Post by sammiev on 2012-05-12
Post 2 and 3 are very well answered. I use a virus checker as I transfer files between different operating systems and I have never had a virus yet with Linux.

---

### Post by GreatDanton on 2012-05-12
I think you shouldn't worry about viruses, because hackers are usually writing them for Windows(over 90% of computers has Windows on it-so this can be the reason why there are no Linux viruses).

---

### Post by ex_isp on 2012-05-12
Since I run exclusively Linux, I will usually have clam installed just so I don't inadvertently pass something to Windows friends via an email I forward or such.

Just my 2 cents

---

### Post by codemaniac on 2012-05-12
As mentioned by ex_isp above your Ubuntu system cannot get affected by windows viruses , still it can act as carrier to those virus and affect the fellow windows systems .Clam would be a good rescuer in this situation .

---

### Post by wilee-nilee on 2012-05-13
Watch out for false positives if you use any av scanner, I had clamav show 5 that were just days ago.

I have that, avast and bitdefender installed they work nicely for scanning my W7 setup while it is off, the avast also shows false positives on my comodo setup, so always lookup on the web any found before just deleting, or quarantining.

---

### Post by codemaniac on 2012-05-13
> **wilee-nilee said:**
> Watch out for false positives if you use any av scanner, I had clamav show 5 that were just days ago.

I have that, avast and bitdefender installed they work nicely for scanning my W7 setup while it is off, the avast also shows false positives on my comodo setup, so always lookup on the web any found before just deleting, or quarantining.

+1 .They often tend to false alarms , you need to crosscheck their virus database before purging your "affected" files .

---

### Post by Hungry Man on 2012-05-13
I wouldn't use any AV. If you want to be protected against threats (remember, there were no OSX viruss in the wild until recently) that may show up in the future you should read up on apparmor - something that would have prevented the 700k sized botnet on OSX.

---

### Post by rookcifer on 2012-05-13
> **Hungry Man said:**
> I wouldn't use any AV. If you want to be protected against threats (remember, there were no OSX viruss in the wild until recently) that may show up in the future you should read up on apparmor - something that would have prevented the 700k sized botnet on OSX.

Chrome would have probably prevented it too (though I don't know if Chrome sandboxes on OSX or not).  In any case, I would wager most of the victims were using Safari.

I still haven't figured out how the trojan executed itself after it implanted itseld into the user /home directory.  Umask should have prevented it, though I am probably misunderstanding the exploit.

---

### Post by deadflowr on 2012-05-13
> **machdohvah said:**
> I have looked at a lot of the forums and would really like to know if viruses were actually detected on Ubuntu especially if one updates to the latest and greatest as they come along as I do. I mean do I have to worry about virus protextion?

Unfortunately, if your fear is that there are linux viruses running in the wild, anti-virus scanners will not help, as they do not know of any. AV are designed to scan for known viruses, such as windows viruses. Which is why most people who have installed an av on their ubuntu use it to scan email attachments, and most likely their wine directory.
Should you be worried? In a small way, I'd say yes. Being worried can keep someone proactive in their approach to the upkeep of a secure enviroment.
Fortunate for you linux and Ubuntu supply ample ammunition to combat malicious activity. If I were you I'd read up on the Stickies at the top this threads subforum starting with this

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

And I like to add that even though there are loads of tools and procedures you can add to your system to add extra security, Ubuntu is a very secure system out of the box.

---

### Post by Hungry Man on 2012-05-13
> **rookcifer said:**
> Chrome would have probably prevented it too (though I don't know if Chrome sandboxes on OSX or not).  In any case, I would wager most of the victims were using Safari.

I still haven't figured out how the trojan executed itself after it implanted itseld into the user /home directory.  Umask should have prevented it, though I am probably misunderstanding the exploit.

Chrome uses the BSD Sandbox on OSX. I don't think it sandboxes Java. On Windows Chrome limits IPC between Java and the broker process but other than that it doesn't sandbox or harden Java in any way.

I executed itself because Java called it. If you have one process open it can call others, right? My browser can start my Java process or Flash process and my Pidgin process opens my browser when I click a link etc. If Java is exploited it can just launch ****.

---

### Post by machdohvah on 2012-05-13
The reason I asked is that an Office Depot employee insisted that there are viruses out there that affect Ubuntu. Just saying...

---

### Post by Prescilla on 2012-05-13
I've been an Ubuntu user for almost 3 years now and I have never ever encountered any virus.
So, no worries.

---

### Post by deadflowr on 2012-05-13
> **machdohvah said:**
> The reason I asked is that an Office Depot employee insisted that there are viruses out there that affect Ubuntu. Just saying...

Well if your office depot employee is talking about the actual viruses as commonly defined, that sits in the realm of the unknown.At this point, we really don't know what sits out there in terms of viruses against linux.
However, if the employee is using the term virus as a catch-all for all malicious behaviors, then sure. There are malware and other things out there that can mess up your system.Rootkits for example.
I think it is important for anyone to use standard operating procedure when using their system. Such as don't run everything as root, don't install every packaged deb, or tar you comes across without thinking, don't install ppa's from someone who promises the moon. I think in essence use your brain, follow basic tenets, as this will help mitigate against most problems.
In terms of viruses infecting other outside programs like java and such. Sure they probably exist(I use probably, as I'm sure they do exist, I however don't know), but at this point all it will do is just crap out that particular program(And maybe something with a badly designed link to it). Linux systems make it hard to spread. As always I advice to keep your system up to date and to be proactive in the latest news in terms of security
know how.

---

### Post by Ms. Daisy on 2012-05-14
> **machdohvah said:**
> The reason I asked is that an Office Depot employee insisted that there are viruses out there that affect Ubuntu. Just saying...
Linux is not IMMUNE to viruses.  Using publicly-available tools, a knowledgeable person can crack linux as easily as windows.  Linux is not more secure than windows.  However, there are no viruses outside of laboratories or proof-of-concept for Linux.  Saying there are no viruses for Linux is NOT the same thing as saying there's no POSSIBILITY of viruses for Linux.  Hope that makes sense.

Read the basic security wiki in my signature for more about viruses in linux.  

The Office Depot guy doesn't know what he's talking about or his quote has been horribly misshapen.

---

### Post by rookcifer on 2012-05-14
> **machdohvah said:**
> The reason I asked is that an Office Depot employee insisted that there are viruses out there that affect Ubuntu. Just saying...

He is both wrong and right.  He is wrong in the sense there are none in the wild, and haven't been for years.  But he is right that there have been POC viruses written in the past. (it's not hard to write malware, but making it spread on Linux is much more difficult).

Viruses are the least of your worries on Linux.  More important is just keeping everything up to date.  If viruses ever become a problem, we will let you know.

EDIT:  Someone above mentioned rootkits.  Rootkits on Linux are not the same as they are on Windows.  People in the Windows security industry twisted the name "rootkit" to fit their own scare-tactic needs about 5-6 years ago.  Rootkits are a UNIX thing and have been around forever.  A rootkit on Windows is nothing but a trojan -- that's all it is.  The Windows security vendors "borrowed" the name from UNIX so they could create a new scary threat to make people buy more AV software.

A rootkit on Linux has a specific purpose, and that is to allow an attacker to hide his tracks after the box has been rooted. (that's why it's called a **root** kit).  The rootkit sits on the machine and performs actions to hide tracks (deleting log files, taking control of processes and hiding the fact they are running, etc.).  It also opens a backdoor to allow the attacker easy access to get back in.  Rootkits in Linux typically are installed manually and are not something you just get by browsing a website (people will generally use rootkits when they have compromised a server.  Once they get in, they install a rootkit to ensure the system remains compromised).

---

### Post by wilee-nilee on 2012-05-14
> **rookcifer said:**
> He is both wrong and right.  He is wrong in the sense there are none in the wild, and haven't been for years.  But he is right that there have been POC viruses written in the past. (it's not hard to write malware, but making it spread on Linux is much more difficult).

Viruses are the least of your worries on Linux.  More important is just keeping everything up to date.  If viruses ever become a problem, we will let you know.

EDIT:  Someone above mentioned rootkits.  Rootkits on Linux are not the same as they are on Windows.  People in the Windows security industry twisted the name "rootkit" to fit their own scare-tactic needs about 5-6 years ago.  Rootkits are a UNIX thing and have been around forever.  A rootkit on Windows is nothing but a trojan -- that's all it is.  The Windows security vendors "borrowed" the name from UNIX so they could create a new scary threat to make people buy more AV software.

A rootkit on Linux has a specific purpose, and that is to allow an attacker to hide his tracks after the box has been rooted. (that's why it's called a **root** kit).  The rootkit sits on the machine and performs actions to hide tracks (deleting log files, taking control of processes and hiding the fact they are running, etc.).  It also opens a backdoor to allow the attacker easy access to get back in.  Rootkits in Linux typically are installed manually and are not something you just get by browsing a website (people will generally use rootkits when they have compromised a server.  Once they get in, they install a rootkit to ensure the system remains compromised).

Never said they were the same in differing platforms, but thanks for clearing that up.

---

### Post by rookcifer on 2012-05-14
Also see [this guy's take]("https://linuxmafia.com/~rick/faq/index.php?page=virus") on the whole issue.  He gives a comprehensive overview of "viruses" on Linux and why they generally are not a problem.

---

### Post by Hungry Man on 2012-05-14
> **rookcifer said:**
> He is both wrong and right.  He is wrong in the sense there are none in the wild, and haven't been for years.  But he is right that there have been POC viruses written in the past. (it's not hard to write malware, but making it spread on Linux is much more difficult).

Viruses are the least of your worries on Linux.  More important is just keeping everything up to date.  If viruses ever become a problem, we will let you know.

EDIT:  Someone above mentioned rootkits.  Rootkits on Linux are not the same as they are on Windows.  People in the Windows security industry twisted the name "rootkit" to fit their own scare-tactic needs about 5-6 years ago.  Rootkits are a UNIX thing and have been around forever.  A rootkit on Windows is nothing but a trojan -- that's all it is.  The Windows security vendors "borrowed" the name from UNIX so they could create a new scary threat to make people buy more AV software.

A rootkit on Linux has a specific purpose, and that is to allow an attacker to hide his tracks after the box has been rooted. (that's why it's called a **root** kit).  The rootkit sits on the machine and performs actions to hide tracks (deleting log files, taking control of processes and hiding the fact they are running, etc.).  It also opens a backdoor to allow the attacker easy access to get back in.  Rootkits in Linux typically are installed manually and are not something you just get by browsing a website (people will generally use rootkits when they have compromised a server.  Once they get in, they install a rootkit to ensure the system remains compromised).
That's what they are on Windows too... A trojan is malware that tracks the user into installing it by pretending to be a legitimate piece of software (hence the name Trojan) and a rootkit on both Windows and Linux is as you described.

---

### Post by computeratin on 2012-05-14
Well, I'm still learning on the *nix side of things. But, a win "root kit" sounds like it shares some features with a *nix nasty of the same name.

Its basic point is to hide what's going it. On a doze machine they do things like hide bad stuff in the alternate data stream. Which is almost completely invisible to the OS (kind of). And a very good place to hide bad stuff; especially from scanners (though the better scanners are finally starting to catch on). The whole ADS is one of the biggest flaws in doze. (Um, correction FEATURE! LOL)

Win "root kits" also do things like create null registry values. Which are once again rather hard to scan and a good place to hide.

In so far as Ubuntu getting a "virus" goes: Can't happen. A windows executable pay load cannot run in a *nix environment without a lot of work; like installing Wine. Even then it still doesn't work a lot of the time.

But, that does not mean that you are 100% safe from every bad computer thing ever invented. Anything that one person can make another person can break. But, unless you're doing a lot of file transfers with a windows system then viruses are not really a concern.

Follow some basic safety / security guidelines and you'll be a lot safer than you would be on a windows machine.

As a matter of fact, I've been using Ubuntu virtual machines to protect my windows install from the web for the last year. It worked perfectly until I broke my own rules (nobody to blame but myself) and let windows connect directly to the web to download some stuff from a *very *reputable site that had been breached / infected and gave me coodies.

My wife's machine is still running strong because she didn't get lazy and break the house rules.

And as a 30 year win user I'm now in the process of building a Ubuntu machine that is actually designed to keep a windows virtual machine clean when it connects to a known dirty network.

Then, I'm going to make Ubuntu the primary installation on my computer.

So, long short: The guy at the store was probably trying to sell you something. Fear is one of the best motivators in the world to get people to part with their money.

---

### Post by jmore9 on 2012-05-14
I have been using linux since caldara came out long time ago.  There is very little chance of a linux machine being infected by a windows virus.  Linux is not bullet proof but it fairs way way better than windows on the virus front.

In my experience as long as you keep it updated and keep the firewall on you should not have any problems with virus's.  Now malware can fun on certain apps that you have running inside and that could happen but not that big of a concern.

If you back up regularly should never be bothered.

---

### Post by rookcifer on 2012-05-15
> **Hungry Man said:**
> That's what they are on Windows too... A trojan is malware that tracks the user into installing it by pretending to be a legitimate piece of software (hence the name Trojan) and a rootkit on both Windows and Linux is as you described.

Yeah but most "rootkits" on Windows are not installed manually by an intruder.  Rather, they are auto-attacks (drive-by's) since Windows security basically sucks, especially pre Windows 7.  The infamous Sony Rootkit was really just a trojan and not a "rootkit" at all.  Hence my point that rootkits on Windows are typically trojans that have a new scary name.

---

### Post by asadmalik on 2012-05-15
The first time i used an AV for linux was when I installed eset nod32 in my 11.04 and then again in 11.10. but it was never useful. but i did install it in 12.04 too.

As for windows, being aware and cautious is the thing if you have a weak av, but the same goes for linux.

Its very easy to say that there are very few virus/malware for linux, but then what if your system gets affected by one of those.Its always better to have a protection.

---

### Post by OpSecShellshock on 2012-05-15
> **rookcifer said:**
> Yeah but most "rootkits" on Windows are not installed manually by an intruder.  Rather, they are auto-attacks (drive-by's) since Windows security basically sucks, especially pre Windows 7.  The infamous Sony Rootkit was really just a trojan and not a "rootkit" at all.  Hence my point that rootkits on Windows are typically trojans that have a new scary name.

Yes, this is important to keep in mind. On Windows you can get something that is still considered a "trojan" even though no manual steps have to be taken by the user apart from navigating to the wrong site at the wrong time (for example every mainstream news website at one time or another has spread malware through its ad platforms, and every out of date Wordpress installation should be considered suspicious). On Linux there's a chance that browser/plugin exploits will function, but will lead to a crash at most rather than installing malware because the malware is developed for Windows. Sometimes the scripts will see that the browser isn't running on a Windows system and won't even load the exploits in order to avoid people like me finding them out.

There are folks out there who will happily develop malware specifically just for your system if someone pays them to, regardless of OS, but there's nothing you can do to stop that so it's best not to worry. It's only an outside chance for home users anyway.

---

### Post by Hungry Man on 2012-05-15
Malware does not have to be one thing or another. You can have a rootkit and a trojan. In fact, I'd say it's more common for malware to be considered "part x and part y" than anything else. The definitions for malware tend to be based on behavior (polymorphic, worm, virus, trojan - all are based on behaviors) and modern hackers pack multiple behaviors into a single sample. So while rootkits such as TDL4 and ZeroAccess are most definitely rootkits (they attain the highest privilege possible on the OS) they may also be rootkits that are installed through social engineering or worms that are installed through exploited computers on your network etc.

---

### Post by praveenkumarpon on 2012-05-16
> **wilee-nilee said:**
> Watch out for false positives if you use any av scanner, I had clamav show 5 that were just days ago.

I have that, avast and bitdefender installed they work nicely for scanning my W7 setup while it is off, the avast also shows false positives on my comodo setup, so always lookup on the web any found before just deleting, or quarantining.

Well, I am new to Ubuntu and I run it alongside Windows 7.
Clam antivirus showed about 30 threats in a folder which contained certain important pdf files. Later I scanned them in Windows using Microsoft Security Essentials and I was shocked that they were pdf files. I could have mistakenly deleted them using clam.

---

### Post by computeratin on 2012-05-17
> **praveenkumarpon said:**
> Well, I am new to Ubuntu and I run it alongside Windows 7.
Clam antivirus showed about 30 threats in a folder which contained certain important pdf files. Later I scanned them in Windows using Microsoft Security Essentials and I was shocked that they were pdf files. I could have mistakenly deleted them using clam.
 
They could just be CAV false positives. But, just because they are PDF does not mean that they are not infected. One of the most common forms of malware now is corrupted PDFs. If it were me, just to be sure, I'd DL one of the scanners that does not install to the system and runs in an independent / self contained package; like Comodo Cleaning Essentials. If it shows clean as well then I wouldn't worry about it.
 
I'd also suggest you get away from MSE. It's one of the worst endpoint clients out there. Comodo makes a good one.
 
And, if you're only reading PDFs then I'd suggest either doing it strictly on your UB install, creating a UB VM on your winstall for the job or or installing any of the better Adobe alternatives and putting it in a sandbox.
 
No matter how good your sec is one of the quickest ways to get infected on a winstall is to open a malformed PDF in Adobe.

---


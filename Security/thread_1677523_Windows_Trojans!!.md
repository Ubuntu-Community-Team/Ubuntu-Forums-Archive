---
title: "Windows Trojans?!?!"
date: 2011-01-28
forum: Security
---

### Post by IchBinWamphyri on 2011-01-28
Hi, just upgraded 10.10.
Just for shits and giggles last night I decided to run a CLAMAV antivirus scan.
came out with 360 Trojan.Gen7's all in files associated with microsoft (wine,crossover linux, and moonlight) scared the crap out of me as i havent had any problems with viruses in Ubuntu in the past. I Quarentined all infected files and uninstalled wine,crossover and moonlight. Wondering if anyone else has had issue with this at all and if so, how much trouble am i in here? Running ClamTK scan now, see how it turns out.

---

### Post by coffee412 on 2011-01-28
> **IchBinWamphyri said:**
> Hi, just upgraded 10.10.
Just for shits and giggles last night I decided to run a CLAMAV antivirus scan.
came out with 360 Trojan.Gen7's all in files associated with microsoft (wine,crossover linux, and moonlight) scared the crap out of me as i havent had any problems with viruses in Ubuntu in the past. I Quarentined all infected files and uninstalled wine,crossover and moonlight. Wondering if anyone else has had issue with this at all and if so, how much trouble am i in here? Running ClamTK scan now, see how it turns out.

The trojan is (as far as linux is concerned) is just another file. But its not going to run in linux. Wrong enviroment. So they would just sit there. Of course I hear that if you run them in wine they would atleast run. 

Its just they are treated like another file in my opinion.

---

### Post by IchBinWamphyri on 2011-01-28
thats what i was kind of worried about, they were found in moonlight, which is pretty much the linux workaround for silverlight, so wont the file be running as long as firefox is?

---

### Post by foxmulder881 on 2011-01-28
I have no idea about Moonlight as I've never heard of it. If it were me, I'd dump it as there's no real reason to even have Silverlight these days anyway.

But as already pointed out, the virus' are indeed just 'another' file. Nothing more than more 000 and 111's on the hard drive which will simply sit idle. So there's nothing to worry about.

---

### Post by coffee412 on 2011-01-28
> **IchBinWamphyri said:**
> thats what i was kind of worried about, they were found in moonlight, which is pretty much the linux workaround for silverlight, so wont the file be running as long as firefox is?

I think most viruses work on the underlying operating system rather than the browser. 

I think the number one reason to run clamav on linux is because you have connections to it from windows boxes. Example would be a mail server.

If your just running linux they should make no difference.

---

### Post by uRock on 2011-01-28
> **foxmulder881 said:**
> I have no idea about Moonlight as I've never heard of it. If it were me, I'd dump it as there's no real reason to even have Silverlight these days anyway.

But as already pointed out, the virus' are indeed just 'another' file. Nothing more than more 000 and 111's on the hard drive which will simply sit idle. So there's nothing to worry about.

+1 with removing Moonlight. It is incompatible with anything that uses Silverlight, such as Netflix. Thankfully, Netflix can be accessed via the Wii.

---

### Post by FuturePilot on 2011-01-28
> **uRock said:**
> +1 with removing Moonlight. It is incompatible with anything that uses Silverlight, such as Netflix. Thankfully, Netflix can be accessed via the Wii.

Incompatible with Netflix (currently)? Yes. Incompatible with anything written for Silverlight? Absolutely not.

---

### Post by BearDrummer on 2011-01-28
> **FuturePilot said:**
> Incompatible with Netflix (currently)? Yes. Incompatible with anything written for Silverlight? Absolutely not.

OK, then, how does one watch Netflix using ubuntu as their operating system?

---

### Post by uRock on 2011-01-28
Let's keep the thread on topic. Moonlight's uses are a different discussion.

---

### Post by steveneddy on 2011-01-28
There is really no reason to have anti-virus applications running on Linux unless you are scanning any forwarded messages, photos or other files to your Windows using friends.

At this time there aren't any virus, trojan or malware in the wild that is affecting Linux of any kind AFAIK.

That is not to say that there could be malicious software from a web site or maybe from gnomelook.org or something - (it's happenned before)

---

### Post by The Cog on 2011-01-29
> But as already pointed out, the virus' are indeed just 'another' file. Nothing more than more 000 and 111's on the hard drive which will simply sit idle. So there's nothing to worry about.
I disagree. As soon as you run an infected file in wine, you are breathing life into the virus. It can pretty-much do what it would do in a real windows system, except it won't be able to find the usual windows system files to infect. 

Bear in mind that the default wine install maps windows drives to your media folder, your cdrom drive and maps Z: to the Linux filesystem root. This means that the virus has the same access to your entire Linux file system as you do. It can read and write all your documents, probably read all other user's documents too.

---

### Post by rookcifer on 2011-01-29
> **BearDrummer said:**
> OK, then, how does one watch Netflix using ubuntu as their operating system?

You don't.

---

### Post by Jive Turkey on 2011-01-29
It may have improved since I used it last but clamav seems to pick up lots and lots of false positives.  I ran a scan once and it flagged almost every single win32 binary on my box as being either a virus or an infected file.  Try scanning your windows install cd with it and see for yourself.

---

### Post by IchBinWamphyri on 2011-01-30
what need would i have for a windows disc? I am running Ubuntu 10.10

---

### Post by uRock on 2011-01-30
> **IchBinWamphyri said:**
> what need would i have for a windows disc? I am running Ubuntu 10.10
It was meant to be hypothetical. If you scan a Windows install disk with ClamAV it will say there are viruses on the disk. Proving ClamAV does give lots of false positives. [s]ClamAV does not search for Linux viruses.[/s]

---

### Post by bodhi.zazen on 2011-01-31
> **uRock said:**
> ClamAV does not search for Linux viruses.

Yes it does.

Enter linux into the search box:

[http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

---

### Post by uRock on 2011-01-31
> **bodhi.zazen said:**
> Yes it does.

Enter linux into the search box:

[http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

I stand corrected.:p 

Cheers,
uRock

---

### Post by bodhi.zazen on 2011-02-01
> **uRock said:**
> I stand corrected.:p 

Cheers,
uRock

It is "OK", it is a common mistake / misunderstanding, I have seen it posted many times in many forums.

The thing is, your system should be patched to the known Linux viruses ;)

---

### Post by 1clue on 2011-02-01
> **steveneddy said:**
> There is really no reason to have anti-virus applications running on Linux unless you are scanning any forwarded messages, photos or other files to your Windows using friends.

At this time there aren't any virus, trojan or malware in the wild that is affecting Linux of any kind AFAIK.

That is not to say that there could be malicious software from a web site or maybe from gnomelook.org or something - (it's happenned before)

Holy misinformation, Batman!

Linux/UN*X with traditional permission schemes and security measures is not susceptible to viruses.

It is, however, susceptible to trojans, worms, buffer overruns and a large number of other techniques.  Google "Linux cert advisory" and start reading.


I see this sort of thing all the time, and then people wonder why they just got pwned.  No disrespect to steveneddy, but you GOTTA know better than this.

Wine, VMware and any other emulation software emulates Windows software.  All of it.

Moreover, any language that is common between the two works on Linux as well as it works on Windows.  Javascript, Java, Perl, PHP, all sorts of languages out there that are either interpreted from text on the fly or compiled to byte code for virtual machines will not care in the slightest if they're running on Windows, Mac, Linux, Solaris or some mainframe.  As long as they stick to the standard API that is implemented across all platforms, you have a universal application.  There are usually some cross-platform issues that need to be specifically addressed, but those may not have anything to do with what the malware is trying to accomplish.

Over 10 years ago, I worked at IBM.  There was a debate about whether somebody could write an email virus for Lotus Notes, which was the corporate email reader at the time.  A friend of mine did it, it would execute as soon as it hit the in box, you didn't even have to click on it.  Windows or Linux.

If it's a programming language, you can write malware in it.  If it's cross-platform then anywhere it runs, that malware can run.

UN*X is inherently resistant to viruses because of the way it's designed.  It's NOT inherently resistant to anything else.  Read your security-howto and start paying attention.

---

### Post by rookcifer on 2011-02-01
> **1clue said:**
> Wine, VMware and any other emulation software emulates Windows software.  All of it.

Not really.  The behavior of a Windows binary in WINE is not as predictable as it would be on Windows.  Some don't work at all.  And most trojans will not work under WINE because they are not programmed to be cross-platform (though I am sure this could be done, but I see no reason to when one could just write a trojan for Linux directly).

> Over 10 years ago, I worked at IBM.  There was a debate about whether somebody could write an email virus for Lotus Notes, which was the corporate email reader at the time.  A friend of mine did it, it would execute as soon as it hit the in box, you didn't even have to click on it.  Windows or Linux.

I don't see how that can happen with the proper umask setting.  Newly created files must be given explicit execute permission.  Try writing your own bash script and then saving it.  You will notice it wont run until you chmod +x it.

> UN*X is inherently resistant to viruses because of the way it's designed.  It's NOT inherently resistant to anything else.  Read your security-howto and start paying attention.

Anyone can wreck their system by running a trojan as root.  Anyone can have their server hacked if they are running a vulnerable service that hasn't been patched (or that isn't protected by NX/ASLR/SElinux).  So, yes, people should not be too complacent, but I see no reason for them to panic and begin installing AV software either.

---

### Post by 1clue on 2011-02-01
> **rookcifer said:**
> Not really.  The behavior of a Windows binary in WINE is not as predictable as it would be on Windows.  Some don't work at all.  And most trojans will not work under WINE because they are not programmed to be cross-platform (though I am sure this could be done, but I see no reason to when one could just write a trojan for Linux directly).


Yes, really.  The problem with wine is that some or all of the commercially licensed DLLs are missing.  Take a Windows system and remove those libraries and see how different it is.  If somebody has an installation in which they've added enough libraries and configured things properly then there's no reason why the malware wouldn't work.

I use VMware and other virtualization engines.  I use them specifically to test Windows software from a non-Windows system.  The testing is reliable enough to verify that the software I write can be safely sold to some company that pays a 6-digit number of US dollars to get it.

The difference between VMware and wine is that wine attempts to do everything with nonstandard rewritten implementations of the standard libraries.  Go try Crossover Office, they have some of the DLLs but it's wine under there.  Works pretty well.  The degree to which software works depends on how good the implementation of the underlying library calls are.

If the script uses fairly standard calls, then there's a pretty good chance that it WILL run on wine.  Are you going to bet your system security on the premise that it won't?

> 
I don't see how that can happen with the proper umask setting.  Newly created files must be given explicit execute permission.  Try writing your own bash script and then saving it.  You will notice it wont run until you chmod +x it.


At the time the Lotus Notes implementation we got was a wrapper around the Windows Lotus Notes.  It was definitely a hack, because the Powers That Be at IBM had dictated that every email client in the company would be a Lotus Notes application that had presumably been designed internally.  There was quite a bit of hardware that needed to have a client on it, so they were struggling to make it work.  

> 
Anyone can wreck their system by running a trojan as root.  Anyone can have their server hacked if they are running a vulnerable service that hasn't been patched (or that isn't protected by NX/ASLR/SElinux).  So, yes, people should not be too complacent, but I see no reason for them to panic and begin installing AV software either.

I've never installed antivirus on a Linux box.  You need to have good security and you probably should have some sort of tripwire or root-kit hunter installed, but to have something that looks like a genuine virus scanner, that seems a bit extreme to me too.

---


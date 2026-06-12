---
title: "How do I figure out what files are infected?  FULL PANIC MODE!"
date: 2008-11-11
forum: Security
---

### Post by josephellengar on 2008-11-11
I just ran a clamscan and it tells me that I have ELEVEN infected files (including my windows partition- but that does have F-secure on it, with regular updates).  But the readout doesn't say which files are infected.  How do I figure this out?  I had it do the -l option into a files, so I have that.  But I searched both virus and infected in the log and it didn't have either of those with any information.  Is there anywhere that clamscan records this?  Thanks!

---

### Post by phantomgunex on 2008-11-11
A... as for your ubuntu partition i dont think you should care so much about that cuz there is like so little viruses that are meant to infect computers running on linux. What you should do is boot into your windows partition and do an anti virus scan from there. I dunnno whether you can do that using vmware though...

---

### Post by josephellengar on 2008-11-11
> **phantomgunex said:**
> A... as for your ubuntu partition i dont think you should care so much about that cuz there is like so little viruses that are meant to infect computers running on linux. What you should do is boot into your windows partition and do an anti virus scan from there. I dunnno whether you can do that using vmware though...

My windows partition is entirely clean and it can't scan an ext3 fs.  There has to be at least some viruses on my linux partition.  How do I see what the results of the clamscan were?  I doubt that there could be eleven false positives.

---

### Post by randy78 on 2008-11-12
Before going into panic mode, do a search on the forums and you'll see that it's not that big of a deal ;)

Check here: [http://ubuntuforums.org/showthread.php?t=972312&highlight=viruses]("http://ubuntuforums.org/showthread.php?t=972312&highlight=viruses") and then here: [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by aysiu on 2008-11-12
> **idigchess said:**
> I doubt that there could be eleven false positives. Why do you doubt it?

---

### Post by cariboo on 2008-11-12
Clamav logs are located in /var/log, check your log files for which files are supposedly infected. Clamav only scans  for Windows viruses, and as you may have found out Windows executables do not run on Linux. 

I tried Clamav on my Linux installation including my Vista partiton it found the 2 windows viruses that I knew about on my Linux partition plus a couple on my Vista partition, that AVG hadn't sent to the virus vault.

The 2 viruses it found on my linux partition were ones I recieved in emails and I just saved them to see what I could find out about them. I guess I should get rid of them because I havent looked at them in a couple of years.

Jim

---

### Post by hyper_ch on 2008-11-12
don't run a windows virus scanner on linux binaries :)

Only run it on attachments of emails or (windows) files / documents in a shared/networked folders...

---

### Post by nubdora on 2008-11-12
Smells like false positives in here.

---

### Post by Kinstonian on 2008-11-12
It's impossible to tell if they are false positives before you investigate it or have more information.

Was the OP running as root and not taking proper precautions against viruses?  Does ClamAV say all files are infected with the same virus, or is it 11 different viruses?  Can you research the symptoms of the virus and see if you can find evidence of it's effects on your computer?  Are the alleged infected files in /bin, and have recent modification dates that are much more recent than other /bin binaries?  Is this the first time you've run an AV scan?  Have you perhaps done anything that could of infected your computer since the last AV scan?  A lot of hacker tools are infected with viruses.  Are there any obvious signs you've been hacked?  Can you submit the suspected infected files to [www.virustotal.com](www.virustotal.com) and see what other AV software says?

If you guys just dismiss anti-virus alerts as being fase positives without investigating them, then what's the point of running anti-virus software?

---

### Post by koenn on 2008-11-12
> **Kinstonian said:**
> 
If you guys just dismiss anti-virus alerts as being fase positives without investigating them, then what's the point of running anti-virus software?
see post  #6, #7 : AV programs only detect windows viruses, and windows viruses, just like any other winows executable, can't run on Linux, so if the OP detects viruses on his ext3 linux partition (post #3), it's most likely false positives. The other possibilities are : infected windows files inside wine, or infected files that came through downloads, mail attachments, etc. In any case, they won't run on Linux so they're harmless (although some might run in wine)

---

### Post by aysiu on 2008-11-12
> **Kinstonian said:**
> 
If you guys just dismiss anti-virus alerts as being fase positives without investigating them, then what's the point of running anti-virus software? Good point. I don't think there is a need for antivirus for home computers (they can be handy for servers, especially mail servers, though), even on a Windows computer. If you want real security, lock down your accounts instead of making them administrator accounts, and then educate yourself on how to avoid social engineering scams.

---

### Post by Kinstonian on 2008-11-12
> **koenn said:**
> see post  #6, #7 : AV programs only detect windows viruses, and windows viruses, just like any other winows executable, can't run on Linux, so if the OP detects viruses on his ext3 linux partition (post #3), it's most likely false positives. The other possibilities are : infected windows files inside wine, or infected files that came through downloads, mail attachments, etc. In any case, they won't run on Linux so they're harmless (although some might run in wine)

I don't know why you think ClamAV only detects Windows viruses, but it's not true.  My first Linux honeypot got hacked and infected with the Linux RST-B virus, a bot, and a rootkit.  ClamAV could detect all three according to virustotal.com.  In fact it's standard procedure when doing forensics on any system (Linux or Windows) to scan it for viruses.

---

### Post by HermanAB on 2008-11-12
On a Linux system, the fix for malware is to re-install the system.  Scanning for viruses is not particularly useful.  It is better to check your logs and occasionally run top to see what is running on the machine.

So if you got RST-B, then you should shut down and re-install Ubuntu from the CD.  That should not take more than about 20 minutes and then you know that the system is clean.  To keep a Linux system clean, is easy - don't install random crapware off the internet.

Cheers,

Herman

---

### Post by koenn on 2008-11-12
> **Kinstonian said:**
> I don't know why you think ClamAV only detects Windows viruses, but it's not true.  My first Linux honeypot got hacked and infected with the Linux RST-B virus, a bot, and a rootkit.  ClamAV could detect all three according to virustotal.com.  In fact it's standard procedure when doing forensics on any system (Linux or Windows) to scan it for viruses.
I don't remember where I got that - and it looks like you're right, clamav *can* scan linux executables (and *presumably* carries signatures for linux viruses). 
Still, the fact remains that it's practically impossible to create a successful linux virus (i.e. one that propagates by itself, not planted like the example you gave), that repairs for infections and fixes for exploitable holes come through the software distribution system rather than through the AV software (re what HermanAB said), and that AV on Linux is usually deployed on mail and file servers to detect Windows viruses. Also, of the 40-50 viruses that could run on Linux, there are between 0 and 'some' in the wild (numbers vary a bit depending on who you ask), the rest are experiments that only exist in laboratories;-.

---

### Post by cariboo on 2008-11-12
From: [http://linuxpoison.blogspot.com/2008/02/linux-virus-linuxrst-b-can-make.html](http://linuxpoison.blogspot.com/2008/02/linux-virus-linuxrst-b-can-make.html)

> A previous analysis by McCourt suggested that Rst-B infections are not being used by intruders to gain access to systems, rather they occur as a side-effect of already-infected hacking tools being downloaded onto servers once a foothold has been gained.

"The number of malware in existence is around 350,000, and while only a teeny number of these target Linux, it seems as though hackers are taking advantage of this false sense of security," said Carole Theriault, senior security consultant at Sophos.


at the bottom of the article:

> Sophos sells an on-access scanner for Linux. Alternatives include the AVG and Avast products for Linux, as well as software that works with the popular ClamAV to provide on-access scanning. 

The only thing I can find on this Rst-b is from for pay anti-virus companies.

Jim

---

### Post by brian_p on 2008-11-12
> **cariboo907 said:**
> 

The only thing I can find on this Rst-b is from for pay anti-virus companies.

Jim

[http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-01/0263.html](http://www.derkeiler.com/Newsgroups/comp.os.linux.security/2005-01/0263.html)

The link to linuxmafia.com near the bottom of the page is well worth a read.

---

### Post by HermanAB on 2008-11-12
> **cariboo907 said:**
> 
The only thing I can find on this Rst-b is from for pay anti-virus companies.

...and I think that is the clincher.  The AV companies want you and Pointy Haired Bosses to blow money on their 'solutions', even though they
a) Don't detect anything real and
b) Don't provide a solution to the detected 'problems'.

So the AV companies just want people to buy a 'feel good' toy to improve their balance sheet.

The *only* times I had to fix compromised servers was when some dumkopf thought it a bright idea to use a four character password, so someone got into the machine with SSH and turned it into a spam sender.  In those cases the compromise is very easy to detect, since the machine slows to a crawl and the network connection is flooded with crap, so a simple 'top' quickly shows what is running. Then I kill it and re-install the machine and send the client a big fat bill...

Cheers,

Herman

---

### Post by josephellengar on 2008-11-12
Thanks for all the help guys.  I found that most of them are false positives and the others were only emails.  Lol.  I really was panicking.  Anyway, I have two questions: is there any free software that makes clamav scan on access (I know I don't need it, but I still have some of the windows mindset), and if I run one of these viruses that I found in wine, is it possible that wine could damage the rest of my install?  Thanks!

---

### Post by randy78 on 2008-11-12
The most important thing is to stop messing around with infected files if you don't know what they can do/are capable of doing.

Legit software doesn't come packaged with Malware, so pay a bit more attention as to where your files are coming from.

You need to understand that you DO NOT need an on access scanner for Linux (they don't exist anyways).

---

### Post by linux_tech on 2008-11-12
Load Windows, then run a av scan from windows, AVG, Kaspersky av, etc.

---

### Post by josephellengar on 2008-11-12
> **Kinstonian said:**
> It's impossible to tell if they are false positives before you investigate it or have more information.

Was the OP running as root and not taking proper precautions against viruses?  Does ClamAV say all files are infected with the same virus, or is it 11 different viruses?  Can you research the symptoms of the virus and see if you can find evidence of it's effects on your computer?  Are the alleged infected files in /bin, and have recent modification dates that are much more recent than other /bin binaries?  Is this the first time you've run an AV scan?  Have you perhaps done anything that could of infected your computer since the last AV scan?  A lot of hacker tools are infected with viruses.  Are there any obvious signs you've been hacked?  Can you submit the suspected infected files to [www.virustotal.com](www.virustotal.com) and see what other AV software says?

If you guys just dismiss anti-virus alerts as being fase positives without investigating them, then what's the point of running anti-virus software?

I don't know how to tell what files are infected with the clamav readout.  That's why I posted this thread- so that I could figure out how to figure out what files are infected.  In response to your othere questinos, I never run as root, and I don't even know how to tell what the viruses were.

---

### Post by josephellengar on 2008-11-12
> **linux_tech said:**
> Load Windows, then run a av scan from windows, AVG, Kaspersky av, etc.

I have F-secure, and it can't scan any ext3 filesystems.

---


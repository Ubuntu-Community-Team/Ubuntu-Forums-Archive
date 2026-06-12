---
title: "Security recommendations for a new ubuntu user"
date: 2008-08-06
forum: Security
---

### Post by JoeLaX75 on 2008-08-06
Hello all! Two weeks ago I installed 8.04 and love it! Only problem is (or at least one of them so far) that I am concerned about how secure my computer is. I've done some searching and reading and found that there are no viruses out there, so a virus scanner is not needed. I've also read that ubuntu comes with a firewall.

What I want to know, is what would you recommend to someone who has a freshly installed version of ubuntu?

When I say security, I mean everything from viruses to people hacking into my computer.

I'm sorry if this question is a redundant one. I tried doing some searches, but was unable to find anything that completely answered my questions. Thanks for taking the time of reading my post and, again, I apologize for my "newness" to all this!

---

### Post by duckfeet on 2008-08-06
It's a good, reasonable, question, and usually lots of different answers: after I went thru all that, I figured I wanted a firewall I kind of understood, and so I installed "firestarter", and unless the world changes a whole lot--which it will, but not yet--I didn't figure I needed all the antivirus and malware scans I have on my XP HardDrive.  So I have a router, and then firestarter, and that's plenty, again, until I hear different...here's their site, if yer interested: [www.fs-security.com](www.fs-security.com)

---

### Post by tuxxy on 2008-08-06
Firestarter has been discontinued or so I beleive, think you should be using the ufw command line config tool for your firewall

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

As for antivirus theres a few available like Avast, ClamAV etc I dont think you would need one unless your regualrly sharing files with another windows drive.

---

### Post by vlovich on 2008-08-06
Turn off unneeded services and have a good password.  Linux security issues generally tend to get resolved really quick.

Also, I generally don't bother with a firewall because my computers tend to always be behind a router & its firewall (which tend to be much easier to set up although usually less flexible/powerful than the linux-based solution).  Anti-viruses are also unnecessary, although as with Windows, do not go around executing random binaries downloaded from the net.

Remember - generally all programs you'll ever install on Linux will either come with the source and you have to compile it yourself, or, more commonly, you'll just use Synaptic to install the binary you want directly.

---

### Post by hyper_ch on 2008-08-07
basically no firewall is required (or rather no modification of it)
basically no antivirus is required
basically as long as you stick to install software from the official repos you are fine

there are however exceptions.

If you are already behind a router for your lan then you don't need to mess with the firewall at all... only when you portforward services that you run and want to limit access you might want to alter the default rules

and by default there are no unnecessary services running like on windows.

antivirus is not needed also... there is no malware for linux out in the wild - however you could pass a virus to a windows user but I think it's ther responsability to keep their machines clean....

---

### Post by Dr Small on 2008-08-07
> **tuxxy said:**
> Firestarter has been discontinued or so I beleive, think you should be using the ufw command line config tool for your firewall

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

As for antivirus theres a few available like Avast, ClamAV etc I dont think you would need one unless your regualrly sharing files with another windows drive.
How can you discontinue an opensource project? As long as the source code is still avaliable, you can still use it, whether they officially support it or not.. If I would need a GUI based way to configure my firewall (which I don't), I would use Firestarter, whether it was outdated and unsupported or not.

Dr Small

---

### Post by hyper_ch on 2008-08-07
> **Dr Small said:**
> How can you discontinue an opensource project?

The original devs aren't working on it anymore... no other devs have been found to do so... no working on it for several years... this is, IMHO, sufficient to say it's discontinued as other projects like UFW have emerged.

---

### Post by ihatetryingtopickaloginna on 2008-08-07
I just ran the command ufw and it says my firewall is not loaded. But Firestarter shows it to be running. It even shows the very rare hits that is being blocked. If Firestarter isn't the firewall itself and it isn't loaded, then I'm just confused and am waiting for someone to un-confuse me.

---

### Post by hyper_ch on 2008-08-07
never used ufw.... only used firestarter a very long time ago when I thought I really need it - like on windows... but the firewall is called iptables

---

### Post by Kinstonian on 2008-08-07
I disagree with a couple things that have been mentioned in this thread.

1.  No firewall:  NAT capable routers are great as a **very** basic firewall.  The problem is it only protects your computer from external attacks.  One of the most common things an attacker does once she compromises a computer, is she uses it to attack other computers.  So, while a router with NAT will protect you from external attacks, it won't protect you from internal attacks.  If one computer on your network is compromised it is very possible it will be used to attack other computers on your network.  Every computer on your network should be able to some degree defend itself, and not rely 100% on the perimeter security.

2.  No anti-virus software:  I had one Linux based honeypot get hacked and the attacker downloaded a rootkit, bot script, and other binaries that she used were infected with the RST-B virus.  AV software would of detected all three of those forms of malware.  There is no doubt that viruses aren't as big of a threat for Linux as they are for Windows, but AV software clearly has some benefits on Linux.

---

### Post by hyper_ch on 2008-08-07
> **Kinstonian said:**
> Every computer on your network should be able to some degree defend itself, and not rely 100% on the perimeter security.
If no services are running on a computer - how would you attack it then?

> **Kinstonian said:**
> There is no doubt that viruses aren't as big of a threat for Linux as they are for Windows, but AV software clearly has some benefits on Linux.
So the box was hacked... and then manually put a virus on it... hmmm... how would an antivirus have prevented the planting of a virus WHILE the hacker - obviously skilled enough - had full root access?

---

### Post by timcredible on 2008-08-07
unless you have installed a server that open inbound ports (like telnetd, sshd, apache, etc.), a firewall will do nothing, because by default, there are no ports open with ubuntu desktop edition.  so, if it makes you feel better, run a firewall, but it isn't doing anything.  without open ports, nobody can access your machine remotely.  what you need to watch for is vulnerabilities in the applications, like firefox or thunderbird, etc.  that means don't click on links you don't know, don't try to open stuff you don't know in email, etc.

---

### Post by Dr Small on 2008-08-07
> **timcredible said:**
> that means don't click on links you don't know, don't try to open stuff you don't know in email, etc.

```
DrSmall> .cklinks
<VoteBot> Do not open any links from compiledkernel!
```

---

### Post by JoeLaX75 on 2008-08-07
Wow! Thank you all! I'm learning so much.

There seem to be a lot of conflicting viewpoints on the subject of security. Basically, I would PROBABLY be fine as long as I'm careful not to make a user error, however there are definitely risks out there. 

Since I am the "better safe than sorry" type of person, I think that it would be a good idea for me to set up my firewall and a virus scanner.

I saw the recommendations of cfw(sp?), but I have no idea what to do with it. I'm going to do a search on it, but in the mean time, does anyone have any suggestions?

Also, can anyone recommend a good virus scanner?



> **timcredible said:**
> unless you have installed a server that open inbound ports (like telnetd, sshd, apache, etc.), a firewall will do nothing, because by default, there are no ports open with ubuntu desktop edition.  so, if it makes you feel better, run a firewall, but it isn't doing anything.  without open ports, nobody can access your machine remotely.  what you need to watch for is vulnerabilities in the applications, like firefox or thunderbird, etc.  that means don't click on links you don't know, don't try to open stuff you don't know in email, etc.
How do I check whether or not I have any open ports.

---

### Post by animalprimate on 2008-08-07
heres a link to one good compilation of security information for new users, it includes some virus scanners too:

[http://ubuntuforums.org/showthread.php?t=765421]("http://ubuntuforums.org/showthread.php?t=765421")

---

### Post by jimv on 2008-08-07
There's really only one thing you have to worry about.  Don't give your password to anyone that you don't trust.  For 99% of home users, the Ubuntu defaults are just fine.

This flood of "recommendations" that you're getting is just the Ubuntu community showing off it's collective knowledge.

---

### Post by jflaker on 2008-08-07
Unlike windows, you must put some effort into getting an infection.  Windows will allow arbitrary code to run without you knowing...

Linux is more prone to social engineering than to malware that just "installs itself".  Most applications will need root access to further infection on a machine.  

You stand a better chance of corrupting your system by experimenting than by malware.  If you are given scripts or download them, always inspect the code before executing them.  If someone suggests commands to run, Understand WHAT the command does and WHY you would want to do that......a simple rm command with a few switches can wipe a whole directory structure from your system.

---

### Post by JoeLaX75 on 2008-08-07
> **animalprimate said:**
> heres a link to one good compilation of security information for new users, it includes some virus scanners too:

[http://ubuntuforums.org/showthread.php?t=765421]("http://ubuntuforums.org/showthread.php?t=765421")

Thank you! I've looked at this thread earlier, but it didn't spell everything out for me haha.  In other words, being a new user, the document still left me wondering what to do.


[QUOTE=jimv]This flood of "recommendations" that you're getting is just the Ubuntu community showing off it's collective knowledge.[/QUOTE]

I know. I love it! It's how I learn.

---

### Post by Dr Small on 2008-08-07
> **JoeLaX75 said:**
> 
Since I am the "better safe than sorry" type of person, I think that it would be a good idea for me to set up my firewall and a virus scanner.


But whether that is your mentality or not, it is not required. Virus scanners are useless on linux to protect you against any viruses that could come in the future, and you don't need a firewall if you are not running any services.

---

### Post by SuperSonic4 on 2008-08-07
Isn't **clamav** in the repos for an antivirus program? I suggest getting one if you run wine or dual boot with windows

---

### Post by cariboo on 2008-08-08
If you want to check for open ports I use namp it is available in the repositories and there is a gui for it if you need one. Search Synaptic Package manager for nmap and nmapfe.

You will see one port reported open port 631 this is for the cups printing system,by default it is set that only your computer can access it.

Jim

---

### Post by Jose Catre-Vandis on 2008-08-11
For those of us who might carry out on-line banking or any on-line shopping in the UK, the current banking code expects us to keep our "security" (firewall/antivirus/malware protection etc) "up to date".

Now I religiously update Ubuntu when asked by the update manager, but have not seen the need for firewall/antivirus/malware checker on Ubuntu. I am also behind a netgear router with NAT / Firewall. So where will I stand if my financial information gets compromised somehow and the "bank" decides not to support me and expect me to pick up the costs? Now I could install the firewall/antivirus etc, but I know they are thinking about Windows PCs...

---

### Post by dperfors on 2008-08-12
I think that recommandation is mostly there so that it is not possible to get virusses and stuff that detects your keyboard input or unencrypted messages. as long as you know that there can't be anything installed without your approval and the website of the bank is safe (uses encryption), than I think you are safe.

---

### Post by hyper_ch on 2008-08-12
> **Jose Catre-Vandis said:**
> For those of us who might carry out on-line banking or any on-line shopping in the UK, the current banking code expects us to keep our "security" (firewall/antivirus/malware protection etc) "up to date".
Has this ever been tested at court? The banks can put as many conditions as they want - if it's against the law the court will not uphold them. There has been a court decision lately regarding CC cards and pins... I think it was a German verdict where the customer was protected.

---

### Post by CHECKMATE2X on 2008-08-12
I am currently using Ubuntu 8.04. I have installed the Panda anti-virus. When I clicked on the icon button to udate, the window just flashes and disapper. Anybody kindly advise how to stop this form happing. Thanks in advance.

---


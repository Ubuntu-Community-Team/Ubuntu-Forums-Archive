---
title: "Anti virus for Ubuntu"
date: 2012-08-27
forum: Security
---

### Post by emmagood on 2012-08-27
Hi,

  I was going though a list of anti virus on the net for my Windows setup when I came across anti viruses for ubuntu. Previously, as I knew, anti viruses are not required for Linux. Can anyone advice on this. Same for firewalls and anti-malware.

Thanks,
Emma Good

---

### Post by NilPointer on 2012-08-27
> **emmagood said:**
> Hi,

  I was going though a list of anti virus on the net for my Windows setup when I came across anti viruses for ubuntu. Previously, as I knew, anti viruses are not required for Linux. Can anyone advice on this. Same for firewalls and anti-malware.

Thanks,
Emma Good

Firewall is definitely must-have on any system, Linux included (well, NetFilter firewall is already bundled into linux kernel and can be configured with iptables or GUI tools, so there is no need to install anything).

As for antiviruses, they're used only to check mail, etc. to prevent infection of Windows machines. Some viruses for linux exist, but almost all of them must be compiled and executed manually, so basically, linux doesn't need antivirus. Anyway, you can install chkrootkit and rkhunter and check your system from time to time just to be safe, but they tend to find lots of false positives.

---

### Post by jwright8 on 2012-08-27
Before you do anything else, I'd read here first:

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

Then I'd read over (at least mostly) this:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Are you talking about a client or a server implementation of Linux?  The above poster is correct; anti-viruses on Linux TYPICALLY are for not becoming a "carrier" for sending a virus from one Windows machine to another over your mail server. 

You do, however, need a rootkit analyzer such as chkrootkit or rkhunter, imo.  These can, and likely will, throw false positives, so be sure to investigate every time something comes up when you scan with it.  

An interesting caveat here, though, is something interesting I ran into when I was first toying around with web servers, just to learn about them.  I had made a backup on my Windows machine, as my Linux server was really acting funny and sluggish, and it was spiking at the most random of times.  I scanned my hard drive on the Windows machine by chance and Avast (the Windows AV I use) came up with a file in the backup that was .php as a type of virus.  I later checked on the Linux box and discovered my machine was being used as part of an IRC botnet to (presumably) DDoS others.  I contacted my provider (Linode) and told them of it, and they immediately responded saying that they were about to cut my service since they had noticed the same thing.  The .php file was actually what they used to somehow gain shell access to WGET all they'd need and execute.  In this case, an AV gave me a good indication.  However, this was when I knew less than I do now about Linux (though I'm far from knowing a lot), but perhaps me relating that to you will help someone else in the future that is learning as well.

Since, I've always chmodded my WGET/GET to only allow root to use it.  The reasoning here is that if they already have root access, I have a lot more to worry about than them WGET'ing some more stuff.  

If, however, you want an AV client just because, you can install ClamAV, which is the typical AV of choice for Linux from what I've seen.  It will also detect Windows viruses, as well as the (rare) piece of Linux malware, to my understanding.

```

apt-get install clamav

```When you tell us if you use it for client or server, we could probably give you a better idea about what you're asking, though there are a lot of people that know a lot more about it than I here.  This is a wonderful place to learn about Linux in general :).

---

### Post by Ms. Daisy on 2012-08-27
This [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) has all the answers to your questions.
 
Anti-Virus: [QUOTE=wiki]At the time of writing, there are no known viruses on the big bad web designed to target Linux. A few targeting Windows can execute in a manner that could allow compromise of a Linux system via an interpreter layer like [Wine]("https://help.ubuntu.com/community/Wine"). Very few people recommend existing anti-virus software for Linux machines, in part because there are few decent free anti-malware solutions available. Enterprise class solutions are good, but the consumer-grade products aren't on par with their Windows counterparts enough to warrant their use. Moreover, if you focus entirely on viruses then you are ignoring the vast majority of real threats to your Ubuntu machine.[/QUOTE]
 
You need a Firewall: [QUOTE=wiki]There is a lot of existing information about firewalls - along with a long-term raging debate on the need of a firewall on Ubuntu. We recommend you enable it because you have ports open if you are reading this page. Traffic can go in and out of that port unhindered without a firewall. Malicious programs can open arbitrary ports unless you have a firewall to prevent that. A NAT router can add a layer of protection, but it will not protect you in lieu of a firewall.[/QUOTE]

---

### Post by rookcifer on 2012-08-27
> **jwright8 said:**
> You do, however, need a rootkit analyzer such as chkrootkit or rkhunter, imo.  These can, and likely will, throw false positives, so be sure to investigate every time something comes up when you scan with it.  

You don't need those tools. They are only good for people who are experts and/or server admins.  Completely useless on a desktop machine.  All these tools do is confuse newbs.

---

### Post by jwright8 on 2012-08-27
There's only one way to learn, hence why I added the part about it throwing false positives.  I tend to give people the benefit of the doubt instead of labeling them mindless "newbs," as it is precisely the way I learned what little I know in the scheme of things in this particular area.      Although, that assumption aside, I'll beg to differ on that too.  Rootkits are made for Linux (and ALL other operating systems), beginning and end of story.  While they're not nearly as common as, say, Windows viruses, its still very possible to run up on one in the wild (particularly if you're using a Linux distro as your daily user).  I'd hardly say that a few false positives (which they can ask about on this forum.. you know the place they posted in the first place?) are a huge price to pay for a little extra peace of mind and a little learning. 

For instance, when you say ClamAV is sufficent: 
   [http://www.pcworld.com/businesscenter/article/145703/hackers_find_a_new_place_to_hide_rootkits.html](http://www.pcworld.com/businesscenter/article/145703/hackers_find_a_new_place_to_hide_rootkits.html) 
   Please, read that article and tell me again that ClamAV is and will always be sufficient for the easily-confused "newbs."  Every little bit helps.

If you'll read here:
[http://chakra-linux.org/wiki/index.php/Anti-Malware](http://chakra-linux.org/wiki/index.php/Anti-Malware)
It says:
> 
ClamAV is great, but it was not designed to detect rootkits. Rootkits, a  type of malware, are used to hide the presence of an attacker or other  malicious software on your system, and can be very difficult to detect.  Fortunately, Chakra provides two tools that can help you detect the  presence of these nasty pieces of code: [[[1]]("http://www.chkrootkit.org/%7Cchkrootkit")], and [[[2]]("http://rkhunter.sourceforge.net/%7Crkhunter")]. These tools both work in different ways, so if you are worried you might have a rootkit, you may want to run both.  
 In addition, I find rkhunter to be fairly straightforward.  If the user has any problems, there's this crazy thing called apt-get remove that might possibly be of use.  She asked for stuff she MIGHT need, and I think keeping her in the dark is hardly the "pro" way to help a "newb" asking for help on a help forum.  Regardless, it's not rocket science to understand the (general) output of rkhunter.  Like I said, she can always remove it if it proves useless, but I feel better at least letting her know of the possibility of ClamAV not being quite as comprehensive as it is sometimes made out to be.

If I had told her to use something like snort, or configure her own iptables scripts and cron tabs, I could see that comment having some relevance.  As it stands, it was completely over the top and potentially detrimental.

As an aside to the OP, if you wanted to learn more in general, this seems like a good link:
[http://www.ibm.com/developerworks/linux/tutorials/l-harden-desktop/index.html](http://www.ibm.com/developerworks/linux/tutorials/l-harden-desktop/index.html)
I was just looking over it, and it actually seems fairly interesting (though I think a little outdated, but the material should still be good).

---

### Post by rookcifer on 2012-08-28
> **jwright8 said:**
> Although, that assumption aside, I'll beg to differ on that too.  Rootkits are made for Linux (and ALL other operating systems), beginning and end of story.  While they're not nearly as common as, say, Windows viruses, its still very possible to run up on one in the wild (particularly if you're using a Linux distro as your daily user).  

Show me one desktop user who has *ever* ran into a rootkit in the wild.  Rootkits on Unix/Linux are different animals than on Windows.  On Unix, they are tools a hacker uses to *maintain* access to a box he has already cracked some other way (and to also cover his tracks).  You aren't going to be surfing around and suddenly get pwned by a rootkit on Linux.  This is especially true if you stick with the official repositories.

Servers are different because they are much bigger targets (well, because they are servers listening to the web at large).  If Apache has a flaw, for instance, a hacker could get in and then manually install a rootkit.  In that case one could make an argument that a server admin *might* need a rootkit scanner.  However, even then I think they are worthless.  Why?  Because if an attacker gets root, he can hide from a scanner.  If he has root it's game over and a rootkit scanner wont help one bit.  The only course of action is to reinstall fresh.

Better alternatives for servers are tools like Tripwire or AIDE.  They can detect intrusions and cannot be modified by an attacker if setup properly.

So, yes, I think discussions of rootkit scanners only confuses newbs.  They think AV scanners are the answer to all security problems (since they came from Windows) and don't realize that on Linux they are all but worthless.

---

### Post by jwright8 on 2012-08-28
> **rookcifer said:**
> Show me one desktop user who has *ever* ran into a rootkit in the wild.  Rootkits on Unix/Linux are different animals than on Windows.


nakedsecurity.sophos.com/2010/10/28/cross-platform-worm-targets-facebook-users/

Guess I better stop WGET'ing all those MySpace layouts for my coding inspiration while I'm at it, too ;).  :lolflag:

In seriousness, that article is also almost two years old, and I found it in about 10 seconds.  We all know that computing, both the good AND the bad, tends to advance at a rapid pace.  To assume that it isn't possible is actually foolhardy.  It reminds me of someone I spoke to once that had this massive conspiracy theory about Windows AV programs.  He told me:

> 
I've never gotten a virus, those anti-virus programs are just a gimmick to get your money.  Get this.  I've had a computer for 6 years, and I've never had anything pop up telling me I had a virus.
Needless to say, I was embarrassed for him.

You are also overlooking the lack of popularity of Linux as a daily use desktop environment. I'm sure if Linux gained in popularity (as OSX did), then we'd be having a very different conversation.  Remember the joke behind OSX having no viruses is because no one  cares to make one?  Even that old joke, though, actually shows how things  change.  Remember the OSX virus article that surfaced on Slashdot less  than a month ago?

It also stands to reason that people infected with rootkits might not even realize they are infected... especially given that you are correct in saying that they operate far differently than Windows-based viruses/malware/rootkits.  

Regardless, this isn't about stoking your ego.  It's about helping someone else at least have a fighting chance at trying to protect themselves and detect problems while they are able to learn more about it.  You also overlooked the fact that in the event that something like RKHunter was confusing, I said it would be easy enough to remove it. RKHunter scans files; it doesn't automatically change them without the user's consent.  If it did, then you MIGHT have a point; as it stands, you don't.  If you really wanted to help, you'd have offered any other suggestions you may have instead of dismissing the OP as an idiot that can't figure out a rootkit scanner or post a question to ask what the results mean.  That is particularly ironic considering that this topic is in the proper help forum on the proper site in the first place.

---

### Post by rookcifer on 2012-08-28
> **jwright8 said:**
> nakedsecurity.sophos.com/2010/10/28/cross-platform-worm-targets-facebook-users/

That's not a rootkit.  It is a Java applet that the user must manually install himself.  I asked for examples of rootkits.

> You are also overlooking the lack of popularity of Linux as a daily use desktop environment. I'm sure if Linux gained in popularity (as OSX did), then we'd be having a very different conversation.  Remember the joke behind OSX having no viruses is because no one  cares to make one?  Even that old joke, though, actually shows how things  change.  Remember the OSX virus article that surfaced on Slashdot less  than a month ago?

Yes that OSX "virus" that was essentially due to Java being exploited in the browser. 

Indeed there is a new Java 7 exploit that was released just yesterday in the wild.  Metasploit has already added it to their collection.  I tested it against Ubuntu 12.04 and it owned Firefox and Chrome (it didn't get root however).  But I turned AppArmor on for both browsers and the exploit failed.  AppArmor wouldn't let it download and execute the payload from /tmp.  This is why AppArmor and other MAC systems (SELinux, etc.) are far more effective than AV and is what I recommend users learn if they want real security.

> It also stands to reason that people infected with rootkits might not even realize they are infected... especially given that you are correct in saying that they operate far differently than Windows-based viruses/malware/rootkits.

That's my point.  You wont know and a scanner wont help.  All the attacker has to do is modify the scanner or modify the rootkit itself.  If he has root, he can modify anything.  The only way around this is to scan the machine from another clean machine.  But even then the results are often difficult to interpret.  Usually you only know you are compromised when things start "acting funny."  It could be you notice connections to some unknown server or that your CPU is going crazy for no reason, etc.  But this is usually not an issue on a desktop machine behind a firewall (assuming the user isn't stupid and is running a wide open VNC or SSH server).

> Regardless, this isn't about stoking your ego.  It's about helping someone else at least have a fighting chance at trying to protect themselves and detect problems while they are able to learn more about it. 

If you're a server admin then by all means experiment with RKHunter.  It is not needed on a desktop machine.  There are far more effective measures to take (like PaX and MAC systems).

---

### Post by emmagood on 2012-08-29
Hi,

  Thanks for the replies. As I understand, firewall is required. For antivirus, if there is windows installed in the PC it may be required so that viruses dont proliferate into the windows installation. 

 I have a dual boot system (WinXP/Ubuntu). It is a regular installation (non Wubi). So if I dont keep an anti-virus, can the viruses come through Ubuntu and move into windows side.

Thanks,
Emma Good

---

### Post by NilPointer on 2012-08-29
> **emmagood said:**
> Hi,

  Thanks for the replies. As I understand, firewall is required. For antivirus, if there is windows installed in the PC it may be required so that viruses dont proliferate into the windows installation. 

 I have a dual boot system (WinXP/Ubuntu). It is a regular installation (non Wubi). So if I dont keep an anti-virus, can the viruses come through Ubuntu and move into windows side.

Thanks,
Emma Good

It shouldn't move to Windows, unless you help it to do so. I mean,

1) If you download any Windows software, you can check it on VirusTotal before running on Wine/Windows. It's free online service, that can check file you send with 40+ antiviruses. Detection probability is certainly higher than of single antivirus.

2) Don't run unchecked software under Wine - some malware won't run, but others will. If Wine isn't securely configured, malware could infect all executable files it could find, including Windows ones.

3) If you run untrusted software under virtual machine - disable networking and shared folders, so virus won't escape it.

If you follow these rules, viruses shouldn't be able to get to Windows side and antivirus wouldn't be needed at all.

---


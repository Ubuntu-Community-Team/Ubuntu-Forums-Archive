---
title: "beginner with hacked openssh box, please help!"
date: 2009-07-29
forum: Security
---

### Post by quixote on 2009-07-29
I set up openssh 2 months ago on a Debian Lenny server.  This morning I saw it was being accessed by an IP in China! I was forwarding port 22 on my router: so could they have been using something besides ssh to get in?  I still had password access as a fallback.  Was that the weakest link?  Here are the details:

I don't think there was an attempt to brute force crack the passwords (which were kind of simple :( ) because wouldn't there have been messages to root about the attempts?  Or can those messages be suppressed?  I checked that before I sent "halt now" to the system.

Can some other protocol besides ssh get into the server using port 22, which was enabled for ssh access?  If the answer is yes, how should I forward a port for ssh without allowing other access?  The firewall on my router is such that the only way to access anything behind it is with port forwarding.

The openssh version is whatever was current about two months ago.  Not sure of the number, but it is a recent version.

After I forced the system to shut down, it won't boot back up.  Is there a way to look at the hard disk and try to figure out what they were trying to do?  I'm planning on repartitioning and reinstalling, which I assume will wipe out anything they might have left hanging around, right?

---

### Post by cariboo on 2009-07-29
Your password was more then likely the culprit. If you have a Live CD you can boot from it and check /var/log/Auth.log to see if that was the problem. The log will tell you how many tries it took to break your password. Seeing as you don't know what has been done, the best thing to do is to backup all your important data, and reformat and reinstall.

---

### Post by jerome1232 on 2009-07-29
Personally once i get keys working I disable password auth.

At the least install fail2ban or denyhosts. Alternatively setup iptables to ban connections. All three can be setup to ban an ip address after so many failed attempted ssh logins. 

A server running on port 22 will get hit all day everyday so key's or a good passphrase are mandatory.

---

### Post by igorzwx on 2009-07-29
To be reasonably paranoid, if the box was really hacked that file
/var/log/Auth.log
is likely to be removed or "corrected".
Some people store such files on another box.

---

### Post by igorzwx on 2009-07-29
**[*Practical UNIX* and *Internet Security* | O'Reilly Media]("http://oreilly.com/catalog/9781565921481/")**

This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more **...**
oreilly.com/catalog/9781565921481/ - [Cached]("http://209.85.129.132/search?q=cache:S8ZqyAGhsCwJ:oreilly.com/catalog/9781565921481/+practical+internet+and+unix+security&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:oreilly.com/catalog/9781565921481/")

---

### Post by quixote on 2009-07-29
Thanks for the answers, folks!  I'm going to be quicker about removing password access after the next install!  

I have a dumb problem with looking at /var/log/Auth.log:  This was a headless server that I could only access via ssh from one of my ubuntu machines.  So, now, with no OS on the server, and no ssh on it, it doesn't show up as anything.  It doesn't have a CD drive.  I could boot off a USB stick perhaps, but I don't have one ready to go to do that.  If I plug into its USB port directly, it doesn't show up as a partition either. Is there any way I can look at the file, under the circumstances, that I haven't thought of?  If it's complicated, and since the only purpose to looking at it is curiosity, should I just forget about it and go ahead with the reinstall?

---

### Post by bodhi.zazen on 2009-07-29
> **jerome1232 said:**
> personally once i get keys working i disable password auth.

At the least install fail2ban or denyhosts. Alternatively setup iptables to ban connections. All three can be setup to ban an ip address after so many failed attempted ssh logins. 

A server running on port 22 will get hit all day everyday so key's or a good passphrase are mandatory.

+1

---

### Post by koenn on 2009-07-29
> **quixote said:**
> T Is there any way I can look at the file, under the circumstances, that I haven't thought of?  If it's complicated, and since the only purpose to looking at it is curiosity, should I just forget about it and go ahead with the reinstall?
if it's worth the trouble, you can see of you can temporarily put the drive in another, working, computer, and mount it there to have a look at it contents.
Other than that, if it has nothing you can boot off, how you going to reinstall ? 
While you repartition for a nes install, you might consider trying to shrink and keep the existing partition so that after the install, you can mount it and salvage your logs. Then wipe the partition and mount it as something useful (/srv, /home, /var/log ...) 

but i doubt it's worth it. If your OS is already toast, what are the chances they left the log files there ?

---

### Post by quixote on 2009-07-29
Okay.  This is embarrassing.  Apparently the OS was not toast.  I'd disconnected everything from the internet, in the process also disconnected the headless server from the router, so it couldn't get its dhcp lease, so -- duh -- nothing else could see it.  (Re: how could I reinstall: this is an HP 1TB drive that has the option to put into rescue mode with a hardware switch, download a new bootloader, and start over.)

/var/log/auth.log had hundreds of attempted accesses in it, all within the last few hours.  If I make more than 3 typos logging in, I get locked out for some time.  Why didn't that happen here??

The other thing I don't get is that buried in the failed logins, is one with my login name saying I'd successfully su'ed to root (about 40 min before I noticed and shut it down).  That's followed by more unsuccessful login attempts.  ??  If they were in, why would they continue making failed attempts?

When I checked to see which files had been accessed in the last day, that was about 30GB of files in less than an hour, so I'd guess they were scanning to see if there was anything fascinating on there :P

The big issue though: now that the OS is still there, I'm wondering if I can risk NOT reinstalling?  I haven't really given the whole antivirus thing much thought.  (There's a reason I use Ubuntu :D .)  I've used ClamAV in a half-assed sort of way.  I'm not sure what a sensible procedure would be at this point.

---

### Post by koenn on 2009-07-29
> **quixote said:**
> 
The big issue though: now that the OS is still there, I'm wondering if I can risk NOT reinstalling?  I haven't really given the whole antivirus thing much thought.  (There's a reason I use Ubuntu :D .)  I've used ClamAV in a half-assed sort of way.  I'm not sure what a sensible procedure would be at this point.
no, you can't risk that.
you are positive that someone was able to tamper with your system, and you have no way of knowing what they did to it.
Viruses aren't the issues, hidden modifications to the system (backdoors, trojans, rootkits, ...) are.

---

### Post by igorzwx on 2009-07-29
It seems that it was a quite ordinary bot attack.
Not seldom, if to believe The Register, Linux servers are integrated
to botnets.
If a bot is inside, it might be intersting to see what it is doing.

---

### Post by bodhi.zazen on 2009-07-29
If you think your OS was cracked, re-install =)

---

### Post by quixote on 2009-07-29
Yeah.  I was afraid that would be the answer.  I'm off to start reinstalling now.  At least I didn't lose any data, and all my important passwords are already changed.  So I got off pretty easy.

Thanks to all for your excellent help!

---

### Post by igorzwx on 2009-07-29
a nice LiveCD
[http://frenzy.org.ua/eng/](http://frenzy.org.ua/eng/)

Look what is inside and google each security app

---

### Post by igorzwx on 2009-07-29
[http://www.theregister.co.uk/2009/07/29/kaminsky_hacked/](http://www.theregister.co.uk/2009/07/29/kaminsky_hacked/)
QUOTE:
Security researchers gathered at Black Hat have revived rumors that there's a zero-day vulnerability that's being exploited in SSH applications, but so far, there is no evidence to support the suspicions

---

### Post by quixote on 2009-07-29
Thanks for the links, igorwx.  The frenzy CD (good name for it!) looks like it would be a useful thing to learn my way around.  I'll be following the news about ssh vulnerabilities with more interest these days.

---

### Post by Dave_Connor on 2009-07-30
If your looking for security aside from key auth over password auth, there is Backtrack which is a good live cd distro filled with hundreds of security apps you can use to test the security of your system. They switch to Ubuntu resporties and dpkg with apt-get for package management to.

---

### Post by dragos2 on 2009-07-30
> **igorzwx said:**
> [http://www.theregister.co.uk/2009/07/29/kaminsky_hacked/](http://www.theregister.co.uk/2009/07/29/kaminsky_hacked/)
QUOTE:
Security researchers gathered at Black Hat have revived rumors that there's a zero-day vulnerability that's being exploited in SSH applications, but so far, there is no evidence to support the suspicions

+1

One of my secured patched to day servers were exploited an only ssh was opened.
So I suspect a ssh 0-day in the wild too.

Coincidence or not it was from China too :))

---

### Post by Sepanderi on 2009-07-30
> **jerome1232 said:**
> A server running on port 22 will get hit all day everyday...

This is true, hence moving your SSH server to some other port decreases the number of login attempts massively. I also used to get hundreds or thousands of login attempts a day (most of them from China), so I started using sshblack, but really the fastest and easiest cure is to use a non-standard port.

---

### Post by igorzwx on 2009-07-30
Of, course, BackTrack
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)
BackTrack is the most top rated linux live distribution focused on penetration testing. With no installation whatsoever, the analysis platform is started directly from the CD-Rom and is fully accessible within minutes. 

But Frenzy is so nice :)

The latest news are here:
[http://www.theregister.co.uk/security/](http://www.theregister.co.uk/security/)

---

### Post by igorzwx on 2009-07-30
old Unix hackers tend to use this method to restrict access to SSH server
[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

### Post by jerome1232 on 2009-07-30
> **Sepanderi said:**
> This is true, hence moving your SSH server to some other port decreases the number of login attempts massively. I also used to get hundreds or thousands of login attempts a day (most of them from China), so I started using sshblack, but really the fastest and easiest cure is to use a non-standard port.

Meh they are just bots using dictionary attacks. If someone was actually trying to get in they would just port scan you. All moving the port does is clean up your logs.

I mean seriously I saw one bot was going through the alphabet trying users (A B C etc..). I'll bet the passwords it was trying were the same as the user names it was trying.

---

### Post by igorzwx on 2009-07-30
[LIST=1]
[*]**[What Every Web Programmer Needs To Know About *Security* - *Google* [B]...**]("http://code.google.com/edu/submissions/daswani/index.html")[/B]

Skip to page content Skip to main navigation. *Google* Code **...** the book "*Foundations of Security*: What Every Programmer Needs To Know" for use by instructors **...**
code.**google**.com/edu/submissions/daswani/index.html - [Cached]("http://209.85.129.132/search?q=cache:fZMvLghQEjEJ:code.google.com/edu/submissions/daswani/index.html+Foundations+of+Security+Google&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:code.google.com/edu/submissions/daswani/index.html")
[*]**[Web *Security* - *Google* Code University - *Google* Code]("http://code.google.com/edu/security/index.html")**

Skip to page content Skip to main navigation. *Google* Code **...** of the chapters in the book "*Foundations of Security*: What Every Programmer Needs To Know" for **...**
code.**google**.com/edu/**security**/index.html - [Cached]("http://209.85.129.132/search?q=cache:TZc0SXhpBeEJ:code.google.com/edu/security/index.html+Foundations+of+Security+Google&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:code.google.com/edu/security/index.html")
[*]**[APRESS.COM : *Foundations of Security*: What Every Programmer Needs [B]...**]("http://www.apress.com/book/view/9781590597842")[/B]

Click the *Google* Preview image to preview this book! If you wish to preview other books, check this listing. Book Details. *Foundations of Security*: What **...**
[www.apress.com/book/view/9781590597842](www.apress.com/book/view/9781590597842) - [Cached]("http://209.85.129.132/search?q=cache:WG9AlVtZVFEJ:www.apress.com/book/view/9781590597842+Foundations+of+Security+Google&cd=3&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.apress.com/book/view/9781590597842")
[/LIST]

---

### Post by bodhi.zazen on 2009-07-30
> **jerome1232 said:**
> Meh they are just bots using dictionary attacks. If someone was actually trying to get in they would just port scan you. All moving the port does is clean up your logs.

I mean seriously I saw one bot was going through the alphabet trying users (A B C etc..). I'll bet the passwords it was trying were the same as the user names it was trying.

I agree but changing the default port gets rid of 90 % + of the script kiddies as they are called and performing a port scan is taking the game to another level, and port scanning can get very sophisticated.

A well configured set of iptables will help a ton with port scans.

---

### Post by quixote on 2009-07-30
Thanks again to all for the further ideas. I'm getting a whole toolchest for future reference.  First (and easiest)  I'll definitely be using a nonstandard ssh port.  A good idea, even if it's not perfect.  After all, in this game it's not so much a matter of being invulnerable as of being less vulnerable than the next guy. :?

---

### Post by bodhi.zazen on 2009-07-31
> **quixote said:**
> Thanks again to all for the further ideas. I'm getting a whole toolchest for future reference.  First (and easiest)  I'll definitely be using a nonstandard ssh port.  A good idea, even if it's not perfect.  After all, in this game it's not so much a matter of being invulnerable as of being less vulnerable than the next guy. :?

Security is like an onion - It has layers and they stink :twisted:

---

### Post by kevdog on 2009-07-31
Why does security stink?  Couldn't it be related to petals on a rose instead?

---

### Post by koenn on 2009-07-31
if it stinks, you're doing it wrong ...

---


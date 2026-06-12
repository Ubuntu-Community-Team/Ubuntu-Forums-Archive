---
title: "Security Risk having Windows and Ubuntu"
date: 2007-11-13
forum: Server Platforms
---

### Post by teabuntu on 2007-11-13

Hi,
I'm totally new with things Ubuntu and Linux, and I was wondering if people could pitch in and share their ideas about security concerning Windows and Ubuntu working toegether:

If there is a security risk involved on a computer having both Windows XP Home Edition SP2 and Ubuntu Gutsy Gibbon (both OS installed on a single disk OR having Windows installed on laptop hard disk--I have a laptop--and then installing Ubuntu on a USB stick, how might security be breached?  

Put in another way: if a virus, spyware or other nasties come in while using Ubuntu and browsing the internet, would they not go straight to the Windows OS and attack it there (since most viruses etc are designed to attack Microsoft OS)?  I have a security software that works with Windows but would that be "working" if I'm using Ubuntu?  Thus, even with the security software in place for Windows, the viruses etc that came in while using Ubuntu would not be stopped by the security software installed in Windows?

This might be a weird question, but how might viruses etc that comes in through using Ubuntu "migrate" across th Windows, or can it?

Thank you for any advice or input.

---

### Post by HermanAB on 2007-11-13
You'll have to go to great lengths to make a virus enter via Linux.  See this: [http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

However, if you are hosting a mail server then you should run SpamAssassin and ClamAV to ensure that your mail server doesn't pass on garbage to the rest of the world.

Provided that you use LONG passwords of at least 9 characters for all accounts and you will be OK.  I use 16 character semi-pronounceable passwords.  Most hack attacks are due to some wise guy using a 4 character password.

So, relax and enjoy Linux.  

Cheers,

Herman

---

### Post by teabuntu on 2007-11-13
Hi,
Thanks for your post.  I was looking for something mroe concrete so that I can learn more about security related to having Windows and Linux OS together.  Thanks.

---

### Post by HermanAB on 2007-11-13
Well, what are you after?  

There are three main reasons why you need not worry much:
a. Linux has security in depth: netfilter (iptables), tcpwrappers, stack protection, user privilege separation, daemons run as unprivileged users.
b. A Windows virus dropped onto your HDD by a browser or email client, won't execute, since Linux doesn't run Windows files.
c. Linux viruses are exceedingly uncommon.  There are none at the moment.

Windows has hundreds of thousands of viruses, but they don't run on Linux.  You can read email, browse the web and click on anything with wild abandon, the way the internet gods intended.

If you want to bone up on security, go to tldp.org and read the various firewall and routing howtos.

In the mean time, relax and enjoy it.

Cheers,

Herman

---

### Post by teabuntu on 2007-11-13
[QUOTE=HermanAB;3761583]Well, what are you after?  

Well, I thought I made myself clear as to what I'm after in my original post..... anyway, the information I'm looking for is about security when a condition is such that both Windows and Linux (Ubuntu in this case) is placed together, either on a single hard disk or seperate disks as I mention above.  Thanks.

---

### Post by MJN on 2007-11-13
The risk is as per point B made by HermanAB:

>  b. A Windows virus dropped onto your HDD by a browser or email client, won't execute, since Linux doesn't run Windows files.If that virus was saved on your HDD where you could subsequently access it from Windows (when it's booted) then that's your input path to potentially compromise Windows. This would require the file to be executed - either manually or automatically (particularly if that file has overwritten an existing 'innocent' executable).

The risk is only present if you mount your Windows partitions under Linux - doing so is quite common but you just have to be aware of the risk of infection and follow good practice with regards to defending against viruses, e.g. not downloading from untrusted sites, ensuring you have sufficient virus detection on Windows (when running), and even adding a supplementary layer of protection of running an on-access virus scanner under Linux (mainly to protect the Windows installation as discussed).

Similarly, if you are mounting your Linux partitions under Windows then again these could be a source of infection. A file on the Linux HDD/partition might well be benign whilst running Linux, but executed within Windows it could be a real risk.

Mathew

---

### Post by otake-tux on 2007-11-13
mjn is correct.   one thing you also have to take into account is that viruses aren't the only threats out there and running linux does not automatically make you safe.  good practices and proper authentication , etc. on both windows and linux are the only ways to be relatively secure.

---

### Post by HermanAB on 2007-11-13
On Linux, the biggest threat is bad quality passwords.  On Windows, bad passwords are also a threat, but there are a multitude of other worse things that don't even get to a password challenge!

---

### Post by teabuntu on 2007-11-13
Hi,
Thank you guys for your posts.  I guess what I was looking for was Windows targeted viruses etc that comes in while using Linux.  I know that in Linux, it would not be a threat, but I wanted to know if such viruses coming in through Linux can affect when you switch over to Windows, and whether the security risk changes if you have Windows and Linux on a seperate disk (ie: Windows on main ahrd drive in my laptop, then Linux (Ubuntu) on a USB stick for example).  I think the answers posted above answered part of my question.  Thanks.

---

### Post by HermanAB on 2007-11-13
In general, viruses will not come in through Linux, because Linux doesn't auto-execute stuff in browsers and email clients.  

The whole Unix environment is far more security conscious than the Windows environment.  Unix clients are not allowed to automatically alter settings in servers the way Windows systems can do and Unix servers do not expect their clients to be well behaved the way Windows servers do.

Even old server systems such as Windows 2003 still have gaping security holes that you can drive a 100 ton truck through.  Microsoft developers just do not grok security at all.

Cheers,

Herman

---

### Post by teabuntu on 2007-11-14
Hi Herman,
Thanks for your post.  So to understand you correctly, you're saying that ANY virus or other kinds of malaware etc, whether designed to attack Windows OR Linux will not get through a Linux OS such as Ubuntu?  Thank you.

---

### Post by HermanAB on 2007-11-14
I fix one or two hacked servers per year. So far, these were all public web servers and the hackers all gained a foothold thanks to a stupid password of 4 to 6 characters.  

The exploits were related to Apache (PHP), SSH and FTP.  All of these exploits were automated attacks, which lead to the machines sending out spam and hosting the same attacks against other machines.

Cheers,

H.

---

### Post by teabuntu on 2007-11-14
Thanks.  I read somewhere that FAT32 is an issue when it comes to security risk with having Widnows and Linux installed together.  Would anyone like to comment on this or provide me with more info regarding this or any others pertaining to dual booting?  Thank you.

---

### Post by HermanAB on 2007-11-14
Well, FAT32 has a number of issues.  Firstly, it is not a robust file system and it is guaranteed to screw up sooner rather than later.  It also doesn't have meta information to control user access.  If you have to be Windoze compatible, use NTFS or Ext3.  Linux has NTFS drivers and Windoze has Ext3 drivers available, so there is no good reason to use FAT.

Cheers,

H.

---


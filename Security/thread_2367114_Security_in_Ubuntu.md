---
title: "Security in Ubuntu"
date: 2017-07-26
forum: Security
---

### Post by sawsrinath on 2017-07-26
Hello,
         I have installed ubuntu 17.04 on my laptop. I'm web designer, So I will be doing online transactions heavily. I wan't to know is it safe to use ubuntu without a antivirus? Any help would be greatly appreciated. Thanks.

---

### Post by Autodave on 2017-07-26
Make sure that your system is up to date. Did you enable automatic updating? If not, do it now. If you want to make sure that your system is up to date, in a termional run:

sudo apt-get update
sudo apt-get upgrade

That will make sure that it is up to date.

As far as I kn ow, there is no antivirus for Ubuntu. The only antivirus programs really only scan for Windows viruses so that you don't pass them on to your Windows user friends.

You will probably get a few more in depth answers than mine, but rest easy. :-)

---

### Post by slickymaster on 2017-07-26
*Thread moved to **Security**.*

---

### Post by mastablasta on 2017-07-26
you can get an antivirus, but you really do not need one. 

you can also install gufw firewall if you wish. it is not necessary though as all ports are closed by default.

you cna harden it a lot but for your use it is probably not necessary.

just use some "common sense" when browsing the web.

---

### Post by sp40140 on 2017-07-26
For typical user commonsense goes a long way for securing the computer.
However, since you will be doing payments on the machine, I suggest you lock it down very heavily. Meaning enabling firewall, disabling all of non essential services and on and on. 
What you are talking about is sensitive production environment. You need to know (and if you don't, learn very fast) the System Admin side of Linux server management. 
As you might know already it is a full time dedicated position in it's own right.
Also, I am not sure what your strategy for backup/DR is, to me laptop doesn't fit well with this.
Antivirus is not needed but you do need other things.

---

### Post by SeijiSensei on 2017-07-26
What do you mean by "doing online transactions?"  If you mean connecting to secure sites with HTTPS then any browser on any platform will do what you want.  If you're talking about designing a server that will accept secure payments, that raises entirely different issues.

---

### Post by sawsrinath on 2017-07-27
@Autodave[COLOR=#000000] [/COLOR]@mastablasta Thanks. 
@sp40140 @ SeijiSensei I will be adding funds to my credit card, buying things on ebay etc. Also I will be doing web designs (wordpress non https) etc. I also share my projects via torrents. I'm afraid that I will get viruses via torrents. Thanks

---

### Post by vasa1 on 2017-07-27
While you're free to ask questions, have you read [https://ubuntuforums.org/showthread.php?t=510812?](https://ubuntuforums.org/showthread.php?t=510812?) Maybe you'll fewer doubts after reading that?

---

### Post by sgian on 2017-07-29
I would be afraid to use Windows for finances and so I only use linux for that.

Nothing is impossible.  However it is harder to make malware for linux due to frequent updates for known vulnerabilities and due to the root privileges use, and it is not worthwhile for the common hacker to target linux when we are such a small percentage of the desktop users.  When most of the world uses Windows and when Windows is easier to hack, why bother with linux desktop users?  Linux servers with older software and a tendency to avoid updates for fear of breaking something are more vulnerable.  

And even when someone with the skills decides to go after linux, the malware quickly becomes outdated for Linux desktop users.  For example, Wikileaks just released the CIA hack for linux called Aeris.  [https://fossbytes.com/macos-linux-hacking-tools-cia-vault-7-wikileaks/](https://fossbytes.com/macos-linux-hacking-tools-cia-vault-7-wikileaks/)  If you look at what is affected, Ubuntu is not even mentioned but Debian (which Ubuntu is based on) is mentioned.  Even in that case, it is Debian 7 which is affected and that is a version of Debian so old that support will be discontinued next year.  Debian 8 and the current Debian 9 are not even affected.  However, I am sure that governments in Russia, the US, China, etc are working on linux exploits for current distros and if those get leaked too then there might be a problem until the open source community patches the vulnerabilities once known.

As I understand it, the most likely vector of attack through the internet for a linux desktop with an up to date system is through javascript and flash on your browser.  Unlike Windows, you are not likely to face a system wide problem because you need root privileges for installing stuff and because most of it is written for Windows and not Linux.  So deleting your history to include cookies, cache, saved web pages, etc will take care of the problem in probably any case.  However, whatever you did while the browser was infected may be compromised.  So that is why some people use programs like ad-block, firejail, noscript, etc.  What I do is to use two browsers; Chromium for just finances and Firefox for general browsing.

So, things to do or not do:
On the system you use for finances, do not use ssh, Oracle java, samba, wine, or ppa's.  Keep it basic, keep it updated at leastly weekly if not more often, and enable the firewall by the terminal command 
> sudo ufw enable
or as suggested use gufw.  The browser you use for banking, don't use for anything else.  If you do this, I really doubt you will have a problem.

However on a computer you might want to use torrents, play games, and use everyday, that might not be practical.  It certainly isn't for me.  So some options might be to have the everyday use computer set up how you want, and then for finances have another partition to boot into.  Or you might use a virtual machine with a separate OS for playing on, and have the bare metal installation hardened.  Or vice versa.  Or you could use firejail to sandbox your torrent program and general use browser [https://firejail.wordpress.com/](https://firejail.wordpress.com/)

As for an antivirus, I understand that you coming from Windows might be afraid of not using an antivirus program.  There is a GUI antivirus called clamtk.  Just don't enable PUA (potentially unwanted applications) on the scanner because it might cause problems, and scan away until you feel more comfortable with linux.

---

### Post by TheFu on 2017-07-30
> **sawsrinath said:**
> Hello,
         I have installed ubuntu 17.04 on my laptop. I'm web designer, So I will be doing online transactions heavily. I wan't to know is it safe to use ubuntu without a antivirus? Any help would be greatly appreciated. Thanks.

At the top of this forum are "sticky" threads. You might find them helpful.

---

### Post by ClickXT on 2017-08-02
Safer than any Microsoft option with an additional purchased security suite.....imo.

---


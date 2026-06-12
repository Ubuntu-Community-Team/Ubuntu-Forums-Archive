---
title: "Tips Regarding Virus"
date: 2010-12-02
forum: Security
---

### Post by xavier666 on 2010-12-02
I'm thinking of not installing an anti-virus after seeing all the security measures of Linux

However, just in case, what should I keep in mind when handling files from unknown origins?

I understood that I should not enter my password for an unknown application.
Is there anything else?

[Using Ubuntu 10.10]

---

### Post by wilee-nilee on 2010-12-02
I would say reading the stickies in this section might help.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by Verbeck on 2010-12-02
don't use wine :-\"

---

### Post by hawthornso23 on 2010-12-02
1. Stick to software you can install from the repositaries, wherever possible.
2. Don't make anything executable that shouldn't be.
3. Use sudo sparingly.

You should be fine. The most common way people get into trouble is by doing stupid things which mess up their own systems. Viruses are seldom if ever an issue. The best security step you can take is to become better informed so you are less likely to do anything foolish.

---

### Post by Sef on 2010-12-02
> I'm thinking of not installing an anti-virus after seeing all the security measures of Linux.

The only time anti-virus is recommended in Linux is if you have an email client, so you do not infect your friends who have Windows computers. Windows viruses cannot infect a Linux computer, but they can ride on top and attach to emails.

---

### Post by Rubi1200 on 2010-12-02
+1 to all the suggestions previously posted.

And, I have one more: use strong passwords; anything from 9 characters in length and upwards.

---

### Post by uRock on 2010-12-02
As long as you do not do the command **chmod +x <NameOfFile>**, which will make a file executable, then you'll be fine as far as Ubuntu goes. As others have said, anti-virus is for protecting files that may be shared with Windows systems.:D

Edit: Moved thread to the Security Discussions sub-forum.

---

### Post by conradin on 2010-12-02
encrypt stuff.
get an antivirus software like clamav just because,
monitor your logs, 
install a firewall / check up on it at a site like 
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
beware of tools like snort,
beware torrenting or offering any service or fil-eshare will make you a target.

---

### Post by HermanAB on 2010-12-03
Bah, note that chrootkit and rkhunter don't actually work.  You don't need 3rd party crapware to protect a Linux system.

Relax and enjoy your Ubuntu machine.

---

### Post by xavier666 on 2010-12-03
Thanks for all the reply, guys!! =D>
I should have specified my setup.
I'm a single Ubuntu user but have XP as well with 2 accounts.
I'm connected to the net by an ethernet based cable. Hence, i'm also connected to people through LAN. So, I was thinking whether I could be subjected to attacks through LAN 

>don't use wine
lol :)

>Use sudo sparingly
I'm thinking that if i use sudo on apps provided by ubuntu itself then, it won't be much of a problem

>The only time anti-virus is recommended in Linux is if you have an email client, so you do not infect your friends who have Windows computers
If i'm using Gmail ONLY, I think I should be safe

>beware of tools like snort
WHY?? :confused:
I thought it was a good tool

>beware torrenting or offering any service or fil-eshare will make you a target
I can't use torrent, rapidshare or any other site!

---

### Post by OpSecShellshock on 2010-12-03
Snort is an excellent tool for people who have experience using it in a professional capacity or lots of experience using it at home. For people who don't know what to pay attention to vs. what to ignore or tune out it usually just scares them.

---

### Post by uRock on 2010-12-03
> **HermanAB said:**
> Bah, note that chrootkit and rkhunter don't actually work.  You don't need 3rd party crapware to protect a Linux system.

Relax and enjoy your Ubuntu machine.
+1 I don't think I have ever seen anyone with a actual root kit. Just a bunch of false positives.

The only security tool I use is the UFW firewall and the only time I use it is when I am using a public wireless network that allows port scans.
> **OpSecShellshock said:**
> Snort is an excellent tool for people  who have experience using it in a professional capacity or lots of  experience using it at home. For people who don't know what to pay  attention to vs. what to ignore or tune out it usually just scares  them.
Snort is one of my favorite tools to play with, but it is useless for someone that doesn't know what they are looking at.

---

### Post by lisati on 2010-12-03
+1 to the earlier suggestions, to which I add, "Be smart with what you allow on your computer and what you open."

---


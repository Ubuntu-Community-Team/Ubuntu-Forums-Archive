---
title: "Is ubuntu secure enough to be on a production machine? (new to linux)"
date: 2011-10-14
forum: Security
---

### Post by fishfisting on 2011-10-14
I have been looking at Linux for some time now, however the system itself is something I have little understanding off.

That has prevented me from making a switch. I don't think that my close to zero Linux understanding will be enough to keep my computer safe. 

The question(s) I have is: is unbuntu hard to learn (I'm talking about the security aspect and not about starting the browser and edit some documents)? What are the general ways of locking-down a Linux installation and to prevent me from become the victim of hackers? Are the security related settings/options well documented? Also when/if installing Ubuntu Linux will there be an option opt-out stuff I probably don't need or is the approach more that everything gets installed and remove stuff from there?

Thanks for your time.

---

### Post by tubbygweilo on 2011-10-14
May I suggest if you have not yet glanced at the [Ubuntu Security sticky]("http://ubuntuforums.org/showthread.php?t=510812") attached to this forum then a browse may well be in order.

Please return with more questions if you feel the need.

---

### Post by rg4w on 2011-10-14
**is unbuntu hard to learn (I'm talking about the security aspect and not about starting the browser and edit some documents)?**
Easier than learning to secure Windows, IMO.

**What are the general ways of locking-down a Linux installation and to prevent me from become the victim of hackers?**
Ubuntu ships with no open ports, and most viruses are written for Win APIs.  This combination helps make Ubuntu inherently more secure from the moment you boot.

**Are the security related settings/options well documented?**
See the previous poster's link (really good stuff there).

**Also when/if installing Ubuntu Linux will there be an option opt-out stuff I probably don't need or is the approach more that everything gets installed and remove stuff from there?**
The bloatware commonly associated with commercial OS distributions is pretty much absent from Ubuntu and other Linux distros.

AFAIK the only such thing in Ubuntu might be the Ubuntu One cloud storage and maybe the chat tools that come with it, and both of those are opt-in.

---

### Post by bodhi.zazen on 2011-10-14
> **fishfisting said:**
> I have been looking at Linux for some time now, however the system itself is something I have little understanding off.

That has prevented me from making a switch. I don't think that my close to zero Linux understanding will be enough to keep my computer safe. 

The question(s) I have is: is unbuntu hard to learn (I'm talking about the security aspect and not about starting the browser and edit some documents)? What are the general ways of locking-down a Linux installation and to prevent me from become the victim of hackers? Are the security related settings/options well documented? Also when/if installing Ubuntu Linux will there be an option opt-out stuff I probably don't need or is the approach more that everything gets installed and remove stuff from there?

Thanks for your time.

Linux (and Ubuntu) are quite secure out of the box. Most of the cracks we see on these forums are either VNC or SSH, with a weak password.

If you install a server or server application (apache, mysql, php, ssh, etc) you should look at hardening it as needed.

---

### Post by Dangertux on 2011-10-15
> **bodhi.zazen said:**
> Linux (and Ubuntu) are quite secure out of the box. Most of the cracks we see on these forums are either VNC or SSH, with a weak password.

If you install a server or server application (apache, mysql, php, ssh, etc) you should look at hardening it as needed.

Absolutely correct the one thing that I would add here is in terms of dynamic web applications if you're hosting any. Please please please audit the code properly.

If I were to make a bet  I would say the most exploited vulnerability next to weak credentials would be poorly coded web applications (SQL injection, inclusion etc)

Note there are working public exploits for some services in repos, so make sure you do your research and stay updated.

Also to answer another question the OP asked, you will not have to opt out of anything. With Ubuntu server or minimal , you're not going to get much of anything but a base system. Anything you get will be added by you.

---

### Post by CharlesA on 2011-10-15
> **Dangertux said:**
> Absolutely correct the one thing that I would add here is in terms of dynamic web applications if you're hosting any. Please please please audit the code properly.

If I were to make a bet  I would say the most exploited vulnerability next to weak credentials would be poorly coded web applications (SQL injection, inclusion etc)

Note there are working public exploits for some services in repos, so make sure you do your research and stay updated.

Also to answer another question the OP asked, you will not have to opt out of anything. With Ubuntu server or minimal , you're not going to get much of anything but a base system. Anything you get will be added by you.
Huge +1 to that. SQL injection can be prevented by sanitizing any input that gets written to the db, right?

---

### Post by Slim Odds on 2011-10-15
> **CharlesA said:**
> Huge +1 to that. SQL injection can be prevented by sanitizing any input that gets written to the db, right?

Somewhat... SQL Injections that are security related are more about getting system commands to the system, bypassing the normal protections that already exist.

---

### Post by Dangertux on 2011-10-15
> **CharlesA said:**
> Huge +1 to that. SQL injection can be prevented by sanitizing any input that gets written to the db, right?


Not just written, but queries made to it as well , you want to make sure that whatever your web app is feeding your database is good for it.

Like the poster above me stated SQL injection CAN be used to pass system commands on a VERY poorly configured database but it's more often used to dump credentials and other information from the web app's database it self. 

However, web apps are not the only thing that can be vulnerable to SQL injection, for instance ProFTP in some configurations can be vulnerable to SQL injection as well.

---

### Post by CharlesA on 2011-10-15
> **Slim Odds said:**
> Somewhat... SQL Injections that are security related are more about getting system commands to the system, bypassing the normal protections that already exist.

Ah, gotcha.

> **Dangertux said:**
> Not just written, but queries made to it as well , you want to make sure that whatever your web app is feeding your database is good for it.

Like the poster above me stated SQL injection CAN be used to pass system commands on a VERY poorly configured database but it's more often used to dump credentials and other information from the web app's database it self. 

However, web apps are not the only thing that can be vulnerable to SQL injection, for instance ProFTP in some configurations can be vulnerable to SQL injection as well.

Thanks for that! That's quite interesting to know. I guess I'll have to read up on SQL injection some more. :)

---

### Post by fishfisting on 2011-10-15
Thanks for all the input it was very helpful. The sticky was (is) especially interesting. 

It seems like Unbuntu has a lot of options that I will have to dig deeper in before deciding if to make a switch. Again, thanks. :p

---

### Post by SeijiSensei on 2011-10-15
You asked this question in the server forum, though it sounds more like you're asking about securing a desktop machine.  If you're running a desktop Ubuntu installation behind a firewall device like a wifi router, there's literally nothing you need to do to secure it out-of-the-box.

Since you posted in the server forum, people were commenting about security threats that running web sites, mail servers, and the like might face.  In those cases the server must be open directly to the Internet which raises the level of threat considerably. However the commonly-used applications like the Apache web server and the Postfix mail server have been in widespread use for years so that most of their security problems have been identified and fixed.  Once in a while a [new threat]("http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-3192") pops up, but fixes for these bugs are usually released in a few days at most.

Also, attacks like SQL injection do not depend on the server platform but the security of the code that powers a web application.  A poorly-written PHP application can be just as insecure on a Windows server as on a server running Linux.

In 2008, no less an authority than Microsoft's own Steve Ballmer [stated]("http://www.pcworld.com/businesscenter/article/151568/ballmer_still_searching_for_an_answer_to_google.html") that the majority of servers were running Linux.  I suspect the figures are even more imbalanced for Internet-facing servers.

---

### Post by Algus on 2011-10-15
If you're looking for something highly customizable that is only running the stuff you want it to run, Ubuntu might not be your best choice for a Linux distro.

As others have said, Ubuntu, and Linux in general, are very secure both because of the way the work and because Linux largely isn't targeted by troublemakers.  So if all you're worried about is security and ease of use, Ubuntu is great.  

Otherwise you might want to try a more lightweight distro like Slackware or something.  Some Linux distros are a real pain because you have to do a lot of it yourself (like compiling programs, etc.) but if you have the technical expertise or interest, you'll get better (and probably more secure) results than a more user-friendly distro like Ubuntu.

---

### Post by CharlesA on 2011-10-15
You could always run Ubuntu Server or install using the minimal iso and only install what you want.

---

### Post by SeijiSensei on 2011-10-15
> **Algus said:**
> Linux largely isn't targeted by troublemakers

Internet-facing Linux servers and the applications they run *are* targeted though, just by a different type of trouble maker than people trying to log your keystrokes or turn your computer into a spambot.

---

### Post by Jonathan L on 2011-10-17
> **fishfisting said:**
> I have been looking at Linux for some time now, however the system itself is something I have little understanding off.

That has prevented me from making a switch. I don't think that my close to zero Linux understanding will be enough to keep my computer safe. 

The question(s) I have is: is unbuntu hard to learn (I'm talking about the security aspect and not about starting the browser and edit some documents)? What are the general ways of locking-down a Linux installation and to prevent me from become the victim of hackers? Are the security related settings/options well documented? Also when/if installing Ubuntu Linux will there be an option opt-out stuff I probably don't need or is the approach more that everything gets installed and remove stuff from there?

Thanks for your time.

Hi Fish

My answer would be Yes, certainly.

In general you are going to be more secure with "tried and trusted" things than with "new and improved" things, because the new things have new bugs.  For this reason, if you use something like the long-term support releases of Ubuntu, you have a better chance of staying secure easily.

If you're speaking about servers, you're much more likely to be in good shape with a non-GUI system, as the commands and configurations are almost always in text files, which means you can document and audit so much more easily.  Additionally you can use features like "immutabile" files and having most of your system largely read-only; all depending on what you're doing, of course.  I've run systems without disks which boot off CD-ROMs, which though in princiiple could be hacked, the problem can't survive a reboot as there's nowhere to write anything.

But I think the biggest point is that Ubuntu (and certainly some other distributions) are well run and well organised.  Which means, for example, unless you explicitely say otherwise, your system won't install software which hasn't been checked by Canonical.  And indeed most of the professional users are really clear about the need for security, sometimes at the cost of usability, which informs the discussions pretty well.  For example, people always speak separately about web servers, mail servers, DNS servers, file servers and so on ... knowing that each of those has their own risks and requirements.

And lastly, of course, if it's open source *you* are the final authority about what's safe: you can always find out what program X does in circumstance Y by looking yourself or getting someone with more experience to look.

Just my experiences, but they've been very good indeed.  

Kind regards,
Jonathan.

---


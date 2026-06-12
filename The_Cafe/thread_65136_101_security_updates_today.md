---
title: "101 security updates today"
date: 2005-09-13
forum: The Cafe
---

### Post by mtron on 2005-09-13
just turned on the update manager today, and it seems that there are 101 available updates for hoary (totalling ca 100 MB) coming in over security.ubuntu.com mainly affecting the xserver.

This is the security announcement: [http://lists.ubuntu.com/archives/ubuntu-security-announce/2005-September/000202.html](http://lists.ubuntu.com/archives/ubuntu-security-announce/2005-September/000202.html)

Just in case sb is wondering...

---

### Post by GeneralZod on 2005-09-13
Hopefully the modularisation of X will prevent this kind of thing.

I remember a post on slashdot during one of Microsoft's "Patch Tuesday"s where in response to a 15MB patch from MS, some idiot gloated "As a Linux user, I'm glad I don't have to put up with this!".  It really put just how bad Linux's "patching" system is into perspective, *especially* for a dial-up user which, we must remember, is still the most prevalent form of internet connectivity in developing nations.  There's no way my mum would have been able to download this much, and she would still be vulnerable.  Kernel & KDE "patches" are another huge source of bandwidth drain.

Does anyone know if Debian is going to be adopting a "binary-diff"-style manner of patching?  I gather SUSE 9.3 either has it working or is working on it.  If not, I'll go file a bug report :)

---

### Post by endy on 2005-09-13
It is a local exploit only so most desktop users should be ok even if they don't update. I  agree with you though :)

---

### Post by GeneralZod on 2005-09-13
[QUOTE=endy]It is a local exploit only so most desktop users should be ok even if they don't update. I  agree with you though :)[/QUOTE]

It's actually rather more serious than that, I think: it should be noted that "local exploit" does not necessarily mean that some hostile party already has access to your machine.   For example, I see little in the report that suggests that, say, browsing with Firefox could not trigger this exploit if a webpage fed it a large pixmap; we then have the appalling situation in which someone's machine could be rooted simply by surfing the web, and the only fix is a 90+MB download .  Please do correct me if I'm wrong, though :)

---

### Post by Brunellus on 2005-09-13
Thanks for the heads-up--I read this before my update notifier popped up.  The home machine is busy apt-getting the necessary stuff now.

---

### Post by XDevHald on 2005-09-13
Thank you for the update as Martin Pitt missed the input on his post by mistake. --> [http://www.ubuntuforums.org/showthread.php?t=64867]("http://www.ubuntuforums.org/showthread.php?t=64867")

---

### Post by mtron on 2005-09-13
[QUOTE=Steve Myers]Thank you for the update as Martin Pitt missed the input on his post by mistake. --> [/QUOTE]

Interresting, but the email came to me ok (see link in first post), i thought the security mailing list is just "feeded" in this forum?
l

---

### Post by XDevHald on 2005-09-13
[QUOTE=mtron]Interresting, but the email came to me ok (see link in first post), i thought the security mailing list is just "feeded" in this forum?
l[/QUOTE]
 It is, but for some reason it didn't read the page script correctly when submitting it's self to this server.

---

### Post by Stormy Eyes on 2005-09-13
[QUOTE=GeneralZod]There's no way my mum would have been able to download this much, and she would still be vulnerable.  Kernel & KDE "patches" are another huge source of bandwidth drain.[/QUOTE]

If your mum is on dialup, then she should be reasonably safe. Crackers are more likely to go after hosts with persistent connections (aka broadband). If she's not running any unnecessary daemons, then she might not need to worry too much about security patches in Linux.

I used to run Gentoo on dialup. If you do your downloading overnight, and aren't paying by the minute or megabyte to connect, Linux on dialup isn't horrible.

---

### Post by GeneralZod on 2005-09-13
[QUOTE=Stormy Eyes]If your mum is on dialup, then she should be reasonably safe. Crackers are more likely to go after hosts with persistent connections (aka broadband). If she's not running any unnecessary daemons, then she might not need to worry too much about security patches in Linux.

I used to run Gentoo on dialup. If you do your downloading overnight, and aren't paying by the minute or megabyte to connect, Linux on dialup isn't horrible.[/QUOTE]

Fair enough; I still think that binary-diff style patches would be a far more elegant solution, though :)

---

### Post by endy on 2005-09-13
Just an update, according to frsirt.com the exploit is not remotely exploitable. Good news I suppose :)

[http://www.frsirt.com/english/advisories/2005/1711](http://www.frsirt.com/english/advisories/2005/1711)

---

### Post by zenwhen on 2005-09-13
[QUOTE=Stormy Eyes] If you do your downloading overnight, and aren't paying by the minute or megabyte to connect, Linux on dialup isn't horrible.[/QUOTE]

True enough. I was on dial up using Linux for over a year before last month. I made it by just fine by downloading nightly install images of Hoary while it was in development, and getting security fixes overnight afterward.

---

### Post by jdong on 2005-09-13
[QUOTE=GeneralZod]Hopefully the modularisation of X will prevent this kind of thing.

I remember a post on slashdot during one of Microsoft's "Patch Tuesday"s where in response to a 15MB patch from MS, some idiot gloated "As a Linux user, I'm glad I don't have to put up with this!".  It really put just how bad Linux's "patching" system is into perspective, *especially* for a dial-up user which, we must remember, is still the most prevalent form of internet connectivity in developing nations.  There's no way my mum would have been able to download this much, and she would still be vulnerable.  Kernel & KDE "patches" are another huge source of bandwidth drain.

Does anyone know if Debian is going to be adopting a "binary-diff"-style manner of patching?  I gather SUSE 9.3 either has it working or is working on it.  If not, I'll go file a bug report :)[/QUOTE]

SuSE's deltarpms work very beautifully... Firefox patches are usually <100KB long.

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=mtron]just turned on the update manager today, and it seems that there are 101 available updates for hoary (totalling ca 100 MB) coming in over security.ubuntu.com mainly affecting the xserver.
[/QUOTE]

Times like these are when my cable internet service pays for itself.

---

### Post by GreyFox503 on 2005-09-14
Are these actually *security* updates?  I don't know if they are, but remember that regular program updates happen that way too.

That's one important difference between updating Windows/Linux:  When you reinstall Windows, and you have to download 100 or 200 or whatever MB of "patches", they, by and large, really are security patches, not adding new features.  I can't count the number of times I've "prevented a remote attacker from gaining control of my computer." (paraphrased)

When you install Ubuntu, you're updating *all* your software to latest version, regardless of whether those new versions are mere security updates or true updates to the programs to change or add functionality.

---

### Post by GeneralZod on 2005-09-14
[QUOTE=GreyFox503]Are these actually *security* updates?  I don't know if they are, but remember that regular program updates happen that way too.

When you install Ubuntu, you're updating *all* your software to latest version, regardless of whether those new versions are mere security updates or true updates to the programs to change or add functionality.[/QUOTE]

Read the link in the first post; these are indeed security updates :)

Also, Ubuntu has a policy of freezing all packages a short while prior to release and not updating any of these packages except for security issues and serious bugs (is this correct...?), which is why backports was formed.  So probably the vast majority of updates you'd download are for security and contain no new features, although if you have backports enabled, you'll have a few new toys to look forward to :)

---

### Post by GreyFox503 on 2005-09-14
Hehe, whoops.  Ok, I'll admit it, I didn't even click the article link the first time.  But I can still comment, right?  Just like slashdot :)

---


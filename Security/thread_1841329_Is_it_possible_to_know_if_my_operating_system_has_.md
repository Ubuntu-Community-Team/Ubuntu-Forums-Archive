---
title: "Is it possible to know if my operating system has been affected by malware/virus etc?"
date: 2011-09-09
forum: Security
---

### Post by arroy_0209 on 2011-09-09
I am using ubuntu 10.04 LTS and I am trying to learn various things by experimenting.

One doubt I have is this: I have installed noscript and adblockplus and since then I am unable to access some vital parts of some webpages. One such caes is a blog (motls.blogspot.com) I like where at the end of the discussion, there is a link for quick discussions and earlier I used to just click it and one small window opened where I could write my opinion or read what others had commented. After installing these packages, it is not possible to click open the window, rather if I bring mouse there, a message like "javascript(0)" is shown at the bottom of the firefox screen. In case I allow temporarily everything in noscript option, then the page reloads and the link works properly. But this process of "temporarily allowing everything" in the page seems not the correct way. Can anybody please indicate how to solve this problem of selectively allowing a page to load java related items.

Second, it seems possible to get my browser and the operating system affected by unwanted objects like malware/virus etc when I am forced to temporarily allow everything to access my system. How do I know if any such incident had taken place? I do not have any antivirus like clamav etc. Can anybody please help me with these two issues?

---

### Post by haqking on 2011-09-09
> **arroy_0209 said:**
> I am using ubuntu 10.04 LTS and I am trying to learn various things by experimenting.

One doubt I have is this: I have installed noscript and adblockplus and since then I am unable to access some vital parts of some webpages. One such caes is a blog (motls.blogspot.com) I like where at the end of the discussion, there is a link for quick discussions and earlier I used to just click it and one small window opened where I could write my opinion or read what others had commented. After installing these packages, it is not possible to click open the window, rather if I bring mouse there, a message like "javascript(0)" is shown at the bottom of the firefox screen. In case I allow temporarily everything in noscript option, then the page reloads and the link works properly. But this process of "temporarily allowing everything" in the page seems not the correct way. Can anybody please indicate how to solve this problem of selectively allowing a page to load java related items.

Second, it seems possible to get my browser and the operating system affected by unwanted objects like malware/virus etc when I am forced to temporarily allow everything to access my system. How do I know if any such incident had taken place? I do not have any antivirus like clamav etc. Can anybody please help me with these two issues?


Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by SeijiSensei on 2011-09-09
I found noscript an annoying, and ultimately unnecessary, pain in the butt.  As I recall, you can whitelist sites fairly easily, so I'd suggest that route.  Simply add motls.blogspot.com to the whitelist.

The best defense against malware is you.  If you limit your travels to legitimate sites and don't download things that look dicey, you'll be fine.  Don't download random software from unknown sites; stick to the Ubuntu repositories or PPA's that have a good rep here.

---

### Post by Enigmapond on 2011-09-09
The OS can't be effected...true. But you CAN pick up something in the browser to effect browsing. Try clearing the cache of the browser and yes...just be careful where you go.

---

### Post by Johnny3 on 2011-10-05
Where is the cache for firefox? I have looked in a bunch of files and can't find it. Would I have to use sudo nautilus to delete them?
Thanks and God Bless Johnny3 65++

---

### Post by OpSecShellshock on 2011-10-05
> **Johnny3 said:**
> Where is the cache for firefox? I have looked in a bunch of files and can't find it. Would I have to use sudo nautilus to delete them?
Thanks and God Bless Johnny3 65++

Under Tools-->Clear Recent History one of the options will be to clear the cache.

---

### Post by Johnny3 on 2011-10-05
> **OpSecShellshock said:**
> Under Tools-->Clear Recent History one of the options will be to clear the cache.
Thanks. I thought you had to do it in the file system.
Thanks and God Bless Johnny3 65++
PS I can't mark this as solved. Do I have to be the one that started it to do that?

---

### Post by KIAaze on 2011-10-06
Yes, which is why you cannot do it.
Otherwise, in general, simply go to: "Thread tools->Mark this thread as solved" (on the top-right side of the initial post)

---


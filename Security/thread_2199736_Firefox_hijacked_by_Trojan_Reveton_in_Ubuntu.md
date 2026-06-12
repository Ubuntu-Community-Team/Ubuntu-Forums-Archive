---
title: "Firefox hijacked by Trojan Reveton in Ubuntu"
date: 2014-01-15
forum: Security
---

### Post by altdatamgt on 2014-01-15
Good afternoon. I am completely new to Ubuntu/Linux & know nothing of command lines, etc. 

 I was surfing in firefox this morning, and noticed a second firefox window was open. Upon viewing that window, I found a page stating my browser has been locked for illegal activities and I must pay a fine to unlock it. (screenshot) - I cannot close the tab or the program.

 I opened Opera and searched the url, and found Trojan Reveton as the source. I've only been able find windows solutions though, and nothing for ubuntu/linux.

 Does anyone know how to remove this trojan? Is my data compromised by something like this?

Thanks in advance for your help.

---

### Post by Bucky Ball on 2014-01-15
*Thread moved to **Security Discussions**.*

---

### Post by deadflowr on 2014-01-15
Delete the firefox profile and make a new one.
The profile is a folder in
/home/username/.mozilla/firefox.
Normally, if you only have one is says something like 
XXXXXXX.default.
You could also delete the firefox cache, to be safe.
That should be in
/home/username/.cache/mozilla/firefox

You can make a new profile or multiple profiles by running
```
firefox --Profilemanager
```
in a terminal.
Then a window will open up and you can create a new one.
I think though, that if you delete the default, a new one will generate without a need to make it.

Good Luck.
PS: None of this will require any elevated rights, so you don't need to run sudo or as root.

---

### Post by Bucky Ball on 2014-01-15
BTW, to kill the Firefox window you might try opening a terminal and:

sudo killall firefox

You probably don't need the sudo.

---

### Post by altdatamgt on 2014-01-15
Bucky Ball - The "killall firefox" command took care of my problem. I was able to reopen firefox and navigate anywhere I wanted to go. Thanks!!!

deadflowr - I had to re-read your solution a couple of times before I noticed the "dot" indicating the folder(s) are hidden! (as I mentioned - I'm a complete newbie to ubunto)  Even though the "killall" command resolved the problem, I followed your advice and I deleted the profile. However it has also deleted all my bookmarks. Are those bookmarks stored in a file somewhere for recovery or, will I just have to import them back into firefox from Opera?

Are you able to recommend any antivirus software to prevent anything like this from happening in the future? I was under the impression viruses like this were "non-issues" with Linux OS. That's not to say that the fix was certainly much easier than anything I've ever experienced in windows.

Thank you both for your quick response to my problem!

---

### Post by Dave_L on 2014-01-15
The bookmarks are probably gone, since they're stored in your Firefox profile.

This page may not be fully up to date, but it seems to have some good advice.  See the section on Firefox:
[https://www.cert.org/tech_tips/securing_browser/](https://www.cert.org/tech_tips/securing_browser/)

---

### Post by The Spectre on 2014-01-15
I noticed in your screenshot that you have a crap load of updates (467) that needed to be installed.

Which means you might be running an old version of Firefox not to mention security updates for Flash and the OS.

A fully patched and updated system might have prevented this from happening.

But you never know because even though Linux is very safe from Viruses a Browser Exploit is still a Browser Exploit regardless of what platform it is on.

---

### Post by sam_baker2 on 2014-01-15
Do you have any add-ons for security?

I have BetterPrivacy 1.68  and  NoScript 2.6.8.12

I also use flash block, but usualy more than not, have it turned off.
Flashblock 1.5.17

Not sure if these versions are the latest, but these are the ones that I have.


~Also, you may want to check into using a host file.
There are many on the internet. I download several and have a script
to combine them into one file.

 This is a windows site, but they have a host file and good
info about how to install it if you don't know how. ( It is just a text file )

[http://winhelp2002.mvps.org/](http://winhelp2002.mvps.org/)

---

### Post by Don_Stahl on 2014-01-15
Just a note -- any attacks which claim to have locked your OS or encrypted your drive and demand a ransom to unlock are virtually certain to be bogus if you're running Ubuntu, or any Linux, or Mac. The programs which actually lock or encrypt are *.exe executables and only run under Windows.

---


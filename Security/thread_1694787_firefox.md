---
title: "firefox"
date: 2011-02-24
forum: Security
---

### Post by gorxxx on 2011-02-24
Hey guys,

I got tired from getting viruses in windows. So i moved to ubuntu. Still one thing concerns me last virus i caught was firefox add-on type. Linux or not will i get infected if the virus targets browser not os. You kinda can install add-ons for firefox on linux and windows.

That pesky cr*p got auto installed in FF and was sniffing passwords. 
If  ff under linux can be infected migration to ubuntu wont solve my security problems.

Your thoughts are welcomed about it ..

P.S: if i install vpn on one of my servers will that prevent any information leaking even if i catch something ?
P.S.S: Checked Antivirus KlamAV  and i haven`t found an option for it to scan sites witch i browse and prevent them from loading unwanted malware if such exists on it.

---

### Post by I&#9829;HTML5 on 2011-02-24
Try [Google Chrome](http://www.google.com/chrome). It is a secure, modern browser. I haven't had any security problems with Chrome, even on Windows.

---

### Post by gorxxx on 2011-02-24
> **I&#9829 said:**
> Try [Google Chrome]("http://www.google.com/chrome"). It is a secure, modern browser. I haven't had any security problems with Chrome, even on Windows.

gets popular sooner or later will be a target as well. I am at the point where i am thinking of buying a separate pc only for online banking and gmail.

---

### Post by mikewhatever on 2011-02-24
Are you saying you had a virus in Windows that was a Firefox addon, and that installed itself without your intervention? Can you post a link or name the addon.

---

### Post by gorxxx on 2011-02-24
> **mikewhatever said:**
> Are you saying you had a virus in Windows that was a Firefox addon, and that installed itself without your intervention? Can you post a link or name the addon.


its gone with windows, firefox warned me about about unwanted add-on`s, i  used avira antivirus it was giving me warnings as well when i asked to scan the folder . when i went to  the folder it was located folders were called  {aszzzzzzzzzzzasdasdadasdasds} and when i tryed to enter it my system  hanged soo i had to reset every time. Also it managed to kill avira i  didnt saw it in task manager on next reboot witch is in my book  unbelievable. 
I dont know how it was called mate. it was in /users/username/AppData/mozilla/firefox

---

### Post by mikewhatever on 2011-02-24
Take a look at [Howto secure Firefox]("http://ubuntuforums.org/showthread.php?t=671604") tutorial.
Ultimately, if you run as root and click everything a web site decides to through at you, installing Ubuntu is not going to be much help. On the other hand, if you use a restricted account, Firefox with NoScript and common sense, malware will be a no issue on both Linux and Windows.

---

### Post by amanjsingh on 2011-02-24
Chrome was the "last man standing" on Pwn to Own workshop. No one could hack it. Firefox was the second to go after IE on Win. I'd stick to the best webkit based browser if I were you.

---

### Post by gorxxx on 2011-02-24
Thanks Mike i`ll read the FF manual threw carefully 

amanjsingh
Maybe i am wrong but common sense tells me to use less popular browser. Chrome by the looks of it is used widely sooner or later they will start making sploits for it too imho
[http://www.w3schools.com/browsers/browsers_stats.asp](http://www.w3schools.com/browsers/browsers_stats.asp)

---

### Post by dionysius on 2011-02-25
You could also have a look at Opera. Its security record is quite impressive, and has an online repository for automated updates on various Linux distros. 

[http://www.opera.com](http://www.opera.com)


Clam doesn't do real time protection, so if you require real time protection and heuristics (for Windows for example) you should have a look at the free editions by commercial anti-virus software vendors.

---

### Post by honey_bee on 2011-02-25
i am strange to know virus in linux especially in ubuntu.is there any virus concept in ubuntu linux?kindly logically explain.

---

### Post by honey_bee on 2011-02-25
i am strange to know virus in linux especially in ubuntu.is there any virus concept in ubuntu linux?kindly logically explain.

---

### Post by walt.smith1960 on 2011-02-25
> **gorxxx said:**
> gets popular sooner or later will be a target as well. I am at the point where i am thinking of buying a separate pc only for online banking and gmail.

I'm not sure you need a separate PC, just separate partitions/installs where never the twain shall meet.  Yes, it means restart but this should take less than a minute.  I use a boot manager that can create way more than 4 primary partitions on the same H.D. and the partitions do not see one another unless I give them permission to look at one another. it would almost be tempting to use a LiveCD or LiveUSB session but some secure sites look for "you've been here before" cookies to validate the user.

---

### Post by honey_bee on 2011-02-25
smith can  you mention the name of boot manager you r using so others may also try it thanks

---

### Post by cariboo on 2011-02-25
> **honey_bee said:**
> i am strange to know [s]virus[/s] malware in linux especially in ubuntu.is there any virus concept in ubuntu linux?kindly logically explain.

There is malware out there that works in Linux, most of what windows users call viruses are not out in the wild, and are more a proof of concept then anything else. There is malware out that that reqiures user intervention in order to work, but so far no one has come up with a working example.

Check out the wikipedia page about linux viruses [here]("http://en.wikipedia.org/wiki/Linux_malware"), there is a nice list of viruses, malware and worms, in most cases there is a link to a page on how they work.

---

### Post by walt.smith1960 on 2011-02-26
> **honey_bee said:**
> smith can  you mention the name of boot manager you r using so others may also try it thanks

[http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)

I started with this before I started with Linux. I use Bootit NG for partition and boot management. I also use Image for Linux for partition imaging.  These are shareware apps.

---


---
title: "Spyware via javascript in Linux"
date: 2008-12-02
forum: Security
---

### Post by dpatel on 2008-12-02
I’ve read many threads and articles about linux and spyware, etc. But none truly answer my question: if your browser (running in a linux os) is javascript enabled, can you be affected by spyware? I’m not just asking about ‘destroy your system’ stuff but things like log keystrokes, sites visited, etc.

Javascripts don’t need your permission to load – correct? (Unless you have ‘no-script’ or similar)
What is the extent of javascript’s ‘range’? I’ve heard it’s ‘sandboxed’ – but what does that really mean?
What is the life of a javascript? Only exists as long as your browser is open?

---

### Post by Titan8990 on 2008-12-02
There are no Linux viruses "in the wild". What this means is that you are not going to get a Linux virus unless you are a target of attack (not random submission of viruses like in Windows). You can safely browse the internet without worrying about spyware.

---

### Post by imbjr on 2008-12-02
> **Titan8990 said:**
> There are no Linux viruses "in the wild". What this means is that you are not going to get a Linux virus unless you are a target of attack (not random submission of viruses like in Windows). You can safely browse the internet without worrying about spyware.

JavaScript exploits are still possible and could be used to carry out something like a phishing attack. Google Mail, for example, has previously suffered from cross-site attacks that do not care one wit about the OS of the user. This is why many ppl surf the net with NoScript or just turn JavaScript off.

---

### Post by koenn on 2008-12-02
> **Titan8990 said:**
> There are no Linux viruses "in the wild". What this means is that you are not going to get a Linux virus unless you are a target of attack (not random submission of viruses like in Windows). You can safely browse the internet without worrying about spyware.

You go from "there are no viruses ..." to "[therefore, don't worry about] spyware".
spyware is much wider than viruses. You may be save from visuses, but you'd still have to worry about malicious javascript.

---

### Post by HermanAB on 2008-12-02
Yes, there is a slight risk due to malicious Javascript.  The solution is simple: Don't type personal data into a form unless it is a SSL link.

If a web browser connection is not SSL, then it is not secure.  Simple as that.

---

### Post by bodhi.zazen on 2008-12-02
> **Titan8990 said:**
> You can safely browse the internet without worrying about spyware.

I disagree with that statement. I have run across malicious java script more then once, and as you know javascript is platform independent.

More and more it is important to secure your browser (next to the user, the browser may well be the weakest security link).

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by OrangeCrate on 2008-12-02
^,

Exellent tutorial, thanks. One comment...

Adblock Filterset.G Updater is no longer recommended for use with Adblock Plus:

[http://adblockplus.org/en/faq_project#filterset.g](http://adblockplus.org/en/faq_project#filterset.g)

There is an excellent alternative, however. EasyList:

[http://easylist.adblockplus.org/](http://easylist.adblockplus.org/)

Personally, I have the three EasyList subscriptions installed with Adblock Plus, and I don't use a Hosts file. I'll look into that as an alternative to my set-up. Thanks for the tip.

My personal set-up for Firefox includes:

NoScript
Adblock Plus, plus the three EasyList subscriptions
No third party cookies
CustomizeGoogle
A heavy dose of common sense when surfing

---

### Post by dpatel on 2008-12-02
Thanks to all for replying. :p

So, basically you are saying that malicious javascript ***can*** affect you via your browser even in the Linux world.

But how far reaching can it effects be? Is it contained to your browser and only as long as your browser is open? Or can it be something that loads everytime your browser loads? Can it effect other parts of your system (e.g. delete files)?

---

### Post by s3gfault on 2008-12-02
dpatel:
In theory, javascript can do none of these things, so this is a difficult question to answer.  The javascript runs at the privilege level of the browser, which should be that of a normal user.  It is unlikely to be able to get in there and destroying or modifying system files, this would indicate that the script is exploiting a vulnerability specific to your distribution/version, but it may be able to open network connections, view and modify your personal files, etc.

---

### Post by koenn on 2008-12-02
> **s3gfault said:**
> dpatel:... this would indicate that the script is exploiting a vulnerability specific to your distribution/version, ....
... or you're running your browser as root,

---

### Post by dpatel on 2008-12-02
Well I certainly don't run my browser as root.

By the way, I've not got a specific issue...I wanted to clarify the true extent of the safety of linux with regards to spyware as I've seen so many posts/articles claiming linux is spyware free.

---

### Post by OrangeCrate on 2008-12-02
> **s3gfault said:**
> dpatel:
In theory, javascript can do none of these things, so this is a difficult question to answer.  The javascript runs at the privilege level of the browser, which should be that of a normal user.  It is unlikely to be able to get in there and destroying or modifying system files, this would indicate that the script is exploiting a vulnerability specific to your distribution/version, but **it may be able to open network connections, view and modify your personal files, etc**.

@dpatel

In a nutshell, I would agree with s3gfault, that this is basically what we protect ourselves from, by hardening the browser. And, bodhi.zazen's tutorial is a good template to follow to achieve that.

---

### Post by OrangeCrate on 2008-12-02
> **dpatel said:**
> Well I certainly don't run my browser as root.

By the way, I've not got a specific issue...I wanted to clarify the true extent of the safety of linux with regards to spyware as I've seen so many posts/articles claiming linux is spyware free.

This link is often given here, as a starting point in understanding Linux security:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

And, here's another one:

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by koenn on 2008-12-02
> **dpatel said:**
> Thanks to all for replying. :p

So, basically you are saying that malicious javascript ***can*** affect you via your browser even in the Linux world.

But how far reaching can it effects be? Is it contained to your browser and only as long as your browser is open? Or can it be something that loads everytime your browser loads? Can it effect other parts of your system (e.g. delete files)?
(web-based) javascript would typically be executed by your browser, and thus your browser would have to be open for the script to be executed. 
A javascript might be able to start other programs (a shell script or some other executable present in an accessible part of your disk, i.e. normally only your home dir) and theoretically that might continue to run after the browser is closed. I'm not to sure if this is practically possible, and I don't know any concrete eamples, but I'm no expert on the subject. 

javascript in a web browser would be able to autoload if e.g. you've set the page that contains the script as your browser's start page or used some other, similar feature ("save tabs and reload them next time FF starts"), but, as you can tell from these examples, that requires explicit intervention from the user. Unless, theoretically, the javascript in question is capable of editing user preferences of the browser, which is, again, theoretically possible (eg lots of Firefox preferences andend configuration itself are written in javascript) although I don't know of any real life examples (other than in IE using vbscript on Windows, but that's another story)

---

### Post by bodhi.zazen on 2008-12-02
> **dpatel said:**
> Well I certainly don't run my browser as root.

By the way, I've not got a specific issue...I wanted to clarify the true extent of the safety of linux with regards to spyware as I've seen so many posts/articles claiming linux is spyware free.

I have NEVER heard of spyware on Linux.

---

### Post by OrangeCrate on 2008-12-02
> **bodhi.zazen said:**
> i have never heard of spyware on linux.

+1

---

### Post by koenn on 2008-12-02
> **bodhi.zazen said:**
> I have NEVER heard of spyware on Linux.

Me neither, 
but 
A/ the question of the op is a bit broader than spyware, it's also about the exploitability of javascript in a browser on Linux

B/ just found this :
[http://news.zdnet.com/2100-1009_22-149736.html](http://news.zdnet.com/2100-1009_22-149736.html)

---

### Post by dpatel on 2008-12-03
But at the bottom of the article it states he latered retracted his claim and only managed to make the PC crash.

---

### Post by Chayak on 2008-12-04
There was a a briefing at BlackHat 2008 on javascript based malware that could steal data and ran from an infected browser.  I'll save myself a lot of typing and just post the link to the brief.

[http://www.blackhat.com/presentations/bh-usa-08/Kotler_Rom/H_US_08_Kotler_Rom_Jinx_Malware.pdf]("http://www.blackhat.com/presentations/bh-usa-08/Kotler_Rom/H_US_08_Kotler_Rom_Jinx_Malware.pdf")

It would be cross platform and designed for Firefox.  They also handed out disks with the proof of concept code and it's availible to download so yes there is the potential for someone to use this and there are zero AV scanners looking for it.

---

### Post by bodhi.zazen on 2008-12-05
I came across the PWN2OWN contest :

> Pwn2Own contest at CanSecWest where three fully patched laptops, Mac, Windows Vista and Ubuntu were placed in a contest to see who and how long it would take to hack these systems. The MacBook Air with a fully patched leopard was first after a Safari browser vulnerability was employed to bring it down. The Vista machine was next brought down by a vulnerability in Adobe Flash. The Ubuntu machine was not hacked in the 3 day contest.

[http://www.channelregister.co.uk/2008/03/28/mac_hack/](http://www.channelregister.co.uk/2008/03/28/mac_hack/)

[http://blogs.zdnet.com/security/?p=988](http://blogs.zdnet.com/security/?p=988)

Both Mac and Vista "fell" via browser hacks.

---

### Post by Kinstonian on 2008-12-05
Here is a recent [Slashdot article](http://it.slashdot.org/article.pl?sid=08/12/04/1536231&from=rss) on how malicious javascript is used to steal passwords in FireFox.  It apparently only works on Windows, but to my knowledge, it could also be modified to work on Linux.

---


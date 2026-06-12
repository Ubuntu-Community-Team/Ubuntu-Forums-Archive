---
title: "Network accountability software"
date: 2010-09-20
forum: Ubuntu Christian Edition
---

### Post by greenwom on 2010-09-20
I've got Dans Guardian running on a transparent proxy for my home network.

for my laptop that's on the go I really don't want dans guardian filtering everything.  (it's a netbook, not a lot of resources)

I wanted just something that can email my browsing history to my accountability partner.  

I've installed Net Responsibility - it doesn't work.  It's own bug report shows that email reports do not work.  When I try to run a manual report nothing happens.  needless to say I removed that software and deleted the account from the website ([http://www.netresponsibility.com/](http://www.netresponsibility.com/))

I also tried accountability pal.  After compiling all of the dated dependencies it installed but again nothing working and poor documentation.  ([http://www.accountabilitypal.org/](http://www.accountabilitypal.org/))

So what other options do we have.
Are there any other projects for this that I haven't found yet.

Or would anyone be interested in helping write a script that could be run by a cron job?

---

### Post by hawkeye2777 on 2010-09-22
I don't necessarily want to promote it or anything like that, but I am working on one that would be free and open-source, cross-platform, etc. It is still in the early stages of development though... I haven't even made up a name for it yet.

---

### Post by greenwom on 2010-09-23
Great to hear, I will be a tester for you if you like. 

So far in my experience, keeping it simple would be the best.
I just would want all host name sent in an daily or weekly email.

All of these options for blacklists, whitelists, allowed sites, not allowed sites, etc...  makes this confusing for some end users.  

Seems as simple as a formatted log that records network traffic by host name & time and date stamp.  and then a cron job that runs daily.  

Wish I knew more about programming or I'd offer to help.

---

### Post by McMurdo on 2010-10-07
You may want to consider working in some capacity with the Net Responsibility team. Even if it's kinda broken now, the point of open source is to help each other fix stuff, no? (or at least one of the points...)

Just sayin'. It's be nice to avoid repeat work if you don't really need to repeat it, right?

---

### Post by hawkeye2777 on 2010-10-07
> **McMurdo said:**
> You may want to consider working in some capacity with the Net Responsibility team. Even if it's kinda broken now, the point of open source is to help each other fix stuff, no? (or at least one of the points...)

Just sayin'. It's be nice to avoid repeat work if you don't really need to repeat it, right?

I tried seeing if I could just do that, but it seems like Net Responsibility is intended to be Linux only and I wanted something cross-platform. That's one thing I can think of from when I was deciding if I should code something separate or help that project. I may end up contributing some of my work to it later too.

---

### Post by McMurdo on 2010-10-08
I see. Right on, then.

---

### Post by mpnordland on 2010-10-15
Hi, I am one of the Net Responsibility devs, and I think you should take another look at it, version 2.0a3 is now out and we've made alot of improvements. New in this release is a gui for configuration, along with a few important bug fixes. Automatic reports are working, as for something cross platform, net responsibility is written in Ruby and Python, which are both interpreted languages, and I think that beside the dsniff package, everything else is cross platform, so maybe a cross platform thing wouldn't be too hard. Any way, if you want free accountability for Windows,Mac,Iphone,Android, try x3watch. And come to think of it, Android is linux, so maybe it could be made to work Ubuntu. Just some thoughts!
I hope you find some good accountability software.
Micah
Edit: there is dsniff for windows, so with a little work, net responsibility would work on Windows!

---

### Post by hawkeye2777 on 2010-10-15
> **mpnordland said:**
> Hi, I am one of the Net Responsibility devs, and I think you should take another look at it, version 2.0a3 is now out and we've made alot of improvements. New in this release is a gui for configuration, along with a few important bug fixes. Automatic reports are working, as for something cross platform, net responsibility is written in Ruby and Python, which are both interpreted languages, and I think that beside the dsniff package, everything else is cross platform, so maybe a cross platform thing wouldn't be too hard. 

At the time, what I wanted to do with the application would not have worked with Ruby/Python (at least on the Windows side on things). So I decided to work on my own app. I already wrote my own "logging" program based on libpcap, which I think is a bit more lightweight than dsniff (haven't benchmarked anything yet to prove that, it's just an estimate). It might not be as stable though.

But anyway, now that my plans for what I wanted have changed a bit, maybe I could try and "merge" my work with Net Responsibility. Then again, I might want to do something different with my program. I'm not sure right now though; I haven't had much time recently to work on my program. Anyway, I digress. At some point though, I hope to help out Net Responsibility too in some shape or form.

> **mpnordland said:**
> Any way, if you want free accountability for Windows,Mac,Iphone,Android, try x3watch. And come to think of it, Android is linux, so maybe it could be made to work Ubuntu. Just some thoughts!
I hope you find some good accountability software.

I thought that x3watch was just like Covenant Eyes in that it required a subscription; I must have read their site wrong or something. Still, I guess it doesn't hurt to have some more options for accountability software too. Thanks for mentioning that though; I'll keep that in mind for the future.

---

### Post by greenwom on 2010-10-15
Have you fixed the emailing of reports with this release?  It looked promising when I installed it last.  but I couldn't get an email out even with the manual command.

I'll check it out again.

on a different not I though x3watch cost $$, last I checked the android market I though it was like 6 bucks.   It's not about the 6 bucks for me.  I just want something that works they way I want it, I hope the new version of NR works.

---

### Post by Nicodemus144 on 2010-11-11
X3Watch has free and paid versions.

I use the free versions.

The android app is free.

I'm trying to get net responsibility working.  I really want it to work, but it always gives me a hard time. =/  I'll keep at it though.

---

### Post by sadastronaut on 2010-11-19
I have a two computer solution for this issue.  I run a Linux machine , but I also have a Windows machine running Proxy Server software (specifically Proxy+) and it runs Covenant Eyes.  Linux connects to the internet through this windows proxy.  I haven't tried it, but apparently software called proxychains will work as a transparent proxy.  Right now I have a static IP set on my Linux machine (as well as Windows so I know where the proxy server is), and my router can be configured to block this IP's direct access to windows.

---

### Post by DustStuff on 2012-05-14
Just in case anyone is following this thread or comes across it who is not aware of Net Responsibility (NR) or hasn't been following it's progress, I would definitely recommend [checking it out]("http://www.netresponsibility.com") . The latest versions are a complete rewrite of the software, getting rid of some previous limitations and making it more flexible. Since the rewrite was being done anyway, the developers are coding in such a way as to make it available for as many platforms as possible, including [Windows and Mac OS X]("http://netresponsibility.com/documentation.php?id=0304-InstallFromPackages#3"). I am a NR user (on Ubuntu) and, while it is still not perfect, it does work for me and I would say it is currently the best option for a Linux system. As I have time, I am working on developing and expanding the documentation. If anyone is interested in helping out with this project, whether you are a coder/programmer or just an interested end-user, [see this guide]("http://netresponsibility.com/documentation.php?id=0903-ContributeToNR") for ideas on how you can contribute. We'd love to have you join us! :)

---

### Post by Sef on 2012-05-16
Necromancing, so locked.

---


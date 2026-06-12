---
title: "Configuring DansGuardian &quot;For Dummies&quot;"
date: 2013-03-15
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-03-15
Hi everyone!

I'm testing Ubuntu Christian Edition in a VM on my Mac, and I'm looking at solely moving to Ubuntu CE on all my office machines as our day-to-day work machines (running on custom hardware we're building). I'm pretty familiar with Ubuntu and Linux in general since I'm a web designer and have enough server knowledge and Linux terminal knowledge from compiling Linux apps through the command line.

Ubuntu CE is looking great so far, and I'm really enjoying it.

I have a couple of quick questions though.

1. How can I easily (give me the "for dummies version") control/change settings on DansGuardian? I'd like to keep DansGuardian running if possible since it would allow our machines to be more secure, but in it's current state, it's too intrusive for me to run my day-to-day work. For example, it's blocking the download of ZIP files, Windows EXE files (on most people's machines, I'm fine leaving them blocked, but on my machine, I need to run some Windows applications under WINE and really need to be able to download EXE's), plus when I go to certain websites like to download TeamViewer (since one one of my machines, I need to install TeamViewer to remote into it on the go), it's blocking loading the page. How can I go in and override settings? In addition, if someone else in my office lands on a legitimate website that gets blocked, how can I go in and quickly override it on their machine? I know some of my staff will be hollering at me everytime a website is blocked, and I need to know how to quickly override the legitimate websites for them.

2. Also, how do I go about uninstalling Google Chrome quickly? Can I do it through Terminal or do I need to use Ubuntu Software Center or the Package Manager? We want to use FireFox instead of Chrome.

Thanks!

---

### Post by parkernathan on 2013-03-16
I've been playing around with DansGuardian, and I have it somewhat figured out. Quick side question. When I add a URL to an exception list (like the URL exception list), is it required I restart my machine before I can browse to that site, or can I just refresh the browser page? 

Thanks!

---

### Post by stlsaint on 2013-03-16
> **parkernathan said:**
> Hi everyone!

I have a couple of quick questions though.

1. How can I easily (give me the "for dummies version") control/change settings on DansGuardian? I'd like to keep DansGuardian running if possible since it would allow our machines to be more secure, but in it's current state, it's too intrusive for me to run my day-to-day work. For example, it's blocking the download of ZIP files, Windows EXE files (on most people's machines, I'm fine leaving them blocked, but on my machine, I need to run some Windows applications under WINE and really need to be able to download EXE's), plus when I go to certain websites like to download TeamViewer (since one one of my machines, I need to install TeamViewer to remote into it on the go), it's blocking loading the page. How can I go in and override settings? In addition, if someone else in my office lands on a legitimate website that gets blocked, how can I go in and quickly override it on their machine? I know some of my staff will be hollering at me everytime a website is blocked, and I need to know how to quickly override the legitimate websites for them.

2. Also, how do I go about uninstalling Google Chrome quickly? Can I do it through Terminal or do I need to use Ubuntu Software Center or the Package Manager? We want to use FireFox instead of Chrome.

Thanks!

Answer for question 1: 
DG is configured fully with config files. These files allow quick and easy management of Dansguardian. For a further explanation please see here: [http://dansguardian.org/downloads/detailedinstallation2.html#further](http://dansguardian.org/downloads/detailedinstallation2.html#further)

Answer for question 2: ```
 sudo apt-get remove google-chrome-stable 
```

Answer for second post you made: 
```
 sudo service dansguardian restart 
```

---

### Post by parkernathan on 2013-03-17
Thanks for the info! Looking over this, I'll be able to easily tweak DansGuardian on systems. Great to know!

---


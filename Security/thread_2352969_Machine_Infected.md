---
title: "Machine Infected"
date: 2017-02-17
forum: Security
---

### Post by cobras on 2017-02-17
Greetings,

I was browsing just minutes ago, and I must have inadvertently clicked on something, because a window suddenly popped open.  It was one of those annoying threats that you've been attacked by a virus that wants to take all your money, and the only way to fix it is to contact them.  You know, one of those windows that you can't close or shut up.

I rebooted and it seems to be gone.  My question is, how do I make sure that it is gone?

Maybe I should mention that I'm running Ubuntu 12.04 on a Toshiba Satellite C55-A.

Thanks for help you can offer.

---

### Post by mörgæs on 2017-02-17
How do you come from seeing a pop-up window to concluding that your machine is infected?

---

### Post by Perfect Storm on 2017-02-17
Clean cache of the browser for safty.

---

### Post by ajgreeny on 2017-02-17
Don't forget you must upgrade your OS in April at the latest as it will otherwise be unsupported.

---

### Post by bearlake on 2017-02-17
When that happen to me, I backup my bookmarks.

Removed Firefox using Software Center or Synaptic, removed Firefox directories, rebooted and did a fresh install.

Never looked back after that.

---

### Post by cobras on 2017-02-17
> **mörgæs said:**
> How do you come from seeing a pop-up window to concluding that your machine is infected?

Because I recognized the window, not a pop-up, and I was pretty sure that by my brief description most people would realize what I was talking about.  I caught it using Windows once and had to jump through some hoops to get rid of it, but I don't know how things go with Ubuntu.

> **Artificial Intelligence said:**
> Clean cache of the browser for safty.

Per chance, I've been updating my website and have done so as a matter of course.

> **ajgreeny said:**
> Don't forget you must upgrade your OS in April at the latest as it will otherwise be unsupported.

Thanks for the reminder.  I've been thinking of upgrading any way 'cause 12.04 has been a terrible and frustrating disappointment.  I've acutally thought of going back to 10 (or was 9 my last version?).

Any tips on what the best alternative/s may be?

> **bearlake said:**
> When that happen to me, I backup my bookmarks.

Removed Firefox using Software Center or Synaptic, removed Firefox directories, rebooted and did a fresh install.

Never looked back after that.

But it seems to be gone after rebooting.  Is it not?

---

### Post by sgian on 2017-02-18
An internet virus that will wreak havoc on Windows won't normally do anything to linux other than potentially infect wine if you have it or the browser.  Something to do with software not having as many permissions in linux, quicker security patches, and requiring different commands to be programmed.  As long as you cleared your browsing data, including cookies and cache, it should be gone.  If it will make you feel better, install ClamAV or if you need it to be graphical then ClamTK.  Update the definitions, do NOT enable PUA, and let it scan.  If it finds anything, you can upload the potentially compromised file to virustotal.com to make sure it is not a false positive, which has happened a lot for me with ClamAV.

Also, make sure you have your firewall enabled.  If you just browse the internet and don't have any specific ports that need to be opened, then just open a terminal and type ```
sudo ufw enable
```  If you need a graphical interface for the firewall, then install something like gufw.

Regarding the ubuntu version, one of the advantages of linux is having faster security patches.  If you continue with a version of ubuntu that is no longer supported, then you lose that advantage.  Also, many versions of software might not work much longer with ubuntu 10.04, 12.04, etc since it shouldn't be used anymore.  Using 10.04 wouldn't be as risky as Windows XP, but it is a similar problem in that both will no longer have security patches.  I would recommend Ubuntu 14.04 for that laptop.  14.04 boots up fast, and should be supported until April of 2019, and run nicely on your laptop.  More programs will work with 14.04 than 12.04, and you will still get security updates for a longer time with 14.04.  I would even expect Ubuntu 16.04 to work ok on that laptop if you still have the 4 GB of RAM, it will just take a minute or so to start up since your CPU is slow by today's standards.  Ubuntu 16.04 will be supported until April 2021.  For more info, see [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by cobras on 2017-02-18
Thank you so much sgian.  That's all very useful.  I've upped my RAM to 12, so maybe i'll go with 16.04.

---

### Post by HermanAB on 2017-02-19
Install HTTPS Everywhere, Ghostery and Adblock in your browser and all the cruft will be gone, then relax and enjoy your Linux machine.

---


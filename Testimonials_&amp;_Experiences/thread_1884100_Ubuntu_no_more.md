---
title: "Ubuntu no more"
date: 2011-11-20
forum: Testimonials &amp; Experiences
---

### Post by decoherence on 2011-11-20
I've finally done it. I've finally wiped Ubuntu off my last laptop like I said I was going to for the past however long. The machine in question is the netbook I use for field work.

Things started going south for me after Natty, with lots of inconsistent behavior. Lately, the main issue has been networking. When I do field work I'm generally configuring routers and switches and other 'smart' devices, using either a RS-232 console or ssh/telnet over directly connected ethernet.

The straw that broke the camel's back was not being able to ping the console server that I was configuring. Tried with networkmanager, tried without it but no love. After a few attempts to troubleshoot it, it chalked it up to a hardware problem. Rebooted in to Windows 7 to test that and the ping worked fine. That burns...

When configuring and testing a network device, it's vital that you be able to reliably control the network functions of your computer. This is not the first time Ubuntu has done this to me -- it can be fixed by simply resetting the network stack. But trying to test something and having to worry about whether your own gear is working properly at that moment just isn't a good mxi.

Yesterday I backed up everything up and installed AntiX. Installation was a snap and the MEPIS setup tools, while they aren't pretty, are perfectly functional. Sadly, Debian Testing is officially 'too out of date' for me. Many sites were broken on Iceape. I couldn't get my backed up thunderbird and gnupg stuff to work in icedove. I probably could've figured it out but I gave up and went with my old standby, Arch.

It took quite a while to get Arch working like I want but I now have a screaming fast GNOME3.2 desktop (yes, screaming fast. on a crappy netbook with intel graphics. up-to-date software rocks!) and a version of network manager that doesn't drive me to drink.

May Ubuntu continue to meet your needs. But if not, Fedora and Arch may have what you're looking for. I run both and lean towards Arch but I've been using it longer.

I look forward to trying future Ubuntu releases. Keep up the good fight!

---

### Post by AlexDudko on 2011-11-20
Debian, CentOS, Scientific Linux are more stable and reliable than Ubuntu or Fedora (and Arch as well). If you need stability - use one of them. 
If you are just playing and testing - do not complain but file a bug report if you find one.

---

### Post by marl30 on 2011-11-20
I'm so ashamed to say that I find Windows 7 faster, more functional, and more stable than the current version of Ubuntu. It was the opposite when 10.04 impressed me so much more that I dumped Windows 7 for it, now I find myself using Windows much more since I stated using the newer versions of Ubuntu. Kubuntu 11.10, is far more pleasant to use than the main version. Things should not feel like one step forward then two step backward after certain release.

---

### Post by Bucky Ball on 2011-11-20
Your fieldwork machine would be considered a production machine. LTS releases recommended for these machines (and servers), *not* upgrading to every new release. Stick with the LTS, supported for three years, if you intend actually working on the machine (and it sounds like it is used in a professional or study/research capacity). Keep a separate partition if you want to diddle with new releases. 10.04 LTS is the current long-term support release. You might want to try that or wait a few months after the release of the next, 12.04 LTS. Good luck.

---

### Post by decoherence on 2011-11-20
> Debian, CentOS, Scientific Linux are more stable and reliable than Ubuntu or Fedora (and Arch as well). If you need stability - use one of them. 

Well, I listed my reasons for not going with a Debian thing. CentOS and Scientific are interesting distros -- I used to run CentOS and I'll probably try Scientific at some point. RedHat based systems aren't my strong suit, though.

Arch is plenty reliable (as long as you read the wiki and the news before you update) and I'm familiar with it, so that made it the right choice for me in these circumstances.

---

### Post by decoherence on 2011-11-20
> **Bucky Ball said:**
> Your fieldwork machine would be considered a production machine. LTS releases recommended for these machines

This started out as an LTS machine but particular vital packages had bugs (go fig) so here we are.

In my experience, Arch will be sufficient for what I need due mostly to it's "KISS" philosophy and it's up to date, downloadable docs.

I'll definitely look at Ubuntu's next LTS.

---


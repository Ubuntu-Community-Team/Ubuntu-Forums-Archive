---
title: "Security Issues with Ubuntu"
date: 2008-08-20
forum: Security
---

### Post by geotev on 2008-08-20
Hello,

I began using Ubuntu a year ago. I have a dedicated machine that is joined to a Windows network. I use an Internet Security program on all my Windows machines. I thought that Linux was not being affected with security problems. However, I recently have been seeing anti-virus and internet security programs for Linux computers. 

1) Are these types of programs now necessary for my Ubuntu machine?
2) If so, are there open source projects to check into concerning this?

Thank you for your help in my understanding!

P.S. I realize I need to check into this forum instead of others for future reference. I think my questions will help focus me on current & future security issues with Ubuntu Linux.

---

### Post by xouns on 2008-08-20
I don't feel safe using Ubuntu as a long time Windows user, I have the same question. Please reassure me!

---

### Post by sandysandy on 2008-08-20
see these articles

[http://www.linux.com/articles/60208](http://www.linux.com/articles/60208)

[http://www.linux.com/articles/22899](http://www.linux.com/articles/22899)

regards

---

### Post by AndyCee on 2008-08-20
Heya,

If you haven't already looked, LaRoza has posted a very detailed thread about Ubuntu security [here]("http://ubuntuforums.org/showthread.php?t=765421").

To briefly answer your questions, geotev, viruss canners for linux are intended for scanning windows machines.

In terms of firewall - by default linux has all ports closed and the latest release uses ufw. I don't use it myself, but it can't hurt (it can complicate slightly if you use port-forwarding or ssh server, but not much).

Anyway, check the above link. It's got very useful info.

---

### Post by decoherence on 2008-08-20
The anti-virus programs you see check for Windows viruses. While a Windows virus will not affect Ubuntu, it is still possible to pass the virus on to our less fortunate Windows using friends. So these linux antivirus programs are more for the benefit of Windows users, and they're a good idea if you're networking with Windows machines.

Running Ubuntu securely generally requires only common sense. If security is likely to be a major concern, you'll be more interested in the various extended permissions schemes (SELinux, AppArmor) and intrusion detection systems (aide, snort, tripwire) than anti-virus.

---

### Post by hyper_ch on 2008-08-20
(1) you generally don't need antivirus
--> antivirus programs only delete windows viruses. It can be of use to run antivirus on linux if you operate an email or fileserver and if you feel obliged to "protect" windows users that make use of emails and files from you.

(2) you generally don't need antimalware stuff
--> see (1)

(3) you generally don't need a firewall - or rather alter it's default state
--> there's already a firewall installed called iptables. By default it does not do anything. This is reasonable as by default there are no services listening.
However when you want to offer services (webserver, email server, file server, .....) then you maybe want to limit who can access it. And don't forget, on windows a lot of software "phone home". So on windows you not only protect yourself against what gets in but also against what gets out. In linux such spyware is hardly non-existant.

(3) there are security tools that you may want to run. The two most populars are probably chkrootkit and rkhunter.

(4) general advice on security:
--> Use a strong password for your user account
--> Don't download .deb files or source code from just anywhere on the net. Most stuff is available in the repos. For other stuff you have trusted sites like getdeb or sourceforge...
--> Don't run everything as root
--> Use your brain...

---

### Post by Master Chief on 2008-08-20
Hi guys/gals,

Sure, there are anti-virus software kits available for GNU Linux OSes like Ubuntu, but the question is not *why* you need them, but *when*.

Installing anti-virus programs might, or might not, offer additional "security" because this solely depends on how you setup and use Ubuntu (don't use the root account) and how you setup the (additional) software (think shares).

You might for example download files via Ubuntu (from unknown sources / networks) and share these with other Windows computers on your network, which doesn't offer the same level of file/user protection (permissions) as Unix/GNU Linux offers.

So what exactly are you doing / planning to do with Ubuntu?

Note: Most people, including me, won't install anti-virus software because they don't need it, others might need it badly. Again it all depends on your needs!

---


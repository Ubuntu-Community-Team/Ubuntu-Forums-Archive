---
title: "Securing linux bare-minimum checklist?"
date: 2011-07-10
forum: Security
---

### Post by supershin on 2011-07-10
That's the title of article at [http://linux-news.org/?p=1837]("http://linux-news.org/?p=1837")

Did ubuntu do all this already or is it that ubuntu isn't secure out of the box that it is assumed to be? 

Please explain if these steps are applicable to ubuntu and why/why not.

---

### Post by Dangertux on 2011-07-10
That article is written in terms of a machine running as a server. It is also a very narrow scoped document and contains only a few hardening measures. There are hundreds if not thousands of things you can do in terms of server hardening. 

As for if it applies to Ubuntu , server hardening regardless of OS is necessary. Unless you're building a honeypot ;)

Now, the statement about Ubuntu being secure out of the box. I don't like it , it's a clever marketing device and I understand its reason for being. However it generates questions like yours. For a simple desktop installation Ubuntu is rather secure out of the box. Note I will not speak in terms of absolutes because nothing controlled by a human will ever be absolutely secure. 

To further answer your question some of those methods could be used on a desktop system particularly the sysctl.conf portion. However, in terms of a desktop machine they would not yield great benefit. Unless you spend alot of time using public wifi then I might do the changes to sysctl.

Bottom line for desktops Ubuntu's default configuration is fine.  Once you start running services it becomes much more complicated.

---

### Post by bodhi.zazen on 2011-07-11
> **supershin said:**
> That's the title of article at [http://linux-news.org/?p=1837]("http://linux-news.org/?p=1837")

Did ubuntu do all this already or is it that ubuntu isn't secure out of the box that it is assumed to be? 

Please explain if these steps are applicable to ubuntu and why/why not.

That article is horrible and although some of it may apply to Ubuntu, some if the information on that page is wrong and some of it does not apply to Ubuntu at all. XINETD ? What distro uses that ?

Get your security information from credible sources, starting with the distro you are using.

Start with the security sticky on these forums, then learn apparmor.

[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by movieman on 2011-07-13
> **bodhi.zazen said:**
> XINETD ? What distro uses that ?

RHEL5 certainly does.

The NSA have a great guide to securing Red Hat, a fair amount of which is also relevant for Ubuntu, particularly if running as a server. I don't have the URL handy.

---

### Post by bodhi.zazen on 2011-07-13
This is a better check list: [http://www.cyberciti.biz/tips/linux-security.html](http://www.cyberciti.biz/tips/linux-security.html)

---

### Post by supershin on 2011-08-07
Thanks all for clearing that up. Especially you bodhi.zazen, I've read your stickies and posts, good work.

---


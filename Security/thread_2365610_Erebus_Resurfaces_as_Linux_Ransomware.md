---
title: "Erebus Resurfaces as Linux Ransomware"
date: 2017-07-08
forum: Security
---

### Post by amjjawad on 2017-07-08
Hi,

The other day, there was yet another debate on LinkedIn about Microsoft Windows vs GNU/Linux. Today, someone posted this:

[http://blog.trendmicro.com/trendlabs-security-intelligence/erebus-resurfaces-as-linux-ransomware/](http://blog.trendmicro.com/trendlabs-security-intelligence/erebus-resurfaces-as-linux-ransomware/)

> On June 10, South Korean web hosting company NAYANA was hit by Erebus ransomware (detected by Trend Micro as RANSOM_ELFEREBUS.A), infecting 153 Linux servers and over 3,400 business websites the company hosts.

My question to our Ubuntu and/or GNU/Linux Security Masters and Gurus, is this true?

I know there is NO 100% secure system on earth as of this very moment but can GNU/Linux resist this nasty virus and/or other viruses?! 

Are these statements true:

> This is a message to companies and security professionals that no system is immune to attacks by default, and to beginners those were bragging about how Linux is powerful  compared to windows  when it comes to viruses...well, here you go! 

> To Linux lovers, no one is safe anymore, you should rethink your server security seriously and deploy server security ASAP!

Thanks in advance :)

---

### Post by gjohnz on 2017-07-08
I would say that since Trend Micro put info on their blog, then there is some weight to the story. But, reading the blog, I see a couple of interesting points. This paragraph from the blog points out the fact that the alleged infected servers are old and/or haven't been updated in years.
> [COLOR=#666666][FONT=Arial]***Possible Arrival Vector***
As for how this Linux ransomware arrives, we can only infer that Erebus may have possibly leveraged vulnerabilities or a local Linux exploit. For instance, based on open-source intelligence, NAYANA&#8217;s website runs on Linux kernel 2.6.24.2, which was compiled back in 2008. Security flaws like DIRTY COW that can provide attackers root access to vulnerable Linux systems are just some of the threats it may have been exposed to.[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]Additionally, NAYANA&#8217;s website uses Apache version 1.3.36 and PHP version 5.1.4, both of which were released back in 2006. Apache vulnerabilities and PHP exploits are well-known; in fact, there was even a tool sold in the Chinese underground expressly for exploiting Apache Struts. The version of Apache NAYANA used is run as a user of *nobody(uid=99)*, which indicates that a local exploit may have also been used in the attack.[/FONT][/COLOR]


If I stopped reading after that paragraph I would already feel 99% more secure with my fully updated and maintained 2016-2017 vintage Linux installs.

This being said, I would also not necessarily be complacent with my systems. Unfortunately we always need to be on guard with our Internet connected devices.

---

### Post by amjjawad on 2017-07-08
Another link:
[https://access.redhat.com/solutions/3094421](https://access.redhat.com/solutions/3094421)

---

### Post by webmiester on 2017-08-26
Just read through this thread.  It appears that a South Korean company paid 1M dollars in ransom because of Erebus.  Have we patched Erebus in ubuntu?  How safe are we?

---

### Post by HermanAB on 2017-08-27
It seems to work only on a specific version of some long obsolete server from ten years ago.

---


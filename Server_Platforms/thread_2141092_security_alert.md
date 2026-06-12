---
title: "security alert"
date: 2013-05-01
forum: Server Platforms
---

### Post by Vegan on 2013-05-01
[http://www.zdnet.com/sophisticated-backdoor-malware-opens-up-security-blackhole-in-apache-web-servers-7000014758/]("http://www.zdnet.com/sophisticated-backdoor-malware-opens-up-security-blackhole-in-apache-web-servers-7000014758/")

---

### Post by CharlesA on 2013-05-01
Good thing I use Nginx. :p

---

### Post by SeijiSensei on 2013-05-02
According to the article, the exploit requires that the Apache daemon be *replaced* with a corrupted version.  Just how does it do that?  Last I checked every version of Apache I have running came from CentOS or Ubuntu.  Unless their repositories are corrupted how does this exploit take place?  The ZDNet article was sadly lacking in important details like that.

Also they claim it is running on "hundreds" of servers, not a very large fraction when Apache is hosting well over [300 million domain names]("http://news.netcraft.com/archives/2013/01/07/january-2013-web-server-survey-2.html").

Charles, the article observes that nginx is the hot up-and-coming contender; it's now hosting 12% or so of web domain names.

---

### Post by CharlesA on 2013-05-02
> **SeijiSensei said:**
> According to the article, the exploit requires that the Apache daemon be *replaced* with a corrupted version.  Just how does it do that?  Last I checked every version of Apache I have running came from CentOS or Ubuntu.  Unless their repositories are corrupted how does this exploit take place?  The ZDNet article was sadly lacking in important details like that.

Also they claim it is running on "hundreds" of servers, not a very large fraction when Apache is hosting well over [300 million domain names]("http://news.netcraft.com/archives/2013/01/07/january-2013-web-server-survey-2.html").

Charles, the article observes that nginx is the hot up-and-coming contender; it's now hosting 12% or so of web domain names.

Heh, yeah, Nginx is getting up there too.

I am in the same boat with the machines I run Apache on - Debian and Ubuntu, but I'm running Nginx on my VPS, cuz it's a tiny one. ;)

The only way I can think that the Apache executable could be replaced like that is if the server already got owned and someone has root access to do whatever they want with it.

With that being said, I'm sure there are people who compile Apache manually, but I don't really know how widespread that is and if you are going to be compiling anything, wouldn't you get the package from the official site?

Overall the article smells like FUD to me, especially since they don't really go into detail about how this exploit is supposed to work.

---

### Post by SeijiSensei on 2013-05-02
I've compiled Apache from source a few times in my career, but not any time recently.  I've compiled PHP as well.  Now I let the distribution maintainers handle all that.  I no longer find myself bumping up against limitations that are only fixed in more recent releases.  I have built from the original source, and from source RPMs as well.  (Sometimes I want to enable or, more often as in the case of Kerberos, disable a setting passed to autoconf.) 

I notice that Netcraft reports most people are still using Apache 2.2 when 2.4 is available.  I'm sure the fact that RedHat is still distributing 2.2 with backported patches has a lot to do with that.  I updated my CentOS 6.2 version of Apache just today; it's still at 2.2.15.

---

### Post by CharlesA on 2013-05-02
I've never compiled Apache from source but I haven't run into things where I would need to.

I just checked my 12.04 box and it's running Apache 2.2.22 with PHP 5.3.10. I figure security patches and the like are backported on Ubuntu the same way they are on RH, but I am not 100% sure about it.

That is also why it's a bad idea to rely on security scanners that only check version numbers.

---


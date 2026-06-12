---
title: "HOWTO : Almost a perfect and secure Ubuntu 9.04 server"
date: 2009-06-14
forum: Security
---

### Post by samiux on 2009-06-14
Hi all,

When I set up my Ubuntu 9.04 server, I find that there is almost no information about how to hardening it.

The following link is about how I setup my Ubuntu 9.04 server and how to make it more secure.  I would like to share it with you all.

[The original link is here.]("http://samiux.wordpress.com/2009/06/13/howto-almost-a-perfect-and-secure-ubuntu-9-04-lamp-server/")

[Another link is here.]("http://secure-ubuntu-server.blogspot.com/")

As I am a newbie in Linux security, there may be some mistakes and drawback.  Your comment and tips are welcome.

Samiux

---

### Post by Dave_Connor on 2009-06-14
One use of securing, if you ssh, you can switch to key auth and disable password auth and set up tunneling so you can browse much more secure.

---

### Post by bodhi.zazen on 2009-06-14
Thank your for sharing your experience.

Hardening is performed service - by - service.

For ssh, I use keys and rather then denyhosts / fail to ban I use iptables.

Other advice is to use Apparmor or selinux.

See the security sticky at the top of these forums.

You can also try mod_evasive and mod_security for apache.

Last, see the hardening Debian guide :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by samiux on 2009-06-14
bodhi.zazen,

Thank you for your advice.

Now, my server can be logged in via SSH key only.  :D

I am now studying AppArmor and hope that I can master it in a short time.

Samiux

---

### Post by dnvikram on 2010-01-15
> **samiux said:**
> bodhi.zazen,

Thank you for your advice.

Now, my server can be logged in via SSH key only.  :D

I am now studying AppArmor and hope that I can master it in a short time.

Samiux

I think you should change the description of one of the features of samiux and not point to specific names.Else,some people who are really interested in this distro may get turned off.

"Web Filter : Block time-wasting sites like MySpace and Facebook. Clientless installation and custom block lists."

The above description sounds more like your own Opinion than a simple description of the Web-Filter feature.People who use Facebook and MySpace may find it offensive and some people may find it another example of Chinese Internet Censoring of Non-Chinese popular sites.And,it doesnt mention a single name of the Chinese versions of facebook or myspace.So to make it simple,those names can be replaced by a simple,"Popular time wasting social networking sites".

Thanks.

---

### Post by BigCityCat on 2010-01-16
When China starts coming up with their own ideas rather than rip everybody else off. Then I might actually be impressed.

---

### Post by cariboo on 2010-01-16
Please keep this thread civil, Just because the op is from Hong Kong, doesn't necessarily mean he is Chinese.

As far as blocking "time wasting" web sites, in the workplace many companies block Facebook and Myspace. I've blocked those sites and many more at some of the places I have worked.

---

### Post by running_rabbit07 on 2010-01-16
I agree with Cariboo. In business, I would consider anything not getting work done as time wasting.

---

### Post by tommynz1975 on 2010-01-16
Would not using social networking sites and surfing for fun be considered employee theft?. 
As anything that puts strain on the servers might make a company buy extra hardware to satisfy a group of employees personal tastes.

Even thou in New Zealand where I live it was successfully argued that it was part of the company culture, when an employee was fired for sending objectionable images via email around the company.

---

### Post by running_rabbit07 on 2010-01-16
I've seen the same here in the states.

---


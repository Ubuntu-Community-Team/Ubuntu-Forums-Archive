---
title: "Why would I want to run Ubuntu as a Server vs Centos?"
date: 2010-02-09
forum: The Cafe
---

### Post by waloshin on 2010-02-09
Why would I want to run Ubuntu 9.10 as a single user mail server or using Centos 5.4?

But for the great ubuntuforums.org community! :)

---

### Post by Simon17 on 2010-02-09
I'm not certain that you would.

---

### Post by Icehuck on 2010-02-09
RHEL is supported for 7 years and stable. Ubuntu server is not supported for seven years, and well not as stable(I don't find debian stable either).

Home use? Doesn't matter which one you use. I will say that my CentOS server never went down until one of my hard drives died. I can't say the same for Debian/Ubuntu.


FYI - CentOS is Red Hat Enterprise Linux without the Red Hat Logos.

Edit - Learning on CentOS translates to learning on RHEL which in turn becomes a job skill. One that is highly desired in the world of IT.

---

### Post by Kenny_Strawn on 2010-02-09
Use Ubuntu, and run the following command at the shell:

```
sudo apt-get install apache2
```

You may also want to add MySQL and PHP, but there is no metapackage for either of them, so you're off manually installing all the packages that come with them (probably close to 100).

---

### Post by LightB on 2010-02-09
For the lulz?

---

### Post by mushwars on 2010-02-09
dont.
```
vim /etc/make.conf
```
'i'
```
USE="centos"
```
[esc] :wq

---

### Post by TuckLive on 2010-02-09
I'm trying to decide between 10.04 and CentOS 6, which will both be out roughly the same time.  My use will be a web/media server.  Any more suggestions or thoughts?

---

### Post by snowpine on 2010-02-09
Ubuntu 10.04 will have more recent software; CentOS 6 will have older software that is well-tested and known to be stable. It really depends on your needs and preferences; try both and decide for yourself. :)

---

### Post by juancarlospaco on 2010-02-09
I dont like RHEL or Centos, 
it just use/install/run too many unrequested services by default and
RPM dependencies is a pain to solve.

---

### Post by cariboo on 2010-02-09
> **Kenny_Strawn said:**
> Use Ubuntu, and run the following command at the shell:

```
sudo apt-get install apache2
```

You may also want to add MySQL and PHP, but there is no metapackage for either of them, so you're off manually installing all the packages that come with them (probably close to 100).

Please do some research before answering a question, you can select the LAMP stack while doing a server installation, there are also many other services you can install at that time. If you don't chose to install any services when doing the install, you can later install what you want, by typing:

```
sudo tasksel
```

at the prompt.

---

### Post by foldingstock on 2010-02-09
> **juancarlospaco said:**
> I dont like RHEL or Centos, 
it just use/install/run too many unrequested services by default and
RPM dependencies is a pain to solve.

RPM dependencies are a pain? So are DEB dependencies. That is why both RHEL/CentOS and Debian/Ubuntu come with package managers. 

Debian/Ubuntu has apt, RHEL/CentOS has yum. Software is no harder to install on CentOS than Ubuntu.

---

### Post by juancarlospaco on 2010-02-09
lol,* BTW talking with experience on both...*

---

### Post by TuckLive on 2010-02-09
> **snowpine said:**
> Ubuntu 10.04 will have more recent software; CentOS 6 will have older software that is well-tested and known to be stable. It really depends on your needs and preferences; try both and decide for yourself. :)

Very helpful thanks :D.  I haven't used CentOS much, but was looking at it for a future server.  My main concern is backing/support.  Ubuntu has Canonical for some backing while CentOS is entirely community based and well almost fell apart last year.  CentOS may be more stable because it's based off RHEL, but Ubuntu seems to have better support I believe.  So I think I'm gonna stick with Ubuntu.

---

### Post by snowpine on 2010-02-09
> **TuckLive said:**
> Very helpful thanks :D.  I haven't used CentOS much, but was looking at it for a future server.  My main concern is backing/support.  Ubuntu has Canonical for some backing while CentOS is entirely community based and well almost fell apart last year.  CentOS may be more stable because it's based off RHEL, but Ubuntu seems to have better support I believe.  So I think I'm gonna stick with Ubuntu.

By that logic, paying for RHEL may be your best option. :)

---

### Post by phrostbyte on 2010-02-09
I like Ubuntu Server better. If you are more used to Ubuntu I think it's a better choice, because the file system layout and command set will be more familiar.

If you are worried about usage:

Wikipedia runs on Ubuntu Server. And Digg runs Debian. :) And in regards to jobs, you should all check out Monster/Dice, there are jobs out there specifically looking for Ubuntu Server or Debian experience. :p They are more popular then you think.

---

### Post by YeOK on 2010-02-09
> **TuckLive said:**
> Very helpful thanks :D.  I haven't used CentOS much, but was looking at it for a future server.  My main concern is backing/support.  Ubuntu has Canonical for some backing while CentOS is entirely community based and well almost fell apart last year.  CentOS may be more stable because it's based off RHEL, but Ubuntu seems to have better support I believe.  So I think I'm gonna stick with Ubuntu.

CentOS is not RedHat based. It is RedHat, with the copyright logo's removed and the CentOS Community providing support. ( You pay for that with RedHat )

Anyway, for a home server its a none issue, use which ever distro you have the most knowledge of.

---

### Post by TuckLive on 2010-02-09
> **YeOK said:**
> CentOS is not RedHat based. It is RedHat, with the copyright logo's removed and the CentOS Community providing support. ( You pay for that with RedHat )

Anyway, for a home server its a none issue, use which ever distro you have the most knowledge of.

Yes, I know.  Sorry for bad wording.

---

### Post by TuckLive on 2010-02-09
> **phrostbyte said:**
> 

If you are worried about usage:

Wikipedia runs on Ubuntu Server. And Digg runs Debian. :) And in regards to jobs, you should all check out Monster/Dice, there are jobs out there specifically looking for Ubuntu Server or Debian experience. :p They are more popular then you think.

That's cool. I did not know that.  :cool:

---

### Post by juancarlospaco on 2010-02-09
I dont like the YellowDog Updater Modified, because it dont have Super Cow powers, 
*and WTF a Yellow Dog?*

((EDIT: i know that yellow dog is a distro))

---

### Post by cariboo on 2010-02-09
Yellow dog is a ppc Linux distribution.

---

### Post by squilookle on 2010-02-09
i run an ubuntu server because it was ridiculously easy to set up - but i use it for development/testing. 

if i were running a production server, it would be centos.

---

### Post by koenn on 2010-02-09
> **Kenny_Strawn said:**
> Use Ubuntu, and run the following command at the shell:

```
sudo apt-get install apache2
```

You may also want to add MySQL and PHP,
Why would  you suggest to install a *web* server when the OP is asking about a _mail_ server ?

---


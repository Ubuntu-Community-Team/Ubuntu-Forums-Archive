---
title: "Will LTSP work in Ubuntu Server 14.04"
date: 2012-03-03
forum: Server Platforms
---

### Post by Avinash.Rao on 2012-03-03
Hi, 

I am in the process of choosing a proper operating system environment for my office. I have about 120 windows users involved in basic office activities. 

I have implemented LTSP in Ubuntu 8 in the past but had few glitches and spent a lot of time troubleshooting as we had different client hardware like laptops, desktops etc. 

My question is will LTSP work in Ubuntu Server 14.04? If yes, how easy or tough is it configure different client hardware, drivers etc. 

I am surprised LTSP is not mentioned in the list of features for Ubuntu Server in the website.

Thanks,
Avinash

---

### Post by Bucky Ball on 2012-03-03
14.04 LTS!!! That will not be released until April 2014 and is a twinkle in the developer's eyes at the moment. Are you meaning 12.04 LTS??? That is out in a couple of months (late April 2012) ...

Can't help with your actual question but can say this: for production machines and a situation like yours stick with the LTS (long term support releases) as that's why they're there. The current (and if you need to start now, use it) is 10.04 LTS and the server version has five years support (until April 2015). It is rock solid.

---

### Post by Avinash.Rao on 2012-03-03
I am talking about LTSP - Linux Terminal Server Project (LTSP) and NOT LTS.

---

### Post by Bucky Ball on 2012-03-03
> **Avinash.Rao said:**
> I am talking about LTSP - Linux Terminal Server Project (LTSP) and NOT LTS.

Totally aware of that. 14.04 doesn't exist but it will be an LTS release when it does. You are misunderstanding me. Goodnight. ;)

---

### Post by Avinash.Rao on 2012-03-03
Oh.. My apologies for typing the wrong version. 

Please read the version as Ubuntu Server Version 11.10

---

### Post by Exonimus on 2012-03-08
Although I can't help you with the specifics, I can't see why ltsp would not be there in 11.10, (it is, of course, there! :D) Have you checked out this link?

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by spynappels on 2012-03-08
And you'd probably be safer waiting for US12.04 as it is a LTS release and will be able to do LTSP.

---

### Post by Avinash.Rao on 2012-03-08
Yes, I have seen this site before. My worry is that if getting LTSP to work is left the forums and other users, this creates a bigger doubt in the minds of administrators who are in the process of deciding the operating environment. Just a link to a documentation site and forums isn't really convincing to be able to make a crucial decision. And testing doesn't come easy either.. Migrating from windows to LTSP is not a minor thing! Which is why my question was why isn't it mentioned in the list of features? Has it been given the same importance as other modules! Is it easier to setup and make life easier for administrators.. these are questions that needs to be answered. 




> **Exonimus said:**
> Although I can't help you with the specifics, I can't see why ltsp would not be there in 11.10, (it is, of course, there! :D) Have you checked out this link?

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by snowpine on 2012-03-08
> **Avinash.Rao said:**
> My worry is that if getting LTSP to work is left the forums and other users, this creates a bigger doubt in the minds of administrators who are in the process of deciding the operating environment. Just a link to a documentation site and forums isn't really convincing to be able to make a crucial decision. 

If it helps convince the "powers that be" that Ubuntu is the real deal, paid "enterprise" support is available: [http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

---

### Post by iangarforth on 2012-03-09
Avinash, I understand your concern, and agree entirely.  I'm not sure why LTSP has developed into this kind of 'bit part add on', rather being an integral and celebrated part of Ubuntu.

LTSP is obviously a wider concern than Ubuntu.  It isn't developed by Ubuntu, but by a wider community.  I guess that's why LTSP can't be guaranteed.  It's part of Linux, and so Canonical cannot guarantee how it will be developed.

There is, though, no reason to think the worst; and it is very much an integral part of Edubuntu, if that's any reassurance...

---


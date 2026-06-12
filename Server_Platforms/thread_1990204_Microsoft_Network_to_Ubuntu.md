---
title: "Microsoft Network to Ubuntu"
date: 2012-05-29
forum: Server Platforms
---

### Post by sergiofm on 2012-05-29
Hi,

I have a network with multiple servers and about 700 pc´s all microsoft's and I wanted to change everything for Unbuntu. Is there a manual for this change? Any articles?

Tanks

Sérgio Marques

---

### Post by codemaniac on 2012-05-29
Hello sergiofm,
Welcome to the UbuntuForums !!

Yes you can always replace your windows PC's with Ubuntu , however installing it on 700 pc's would be a herculian task .
However if you want to automate the administration activities to all your systems at network , PUPPET can be a good choice .
Here is a reading for you .
[https://help.ubuntu.com/11.04/serverguide/puppet.html](https://help.ubuntu.com/11.04/serverguide/puppet.html)

---

### Post by sergiofm on 2012-05-29
Hi,

I will not change everything at once, it will be slowly. I would liked to have information to guide me.

---

### Post by LHammonds on 2012-05-29
Sounds like an interesting project and I'd like to see how it turns out for you.

I would imagine the conversion completely depends on what servers/services you are providing right now.

Although I have not done such a thing, I would imagine the desktops would be the last thing converted.

Changing file and print services is easy.  Converting user accounts from Windows Active Directory may be a bit tricky.

It would be fairly impossible for my company to switch out 100% because we rely on so many Windows-specific applications and hardware that requires interactions with Windows systems.

You might want to check out Zentyal.org and have a look at their Ubuntu-based server that is targeted as a replacement for Microsoft's Small Business Server edition.

LHammonds

---

### Post by SeijiSensei on 2012-05-30
1) Converting servers is the least disruptive thing you can do because it won't affect the users directly.  I'd start by trying to set up Samba to replace any file and print sharing you are using.  With 700 users you'll need a network authentication mechanism like OpenLDAP or NIS.  Samba 4 might be an alternative, but it's still considered too unstable for production environments.

2) Once you decide to tackle the desktops, I'd start with a small, tech-savvy department that are willing to be guinea pigs.  

3) Remember that one of the biggest obstacles you'll face isn't technological, but human.  Expect to spend a lot of time running user re-training sessions, and have people available to work with users at their desks.  Training can easily require much more time than you'll spend actually converting machines from Windows to Linux.  Technical people usually vastly underestimate how difficult transitions like these are for ordinary people.  Just moving someone used to working with Word 2010 to Libre Office Writer 3 can be a substantial task.

---

### Post by sergiofm on 2012-05-31
Hi,

I am aware that it will be difficult and time consuming, I will start by a department and then if all goes well go to another department. I really liked was information on how to make the switch to Ubuntu, books, articles, etc ...

Thanks you all for the replies

---

### Post by codemaniac on 2012-05-31
> **sergiofm said:**
> Hi,

I am aware that it will be difficult and time consuming, I will start by a department and then if all goes well go to another department. I really liked was information on how to make the switch to Ubuntu, books, articles, etc ...

Thanks you all for the replies

There are array of documentation out here on Ubuntu deployment.
Here are some for you .
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by SeijiSensei on 2012-06-01
On the server side, you can't go wrong with the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/index.html).  If you've never configured a Linux-based TCP/IP network before, I'll also recommend Craig Hunt's [TCP/IP Network Administration](http://shop.oreilly.com/product/9780596002978.do) to help you through the arcana of things like DNS servers.  It might be a bit dated, but most of the fundamentals haven't changed in years.

Transitions like yours are often determined mostly by what software your users need to do their work.  If you have lots of proprietary Windows-based applications, moving to Linux will be difficult at best and perhaps impossible for all practical purposes.  If most of your applications are platform-independent, like web applications, the transition will be much easier.  Tasks like accounting are often the most difficult functions to replace with Linux because the Windows software is generally superior and well-supported.  What software your accountant wants your company to use is often the most important criterion.

One way you can begin the transition even before introducing Linux on the desktop is to encourage people to use platform-independent software like Libre Office, Firefox and Thunderbird on their Windows machines today.  If you can move a good chunk of your Windows users now to the applications they'll be using on Linux, it'll make life much easier when you begin replacing the desktop OS as well.

---


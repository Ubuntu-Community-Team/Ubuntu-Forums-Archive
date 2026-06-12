---
title: "Anonymity"
date: 2008-10-16
forum: Security
---

### Post by Chamillionaire2 on 2008-10-16
Hello,

Basically is there any ip hiding software for ubuntu? not just for web browsing IE thourgh firefox, thourgh everything,

i did find tor on a google search but it were a little difficult to install, is there any easy ones to setup?

Thanks bye.

---

### Post by cariboo on 2008-10-16
Tor is available in the repositories, go to System-->Administration-->Synaptic Package Manger and search for tor. Synaptic will install tor for you. I you are looking for a program and find it through a search engine check synaptic first before downloading it. There are over 12,000 packages listed in the repositories, most normal applictions will be listed.

Jim

---

### Post by Chamillionaire2 on 2008-10-16
> **cariboo907 said:**
> Tor is available in the repositories, go to System-->Administration-->Synaptic Package Manger and search for tor. Synaptic will install tor for you. I you are looking for a program and find it through a search engine check synaptic first before downloading it. There are over 12,000 packages listed in the repositories, most normal applictions will be listed.

Jim

I searched in syntax manager but i coudent find anything. is there another way i could get it?

---

### Post by panhandle on 2008-10-17
open a terminal, type:

> sudo apt-get install tor

---

### Post by daleus on 2008-10-17
> **Chamillionaire2 said:**
> I searched in syntax manager

This has to be a troll...

---

### Post by Chamillionaire2 on 2008-10-17
> **daleus said:**
> This has to be a troll..

wtf? I searhec Tor in the manager thing but it dident come up with anything,

leave it ill have to look for a diffrent way :)

---

### Post by cdenley on 2008-10-17
System>Administration>Software Sources
Make sure "Community-maintained Open Source software (universe)" is checked.

Open a terminal
Applications>Accessories>Terminal

type these commands
```

sudo apt-get update
sudo apt-get install tor

```

You may have to configure privoxy to use tor, then configure whatever you want to use privoxy.
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
System>Preferences>Network Proxy

Tor does NOT make it impossible for anyone to read your traffic, just for people between you and your ISP. Your traffic can still be traced to you if the attacker happens to control the first and last node your traffic goes through (very unlikely). Make sure you read this.
[http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)

---

### Post by mikeymike11 on 2013-01-01
> **cdenley said:**
> System>Administration>Software Sources
Make sure "Community-maintained Open Source software (universe)" is checked.

Open a terminal
Applications>Accessories>Terminal

type these commands
```

sudo apt-get update
sudo apt-get install tor

```

You may have to configure privoxy to use tor, then configure whatever you want to use privoxy.
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
System>Preferences>Network Proxy

Tor does NOT make it impossible for anyone to read your traffic, just for people between you and your ISP. Your traffic can still be traced to you if the attacker happens to control the first and last node your traffic goes through (very unlikely). Make sure you read this.
[http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)
hey,
you shouldnt do it that way. If you go to [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu) you will see that they recommend you settingup a repository (setting, repositories,) in synaptic. they provide the settings info. but what the hell you do after that, i have no idea. reload?

---

### Post by sffvba[e0rt on 2013-01-01
*Back to sleep **old **thread.*


404

---


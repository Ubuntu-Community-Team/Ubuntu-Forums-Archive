---
title: "Firestarter"
date: 2009-03-02
forum: Security
---

### Post by ultimate_aektzis on 2009-03-02
Hi guys,

I want to ask a simple question.I have installed firestarter in my ubuntu.But, as I can see, it doesn't launch on startup.How can I achieve this?

thanks in advance

---

### Post by bodhi.zazen on 2009-03-02
Firestarter is, IMO , somewhat outdated. although it still works , really you should look at an alternate 9firestarter is no longer maintained and it is starting to show it's age as your thread shows).

Your options are ufw (gui front end == gufw) , guard dog (nice built in help), and learning iptables.

iptables takes some time, but once you learn it is quite powerful.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

For ufw : [Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by CAPLinux on 2009-03-02
> **ultimate_aektzis said:**
> Hi guys,

I want to ask a simple question.I have installed firestarter in my ubuntu.But, as I can see, it doesn't launch on startup.How can I achieve this?

thanks in advance

Ultimate,

I at first had the same question, but what I had to learn is the fact that Firestarter is not a Firewall.  It is only a GUI front-end to IPTables.  Realize IPTables is always running on startup.  You really don't need Firestarter to launch on startup.

As an aside, IPTables is always set by default to block everything, from the begining.  You really don't even need Firestarter to properly configure IPTables. It is set to block every port by default.

Hope this helps!

---

### Post by ultimate_aektzis on 2009-03-02
Yeah.Both answers are very useful.Thanks guys.CAPLinux, I know that iptables does the whole job but I didnt thnk it that way.I am reading ufw documentatin now, an d I will come back for any questions:D

---

### Post by ultimate_aektzis on 2009-03-02
Ok, I have one question.I know that is good to learn iptables, but I dont have the required time.Is there any way to allow access to the "typical" apps that need the internet (eg.browsers,IM clients etc)?I dont think that commands like this

```
sudo ufw delete allow from 192.168.0.0/24 to any port 22
```

will help me this time.

---

### Post by bodhi.zazen on 2009-03-02
Yes, install gufw, it is a graphical front end.

@CAPLinux: By default with ubuntu iptables is permissive.

```
sudo iptabels -L
```will show all traffic is allowed.

all the tools merely configure iptables as you say and your point gufw and firestarter and guard dog, none of these tools should be run all the time.

Configure your firewall and close the gui tool ;)

---

### Post by ultimate_aektzis on 2009-03-02
Do I install it by

```
sudo apt-get install gufw

```

??

Cant find the package...

---

### Post by cdenley on 2009-03-02
> **ultimate_aektzis said:**
> Ok, I have one question.I know that is good to learn iptables, but I dont have the required time.Is there any way to allow access to the "typical" apps that need the internet (eg.browsers,IM clients etc)?I dont think that commands like this

```
sudo ufw delete allow from 192.168.0.0/24 to any port 22
```

will help me this time.

If you choose UFW, it does not filter outgoing connections, so all your software will be able to establish connections over the internet.

---

### Post by cdenley on 2009-03-02
> **ultimate_aektzis said:**
> Do I install it by

```
sudo apt-get install gufw

```

??

Cant find the package...

If you're using hardy 8.04, then you have to enable backports in "/etc/apt/sources.list". GUFW was not in the repos when hardy was released.

---

### Post by bodhi.zazen on 2009-03-02
> **ultimate_aektzis said:**
> Do I install it by

```
sudo apt-get install gufw

```??

Cant find the package...

What version of Ubuntu are you on ? More recent versions gufw is in the repos.

If you are on 8.04 see :

[http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04](http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04)

---

### Post by ultimate_aektzis on 2009-03-02
Is it impossible to get it from repos?I have to check frequently for updates if I install it by myself:confused:

-----------------------

i run hardy heron

---

### Post by bodhi.zazen on 2009-03-02
As has been suggested you can try backports.

Otherwise I doubt it is *that* much hassle to check for updates from time to time. I seriously doubt it is critical to update immediately, especially if it is working.

---

### Post by ultimate_aektzis on 2009-03-02
Ok, I have downloaded gunfw.Is there any tutorial for help?

---

### Post by sanath1978 on 2009-03-03
Thanks.

---


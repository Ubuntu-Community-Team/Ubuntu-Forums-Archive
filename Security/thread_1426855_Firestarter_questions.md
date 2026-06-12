---
title: "Firestarter questions"
date: 2010-03-10
forum: Security
---

### Post by Sir Jasper on 2010-03-10
Hi,

I am very happy with iptables and have only made one change since I set it up with Firestarter about one year ago.

Firestarter seems to have achieved all I wanted it to (perhaps that is my deficiency) so I am not at all clear as to why UFW is more effective (though it may be more convenient). 

Also, as Firestarter is a front end I assume (perhaps wrongly) if I were to uninstall it my iptables settings would remain as is.

My regards

---

### Post by bodhi.zazen on 2010-03-10
> **Sir Jasper said:**
> Hi,

I am very happy with iptables and have only made one change since I set it up with Firestarter about one year ago.

Firestarter seems to have achieved all I wanted it to (perhaps that is my deficiency) so I am not at all clear as to why UFW is more effective (though it may be more convenient). 

Also, as Firestarter is a front end I assume (perhaps wrongly) if I were to uninstall it my iptables settings would remain as is.

My regards

If firestarter works for you there is no reason not to use it.

If, however, if you run into bugs, you could have a problem as the project is no longer active, and although the package is available, bug reports go unanswered:

[https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter](https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter)

As you can see, not much activity since 2007 ...

The current release of firestarter was released in 2005

[http://sourceforge.net/projects/firestarter/files/](http://sourceforge.net/projects/firestarter/files/)

ubuntu has moved to ufw, and for the vast majority of desktop users ufw is fine.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

So if you ever need a replacement, you may want to look at UFW.

In terms of conflicts, if you remove Firestarter you need to purge it, or the config file remains in place and conflicts with other fire wall front ends, such as gufw.

---

### Post by Sir Jasper on 2010-03-10
Hi bodhi,

Thank you for your detailed and helpful explanation and also for your ¨purge¨ tip.

My regards

---

### Post by bodhi.zazen on 2010-03-10
> **Sir Jasper said:**
> Hi bodhi,

Thank you for your detailed and helpful explanation and also for your ¨purge¨ tip.

My regards

You are most welcome, hope that explains the firestarter vs ufw debates the flair from time to time.

Many many use firestarter without a problem, but over time, problems occur from time to time and the only solution is to migrate to GUFW.

Too bad at times it turns to a flame fest , lol.

---

### Post by Sir Jasper on 2010-03-10
Hi again bodhi,

I have now viewed all the links you so kindly provided and I would be most concerned about the Firestarter bugs except that when I boot Firestarter tries to load, but it is automatically disabled.

You have also given me food for thought and so if I experience a problem with any package I will see if I can track down a relevant bug report summary and/or try to find something you have written.

My regards

---

### Post by bodhi.zazen on 2010-03-10
If you are having problems with firestarter, purge both firestarter and ufw, then re-install firestarter.

If you are still having problems, post back.

Note: I am going to split our conversation to it's own thread =)

---

### Post by Sir Jasper on 2010-03-10
Hi bodhi,

I don´t currently have a Firewall problem and I do not think one will arise with the benefit of your above advice.

However, others forum users may also find your extensive explanations and links of considerable benefit so making this a separate thread can only be useful.

My regards

---

### Post by bodhi.zazen on 2010-03-10
> **Sir Jasper said:**
> Hi bodhi,

I don´t currently have a Firewall problem and I do not think one will arise with the benefit of your above advice.

Ah, glad to learn you are NOT having a problem.

If it is not broken, don't fix it.

---


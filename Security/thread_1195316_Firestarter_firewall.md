---
title: "Firestarter firewall"
date: 2009-06-23
forum: Security
---

### Post by And-car on 2009-06-23
I'm a newbie to 8.04 Hardy Heron. Just looking at Firestarter, I can configure it OK and get an icon at top of screen confirming it's on. If I then exit the program the icon disappears, does this mean the firewall is now off? I wondered if Lock would say keep it on but not sure what that does. Can you advise pls?

---

### Post by catelee2u on 2009-06-23
Go into preferences and select the interface tab and check the option to display tray icon. It'll show up then.

Also if you want the program to load up at startup with no hassles....this page explains it really well and clearly.
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php) 

The line that says:
username ALL= NOPASSWD: /usr/bin/firestarter 

should say:

username ALL= NOPASSWD: /usr/sbin/firestarter

as Ubuntu is Debian based. 

It's a really great firewall. The help file on the website is fantastically clear...which it needs to be for me ;-)

---

### Post by lovinglinux on 2009-06-23
> **And-car said:**
> If I then exit the program the icon disappears, does this mean the firewall is now off?

No. You can and you should close Firestarter after configuring it, due to security reasons. Firestarter is just a graphical interface to create rules for iptables (the real firewall), so when you close it, the firewall will still work on the background. As far as I know, you don't even need to start it again on next boot, unless you need to change the rules.

Nevertheless, Firestarter is not recommended anymore. Ubuntu comes with UFW (Uncomplicated Firewall) installed by default, but inactive. It is another firewall manager, like Firestarter. If you want a graphical interface, then you can install [gufw](apt:gufw) [apt-get]. But first remove Firestarter. To do this Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get purge firestarter && sudo apt-get install ufw gufw
```

This command will purge firestarter application, including settings and then install ufw and gufw. Since ufw is installed by default you will get a message saying that it is the newest version. I included it just in case.

To configure ufw, open "System >> Administration >> Firewall Configuration".

I think you should at least try it, to see your options. Gufw is pretty simple to configure.

---

### Post by And-car on 2009-06-24
Thanks people.

---

### Post by shane2peru on 2009-06-24
> **lovinglinux said:**
> No. You can and you should close Firestarter after configuring it, due to security reasons. Firestarter is just a graphical interface to create rules for iptables (the real firewall), so when you close it, the firewall will still work on the background. As far as I know, you don't even need to start it again on next boot, unless you need to change the rules.

Nevertheless, Firestarter is not recommended anymore. Ubuntu comes with UFW (Uncomplicated Firewall) installed by default, but inactive. It is another firewall manager, like Firestarter. If you want a graphical interface, then you can install [gufw](apt:gufw) [apt-get]. But first remove Firestarter. To do this Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get purge firestarter && sudo apt-get install ufw gufw
```

This command will purge firestarter application, including settings and then install ufw and gufw. Since ufw is installed by default you will get a message saying that it is the newest version. I included it just in case.

To configure ufw, open "System >> Administration >> Firewall Configuration".

I think you should at least try it, to see your options. Gufw is pretty simple to configure.

Thanks for this info!  I have always been a gui kind of person for firewalls.  I was always a fan of Firestarter too, but knew it had been replaced with ufw.  I didn't know that gufw existed!  Thanks.

Shane

PS  I like the little icon tray thing makes me feel better to see it up and running. :)

---

### Post by lovinglinux on 2009-06-24
> **shane2peru said:**
> Thanks for this info!  I have always been a gui kind of person for firewalls.  I was always a fan of Firestarter too, but knew it had been replaced with ufw.  I didn't know that gufw existed!  Thanks. PS  I like the little icon tray thing makes me feel better to see it up and running. :)

You are welcome. I also was a gui person, but now I'm hooked to the cli. I create my own iptables rules now and use [iptstate](apt:iptstate) [apt-get] on terminal screenlet for monitoring connections and the command below on another terminal screenlet to monitor blocked connections ;)

```
tail -f /var/log/kern.log | grep eth0
```

---

### Post by shane2peru on 2009-06-24
> **lovinglinux said:**
> You are welcome. I also was a gui person, but now I'm hooked to the cli. I create my own iptables rules now and use [iptstate](apt:iptstate) [apt-get] on terminal screenlet for monitoring connections and the command below on another terminal screenlet to monitor blocked connections ;)

```
tail -f /var/log/kern.log | grep eth0
```

Don't get me wrong I love cli, I just have never taken the time to learn iptables. BTW, somehow (my lack of knowledge of iptables probably) ufw or gufw broke my Gyachi connection to Yahoo IM.  Empathy won't connect either and neither will pidgin.  However Swiftfox does when I disable the gufw.  Help what I have done this time???

Shane

---

### Post by shane2peru on 2009-06-24
Ooops,  I guess it wasn't me this time. :)  Here was my problem:

[http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

If anyone else has this problem.  That link should fix it.

Shane

---


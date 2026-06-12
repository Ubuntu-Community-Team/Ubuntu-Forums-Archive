---
title: "Fedora Firewall in Ubuntu?"
date: 2008-07-02
forum: The Cafe
---

### Post by Lord Xeb on 2008-07-02
Anyway to do this?

---

### Post by LaRoza on 2008-07-02
Any way to do what?

Use Fedora's firewall? I don't know. What does Fedora use?

---

### Post by JetskiDude911 on 2008-07-02
Doesn't Fedora use SELinux?

---

### Post by Lord Xeb on 2008-07-02
I believe so... SElinux in Ubuntu? >_> As if that is going to happen. I got to make a whole new kernal... I think.

---

### Post by Kingsley on 2008-07-02
Fedora has SELinux and something else that's a separate firewall AFAIK. It's called system-config-firewall.py 1.2.9.

Edit: I did a little bit of googling and found out system-config-firewall is just a frontend to iptables.

---

### Post by Lord Xeb on 2008-07-02
Can I put that into Ubuntu?

---

### Post by ibutho on 2008-07-02
> **Lord Xeb said:**
> Can I put that into Ubuntu?
You could do, but you may have to port it to Ubuntu on your own if someone else hasn't already done so. Alternatively you could use ufw, shorewall, guarddog or any of the other iptables frontends available for Linux.

---

### Post by Lord Xeb on 2008-07-02
> **ibutho said:**
> You could do, but you may have to port it to Ubuntu on your own if someone else hasn't already done so. Alternatively you could use ufw, shorewall, guarddog or any of the other iptables frontends available for Linux.

Yes I could but I like the layout and simplicity of Fedora's firewall. I have already tried to port it in but I haven't been able to yet.

---

### Post by nick09 on 2008-07-02
You could try firestarter from the repos.

---

### Post by macogw on 2008-07-02
Gah, the misinformation is astounding!

SELinux is *not* a firewall.  It's an attempt at improving on the owner, group, world permissions model.  It has nothing to do with networking.

Iptables is the firewall in every single Linux distro there is.

Firestarter is *not* a firewall.  It's just a GUI to configure iptables.  Ubuntu also includes ufw (uncomplicated firewall) which is a wrapper for iptables with simpler syntax, similar to OpenBSD's ipfw syntax.

---

### Post by stmiller on 2008-07-02
Yes Redhat/Fedora's firewall interface is nice. Even the terminal version is clear and easy to use.

I'm actually surprised that Ubuntu has been here for so long and not written their own firewall GUI of some kind, or just adopted redhat's. 

It seems to be a critical system component these days.

---

### Post by macogw on 2008-07-03
> **stmiller said:**
> Yes Redhat/Fedora's firewall interface is nice. Even the terminal version is clear and easy to use.

I'm actually surprised that Ubuntu has been here for so long and not written their own firewall GUI of some kind, or just adopted redhat's. 

It seems to be a critical system component these days.

Why write a new one when Firestarter exists for simple stuff or Guarddog if you want to get really advanced?  Ubuntu's already gone and created a simplified command line interface for iptables.

---

### Post by pferpaddy on 2008-07-03
yeah SElinux is nothing to do with firewalls and ubuntu comes with its own firewall so just download firestarter to configure it 
good luck

---

### Post by kevdog on 2008-07-03
macogw

Wow -- such an outburst -- I've never seen that before.  Just edit the d**n IPtables by hand.  Its not that hard, and its way more powerful.  Firestarter gives you a limited set of commands.  Guarddog is definitely an improvement over Firestarter, however its KDE based -- too bad!!  ufw -- if you going to go through all the trouble to learn its syntax, you might as well learn iptables syntax instead.  Here is a great tutorial:

[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by Iandefor on 2008-07-03
> **Lord Xeb said:**
> Anyway to do this?There's nothing especially "Fedora"-ey about the firewall in Fedora. It's just iptables.

If you want a simple frontend, I recommend using Ubuntu's ufw.

If you meant the GUI configuration tool called system-config-firewall, you can grab the SRPM's off the Fedora build system: [http://koji.fedoraproject.org/koji/packageinfo?packageID=4912](http://koji.fedoraproject.org/koji/packageinfo?packageID=4912).

---

### Post by ibutho on 2008-07-03
> **macogw said:**
> Why write a new one when Firestarter exists for simple stuff or Guarddog if you want to get really advanced?  Ubuntu's already gone and created a simplified command line interface for iptables.

It would be nice if they included a GUI frontend by default (not necessarily Fedora, which I agree is very good) and an option to enable the firewall right from the start (during install time or first boot).

---

### Post by macogw on 2008-07-04
> **ibutho said:**
> It would be nice if they included a GUI frontend by default (not necessarily Fedora, which I agree is very good) and an option to enable the firewall right from the start (during install time or first boot).
Since nothing listens on any ports by default, it's effectively the same as having drop all.

---

### Post by Lord Xeb on 2008-07-04
Problem is that I do not understand the command line interface e_e Also, the GUI interface with Fedora's firewall is awesome and I would like it in Ubuntu.

---

### Post by macogw on 2008-07-04
> **Lord Xeb said:**
> Problem is that I do not understand the command line interface e_e Also, the GUI interface with Fedora's firewall is awesome and I would like it in Ubuntu.

Have you at least *tried* Firestarter? It's very easy to use.

Most people don't understand iptables, I don't think.  I've edited the /etc/sysconfig/iptables/iptables.conf (I think?) in Red Hat, but it's a pain.  That's why we have ufw for a simple command line way to do it.

---

### Post by PmDematagoda on 2008-07-05
> **Lord Xeb said:**
> I believe so... SElinux in Ubuntu? >_> As if that is going to happen. I got to make a whole new kernal... I think.

It can be done very easily since the Linux kernel has SELinux built-in to it, so the Ubuntu kernel has the capability to use SELinux(I believe SELinux is enabled) so that you only need to install the SELinux packages, so yes, it has already happened a long time back. The only problem comes when trying to configure SELinux although it should be easy to use after you get used to it.

---

### Post by Lord Xeb on 2008-07-05
I got it installed using alien, now how do I configure it? (I installed it using the command "dpkg -i file_created_by_alien)

---

### Post by Iandefor on 2008-07-05
Try > /usr/bin/system-config-firewall

---

### Post by Lord Xeb on 2008-07-05
```
nathan@Omnious:~$ /usr/bin/system-config-firewall
bash: /usr/bin/system-config-firewall: No such file or directory

```

---

### Post by fjf on 2008-07-06
Firestarter is nice, but it doesnt work in hardy.  It says:  "device eth0 not ready" in my machine.

---

### Post by Lord Xeb on 2008-07-06
I use gutsy. Hardy makes my machine run slower and hotter e_e. I got the fedora thingy installed, now I need to know how to configure it

---


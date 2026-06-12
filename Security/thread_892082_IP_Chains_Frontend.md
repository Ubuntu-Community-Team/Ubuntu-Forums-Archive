---
title: "IP Chains Frontend"
date: 2008-08-16
forum: Security
---

### Post by devil81 on 2008-08-16
Hi:

My PC is behind a router with an inbuilt firewall so I know that a software firewall or GUI frontend to IP chains is not necessary but I prefer to air on the side of caution, once bitten, twice shy and all that.

I have configured IP chains manually via the CLI successfully but in the main I found it overly complex and convulted having to always remember the correct syntax and placement.

So what I really want is a GUI front that is:

Configurable with the minumal clicking and typing
Is also clearly laid out and intuitive to use

Many Thanks.

---

### Post by brian_p on 2008-08-16
> **devil81 said:**
> Hi:

My PC is behind a router with an inbuilt firewall so I know that a software firewall or GUI frontend to IP chains is not necessary but I prefer to air on the side of caution, once bitten, twice shy and all that.

Ah, you're a belt and braces person then. Very wise. You never know when these inbuilt firewalls will let a packet or two slip through when you're not looking.

> I have configured IP chains manually via the CLI successfully but in the main I found it overly complex and convulted having to always remember the correct syntax and placement.

So what I really want is a GUI front that is:

Configurable with the minumal clicking and typing
Is also clearly laid out and intuitive to use

Firestarter is very popular. I'm very surprised you didn't come across it in your search of these forums. ufw also has a gui, gufw I think. Also, you could do a search on your machine with the intuitive command:

```
apt-cache search firewall
```

Very little typing and just one key press.

---

### Post by pparks1 on 2008-08-16
Firestarter was going to be my recommendation as well.   Although, the ucf (uncomplicated firewall) GUI is pretty non-intimidating if you have some rough idea of what you are doing.

---

### Post by jerome1232 on 2008-08-17
I would personally recommend UFW just because firestarter is dead. Honestly ufw is very easy

```
sudo ufw default deny
sudo ufw logging on
sudo ufw allow 22 (or whatever port you want)
sudo ufw enable
```

It's syntax can get *slightly* more advanced than that but not much. Once you enable it you never have to think about it again.

(I know you said gui but I've never used the gui version just don't see the need)

---

### Post by Vivaldi Gloria on 2008-08-17
> **jerome1232 said:**
> i would personally recommend ufw just because firestarter is dead. Honestly ufw is very easy


+1

---

### Post by devil81 on 2008-08-19
Thanks to everyone for the kind help, in the end, I decided to go with Firestarter as it seemed to be the easiest one out of the many choices.

---


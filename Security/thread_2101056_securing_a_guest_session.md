---
title: "securing a guest session"
date: 2013-01-03
forum: Security
---

### Post by Charles-2007 on 2013-01-03
First, the objective:  logon to 12.04 or later using the native non-persistent GUEST session but only permit access to specific web sites.  The limits need to be configured in the PC (not on the local network).

If GUEST is non-persistent, can I configure either the innate firewall or use a proxy like Privoxy (which can blacklist everything except sites on its whitelist) despite the guest session's lack of persistence?

Thanks for any direction you can provide.

---

### Post by thnewguy on 2013-01-03
Do you want to block these same websites for all users, or just the ones logged in using the Guest account? If you want to block all accounts, then you might look at setting up a domain blocker or adding the sites you want to block to the /etc/hosts file. On the other hand, just blocking access to sites from one account is tricky, especially since the account and its settings will be wiped. Add to that anyone with some technical skills will probably get around a block using a web proxy or Tor or similar technology makes this a bit of an uphill battle.

---

### Post by unspawn on 2013-01-03
> **Charles-2007 said:**
> If GUEST is non-persistent, can I configure either the innate firewall or use a proxy like Privoxy (which can blacklist everything except sites on its whitelist) despite the guest session's lack of persistence?
Apart from what a separate home mount point, container, virtualization, cgroups, GRSecurity-reinforced TPE (exec) plus jail or SELinux sandbox may offer (vs stock installation) wrt account isolation plus the fact you'll be sacrificing a Privoxy instance for solely this UID, I'd use the firewall in conjunction with Privoxy. The guest session's lack of persistence could be partially overcome if you could trigger a script on account creation that disables unrestricted Sudo for the account, sets immutable proxy environment variables for the UID, uses the iptables "owner" module to set per-UID rules blocking egress traffic, only allowing HTTP(S) through the proxy and logs account activity (Rootsh, audit service, LOG target rules). The latter is important because it helps you analyze what measures to add or adjust.

---

### Post by Charles-2007 on 2013-01-04
I'm going to work this up on both a guest (non-persistent) account as well as a generic user account and see what happens better.  I'll post my results.  I am particularly interested in the guest mode as it will autodestruct changes on logout.

There are some tools in the Gnome environment that might help as well as some tutorials for the XFCE desktop about locking stuff down.  There are references to KDE "kiosks" but no good howto's, and I found Kubuntu to be a little buggy.

Alan writes about building kiosk iso's elsewhere in these forums, but what he can do is beyond my skill level.

There is actually a pre-built Fedora kiosk iso but it is not 32 bit.

Yes there is Webconverger but it requires an ongoing subscription and I can't figure out how to install the free version.  The best pre-built kiosk I've seen is Linutop which is around 79 Euros for the software.  Guess what Linutop is?  XFCE Xubuntu with a lot of config edits!

Best wishes.

---

### Post by Charles-2007 on 2013-01-04
Oh, if you are wondering what I am doing (and I see via Google that lots of folks are trying to do the same), I am attempting to build an OPAC station (library catalog) for a modest church library.

Our librarians wanted to load our titles into a database that folks could browse at home (and pitch the card catalog).  There are several good database programs available for free.  Our web host (we have plain old shared hosting) let me install OpenBiblio on our domain's space (which was not hard) and it works very well.  Probably the most popular is Koha but I could not figure out how to do this quickly unless we did it with a server under our direct control.

Now we need a computer that can sit unattended in a church library to replace the (departing) hardcopy records.  We are full of kids, and, as the father of mischievous teenagers myself, the device needs to be somewhat hardened.

The PC will sit on the church's ethernet network (plain ethernet DHCP) and the rest of the network (other than firewalls etc on the individual workstations) doesn't need restrictions, and so I am hesitant to suggest an upstream control.

This project may get dropped in the future so I am not interested in committing to a subscription-model solution.

Best wishes.

---

### Post by Frogs Hair on 2013-01-04
I don't know that you would be able to save any settings in the Guest Session, but a user account with auto login allow you to accomplish what you want. I know that on my computer the guest session doesn't even save theme settings.

---

### Post by sudodus on 2013-01-04
> **Charles-2007 said:**
> ...
Yes there is Webconverger but it requires an ongoing subscription and I can't figure out how to install the free version.  The best pre-built kiosk I've seen is Linutop which is around 79 Euros for the software.  Guess what Linutop is?  XFCE Xubuntu with a lot of config edits!
Best wishes.
You can run Webconverger as a live system. It is not necessary to install it. The iso file download is free (but you must bear with the nagging home page).

Furthermore, on the web site it is written, that you can download the source  code. So if you want to and know how to, you can compile it and of course later on tweak it on the source code level.

---

### Post by sudodus on 2013-01-04
> **Charles-2007 said:**
> Oh, if you are wondering what I am doing (and I see via Google that lots of folks are trying to do the same), I am attempting to build an OPAC station (library catalog) for a modest church library.

Our librarians wanted to load our titles into a database that folks could browse at home (and pitch the card catalog).  There are several good database programs available for free.  Our web host (we have plain old shared hosting) let me install OpenBiblio on our domain's space (which was not hard) and it works very well.  Probably the most popular is Koha but I could not figure out how to do this quickly unless we did it with a server under our direct control.

Now we need a computer that can sit unattended in a church library to replace the (departing) hardcopy records.  We are full of kids, and, as the father of mischievous teenagers myself, the device needs to be somewhat hardened.

The PC will sit on the church's ethernet network (plain ethernet DHCP) and the rest of the network (other than firewalls etc on the individual workstations) doesn't need restrictions, and so I am hesitant to suggest an upstream control.

This project may get dropped in the future so I am not interested in committing to a subscription-model solution.

Best wishes.
In a fairly standard router you can block services (think of internet access) for a certain IP number (or group of IP numbers). This is an easy way to block that particular computer and all its users from the internet. And I guess you could dedicate an old (unattractive) computer for your members to browse the library catalogue.

---

### Post by Ms. Daisy on 2013-01-04
Why don't you just remove the guest account altogether and create a separate, non-sudo user? Then make all the dansguardian (or whatever) configurations you want to that user account and it will be persistent. You could probably also have the sudo account hidden at login so that the only apparent account is the non-sudo one with the proxy.

---

### Post by Charles-2007 on 2013-01-07
I am working this up via both a guest session as well as a user session to see which seems more hardened.  In XFCE there are some kiosk settings and I will look at whether or not these persist in a non-persistent guest session.

---

### Post by Charles-2007 on 2013-01-13
Wow "guest" is exquisitely hard to lock down.  Yes it seems easier to create a user in an XFCE (Xubuntu) desktop and lock the panels.  Evidently this was easier in older XFCE.  Then whitelist/blacklist in IP tables or host files.  I will post how I did it once I think I have it.

Best wishes.

---

### Post by Charles-2007 on 2013-02-06
My HOWTO is posted here:

[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)

---


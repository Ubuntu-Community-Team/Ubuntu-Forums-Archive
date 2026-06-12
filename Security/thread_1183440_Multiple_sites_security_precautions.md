---
title: "Multiple sites security precautions"
date: 2009-06-10
forum: Security
---

### Post by markvdm on 2009-06-10
Hi Guys

Apologies if this is a daft question, but if I don't ask I won't know, so here goes...

I have installed 9.04 through WUBI on my work laptop, which runs Vista. No separate partition for Ubuntu, just installed on Vista partition. I work on multiple customer sites, and connected to the net practically permanently, and I'm worried about both picking something up (virus, malware etc) and/or unintentionally passing something on when using Ubuntu. I hardly boot up Vista anymore.

What precautions/software can you guys recommend to help minimise this risk? I know most things won't break Ubuntu, but I'd like to help by not passing anything on either.

---

### Post by marshall.robert on 2009-06-10
The only thing I can think of is ClamAV. There are others like Avast and AVG but they dont offer a graphical based system.

---

### Post by HermanAB on 2009-06-10
Howdy,

Install ClamWin on Vista.  Don't worry about Ubuntu.  Please ensure that you use decent passwords at least 9 charaters in length for ALL user accounts and don't use FTP, Telnet or VNC servers - use SSH.

---

### Post by markvdm on 2009-06-10
Thanks for the replies guys.

I have also installed Firestarter, but after doing so I was reading that it's not good to have the GUI running all the time as it runs as a root user. Any thoughts on this? Also, if the GUI is not running, is there a way I can check that the firewall is still active and using the settings I have requested?

If there is a better application, then also by all means let me know.

This is the most I have used Linux. I usually get upset by some small issue, that I'm in too much of a rush to have working and just go back to Vista, but so far it's been almost 2 weeks without having to do that... lol... baby steps here ;)

---

### Post by bodhi.zazen on 2009-06-10
> **markvdm said:**
> Thanks for the replies guys.

I have also installed Firestarter, but after doing so I was reading that it's not good to have the GUI running all the time as it runs as a root user. Any thoughts on this? Also, if the GUI is not running, is there a way I can check that the firewall is still active and using the settings I have requested?

If there is a better application, then also by all means let me know.

This is the most I have used Linux. I usually get upset by some small issue, that I'm in too much of a rush to have working and just go back to Vista, but so far it's been almost 2 weeks without having to do that... lol... baby steps here ;)

I suggest you use ufw or learn iptables directly.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

you will have to remove (purge) firestarter.

Your firewall is iptables, firestarter , gufw, ufw, guraddog, etc are simply gui tools.

To see your firewall in action :

```
sudo iptables -L -v
```

You can use a gui tool if you wish, simply ssh -X (forward X applications).

If you use a gui tool, configure  your firewall and close it.

---

### Post by ibuclaw on 2009-06-10
> **bodhi.zazen said:**
> I suggest you use ufw or learn iptables directly.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

you will have to remove (purge) firestarter.

Your firewall is iptables, firestarter , gufw, ufw, guraddog, etc are simply gui tools.

To see your firewall in action :

```
sudo iptables -L -v
```

You can use a gui tool if you wish, simply ssh -X (forward X applications).

If you use a gui tool, configure  your firewall and close it.

I fully support this information. :)

---


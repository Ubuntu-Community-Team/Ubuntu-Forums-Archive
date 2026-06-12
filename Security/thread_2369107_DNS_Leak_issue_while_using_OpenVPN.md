---
title: "DNS Leak issue while using OpenVPN"
date: 2017-08-18
forum: Security
---

### Post by eddie25 on 2017-08-18
I'm currently using Ubuntu 17.04, in the past I had issues with the /etc/resolv.conf file not updating correctly causing DNS leaks.  It was working correctly last week but found out yesterday I still had a DNS leak.  Not only is the /etc/resolv.conf not updating when I turn on my VPN but when I updated it manually I still have a DNS leak?

In the past, whenever I updated the /etc/resolv.conf manually it always fixed my DNS leak issues.

Anyway, this is what I'm doing?

In the terminal;
sudo nano \etc\resolv.conf
nameserver ip address of VPN

I save the file and went to [https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)

Everytime I do the standard test and extended test, it would show both my ISP IP address as well as my VPN IP address.

What I have done above has always worked in the past to fix a DNS leak issue.  Does anybody have any idea why it's showing IP addresses not listed in the \etc\resolv.conf file and what I need to do to resolve it?

Thanks in advance

---

### Post by #&amp;thj^% on 2017-08-18
This is how I configure mine: [http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html](http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html)
Good Luck, and tell us how it goes.

---

### Post by eddie25 on 2017-08-18
Thanks for the reply 1fallen,

Is there anyway to do this using network manager or openresolv just to make it easier? it was working with openresolv last week and for whatever reason it stopped so I tried network manager. I'm not the greatest using linux but apparently that is what is currently updating my \etc\resolv.conf file.

Also, have any idea's why it's no longer working when I just update the \etc\resolv.conf manually?

I did try your method adding:
[COLOR=#666666]script-security 2
[/COLOR]up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

[FONT=Verdana]to the opvn file and typed:
[/FONT]sudo openvpn --us545.nordvpn.com.tcp443.ovpn

I ended up with the following error:
Options error: Unrecognized option or missing or extra parameter(s) in [CMD-LINE]:1: us545.nordvpn.com.tcp443.ovpn (2.4.0)
Use --help for more information.

I had no clue what to do next.

---

### Post by #&amp;thj^% on 2017-08-19
To restart mine I simply use the network-manager via:
```
sudo service network-manager restart
```
And one thing that differs from mine is I don't use sudo to start my VPN Service.(Just to note only)

As for this:"**Options error: Unrecognized option or missing or extra parameter(s) in [CMD-LINE]:1: us545.nordvpn.com.tcp443.ovpn (2.4.0)**"
I've never seen this kind of error on my end so I'm not sure how to advise intelligently here, but a guess would indicate there is something wrong with the configs files,(Good place to start looking)
Might not hurt to brush up here: [https://nordvpn.com/tutorials/linux/](https://nordvpn.com/tutorials/linux/)
I find I over look the simple things when trouble shooting these matters.:D

---

### Post by eddie25 on 2017-08-21
After trying everything I could find via the internet, I gave up on Ubuntu 17.04. No matter what I did, I still had DNS leaks.

I ended up wiping my whole hard drive and installed Ubuntu 16.04.  

I reinstalled sudo apt-get install network-manager-openvpn-gnome and set up my VPN.

I still had DNS leaks but after installing:
apt-get install openresolv nscd unbound

I no longer had DNS leaks when checking with [https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)

Thanks

---

### Post by Billingd on 2017-12-21
Hi Eddie25 or Openresolv user

Do you have more details on how you used openresolv to fix this problem ? I have exactly the same DNS leak problem you describe with ubuntu 16.04. None of the fixes I have found online have worked. And when I change the vpn connection in network manager to use a different DNS (eg google public dns or opennic), then the DNSleaktest.com extended test reports a leakage via my ISPs DNS. So something not working at all right in 16.04

Many thanks


David

---

### Post by litlesam on 2017-12-21
Hi Billingd,

You really should have started your own thread but this is what I have done to get by this issue.

Install bind9

```
sudo apt install bind9
```

```
sudo /etc/init.d/bind9 restart
```

Then edit your network connection and set it to "Automatic (DHCP) address only"

Where it says "DNS servers" add "127.0.0.1" without the ""

Restart your Internet connection and check for DNS Leaks.

---

### Post by Billingd on 2017-12-24
Answered my own question here. "sudo apt install openresolv nscd unbound" has fixed my problem. I thought there would have been more config of openresolv required. But this one line has sorted it out
Yippee !

---


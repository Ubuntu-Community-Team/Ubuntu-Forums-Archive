---
title: "Block Whole Countries in Firewall?"
date: 2017-05-17
forum: Server Platforms
---

### Post by webdevde on 2017-05-17
Hi, 
     With all the craziness and hacking that's going on in the Internet lately, I would like to ban ip address from  the following countries from connecting to my server:

Russia
North Korea
USA

Is there a way to set up the firewall in Ubuntu server to automatically do this?

Thanks

---

### Post by LastDino on 2017-05-17
There might be other ways to do this but in my Uni it was achieved by simply using  CSF firewall on Linux, they also had Cyberoam, but that was good when you were having Uni lappy within premiss's.

Here is quick guide which google threw up > [https://www.scalescale.com/tips/nginx/how-to-block-a-country-using-csf-firewall-on-linux/](https://www.scalescale.com/tips/nginx/how-to-block-a-country-using-csf-firewall-on-linux/)

I've personally never set this up, but the thought is interesting, maybe give this a try?

---

### Post by TheFu on 2017-05-17
Welcome to the forums.

Anyway? Yes. It isn't hard, but it isn't point-n-click trivial either.
100% accurate? No, but probably close enough.
Automatic? No, but you can automate it.

I block many different countries using published routing tables.  These change constantly, so we have to accept either being out of date or errors.  The fastest, most efficient way, is to write a script that adds all the subnets for countries we want to block using the most current data we have available into an 'ipset', then apply that 'ipset' to the kernel's firewall using whatever front-end firewall tool you like.  iptables would be the normal method.
Here's an article about that: [https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset](https://www.linuxjournal.com/content/advanced-firewall-configurations-ipset)

You can google for the routing or country subnet lists.  A popular one has been moved in the last 6 months. I haven't done an exhaustive search for a replacement myself.

---

### Post by Michael_McKenney on 2017-05-22
I bought the Fortinet 800C firewall for that reason.  I asked Cisco 20+ years ago for geographical based blocking using the ICANN addresses assigned to each country.  Fortinet did it.  I have over 200 countries on the list.

---

### Post by TheFu on 2017-05-22
> **Michael_McKenney said:**
> I bought the Fortinet 800C firewall

It's $1300!
[https://thehackernews.com/2016/01/fortinet-firewall-password-hack.html](https://thehackernews.com/2016/01/fortinet-firewall-password-hack.html)
[http://www.theprohack.com/2016/03/fortigate-ssh-backdoor-password-calculator.html](http://www.theprohack.com/2016/03/fortigate-ssh-backdoor-password-calculator.html)

and they fixed the ssh-backdoor:
[http://www.zdnet.com/article/cisco-fortinet-patch-flaws-exposed-by-alleged-nsa-hacking-group/](http://www.zdnet.com/article/cisco-fortinet-patch-flaws-exposed-by-alleged-nsa-hacking-group/)

For $1300 I bet someone would create the IP tables for you.

Paying for something doesn't guaranty anything.

---

### Post by Michael_McKenney on 2017-05-22
Fortinet fixed that a while back.  You get many more features for the money than just country blocking.   One mistake on the list can block other IPs that you want.   You are paying for a team to test before.   Paying one person to type of the hundreds of pages of addresses can lead to a lot of typos that would be hard to troubleshoot.   Ubuntu is great for some things.  Real hardware is better for your firewall.

---

### Post by mastablasta on 2017-05-23
> **webdevde said:**
> Hi, 
     With all the craziness and hacking that's going on in the Internet lately, I would like to ban ip address from  the following countries from connecting to my server:

Russia
North Korea
USA

Is there a way to set up the firewall in Ubuntu server to automatically do this?

Thanks

you should at least add China to the list

they can just use TOR to bypass your block. depending on the server use it might be more efifcient to create a whitelist rather than blacklist. not 100% security, but just one of the layers.

---

### Post by Michael_McKenney on 2017-05-23
Most firewalls do run some version of Linux as the base OS including Fortinet.

---


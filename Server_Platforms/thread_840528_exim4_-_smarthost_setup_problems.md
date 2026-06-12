---
title: "exim4 - smarthost setup problems"
date: 2008-06-25
forum: Server Platforms
---

### Post by AnthonyArde2 on 2008-06-25
Hi all i am trying to setup my ubuntu 7.10 system with exim4 but i have a problem when i do a test email to a nonlocal system, i am using a smarthost configuration and have set the dc_smarthost option in /etc/exim4/update-exim4.conf.conf to my isp's smtp server. my network i have configured as follows: i have two networks cards running two different networks, i have taken the internet connection from the one network and shared it to the other network using firestarter, under network settings i have my hostname filled in as anthony-linux and my domain name filled in as example.co.za (does this make a difference?)

in the terminal i try to run: echo "test email" | exim4 [email]emailname@blabla.co.za[/email]

i have replaced the true email address with a non existant email address for this post. anyway when i run this command i recieve this error in my mainlog file for exim4:


2008-06-25 19:30:14 exim 4.67 daemon started: pid=5646, -q30m, listening for SMTP on port 25 (IPv6 and IPv4)
2008-06-25 19:30:28 Start queue run: pid=5654
2008-06-25 19:30:28 1KBYku-0001iS-VF Message is frozen
2008-06-25 19:30:28 End queue run: pid=5654
2008-06-25 19:33:01 1KBYrc-0001fq-UR <= anthony@anthony-linux U=anthony P=local S=322
2008-06-25 19:33:02 1KBYrc-0001fq-UR ** [email]emailname@blabla.co.za[/email]: Unrouteable address
2008-06-25 19:33:18 1KBYru-0001ft-02 <= <> R=1KBYrc-0001fq-UR U=Debian-exim P=local S=1136
2008-06-25 19:33:18 1KBYrc-0001fq-UR Completed
2008-06-25 19:33:31 1KBYru-0001ft-02 => anthony <anthony@anthony-linux> R=local_user T=mail_spool
2008-06-25 19:33:31 1KBYru-0001ft-02 Completed

if you have any idea what is going on please let me know, do i have to have a specific hostname or domain name in my network configuration? or am i able to use any name, how does this work exactly.

Thanks 

Anthony

---

### Post by Titan8990 on 2008-06-26
This sounds like exim4 is failing to resolve the DNS. The "Unroutable Address" error typically occurs when either the e-mail domain you are trying to send e-mail to do does no exist or you computer, like it says, does not have a route to the address. 

I'm not 100% on smarthost configurations, as my exim4 setup in independent, but are you sure you ISP allows you to use their SMTP server as a smarthost?

If you do nslookup for blabla.co.za does it resolve the name?

---


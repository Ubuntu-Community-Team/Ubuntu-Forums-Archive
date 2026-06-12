---
title: "VirtualBox no internet connection"
date: 2009-08-03
forum: Virtualisation
---

### Post by FokkerCharlie on 2009-08-03
Hi All

I've been using VirtualBox (not the OSE!) to run Win XP for a long time without problems.  However, a few days ago, and a while after an update to IE8, it stopped connecting to the interweb.

When I open IE, I get the following, regardless of URL:

>   Internet Explorer cannot display the webpage 
   
   What you can try: 
    Diagnose Connection Problems  
 
     More information 

This problem can be caused by a variety of issues, including: 

•Internet connectivity has been lost.
•The website is temporarily unavailable.
•The Domain Name Server (DNS) is not reachable.
•The Domain Name Server (DNS) does not have a listing for the website's domain.
•There might be a typing error in the address.
•If this is an HTTPS (secure) address, click Tools, click Internet Options, click Advanced, and check to be sure the SSL and TLS protocols are enabled under the security section. 


Which is no good.  The diagnostic doesn't turn anything up.  I can see the connection (PC Net Fast III/NAT) in network connections, and all looks well, in fact it seems to send/receive the odd packet (112/26 as I type, after booting 3 mins ago).  The shared folder I have set up via VB works fine, too.

I found an old thread on the subject, and tried:

```
sudo service networking restart
```

which fixed the problem for a few minutes!  /etc/init.d/networking restart has no effect.

So, is this a problem with my VB settings, the setup within XP, or something else?

All advice gratefully received!

Charlie

---

### Post by jocampo on 2009-08-03
Hey Charlie...

ok, so, you're running XP on a VirtualBox, right? let's do this (in that order)


-Please run IPCONFIG /ALL inside your XP virtual machine
-Write down your IP address and gateway
-Find out your host (the real one) IP
-Find out an IP and Hostname (on internet) that you know you can ping

Armed with that information, proceed as follow:

1. Ping Gateway
2. Ping IP of your host (real one) <-- should be the same IP for VirtualMachine if you're using NAT. Different if using bridged network
3. Ping hostname
4. Ping internet IP
5. Ping internet hostname

4 & 5 are for checking outside/internet connectivity.

If all succeeded, your VirtualBox is fine and it's an obscure IE setting :-) ... I hate new IE version; they tried to make it more secure but it's a pain to revert all those security settings.

If 1 failed, revise your virtualbox adapter or the internal virtual machine NIC configuration

If failed at step 5 but 4 succeeded, you got a DNS issue, problem could reside on your Virtual Machine.

Please check and let us know,

---

### Post by FokkerCharlie on 2009-08-03
Hi Jocampo

Yes, XP on VM.

I'm afraid that I'm not a great networking expert, so could you confirm that I have used the right addresses and wotnot for the investigations?  See attached pic for result of ipconfig /all.

1) Ping gateway (10.0.2.2), worked fine.
2/3) Ping IP of host/hostname- how do I know what my host is?
4) Ping internet IP (as reported by whatismyip.com - is this correct?) timed out.  I think I have done this wrong, as it didn't work in Ubuntu, either.
5) How do I find my internet hostname?

I'm very sorry to be a dullard, and thank you for your patience!

Charlie

[IMG]http://filebin.ca/phweao[/IMG]

---

### Post by jocampo on 2009-08-04
> **FokkerCharlie said:**
> 
[IMG]http://filebin.ca/phweao[/IMG]

You're getting a Class A IP: 10.0.2.15. That makes me think you are using NAT. So, some way, you're receiving your IP from your internet connection via DHCP. 

Try to find out the IP address and hostname of FQDN or something which already resides on internet. For instance (this is a hypotethical example) [www.mysite.com](www.mysite.com) which IP a.b.c.d If for some reason you can ping the IP but not the hostname  means you have a DNS problem.

If you really want to know if you have internet connection or not inside your VM, put an IP address on the URL (of course, the IP of a real internet webpage) and press [enter] Your browser should be able to display something.

BTW, your VM hostname is charlie-vb-xp.

---

### Post by FokkerCharlie on 2009-08-04
Hello!

OK, so I tried ping [www.bbc.co.uk](www.bbc.co.uk) , which worked.  Then I tried ping 212.58.251.197, which didn't... however, I then rebooted, and it worked.  Very strange.  IE still not wanting to play, however.

I do have VB set up with NAT, ping charlie-vb-xp worked OK, too.

So does this mean it's a problem with the IE8/XP setup and not really a VirtualBox problem?

Cheers
Charlie

---

### Post by jocampo on 2009-08-04
> **FokkerCharlie said:**
> Hello!

OK, so I tried ping [www.bbc.co.uk](www.bbc.co.uk) , which worked.  Then I tried ping 212.58.251.197, which didn't... however, I then rebooted, and it worked.  Very strange.  IE still not wanting to play, however.

I do have VB set up with NAT, ping charlie-vb-xp worked OK, too.

So does this mean it's a problem with the IE8/XP setup and not really a VirtualBox problem?

Cheers
Charlie


It could be. If you can ping an internet website (IP or FQDN) you can "see" outside world. Did you check Proxy Settings for IE? also, take a look on your DNS suffixes for your network card; you should have enable this option: Obtain DNS address automatically.

As a temporary measure and for testing purposes, downgrade the security level for the Internet Zone; change it to Medium or Medium low. Not sure what IE version you're running but most recent versions are so secure that some of them just block all internet traffic.

---

### Post by FokkerCharlie on 2009-08-05
Hi Jocampo

Thanks for this.  It looked to me like a problem with the XP setup, rather than VB, so I managed to find an old XPI image that I had lying around- I downgraded to that and now it's working fine.

I greatly appreciate your help.

Charlie

---

### Post by jocampo on 2009-08-05
> **FokkerCharlie said:**
> Hi Jocampo

Thanks for this.  It looked to me like a problem with the XP setup, rather than VB, so I managed to find an old XPI image that I had lying around- I downgraded to that and now it's working fine.

I greatly appreciate your help.

Charlie

:-)  great! Happy VirtualBox time then ... please mark it as SOLVED

---

### Post by FokkerCharlie on 2009-08-05
Well, I would, but it's not possible to do that on these forums anymore, as far as I can tell!

---

### Post by jocampo on 2009-08-05
;-) I put a tag Charlie

---


---
title: "Any way to avoid packet sniffing/ packet filters?"
date: 2011-05-11
forum: Security
---

### Post by lmn. on 2011-05-11
Hi

recently moved from windows over to ubuntu, because the sick <snip> I live with decided to remotely control my PC & destroy my website.

I believe he is still sniffing my traffic, and using IP packet filters to stop me accessing certain sites.

I've installed the firefox addon; ```
https://www.eff.org/https-everywhere
```but my real question is, without VPN, is there a workaround to accessing my email/paypal account?

many thanks

---

### Post by i.r.id10t on 2011-05-12
Depends on how he is doing it.  If on the DNS level, then putting entries in your /etc/hosts file will fix it.  If on the router and he is dropping the packets based on the destination, then not much.

---

### Post by matt_symes on 2011-05-12
Hi

Have you considered TOR ?

[https://www.torproject.org/](https://www.torproject.org/)

Kind regards

---

### Post by lmn. on 2011-05-12
> **i.r.id10t said:**
> Depends on how he is doing it. If on the DNS level, then putting entries in your /etc/hosts file will fix it. If on the router and he is dropping the packets based on the destination, then not much.

OK thanks I will look into it


> **matt_symes said:**
> Hi

Have you considered TOR ?

[https://www.torproject.org/](https://www.torproject.org/)

Kind regards

Yep I installed and did everything I could to see if I could get it working, then found [this]("http://askville.amazon.com/TOR-Network-free-crime-syndicates-hackers-spies-child-pornographers-Shut/AnswerViewer.do?requestId=60469011") and decided to uninstall.


thanks again guys

---

### Post by matt_symes on 2011-05-12
Hi

> **lmn. said:**
> 
Yep I installed and did everything I could to see if I could get it working, then found [this]("http://askville.amazon.com/TOR-Network-free-crime-syndicates-hackers-spies-child-pornographers-Shut/AnswerViewer.do?requestId=60469011") and decided to uninstall.

thanks again guys

And that would stop you using it for legitimate purposes ? Maybe you also should stop using e-mail then or the web in general. 

Anyways, regardless if it's true or not, the article produces no references and has no citations, just some empty handwaving.

I fail to see how another persons nefarious use of a technology should impact on your decision not use the technology. :confused: The decision is yours though.

That said, I hope you find a solution to your problem. Moving might be one :D

Kind regards

---

### Post by lmn. on 2011-05-12
> **matt_symes said:**
> Hi



And that would stop you using it for legitimate purposes ? Maybe you also should stop using e-mail then or the web in general. 

Anyways, regardless if it's true or not, the article produces no references and has no citations, just some empty handwaving.

I fail to see how another persons nefarious use of a technology should impact on your decision not use the technology. :confused: The decision is yours though.

That said, I hope you find a solution to your problem. Moving might be one :D

Kind regards

I would like to use it for legitimate purposes, but if I used the service I think it would be fair to allow others to use my connection. And I'm not prepared to allow pedos to hide behind my computer.

The idea is great, but I don't agree with the way it allows people to break the law against my name.

---

### Post by matt_symes on 2011-05-12
Hi

> **lmn. said:**
> I would like to use it for legitimate purposes, but if I used the service I think it would be fair to allow others to use my connection. And I'm not prepared to allow pedos to hide behind my computer.

The idea is great, but I don't agree with the way it allows people to break the law against my name.

Then just run the client :confused: You don't have to set up a TOR server.

Kind regards

---

### Post by lmn. on 2011-05-12
> **matt_symes said:**
> Hi



Then just run the client :confused: You don't have to set up a TOR server.

Kind regards

Doesn't the service depend on people relaying connections? I don't want to be a leech :grin:

Also, if I decided to run the client, would that mean the person I'm connecting through has access to my credentials?

---

### Post by doas777 on 2011-05-12
> **lmn. said:**
> I would like to use it for legitimate purposes, but if I used the service I think it would be fair to allow others to use my connection. And I'm not prepared to allow pedos to hide behind my computer.

The idea is great, but I don't agree with the way it allows people to break the law against my name.
that is not how tor works. you are just installing a client, not a node-server. 
I think you may be thinking of FreeNet or I2P, a TOR-like proxy network, where everyones box is a routing node. 

in the end, the only way to defeat an analysis coming from inside your network, is to use a tunneling protocol on your host that terminates on a trusted host outside your network. that means VPN, SSH, SSL, or somthing like TOR. 

keep in mind, regarding email//paypal. those should both be ssl encrypted, wether you use https everywhere or not. that means that he can see who your packets are going to, but cannot see what is in them, or modify the connection. make sure he has not reconfigured FF to use a proxy server or dns server that he controls. 

as for DNS, I would point your PC to use OpenDNS servers, or google or whatever. if he is blocking return UDP/53 traffic from unknown DNS servers, then this is problematic, and is best defeated by tunneling as described above.

also, modern switch ports only carry traffic that is destined for one of the endpoints, so he typically should not be able to see your traffic unless his switch port is in promiscuous mode (not a trivial task). I have to assume he controls your shared router or an upstream server? if not, then you probably don't have anything to worry about on the net end. i'd be more afraid of physical acccess.

lock up your PC case (just a llittle suitcase padlock will work fine), set a bios poweron/setup password, and disable boot from CD in your bios. clearing a bios password is trivial if they can open your case, so the little padlock is essential. 
no guarantees, but then at least he has to explain to you why he physically broke your case to get in. 

if it continues, call the police. that'll stop most folks.

---

### Post by doas777 on 2011-05-12
> **lmn. said:**
> Doesn't the service depend on people relaying connections? I don't want to be a leech :grin:

Also, if I decided to run the client, would that mean the person I'm connecting through has access to my credentials?

No, and No. you yourself with residential bandwidth would provide little value to tor, and the network is not designed to be dynamic enough to accommodate many routing nodes coming on, and then falling off every minute. TOR endpoints are in reasonably predictable places and don't change signifigantly day to day. 

also, all traffic passing throgh a tor node is encrypted inside the tunnel, so no, an intermediary system cannot (easilly) see what you pass. this is especially true of encrypted protocols like ssl, which would be used to encrypt any authentication data/credentials you send. tunnels inside of tunnels.

---

### Post by matt_symes on 2011-05-12
Hi

> **lmn. said:**
> Doesn't the service depend on people relaying connections? I don't want to be a leech :grin:

Yes. You would be relayed through the TOR network. Therefore it is slower than normal browsing. But it is encrypted on your PC before being transmitted  so the your housemate would not be able to sniff your packets.

> Also, if I decided to run the client, would that mean the person I'm connecting through has access to my credentials?I don't believe so. Especially on a secure connection. i.e. https

Have a read of these if you are interested.

[https://www.torproject.org/docs/faq-abuse.html.en](https://www.torproject.org/docs/faq-abuse.html.en)
[https://www.torproject.org/docs/faq.html.en](https://www.torproject.org/docs/faq.html.en)

Kind regards

---

### Post by matt_symes on 2011-05-12
Hi 

The other thing you could do is set up an account with an ssh enabled proxy server and browse through that.

This will give you the general idea.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

No need for the TOR network then.

Kind regards

---

### Post by lmn. on 2011-05-12
what a mess, just as i was about to post my reply, he blocks this site.

couldnt get torbrowser working in ubuntu, so i installed it in xp -virtualbox.

when i go to copy my paste over to pastebin i receive this message:
'your request for pastebin.com/post.php could not be fulfilled, because  the connection has been closed before Privoxy received any data

obviously I now google privoxy and it seems thats the program hes been using to block connections etc.
[FONT=Courier New][SIZE=1]
Privoxy is a non-caching web proxy with advanced filtering capabilities  for enhancing privacy, modifying web page data and HTTP headers, controlling  access, and removing ads and other obnoxious Internet junk. Privoxy has a  flexible configuration and can be customized to suit individual needs and tastes.  It has application for both stand-alone systems and multi-user networks.[/SIZE][/FONT]

what a nob


im not rewriting my reply, but ill be on a different connection tomorrow and ill post it then

thanks all for your input


*also linux pwns windows

---

### Post by doas777 on 2011-05-12
if he is using privoxy to block your sites, then at some point your network traffic is moving through a device he controls. if this continues, a sledghammer to that device may get the point across in a non-confusable fashion. 

have you considered having a long conversation with your roommate? perhaps finding some one to live with who respects your property? as I said before, if he's breaking into your PC, and you have made it clear that he is not welcome, then calling the police may be a good choice.

---

### Post by lmn. on 2011-05-12
> **doas777 said:**
> if he is using privoxy to block your sites, then  at some point your network traffic is moving through a device he  controls. if this continues, a sledghammer to that device may get the  point across in a non-confusable fashion. 

have you considered having a long conversation with your roommate?  perhaps finding some one to live with who respects your property? as I  said before, if he's breaking into your PC, and you have made it clear  that he is not welcome, then calling the police may be a good  choice.

he needs a sledgehammer to the face

I don't enjoy conversation  with him, -

my copy of windows wasnt exactly genuine so im not sure what grounds i stand on when it comes to legality issues with that.

He did use my paypal account to pay for a usenet service so ill consider havin him for fraud.

moving out in a couple of months, can't wait :grin:

---

### Post by zealibib slaughter on 2011-05-12
You need to check out this ubuntu geek post. [http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html).
 
some of these tools will help you stop the packet sniffing, and others can be used to give him a taste of his own medicine :).  
 
Also you can try out backtrack linux which comes preloaded with many tools for identifying and exploiting.  Hopefully you can find out what device he has which your traffic is flowing through and tunnel, block or exploit it.

---

### Post by CandidMan on 2011-05-12
> **zealibib slaughter said:**
> 
 
Also you can try out backtrack linux which comes preloaded with many tools for identifying and exploiting.  Hopefully you can find out what device he has which your traffic is flowing through and tunnel, block or exploit it.
That's just mean-spirited and vengeful. I thoroughly approve.
But if the situation escalates, make sure you 'win'

---

### Post by ehode on 2011-05-12
Also for items like paypal and if you have it gmail, turn on two factor authentication.

---

### Post by Thewhistlingwind on 2011-05-12
If you don't mind, the output of arp -a would be useful. (Though it will reveal the machine names on your network I must caution you.)

---

### Post by doas777 on 2011-05-13
> **lmn. said:**
> what a mess, just as i was about to post my reply, he blocks this site.

couldnt get torbrowser working in ubuntu, so i installed it in xp -virtualbox.

when i go to copy my paste over to pastebin i receive this message:
'your request for pastebin.com/post.php could not be fulfilled, because  the connection has been closed before Privoxy received any data

obviously I now google privoxy and it seems thats the program hes been using to block connections etc.
[FONT=Courier New][SIZE=1]
Privoxy is a non-caching web proxy with advanced filtering capabilities  for enhancing privacy, modifying web page data and HTTP headers, controlling  access, and removing ads and other obnoxious Internet junk. Privoxy has a  flexible configuration and can be customized to suit individual needs and tastes.  It has application for both stand-alone systems and multi-user networks.[/SIZE][/FONT]

what a nob


im not rewriting my reply, but ill be on a different connection tomorrow and ill post it then

thanks all for your input


*also linux pwns windows


having reread your post, I think the privoxy problem is on your XP VM box, rather than a sign that your adversary is interfering with your transmissions. the windows versions of TOR still use Privoxy/vidalia for the secure proxy. Privoxy will attempt to prevent leakage of identity data, but will sometimes interfere with normal site operations.

> **Thewhistlingwind said:**
> If you don't mind, the output of arp -a  would be useful. (Though it will reveal the machine names on your  network I must caution you.)
agreed.
@Op,  some knowledge of your network cabling would also be helpful. do  you use a router or a proxy/dns server on your network? are you routing  through a machine using internet connection sharing or anything?

---

### Post by kev77 on 2011-05-13
Using a mobile broadband dongle may be your answer until you are away from the offender?

---

### Post by lmn. on 2011-05-13
> **zealibib slaughter said:**
> You need to check out this ubuntu geek post. [http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-security-tools-available-in-ubuntu.html).
 
some of these tools will help you stop the packet sniffing, and others can be used to give him a taste of his own medicine :).  
 
Also you can try out backtrack linux which comes preloaded with many tools for identifying and exploiting.  Hopefully you can find out what device he has which your traffic is flowing through and tunnel, block or exploit it.

incredibly useful post, cheers pal


> **doas777 said:**
> having reread your post, I think the privoxy  problem is on your XP VM box, rather than a sign that your adversary is  interfering with your transmissions. the windows versions of TOR still  use Privoxy/vidalia for the secure proxy. Privoxy will attempt to  prevent leakage of identity data, but will sometimes interfere with  normal site operations.


agreed.
@Op,  some knowledge of your network cabling would also be helpful. do   you use a router or a proxy/dns server on your network? are you routing   through a machine using internet connection sharing or  anything?

I think it's unlikely my ISP would have problems with email & paypal  so as far as i can tell it's an internal problem/ which led me to  believe my housemate was behind it.. I could only access these sites using tor, any direct connection under any OS wouldn't work.

it's a router we use; I hadn't used any DNS or proxy servers and the last thing I'd want is to use connection sharing. I don't know whether it's possible for that to be forced upon the network. probably.

I'll do an arp thing when I'm back on that connection :)

thanks again :grin:


> **kev77 said:**
> Using a mobile broadband dongle may be your answer until you are away from the offender?

would work, but I think I'd rather pay for VPN ;)

---

### Post by bodhi.zazen on 2011-05-13
Your options are to:

1. Do not use untrusted networks. Probably the very best option.

2. Tunnel your traffic over VPN or SSH.

3. Use tor and https.

---

### Post by cprofitt on 2011-05-14
> **lmn. said:**
> Hi

recently moved from windows over to ubuntu, because the sick <snip> I live with decided to remotely control my PC & destroy my website.

I believe he is still sniffing my traffic, and using IP packet filters to stop me accessing certain sites.

I've installed the firefox addon; ```
https://www.eff.org/https-everywhere
```but my real question is, without VPN, is there a workaround to accessing my email/paypal account?

many thanks

I am going to assume you are on the same network (wired or wireless) as the person you are concerned with... as long as that is the case then given that person having the right set of knowledge you will not, even with a VPN, be able to secure your traffic.

If you own/control the router then you can lock them out of the network though.

---

### Post by Thewhistlingwind on 2011-05-14
> **kev77 said:**
> Using a mobile broadband dongle may be your answer until you are away from the offender?

+1, just make sure it works with Linux. That'll REALLY throw him off.  Make sure he never sees it.

However, those are expensive, and cat and mouse is more fun.;)

---

### Post by kev77 on 2011-05-14
> **Thewhistlingwind said:**
> +1, just make sure it works with Linux. That'll REALLY throw him off.  Make sure he never sees it.

However, those are expensive, and cat and mouse is more fun.;)

very cheap in the UK,and ubuntu sets them up lovely, :)

---

### Post by rookcifer on 2011-05-14
> **lmn. said:**
> Hi

recently moved from windows over to ubuntu, because the sick <snip> I live with decided to remotely control my PC & destroy my website.

It looks like you should be on a marriage/relationship counseling forum and not here. :(

---


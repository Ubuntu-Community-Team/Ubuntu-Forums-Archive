---
title: "Use ClamAV as Privoxy(Proxy) antivirus"
date: 2010-08-05
forum: Security
---

### Post by wacky_sung on 2010-08-05
Can anyone tell me does it effective using ClamAV as Privoxy antivirus?I have actually configure it but it does not seem to come into any effect.Why?I test it with Eicar(test virus) online and it does not even prompt there is a problem unless i have scanned.Beside that,i have installed ClamAV daemon along with it.

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
```
Proxy
If you are using a http proxy to connect to the internet you will have to edit the file /etc/clamav/freshclam.conf adding:


HTTPProxyServer serveraddress
HTTPProxyPort portnumber
```

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

Issue :How come the Clam Antivirus does not prompt there is a virus when i opened the file or problem link?Does it work difference as Window OS antivirus which prompt when there is a virus detected?

---

### Post by espressobeanie on 2010-08-05
If I'm not mistaken, Privoxy is a tunnel from your computer to the Tor network. Therefore, it employs encryption to every incoming and outgoing packet. My guess is that the virus is being encapsulated in an encrypted channel and ClamAV cannot scan encrypted channels.

---

### Post by OpSecShellshock on 2010-08-05
I'm not aware of any AV applications that prompt upon detection of malware other than the fakes and rogues. Most of the legitimate software just logs the detections and silently deletes or quarantines the files. Have you checked the logs for something about the EICAR file?

---

### Post by bodhi.zazen on 2010-08-05
> **espressobeanie said:**
> If I'm not mistaken, Privoxy is a tunnel from your computer to the Tor network. Therefore, it employs encryption to every incoming and outgoing packet. My guess is that the virus is being encapsulated in an encrypted channel and ClamAV cannot scan encrypted channels.

You can use TOR with or without a proxy. Using a proxy adds additional privacy in the connection between your computer and the TOR node.

See:[* Privoxy*  - *Home Page*]("http://www.privoxy.org/")

Personally I use Privoxy for both privacy and adblocking, I do not feel I need TOR and TOR is slow.

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

You may use any proxy you wish in combination with TOR, privoxy is not the only option, and, as indicated, you may use TOR without an additional proxy if you wish.

---

### Post by bodhi.zazen on 2010-08-05
> **wacky_sung said:**
> Can anyone tell me does it effective using ClamAV as Privoxy antivirus?I have actually configure it but it does not seem to come into any effect.Why?I test it with Eicar(test virus) online and it does not even prompt there is a problem unless i have scanned.Beside that,i have installed ClamAV daemon along with it.

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
```
Proxy
If you are using a http proxy to connect to the internet you will have to edit the file /etc/clamav/freshclam.conf adding:


HTTPProxyServer serveraddress
HTTPProxyPort portnumber
```[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

Issue :How come the Clam Antivirus does not prompt there is a virus when i opened the file or problem link?Does it work difference as Window OS antivirus which prompt when there is a virus detected?


What are you wanting to do exactly ?

The instructions for HTTPProxyServer is included as a part of the instructions to update the clam database.

It sounds from your post as if you wish to scan downloads for viruses ? If that is the case, why ? There are no know active viruses in Linux so it is a lot of effort for little (or no) benefit. I suggest you read the security sticky.

If for some reason you wish to scan internet traffic/downloads for viruses, I believe you need squid:

[http://squidclamav.darold.net/](http://squidclamav.darold.net/)
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

With that second link, you can skip dansguardian if you wish.

What does Privoxy have to do with anything ? Are you using Privoxy ? For what ?

I have not seen Privoxy + clamav to scan downloads, what how to are you following ?

---

### Post by wacky_sung on 2010-08-06
> **OpSecShellshock said:**
> I'm not aware of any AV applications that prompt upon detection of malware other than the fakes and rogues. Most of the legitimate software just logs the detections and silently deletes or quarantines the files. Have you checked the logs for something about the EICAR file?

It does not have the log of the detections or silently deletes / quarantines the files which it does not have the real-time(on-access) capability.It will only detect when you scan it.

Note:Look at my signature in which there is a request for it.

---

### Post by wacky_sung on 2010-08-06
> **bodhi.zazen said:**
> What are you wanting to do exactly ?

The instructions for HTTPProxyServer is included as a part of the instructions to update the clam database.

It sounds from your post as if you wish to scan downloads for viruses ? If that is the case, why ? There are no know active viruses in Linux so it is a lot of effort for little (or no) benefit. I suggest you read the security sticky.

If for some reason you wish to scan internet traffic/downloads for viruses, I believe you need squid:

[http://squidclamav.darold.net/](http://squidclamav.darold.net/)
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

With that second link, you can skip dansguardian if you wish.

What does Privoxy have to do with anything ? Are you using Privoxy ? For what ?

I have not seen Privoxy + clamav to scan downloads, what how to are you following ?

Thank i have tried to HTTP Antivirus proxy but it does not work at all.

[http://www.server-side.de/features.htm](http://www.server-side.de/features.htm)

---

### Post by bodhi.zazen on 2010-08-06
> **wacky_sung said:**
> Thank i have tried to HTTP Antivirus proxy but it does not work at all.

[http://www.server-side.de/features.htm](http://www.server-side.de/features.htm)

What are you trying to accomplish exactly ? Again, there are no known active viruses for Linux, so it is a lot of effort for little or no gain.

Or are you trying to install a gateway / proxy for a LAN that includes multiple Windows clients ?

If you want support for such an endeavor, you need to tell us more, what did you install, how did you configure it, and what makes you think it is not working ? What how to are you following ?

Does clamav recognize the test file as bad (if you download and scan the file ) ?

---

### Post by wacky_sung on 2010-08-07
> **bodhi.zazen said:**
> What are you trying to accomplish exactly ? Again, there are no known active viruses for Linux, so it is a lot of effort for little or no gain.

Or are you trying to install a gateway / proxy for a LAN that includes multiple Windows clients ?

If you want support for such an endeavor, you need to tell us more, what did you install, how did you configure it, and what makes you think it is not working ? What how to are you following ?

Does clamav recognize the test file as bad (if you download and scan the file ) ?

Ok,what i need is to use ClamAV in Proxy(Privoxy) as a gateway to have real-time(on access) scan while using the browser.Which mean that i do not require to perform a manual scan on my system while using the proxy connected browser to surf the net if those hostile script / file being downloaded and detected automatically by the ClamAV.Hopefully you have got what i mean.Currently i found ClamAV is not working because it does not automatically prompt the user when open an hostile file / links with the link provided below.

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)
  
Very much appreciated if you can find any solution for it.Cheer :)

---

### Post by bodhi.zazen on 2010-08-08
I understand what you are trying to do, you have not answered why ?

There is not need for such a thing on Linux machines.

The only way I know to accomplish what you want is with squid, not privoxy. I have never seen privoxy and clamav used this way.

This how to :

[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

describes how to do this with dansguardian + squid. I suppose you could use dansguardian + privoxy.

The key is on a single line :

[quote]The "contentscanner" line is already in /etc/dansguardian/dansguardian.conf towards the bottom. Uncomment this line to tell DansGuardian to use ClamAV to scan items requested via HTTP.[/quoto]

That link walks you through configuration of dansguardian, I gave you links to my blog on how to dansguardian + privoxy.

From there, stating that it is not working is not helpful. You need to tell us what applications you have installed and how you have configured them.

Again, I am unaware of using privoxy + calmav. As far as I know, you need to use dansguardian + either privoxy or squid.

IMO such a set up is less then ideal for a variety of reasons, and, IMO, if you are trying to protect Windows machines in some way there are much better methods, ie you should still run av on windows clients.

---

### Post by wacky_sung on 2010-08-08
> **bodhi.zazen said:**
> I understand what you are trying to do, you have not answered why ?

There is not need for such a thing on Linux machines.

The only way I know to accomplish what you want is with squid, not privoxy. I have never seen privoxy and clamav used this way.

This how to :

[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

describes how to do this with dansguardian + squid. I suppose you could use dansguardian + privoxy.

The key is on a single line :

[quote]The "contentscanner" line is already in /etc/dansguardian/dansguardian.conf towards the bottom. Uncomment this line to tell DansGuardian to use ClamAV to scan items requested via HTTP.[/quoto]

That link walks you through configuration of dansguardian, I gave you links to my blog on how to dansguardian + privoxy.

From there, stating that it is not working is not helpful. You need to tell us what applications you have installed and how you have configured them.

Again, I am unaware of using privoxy + calmav. As far as I know, you need to use dansguardian + either privoxy or squid.

IMO such a set up is less then ideal for a variety of reasons, and, IMO, if you are trying to protect Windows machines in some way there are much better methods, ie you should still run av on windows clients.

The whole intention of my setup for the ClamAV to have real-time(on access) is to be safe than sorry(just to function the same way as window inspite it is immune to most virus out there) and i personally feel that it is a good practice to have your antivirus to be on real-time(on access) at all time.

Thank for your link and i will have a good reading before i decide to move on with it(because i just find that it is kinda tough just to configure squid to a newbie like me) :)

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> [QUOTE=bodhi.zazen;9694143]I understand what you are trying to do, you have not answered why ?

There is not need for such a thing on Linux machines.

The only way I know to accomplish what you want is with squid, not privoxy. I have never seen privoxy and clamav used this way.

This how to :

[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

describes how to do this with dansguardian + squid. I suppose you could use dansguardian + privoxy.

The key is on a single line :



The whole intention of my setup for the ClamAV to have real-time(on access) is to be safe than sorry(just to function the same way as window inspite it is immune to most virus out there) and i personally feel that it is a good practice to have your antivirus to be on real-time(on access) at all time.

Thank for your link and i will have a good reading before i decide to move on with it(because i just find that it is kinda tough just to configure squid to a newbie like me) :)

This set up is very much unnecessary in Linux. You are much better off learning to use apparmor or snort or OSSEC.

Be that as it may, Privoxy + Dansguardian is much easier to set up (although squid is not hard either) than add clamav and configure Dansguardian. In all it is editing something like 3 or 4 lines in 2 or 3 configuration files.

---

### Post by wacky_sung on 2010-08-08
> **bodhi.zazen said:**
> [QUOTE=wacky_sung;9694904]

This set up is very much unnecessary in Linux. You are much better off learning to use apparmor or snort or OSSEC.

Be that as it may, Privoxy + Dansguardian is much easier to set up (although squid is not hard either) than add clamav and configure Dansguardian. In all it is editing something like 3 or 4 lines in 2 or 3 configuration files.

Thank for your recommendation.In fact,i have done my installation for Privoxy + Dansguardian from the [blog]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/") in which you have wrote.Probably i will try to learn as much as i can because i love to know more.If you can spare some time,may be you can write some simplfy snort or OSSEC guide inspite i have read what you wrote on the sticky into your personal blog site.

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> 

Thank for your recommendation.In fact,i have done my installation for Privoxy + Dansguardian from the [blog]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/") in which you have wrote.Probably i will try to learn as much as i can because i love to know more.If you can spare some time,may be you can write some simplfy snort or OSSEC guide inspite i have read what you wrote on the sticky into your personal blog site.

Did you look at the HIDS and NIDS threads from the security sticky ? Those threads cover snort and OSSEC.

---

### Post by wacky_sung on 2010-08-08
> **bodhi.zazen said:**
> Did you look at the HIDS and NIDS threads from the security sticky ? Those threads cover snort and OSSEC.

Yes i do but the issue for me is that for a newbie like me very much appreciated if there is a simplified version which only include only the installation and configuration of Snort / OSSEC instead of the explanation of choice to choose for each usage.

FYI I do not mean you wrote very badly on your security sticky but very well explained.What a newbie like me usually prefer a quick guide and it help us a lot.

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> Yes i do but the issue for me is that for a newbie like me very much appreciated if there is a simplified version which only include only the installation and configuration of Snort / OSSEC instead of the explanation of choice to choose for each usage.

FYI I do not mean you wrote very badly on your security sticky but very well explained.What a newbie like me usually prefer a quick guide and it help us a lot.

Those were the quick guides, lol

---

### Post by wacky_sung on 2010-08-09
> **bodhi.zazen said:**
> Those were the quick guides, lol

Thank anyway and i am laughing at myself.

---


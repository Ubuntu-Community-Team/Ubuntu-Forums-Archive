---
title: "need firewall help"
date: 2009-10-29
forum: Security
---

### Post by Ubunt2u on 2009-10-29
i have a server with 2 nic's, one with internal ip & one with external ip.  i just discovered that nfs (which im using for rsnapshot) is also using the public ip.  can someone help me configure external to only allow http, https while letting internal allow all?  
Thanks in advance...

---

### Post by dvlchd3 on 2009-10-29
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Ubunt2u on 2009-10-30
> **dvlchd3 said:**
> [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


WOW that's awesome I'd never have thought of that
How about next time rather than taking time to find the man page, just type in [http://www.google.com](http://www.google.com)

---

### Post by cariboo on 2009-10-30
There are lot of very well written community documents [here]("https://help.ubuntu.com/community").

---

### Post by bodhi.zazen on 2009-10-30
> **Ubunt2u said:**
> WOW that's awesome I'd never have thought of that
How about next time rather than taking time to find the man page, just type in [http://www.google.com](http://www.google.com)

Your question is quite broad and you did not give a lot of information, specifically you have not told us how your networking is configured or your ip addresses.

I advise you use iptables directly, you may also use a tool such as shorewall.

If you prefer, see :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Come on back if you get stuck or have a more specific question. please give us sufficient details about your configuration, what tool you are using to configure your firewall with, and where you got stuck.

---

### Post by Ubunt2u on 2009-11-04
Sorry for lack of specifics & smarta$$ reference to google. 

Without giving my specific ip's, my configuration is not complicated.  Using 8.04 Desktop Edition.  Inside the computer are 2 nic's.  One of them has an internal ip 192.168.0.0 and the other, which is hosting vTiger has public ip 12.125.0.0.
I'm using nfs to share out folder which contains backup of vtiger database & i backup every day.  

the other day i noticed that nfs is shared out on external as well as internal & was just wondering if there's a relatively easy way of only using internal nic as "trusted" & block nfs from being shared out on the external.

I've installed gufw but am hesitant to use it until i've received advise on the matter.  Perhap's this can be achieved through nfs configuration?

---


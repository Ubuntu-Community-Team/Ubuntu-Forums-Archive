---
title: "IP Blocker"
date: 2010-04-17
forum: Server Platforms
---

### Post by iissmart on 2010-04-17
I'm looking for an IP blocker for my Ubuntu 8.04 LTS server **(no X)**, but I have no idea where to start. Anyone have any recommendations? It would need to support universal block lists that I could import, such as ones from PeerGuardian.

---

### Post by marbertone on 2010-04-17
I know there is a text file in which you can put all the ip you want to deny ssh access to. Unfortunately, I don't remember where it is located.
Cheers,
Mario Alberto

---

### Post by lisati on 2010-04-17
I use the mod-defensible package on my server running 9.04. It blocks IPs based on opinions sought from DSNBL lists.

Have a look here: [http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch](http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch)

---

### Post by iissmart on 2010-04-17
> **lisati said:**
> I use the mod-defensible package on my server running 9.04. It blocks IPs based on opinions sought from DSNBL lists.

Have a look here: [http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch](http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch)
Thanks for the suggestion. It looks promising, but my only concern is that returning a 403 Forbidden page will still produce load on my machine. I am hoping to find something that will just drop the connection rather than allow it to connect (trying to reduce the amount of apache2 threads on my machine).

I found something called "moblock" but that looks pretty old/outdated, am I right?

---

### Post by bark50 on 2010-04-17
Will IP Blocker work for you?  It's thread is here:  [http://ubuntuforums.org/showthread.php?t=530183]("http://ubuntuforums.org/showthread.php?t=530183")

---

### Post by iissmart on 2010-04-17
> **bark50 said:**
> Will IP Blocker work for you?  It's thread is here:  [http://ubuntuforums.org/showthread.php?t=530183]("http://ubuntuforums.org/showthread.php?t=530183")
Nope, it is a server with no GUI. Thanks though.

---

### Post by bark50 on 2010-04-17
> **iissmart said:**
> Nope, it is a server with no GUI. Thanks though.

Hmmmmmm, probably I don't understand, but the IP Blocker I installed using the instructions from its thread has a gui.  I'll attach a screenshot if I can figure out how to do that!  :lolflag:

---

### Post by iissmart on 2010-04-17
> **bark50 said:**
> Hmmmmmm, probably I don't understand, but the IP Blocker I installed using the instructions from its thread has a gui.  I'll attach a screenshot if I can figure out how to do that!  :lolflag:
Yes, but I do not want a GUI, because my server doesn't have one.

---

### Post by ubun2warrior on 2010-04-17
Hi 
You can try firestarter to block IP, I have tried and it works well. If you are looking at blocking websites on firefox the i would suggest an ad on called 'procon latte' which is excellent.

---

### Post by d3v1150m471c on 2010-04-17
```

**iptables -I INPUT -s 25.55.55.55 -j DROP**


```

---

### Post by Xipher on 2010-04-18
Manage iptables/netfilter by hand
Maybe ConfigServer Firewall will work
I don't know if UFW was available in 8.04 but worth a look
For automated blocking CSF includes LFD or Fail2Ban is an alternative.

---

### Post by iissmart on 2010-04-18
> **d3v1150m471c said:**
> ```

**iptables -I INPUT -s 25.55.55.55 -j DROP**


```
Any way to automate that process given a blocklist?

---

### Post by jre on 2010-04-18
You can run IPList/IPBlock without a GUI. That's just optional.

Or you can use moblock (see signature). Although it's indeed quite old it will do exactly what you want.

And in some time I will release PeerGuardian Linux (pgl) which is based on nfblock (which itself is a clone of moblock) and blockcontrol. You can already try it. Just download the source from the git development repository from peerguardian.sourceforge.net. If you need help for that just ask.

---

### Post by iissmart on 2010-04-18
> **jre said:**
> You can run IPList/IPBlock without a GUI. That's just optional.

Or you can use moblock (see signature). Although it's indeed quite old it will do exactly what you want.

And in some time I will release PeerGuardian Linux (pgl) which is based on nfblock (which itself is a clone of moblock) and blockcontrol. You can already try it. Just download the source from the git development repository from peerguardian.sourceforge.net. If you need help for that just ask.
I actually had the nfblock and blockcontrol pages bookmarked already :) . Thanks for the advice, I'll let you know when I get some time to look into those and see what works for me.

---

### Post by kewlrichie on 2010-04-18
Have u checked out UFW it's an easier way to use iptables [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by iissmart on 2010-05-21
I ended up using blockcontrol and moblock through the Hardy packages [HERE](http://moblock-deb.sourceforge.net/), set up my IP block lists, and it works great! Thanks for all the help, I can't wait for a full release of PeerGuardian Linux :)

---

### Post by jre on 2010-05-22
I made the full release a few days ago! It still lacks the GUI, but otherwise it is superior to moblock/blockcontrol. 
Packages are available for karmic and lucid at moblock-deb.sourceforge.net. They are called pgld and pglcmd.

---

### Post by iissmart on 2010-05-24
I've added your repository to my server, but I'm still using Hardy. You should make a package for it; there's still official support until 2013 (8.04 LTS). I'd love to get it set up!

---

### Post by clrg on 2010-05-25
You don't need any additional software for that. Just put the hosts you want your server to refuse any connection with in */etc/hosts.deny*.

The file should look like

> 
ALL: 123.321.12.21
ALL: 121.123.32.32
[etc]


---

### Post by jre on 2010-05-25
> **iissmart said:**
> I've added your repository to my server, but I'm still using Hardy. You should make a package for it; there's still official support until 2013 (8.04 LTS). I'd love to get it set up!
Thanks for your interest, I'd really like to help you. Unfortunately this is too much work for the time I have available.

Generally pgl should run under Hardy. There just might be problems once we have a working GUI, which requires newer Qt versions.

But the Debian/Ubuntu packaging itself requires a debhelper version >= 7.0.50~ which is not even available in hardy backports. Technically this means I would have to write a complete debian/rules file, instead of the current "minimal" one. Although this is not too hard, it definitely would mean that I can't take advantage of this and other debhelper advantages. In other words, I could fix that now, but most probably would have an increased workload in the future. So, sorry for that.

The only advice I can give is to either change to the new LTS lucid, or download the source and build it manually with "make && make install", or do your own backporting.


> **clrg said:**
> You don't need any additional software for that. Just put the hosts you want your server to refuse any connection with in */etc/hosts.deny*.

We're talking about hundreds of thousands of IP ranges here. E.g. the current (nearly paranoid) default setup has 162908 IP ranges (2991453638 IPs). I'm not aware of any other efficient solution in order to do this.

Further there are additional features (automatic blocklist update, allow/whitelists, ...)

---

### Post by compweisen on 2010-08-03
> **jre said:**
> I made the full release a few days ago! It still lacks the GUI, but otherwise it is superior to moblock/blockcontrol. 
Packages are available for karmic and lucid at moblock-deb.sourceforge.net. They are called pgld and pglcmd.


hehe ok so I am gonna take a look at peerguardian and see if it does what I need it to do.
I have a need to block IP's and URL's and perform reverse look up hopefully so that if I block Facebook and someone puts in the IP ... it gets blocked too...

funny thing I am using dansguardian right now and it is blocking sourceforge pages apparently there is a possible proxy redirector there. LMAO.

take a look at my work so far at my thread....
[http://ubuntuforums.org/showthread.php?t=1543738](http://ubuntuforums.org/showthread.php?t=1543738)

it is working at this point to block most bad everything malware i know about and porn duh outbound web proxies that allow a circumvent of blocking ....  now I just need to be able to apply a list of "good" websites that I want blocked. but my smart kids have already figured out that they can find the IP through whois and continue to do what they want...

any ideas I will look at pgl

---


---
title: "script to use OpenNIC: looking for testers"
date: 2013-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by vincezd on 2013-10-31
Hi all, 
I recently re-discovered the OpenNIC project:
[http://www.opennicproject.org/](http://www.opennicproject.org/)
[https://en.wikipedia.org/wiki/OpenNIC](https://en.wikipedia.org/wiki/OpenNIC)
In short, the OpenNIC project is an alternative DNS provider. Users of the OpenNIC DNS servers are able to resolve all existing ICANN top-level domains (TLD) as well as their own. You should use it if you're concern about censorship, if you don't like the internet domain names to be controlled by the US, etc.

While it is quite easy to configure with Network Manager, I wanted to script it :) So here is my attempt: [https://github.com/vindarel/open-nic](https://github.com/vindarel/open-nic)
It is working fine on my Debian, but [SIZE=3]**I'd like some more tests**[/SIZE] ! Can someone tell me it's working fine on his/her machine ? 

You may need that dependency: 
```
 sudo apt-get install python-pip && sudo pip install BeautifulSoup4
``` Can someone tell me if it's included by default in Ubuntu ? (you also need the resolvconf package but it's included in Ubuntu)

The command to download, run the script and start using OpenNIC:
```
wget https://raw.github.com/vindarel/open-nic/master/opennic-set.py && sudo python opennic-set.py
```

Now you should be able to visit openNIC's reserved Top Level Domains, like that site: [http://wiki.opennic.glue/SponsoredTLDs](http://wiki.opennic.glue/SponsoredTLDs) You can also run ```
python open-nic.py --test
```. You will use openNIC's servers for their own TLDs only, for **the usual sites you will carry on using your default DNS servers**  (the ones of your internet provider). For more information, please follow the github link.

Any observation welcomed.
Thanks in advance !

ps: your life isn't in danger :) if it doesn't work your surfing experience won't be affected. In the worst case, we need to put back a backup file (/etc/resolvconf/resolv.conf.d/tail.back)

---

### Post by bapoumba on 2013-10-31
Moved to Ubuntu, Linux and OS Chat.

---


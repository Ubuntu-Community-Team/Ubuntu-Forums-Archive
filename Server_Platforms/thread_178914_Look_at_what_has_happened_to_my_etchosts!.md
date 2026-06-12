---
title: "Look at what has happened to my /etc/hosts!"
date: 2006-05-18
forum: Server Platforms
---

### Post by caspar_wrede on 2006-05-18
Suddenly my hosts files contains a lot of suspicious looking crap. See below. How could this happen?? Where is it from? have I been hacked?


Begin /etc/hosts:

127.0.0.1 localhost.localdomain localhost kronos
192.168.0.122 erik   # network
192.168.0.180 erik   # network
192.168.0.148 erik   # wlan
192.168.0.159 elsa

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


# This MVPS HOSTS file is a free download from:           #
# [http://www.mvps.org/winhelp2002/](http://www.mvps.org/winhelp2002/)                        #
# Notes: the browser does not read this "#" symbol        #
# You can create your own notes, after the # symbol       #
# This *must* be the first line: 127.0.0.1     localhost  #
# ********************************************************#
# ------------------Updated: 12-28-05---------------------#
# ********************************************************#
# Entries marked with Parasite or Trojan comments should  #
# be placed in the Internet Explorer Restricted Zone.     #
# [http://mvps.org/winhelp2002/restricted.htm](http://mvps.org/winhelp2002/restricted.htm)              #
#                                                         #
# Entries with other comments are searchable via Google.  #
#                                                         #
# Disclaimer: this file is free to use, however it is NOT #
# permitted to post on any other site without permission. #
#                                                         #
# This work is licensed under the Creative Commons        #
# Attribution-NonCommercial-ShareAlike License.           #
# [http://creativecommons.org/licenses/by-nc-sa/2.0/](http://creativecommons.org/licenses/by-nc-sa/2.0/)       #

127.0.0.1  localhost

#start of lines added by WinHelp2002
# [Misc A - Z]
127.0.0.1  phpadsnew.abac.com
127.0.0.1  a.abnad.net
:127.0.0.1  b.abnad.net
127.0.0.1  c.abnad.net #[IE-SpyAd]
127.0.0.1  d.abnad.net
127.0.0.1  e.abnad.net
127.0.0.1  [www.accoona.cn](www.accoona.cn)
127.0.0.1  [www.accoona.com](www.accoona.com) #[Adware-Accoona][Adware.Atoolb][Panda.Accoona]
127.0.0.1  gtcc1.acecounter.com
127.0.0.1  gtp1.acecounter.com
127.0.0.1  acestats.com
127.0.0.1  [www.acestats.com](www.acestats.com)
127.0.0.1  data2.activshopper.com
127.0.0.1  search.activshopper.com
127.0.0.1  [www.activshopper.com](www.activshopper.com) #[McAfee.Adware-ActivShop]
127.0.0.1  [www.activesearch.com](www.activesearch.com) #[Adware.ActiveSearch]
127.0.0.1  actualnames.com #[Parasite.ActualNames][Spyware.ActualNames]
127.0.0.1  [www.actualnames.com](www.actualnames.com)
127.0.0.1  ad-up.com
127.0.0.1  [www.ad-up.com](www.ad-up.com)


... and so for a long time!

---

### Post by beeldings on 2006-05-18
First off, relax, you were not hacked.

It appears as if your hosts file was modified for use as an ad-blocker. If you want detailed information about the hosts file, visit [http://www.mvps.org/winhelp2002/](http://www.mvps.org/winhelp2002/) (as listed in your hosts file). If someone else uses your computer, perhaps they set up your hosts file to block ads and other malicious web sites.

---


---
title: "Syslog configuration"
date: 2011-01-03
forum: Server Platforms
---

### Post by john_mc on 2011-01-03
Hey all,

I have been tinkering with syslog on my Ubuntu 9.10 box to monitor my for a few days now. Today I cracked it with the help of posts from a number of users seeking support and kind souls offering advice. So I hope this helps someone. 

First off I disabled the firewall on my router and configured my Linux box with a static IP. Tested my routing works by getting replies pinging from [www.network-tools.com](www.network-tools.com) to my IP. 

After reading a number of threads I had no luck until I landed here:
[http://ubuntuforums.org/showthread.php?t=1623265](http://ubuntuforums.org/showthread.php?t=1623265)
# see the comment from ajoliveira

To view my log file I am using the the log viewer. See - [http://www.thegeekstuff.com/2009/11/ubuntu-tips-how-to-view-system-log-files-in-gui/](http://www.thegeekstuff.com/2009/11/ubuntu-tips-how-to-view-system-log-files-in-gui/)

When I reboot my router I get the NIC (Network card on my linux box) going down. Once powered back on my NIC comes back up and a few seconds later I see the LCP initiate between the router and exchange equipment. Then my PPP link comes up and I have the Internet.  

As I say I hope this helps someone and may not be able to offer much advice as I am a novice on linux and have a whole raft of new stuff to learn. Hopefully i will be able to see why my internet connection is so intermittent.

Happy for any advice from experts on using syslog to alert me when the connection goes down? understanding the log? Making it easier to use if I have more than one connection as I am not confident cahnging the syslog-ng.conf file? General tips?

G#Don't bang your head of the wall, hit the forums. There are some good folk about.

---


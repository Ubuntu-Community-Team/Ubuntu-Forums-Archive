---
title: "network hosts file"
date: 2013-01-11
forum: Server Platforms
---

### Post by Toriku on 2013-01-11
I want to use a single hosts file for all the computers on a network; I have a DNS server that they all use already, and a hosts file I acquired on the internet that blocks thousands of undesirable website addresses known to be associated with malicious programs.
 Can I use the hosts on my DNS server for all the machines on the network, or would it be easier to improvise a domain zone for blocked websites with all the addresses listed? (on reflection not sure how I'd improvise this...)

---

### Post by SeijiSensei on 2013-01-11
I suspect you're referring to the "[malware block list]("http://www.malware.com.br/lists.shtml")."  If you're trying to institute filtering for a whole network of users, I recommend looking into setting up a [transparent Squid proxy]("http://ubuntuserverguide.com/2012/06/how-to-setup-squid3-as-transparent-proxy-on-ubuntu-server-12-04.html").  There is a [Squid version]("http://www.malware.com.br/cgi/submit?action=list_squid") of the MBL that I use on a client's Internet gateway, along with a variety of other custom filtering rules.  We run a cron job to update the list every four hours.  We also use the MBL version for SpamAssassin to block emails with dangerous URLs.

If you have any reasonable number of workstations on your network, filtering by using hosts files on every machine is a pain in the butt.  Centralize the filtering at the egress gateway with Squid.

---

### Post by Toriku on 2013-01-18
thanks, I'll read into Squid now

---


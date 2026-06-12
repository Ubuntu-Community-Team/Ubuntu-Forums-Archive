---
title: "Inadyn issues"
date: 2014-08-28
forum: Server Platforms
---

### Post by Ettienne_Gous on 2014-08-28
Hi all looking for some advice on getting Inadyn to work
I found this guide but it seems dated as the config file doesnt look the same as the example anymore and there was already a file located in etc/init.d/inadyn by default.
[http://blog.schmidt.br.com/2012/04/installing-dyndns-inadyn-as-service-on.html](http://blog.schmidt.br.com/2012/04/installing-dyndns-inadyn-as-service-on.html)

I have a older version of this script that worked perfectally on an older version of ubuntu.  

I had to now set it up again for 14.04.
This is what I found

Just running 
sudo inadyn --test
Thu Aug 28 20:41:08 2014: No DDNS provider setup in configuration.
Thu Aug 28 20:41:08 2014: Failed starting daemon: RC_DYNDNS_INVALID_OR_MISSING_P

However if I run 
sudo inadyn --config /etc/inadyn.conf --test
It works as expected.

My next step was to try and register the script to run on start with 
sudo update-rc.d inadyn defaults

After restarting a few times I realised the service never starts.

If I run this command after a restart
sudo service inadyn start 
It fails with
 * Starting DynDNS client  inadyn [fail]
Checking /var/log/inadyn/inadyn.log shows nothing.

However if I run 
sudo inadyn --config /etc/inadyn.conf --test
And then run  
sudo service inadyn start 
The service starts and works as expected.

Any advice on how to get the service to start on boot correctly will be greatly appreciated.

---

### Post by robenroute on 2014-11-27
Hi there, Ettienne. I'm more or less struggling with the same issues. The last time I set up inadyn (for remote desktop use) was on the previous LTS version of Ubuntu (12.04) and everything worked straight away. I would appreciate any help from other forum members.

Many thanks.

---


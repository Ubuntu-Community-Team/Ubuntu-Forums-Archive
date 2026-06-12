---
title: "Awstats with Virtual Hosts"
date: 2008-03-07
forum: Server Platforms
---

### Post by coas50 on 2008-03-07
I'm having trouble getting Awstats to work with virtual hosts. I was able to get Awstats installed and working with one of Apache's virtual hosts, but not with the others. So far I have not been able to find a good tutorial on how to get Awstats working with multiple virtual hosts. Can someone point me in the right direction? I'm using one IP address and Name-Based virtual hosts to direct Apache to the right directory. My apache directory structure is as follows:

example-site-one.com
htdocs
logs

example-site-two.com
htdocs
logs

example-site-three.com
htdocs
logs

Thanks in advance for any help you can offer.

---

### Post by Oldsoldier2003 on 2008-03-07
> **coas50 said:**
> I'm having trouble getting Awstats to work with virtual hosts. I was able to get Awstats installed and working with one of Apache's virtual hosts, but not with the others. So far I have not been able to find a good tutorial on how to get Awstats working with multiple virtual hosts. Can someone point me in the right direction? I'm using one IP address and Name-Based virtual hosts to direct Apache to the right directory. My apache directory structure is as follows:

example-site-one.com
htdocs
logs

example-site-two.com
htdocs
logs

example-site-three.com
htdocs
logs

Thanks in advance for any help you can offer.
sounds like an issue with your awstats configuration.. have you gone through the documents on enabling multiple sites? I'm guessing you missed an option or configuration path somewhere.

---

### Post by coas50 on 2008-03-12
I have set up an awstats conf file for each of the virtual hosts. They are located in ect/awstats/. It looks like this:

awstats.example-site-one.com.conf

awstats.example-site-two.com.conf

awstats.example-site-three.com.conf

Each of the files are set up like to following:
LogFile="/var/www/www.example-site-one.com/logs/access.log.1"
LogFormat=1
SiteDomain="www.example-site-one.com"
HostAliases="example-site-one.com"

I'm not sure what else I might be missing. When try to view the stats by going to 
example-site-one.com/cgi-bin/awstats.pl?config=www.example-site-one.com

I'm getting stats from what appears to be all three of the sites and not just the one I'm requesting. Any help would be greatly appreciated!

---

### Post by tubezninja on 2008-03-12
Are all of your virtual hosts writing to the same log?  If so, then awstats is going to read the entire log and compile whatever's there, including the stats from other sites.  You'll need to set up the .conf files for each virtual host to write to separate log files.

---


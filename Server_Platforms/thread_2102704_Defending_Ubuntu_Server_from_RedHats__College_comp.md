---
title: "Defending Ubuntu Server from RedHats?  College competition."
date: 2013-01-07
forum: Server Platforms
---

### Post by Roskow on 2013-01-07
I have some moderate experience with Ubuntu Terminal on both the desktop and the server, but self taught and learning. I'm in college for IT Security and joined a campus Cyber Defense team that accepts newbies.  

The goal is for each team member to learn an OS. Some people will be in charge of Fedora or Windows or Routers/Switches on a LAN Network and my OS is Ubuntu Server. 

While previewing this forum I've seen a sticky post on Security which is a great resource, but wondered if I should ask for specific recommendations to narrow down what I really need in my situation. 

This college team will compete by securing the network against a RedHat team that will attack us. My understanding is whoever keeps up the Network services without being knocked out, having services hacked, or lasts the longest wins.  

On the network my server service will just be MySQL(another thing I'm learning). So far I have MySQL installed and accessed by a Windows machine on the LAN with a Web browser and PHPMyAdmin.  

Aside from that I think I should close up the server as much as possible with UFW. My team leader said we don't need to be concerned with SSH so I should close that off. One question I had is if UFW is enough or if I need to mess with learning IPtables?  If MySQL is involved should I learn Snort? 

Also, I looked into Fail2Ban and wondered if that can work with UFW?  If that can be used to shutout RedHats doing a brute force attack?  

This is a big security job and I don't expect people to respond with lengthy tutorial posts. If I can get recommended security tool names for my specific situation, or advice on what I don't really need, that would help me focus on the really essential tools. 

For example, I've looked at Nagios3 Core and while it sounds powerful I'm wondering if that is overkill. Since MySQL is involved I wondered if I should learn Snort?  I stumbled across an alternate to Apache2 called Hiawatha and wondered if that was even worth messing with? 

Aside from purely defensive tools I've messed vulnerability tools like Nmap and TCPdump a little bit. Next I'm looking to install Nessus. 

This week winter break ends and I actually start Intro to Linux/Unix class at college so that should be a big help.

---

### Post by Wim Sturkenboom on 2013-01-08
I'm not the specialist on the security subject. Regarding MySql however I would suggest that the MySql root user can only gain access via localhost and not via any other means (so throw away phpmyadmin ;)); to achieve this, remove all root users in the MySql user table except the one for localhost. This implies that the only means to access the MySql databases on the machine for the MySql root user is via physical access to the machine or via SSH and work remotely on it for MySql maintenance. 

Create other MySql users with more limited privileges that can be used to access the databases remotely; e.g. for webpages that only need to display data from a database, create a MySql user that has only select privileges on tables in that database and use that user in e.g. PHP scripts.

The MySql root user can create databases. Create a dedicated user that can do maintenance on a database (e.g. create / drop tables), only via the local network. There is no need to that via webpages. If it needs to be done from the outside world, again use SSH.

Note that MySql is usually part of a bigger picture. Somebody needs to be able to input data in it, so consider from where that's going to happen. Internally or via the web? There is nothing that you can do if webpages allow for MySql injection due to poor design.

---

### Post by mastablasta on 2013-01-08
> **Wim Sturkenboom said:**
>  This implies that the only means to access the MySql databases on the machine for the MySql root user is via physical access to the machine or via SSH and work remotely on it for MySql maintenance. 
 
briliant! how about just unplugging the network cable from the server? that will show them.... :P 
ofcourse depends on what the sevrer has to be doing, but presumably it has have an option to be accessed from outside and probably perform certain funcitons for it to be considered functioning.
 
> 
There is nothing that you can do if webpages allow for MySql injection due to poor design.
how about virtualising the thing? creating jails or something similar?! and making snapshots. so even if it gets breached you could restore fast and put them back on suqare one.
 
have a look at this concept: [http://distrowatch.com/table.php?distribution=qubes](http://distrowatch.com/table.php?distribution=qubes)
 
also use hardened kernel. i am sure m server people will add better options....

---

### Post by Roskow on 2013-01-08
Thanks for the feedback.  When class and these Cyber Defense meetings start up again I'll ask for more specifics on MySQL as a Service. I think there is a neutral team of users that need to access our network just like customers. I need to find out what they need to access and how. If it will involve the Web that might mean doing something about Apache2. 

It doesn't help I'm completely new to MySQL but I'm willing to learn. I'll eventually have a MySQL college class anyway. 

In the meantime I think everyone on my team needs to get their Servers running in a classroom LAN with some security just for a starting point.  Then hopefully we can start reviewing the system and getting a plan together.

---

### Post by Wim Sturkenboom on 2013-01-08
> **mastablasta said:**
> briliant! how about just unplugging the network cable from the server? that will show them.... :P 
ofcourse depends on what the sevrer has to be doing, but presumably it has have an option to be accessed from outside and probably perform certain funcitons for it to be considered functioning.

Either reading is not your strong point or explaining is not mine. There is NO need for a **MySql [COLOR="Red"]root[/COLOR] user** to connect to the MySql server from outside the local host.
> **mastablasta said:**
> 
how about virtualising the thing? creating jails or something similar?! and making snapshots. so even if it gets breached you could restore fast and put them back on suqare one.

Restoring databases is the least of your worries if all sensitive data has been stolen.

---

### Post by mcduck on 2013-01-08
That sounds exactly like a competition where you could probably have some fun with the extremely feature-rich Arno's iptables firewall script: [http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=46&Itemid=77]("http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=46&Itemid=77")

It has a bit more intrusion detection mechanisms built in than UFW does, and with a bit of creativity you can also do some fun stuff like in case of a detected attack, randomly drop some of the attack packages, or redirect some back to the sender etc... (not really that useful in real life, but you could have some fun at the other team's expense... :D)

---

### Post by howefield on 2013-01-08
Thread moved to the "*Server Platforms*" forum.

---

### Post by Roskow on 2013-01-08
> **mcduck said:**
> That sounds exactly like a competition where you could probably have some fun with the extremely feature-rich Arno's iptables firewall script: [http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=46&Itemid=77]("http://rocky.eld.leidenuniv.nl/joomla/index.php?option=com_content&view=article&id=46&Itemid=77")

It has a bit more intrusion detection mechanisms built in than UFW does, and with a bit of creativity you can also do some fun stuff like in case of a detected attack, randomly drop some of the attack packages, or redirect some back to the sender etc... (not really that useful in real life, but you could have some fun at the other team's expense... :D)

I'm not sure if we're allowed to attack the other team, but they might allow some kind of Honeypot.

---

### Post by Roskow on 2013-01-20
Trying this thread again because the rules for the competition have changed.  

I'm now supposed to be running DNS and some education program called Moodle.  I could choose to run both on a single server but I'm leaning toward running these services separately on 2 machines. Either way these will be running in VMware or VirtualBox. 

A basic security question I have regarding Moodle is should I run it with a standard LAMP server?  Or should I look for any alternative programs like Cherokee for example? Or the more obscure web server Hiawatha which is supposedly more secure?

Also, I confirmed that Honeypots are not allowed. As far as I know our task it to do our best to keep services running while knowing we will be attacked.

---

### Post by Habitual on 2013-01-20
[LAMP, yes.]("http://docs.moodle.org/24/en/Installing_Moodle")

---

### Post by LHammonds on 2013-01-21
Make sure you separate your partitions for added security and stability of the OS.  I have a link in my sig that talks about how I configure the partitions in all my servers which allows me to keep the servers up-and-running even if log files go crazy and start filling up space (which will notify me via email and increase space automatically to accommodate growth).

Never allow your root partition to become full.  The default setup puts everything in one partition (root parition) which is not something you would want to do for a production server.  It is ok for home use, testing or development but not production.

After you install MySQL, there are a few things you can do to tighten up security a bit more such as removing guest access and other things.  I also have some of that info documented in a link in my sig.

LHammonds

---

### Post by Roskow on 2013-01-22
> **Habitual said:**
> [LAMP, yes.]("http://docs.moodle.org/24/en/Installing_Moodle")

Okay I did see LAMP was the standard recommended server to run on but wondered if I should consider other options. I guess because I figured LAMP was very standard and Hackers would be ready with tools to pick at Apache.  So I thought using it might be worth looking at a less conventional setup.  

I did get Moodle going on LAMP for now though and next I'll work with managing DNS. I'll go through my notes to secure it as best I can and then throw Backtrack, Nmap, and Nessus at it.

---

### Post by Roskow on 2013-01-22
> **LHammonds said:**
> Make sure you separate your partitions for added security and stability of the OS.  I have a link in my sig that talks about how I configure the partitions in all my servers which allows me to keep the servers up-and-running even if log files go crazy and start filling up space (which will notify me via email and increase space automatically to accommodate growth).

Never allow your root partition to become full.  The default setup puts everything in one partition (root parition) which is not something you would want to do for a production server.  It is ok for home use, testing or development but not production.

After you install MySQL, there are a few things you can do to tighten up security a bit more such as removing guest access and other things.  I also have some of that info documented in a link in my sig.

LHammonds

Thanks for the info.  I have seen your Nagios post but wasn't sure if my setup fit with the "assumptions" about my system. 

Also, my home practice machine is an old DesktopPC while at school and this competition I'll probably be running on VMware. I'm not sure how different that would be in regards to partitions.  I'll have to look into how I install in VMware.  

I'll save your Sig links for later reference.  Thanks.

---

### Post by koenn on 2013-01-22
your goal is to keep given services up, while you know you're server is going to be attacked. 
It's obvious then that a Denial of Service is going to be one of the likely scenarios.
Trying to fill up disks until something stops working by lack of disk space might could be one of the DoS attempts - one that is easier to deal with if you have directories such as /tmp or /var/log on their own partition - it keeps that junk out of your root directory, which helps keep your system up. Or you can make them as large as possible by mounting a huge volume over NFS. 
That's one way partitioning matters, even in VM. 

Also, reduce your footprint. Don't run services you don't need. If you're not going to use ssh, don't simply block it in a firewall, uninstall the ssh server, or at least make sure it doesn't start up.
You don't know how you're going to be attacked, so the fewer holds your attacker has the better. 


And assume the enemy knows the system. In this case, it's very likely the attacking team knows you'll be running Moodle. Obviously, they'll research known vulnerabilities and attack them.  Make sure your research is at least as good as theirs.

Lastly, don't forget the obvious. You'll probably be relying on DNS to have your clients find and connect to your moodle. Messing up DNS is all it takes to render your Moodle program inaccessible - DoS successful. 

Small extra : since you're be working in a team : disable root, give everyone his own account, and use sudo as needed. This covers a handful of smaller risks (no need to communicate root passwords, easy to change passwords regularly, brute force password attacks are harder because they need both an account name and a password, ...) and gives you a log of all root actions - including failed attempts to get root. 

That takes care of the lowhanging fruit (assuming the usual security stuff such as having strong passwords, measures against passwords in clear text on your network, ... ).

---

### Post by Roskow on 2013-01-22
Thanks Koenn and everyone for the great feedback.  

The competition is in March so I'll post a followup of the results. The program accepts and encourages Noobies and we are a mixed bunch with different skill levels. I want to put in a decent effort though and at least not get steamrolled over.  

I guess I'd say a main resource to prepare is also play with Backtrack.  I have Nessus installed and hope to detect the weaknesses in my server.

---


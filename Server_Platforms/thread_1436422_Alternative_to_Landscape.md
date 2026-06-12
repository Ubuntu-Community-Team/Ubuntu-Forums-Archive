---
title: "Alternative to Landscape?"
date: 2010-03-22
forum: Server Platforms
---

### Post by ronzo on 2010-03-22
Is there a free alternative to Canonical Landscape that allows to manage (e.g. keep systems up-to-date) several machines in my LAN?

---

### Post by ffxigotenks on 2010-05-25
I'm also trying to find something like this, anyone?

---

### Post by Brazen on 2010-05-25
Puppet is a command line tool that can manage groups of servers.

[http://www.puppetlabs.com/](http://www.puppetlabs.com/)

---

### Post by ffxigotenks on 2010-05-26
I've tried that, but I can't seem to get it to work, 
[http://ubuntuforums.org/showthread.php?p=9359057](http://ubuntuforums.org/showthread.php?p=9359057)

---

### Post by anarkhos on 2010-10-13
Has anyone found a real Landscape alternative?

These options are decent: 
munin, ganglia, scout, cacti, puppet, webmin, ebox

... but Landscape is web-based *and* it monitors multiple servers.  So, patching together a few of those services is not really what I'd prefer.

Is there perhaps a new project out there (even a brand new one) that I didn't mention above, which is trying to provide a full-fledged alternative to Landscape/Spacewalk?

---

### Post by hkphooey on 2010-10-14
There is some progress to get spacewalk running on debian based systems:
 [https://fedorahosted.org/spacewalk/wiki/Deb_support_in_spacewalk](https://fedorahosted.org/spacewalk/wiki/Deb_support_in_spacewalk)

But it seems to have stalled, as it was part of someone's thesis. 

If your requirements are modest, you might like to look at clusterssh, which will basically run the same commands via ssh on several servers simultaneously. So if all you're trying to do is 
 ```
apt-get update ; apt-get upgrade
```
on several machines, then that works pretty well. 

Have to say I'd quite like something like this too.

---

### Post by aschmitz on 2011-04-17
I know this is quite the old thread, but it's possible that people here are still interested in an alternative to Landscape, so I'm posting here in case that's true.

I'm trying to gather support for making an open source alternative to Landscape, which I'm calling Portrait. I have a fair amount of the code for interacting with the computers, but it will still take a fair amount of work to get it cleaned up and made into a useful service. If I can gather enough support to let me work on it over the summer, I'll be able to release the code as open source and run a hosted copy that's a lot cheaper for people to use if they don't want to set up their own copy. 

I'm using Kickstarter to try and gather support. If you think it's something that would be useful for you, please take a look at [the Portrait Kickstarter project page]("http://www.kickstarter.com/projects/aschmitz/portrait-linux-system-management-tool"). Kickstarter works with a fundraising goal and deadline: people can pledge their support (in exchange for rewards) at any level they want. If the goal is met by the deadline, everyone pays and the project gets underway. If the goal isn't met, nobody pays anything.

There's not much time left before my deadline, so I'm hoping that I can get enough support so that I can spend the necessary time over the summer making Portrait ready for release. Please take a look at the Kickstarter page for Portrait if you want more information, or feel free to contact me. (In terms of an open source license, I haven't yet decided, but I'm leaning toward the AGPL v3.)

The project page is at [http://www.kickstarter.com/projects/aschmitz/portrait-linux-system-management-tool](http://www.kickstarter.com/projects/aschmitz/portrait-linux-system-management-tool) .

(If you have a company that might be interested in sponsoring Portrait, that would certainly help too - even sponsoring the entire project is probably less expensive than paying for someone to write the software from scratch.)

---

### Post by anarkhos on 2011-08-06
Anyone have any new insights to this quest of a free Landscape?

---

### Post by jrstmartin on 2012-12-20
I know this is an old thread, but the Internet is forever. I stumbled upon this looking for a Landscape alternative. In a round-about-way, I think [Vagrant]("http://vagrantup.com/"), through [VirtualBox]("https://www.virtualbox.org/"), is *sort-of* a way to manage the installation profiles of multiple machines. It's going to be my solution for providing fellow developers with a particular development environment. Hope this helps...

---

### Post by neuman1812 on 2013-03-10
Just adding to the Old thread here.   I would also like to see a free version of a Landscape like product.    I have several Ubuntu systems including cli servers, on my lan, but I also manage family and friends Ubuntu systems.  A landscape product would make seeing them "at a glance"  much easier to update and resolve issues.  

Currently I Use Webmin installed on each system,  but if the home IP changes..that makes it difficult.

---

### Post by smeerbartje on 2013-03-10
Why not creating a web service where you push external ip addresses to? (by using a cronjob). All the servers I manage have a cronjob which opens a url and then the server stores the email adress. Simple as that.

---

### Post by LHammonds on 2013-03-12
I don't know much about Landscape but I use Nagios to monitor all my network equipment (Windows servers, Ubuntu servers, switches, printers, etc.) and I also have a script in a crontab schedule to automatically applies all security updates on a daily basis (and logs the results).  I also have partition backups scheduled to automatically run and make a backup on the local server as well as copying to a remote offsite server.

For non-linux people to manage my servers, I have a script that presents them with a menu of common operator options such as the need to restart services, reboot, check disk space, check running processes, etc.

All of this can be found in my signature.  There are various links to threads covering step-by-step how I have done these things.

LHammonds

---


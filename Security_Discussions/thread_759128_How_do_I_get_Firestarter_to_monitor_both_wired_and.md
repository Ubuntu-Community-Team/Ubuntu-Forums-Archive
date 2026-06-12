---
title: "How do I get Firestarter to monitor both wired and wireless connections?"
date: 2008-04-18
forum: Security Discussions
---

### Post by WebDrake on 2008-04-18
Hello all,

I had a rather nasty shock the other day.  I have Firestarter on my machine and for some unknown reason (divine inspiration...) decided to load it up just to check on the firewall.  Whereupon .... I discovered that the firewall was not enabled.

It seems that Firestarter was waiting for wlan0 to be connected and since at the time I was using eth0, it was waiting in vain.

So, I re-ran the setup wizard and told Firestarter to monitor eth0, and then, later, went home, where I and my flatmates use a wireless router for internet.  I immediately checked Firestarter and sure enough the firewall was again not enabled -- this time because it was attempting to monitor eth0 instead of wlan0.

How can I get Firestarter to monitor both possible network devices?  It seems crazy to have to manually reset the config every time I switch between wired and wireless connections.

Thanks in advance for any answers.

     -- Joe

---

### Post by oilchangeguy on 2008-04-18
> **WebDrake said:**
> Hello all,

I had a rather nasty shock the other day.  I have Firestarter on my machine and for some unknown reason (divine inspiration...) decided to load it up just to check on the firewall.  Whereupon .... I discovered that the firewall was not enabled.

It seems that Firestarter was waiting for wlan0 to be connected and since at the time I was using eth0, it was waiting in vain.

So, I re-ran the setup wizard and told Firestarter to monitor eth0, and then, later, went home, where I and my flatmates use a wireless router for internet.  I immediately checked Firestarter and sure enough the firewall was again not enabled -- this time because it was attempting to monitor eth0 instead of wlan0.

How can I get Firestarter to monitor both possible network devices?  It seems crazy to have to manually reset the config every time I switch between wired and wireless connections.

Thanks in advance for any answers.

     -- Joe

firestarter is not ubuntu's firewall. it's simply a user interface, for iptables.

---

### Post by WebDrake on 2008-04-19
Can you explain further, please?

---

### Post by wrightci on 2008-05-18
What I think the posting is asking is how do you overcome the fact that Firestarter (during configuration) asks you to choose between EITHER eth0 or eth1 or whatever your interface is called.

I have the sameish question really - during configuration I am given the choice of eth0 (wired) or eth1 (wireless) and I must select one or the other. I cannot find anything in the documentation at [http://www.fs-security.com/]("http://www.fs-security.com/")
that might indicate if and how you can get firestarter to monitor BOTH rather than just one or the other.

The backend file that stores your selection is I think found by the following grep:
root@ad2k1g:/etc/firestarter# ls
configuration        firestarter.sh  non-routables  user-post
events-filter-hosts  firewall        outbound       user-pre
events-filter-ports  inbound         sysctl-tuning
root@ad2k1g:/etc/firestarter# grep eth *
configuration:IF="eth0"
configuration:INIF="eth0"
configuration:# Packet rejection method
sysctl-tuning:#  altogether by commenting out this option)

So the question for me is can you put IF="eth0 eth1" in /etc/firestarter/configuration and have the firestarter binary
understand it?

There is nothing in the pdf user manual I just downloaded to suggest firestarter can cope with this.

Note: To the original poster (Webdrake)
One thing I did get from reading the pdf manual for firestarter was perhaps  if there is no ideal solution then you might in fact be able to quickly change between wired and wireless from the graphical interface by doing 'Edit/Preferences/Network' and doing 'stop firewall' then 'start firewall' once you are done there. Still not ideal I know but might be a quicker option than reconfiguring another way.

About firewalls and Ubuntu: To the best of my shaky knowledge Ubuntu does not have a default firewall but rather adopts a minimal ports approach when the default install is completed.
To clarify: You are free to choose from several available firewalls to help you once you do start opening up ports/creating network connections. One of the firewalls available is firestarter (I use it for desktops) - there are several more including firehol, filtergen (I have used filtergen for servers as no need for interactive firewall).
A web search for 'ubuntu firewall' or 'debian firewall' will give some more hints about what other users are finding work well.

---

### Post by jimmy the saint on 2008-07-01
iptables is Ubuntus default firewall as it is integrated into the Linux kernel.  I am also concerned about this though and am looking for a solution.  Is there one out there?  I use my laptop wirelessly at home and via a wired connection on the job.  I really don't want to have to go through the trouble of reconfiguring twice a day.

---


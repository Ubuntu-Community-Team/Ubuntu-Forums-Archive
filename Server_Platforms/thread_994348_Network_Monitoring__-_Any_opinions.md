---
title: "Network Monitoring  - Any opinions?"
date: 2008-11-26
forum: Server Platforms
---

### Post by quietas on 2008-11-26
I've recently had our old Debian 3 box die. It had been running a rather old version of Nagios, but it did give us basic notifications when network devices were down.

I'm looking at replacing it with a new NMS system, but is Nagios the right software for the task or is something else out there better suited?

Here's my network details:
4 remote locations, each with a Cisco 2600 providing VLAN access, Dell managed switches at each as well, 1 even more remote location via VPN with Linksys soho products.

The main office has 2 Win2k DC's (primary/secondary), with DNS, DHCP, file serving, and such. Then there is a Win2k3 server with MS SQL, a Win2k3 Citrix server, and a Win2k3 application server. Along with that I have two Ubuntu mail servers running Zimbra (one live, one as a hot spare). Internally I also have two Ubuntu servers running the Intranet site. Voicemail server using Win2k, and 2 Novell servers with god awful proprietary essential database apps.

Plus I have the phone pbx's at each location, printers, switches, routers, and whatnot that all need to be watched.

What out there would be the best to monitor all this and more? Realtime crash notification for critical components is essential, trending would be nice, and monitoring up individual services such as SMTP/IMAP/HTTP/FTP and such. If it's in the repo's somewhere that's a bonus since it would be easier to maintain as long as it is reasonably up to date.

I've looked at Nagios, ZenOSS, Zabbix, OpenNMS, and more. Many do the same, but with all the propaganda I am not sure what would do the job I need.

---

### Post by Vegan on 2008-11-26
There is no simple tool I am aware of to manage a wide buch of gear. I use telenet to manage most stuff and web for others. 

:guitar:

---

### Post by hictio on 2008-11-26
I use Nagios, MRTG & Zabbix.
Yeah, I know, MRTG it is not for monitoring per se :D

Nagios for early warning (haven't found anything that works better) and Zabbix for trending and hardware calculations/ escalations/ projections.

---

### Post by quietas on 2008-12-01
Darn, I was hoping for an all in one sort of monitoring and trending. I used to use Nagios for crash warnings, it worked great for emailing text messages, but it lacked any sort of reporting.

---

### Post by hictio on 2008-12-01
> **quietas said:**
> Darn, I was hoping for an all in one sort of monitoring and trending. I used to use Nagios for crash warnings, it worked great for emailing text messages, but it lacked any sort of reporting.

Excuse me, what do you mean by "reporting"? Is it like trending?
If so, Nagios does support that, to an extent, of course, it can't compete with Zabbix, but you get some trending too.

---

### Post by quietas on 2008-12-01
Sorry, if I was not specific. Yes, I meant trending and you are right Nagios does it somewhat, but very rough.

I just ran across [Ground Work]("http://www.groundworkopensource.com"), it seems quite decent combining alot of Monitoring and reporting in a clean interface. Has anyone used it with Ubuntu?

---

### Post by CrucifiedEgo on 2008-12-01
Does anyone know of a way to make nagios report actual data in that form (similar to what munin does?)

---

### Post by quietas on 2008-12-02
It seems OpsView might work as well.

---


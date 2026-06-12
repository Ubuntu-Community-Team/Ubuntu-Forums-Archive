---
title: "weekly report for server setup"
date: 2010-11-05
forum: Server Platforms
---

### Post by tapas_mishra on 2010-11-05
I have setup a cluster for some one.Which is basically a few Virtual
Machines running and the applications running in them which are
accessible on internet.
The host os is Ubuntu and  Vms are some ubuntu/debian and some
Fedora/Redhat based servers.
He has asked me to send him a weekly report of this work.
I am sys admin guy who understands ssh,telnet,ftp,tftp,TCP
I am not able to understand what should I write in report.Because all
the servers are perfectly running and applications are also running on
top of them and I am done with this.So basically from my part I do not
have any ssh or ftp to write in a report like this.Can some one give
me a link if there is some sample report that I should send.I am not
able to understand what do I need to Google for the same.
Are there any tools for doing such stuff? Or what exactly should I be Googling for this situation?

---

### Post by TSJason on 2010-11-05
There are lots of tools that can be used to gather statistical data (read: monitor) about servers and their services. One of my favorites (when paired with snmp) is OpenNMS. Check it out: [http://www.opennms.org/](http://www.opennms.org/)

It has the ability to generate reports and graphs as needed and probably will provide the technical data that he's wanting.

---

### Post by CharlesA on 2010-11-05
I'd suggest what asking what they would like on the report and going from there.

---

### Post by tapas_mishra on 2010-11-08
> **CharlesA said:**
> I'd suggest what asking what they would like on the report and going from there.
I understand your point I have asked them.Probably it seems they are also not very clear in this part.So I have to show my creativity.What I understand is they might be looking for some availability of fault tolerance,capacity downtime,upload work time or such problems so that in an event of failure they can look back at the reports and understand what happened.I came to know of one such tool on Solaris BMC Patrol is there any thing equivalent or similar to it for Ubuntu?

For example I wish to write such a sentence in report
> The cluster has ample resources to handle the peak workload. The fault  tolerant hardware helps to ensure that the cluster will continue to  provide service in the event of a hardware failure.How can put the above sentence with facts supporting my argument in report any sort of log analyzers?

When did system had maximum load when minimum load.
Who is using the computer and how they use ?
A batch job to create resource usage reports and use this data to create graphs. The horizontal axis is time, the  vertical axis is percent of resource usage, different color lines  represent memory, cpu, network traffic, disk i/o, etc.
Report could include a judgment about the ability of the machine to  handle the workload on an hourly, daily, weekly, and peak use basis.

---


---
title: "Issues with Snort generating log entries"
date: 2014-04-07
forum: Security
---

### Post by Rameez_Qureshi on 2014-04-07
hello


I am having some problems with Snort, I have installed all of its dependencies and changed the snort.conf file to suit my setup and added filepaths etc but to no avail.


When running snort in packet dump mode and saving it to a log it opens with wireshark and displays all the packets, however when running it in IDS mode it also picks up all the packets but does not generate any logs. The tests I am doing to test snort are basic ping scans, nmap scans and failed MSF exploits however Snort does not seem to be generating any logs for this.


I suspect the problem may  lie with the whitelist & blacklist rule files that I dont have and am unaware of where to get them


I have attached my output when running snort in IDS mode and also my snort.conf file in 3 seperate parts due to the filesize limit being 20.kb for a .txt file


Any help is greatly appreciated

---


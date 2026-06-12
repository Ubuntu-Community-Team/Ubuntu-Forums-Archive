---
title: "VMware 2.0 Help"
date: 2009-07-25
forum: Virtualisation
---

### Post by NetSplitter on 2009-07-25
[COLOR=black][FONT=Verdana]Ok, I have been fighting with my VMware Server 2.0.1 for two days now. I have done everything I can think of, I feel I know what the problem is, but I don't know how to fix it. I cannot access my VMware from the web interface anywhere besides the actual server. I am using port 902 and I can telnet to that port from a remote computer and I get the correct message. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The message I receive after trying to open my VM is "Unable to connect to the MKS: Cannot connect to host computername : No connection could be made because the target machine actively refused it."[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have xinetd but the configuration file doesn't look right to me, in /etc/xinetd.conf
Xinetd is started![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]------------------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# Simple configuration file for xinetd[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]#[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# Some defaults, and include /etc/xinetd.d/[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]defaults[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]{[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# Please note that you need a log_type line to be able to use log_on_success[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# and log_on_failure. The default is the following :[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]# log_type = SYSLOG daemon info[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]}[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]includedir /etc/xinetd.d[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-----------------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In /etc/xinetd.d all the files in there are "chargen" "daytime" "discard" "echo" "time" I've read in other forums about an vmware-authd suspoced to be there, but I have a file in pam.d called vmware-authd, but logging into the web interface is flawless.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have the proper permissions, and I have added the 902 port in /etc/service on the VM server. I have reinstalled VMware twice and still nothing. I am using Ubuntu 9.04.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any help would be appreciated![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you.[/FONT][/COLOR]

---


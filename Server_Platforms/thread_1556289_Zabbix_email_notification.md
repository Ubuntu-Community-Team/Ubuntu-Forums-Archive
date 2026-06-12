---
title: "Zabbix email notification"
date: 2010-08-19
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-19
I've installed zabbix monitoring tool of ver 1.6.x. I got stuck with configuring email notification that notifies to my gmail account and I have only postfix installed.
Plz could anyone help giving step by step guide to sort out this issue.

Thanks all!

---

### Post by Thyagaraj on 2010-09-06
I've installed zabbix version 1.8.3. The following media settings worked fine on my local machine and got mail notification. But the same settings failed on real servers.

Here is my zabbix media settings

Media 
Description:	
Type	               E-mail
SMTP server:   localhost	
SMTP helo:      localhost	
SMTP email: zabbix@localhost


 			 			Zabbix E-mail notification error(audit->actions):

Cannot connect to SMTP server [localhost] [gethost() failed for address 'localhost' [Success]] 		
 		  		  		 		  		  		  		  		 			 			 				[IMG]http://www.zabbix.com/forum/images/misc/progress.gif[/IMG] []("http://www.zabbix.com/forum/editpost.php?do=editpost&p=71451")

---

### Post by Thyagaraj on 2010-09-08
Here are my settings.


/etc/hosts:

127.0.0.1               localhost.localdomain           localhost
<my-ip-here>   station1.lab.mycompany.com   station1



_/etc/zabbix/zabbix_agentd.conf_:

# Default:
# Server=

Server=127.0.0.1

### Option: Hostname
#       Unique, case sensitive hostname.
#       Required for active checks and must match hostname as configured on the server.
#
# Default:
# Hostname=system.uname

Hostname=Zabbix server

### Option: ListenPort
#       Agent will listen on this port for connections from the server.
#
# Mandatory: no
# Range: 1024-32767
# Default:
# ListenPort=10050



_/etc/zabbix/zabbix_agent.conf_:

# This is a config file for zabbix_agent
# To get more information about Zabbix visit [http://www.zabbix.com]("http://www.zabbix.com/")

### Option: Server
#       IP address of Zabbix server
#       Connections from other hosts will be denied
#       If IPv6 support is enabled then '127.0.0.1', '::127.0.0.1', '::ffff:127.0.0.1' are treated equally.
#
# Mandatory: yes
# Default:
# Server=

Server=127.0.0.1

### Option: Timeout
#       Spend no more than Timeout seconds on processing
#
# Mandatory: no
# Range: 1-30
# Default:
# Timeout=3




_Hostname_:
root@station1:~#hostname
station1.lab.mycompany.com

---

### Post by Thyagaraj on 2010-09-13
Any tricks or tips from any one.

---

### Post by Thyagaraj on 2010-09-14
logs of /var/log/mail.log

Sep 14 05:46:32 station1 postfix/smtpd[490]: connect from localhost.localdomain[127.0.0.1]
Sep 14 05:46:32 station1 postfix/smtpd[490]: disconnect from localhost.localdomain[127.0.0.1]
Sep 14 05:47:31 station1 postfix/smtpd[490]: connect from localhost.localdomain[127.0.0.1]
Sep 14 05:47:31 station1 postfix/smtpd[490]: disconnect from localhost.localdomain[127.0.0.1]
Sep 14 05:48:31 station1 postfix/smtpd[490]: connect from localhost.localdomain[127.0.0.1]
Sep 14 05:48:31 station1 postfix/smtpd[490]: disconnect from localhost.localdomain[127.0.0.1]



Please any help:cry:

---

### Post by Thyagaraj on 2010-09-16
Some how I got it working):P

---


---
title: "Configuring email notification in Nagios"
date: 2008-09-11
forum: Server Platforms
---

### Post by supersk on 2008-09-11
Hello,

I've installed Nagios on Ubuntu 8.04 with mailx. I haven't been getting any of the email notification messages.

My email domain is different from my network domain. 

I see this error message in /var/mail/nagios: Mailing to remote domains not supported

Does this mean I have to configure mailx to forward the email to my local Exchange 2003 SMTP server? If so how do you do this? Or is there something else I'm missing?

Thanks for any assistance anyone can provide.

---

### Post by inphektion on 2008-09-11
install postfix and set it up as a satellite mail system and just point it to your exchange smtp server.  Postfix will ask you this info on initial install.  Once setup nagios will use that you don't need mailx for the notifications.

---

### Post by stavrama on 2008-09-25
I dont want to create a new post for the same thing so i ll aks it here. I have setup Nagios recently and i want to receive also notification mails. I ve installed mailx and now i need to setup my exchange and account  details inside /usr/local/nagios/etc/objects/commands.cfg. I dunno yet much about linux so anyone can plz help me and tell me what i need to edit on the following lines in order to start receiving the mails. Thanx in advance for your help :)

# 'notify-host-by-email' command definition
define command{
	command_name	notify-host-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/bin/mailx -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$
	}

# 'notify-service-by-email' command definition
define command{
	command_name	notify-service-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /usr/bin/mailx -s "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$
	}

---

### Post by inphektion on 2008-09-27
You don't edit those.  and you don't need mailx for nagios notifications.  you need something like postfix.  refer to my previous post.

---


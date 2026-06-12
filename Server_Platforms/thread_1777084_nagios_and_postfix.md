---
title: "nagios and postfix"
date: 2011-06-07
forum: Server Platforms
---

### Post by tapi0n on 2011-06-07
I've set up a nagios monitoring box and all that's left to do is get notification mails.

I installed postfix and when doing nc to our mailserver I receive mail in my mailbox. So I'm assuming postfix is configured correctly.

Just to be safe here's part of my *main.cf  *that matters

```
myhostname = ubuntuNagios.local.syscom.be
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntuNagios.local.syscom.be, localhost.local.syscom.be, localhost
relayhost = [xxx.xxx.xxx.xxx]
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```Now since I'm using postfix I had to change any */bin/mail* reference to */usr/bin/mail* in the commands file in */usr/local/nagios/etc/objects/commands.cfg . *The result of which is:

```
# 'notify-host-by-email' command definition
define command{
        command_name    notify-host-by-email
        command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/bin/mail -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$
        }

# 'notify-service-by-email' command definition
define command{
        command_name    notify-service-by-email
        command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$\n" | /usr/bin/mail -s "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$
        }

```my contacts look like this. For testing purposes I'm only enabling host notifications.

```
define contact {
                contact_name                          nagiosadmin
                alias                                 Nagios Admin
                host_notification_options             d,u,r,f,n
                service_notification_options          n
                email                                 me@syscom.be
                host_notification_period              24x7
                service_notification_period           24x7
                host_notification_commands            notify-host-by-email
                service_notification_commands         notify-service-by-email
}
```Now I was going trough */usr/bin/ *and noticed that there is no *mail* in there (which is called in the notification commands). Is this normal? Could this be the reason I'm not getting any mails from nagios? 

Cheers

EDIT: I installed mailx which included mail for */usr/bin/mail *but mail is still not being sent. Also I'm getting no help at all from my logs.

---

### Post by linkageless on 2011-06-07
I think your problem is including the 'n' in 'host_notification_options'. Set it to 'd,u,r,f' and nagios will a least allow itself to try to send those notifications.

---

### Post by linkageless on 2011-06-07
BTW - I've assumed you have your host config working and correctly configured to generate notifications, and that you've got the correct contact group/contact setup!

---

### Post by tapi0n on 2011-06-07
> **linkageless said:**
> I think your problem is including the 'n' in 'host_notification_options'. Set it to 'd,u,r,f' and nagios will a least allow itself to try to send those notifications.

The n stands for none. During testing I just want notifications for hosts. 

And yes everything is configured correctly Nagios side. I haven't found the solution yet but I'm getting closer. I'll probably get it right tomorrow.

---

### Post by tapi0n on 2011-06-08
Solved. Seems I was just editing the wrong file. The person before me left a jungle of config files.

Thanks for any help that was provided :)

---

### Post by sentinelace on 2011-09-06
I have the same problem.  Postfix answers but I never get an email to my inbox.  Do I have to reply to an exchange server or can I have it email directly?  I have allowed the IP on the exchange server.

---


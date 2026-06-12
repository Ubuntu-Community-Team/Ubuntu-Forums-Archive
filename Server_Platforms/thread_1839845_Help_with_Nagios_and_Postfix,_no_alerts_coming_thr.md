---
title: "Help with Nagios and Postfix, no alerts coming through"
date: 2011-09-06
forum: Server Platforms
---

### Post by sentinelace on 2011-09-06
I have been messing with this for a week and cannot get an email.  I have it relaying to my local exchange server which has this IP allowed but I never get the email.  I assume I have to relay.  
 
Main.cf 
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version# Debian specific:  Specifying a file name will cause the first# line of that file to be used as the name.  The Debian default# is /etc/mailname.#myorigin = /etc/mailnamesmtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
readme_directory = no
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = Qmail
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = nextgenfilms.com, Qmail, localhost.localdomain, localhost
relayhost = 192.168.1.20
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
smtp_sasl_auth_enabled = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
canonical_maps = hash:/etc/postfix/canonical
```
 
now I can't even get postfix to answer when I telnet from trying to get this going.  What am I missing?

---

### Post by sentinelace on 2011-09-19
I also get this error:
```
 
 
Return code of 127 is out of bounds - plugin may be missing

```

---

### Post by koenn on 2011-09-19
the nagios error (post #2) indicates your host/service check is  trying to use a plugin that maybe isn't installed, isn't executable, or you have a typo or a syntax error or a mistake in the command definition. something along those lines


to get mail notifications (post #1), a whole lot of things need to be set up right : the notification config in nagios, valid email addresses, + your mail server's config to receive the notification and deliver it.

So you're going to at least explain how you set this up in order for people to be able to help you troubleshoot it. 

Also, look through your logs (mail, nagios) for mentions of failed notification, refused mail, failed connections, etc. to point you in the right direction.

---

### Post by sentinelace on 2011-09-20
I have followed the nagios guide on installing with postfix.  I have all the default configs except for one access point added for a host and my email address for notifications.  Everything else is default.  So why would the commands file be wrong?

---

### Post by koenn on 2011-09-20
you didn't explain that in your OP, so how would I know your setup is "all defaults" ? Furthermore, Nagios is a framework, designed to be extended and customized. it's defaults don't necessarily make for a working config.

Lastly, the error you post suggests exactly what i said : a check is trying to use a plugin that maybe isn't installed, isn't executable, or you have a typo or a syntax error or a mistake in the command definition. something along those lines.
If you think investigating along those lines isn't worth your trouble, feel free to take any other approach you can think of.

---

### Post by sentinelace on 2011-09-20
I install nagios and post fix from source. 
 
Here is my nagios.cfg file:
 
```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Tue Sep 20 15:18:38 EDT 2011
  System load:  0.0               Processes:           120
  Usage of /:   3.9% of 31.18GB   Users logged in:     1
  Memory usage: 23%               IP address for eth0: 192.168.1.73
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
# command file as often as possible.
#command_check_interval=15s
command_check_interval=-1
 
# EXTERNAL COMMAND FILE
# This is the file that Nagios checks for external command requests.
# It is also where the command CGI will write commands that are submitted
# by users, so it must be writeable by the user that the web server
# is running as (usually 'nobody').  Permissions should be set at the 
# directory level instead of on the file, as the file is deleted every
# time its contents are processed.
command_file=/usr/local/nagios/var/rw/nagios.cmd
 
# EXTERNAL COMMAND BUFFER SLOTS
# This settings is used to tweak the number of items or "slots" that
# the Nagios daemon should allocate to the buffer that holds incoming 
# external commands before they are processed.  As external commands 
# are processed by the daemon, they are removed from the buffer.  
external_command_buffer_slots=4096
 
# LOCK FILE
# This is the lockfile that Nagios will use to store its PID number
# in when it is running in daemon mode.
lock_file=/usr/local/nagios/var/nagios.lock
                                                                                                                                                      193,0-1       12%
```
 
my commands.cfg:
```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Tue Sep 20 15:18:38 EDT 2011
  System load:  0.0               Processes:           120
  Usage of /:   3.9% of 31.18GB   Users logged in:     1
  Memory usage: 23%               IP address for eth0: 192.168.1.73
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
# command file as often as possible.
#command_check_interval=15s
command_check_interval=-1

        }
# 'notify-service-by-email' command definition
define command{
        command_name    notify-service-by-email
        command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$\n" | /bin/mail -s "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$
        }
 
 
################################################################################
#
# SAMPLE HOST CHECK COMMANDS
#
################################################################################

# This command checks to see if a host is "alive" by pinging it
# The check must result in a 100% packet loss or 5 second (5000ms) round trip 
# average time to produce a critical error.
# Note: Five ICMP echo packets are sent (determined by the '-p 5' argument)
# 'check-host-alive' command definition
define command{
        command_name    check-host-alive
        command_line    $USER1$/check_ping -H $HOSTADDRESS$ -w 3000.0,80% -c 5000.0,100% -p 5
        }

################################################################################                                                                                                                                                      64,1          14%
```
 
My contacts.cfg :
 
```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Tue Sep 20 15:18:38 EDT 2011
  System load:  0.0               Processes:           120
  Usage of /:   3.9% of 31.18GB   Users logged in:     1
  Memory usage: 23%               IP address for eth0: 192.168.1.73
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
# command file as often as possible.
#command_check_interval=15s
command_check_interval=-1

        }
# 'notify-service-by-email' command definition
###############################################################################
# CONTACTS.CFG - SAMPLE CONTACT/CONTACTGROUP DEFINITIONS
#
# Last Modified: 05-31-2007
#
# NOTES: This config file provides you with some example contact and contact
#        group definitions that you can reference in host and service
#        definitions.
#       
#        You don't need to keep these definitions in a separate file from your
#        other object definitions.  This has been done just to make things
#        easier to understand.
#
###############################################################################
 
###############################################################################
###############################################################################
#
# CONTACTS
#
###############################################################################
###############################################################################
# Just one contact defined by default - the Nagios admin (that's you)
# This contact definition inherits a lot of default values from the 'generic-contact' 
# template which is defined elsewhere.
define contact{
        contact_name                    nagiosadmin             ; Short name of user        use                             generic-contact         ; Inherit default values from generic-contact template (defined above)        alias                           Nagios Admin            ; Full name of user
        email                           myemail@domain[EMAIL="jasonp@.com"].com[/EMAIL] ; <<***** CHANGE THIS TO YOUR EMAIL ADDRESS ******
        }
"contacts.cfg" 55L, 2173C                                                                                                                             7,1           Top
```
 
and here is the one host file I am using called switch for testing.  Everything seems to be working except for the email
 
switch.cfg
```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
  System information as of Tue Sep 20 15:18:38 EDT 2011
  System load:  0.0               Processes:           120
  Usage of /:   3.9% of 31.18GB   Users logged in:     1
  Memory usage: 23%               IP address for eth0: 192.168.1.73
  Swap usage:   0%
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
# command file as often as possible.
#command_check_interval=15s
command_check_interval=-1

        }
# 'notify-service-by-email' command definition
###############################################################################
# CONTACTS.CFG - SAMPLE CONTACT/CONTACTGROUP DEFINITIONS
#
###############################################################################
# SWITCH.CFG - SAMPLE CONFIG FILE FOR MONITORING A SWITCH
#
# Last Modified: 10-03-2007
#
# NOTES: This config file assumes that you are using the sample configuration
#        files that get installed with the Nagios quickstart guide.
#
###############################################################################
 

###############################################################################
###############################################################################
#
# HOST DEFINITIONS
#
###############################################################################
###############################################################################
# Define the switch that we'll be monitoring
define host{
        use             generic-switch          ; Inherit default values from a template
        host_name       192.168.1.89            ; The name we're giving to this switch
        alias           Cisco Access Point      ; A longer name associated with the switch
        address         192.168.1.89            ; IP address of the switch        hostgroups      switches                ; Host groups this switch is associated with        }
 
###############################################################################
###############################################################################
"switch.cfg" 113L, 3273C                                                                                                                              1,1           Top
```

---

### Post by koenn on 2011-09-20
check if your nagios host has /bin/mail

i'm guessing it doesn't.
that would explain why it can't send mail, and is consistent with the 127 error : nagios can't find /bin/mail that is called from the "notify by mail" command definition.

That /bin/mail is not present might be an indication that your Nagios is further lacking in mail infrastructure - on a standard Debian system one can expect Exim4 as MTA + a collection of mail command tools. I'm not sure how Ubuntu and/or postfix handle that.

---

### Post by sentinelace on 2011-09-21
I had to change /bin/mail to /usr/bin/mail and now I get emails but I still get that plugin error

---

### Post by koenn on 2011-09-21
> **sentinelace said:**
> I had to change /bin/mail to /usr/bin/mail and now I get emails but I still get that plugin error

any chance you can figure out which command/service check/... generates that plugin error ?

---

### Post by sentinelace on 2011-09-21
well I still have no idea what you want me to check to fix that error?  Also, how do you change the times it checks?  Like pings etc?  Is there a way to turn off the other features like cpu, hard drive space, etc?  I am only looking for uptime, but I find that if a device gets rebooted it's not enough time for nagios to send the email.

---

### Post by koenn on 2011-09-21
> **sentinelace said:**
> I also get this error:
```
 
 
Return code of 127 is out of bounds - plugin may be missing

```

where exactly do you see that error ?

---

### Post by sentinelace on 2011-09-21
Now I see it in the email, but I also see it when I click on notifications in the gui.  I assume snmp needs to be installed?  Maybe I don't have it installed on my system?  I did turn it on the cisco AP.  I also can't figure out how I can add multiple hosts.

---

### Post by koenn on 2011-09-21
> **sentinelace said:**
>  Also, how do you change the times it checks?  Like pings etc?  Is there a way to turn off the other features like cpu, hard drive space, etc?  I am only looking for uptime, but I find that if a device gets rebooted it's not enough time for nagios to send the email.
all of that is defined in the various .cfg files. 
I installed nagios from a debian package and reorganized the config files to suit the way I organize monitoring (nagios allows for that as it reads **any** file with .cfg extension), so I do not readily know where those defaults would be in a nagios from a project tarbal.
Look for .cfg files under /etc/nagios or /etc/nagios3

Also, get yourself a nagios tutorial or howto, so that you know how nagios reads configs. It's made to be modular and extensible, and to achieve that, things are pretty layered; eg. a host check config will have a "check commannd" that is defined elsewhere, the check command itself will refer to an actual program located elsewhare, it's execution will be in a given interval defined in yet some other file along with other available intervals, etc.etc. 

You need to understand that mechanism before you attempt to troubleshoot or modify your system, or you get completely lost.

---

### Post by koenn on 2011-09-21
> **sentinelace said:**
> Now I see it in the email, but I also see it when I click on notifications in the gui.  I assume snmp needs to be installed?  Maybe I don't have it installed on my system?  I did turn it on the cisco AP.  I also can't figure out how I can add multiple hosts.

In the e-mail, or in the GUI, there is some mention of a check being executed, right. Somethinng like "PING on MyServer failed" - that tells you (at least) the check that is failing, no ? and then you can look at dce definition of that check, and see which commands/plugins it's calling (and can't find, or something like it).

Yes, some checks require snmp and if that is not installed, they will return an error similar to "weird return code, plugin might be not installed"


re multiple hosts: any .cfg file with a valid host definition will do. It's not unusual to use a separate file per host, organiozed in subdirs of /etc/nagios/[objects]. You may need to read some nagios documentation for this to make sense.

---

### Post by sentinelace on 2011-10-17
I did finally get it to email but this is just too much work to maintain to setup hosts.  I have over 40 hosts I need to monitor and it appears I need host.cfg file for every one.  Too much work.  I'm switching to zenoss

---

### Post by sentinelace on 2011-11-13
Well if anyone decides they want this type of service, don't use nagios.  It's horrible and a pain to configure.  I went with zenoss and literary got it up in running on a clean box with posfix in 10 minutes after the fresh install and it works out of the box.

---


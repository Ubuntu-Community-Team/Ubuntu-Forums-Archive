---
title: "How to Have Ubuntu send notification via email and SMS when system boots and shutdown"
date: 2016-10-08
forum: Security
---

### Post by kevdog on 2016-10-08
**[SIZE=5]How to Have Ubuntu Send Notifications via E-Mail and SMS at System Boot and Shutdown[/SIZE]**

**[SIZE=4]I. Introduction[/SIZE]**

  **[SIZE=3]a. Purpose[/SIZE]** - I use my Ubuntu machine as my backup server.  It hosts a lot of files from many different computers. As a security measure I wanted to be notified remotely when the server would shutdown and restart.  I wanted to be notified with both E-Mail and SMS when the computer booted and shutdown. 
 
 **[SIZE=3]b. My Setup[/SIZE]** - Ubuntu 16.04 LTS. Systemd init system version 229. ****Encrypted home directory via ecryptfs -- (***IF YOU HAVE AN ENCRYPTED HOME DIRECTORY SETUP -- PLEASE SEE WORK AROUND BELOW. This particular setup causes difficulties with Postfix which will be used as the Mail Transfer Agent (MTA)). Postfix in this example is used as an [SMTP Relay]("https://en.wikipedia.org/wiki/Open_mail_relay"). 
 
 **[SIZE=3]c. Packages Required[/SIZE]** - **Postfix or other MTU**. Additional Setup Required - **Network Card capable of WOL (Wake-On-LAN)**.  *Optional Packages* - Program on Phone, Tablet or Mobile Device or Internet Web Site capable of Sending WOL packet -- Example ([https://www.depicus.com/wake-on-lan/woli]("https://www.depicus.com/wake-on-lan/woli")). I use an Iphone for my mobile device.  The program I'm using is known as [Scany]("https://itunes.apple.com/us/app/scany-network-scanner/id328077901?mt=8"). Although I no longer own an Android device, similar such programs could be found here: [WOL Applications on Google Play]("https://play.google.com/store/apps/similar?id=co.uk.mrwebb.wakeonlan&hl=en")

**[SIZE=4]II. Setup[/SIZE]**

[SIZE=3]**a. SMTP Relay**[/SIZE] - I'm using Postfix to forward the notifications through my Gmail account.  I believe this could like be done with other providers, however Gmail seems to be heavily documented.  I'm also using 2 Factor Authentication with my Standard Email Account.  Unfortunately a system can not automatically use Gmail as a relay if two factor authentication is involved. To work around this limitation, I recommend generating an app password that postfix will need to relay the mail through a personal gmail account.  This app password will be used by postfix and will be different than your normal gmail account login.  To generate the app password please see: [Sign in Using App Passwords]("https://support.google.com/accounts/answer/185833"). Please write down and save the password as you will use this when setting up postfix.  Here are a few other sites with directions how to do this: [http://email.about.com/od/gmailtips/fl/How-to-Get-a-Password-to-Access-Gmail-By-POP-or-IMAP.htm]("http://email.about.com/od/gmailtips/fl/How-to-Get-a-Password-to-Access-Gmail-By-POP-or-IMAP.htm")

**[SIZE=3]b. Postfix[/SIZE]** - I installed postfix through the mailutils package:
```
sudo apt-get install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules
```
The basic instruction how to install [postfix on 16.04]("https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04") were followed initially.  I then had to modify postfix to configure for an [smtp relay]("https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp/").  For completeness of this tutorial, here is my main.cf file:

***Please read the links above since the aliases files need to be created.  This topic is covered in the above links.  This needs to be done in addition to modification of the /etc/postfix/main.cf file

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
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

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_un
auth_destination
myhostname = ####entry should have been set up here with installation of postfix
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#sender_canonical_maps = hash:/etc/postfix/sender_canonical
myorigin = /etc/mailname
mydestination = $myhostname, localhost.localdomain, localhost
relayhost = [smtp.gmail.com]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
virtual_alias_maps = hash:/etc/postfix/virtual

smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

```

My /etc/postfix/sasl_passwd file looks like this
```

[smtp.gmail.com]:587 <user>@gmail.com:**PASSWORD_FROM_Setup.a_above**

```

Please note that setting up the postfix server can be rather tricky.  I had to refer to the links above several times to confirm the settings.

As you'll have to restart the postfix server several times, for reference this can be done by:
```

sudo systemctl restart postfix

```

[tip]("#tips")
**[SIZE=2]****Caveats due to encrypted home directory setup[/SIZE]**
Whatever the user that sends a mail through postfix, postfix requires that a /Maildir be located in the working directory.  As seen later, the systemd script that mails the notification runs as user root with a base dir of /.  For my setup, I created a directory under /root/Maildir.  This command to make this directory structure is the following:
```

sudo mkdir -p /root/Maildir

```
The purpose for creation of this directory structure will be shown later.  Please note that a different directory structure other than /root/Maildir can be created, however it must be out of the normal /home/<user> tree, since when the notification script is run on system boot, the encrypted home partitions are not yet decrypted and mounted.

**[SIZE=3]c. WOL setup[/SIZE]**

Ensure the ethtool package is installed: sudo apt-get install ethtool

Here are [WOL setup instruction for Ubuntu.]("https://help.ubuntu.com/community/WakeOnLan"). I my situation I found that my WOL settings for my network card kept resetting after every boot.  In order to keep WOL Wake On: g and the Magic Packet settings persistence at boot, I had to create the following service file at /etc/systemd/system/wol@.service as the root user. 
```

# Systemd file to turn on Magic Packet on network card
# Could be improved to actually discover the active interface
# If you want to enable wol on  on interface eth0: sudo systemctl enable wol@eth0.service
# 

[Unit]
Description=Wake-on-LAN for %i
Requires=network.target
After=network.target

[Service]
Type=oneshot
ExecStart=/sbin/ethtool -s %i wol g

[Install]
WantedBy=multi-user.target

```

Once the service file is created, enable and start the service file as follows: If your network interface is not eth0, please modify the following commands to reflect your appropriate network interface card as seen in the ifconfig command
```

sudo systemctl enable wol@eth0.service
sudo systemctl start wol@eth0.service

```

If you ever need to make any modification to this service file, you'll need to reload the service file after making your modifications:
```

sudo systemctl stop wol@eth0.service
sudo systemctl disable wol@eth0.service
sudo systemctl enable wol@eth0.service
sudo systemctl start wol@eth0.service

```

After running the service file, please verify the Magic Packet for the network interface card is set to g with the 
```

sudo ethtool <NIC>

```
and look for 
```

Wake-on: <letters>

```
The letter should contain g and not d.

******If your server sits behind a network router**
If your server sits behind a network router, I needed to port forward port 9 on the router to port 9 on the server.  Port forwarding port 9 for me was all I needed to do for my setup.  My network server is sitting behind an Apple Time Capsule Router.  The WOL magic packet is actually sent as a broadcast packet.  Simply port forwarding port 9 is what I needed to do for my setup, however others may have to forward port 9 to the broadcast interface -- 192.168.1.255.  My simple router wouldn't allow port forwarding to the broadcast interface without some trickery -- luckily I didn't need to do this.

**[SIZE=3]d. Notification Setup[/SIZE]**
Up to this point, everything has been setup for the notification setup.  The first step is to create a script file that will do perform the notifications.  We will then automate the use of this script by creating a systemd service file that will run the script at system boot and shutdown.

The script I used to allow for notifications is shown below. I can be modified as you see fit particularly in regards to the message header, message body, 

**/usr/local/bin/SystemEmail.sh**
```

#!/bin/bash

LAN_IP=`hostname --all-ip-addresses | awk '{print $1}'`
WAN_IP=`wget http://ipinfo.io/ip -qO -`
SERVER_NAME=`hostname -f`
STARTUP_SUBJECT="[${SERVER_NAME}] - System Startup: "`date`
STARTUP_MESSAGE="$SERVER_NAME @ LAN IP = ${LAN_IP} - WAN IP - ${WAN_IP} Started Successfully: "`date`
SHUTDOWN_SUBJECT="[${SERVER_NAME}] - System Shutdown: "`date`
SHUTDOWN_MESSAGE="$SERVER_NAME @ LAN IP = ${LAN_IP} - WAN IP - ${WAN_IP} Shutting Down: "`date`
EMAIL_ADDRESS="<user>@gmail.com"
SENDER_ADDRESS="<user>@<hostname>.com"
SMS_NUMBER="<SMS NUMBER>@vtext.com"  #For a list of email to sms gateways please see http://www.digitaltrends.com/mobile/how-to-send-e-mail-to-sms-text/
RETVAL=0

stop()
{
   echo  $"Sending Shutdown Email "
   echo "${SHUTDOWN_MESSAGE}" |  mail -Ssendwait -Sfrom="${SENDER_ADDRESS}" -s "${SHUTDOWN_SUBJECT}" ${EMAIL_ADDRESS}
   #sleep 10
   echo "${SHUTDOWN_MESSAGE}" | mail -Ssendwait -Sfrom="${SENDER_ADDRESS}" ${SMS_NUMBER}
   #sleep 10
   RETVAL=$?

   return ${RETVAL}
}

start()
{
   echo  $"Sending Startup Email "
   echo "${STARTUP_MESSAGE}" | mail -Ssendwait -Sfrom="${SENDER_ADDRESS}" -s "${STARTUP_SUBJECT}" ${EMAIL_ADDRESS}
   #sleep 10
   echo "${STARTUP_MESSAGE}" | mail -Ssendwait -Sfrom="${SENDER_ADDRESS}" ${SMS_NUMBER}
   #sleep 10
   RETVAL=$?

   return ${RETVAL}

}

case "$1" in
start)
   start
;;
stop)
   stop
;;
status)
   echo "Not applied to service"
;;
restart)
   stop
   start
;;
reload)
   echo "Not applied to service"
;;
probe)
;;
*)
   echo "Usage: SystemEmail{start|stop|status|reload|restart}"
   exit 1
;;

esac
exit ${RETVAL}

```

After creating the script file, please make it executable and ensure it's owned by root:
```

sudo chown root:root /usr/local/bin/SystemMail.sh
sudo chmod +x /usr/local/bin/SystemMail.sh

```

I would highly recommend prior to automating the use of this script, that the user test the script to ensure it can run on the command line by itself without any system intervention.

Testing could be peformed by:
```

$ /usr/local/bin/SystemMail.sh start
$ /usr/local/bin/SystemMail.sh stop

```

Once you are certain the script is able of sending emails, please create the following service file: /etc/systemd/system/SystemEmailNotificationStartStop.service
```

[Unit]
Description=System Email Notification at Startup and Shutdown
Wants=network-online.target
After=network-online.target postfix.service

[Service]
User=root
WorkingDirectory=/root
ExecStart=/usr/local/bin/SystemEmail.sh start
ExecStop=/usr/local/bin/SystemEmail.sh stop
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

```

Please note that the WorkingDirectory specified above points to the directory discussed above.  With /root, there is a /Maildir subdirectory as created above.  If you fail to include this directory, systemd assumes the WorkingDirectory=/ and hence postfix with look for MailDir within the / directory.  

Ensure its owned by root with following permissions
```

sudo chown root:root /etc/systemd/system/SystemEmailNotificationStartStop.service
sudo chmod 644 /etc/systemd/system/SystemEmailNotificationStartStop.service

```

Install and start the service:
```

sudo systemctl enable SystemEmailNotificationStartStop.service
sudo systemctl start SystemEmailNotificationStartStop.service

```

If any modifications are made to this script, please make the modification to the service file and reload the SystemFile
```

sudo systemctl stop SystemEmailNotificationStartStop.service
sudo systemctl disable SystemEmailNotificationStartStop.service
sudo systemctl daemon-reload
sudo systemctl enable SystemEmailNotificationStartStop.service
sudo systemctl start SystemEmailNotificationStartStop.service

***note -- theoretically you could just run the command sudo systemctl (restart or reload) SystemEmailNotificationStartStoop.service.  I've never had much luck with this command unfortunately so I opted for the 5 commands above.

```


**[SIZE=4]III. Other considerations[/SIZE]**
**[SIZE=3]a. Firewall[/SIZE]**
     If running a firewall on the server please ensure incoming connections on port 9 and outgoing connections on port 587 are open.  In testing this script, I would deactivate the firewall and only reactivate it at the last step.
b. Starting and Stopping computer remotely
    The mobile WOL application (either phone, computer or website) can be used to send the Magic Packet to remotely turn on the computer.  In order to send a magic packet you will have to know the MAC address of the network card, and the if sending outside the LAN, the WAN IP address of the network.  The MAC address of the network card can be found by looking at the ifconfig output and looking for HWaddr or by typing
```
 ifconfig | grep HWaddr | awk '{print $5}' 
```

[[img]https://s13.postimg.org/e58gtdh9f/Full_Size_Render.jpg[/img]](https://postimg.org/image/e58gtdh9f/)

I believe that is all that is needed.  
Thanks for reading.

---


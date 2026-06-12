---
title: "Send mail in backup script"
date: 2008-10-20
forum: Server Platforms
---

### Post by ezacon on 2008-10-20
I have programed my first set of scripts to perform diferents backup jobs, scheduled with crontab.
The backup part is working as expected, but i cant send the final report mail.
Here is my script:

#!/bin/sh
# Copia de seguridad del directorio /etc en disco de red
LOGFILE="bcketc`date +%d%m%y`.log"
echo Inicio de copia de /etc: `date` > /root/copias/$LOGFILE
ISMOUNT=$(cat /proc/mounts|grep /media/copias)
if [ -z "${ISMOUNT}" ];
        then
                echo Montando disco de copias >> /root/copias/$LOGFILE
                mount /media/copias
                if [ $? -ge 1 ]
                        then
                                echo No se ha podido montar el disco de copias >> /root/copias/$LOGFILE
                        else
                                /bin/tar \
                                        --create \
                                        --verbose \
                                        --preserve \
                                        --gzip \
                                        --ignore-failed-read \
                                        --file=/media/copias/etc.tar \
                                        /etc \
                                        >> /root/copias/$LOGFILE
                fi
fi
echo Proceso finalizado `date` >> /root/copias/$LOGFILE
# email subject
SUBJECT="Copia de seguridad de /etc `date`"
# Email To ?
EMAIL="myname@mydomain.com"
# Email text/message
EMAILMESSAGE="/root/copias/$LOGFILE"
# send an email using /usr/bin/mail
/usr/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
cp /root/copias/$LOGFILE /media/copias/$LOGFILE
/bin/umount /media/copias

The mail is not sent and i get this in /var/log/exim4/mainlog:

2008-10-20 20:20:16 1KrzMW-00089E-E1 <= [email]myname@myhost.mydomain.com[/email] U=myname P=local S=88664
2008-10-20 20:20:16 1KrzMW-00089E-E1 ** [email]myname@mydomain.com[/email] R=nonlocal: Mailing to remote domains not supported
2008-10-20 20:20:16 1KrzMW-00089G-Fr <= <> R=1KrzMW-00089E-E1 U=Debian-exim P=local S=89593
2008-10-20 20:20:16 1KrzMW-00089E-E1 Completed
2008-10-20 20:20:16 1KrzMW-00089G-Fr => myname <myname@myhost.mydomain.com> R=local_user T=mail_spool
2008-10-20 20:20:16 1KrzMW-00089G-Fr Completed

I have a mail server in the same network. The domain name is mydomain.com, but the mail is sent to [email]myname@myhost.mydomain.com[/email]
 instead of [email]myname@mydomain.com[/email] wich is correctly resolved by the DNS server to the correct MX.
 I think it is an exim4 issue, but no idea how to resolve it.
Any idea to send a notification mail with an authenticated smtp mail user?

---

### Post by jarl on 2009-07-04
You may want to have a look at this one:
[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

Jarl

---


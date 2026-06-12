---
title: "Root/Sent file Issue"
date: 2017-01-25
forum: Server Platforms
---

### Post by hawk0072 on 2017-01-25
Hi, I have an issue that I cant seem to solve. Im only learning so my knowledge is limited.

The issue is that the root/sent file which was created (I presume) to save/create a copy of ALL of the sent emails of my Ubuntu 16.04 VPS.

The issue is that this file is 3GB and growing....

So my question then is: Is there a way to:

1 - Clear the contents of the root/sent file?

and...

2 - Stop the emails being saved in the root/sent file?

I have been struggling to search for answers to this and so would very much appreciate any guidance to help solve this issue.

Many thanks in advance.

---

### Post by ajgreeny on 2017-01-25
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by SeijiSensei on 2017-01-25
You can use logrotate to manage files like logs and the one you mention that grow in size over time.  Create an arbitrarily-named file like "rootsent" in /etc/logrotate.d/ with this format:
```

/path/to/root/sent
{
     rotate 4
     weekly
     missingok
     notifempty
     compress
}

```
That will tell the system to keep four weeks of that file and compress the backups with gzip.  See "man logrotate" for details.

---

### Post by hawk0072 on 2017-01-25
Thanks SeigiSensi... Much appreciated.

Is there a way to clear it now. 

Also I really don't need ANY backups or records of the emails sent as I have them externally. ie I receive the emails for backup purposes anyway?

The main reason I discovered this was that Tripwire wouldn't install because of the file size (or so I believe).

Thanks again for your input. Much appreciated.

---

### Post by SeijiSensei on 2017-01-25
Well you could just delete the file or make it zero-length with "sudo cat /dev/null > /path/to/root/sent".

But a more basic question is why is this file being created in the first place?  You haven't given us much to go on.  What mail exchanger are you using? Postfix?  Is there some archiving setting enabled in places like main.cf?

I don't really know what you mean by a "root/sent" file.  Are we talking about a sent folder in root's mail directory, /root/mail/sent?  On Ubuntu systems root doesn't really send out much mail since the root account is deactivated.  Daemon processes or cron jobs will mail as root.  If things like that are filling up your system, you need to find out why.

---

### Post by hawk0072 on 2017-01-25
Thanks again for the response. 
To answer some of the above... I installed mailutils to enable a site to send admin mails.
Also mysql backups are sent via a cron job which is most likely the reason for the large sent file size. (if its storing the databases?).

The path to the SENT file is root/sent and not root/mail/sent. See attached image of the folder.

[IMG]https://4e-life.com/sent.png[/IMG]

The contents of the main.cf file are:

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


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = vps11111.ovh.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, vps11111.ovh.net, localhost.ovh.net, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 127.0.0.1
inet_protocols = all



```

Thanks for the suggestions so far.

---

### Post by darkod on 2017-01-25
Let me see if I understand this correctly: mysql backups sent through email?

---

### Post by SeijiSensei on 2017-01-25
You should compress those backups with gzip or bzip2 before mailing them if you want to reduce storage requirements.  

I write my database backups to a separate directory on the server then use rsync to transfer them to my home office server for redundancy.

---

### Post by hawk0072 on 2017-01-26
Hi, Sorry for the delay getting back to you.

Thanks for the tips, I will attempt to implement some of them and hopefully get the problem solved.
I am using automysqlbackup and I believe the database files attached top the emails are already compressed.

I really want a way to stop the sent emails being added to the root/sent file but cant find any config file on the vps to allow me to stop the creation of the file.

Thanks again.

---

### Post by darkod on 2017-01-26
If you want to use an email message as a notification that the backup was done successfully, then that's ok. But in such case make sure you configure it so the backup file is never attached to the message.

But if you are trying to use email message to transport/send the backup file to another computer, then that's a very bad choice. You should configure the backup process so that it creates a file locally on the server, then copy it to another computer using rsync or scp. That can be easily scripted in bash script for example. This way there is no big attachment or big data files passing through email.

---

### Post by hawk0072 on 2017-01-26
Thanks darkod... good point.

I will reconfigure as the backup IS emailed to me as well as a backup being stored on the server and I am able to download it using WinSCP.

I appreciate the advice as I'm only just starting to learn this server stuff.
 BUT my issue is still can I delete the root/sent file safely as it is too large and also where is the config option that creates that file in the first place?

I understand that servers are very different regarding configs and releases etc so again I appreciate the input.

---

### Post by hawk0072 on 2017-01-26
Thanks very much darko and SeijiSensei for the brilliant assistance you offered.

After realizing that darko was right and mailing a DB backup was a bad idea I set the automysqlbackup config file to: 

```
MAILCONTENT="quiet" 
```

instead of 

```
MAILCONTENT="files" 
```

That reduced the root/sent file to 60,701 KB immediately ???

I have now been able to install tripwire successfully and hopefully a little mroe secure.

Thanks again fellas... much appreciated. All the best.

---

### Post by darkod on 2017-01-26
No problem. If you consider this solved please mark the thread as Solved using Thread Tools above the first post.

---


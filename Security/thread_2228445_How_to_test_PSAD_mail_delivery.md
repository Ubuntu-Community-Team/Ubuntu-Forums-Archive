---
title: "How to test PSAD mail delivery"
date: 2014-06-07
forum: Security
---

### Post by linuxyogi on 2014-06-07
Hi,

I have installed and configured PSAD as per instructions given [here]("http://www.unixmen.com/how-to-block-port-scan-attacks-with-psad-on-ubuntu-debian/").

My PC is behind my ISP's router/firewall so chances of getting scanned is low.

But still I wanna make sure that if my ip gets scanned I get an email alert.

I have only 1 PC so I cant scan this one from outside to test the setup.

I found this link [http://www.cipherdyne.com/psad/docs/faq.html#sendmail](http://www.cipherdyne.com/psad/docs/faq.html#sendmail)

I am getting this  

```
$  /bin/mail -v -s "test email" abc@gmail.com < /dev/null
bash: /bin/mail: No such file or directory
```

---

### Post by TheFu on 2014-06-07
If the **mail** cmd isn't on the system, you need to install it. On my systems, a package is usually offered that contains the cmd - of course, postfix/sendmail/qmail needs to be setup correctly on the system to send email to external email addresses. Most residential ISPs require outbound email go through their email gateway server.

---

### Post by linuxyogi on 2014-06-07
> **TheFu said:**
> If the **mail** cmd isn't on the system, you need to install it. On my systems, a package is usually offered that contains the cmd - of course, postfix/sendmail/qmail needs to be setup correctly on the system to send email to external email addresses. Most residential ISPs require outbound email go through their email gateway server.

I found the  mail binary is located in /usr/bin/mail.

```
/usr/bin/mail -v -s "test email" abcd@gmail.com < /dev/null
```

When the do the above the mail is getting sent to Gmail but Gmail is regecting it 
  
>     Our system has detected that this message is
    550-5.7.1 likely unsolicited mail. To reduce the amount of spam sent to
    Gmail, 550-5.7.1 this message has been blocked.




```
/usr/sbin $ ls |grep sendmail
sendmail

```

As you can see the sendmail binary  is present but when when I search for it in synaptic it is marked as not installed.

**_/etc/psad/psad.conf_**

```
### system binaries
iptablesCmd      /sbin/iptables;
ip6tablesCmd     /sbin/ip6tables;
shCmd            /bin/sh;
wgetCmd          /usr/bin/wget;
gzipCmd          /bin/gzip;
mknodCmd         /bin/mknod;
psCmd            /bin/ps;
mailCmd          /bin/mail;
[COLOR=#ff0000]**sendmailCmd      /usr/sbin/sendmail;**[/COLOR]
ifconfigCmd      /sbin/ifconfig;
ipCmd            /sbin/ip;
killallCmd       /usr/bin/killall;
netstatCmd       /bin/netstat;
unameCmd         /bin/uname;
whoisCmd         $INSTALL_ROOT/usr/bin/whois_psad;
dfCmd            /bin/df;
fwcheck_psadCmd  $INSTALL_ROOT/usr/sbin/fwcheck_psad;
psadwatchdCmd    $INSTALL_ROOT/usr/sbin/psadwatchd;
kmsgsdCmd        $INSTALL_ROOT/usr/sbin/kmsgsd;
psadCmd          $INSTALL_ROOT/usr/sbin/psad;
```

_**/etc/postfix/main.cf**_

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
myhostname = rambo
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = rambo.com, rambo, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
```

Because Gmail is blocking my mails I decided to keep it internal.

**_/etc/psad/psad.conf_**

```
### Supports multiple email addresses (as a comma separated
### list).
EMAIL_ADDRESSES             rambo@localhost;

### Machine hostname
HOSTNAME                    1.rambo.com;
```


```
$ sudo /usr/bin/mail -v -s "test email" rambo@localhost < /dev/null
Mail Delivery Status Report will be mailed to <root>.
```

^^ That succesfully sends a mail to my username. I have added an account for this local mail account in thunderbird and I am receiving mails manually sent by me.


But I havent received a single mail from psad. So I am still not sure if psad's mail alert is working.

---

### Post by linuxyogi on 2014-06-07
The email alert is working. I got this mail

> [-] You may just need to add a default logging rule to the /sbin/iptables
    'filter' 'INPUT' chain on 1.rambo.com.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:

    [http://www.cipherdyne.org/psad/docs/fwconfig.html](http://www.cipherdyne.org/psad/docs/fwconfig.html)

[-] You may just need to add a default logging rule to the /sbin/ip6tables
    'filter' 'INPUT' chain on 1.rambo.com.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:

    [http://www.cipherdyne.org/psad/docs/fwconfig.html](http://www.cipherdyne.org/psad/docs/fwconfig.html)


Then I did these and restarted the psad service. I will wait and see what happens now.
```
sudo ufw logging on
sudo iptables -A INPUT -j LOG
sudo iptables -A FORWARD -j LOG
sudo ip6tables -A INPUT -j LOG
sudo ip6tables -A FORWARD -j LOG
```

---

### Post by TheFu on 2014-06-08
Great that you got it working!

I know that a few others posting here do have gmail working from their Ubuntu servers at home.  If you are interested in setting that up, might post a specific question about that.  I think they use their ISP login and forward email through the ISP email gateway ... gmail doesn't block that - just direct connections from DHCP residential IPs - just like many other email servers do (including mine).  The transports or relayhost hash-dbs are where that happens, but I don't know.

The sendmail you are seeing is really part of postfix (by design) to be 100% compatible with other programs that expect "sendmail" to exist.

---


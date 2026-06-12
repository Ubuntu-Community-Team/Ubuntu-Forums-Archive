---
title: "Unable to telnet postfix from localhost or internal network - Can't send mail."
date: 2008-03-25
forum: Server Platforms
---

### Post by h00ch on 2008-03-25
I have been running postfix as my mailserver for the past year.  Not really had any problems with it until recently when it started timing out on smtp connections from my client computer.

I tested on the server by putting in telnet localhost 25.

I only get:
xxx@server:~$ telnet localhost 25
Trying 127.0.0.1...

And nothing.  

Same when trying to telnet from the client computer.
But, I DO receive mail just fine.  Plus a regular telnet does reach localhost (although it is properly refused)

xxx@server:~$ telnet localhost
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused


I've pared down my main.cf file to the basics, but it still doesn't work.

Here is my main.cf
-----------------------------

myhostname = ***.***.net
mydomain = ***.net
myorigin = $mydomain
# masquerade_domains = $mydomain
inet_interfaces = all

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

#-------- Virtual MySQL database hookups -------
virtual_mailbox_domains = mysql:/etc/postfix/domains_maps.cf
virtual_alias_maps = mysql:/etc/postfix/alias_maps.cf
virtual_gid_maps = static:5000
virtual_uid_maps = static:5000
virtual_minimum_uid = 5000
virtual_mailbox_base = /var/spool/mail
virtual_mailbox_maps = mysql:/etc/postfix/mailbox_maps.cf

# What domainds to receive mail for
mydestination = $myhostname $mydomain localhost.$mydomain localhost

# what clients to relay mail from
mynetworks = 192.168.0.0/24, [my static ip range], 127.0.0.0/8

# what destinations to relay mail to
relay_domains = $mydestination
relayhost =
local_recipient_maps = unix:passwd.byname $alias_maps

mailbox_size_limit = 0
recipient_delimiter = +

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
home_mailbox = Maildir/

# The mail_spool_directory parameter specifies the directory where
# UNIX-style mailboxes are kept. The default setting depends on the
# system type.
mail_spool_directory = /var/spool/mail

----------------------
I just can't figure out why it isn't listening for telnet.  I thought that the inet_interfaces = all, and mynetworks seem alright.

Any ideas?

---

### Post by Mr. C. on 2008-03-25
What is the output of :

```
ps -elf | grep postfix
netstat -an --tcp

```

---

### Post by h00ch on 2008-03-25
Output of ps -elf

```

1 S root      4122     1  0  80   0 -  1632 fcntl_ 16:43 ?        00:00:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd
1 S root      4124  4122  0  80   0 -  1632 381333 16:43 ?        00:00:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd
1 S root      4125  4122  0  80   0 -  1632 fcntl_ 16:43 ?        00:00:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd
1 S root      4126  4122  0  80   0 -  1632 fcntl_ 16:43 ?        00:00:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd
1 S root      4127  4122  0  80   0 -  1632 fcntl_ 16:43 ?        00:00:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd
4 S root      5335     1  0  75   0 -  1255 -      16:43 ?        00:00:00 /usr/lib/postfix/master
4 S postfix   5338  5335  0  78   0 -  1256 -      16:43 ?        00:00:00 pickup -l -t fifo -u -c
4 S postfix   5339  5335  0  82   0 -  1266 -      16:43 ?        00:00:00 qmgr -l -t fifo -u
4 S postfix   5420  5335  0  75   0 -  1336 -      16:43 ?        00:00:00 tlsmgr -l -t unix -u -c
4 S postfix   5429  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5436  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5437  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5439  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5442  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5444  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5445  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5452  5335  0  75   0 -  1986 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5462  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5463  5335  0  75   0 -  1323 -      16:43 ?        00:00:00 anvil -l -t unix -u -c
4 S postfix   5464  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5465  5335  0  75   0 -  1986 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5472  5335  0  75   0 -  1955 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5479  5335  0  75   0 -  1954 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5484  5335  0  75   0 -  1988 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress  -o content_filter spamassassin
4 S postfix   5485  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5486  5335  0  78   0 -  1926 -      16:43 ?        00:00:00 trivial-rewrite -n rewrite -t unix -u -c
4 S postfix   5523  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5524  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5525  5335  0  75   0 -  1986 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5526  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5527  5335  0  75   0 -  1955 17     16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5528  5335  0  75   0 -  1986 17     16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5529  5335  0  75   0 -  1955 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5530  5335  0  75   0 -  1985 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5531  5335  0  75   0 -  1926 -      16:43 ?        00:00:00 trivial-rewrite -n rewrite -t unix -u -c
4 S postfix   5532  5335  0  75   0 -  1984 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5533  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5534  5335  0  75   0 -  1987 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5535  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5536  5335  0  75   0 -  1987 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5539  5335  0  75   0 -  1954 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5540  5335  0  75   0 -  1987 17     16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5541  5335  0  75   0 -  1954 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5542  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5543  5335  0  75   0 -  1987 move_a 16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5544  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5545  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5546  5335  0  75   0 -  1988 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5547  5335  0  75   0 -  1955 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5548  5335  0  75   0 -  1985 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5549  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5550  5335  0  75   0 -  1988 move_a 16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5551  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5552  5335  0  75   0 -  1985 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5553  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5554  5335  0  75   0 -  1955 17     16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5557  5335  0  75   0 -  1954 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5558  5335  0  75   0 -  1986 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5561  5335  0  75   0 -  1955 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5574  5335  0  75   0 -  1955 17     16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5575  5335  0  75   0 -  1988 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5579  5335  0  75   0 -  1985 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5580  5335  0  75   0 -  1954 move_a 16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5581  5335  0  75   0 -  1988 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5582  5335  0  75   0 -  1954 -      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5583  5335  0  75   0 -  1954 1      16:43 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5584  5335  0  75   0 -  1955 1      16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5585  5335  0  75   0 -  1987 move_a 16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5602  5335  0  75   0 -  1987 move_a 16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5603  5335  0  75   0 -  1963 17     16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5605  5335  0  75   0 -  1987 1      16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
4 S postfix   5617  5335  1  79   0 -  1954 17     16:44 ?        00:00:00 smtpd -n smtp -t inet -u -o stress yes -o content_filter spamassassin
0 S root      5619  5586  0  76   0 -   745 pipe_w 16:44 pts/0    00:00:00 grep postfix


```

output of netstat is VERY long.  Here are the relevant bits.

```

tcp        0      0 0.0.0.0:58912           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:60000         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:36777           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:4559            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 65.101.116.235:53       0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 65.101.116.235:25       209.123.8.89:4222       SYN_RECV   
tcp        0      0 65.101.116.235:25       200.156.65.2:37030      SYN_RECV   
tcp        0      0 65.101.116.235:25       59.42.158.237:21742     SYN_RECV   
tcp        0      0 65.101.116.235:25       153.100.6.38:3772       SYN_RECV   
tcp        0      0 65.101.116.235:25       203.1.72.95:57286       SYN_RECV   
tcp        0      0 65.101.116.235:25       200.198.119.136:41334   SYN_RECV   
tcp        0      0 65.101.116.235:25       212.122.160.108:58829   SYN_RECV   
tcp        0      0 65.101.116.235:25       200.199.23.118:55120    SYN_RECV   
tcp        0      0 65.101.116.235:25       65.42.171.131:44889     SYN_RECV   
.....
tcp        0      0 65.101.116.235:25       203.89.204.41:51045     SYN_RECV   
tcp        0      0 65.101.116.235:25       200.68.116.33:8245      SYN_RECV   
tcp        0      0 65.101.116.235:25       222.151.196.11:30675    SYN_RECV   
tcp        0      0 65.101.116.235:25       213.208.108.81:27151    SYN_RECV   
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:55705           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
tcp        0      0 65.101.116.235:25       221.114.79.52:51756     ESTABLISHED
tcp        0      0 65.101.116.235:25       70.103.68.218:28335     ESTABLISHED
tcp        0      0 65.101.116.235:25       210.164.1.69:28920      ESTABLISHED
tcp        0      0 65.101.116.235:25       68.22.254.74:49317      ESTABLISHED
tcp        0      0 65.101.116.235:25       213.188.134.126:3772    ESTABLISHED
tcp        1      0 65.101.116.235:25       212.227.94.3:55443      CLOSE_WAIT 
tcp        0      0 65.101.116.235:25       64.58.72.114:48754      ESTABLISHED
tcp        0      0 65.101.116.235:25       206.108.144.32:62298    ESTABLISHED
tcp        0      0 65.101.116.235:25       87.242.77.186:42580     ESTABLISHED
....


```

Seems to be listening to localhost, but just not answering.

---

### Post by Mr. C. on 2008-03-25
How long is very long?
Your system appears to be under attack, as it is in stress adaptive mode.

How many SMTPd processes are running ?  I can't tell because the output is truncated.  By default, postfix will allow 100 smtpd processes.  If you are under attach, and all smtpd processes are in use, you'll have trouble creating more.

---

### Post by h00ch on 2008-03-25
My system is always under attack.  I've had this domain since the early 1990s and my mailgraph stats often look like today.

[IMG]https://jpe.net/cgi-bin/mailgraph.cgi?0-e[/IMG]

But, I've never had a problem with it timing out.    The processes in master.cf are set at the default value of 100.  I filter out most of the junk mail with the following in my main.cf:

```

##--- sasl authentication
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
# smtpd_sasl_local_domain = $mydomain
smtp_sasl_security_options =

###  Dovecot authenication
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

smtpd_client_restrictions =
        permit_sasl_authenticated
        permit_mynetworks
        check_client_access hash:/etc/postfix/client_access

smtpd_helo_required = yes

stmpd_helo_restrictions = permit_mynetworks, reject_invalid_hostname

smtpd_recipient_restrictions =
        permit_mynetworks
        permit_sasl_authenticated
        reject_unknown_recipient_domain
        reject_unauth_destination
        reject_unlisted_recipient
        reject_non_fqdn_recipient
        check_recipient_access hash:/etc/postfix/client_access
        check_policy_service inet:{greylisting service}
        reject_rbl_client dnsbl.njabl.org
        permit

smtpd_data_restrictions =
        reject_unauth_pipelining,
        permit


```

If it is a resource problem, is there a way to prioritize connections from $mynetworks, or $sasl_authenticated?

Ironically, I'm actually receiving less hits than I used to, but I've always been able to send.

---

### Post by Mr. C. on 2008-03-25
See: [http://www.postfix.org/STRESS_README.html](http://www.postfix.org/STRESS_README.html)

I find your server times out, so it is unable to respond to even remote connections as well as your local connection.

Consider NoListing also: [http://nolisting.org/](http://nolisting.org/)

---

### Post by h00ch on 2008-03-25
Thanks!  

I like the idea of nolisting.  I grep'd my mail log and apparently I'm under more of an attack than normal.  1000's (not an exaggeration) of senders to the same non-existent address  503mhenry@myserver.  By the order of my smtpd_recipient_restrictions, the address is being rejected before it even gets to greylisting.  I guess this is the true detriment of having had my domain hosted on on webhosts for 10 years.  

As for the Stress info, I recently put in the stress-adaptive tags in my main.cf.  And, I've raised the limit to 150.  But it still isn't responding to my telnets.

I'll give the nolisting a try.  Thank you for the help.

---

### Post by Mr. C. on 2008-03-25
Raising the limits may not be the correct thing here.  It was clear the system was under heavy attack (beyond what you're used to), so raising the limits will likely just allow more bot connections.

- Enable the submission port for your clients.
- Lower the hard limit for the bots during stress
- Reduce the connect time during stress

---

### Post by h00ch on 2008-03-25
How do I enable a submission port for my clients?  Sounds like a good solution, but I haven't ever done that.

I used the postfix scripts to set my hard limit during stress.  Looks like its working, but I have A LOT of incoming traffic.  I guess this was the chosen couple of days to bot me.

```

#smtpd_hard_error_limit = 5  -- old hard limit
smtpd_timeout = ${stress?10}${stress:300}
smtpd_hard_error_limit = ${stress?1}${stress:20}


```

As for connect time, most clients are being rejected even before rbl checks, greylisting, etc.  

```


smtpd_recipient_restrictions =
        permit_mynetworks
        permit_sasl_authenticated
        reject_unknown_recipient_domain
        reject_unauth_destination
        reject_unlisted_recipient
        reject_non_fqdn_recipient
        check_recipient_access hash:/etc/postfix/client_access
        check_policy_service inet:127.0.0.1:60000
        reject_rbl_client dnsbl.njabl.org
        permit

```

Most rejections are happening at the reject_unauth_destination and reject_unlisted_recipient points.

---

### Post by Mr. C. on 2008-03-25
There is likely already a submission entry in master.cf, but you'll want to tailor it to your needs  For example, something like:

```
submission inet n       -       n       -       -       smtpd
   -o smtpd_tls_security_level=encrypt
   -o smtpd_tls_auth_only=yes
   -o smtpd_sasl_auth_enable=yes
   -o broken_sasl_auth_clients=yes
   -o receive_override_options=no_header_body_checks,no_address_mappings
   -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
```

Disable permit_sasl_authenticated in your normal smtpd processes, and have your users connect to the submission port instead (587).  They do this by changing the SMTP port in their client (from the default 25 to 587).

This allows you to have separate controls, content_filter, etc. for your client's mail submissions.

Consider also the cheap reject_non_fqdn_{recipient,sender} checks, and keep the more expensive DNS-based checks in your smtpd_recipient_checks after the cheaper checks.  Eg.:
```

smtpd_recipient_restrictions =
    reject_non_fqdn_recipient
    reject_non_fqdn_sender
    reject_unlisted_recipient
    ...
    check_recipient_access pcre:/usr/pkg/etc/postfix/invalid_recipients.pcre
    permit_mynetworks
    reject_unauth_destination
    reject_unknown_sender_domain
    reject_unknown_recipient_domain
    check_helo_access pcre:/usr/pkg/etc/postfix/helo_checks.pcre
    reject_invalid_helo_hostname
    reject_rbl_client zen.spamhaus.org
    permit
```

To get some reject stats, try also postfix-logwatch:

[http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

This might help you tailor your restrictions better.

---

### Post by h00ch on 2008-03-25
I'll give it a try.  I've seen the submission line in master.cf, but never knew what it was for.  Is port 587 declared anywhere, or just part of postfix?

As for the smtpd_recipient_restrictions, it makes sense to clean that up to a work by process overhead requirements.

Thanks again for all of your help.  Hopefully, the mail flood will subside.

---

### Post by Mr. C. on 2008-03-25
RFC 2476
[http://www.faqs.org/rfcs/rfc2476.html](http://www.faqs.org/rfcs/rfc2476.html)

```
$ grep 587 /etc/services
submission      587/tcp                 # Message Submission
submission      587/udp                 # Message Submission
```

---


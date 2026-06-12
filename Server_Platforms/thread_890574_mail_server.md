---
title: "mail server"
date: 2008-08-15
forum: Server Platforms
---

### Post by ub007 on 2008-08-15
Hi,
I'm installing a mail server using the How To from this link
> [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

It worked fine for most part of it until i reached the stage where i was to create virtual domains:

> To create a Map Database type :

sudo postmap /etc/postfix/virtual

i get this error:
> postmap: fatal: open virtual: No such file or directory

What am i missing here.Thanks in advance
Cheers
David

---

### Post by Oldsoldier2003 on 2008-08-18
I'm moving this thread from ABT to Server Platforms so that you'll get more visibility from the folks that are likely to be able to help you.

---

### Post by MJN on 2008-08-18
It looks like you don't have the /etc/postfix/virtual file - do you? And does it contain the desired address-to-user mappings?
 
Mathew

---

### Post by HermanAB on 2008-08-18
If you really want/have to learn Postfix, or need to process millions of users, then fine.  However, if you just want a mail server that works, try [http://www.citadel.org](http://www.citadel.org).  It only takes about 20 minutes to set up and can handle 10s of thousands of users.

Cheers,

Herman

---

### Post by 3D Peruna on 2008-08-18
We got Ubuntu running on our server and from some servers receive the following error:

> This is the mail system at host myserver.com.

I'm sorry to have to inform you that your message could not be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can delete your own text from the attached returned message.

                   The mail system

<sentto@domain.com>: host mail.primary.net[216.87.38.214] said: 553 5.5.4
    <user>... Domain name required for sender address user (in
    reply to MAIL FROM command)


Is there something I can do to resolve this?

TIA

---

### Post by MJN on 2008-08-18
Given you have modified the error message it is not possible to say with certainty (as by making the changes you have likely mispresented the true error) but it looks like your outgoing mails do not have a domain name in the From: line hence your mail server is using this non-fully qualified address in its envelope.... many MTAs don't like this because it is a violation of the RFCs (other than for bounces), looks like spam and also means it is impossible to send non-delivery reports should it be accepted and then found to be undeliverable.

Post an unmodified error message if at all possible, tell us what mail server you're using (and its configuration), what client you're using (and it's configuration e.g. what is the From: address set to?) and we can take it from there.

Don't make us guess - help us to help you.

If you're using Postfix then you could use the **append_dot_mydomain = yes **directive assuming your mydomain directive is correctly set and your clients cannot be configured properly (it is their responsibility to define this).

Mathew

P.S. You really ought to start your own thread and not hijacking someone else's.

---

### Post by 3D Peruna on 2008-08-18
Thanks.  Sorry about the thread hijack.  Unintentional (see # beans to the left).

---

### Post by MJN on 2008-08-18
Well whilst you're here you we might as well help you out! (the OP's query is likely solved now)

Mathew

---

### Post by ub007 on 2008-08-18
Thanks for moving this thread to the server platorm.
> It looks like you don't have the /etc/postfix/virtual file - do you? And does it contain the desired address-to-user mappings?

Yep,your right mate,i didnt have that file...i had made a typo error and created a new file instead of /etc/postfix/virtual .I just sorted it out.....but now faced with a different issue...

Sending and receiving mails on the localhost works fine.Now how do i extend it to my local intranet.....

This is how my /etc/postfix/main.cf looks like



> myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mynetworks = 127.0.0.0/8, 192.168.11.2/24
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all  


And these are my entries for /etc/postfix/vmaps


> 
[email]info@ub.surey.ac.uk[/email] ub.surey.ac.uk/info/
[email]david@ub.surey.ac.uk[/email] ub.surey.ac.uk/david/  

/etc/postfix/vhosts reads


> 
ub.surey.ac.uk  

I'm able to send mails to [email]info@ub.surey.ac.uk[/email] and [email]david@ub.surey.ac.uk[/email] as root.

I can find them at /home/vmail/ub.surey.ac.uk/info/new & /home/vmail/ub.surey.ac.uk/david/new

Now how can i test this mail set up from a remote machine on the intranet?
What i need to do is send & recieve mails to [email]david@ub.surey.ac.uk[/email] from the other PCs on my local intranet.In effect that would provide an email system for my intranet.I'm not using DNS,however i have all the system names are included in /etc/hosts.Thanks in advance

I posted the same in ABT,plz ignore......didnt check this thread first,i know i should have,my apologies...

Cheers
David

---

### Post by HermanAB on 2008-08-18
I test using telnet, mail and mutt:
telnet server 25
mail -s testmessage whoever@server
mutt -f /var/spool/mail/user

Cheers,

Herman

---

### Post by ub007 on 2008-08-18
Thanks mate...cant wait to try that out tomm,btw,....did u have a look at my config file...is everything ok with it?

---

### Post by MJN on 2008-08-18
As Herman says, testing from the command line can be done as per the above (I prefer the low-level raw telnet option).

However, presumably your next step if you haven't already done so is to set up a POP/IMAP server for your clients to access their stored mail. Having done this you can then configure those clients to use that server to retrieve their incoming mail and your newly created Postfix server to send. Those clients may even be willing to be half-configured for use now with Postfix in a 'send only' mode.

Incidentally, if the quote above is your configuration file in its entirety you would be wise to explicitly state some more variables that are already configured as their default. One example would be **smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination** which gives you in no uncertain terms details of who your server will work for and to what extent (in this case it'll trust the localhost/LAN to send anywhere, and not allow 3rd parties to send to anywhere but domains you are responsible for).

Mathew

---

### Post by ub007 on 2008-08-18
> presumably your next step if you haven't already done so is to set up a POP/IMAP server for your clients to access their stored mail.


Well thats exactly what i need to do....My aim is to measure the performance of the IMAP server.But to be honest,i was confused as to what exactly an IMAP server does and where it resides.....
I know what an MTA ,postfix in this case does,but when it comes to an imap server,its a little confusing....From your post i assume, i will need to install courier-imap only on the client machines...n use this server to retrieve  mails on the respective PCs and utilize the postfix on ub.surey.ac.uk to send mails. A lot of How-Tos show IMAP being installed on the server machine which is a bit confusing.... 

Secondly could anyone tell me how this works in the case of a webmail like gmail..where would the IMAP server reside on?

---

### Post by MJN on 2008-08-18
At the most basic level Postfix is concerned with only two things - accepting mail for your clients/users and sending mail out for them.

Once the mail has been delivered your users needs a means of accessing that mail through their clients (which could be traditional applications or webmail). They usually do this by conversing with a POP/IMAP server. Such a server/service exists to not only to allow access to the delivered mail but also to manage enhanced features such as stored/archived mail in folders etc (particularly in the case of IMAP which I strongly recommend).

In the case of Gmail/Yahoo they appear to the user simply as mail client however their backends will consist of mail servers and POP/IMAP servers (or bespoke services that provide similar functions).

Then we have something like Citadel which muddies the water even further by wrapping up every last bit of functionality of all the above (and more) into one monstrous entity - the epitome of 'jack of all trades, master of none' if you like... 

(completely ignore that last sentence - I only included it because it'll give HermanAB a heart attack ;))

Mathew

---

### Post by ub007 on 2008-08-18
Thanks a ton,finally everything seems to make sense....

> Once the mail has been delivered your users needs a means of accessing that mail through their clients (which could be traditional applications or webmail). They usually do this by conversing with a POP/IMAP server.
So where do u suggest i install an IMAP server.
-install it on a separate PC and configure the clients to access it to retrieve mails or install IMAP servers on each individual client?
if i choose the first method,i'll have one PC as the postfix server and another as IMAP server and the remaining clients utilizing both these machines,do i make sense?or am i missing something here?

> In the case of Gmail/Yahoo they appear to the user simply as mail client however their backends will consist of mail servers and POP/IMAP servers (or bespoke services that provide similar functions).

So clearly those IMAP/POP servers are owned by google or yahoo..

Lastly,a bit off topic,...If i were to test IMAP server,how would that be?like if to test a webserver,i could send simultaneous Http requests to it and load test it...like wise..how do i stress the IMAP server,would writing a script asking the client to retrieve several mails from the IMAP server in a sec do the job?

---

### Post by MJN on 2008-08-18
> **ub007 said:**
> So where do u suggest i install an IMAP server.

In your circumstances you put it on the same machine as Postfix. There's need only be one IMAP server, just like there need only be one mail server.

> So clearly those IMAP/POP servers are owned by google or yahoo..So theres no point in ignoring the postfix ,installing IMAP servers on the clients,connecting to the internet  and trying to measure the time taken to download mails from the IMAP server...

I'm not sure what you mean there, but I'd be inclined to ignore it! (perhaps the confusion is down to the number of servers you though you needed?)

Do some Google searching for IMAP - there's plenty of information out there just waiting to be absorbed.

Mathew

---

### Post by ub007 on 2008-08-18
Thats ok...The info u gave me is good enuff,i now got a clear picture of how it works....
> 
I'm not sure what you mean there, but I'd be inclined to ignore it! (perhaps the confusion is down to the number of servers you though you needed?)

Its a bit off topic,...if i were to test a webserver,i could send simultaneous Http requests to it and load test it...like wise,i was wondering how to stress test the IMAP server,guess writing a script asking the client to retrieve several mails from the IMAP server in a sec would do the job....my project is to measure the performance of the IMAP server under load....yup,in the real world scenario it would be along the lines of how many servers i would need....


> So clearly those IMAP/POP servers are owned by google or yahoo..
i was refering to the part where you said 'In the case of Gmail/Yahoo they appear to the user simply as mail client however their backends will consist of mail servers and POP/IMAP servers (or bespoke services that provide similar functions). ' was just confirming my understanding on that :)Thanks for all the help

---

### Post by ub007 on 2008-08-19
> I test using telnet, mail and mutt:
telnet server 25
mail -s testmessage whoever@server
mutt -f /var/spool/mail/user

Cheers,
Herman

I did the following

```
telnet ub.surey.ac.uk 25 // ub.surey.ac.uk is the server with postfix & imap
mail from:root@cl.surey.ac.uk  // client machine
rcpt to:david@ub.surey.ac.uk
data
my first mail
```

works fine,the mail is sent and i can view it on my server ub.surey.ac.uk
at /home/vmail/ub.surey.ac.uk/david/new //happy with that :)

However how do i access the same from my client -cl.surey.ac.uk

jeff@cl:$mutt -f /var/spool/mail/david 
error msg: No such file or directory

I am definitly missing something here..but cant figure out what it is...plz help..:confused:
How do i configure my client to retieve mails from the server.I have installed IMAP on the server.

---

### Post by MJN on 2008-08-19
If I understand your question correctly, this is where your IMAP server comes in.
 
You client connects to the IMAP server, and it serves up the received mail from the disk.
 
Mathew

---

### Post by ub007 on 2008-08-19
> If I understand your question correctly, this is where your IMAP server comes in.

You client connects to the IMAP server, and it serves up the received mail from the disk.

Well,partly yes....
I installed courier imap as my imap server using the how to on [https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier)

> telnet localhost imap
imap login user password
imap OK LOGIN Ok. works fine...so imap is uo and running on the server..
> 
You client connects to the IMAP server
thats where i need guidance..how do i connect to the IMAP server on ub.surey.ac.uk and read the mails from my client.

eg,i found an article which tells me how i can download thunderbird mail client and configure it to use the imap server and i would be able to read the mail from my client machine...
like wise is there anything simpler from the command line that i can use....

---

### Post by HermanAB on 2008-08-19
I suggest that you install the dovecot POP/IMAP server.  It is quite good and has special workarounds to handle the worst MS Outlook bugs.

Cheers,

Herman

---

### Post by MJN on 2008-08-19
> **ub007 said:**
> eg,i found an article which tells me how i can download thunderbird mail client and configure it to use the imap server and i would be able to read the mail from my client machine...
like wise is there anything simpler from the command line that i can use....

What could be simpler than that? (and I second Herman's advice)

Mathew

---

### Post by ub007 on 2008-08-19
yep,i may very well install thunderbird or kmail.
Theres one more issue though...I tried testing my imap server configuration

[email]simon@ub.surey.ac.uk[/email]:~$ telnet ub.surey.ac.uk 143
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
* OK Courier-IMAP ready.
Copyright 1998-2002 Double Precision, Inc.
See COPYING for distribution information.


AB LOGIN "username" "password" // which 'username & password' do i use here...

 [https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier) states 'Where user and password are local accounts with a Maildir directory.'

The two accounts in the vmaps table are [email]info@ub.surey.ac.uk[/email] & [email]david@ub.surey.ac.uk[/email]-but havent created any passwords on them.So how do i check the IMAP connection for the mail boxes of info & david.All i have done is created entries for entries for /etc/postfix/vmaps and it reads

> info@ub.surey.ac.uk ub.surey.ac.uk/info/
[email]david@ub.surey.ac.uk[/email] ub.surey.ac.uk/david/

The mails are found at /home/vmail/ub.surey.ac.uk/info/new & /home/vmail/ub.surey.ac.uk/david/new respectively.How do i equate that to the IMAP -user & password?

---

### Post by MJN on 2008-08-20
You will need to lookup the Courier documentation for authenticating 'virtual' vs 'system' accounts.
 
Mathew

---

### Post by ub007 on 2008-08-20
Thanks...

I tried to validate them using mysql.
Heres what i did so far...

/etc/postfix/main.cf
```

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = zomb.lboro.ac.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = zomb.lboro.ac.uk, localhost, localhost.lboro.ac.uk
relayhost =
mynetworks = 127.0.0.0/8, 192.168.11.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
```

mysqladmin -u root -p create mail

Users table
> 
[email]david@zomb.lboro.ac.uk[/email]  	/k9NpDD9T03DM  	10485760
[email]emma@zomb.lboro.ac.uk[/email] 	        CkcTt3dpqBOFg 	10485760

domain table
> domain
zomb.lboro.ac.uk

/etc/mysql/my.cnf contains

bind-address            = 127.0.0.1

created /etc/postfix/mysql-virtual_domains.cf
vi /etc/postfix/mysql-virtual_forwardings.cf
vi /etc/postfix/mysql-virtual_mailboxes.cf
/etc/postfix/mysql-virtual_email2email.cf
/etc/postfix/mysql-virtual_transports.cf
/etc/postfix/mysql-virtual_mailbox_limit_maps.cf

/etc/courier/authmysqlrc 

> MYSQL_SERVER localhost
MYSQL_USERNAME mail_admin
MYSQL_PASSWORD mail_admin_password
MYSQL_PORT 0
MYSQL_DATABASE mail
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD password
#MYSQL_CLEAR_PWFIELD password
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD email
MYSQL_HOME_FIELD "/home/vmail"
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
#MYSQL_NAME_FIELD
MYSQL_QUOTA_FIELD quota

when i test this on the local host,It shows mail sent but i cant find it in /home/vmail
I assume the mailbox is not being created..how do i debug this

Cheers
david

---

### Post by ub007 on 2008-08-20
Figured out y its not working.Authentication to IMAP fails.It workd fine with postfix though


telnet localhost 143
gets connected
a LOGIN username password
I get: 

* BYE Temporary problem, please try again later
Connection closed by foreign host.


WHats going wrong here?

---

### Post by MJN on 2008-08-21
Doe the logs say anything? Perhaps try increasing the verbosity?
 
As I said, I don't use Courier so they'll mean little more to me than to you but you should still check them as they usually prove helpful.
 
Mathew

---

### Post by ub007 on 2008-08-21
> Aug 21 14:25:24 leo authdaemond: zero rows returned
Aug 21 14:25:24 leo  authdaemond: no password available to compare
Aug 21 14:25:24 leo authdaemond: authmysql: REJECT - try next module
Aug 21 14:25:24 leo authdaemond: FAIL, all modules rejected
Aug 21 14:25:24 leo imapd: LOGIN FAILED, user=sales, ip=[::ffff:127.0.0.1]

thats the log i'm getting :( Any suggestions

---

### Post by windependence on 2008-08-21
If you get stuck and frustrated after all this nasty config stuff, do as Hermann said earlier and try Citadel. I would also recommend Zimbra. These are both complete mail packages that install everything you need with just one script....so much easier, unless of course you just want to learn or you like pain. ;)

-Tim

---

### Post by ub007 on 2008-08-26
Hi,i still refuse to give up:popcorn: ,however may consider dovecot instead of courier imap.But i think the primary is with postfix:
When i sent a mail from [email]root@inter.surey.ac.uk[/email] to [email]david@inter.surey.ac.uk[/email]
i find the mail in /var/mail/david3 //david3 is my system user name

cat david3
hi
welcome

i think its because my /etc/aliases reads
postmaster : root
root: david3 //guess the mail is bounced back to david3

y isnt the mail being sent to [email]david@inter.surey.lboro.ac.uk[/email]????

```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = inter.surey.ac.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = inter.surey.ac.uk, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $vir$
```

These are the domains and user added
```
INSERT INTO `domains` (`domain`) VALUES ('inter.surey.ac.uk');INSERT INTO `domains` (`domain`) VALUES ('inter.surey.ac.uk');
INSERT INTO `users` (`email`, `password`, `quota`) VALUES ('david@inter.surey.ac.uk', ENCRYPT('secret'), 10485760);
```

---

### Post by ub007 on 2008-08-27
Finally got it working:

> Connected to localhost.
a OK LOGIN Ok.
a select inbox
* FLAGS (\Draft \Answered \Flagged \Deleted \Seen \Recent)
* OK [PERMANENTFLAGS (\* \Draft \Answered \Flagged \Deleted \Seen)] Limited
* 5 EXISTS
* 1 RECENT
* OK [UIDVALIDITY 1219836018] Ok
* OK [MYRIGHTS "acdilrsw"] ACL
a OK [READ-WRITE] Ok

It shows 5 EXISTS...Could anyone plz tell me how to read them from this telnet session?
Thanks in advance

---


---
title: "How to install RequestTracker with email facility on Ubuntu 10.04"
date: 2010-05-09
forum: Tutorials
---

### Post by chrismyers on 2010-05-09
[FONT=Times New Roman][SIZE=3]The following demonstrates how to install RequestTracker 3.8.7 with email facility on Ubuntu server 10.04.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]RequestTracker really shines when it works with email as it can notify the end user at key stages of a ticket progress. It will even record the thread of a conversation between the RT user & the ticket requester.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Before you start, please create a pop3 email account on your mail server. In this example example IT-Support@yourdomain[/SIZE][/FONT][SIZE=3]


**[FONT=Cambria][COLOR=#365f91]Install Ubuntu 10.04 & RT related packages[/COLOR][/FONT]**[/SIZE]     [SIZE=3]
[/SIZE][FONT=Times New Roman][SIZE=3]
Boot from the Ubuntu 10.04 CD & follow the installation steps.[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]When presented with the Software Selection screen, select the following:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Lamp Server[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]Mail Server[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]OpenSSH Server[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set the MYSQL root password when prompted (twice).[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set postfix to "Internet site" when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set Email to your smtp server when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Reboot when install finished & login as the username you created.[/SIZE][/FONT][SIZE=3]


[/SIZE]     [LEFT][SIZE=3]***[FONT=Times New Roman]I suggest logging in remotely via ssh or Putty from now on to make it easy for you to copy & paste in the following commands.[/FONT]***[/SIZE][/LEFT]
 [SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the following command to gain root access:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]sudo su -[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the following command to install packages:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]apt-get update; apt-get install rt3.8-apache2 rt3.8-clients rt3.8-db-mysql request-tracker3.8 fetchmail[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Change "rt.tickets" to "tickets" when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Respond "Yes" to RT_SiteConfig.pm permissions when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Respond "Yes" to Configure RT with dbconfig-common when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Enter the MYSQL root password you used earlier in order to set up the new RT database when prompted.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set the RT database access password (this password is for RT to connect to MYSQL & is stored in RT_SiteConfig.pm).[/SIZE][/FONT][SIZE=3]


**[FONT=Cambria][COLOR=#365f91]Request Tracker config file[/COLOR][/FONT]**[/SIZE]       [SIZE=3]

[/SIZE]     [FONT=Times New Roman][SIZE=3]Run the following command to back-up the RT config file:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]cp /etc/request-tracker3.8/RT_SiteConfig.pm /etc/request-tracker3.8/RT_SiteConfig.pm.old[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the following command to edit the RT config:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/request-tracker3.8/RT_SiteConfig.pm[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Comment out the following two lines with a # as shown below:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]#Set($CorrespondAddress , 'rt@tickets');[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]#Set($CommentAddress , 'rt-comment@tickets');[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Paste in the following two lines:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set($MaxAttachmentSize , 10000000);[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]Set($FriendlyFromLineFormat, "\"%s\" <%s>");[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Save the file.[/SIZE][/FONT][SIZE=3]


**[FONT=Cambria][COLOR=#365f91]Outbound Email config[/COLOR][/FONT]**[/SIZE]     [SIZE=3]

[/SIZE][FONT=Times New Roman][SIZE=3]Run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/postfix/main.cf[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Find the line containing "relayhost" & add your smtp mail server[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Save the file.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]service postfix restart[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Test Outbound mail (Postfix) by emailing a file – (This example sends /etc/fstab).[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]mailx -s "Postfix Test" YourOwnMailbox@domain < /etc/fstab[/FONT]
```[/SIZE][/FONT][SIZE=3]


[/SIZE]     [LEFT][SIZE=3]*[FONT=Times New Roman]Use your own email address in the above command[/FONT]*[/SIZE][/LEFT]
 [SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Check your e-mail client to see if this is working.[/SIZE][/FONT][SIZE=3]


**[FONT=Cambria][COLOR=#365f91]Apache2 config[/COLOR][/FONT]**[/SIZE]     [SIZE=3]

[/SIZE][FONT=Times New Roman][SIZE=3]Run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/apache2/apache2.conf[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Append the following at the bottom of the file on a new line:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]ServerName tickets[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Save the file & run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/apache2/sites-available/default[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Find the last line "</VirtualHost>" and paste in the following two lines just above it:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Include /etc/request-tracker3.8/apache2-modperl2.conf[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]RedirectMatch ^/$ /rt[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Save the file & run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]a2enmod rewrite; service apache2 restart[/FONT]
```[/SIZE][/FONT][SIZE=3]


[/SIZE]      [FONT=Cambria][SIZE=3][COLOR=#365f91]**Configure RT from your web Browser login**[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Log in to RT - Open your web browser, enter your RT IP address use default root login:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]root : password[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Navigate to:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Configuration | Global | Group Rights[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Find "Everyone" in "System Groups" and grant the following rights:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]CommentOnTicket[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]CreateTicket[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]ReplyToTicket[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Navigate to:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Configuration | Queues | General[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Set the "Reply Address" & "Comment Address" to IT-Support@yourdomain[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Change “Description” to “IT-Support”[/SIZE][/FONT][SIZE=3]


[/SIZE]     [LEFT][SIZE=3]*[FONT=Times New Roman]Use a valid email address for your domain.[/FONT]*[/SIZE][/LEFT]
 [SIZE=3]


[/SIZE]     [SIZE=4]**[FONT=Cambria][COLOR=#365f91]Inbound e-mail config[/COLOR][/FONT]**[/SIZE][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/default/fetchmail[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Modify the last line to read:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]START_DAEMON=yes[/SIZE][/FONT][SIZE=3]


[/SIZE]     [FONT=Times New Roman][SIZE=3]Run the command to open the editor & create a new blank file:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]nano /etc/fetchmailrc[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Paste in the following six lines:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]set daemon 60[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]set invisible[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]set no bouncemail[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]set no syslog[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]set logfile /var/log/fetchmail.log[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Times New Roman][SIZE=3]poll YOURMAILSERVER protocol pop3 username "IT-Support" password "secret" mda "/usr/bin/rt-mailgate --queue general --action correspond --url http://localhost/rt/" no keep[/SIZE][/FONT][SIZE=3]


[/SIZE]     [LEFT][SIZE=3]*[FONT=Times New Roman]Note: the last line (beginning poll) is long & may have wrapped in your display.[/FONT]*[/SIZE][/LEFT]
 [SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Run the command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]touch /var/log/fetchmail.log; chown fetchmail /var/log/fetchmail.log[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Reboot.[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]To watch inbound email status, run the following command:[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]```
[FONT=Times New Roman]tail –f  /var/log/fetchmail.log[/FONT]
```[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Send an email to the account: IT-Support@yourdomain[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=Times New Roman][SIZE=3]Fetchmail should pick up this email within 60 seconds & forward it into RT. RT with then reply to you. You should see the ticket in the web console.[/SIZE][/FONT][SIZE=3]


[/SIZE]     [LEFT][SIZE=3]*[FONT=Times New Roman]Note: Once you are happy that inbound email is working, comment out the set logfile line in /etc/fetchmailrc with a # & reboot.[/FONT]*[/SIZE][/LEFT]
 [SIZE=3]
[/SIZE]  [SIZE=3]
[/SIZE] [LEFT][FONT=Times New Roman][SIZE=3]**Cheers... Please respond to this thread to say if this How To helped you. :P**[/SIZE][/FONT][/LEFT]

---

### Post by Wooglin on 2010-07-02
Worked excellently. Thanks!

If your mail server happens to not support POP, you can also use an IMAP account.
Simply change the last line in /etc/fetchmailrc from 
```
poll YOURMAILSERVER protocol pop3 username...
```
to
```
poll YOURMAILSEERVER protocol imap username...
```

If, for some reason you wish to keep a copy on the email server remove the "no keep" from the end of that line, and the messages will remain in the email inbox.

---

### Post by TheFuturian on 2010-09-01
Another success here, thank you very much. :D Might have to add a redirect at the root of my site so visitors just go straight to "/rt", but other then that, fantastic!

_***Edit***_
The relevant section of /etc/apache2/sites-available/default is:-

```
Include /etc/request-tracker3.8/apache2-modperl2.conf
RedirectMatch ^/$ /
```

Within apache2-modperl2.conf is this section:-

```
# Normally a request for a directory will be rewritten to index.html
# (or similar) by default if that file exists. For some reason this does
# not happen with the handler being set to perl-script. We thus have to
# do it ourselves using mod_rewrite.

RewriteEngine on

# You might need to alter these two lines which refer to /rt to match
# whatever base URL you are using for your rt3 site.

RewriteRule ^/rt$ /rt/
RewriteRule ^/rt/(.*)$ /usr/share/request-tracker3.8/html/$1
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^(/usr/share/request-tracker3.8/html.*)/$ $1/index.html
```

Not quite sure what's going on there to be honest.. Time to Google.

---

### Post by majjj on 2011-02-14
I get this error, can somebody help me?

```
Setting up request-tracker3.8 (3.8.7-1ubuntu2) ...
**WARNING**
**WARNING**  If you are using mod_perl or any form of persistent perl
**WARNING**  process such as FastCGI or SpeedyCGI, you will need to
**WARNING**  restart your web server and any persistent processes now.
**WARNING**
hostname: Name or service not known
dpkg: error processing request-tracker3.8 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 request-tracker3.8
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

EDIT: Also tried to reboot, no luck

---

### Post by drcraige on 2011-03-24
Hello, can someone please provide some insight? I am having difficulty setting up & testing, Outbound Email Configuration.
 
My mail service is pop3 hosted externally by Hostway. I am configuring the relay host as smtp.mydomain.com in /etc/postfix/main.cf
 
When testing email nothing is being sent out.
Any suggestions as to what I may be missing would be appreciated.

---

### Post by chrismyers on 2011-03-24
> **drcraige said:**
> Hello, can someone please provide some insight? I am having difficulty setting up & testing, Outbound Email Configuration.
 
My mail service is pop3 hosted externally by Hostway. I am configuring the relay host as smtp.mydomain.com in /etc/postfix/main.cf
 
When testing email nothing is being sent out.
Any suggestions as to what I may be missing would be appreciated.

Are you ***sure ***you are using the correct outbound address?

Test outbound connectivity from your linux box by using:

telnet YourOutboundMailServer 25

Obviously, you should use your own providers outbound mail relay.

More info on testing:

[http://www.activexperts.com/activemail/telnet/](http://www.activexperts.com/activemail/telnet/)

---

### Post by drcraige on 2011-03-24
Thank you for your quick response. 
The server at Hostway  (smtp.mydomain.com) refuses the Telent connection.
Am I confused as to which mail server you are referring to?
I believe I need to have credentials to relay the mail through Hostway. (Example- [EMAIL="username@mydomain.com"]username@mydomain.com[/EMAIL]  password ) Where do I configure that information?
 
Thank you again

---

### Post by chrismyers on 2011-03-25
> **drcraige said:**
> Thank you for your quick response. 
The server at Hostway  (smtp.mydomain.com) refuses the Telent connection.
Am I confused as to which mail server you are referring to?
I believe I need to have credentials to relay the mail through Hostway. (Example- [EMAIL="username@mydomain.com"]username@mydomain.com[/EMAIL]  password ) Where do I configure that information?
 
Thank you again

This is probably a question for your provider.

I'll give you an ***example*** with my provider details:

Inbound: smtp.plus.net

Outbound: relay.plus.net

Cheers.

---

### Post by Sef on 2011-03-25
Moved to T & T.

---

### Post by drcraige on 2011-03-28
I just want to post here for others the site that helped me to get Postfix to send outbound email via my Hostway pop3 account. [http://newbiedoc.berlios.de/wiki/Debian_newbie_help_documentation](http://newbiedoc.berlios.de/wiki/Debian_newbie_help_documentation)

---

### Post by iamthelinux on 2011-09-08
I followed the instructions given in #1(by chrismayers). I am having a problem when i try to configure rt from web browser. The login screen is showing. But when i login, the browser returns a blank page with the following text
"Can't call method "_Accessible" without a package or object reference at /usr/local/share/perl/5.10.1/DBIx/SearchBuilder/Record.pm line 422."

Thanks in advance for any help.

---


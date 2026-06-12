---
title: "php mail() and sendmail"
date: 2008-07-28
forum: Server Platforms
---

### Post by theolster on 2008-07-28
I'm trying to send mail from a php script (cli & apache) on a hardy server and I really don't know how to start configuring this.

The error in /var/log/mail.log looks something like this:```
Jul 28 14:38:01 <removed hostname> sm-mta[18001]: m6PElsEm007582: to=<oliver@<removed hostname>>, ctladdr=<www-data@<removed hostname>> (33/33), delay=2+22:50:07, xdelay=00:00:00, mailer=esmtp, pri=38460480, relay=<removed hostname>., dsn=4.0.0, stat=Deferred: Name server: <removed hostname>.: host name lookup failure
```
So I assume that sendmail is not correctly configured.  I've had a bit of a google on this subject and I really don't know where to start...
Has anyone got any ideas.

---

### Post by Titan8990 on 2008-07-28
Try adding the hostname you are trying to look up to your /etc/hosts file. Any reason you selected sendmail as a MTA?

---

### Post by theolster on 2008-07-29
> **Titan8990 said:**
> Try adding the hostname you are trying to look up to your /etc/hosts file.I tried this, but it didn't work.

> **Titan8990 said:**
> Any reason you selected sendmail as a MTA?Because this is the default for php.  I really don't want to be fiddling around trying to set up mail!!!  So if you have an alternative solution (ie something other than sendmail) that's reasonably easy to implement then I'm all ears.

---

### Post by Titan8990 on 2008-07-29
IMO, there is no email server that is "easy" to implement. Sendmail, however, is by far the most difficult. There are MTAs that are direct substitutes for sendmail. The one I use is Exim4 and is the official MTA for Debian based distros.

I am personally not a programmer but have you tried looking at the source code for an already existent PHP mailer such as squirrelmail?

---

### Post by theolster on 2008-07-29
I completely agree.  I have heard how hard email servers can be.

I've tried googling instructions for exim4, but couldn't get it working.  Can you point me in the right direction, or break down the steps I need to go trough to get it working?

---

### Post by amenszer on 2008-07-29
Yeah sendmail can be a pain. I recommend using ssmtp for doing simple PHP mail functions.

---

### Post by theolster on 2008-07-29
To be honest I'm happy to take either exim or ssmtp - but how do I set this up for php?

I've actually tried several attempts at getting various different ones working, but with no success.

---

### Post by Titan8990 on 2008-07-29
This is a guide I wrote my work's internal wiki. My boss gave me permission a while back to make it available to the public but I had not got a chance to do it. Try to ignore the wiki/HTML code. Here it is:


This guide is here it assist with setting up Exim4 on a Ubuntu server. This E-Mail server also hosts webmail. 

==Dependencies==

We will begin by installing everything that were are going to need for this server. 

Needed dependencies and a short description:

*'''exim4''' - The E-Mail Server
*'''eximon4''' - Utility for monitoring the E-Mail Server
*'''spamassassin''' - Used for filtering spam
*'''spamc''' - Dependency of spamassassin
*'''spampd''' - More for spamassassin
*'''squirrelmail''' - Web mail client
*'''apache2''' - Web server used for hosting the web mail client
*'''courier-imap''' - Needed for IMAP.
*'''clamav-daemon''' - Needed to scan mail for viruses


So now to install these dependencies, copy the following into the terminal:

<code>$sudo apt-get install exim4-daemon-heavy eximon4 spamassassin spamc squirrelmail apache2 courier-imap clamav-daemon sasl2-bin courier-imap-ssl</code>

There are more dependancies that are needed but they will download and install automatically when the command above is given.

<i>Note: You must have exim4-daemon-heavy in order to use an anti-virus.</i>

Now that we have the the needed daemons we can move on to configuring exim4.
<br>

==Exim4 Configuration==
<br>
===Main Configuration File===

The main config file is found in the /etc/exim4/ directory and is named update-exim4.conf.conf. You must be logged in as root in order to edit this file. <i>Note: You <b>can not</b> use <code>"su -"</code> to become root from the terminal and then run gedit, you must actually be logged in as root. There is another alternative. You can run a command as a regular user as long as you prefix it with gksudo. Another alternitvie is to use a command line editor such as vim or nano.</i>
<br>
<br>
So to edit the config file we type into the terminal:

<code>$gedit /etc/exim4/update-exim4.conf.conf</code>

The config file will look like this:

<pre>dc_eximconfig_configtype='internet'
dc_other_hostnames='MYDOMAIN.com'
dc_local_interfaces=''
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets='xxx.xxx.xxx.xxx; xxx.xxx.xxx.xxx;'
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='false'
dc_mailname_in_oh='true'
dc_localdelivery='maildir_home'</pre>

The main things we need to be concerned with are the following:

<b>dc_eximconfig_configtype='internet'</b> - Giving the value "internet" allows exim4 to send and recieve mail both locally and remotely

<b>dc_other_hostnames='MYDOMAIN.com'</b> - This is where you will specify the domain in which the server will be running for. This can be an IP address or a FQDN

<b>dc_relay_nets='xxx.xxx.xxx.xxx; xxx.xxx.xxx.xxx;'</b> - This specifies what IPs can send mail through the E-Mail server. The ip addresses need to be separated by a ";"

<b>dc_localdelivery='maildir_home'</b> - This specifies where and how E-mail is stored. This must be changed to value you shown in order to use IMAP. 
<br>
<br>

===Smaller Configuration Files===

We only have one thing to be concerned about in the next config file. It is located in the /etc/default directory and is named exim4. 

So to edit this we type the following into the terminal:

<code>$ gedit /etc/default/exim4</code>

The only setting we need to change here is <i>QUEUEINTERVAL</i>. This specifies how often the exim4 daemon checks for new mail. The default is 30m, way too long to be waiting on an e-mail. You can set it to whatever you like but I set mine to 1m. 

The end result will look like this:

<code>QUEUEINTERVAL='1m'</code>
<br>
<br>
===Setting Up Maildir===

Remember the <i>dc_localdelivery</i> setting from earlier? It will not work if there is no maildir directory so we need to create one.

The following terminal lines will create a maildir for all users on the system in the /home/%user%/ directory.

<code>$ maildirmake /etc/skel/Maildir/</code>

What this does is automatically creates maildirs for all new users created.

<code>$ maildirmake ~/Maildir/</code>

The command above will create maildirs for all users currently on the system.

<b>Exim4 Configuration is now Complete. It is time to test out your hard work</b>
<br>
<br>

===Testing Exim4 and Loading the Config File===

Now it is time to put that config file to use. Type the following into the terminal:

<code>$ update-exim4.conf</code>

Now test your config file for errors. If the following does not return an error message then you are good to go:

<code>$ exim4 -bV</code>
<br>
<br>
===Starting/Restarting Exim4===

Now we successfully configured exim4 we can start the daemon with the following:

<code>$ /etc/init.d/exim4 start</code>

If we simply type <code>$ /etc/init.d/exim4</code> we will see all the options for the exim daemon. It should look like the following:

<code>Usage: /etc/init.d/exim4 {start|stop|restart|reload|status|what|force-stop}</code>

Whenever we make a change we will
---------------------------------------------------------
Server Settings use the "restart" option to restart exim4. If the e-mail server is live then we would use "reload" to update the config files without stopping the daemon. <b>Remember, anytime you change a config file the daemon will need to be reloaded or restarted. I will not be specifically telling you to restart the daemon each time a config file gets changed because it will occur so often during the course of this tutorial.</b>

I like to make a global command for restarting Exim as well as any other daemons I might have to restart after changes. To do this see the article on [[Handling Frozen Messages]].

That is everything for Exim4, we can move on to configuring the other daemons our e-mail server will be using.
<br>
<br>

==Setting Up Courier-IMAP==

Courier-IMAP itself actually does not require any kind of configuration. Once it is installed it is ready to communicate with your clients. What we will have to configure is the daemon that is going to authenticate IMAP as well as create a certificate for SSL/TLS use. This is a bit more tricky then creating a certificate for Exim4. So lets get started.
<br>
<br>
===Creating Courier-IMAP-SSL Certificate===

We begin by editing the cnf file for IMAP. IMAP typically will absolutely requires a signed certificate but we are going to work around that until we can get a signed certificate. Lets start by having a look at the cnf file located in /etc/courier/imapd.cnf:

<pre>RANDFILE = /usr/lib/courier/imapd.rand

[ req ]
default_bits = 1024
encrypt_key = yes
distinguished_name = req_dn
x509_extensions = cert_type
prompt = no

[ req_dn ]
C=US
ST=NY
L=New York
O=Courier Mail Server
OU=Automatically-generated IMAP SSL key
CN=localhost
emailAddress=postmaster@example.com</pre>

So now we need edit this file from it's defaults. We want it to look like this: $sudo nano /etc/courier/imapd.cnf

<pre>RANDFILE = /usr/lib/courier/imapd.rand

[ req ]
default_bits = 1024
encrypt_key = yes
distinguished_name = req_dn
x509_extensions = cert_type
prompt = no

[ req_dn ]
C=US
ST=STATE
L=CITY
O=COMPANY
OU=Email
CN=mail.MYDOMAIN.com
emailAddress=root@MYDOMAIN.com


[ cert_type ]
nsCertType = server</pre>

Now we need to remove the old certificate that it generated when we installed courier. So we do the following: $sudo rm /etc/courier/imapd.pem

Finally, we need to generate the new certificate: $sudo dpkg-reconfigure courier-imap-ssl

The output should be similar to this:

<pre> * Stopping Courier IMAP-SSL server...                                   [ OK ] 
Generating a 1024 bit RSA private key
.................++++++
...................................++++++
writing new private key to '/usr/lib/courier/imapd.pem'
-----
1024 semi-random bytes loaded
Generating DH parameters, 512 bit long safe prime, generator 2
This is going to take a long time
.............+..............................+...................................................+.............................................................+.+...............................+...............................+..........................................+....................................+.....................+.....+.+........+.+..+....+..................+...........+....................+.............+...........+................................+...............................................................................++*++*++*++*++*++*
subject= /C=US/ST=KY/L=Louisville/O=Smart Systems Design/OU=Email/CN=mail.MYDOMAIN.com/emailAddress=root@MYDOMAIN.com
notBefore=Jul 15 16:37:44 2008 GMT
notAfter=Jul 15 16:37:44 2009 GMT
SHA1 Fingerprint=EF:8E:B3:40:83:93:73:04:C5:F6:BF:C8:6A:1B:28:01:5C:E9:31:93
 * Starting Courier IMAP-SSL server...                                   [ OK ] 
</pre>   
<br>
<br>

===Configuring SASL2-AUTH===

In order for it to start when the machine boots up we need to uncomment a line in the config file. So time to hit up gedit:

<code>$gksudo gedit /etc/default/saslauthd</code>

We need to se the value of "start" from the beginning of the config file. It should look like this:

<pre>#
# Settings for saslauthd daemon
#

# Should saslauthd run automatically on startup? (default: no)
START=yes</pre>

We need to tell exim4 that we are using the sasl2 daemon to authenticate. To do this we go to large config file found in /etc/exim4/:

<code>gedit /etc/exim4/exim4.conf.template</code>

I found that the easiest way to find the section we are looking for is to use gedit's find function to look for "sasl". We need to uncomment the lines that allow for "login". We can enable "plain" as well but it is not as secure as login. Here is a sample of the lines for sasl login and plain authentication:

<pre># Authenticate against local passwords using sasl2-bin
# Requires exim_uid to be a member of sasl group, see README.Debian.gz
# plain_saslauthd_server:
#   driver = plaintext
#   public_name = PLAIN
#   server_condition = ${if saslauthd{{$auth2}{$auth3}}{1}{0}}
#  server_set_id = $auth2
#   server_prompts = :
#   .ifndef AUTH_SERVER_ALLOW_NOTLS_PASSWORDS
#   server_advertise_condition = ${if eq{$tls_cipher}{}{}{*}}
#   .endif

 login_saslauthd_server:
   driver = plaintext
  public_name = LOGIN
   server_prompts = "Username:: : Password::"
   # don't send system passwords over unencrypted connections
  server_condition = ${if saslauthd{{$auth1}{$auth2}}{1}{0}}
   server_set_id = $auth1
   .ifndef AUTH_SERVER_ALLOW_NOTLS_PASSWORDS
   server_advertise_condition = ${if eq{$tls_cipher}{}{}{*}}
   .endif</pre>

Now save and exit gedit.

We now need to allow Exim4 to access the socket file. We do so with the following command:

<code>$ usermod -G daemon Debian-exim</code>

We need to tell Exim4 that it using this auth method. We do this by adding a line to the /etc/exim4/exim4.conf.template config file. So start by editing the file:

<code>$ gedit /etc/exim4/exim4.conf.template</code>

We need to <b>add</b> the following line to the config file: "MAIN_TLS_ENABLE = yes". It should be noted that there is another line preexisting in the file that says MAIN_TLS_ENABLE. We are not changing or modifying this value. We are creating a new line, anywhere in the configuration document. So here is is in code form:

<code>MAIN_TLS_ENABLE = yes</code>

Now we can create a certificate for this authentication.
<br>
<br>

===Creating a Certificate===

There is a application that will walk you through the steps of creating a certificate. To run the file type the following into the terminal:

<code>$ /usr/share/doc/exim4-base/examples/exim-gencert</code>

The application will then help you create our new certificate.
<br>
<br>

===Testing TLS===

We can use a program to verify that our TLS is working correctly. In order to do this we must first install the program. Type the following into the terminal:

<code>$ apt-get install swaks libnet-ssleay-perl</code>

Alright now to use this application to test we type the following into the bash shell:

<code>$ swaks -a -tls -q HELO -s localhost -au jasonb -ap '<>'</code>

The output should look similar to this:

<pre>=== Trying localhost:25...
=== Connected to localhost.
<-  220 einstein ESMTP Exim 4.69 Mon, 05 May 2008 16:02:30 -0400
 -> EHLO einstein
<-  250-einstein Hello localhost [127.0.0.1]
<-  250-SIZE 52428800
<-  250-PIPELINING
<-  250-STARTTLS
<-  250 HELP
 -> STARTTLS
<-  220 TLS go ahead
=== TLS started w/ cipher DHE-RSA-AES256-SHA
 ~> EHLO einstein
<~  250-einstein Hello localhost [127.0.0.1]
<~  250-SIZE 52428800
<~  250-PIPELINING
<~  250 HELP
 ~> QUIT
<~  221 einstein closing connection
=== Connection closed with remote host.</pre>

If there is something that is incorrect then it will error after the line "STARTTLS" and will immediately quit. If it looks like the output above then we have successfully set up TLS for Exim4. Now we can move on to scanning for spam and viruses.
<br>
<br>

==Using ClamAV to scan for Malware==

First thing we need to do is tell Exim4 that we are using an A/V and what it is. We will do this by editing the /etc/exim4/conf.d/main/01_exim4-config_listmacrosdefs file. You know the drill by now:

<code>$ gedit /etc/exim4/exim4.conf.template</code>

Now we are going to modify the following line found in the 02 section of the configuration file:

<code>av_scanner = clamd:/var/run/clamav/clamd.ctl</code>

The lines "av_scanner =" may already exist or be commented out. I can not remember. Just be sure that the line above exists in the configuration file.

Now we need to set the parameters of the A/V. We will be adding to the config file. So back to the terminal:

<code>$ gedit /etc/exim4/exim4.conf.template</code>

We must uncomment some lines here or clamav will scan the emails but exim4 will not reject malware that contains a virus unless we tell it to. Search and uncomment the lines as shown:

<pre>     # Deny if the message contains malware. Before enabling this check, you
  # must install a virus scanner and set the av_scanner option in the
  # main configuration.
  #
  # exim4-daemon-heavy must be used for this section to work.
  #
   deny
     malware = *
     message = This message was detected as possible malware ($malware_name).</pre>

Now to make sure that ClamAV has access rights:

<code>$ adduser clamav Debian-exim</code>

Now restart ClamAV and it is ready to go:

<code>$ /etc/init.d/clamav-daemon restart</code>
<br>
<br>

==Setting Up SpamAssassin==

Setting up SpamAssassin is much like the set up of the anti-virus. This time we will not just be uncommenting what is there. The comments prior to the spamassassin explain that there example is not good for practical purposes. What I wrote was basically a compilation of an example in the book and what was already there. The reason for the comments explaining that their example was not good is because it gave full Exim rights to spamassassin. My method omits that part.

So lets gedit that big config file once again: $sudo gedit /etc/exim4/exim4.conf.template

Around line 168 we need to uncomment the following:

<pre># For spam scanning, there is a similar option that defines the interface to
# SpamAssassin. You do not need to set this if you are using the default, which
# is shown in this commented example. As for virus scanning, you must also
# modify the acl_check_data access control list to enable spam scanning.

spamd_address = 127.0.0.1 783</pre>

Next we will need to add some lines in the ACL Check Data section.

Around line 884 add the following:

<pre>  #This is what I came up with as a Spam filter after reading the Exim4 wiki
  #and the Exim4 book. What we are doing is only scanning smaller email messages.

warn spam = ${if < {$message_size}{20k}{nobody}{false}}
message = X-Spam_score: $spam_score\n\
          X-Spam_score_int: $spam_score_int\n\
          X-Spam_bar: $spam_bar\n\
          X-Spam_report: $spam_report</pre>

That is all it takes to have spamassassin scan our e-mails. You may want to make some changes to the /etc/mail/spamassassin/local.cf file to define what it should consider spam. To find out more on how spam assassin's point system works you can view the following page: [http://spamassassin.apache.org/](http://spamassassin.apache.org/) or you can pick up that spamassassin book from the book shelves. For now we are going to stick with the defaults and modify them as we see a need.

==Webmail==

If you are at all familiar with how apache web servers work then this will not be much of a stretch. We begin by making a symbolic link from the squirrelmail directory to the apache2 www directory. Things linked to this directory will be displayed when people visit your web page or when you visit localhost. So to make a symbolic link we type the following into the terminal:

<code>$ ln -s /usr/share/squirrelmail /var/www/mail</code>

You will probably be happy to hear that squirrelmail configurations are done threw a series of menus and not through direct edit of text. It makes things much easier IMO. To run this configuration application we simply type:

<code>$ squirrelmail-configure</code>

The menu looks like this:

<pre>SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Main Menu --
1.  Organization Preferences
2.  Server Settings
3.  Folder Defaults
4.  General Options
5.  Themes
6.  Address Books
7.  Message of the Day (MOTD)
8.  Plugins
9.  Database
10. Languages

D.  Set pre-defined settings for specific IMAP servers

C   Turn color on
S   Save data
Q   Quit

Command >></pre>

The only thing we need to concern ourselves with to make this work is option <b>2. Server Settings</b>. So we type 2 and hit enter and we get the following menu:

<pre>SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Server Settings

General
-------
1.  Domain                 : MYDOMAIN.com
2.  Invert Time            : false
3.  Sendmail or SMTP       : Sendmail

A.  Update IMAP Settings   : localhost:143 (courier)
B.  Change Sendmail Config : /usr/sbin/sendmail

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

Command >> </pre>

You will need to use option one to enter your email's domain. Option 3 has to be changed from SMTP to Sendmail. I have not figured out why it will not work as SMTP since our Exim4 is functioning as a SMTP server. Exim4 does function as a drop-in replacement of sendmail so configuring this for sendmail works just fine.

The next thing we need to worry about is our IMAP settings. Press the "A" key and hit enter. You will then see this menu:

<pre>SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Server Settings

General
-------
1.  Domain                 : MYDOMAIN.com
2.  Invert Time            : false
3.  Sendmail or SMTP       : Sendmail

IMAP Settings
--------------
4.  IMAP Server            : localhost
5.  IMAP Port              : 143
6.  Authentication type    : login
7.  Secure IMAP (TLS)      : true
8.  Server software        : courier
9.  Delimiter              : .

B.  Change Sendmail Config : /usr/sbin/sendmail
H.  Hide IMAP Server Settings

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

Command >></pre>

There are two settings that need to be changed here. The first is Server software. We are using Courier-IMAP so we want to change that setting from it's default to "courier".

The next things is TLS. Change it from it's default falue to "true".

Before we can continue we will need to alter the default php settings. We will do this by editing php.ini in the apache directory. Do the following:

<code>$ gedit /etc/php5/apache2/php.ini</code>
<br>
You are looking for "magic_quotes_gpc" and will be setting is value to off. Like so:

<pre>; Magic quotes for incoming GET/POST/Cookie data.
magic_quotes_gpc = Off</pre>
<br>
<br>


===Testing SquirrelMail Configuration===

We can now test our SquirrelMail configuration. We do this by pointing a web browser at localhost/mail/src/configtest.php. If we are doing this from a remote system then we replace localhost with the ip address of the computer that is hosting the email server. Our page should looks something like this:

<pre>SquirrelMail configtest

This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.

SquirrelMail version:	1.4.13
Config file version:	1.4.0
Config file last modified:	02 May 2008 11:37:38
Checking PHP configuration...
    PHP version 5.2.4-2ubuntu5 OK.
    display_errors: 1
    error_reporting: 6135
    variables_order OK: EGPCS.
    PHP extensions OK.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins OK.
    Themes OK.
    Default language OK.
    Base URL detected as: [http://xxx.xxx.xxx.xxx/mail/src](http://xxx.xxx.xxx.xxx/mail/src) (location base autodetected)
Checking outgoing mail service....
    sendmail OK
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. On some systems you must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
    not using database functionality.

Congratulations, your SquirrelMail setup looks fine to me!</pre>

The main thing we need to be concerned with here is the last line where it tells us that our configuration is OK. 

That is all there is to it. Plugins can be used to modify the functionality of Squirrelmail and can be found on the Squirrelmail website. 

<b>This tutorial is now complete.</b>

---

### Post by theolster on 2008-07-29
flippin heck!

Thanks very much for this, I'll have to go away and spend some time looking at it and I'll post back a result then!

---

### Post by Titan8990 on 2008-07-29
No problem. Probably a lot more stuff in there than you need.

---

### Post by theolster on 2008-07-31
Unfortunately your wiki guide doesn't actually address the issue I'm trying to solve.  From thoroughly reading the whole thing, I can't find which bit applies to me.

Any further ideas would be greatfully recieved.

---


---
title: "Postfix help..."
date: 2008-05-12
forum: Server Platforms
---

### Post by hockey97 on 2008-05-12
aol website refered me to a company that provides a black list of ip address which mine is on a plc or somthing like that which is normal any residential ip address is on that list.

What the company said to do to fix this is to use SMTP-AUTH and if you have it then it must be configured wrong.

Do any of you guy's know how I can config postfix to use SMTP-AUTH correctly???

---

### Post by hyper_ch on 2008-05-12
[www.howtoforge.com](www.howtoforge.com) --> serach for perfect hardy server setup --> in the howto there is also the setup of a smtp server described.

---

### Post by hockey97 on 2008-05-12
well I found a tutorial area which is : [http://flurdy.com/docs/postfix/#conf_auth](http://flurdy.com/docs/postfix/#conf_auth)

I followed everything except for some areas where I got errors.

cd /etc/postfix openssl req -new -outform PEM \ -out postfix.cert -newkey rsa:2048 -nodes -keyout postfix.key -keyform PEM -days 999 -x509

tried that in the terminal to make a postfix key and cert which it failed saying -out unknown option.

and also this: vi /etc/postfix/sasl/smtpd.conf

I got the file made but it wouldn't let me type anything in it giving me errors. So I just went into notebook and created the file and moved it int the sasl location.

those were the only ones that gave me problems.

I am not sure why in the smtpd.conf file I had to put this:

sql_engine: mysql sql_hostnames: 127.0.0.1 sql_user: mail sql_passwd: apasswd sql_database: maildb sql_select: select clear from users where id='%u@%r' and enabled = 1

am I supposed to use mysql and make a table that will have infomation for postfix??

I am not sure why, I don't have postfix config to use mysql I do have the package downloaded and did try doing it but failed.

I am somewhat getting frustrated.


I looked on aol and aol had on there webpage a link to a company that provides them with a blacklist  and I wasn't on the black list but was on a plb list which indicates I am in a residential zone the list provider I went on there website and it explained to me that I just need the smtpd auth
to have my e-mail to get through to aol users ect.

I am trying setup postfix to send e-mail to any e-mail server. I also want to program my own webpage to display my users e-mail and stuff.

I would like to config my postfix to use mysql database, since I have the users list on mysql and the password and would like to make it in a way that I automatily log them in. I require my users to login First before getting into my website and the website has alot of stuff like games chatting ect. I want to make it in a way when they click the e-mail area they wont have to re-enter the username and password unless they are not logged in for any reason I will still check to make sure they are logged in before doing an auto.

So if anyone can help me in any way like if there are good websites taht can teach or help me out any on how to do this.

I know c++, some python, know some javascript, I know php ,css,html  I am not strong in python and javascript .

---

### Post by hortimech on 2008-05-13
Try it like this:

Enter the command to move to the postfix folder,

cd /etc/postfix 

Then enter all the following:

openssl req -new -outform PEM -out postfix.cert -newkey rsa:2048 -nodes -keyout postfix.key -keyform PEM -days 999 -x509

Then it should work.

---

### Post by hockey97 on 2008-05-15
Ok I made the SMTP AUTH to work.

But now when I send an e-mail using telnet I would get an error not from telnet to posfix would send it to the  Mail Queue and my e-mail would be there with a status of: mail transport unavailable.

What would that mean??

do you think I wrote the e-mail in telnet wrong??

or is it the transport mapping?

---

### Post by hockey97 on 2008-05-15
ok so far that is what I found out.

I done this:

  postmap -q domain transport

and this is what I got :

postmap: fatal: open database transport.db: No such file or directory

looks like I don't have transport.db.


I want to setup posfit to grab data from mysql so if I follow a tutorial on how to config that would that take care of this problem??

_________________________________________________-
new additions:

Hi I am now following this tutorial: [http://hostingsoftware.net/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=56](http://hostingsoftware.net/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=56)

I don't understand what needs to be in the database meaning the values, which they don't explain.

---

### Post by hortimech on 2008-05-15
Firstly Postfix doesn't grab the mail from mysql, mysql is the database that stores your users, domains etc.
That howto that you are trying to follow now, may just be the worst I have ever seen, it just about tells you to create a file with the database creation instructions in it, but not how to then use it!

Lets take a step back here, just what are you trying to do? how did you get on the blacklist? do you have a fixed ip address? probably not if you are an AOL customer.

---

### Post by hockey97 on 2008-05-15
lol ya it's confusing save me from these headaches.

Ok let me start over, I will first explain what I want and then slowly go into about that blacklist ect and then to the current issue.


OK I am currently making a website  that is a social website. I want to have these users to also have a e-mail service which I will provide.

What I want to do is have an e-mail server that  I can use php or some web programming lango  to make my own webmail webpage something  like what aol or hotmail has, but make it myself. I know if I can get postfix to use mysql as it's database I would help towards my goal.

What I want in short terms is a secure mail server that I can create my own webpage to make an interface for my users to uses to read/write e-mails.

Now I had the postfix installed and it worked to a extent. I tested my postfix mail server by e-mailing to my aol account which never go there.
I am also using webmin to look at my servers quicker than using the terminal.

So I got a response by the aol mail server that it refused to talk to me and it spit out a id number which had a link following it I clicked it and aol postmaster page came up showing the details it said I was black listed and then gave instructions on how to get whitelisted. well then it had a link to the company that provides aol for a there lists. I done a check on my domain and I found I was not on a black list but was on a lists known to be residential. It said that I must have SMTP AUTH installed and turned on otherwise they would block me due to not meeting the standards.
I found out I had that on but the config wasn't right.

I now have the SMTP AUTH up and config properly and now I am just getting a transport error.

I do have a static ip address. I now just face a transport error. I then using the terminal I done a check on the domain transport and I found that there was no file.

That is where I am at now.

My goal is to  have a secured mail server and have the ability for me to use web programming to make my own  e-mail page for my users.

I know of squirrl mail  but to me it still dosen't allow a professional look.

if you have seen hotmail and aol  you can just tell by there webpage where you can check your e-mails ect that it looks more professional and dosen't look like they are the same.

I need to keep my own theme  within the mail page to make it look as if it was part of my website not like I have a website and just added software to  it.

In otherwords the mail page has to blend within the overall website.

My theme is ice/coldness. I so far have made the website with ice art.

I would look odd if I use squirrl mail for the e-mail services.

I know php so I know how to use mysql to plug in with my scripts.

It's just I don't know how I can interface my webpage with the postfix to display the users e-mail  and also write the e-mail.

I did some modification in the php.ini which when I use the mail() function it would use postfix.

So right now my transport it not working it was before I config postfix to mysql.


I don't even know what values I would need to put in those tables.


Please help I am going crazy about this. I been working on this for a year.

I kept working on and off on this when I was stuck I then started to work on the website and then try later in a month to then try another try.

One time I was suggest to download and install a package from some tutorial and I then found the hard what that package wiped out my partician and I had to start all over from the beginning.

Now I got to this point and I don't feel like screwing the config up that I would have to reintall it or the OS.

Thanks for your time.

---

### Post by hortimech on 2008-05-16
First things, I take it you have your own registered domain, do you have an  MX record and does it point to your server? if not how are you going to receive mail?

---

### Post by hockey97 on 2008-05-16
Yes I have 2 domain names registered. They both have a mx record.

I had postfix working  before I started to config postfix to make it use mysql.

but when I had it working I only could send and recieve mail from small e-mail servers like not aol or hotmail but people that have postfix or using a e-mail server for there small business ect.

I couldn't send mail to aol,hotmail ect when I say can't send mail I mean I can send the mail but it gets rejected by their mail servers with a link attached to the error to a website aol has that descibes why I am blacked.

it told me I was blacklisted but when I click on the link to where they get these lists which is from a company and I done a search I find I am not on a black list but I am still on a list that indicates I didn't have SMTP AUT on which is standard and must have on in order for aol mail servers to accept the e-mail.

I have all the connections and doamin names config correctly. I could send mail out and recieve it but just not from the big wellknown e-mail companies due to the filtering system.

So I then config the smtp auth correctly I had it on before but had the config wrong so now it's right and working I tested it with telnet.

Then I tried to send the e-mail to aol servers as a test and then I now get  an error saying no transport map available.

I then used the postfix command in the terminal to check the domain transport map and showed me that there is no file.

So then I thought maybe this would be a good time to config postfix to use mysql which I tried before but failed.

So now I am trying to config postfix to use mysql. 

The reason is that I want to create an automation where new users using php I can send in new data to mysql and postfix could add those users auto instead of me keep making a db file for postfix to add new users ect.

So do you know how I can config postfix to use mysql for database purpses like users and there passwords ect and the domain name I want there user name to be with the mail domain name. Like :  [email]myuser@mymaildomain.com[/email]

Is there a way to do this?  I would also like to later on add a auto responder also.

But the main point I want to be able to use php or a web programming language to  be able to grab the persons mail and display it on the webbrowser for them and many other ideas I have to use php to make some neat funcitons.

Like if someone e-mails me for like tech support ect I would like to display a number or so to indicate where I am at reading and replying.
so the user can check if I am getting close to replying to there e-mail.

---

### Post by Donb01 on 2008-05-16
AOL will also blacklist you if you do not have reverse DNS set up to reply with the same name as your mail server when they check to see if you are really who you claim to be.

basically verbally it goes like this:  you have some server that is w.x.y.z IP address.  You call it mail.myserver.tld.  You send out an E-mail and it says to AOL "Hi, this is mail.myserver.tld, I have mail for you"  The AOL server goes out to God and says "Who is mail.myserver.tld" and if it does not get back w.x.y.z it says you're a liar and refuses to send your mail.

As far as I understand it, the transport mapping in postfix is optional if you have your main.cf file properly configured.  Mine is located under /etc/postfix.  There should be a "MyDestination" entry in there that lists all the things your machine could possibly go by.  At the very least the hostname of your mail server needs to be properly defined in there, but I would put mail.myserver.tld or whatever else your machine goes by on that list too.  You also need to have a "MyNetworks" entry that shows all the IP addresses that are allowed to send mail and to be considered to be connected to your network, and a "mailbox_command" entry that says how your system is supposed to deliver mail.  I assume you installed procmail along with postfix?

There are sample main.cf files in /etc/postfix (or wherever yours is hiding) that should help you configure it right.

The "transport" file (which gets converted into "transport.db" is only there to override the settings in main.cf as far as I understand it.

---

### Post by hortimech on 2008-05-16
You might want to take a look at Postfixadmin, there is an howto at [http://codepoets.co.uk/postfixadmin-postgresql-courier-squirrelmail-debian-etch-howto-tutorial](http://codepoets.co.uk/postfixadmin-postgresql-courier-squirrelmail-debian-etch-howto-tutorial)

I know this is for Debian, but will work on Ubuntu and just use mysql instead of postgresql.

Download Postfixadmin from [http://sourceforge.net/project/showfiles.php?group_id=191583&package_id=225300](http://sourceforge.net/project/showfiles.php?group_id=191583&package_id=225300)

DO NOT GET the .deb file, get the tar file instead. If you need any further help, just ask, I run this to collect all my various emails onto my homeserver.

---

### Post by hockey97 on 2008-05-16
ok I used an online tool and found it  it reverses to my ISP is that good??


Right now my mail servers config got screwed up after I followed that tutorial which now I can't get any response from the mail server using telnet.

I am going to take look at the links you guys provided.

Thanks.

---

### Post by hockey97 on 2008-05-16
OK  I got the server to work again.

But my reverse looup shows my isp domain name.

Would this be the reason I can't send mail to aol users??

---

### Post by hockey97 on 2008-05-17
I am still getting the  mail transport unavailable error.

here is a log of postfix when I tried sending an e-mail:
```
May 17 17:15:54 host postfix/trivial-rewrite[10038]: warning: database /etc/postfix/mysql_virtual_alias_maps.cf.db is older than source file /etc/postfix/mysql_virtual_alias_maps.cf
May 17 17:15:54 host postfix/qmgr[8497]: warning: connect to transport smtp: Connection refused
May 17 17:15:54 host postfix/error[10024]: C764918406D: to=<me@aol.com>, relay=none, delay=9565, delays=9563/1.5/0/0.16, dsn=4.3.0, status=deferred (mail transport unavailable)
```

---

### Post by hortimech on 2008-05-18
Can you post a copy of /etc/postfix/main.cf ( just change any private hostnames & domain names)
where did /etc/postfix/mysql_virtual_alias_maps.cf.db come from? My mailserver (Postfix, Courier, Mysql, Postfixadmin etc) works and I do not have that file.

---

### Post by hockey97 on 2008-05-18
well I tried to config postfix to use mysql that file is the file that has the mysql commands to do a lookup in the mysql database.

I will post the file.  Just want to also say that my reverse dns lookup shows my isp domain ect not mine, could this also cause aol to block me..?

here is what is in that file you request:```
 Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = mydomain.com ESMTP mail.mydomain.com (os)
biff = yes

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file =/etc/postfix/postfix.cert
smtpd_tls_key_file =/etc/postfix/postfix.key 
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_data_restrictions = reject_unauth_pipelining
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = myhost
myorigin = mail.mydomain.com
mydestination = mail.mydomain.com
mynetworks = 127.0.0.0/8,internal ip,external ip
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
#transport_maps =  hash:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_alias_maps      = hash:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_uid_maps        = static:1001
virtual_gid_maps        = static:1001
virtual_mailbox_base    = /home/user/WebPage/mail
virtual_mailbox_domains = hash:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_limit   = 51200000
virtual_mailbox_maps    = hash:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid     = 1001
virtual_transport = virtual
daemon_timeout = 1800s
max_idle = 1800s
trigger_timeout = 1800s
ipc_timeout = 1800s
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = mydomain.com
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2 smtpd_sasl_security_options = noanonymous 
#smtpd_sasl_local_domain=
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtp_skip_quit_response = no
fallback_relay = 
```

---

### Post by hortimech on 2008-05-18
You are not using Mysql!

this is a line from my main.cf

virtual_alias_maps = mysql:/etc/postfix/virtual-alias-maps.cf

Notice the difference?

you need to create the Mysql database and alter your main.cf to be similar to the one below. 

[MAIN.CF]
myhostname = server.domain.tld
mydestination = $myhostname, localhost, localhost.localdomain
smtp_sasl_security_options =
mynetworks = 127.0.0.0/8
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/virtual-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/virtual-mailbox-maps.cf
relay_domains = mysql:/etc/postfix/relay-domains.cf
virtual_mailbox_base = /var/mail/vmail
virtual_uid_maps = static:1001
virtual_gid_maps = static:1001
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated,  reject_unauth_destination
smtpd_use_tls=yes
smtpd_tls_cert_file = /etc/postfix/tls/certs/mail-cert.pem
smtpd_tls_key_file = /etc/postfix/tls/private/mail-key.pem
inet_interfaces = all

local_transport = virtual
local_recipient_maps = $virtual_mailbox_maps
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 1001
virtual_transport = virtual

As I said Mysql holds the user details, domain details etc, you seem to be trying to use a Berkeley database?

I would suggest you start again, follow the howto I recommended and lets take it from there.

---

### Post by hockey97 on 2008-05-19
ok I can setup postfix to use mysql with webmin.

I just need to know what tables to make and what values they must hold.

Then everything will be taken care of by webmin.


Also I just done a e-mail test to aol and I got this:  

host mailin-02.mx.aol.com[205.188.249.91] refused to talk to me: 554- (RTR:SC) [http://postmaster.info.aol.com/errors/554rtrsc.html](http://postmaster.info.aol.com/errors/554rtrsc.html) 554 Connecting IP: myexternal ip.

---

### Post by hockey97 on 2008-05-19
HI I just found somthing that might be the reason why I get refused...


on that same page with the error where it takes me to a page of aol.

there is a section on mail standards ect.

in the mail standards it has this:

AOL's mail servers will not accept connections from systems that use dynamically assigned or residential IP addresses.

I think mine has a residential ip address but I am not sure.

if this is true does it mean I have to contact my ISP?? or can I add a ptr record in bind 9 or the people that are hosting my domain name.

---

### Post by hockey97 on 2008-05-19
ok I got my ip address off the residental database.

but what I have now is I can't smtp auth I get faild even though the username and password I provided in telnet using the mimencode which those are the right ones.

I checked the mail log.

and this is what I am getting:

```
May 19 21:49:56 MyHost postfix/smtpd[6258]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: Permission denied
```

That is what I am getting so then I started to play around with the permissions making the file to get chmod to 666 then to 555 then where it's now to 444.

any idea what is wrong??

---

### Post by hortimech on 2008-05-20
I would suggest you go and RTFM, you would seem to be mixing up smtp and smtpd. I relay all my mail through my ISP, so I need the smtp_sasl_password_map, you don't, as far as I know.

You have,
a) a fixed ip
b) a DNS record pointing to your server
c) a MX record in your DNS record pointing to your mail server

If you do have all of the above, you should be able to send email out onto the internet and more importantly, be able to receive it.

What you might need are server certificates

[main.cf]

smtpd_use_tls=yes
smtpd_tls_cert_file = /etc/postfix/tls/certs/mail-cert.pem
smtpd_tls_key_file = /etc/postfix/tls/private/mail-key.pem


As for the virtual*.cf files you require in /etc/postfix, please go and see the howto I suggested, they are there, and I might point out, in many other howto's on the internet

---

### Post by hockey97 on 2008-05-20
Yes I got a fixed ip and the a records and I have a mx record.

The problem I have is how to make the mysql tables.I havent found a tutorial that would explain the values needed in database.

I have those certficate and keys  but they are like"

smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key

but in the log it dosen't spit any errors out concerning the key and cert files.

It is right now just spitting out mail transport errors.

Which I am guessing that the mysql stuff is not config properly.

I have the .cf files all right it's just the tables I don't know what values it needs and where to put those values.

---

### Post by hockey97 on 2008-05-20
I looked and tried the webiste you suggested and followed it.

it only tells about making the config files there is nothing about making the tables or setting up mysql with postfix.

My config files was the same as what they gave. I just went over it again to make sure it's the same thing which it turned out to be.

but when I changed the hash to mysql for those config files I then now get a new error saying unknown error. This also another error that's new which shows in the log file is:

      ```
private/smtp socket: malformed response
```

---

### Post by hortimech on 2008-05-21
Right, I take it you now have the following files in /etc/postfix/ and 
have edited the password in them.

virtual-alias-maps.cf
virtual-domains.cf
virtual-mailbox-maps.cf
relay-domains.cf

You now need to download postfixadmin, untar it into /var/www/
cd into /var/www/postfixadmin (may have the version number added, if so, just rename it to postfixadmin) and read the INSTALL.TXT file. Follow the instructions, change the password in config.inc.php to the password you used for the mysql root user and edit the file to suit your server.
To create the database user in mysql, open a terminal and enter 'mysql -u root -p' press return and then enter your mysql root password; enter the following, line by line

CREATE DATABASE postfix;

CREATE USER 'postfix'@'localhost' IDENTIFIED BY 'the_password_you_put_in_the_.cf_files';

GRANT ALL PRIVILEGES ON postfix.* TO 'postfix'@'localhost';

exit;

pressing the enter key after every line

restart apache2, browse to <your server address>/postfixadmin and this should check your setup, just fix any problems it finds (if any) and follow the instructions. You should now have the required database.
When you get this far, give me another call (or if you get stuck)

---

### Post by hockey97 on 2008-05-21
UPDATE: Ok I got the  postfix admin to work and it looks like verything is working but still It didn't fix the postfix problem I had which it still can't find the transport map.

It spits out a error on the SMTP socket.

---

### Post by hockey97 on 2008-05-22
Ok so now what??  I got postfixadmin working and I checked my mysql database with postfixadmin and looks like it's done right.

I am still getting errors with postfix it's keeps spitting out unknown transport map. 

So what should I do now?

---

### Post by hortimech on 2008-05-22
you should not need transport maps, they are used for relaying mail, either through your isp if you cannot send/receive mail directly or if you are a backup mailserver.

go here,
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)

start from section six, but first
 
apt-get install postfix postfix-mysql postfix-doc mysql-client mysql-server courier-authdaemon courier-authlib-mysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl postfix-tls libsasl2-2 libsasl2-modules libsasl2-modules-sql sasl2-bin libpam-mysql openssl phpmyadmin apache2 libapache2-mod-php5 php5 php5-mysql libpam-smbpass
This , with postfixadmin should give you a working mailserver, postfixadmin will make it easier to create users, domains etc.

---

### Post by hockey97 on 2008-05-22
I got it to work no except I still get aol refused to talk to me errors.

I then tried hotmail I didn't get any error or anything but yet it didn't get to my hotmail account.

what would you need when you send e-mail through telnet?

to what I know I done this:

I telnet mymail server port 25 
then HELO mymailserver
then EHLO blah
then auth login
it then succeeds
then DATA
then MAIL FROM:myuseratmymailserver
it gives me an ok
then RCPT TO: myaol/orhotmail address
it gives me an ok
then Subject: whateverthesubjectis
then Message:This will be the overall e-mail message.
I don't know if I need to use the Message:  or I just type in here without it.

then I end the message/e-mail with a .
it then it said it is sent to postfix waiting area.
then I type in quit  .

is this right??

or do I need to add somthing special??

aol still refused to talk to my server. I don't know about hotmail I tried it and I didn't get any error and I didn't even get the e-mail on the other end.

---

### Post by hockey97 on 2008-05-24
oh and I used <> around the e-mail addreses.

my postfix server is all config right.

it just looks like aol and major companies are blocking my ip becuse my ip is a residential one.

Is there any way around this??

Aol is a pain in the you know where.  I have an aol accounting and I get 81 spam a day most of them keep asking if I want pills to increase a thing ect.. so I am now like boiled that they block me which I don't plan on spamming them  and yet they allow companies that spam their stuff all over.

So I hope someone knows how to get around this.

I think my ip is dynamic not static.

---

### Post by MJN on 2008-05-25
> **hockey97 said:**
> it just looks like aol and major companies are blocking my ip becuse my ip is a residential one.

Is there any way around this??

If by residential you mean it is dynamic as opposed to static then no, there is no way of getting AOL to accept connections from you.

Your only option is to relay all outgoing mail via a 3rd party e.g. your ISP's mail server. Use the **relayhost = [mail server]** directive for this.

Mathew

---

### Post by hockey97 on 2008-05-25
Is there a way I can get a static ip address?

lol thanks for the info I now know what's the problem and I hope aol loses their shirt becuse I have a account with them to use their e-mai services and I get about 81 e-mails that are spam a day.

I think I can only send e-mails to hotmail,yahoo but not aol.

Well Since my config is all right and I can send e-mails to not well-known mails servers then I guess I will use that and just explain to my users why they can't send e-mails to aol users ect.

---

### Post by MJN on 2008-05-25
> **hockey97 said:**
> Is there a way I can get a static ip address?

Just ask your ISP. Some offer it for free, many for a fee, but most not at all.

> Well Since my config is all right and I can send e-mails to not well-known mails servers then I guess I will use that and just explain to my users why they can't send e-mails to aol users ect.

It's not a case of how well-known the servers - many servers already forbid connections from known-dynamic address blocks (mine included) and many more are following suit so whether you agree with it or not you will likely find you end up with a bunch of rightfully-unhappy users on your hands.

Mathew

---

### Post by hockey97 on 2008-05-25
Well  here is the website that hotmail claims they use for their spam/block list.

[Click Here to go to the site.]("http://www.spamhaus.org/pbl/")


That website is the only one that had my ip block well on there list becuse mine was a residential ip address.

Aol reqires you to have a reverse lookup  it dosen't have to show the same domain name at least there is a reverse lookup.

I am just stumped. Hotmail dosen't give me any errors or anything but when I check my hotmail account to see if my test e-mail got through I find out it's not there.

---

### Post by MJN on 2008-05-26
> **hockey97 said:**
> I am just stumped. Hotmail dosen't give me any errors or anything but when I check my hotmail account to see if my test e-mail got through I find out it's not there.

Suspected spam doesn't always generate a bounce, indeed with a carrier the size of Hotmail they'd probably prefer to just drop it. This is particularly true when the anti-spam measures are applied post-SMTP as chances are the From: addresses are spoofed anyway and so bouncing to the innocent true sender is undesirable (it is known as 'backscatter' and is arguably as big a pain, if not more so, than the spam itself).

Mathew

---

### Post by hockey97 on 2008-05-26
Thanks it makes sense. I might e-mail hotmail to see if I can get around this in anyway becuse I don't plan on spamming anyone.
I am really against spam.
I plan to use my mail server to provide e-mail service for users and also make an auto e-mail generation to people that register to send a code and have them type it on my webpage to make sure they submitted the right e-mail address.

Thanks for all the help.

---

### Post by MJN on 2008-05-26
> **hockey97 said:**
> Thanks it makes sense. I might e-mail hotmail to see if I can get around this in anyway becuse I don't plan on spamming anyone.
I am really against spam.

You stand absolutely no chance. Trust me.

> I plan to use my mail server to provide e-mail service for users and also make an auto e-mail generation to people that register to send a code and have them type it on my webpage to make sure they submitted the right e-mail address.

Is there any reason you cannot relay via your ISP? This doesn't stop you running your own mail server, it just means all outgoing mail is sent via them.

Mathew

---

### Post by hockey97 on 2008-05-27
I don't know if I could relay via my isp.  How would I config postfix to do so???

and if I do it that way would it still show my mail server domain ect when it gets to a aol user??

---

### Post by MJN on 2008-05-27
They probably misunderstood your question and thought you wanted them to relay incoming mail. You need to just point Postfix at their outgoing mail server, just as you would do if using a single e-mail client.

Of course perhaps they don't provide any mail service, I'm not familiar with ISPs outside the UK and the services they offer. What's the ISP?

Mathew

---

### Post by hockey97 on 2008-05-27
it's wideopenwest(known as wow) 

How would I know their outgoing mailserver?? should I call them again??

if I do it that way would I still have my own domain with user on the address??

like [email]user@mydomain.com[/email]  ect??? I know for a fact they have a mail server I do have an account with them to use their mail service.

---

### Post by MJN on 2008-05-28
They will have likely told you what the mail server is, in order for you to use a standard e-mail client.

They will usually allow all outgoing mail through untouched, although I have seen at least one which rewrites the From: addresses but thankfully this is rare.

You may need to turn authentication on, although some will authenticate against your IP address.

Mathew

---

### Post by hockey97 on 2008-05-28
ok I will give them a call when I get time too. They didn't tell me anything about there mail servers.  I have the smtp auth setup right and it's on. I have no problem with my mail server config since I tested it with many online tools and also telnet. So the config it ok just needed to get around the aol blockers ect.

---

### Post by hockey97 on 2008-05-28
Hi I send an e-mail to my isp  wow  and this is what they gave me:

```
Thank you for contacting WOW! Internet, Cable and Phone,
 
WOW! will not allow you to pass email from your own person email server thru the WOW! servers.  If your server is connected using the WOW! service, I would suggest reading the Terms of service located here http://www1.wowway.com/wow/wow.aspx?ConIdent=28&RCView=False&TermID=2.  Specifically, section Q references the use of servers on the WOW! network
```

Is there any way where I can own my own network/line??

I might switch my ISP. They don't allow any servers to be runned on their network ect. They have very strict rules.

I rather own a network line   somthing small enought that's cheap  but not slow something like dsl.

---

### Post by MJN on 2008-05-29
If by 'network line' you mean a leased line i.e. a dedicated pipe with no contention just for your use then sure - many providers offer them. However they do cost, and compared to a standard ISP service they are significantly more expensive.
 
Besides which a leased line sounds unnecessary for what you are trying to achieve, just go for another ISP which either provides static IP addresses (many do) or allows relaying via their mail server (most do, but of course you happen to be with one that doesn't).
 
The bottom line is you want to run services, and your current ISP doesn't allow that, so it's time to move on. There are plenty of other ISPs who will be only to happy to take your cash and give you the services you require in return.
 
Mathew

---

### Post by hockey97 on 2008-05-29
well I found a wholseller that would help me get started on being an ISP. The cost is 200 bucks a year and I have to sign a contract for a year  and it would cost 35 bucks per dsl modem.

Is dsl any good? I have broad-band currently.

Well I am now looking for another provider.

---

### Post by MJN on 2008-05-29
DSL is a form of broadband.

If you're now wanting to become an ISP this is beyond the scope of this thread.

Mathew

---

### Post by hockey97 on 2008-05-29
no I don't really want to be an ISP becuse you would still need a crew to help setup the stuff for the users. 

I been searching around for a good deal and haven't found anything. 

The only thing that is cheap is that dsl but in the contract it reqires you to sell there stuff. 200 bucks a year is basicly like 16 and some cents a month which is way cheaper than what we are paying so far for the current isp we have we pay 60 bucks for a broad-band with 8mb download rate.

Well I think my problem is solved I guess just have to find a ISP that will allow me to do what I want to do ect.

---

### Post by hortimech on 2008-05-31
Well I go away for a few days and come back to find that the question I asked you at the start had been answered incorrectly, you have a dynamic ip!!
What you could try to do is find an ISP that will give you a FIXED ip or will set up a multidrop mailbox for you. With the later you would relay mail out through their mailserver and collect the mail with Fetchmail.
I also believe that there are available places that will make your dynamic ip findable by dns, try searching with google

---


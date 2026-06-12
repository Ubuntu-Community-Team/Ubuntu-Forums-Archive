---
title: "mail servers"
date: 2009-06-24
forum: Server Platforms
---

### Post by johnh10000 on 2009-06-24
I tried axigen-7.1.3-1, but it either doesn't work or is very slow on my box. :(

So does anyone know of something similar?

does lamp have a mail server configuration in it?

What I want to do is get mu gmails, put them in mail boxes on tux.isa-geek.org

send mails

and beable to use pop3 get to my mailboxes ..

---

### Post by LepeKaname on 2009-06-24
> So does anyone know of something similar?
Postfix+Dovecot (its my recommendation)

> does lamp have a mail server configuration in it?
LAMP it is not a mail server. It comes with basic functions to send mails from within your codes (from a localhost mail server). But in order to make it work, you need to have a mail server running. 

> What I want to do is get mu gmails, put them in mail boxes on tux.isa-geek.org send mails and beable to use pop3 get to my mailboxes .. 

I think what you are looking for is a PHP class like [phpmailer]("http://phpmailer.codeworxtech.com/index.php?pg=examples") that you can setup to send mails from your gmail account and retrieve them using POP3 inside your codes.
You can download your gmail emails and then send them to your isa-geek.org server.

---

### Post by HermanAB on 2009-06-25
The absolutely easiest mail system to set up is Citadel.  The Easy Install script takes about 20 minutes.  However, you need to set up the DNS first if you want your mail server to work.  You need a static IP address with a FQDN, A, MX and PTR records to run a mail server.

Go to [www.citadel.org](www.citadel.org) for details.

---

### Post by johnh10000 on 2009-06-25
> **HermanAB said:**
> The absolutely easiest mail system to set up is Citadel.  The Easy Install script takes about 20 minutes. 


I like easy.

 However, you need to set up the DNS first if you want your mail server to 

Would dnsmasq work?

work.  You need a static IP address with a FQDN, A, MX and PTR records to run a mail server.

I have a static-ish IP I always get the same IP from virgin, and the router always give me the same dhcp IP

On dynadns I have setup a MX record for tux.

Whats this PTR

---

### Post by HermanAB on 2009-06-25
You can make a mail server work on a LAN to for example handle local Bugzilla and Subversion messages for software development purposes, but to exchange email with the rest of the world, you need to get by their SPAM filters.  The only way to do that, is to pay your ISP for a real static IP address on a server account and register a domain name and configure the DNS properly.  Otherwise, all your messages will end up in SPAM traps.

---

### Post by johnh10000 on 2009-06-25
> **HermanAB said:**
> You can make a mail server work on a LAN to for example handle local Bugzilla and Subversion messages for software development purposes, but to exchange email with the rest of the world, you need to get by their SPAM filters.  The only way to do that, is to pay your ISP for a real static IP address on a server account and register a domain name and configure the DNS properly.  Otherwise, all your messages will end up in SPAM traps.

Ok,

I wonder, I seem to recall way back when in my slackware days, I could grab mail from say gamil, then use say gmail's smtp servers....

---

### Post by windependence on 2009-06-25
> **johnh10000 said:**
> Ok,

I wonder, I seem to recall way back when in my slackware days, I could grab mail from say gamil, then use say gmail's smtp servers....

What's the point in having your own mail server if you do that?

The PTR record is just reverse DNS. Today, if you don't have a PTR, most mailservers won't talk to your mailserver.

-Tim

---

### Post by LepeKaname on 2009-06-25
> The absolutely easiest mail system to set up is Citadel.

Sorry HermanAB, I have to disagree... I tried to install Citadel once and I loose like 2 hours and I couldn't make it work (I followed a tutorial). Maybe I was doing something wrong or just Citadel has many other things I don't really needed. 

I made a script to install Postfix+Dovecot+ClamAV+SpammAssassin (with SSL and SASL) to support a kind of virtual directories (without using MySQL). I have been able to have a running mail server in less than 3 minutes (most of that time is what it takes to download the required packages). 

I have had install it in around 6 server by now and at least for me, I have found no problem. Of course it is not heavily maintained, but its a very good starting point for anyone with little or none experience with that. 

I have been sharing it (for free of course) at my personal blog: [http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Many things still need to be added to the documentation, but the "--help" argument of those scripts may explain the rest.

You can try it on a virtual server and I will be glad to hear your comments.

---

### Post by windependence on 2009-06-25
Everyone seems to have their favorite. It's well known that hermann is the Citadel expert and I prefer Zimbra, so I guess it's whatever works.  The point is to give n00bs as many choices as you can without being an evangelist. I fall into that trap myself at times. ;-)

-Tim

---

### Post by LepeKaname on 2009-06-25
> Everyone seems to have their favorite.

Yes you are right... Usually when something works for me I stick to it. I found Citadel interesting but its too much for what I need... I haven't try Zimbra, I may give it a try. 

Have fun.

---

### Post by yotis on 2009-06-25
> **LepeKaname said:**
> 

I made a script to install Postfix+Dovecot+ClamAV+SpammAssassin (with SSL and SASL) to support a kind of virtual directories (without using MySQL). I have been able to have a running mail server in less than 3 minutes (most of that time is what it takes to download the required packages). 

I have had install it in around 6 server by now and at least for me, I have found no problem. Of course it is not heavily maintained, but its a very good starting point for anyone with little or none experience with that. 

I have been sharing it (for free of course) at my personal blog: [http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Many things still need to be added to the documentation, but the "--help" argument of those scripts may explain the rest.

You can try it on a virtual server and I will be glad to hear your comments.

Hi there!

I had a look into your post and seems ok, I will give it a try. Mainly I need something to migrate from Slackware + Qmail (installed after qmailrock.org tutorial + vpopmail support) to Ubuntu + "Mail Server". The reason why I want to migrate is that Slackware and Qmail does not support to much "automated" task and for each and every upgrade that I have to do, I spend hours to get it work due to the different patches and versions. 

I will let you know how it's working!

---

### Post by LepeKaname on 2009-06-25
> I will let you know how it's working!

Yes please... also if there is something that is not easy to understand (because English is not my native language), please let me know. I would like to improve it.

---

### Post by kustomjs on 2009-06-26
I got a working email server with postfix+dovecot+mysql+spamassassin+maia mailguard+webmin+lamp.

if you want to know more how I got this setup send me a PM.

---

### Post by cariboo on 2009-06-26
@kustomjs

Instead of answering pm's, why not let us all benefit from your knowledge?

---

### Post by Mack1 on 2009-06-26
Hi all,

I have also been trying to get a mailserver running on ubuntu server.

At the moment after reading through 100+ how-to's i have been able to install and use a combination of fetchmail, postfix and dovecot.

All it want is have:
2 pop3 yahoo email accounts to fetch and distribute their contents through imap to different windows/linux clients.

This finally works, although only 1 pop3 yahoo account gets read (fetchmail DOES say it reads both of them when i run it manually).

I'm getting grey hair overhere, especially when everyone says it's only 5 mins work....and i am hardly a computer noob, also been using ubuntu for 3 years now.

I will take a look at the how-to for dovecot+postfix thats posted here, hopefully that works out for me.

About citadel: same experience, i get it running in like 3 or 4 minutes but configure it to fetch pop3 yahoo accounts and redistrubute them via imap....i do not understand....i am at a total loss. No idea how to configure it to do just that.

The mailserver has to send smtp to yahoo, so no domain of my own is used.

If someone could help me out and get me a running mailserver...i would sell my mother to him/her :-)

---

### Post by HermanAB on 2009-06-26
Honestly, getting a Postfix Lego Block system to work the first time, would likely consume at least 100 hours of your time.

In contrast, installing Citadel or Zimbra takes less than an hour.

I have had Citadel running on my Eee PC 701, so it is very efficient.  The main advantage of Citadel or Zimbra is that all data is stored in a database, so if HR sends a message to 25000 employees, the system only stores one copy of the message.  With a Postfix system, you have to run out and buy more hard disks to save 25000 copies of the same MS Word attachment that no-one will read...

---

### Post by kustomjs on 2009-06-26
to HermanAB I got postfix running about 10mins instead of 100 hours as your saying it took me to do. and I got my whole email server running within a half hour installing all the stuff.

I had more problems with Citadel getting installed and running then what I did with postfix.

---

### Post by windependence on 2009-06-26
> **kustomjs said:**
> to HermanAB I got postfix running about 10mins instead of 100 hours as your saying it took me to do. and I got my whole email server running within a half hour installing all the stuff.

I had more problems with Citadel getting installed and running then what I did with postfix.

You either got lucky or you're a genius. :-)

-Tim

---

### Post by johnh10000 on 2009-06-26
> **LepeKaname said:**
> ....
I made a script to install Postfix+Dovecot+ClamAV+SpammAssassin (with SSL and SASL) to support a kind of virtual directories (without using MySQL). 

I have been sharing it (for free of course) at my personal blog: [http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Many things still need to be added to the documentation, but the "--help" argument of those scripts may explain the rest.

You can try it on a virtual server and I will be glad to hear your comments.

Thank you sir.  I am tired tonight, but very very useful.  I found dnsmasq worked for me too.  In your tutorial you show me how to include my router. Yum if you pardon the pun ;)

tux.isa-geek.org

---

### Post by HermanAB on 2009-06-26
You can use Citadel to fetch mail from another service.  This is a personal feature - not site wide - therefore it is configured in the Advanced settings of the Mail account of the relevant user.

Log into Webcit, Click Mail, then click Advanced, as described in the Citadel FAQ:

In WebCit, imply navigate to the room into which you wish to fetch messages (usually your “Mail” room, i.e. your inbox) and select Advanced –> Edit or delete this room –> Remote retrieval, and then enter the hostname of your remote POP3 mail server, along with the username and password of your account there.

You will also notice that you can elect to keep messages on the remote server or delete them.

There is also an option to set the “interval” between collections. This setting is in seconds. If left at zero POP3 collection will occur at the system default interval. If set to a non zero value then POP3 collection for this room will occur at the configured interval. Note, however, that the system administrator can configure a low limit for this interval, if you configure an interval lower than the configured limit then this room will collect POP3 mail only at the interval limit set by the system administrator.

---

### Post by windependence on 2009-06-27
I never understand why people want to do this. Just put the information in your mail client and fetch the mail from the real server. Why relay it? If you want to make it look like it comes from your domain but use someone else's mail server, then there are other, more simple ways of redirecting mail. I just don't get why anyone would go to the trouble of setting up a mail server just to relay mail from another account. If it's your domain, set it up to receive and send mail from YOUR domain and be done with it.

-Tim

---

### Post by johnh10000 on 2009-06-27
> **kustomjs said:**
>   email server running within a half hour installing all the stuff.

I had more problems with Citadel getting installed and running then what I did with postfix.

The latter, yeah!
The former HOW?!!!!!!

---

### Post by johnh10000 on 2009-06-27
> **windependence said:**
>  I just don't get why anyone would go to the trouble of setting up a mail server just to relay mail from another account. If it's your domain, set it up to receive and send mail from YOUR domain and be done with it.

-Tim

I'm getting close.  But the satisfaction, of getting it to work.  I'll be balld soon !! ;;))

tux.isa-geek.org

---

### Post by LepeKaname on 2009-06-27
I updated my script 2 days ago...still no time to comment it in my blog... But I added a fully clean uninstall, IP auto detection, firewall settings between other things.... Its good to know it has been useful to some people.

---

### Post by johnh10000 on 2009-06-28
> **windependence said:**
> I never understand why people want to do this. Just put the information in your mail client and fetch the mail from the real server. Why relay it? If you want to make it look like it comes from your domain but use someone else's mail server, then there are other, more simple ways of redirecting mail. I just don't get why anyone would go to the trouble of setting up a mail server just to relay mail from another account. If it's your domain, set it up to receive and send mail from YOUR domain and be done with it.

-Tim

Ok ok I give in with all this.  I descovered last night dragons knight game, needs a working email (well smtp anyhow) to send you your account login. so....

How the heck do set up using my local mail boxes to send via say gmail and recive through gmail?

Know any tutorial about doing this?

:confused:

---

### Post by kustomjs on 2009-06-28
I told you to PM me about it I am not going to post anything how I got mine setup:

there is a good how to: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")


> **johnh10000 said:**
> The latter, yeah!
The former HOW?!!!!!!

---

### Post by LepeKaname on 2009-06-28
> **johnh10000 said:**
> 
How the heck do set up using my local mail boxes to send via say gmail and recive through gmail?
:confused:

You can use phpmailer to send/receive mails through your gmail account within any php code. If you just want to do it manually, then just setup your thunderbird/evolution/etc email client to do so.

---

### Post by hoen on 2009-07-30
> **LepeKaname said:**
> I made a script to install Postfix+Dovecot+ClamAV+SpammAssassin (with SSL and SASL) to support a kind of virtual directories (without using MySQL). I have been able to have a running mail server in less than 3 minutes (most of that time is what it takes to download the required packages).

Looks like a really cool script there...

BUT of course it doesn't work on my system (Ubuntu Jaunty), and now my website stopped working, I can't connect through ssh anymore (had to connect a screen and a keyboard), and best of all... I had no idea how to reset everything.

Can you tell me what your script could have done to make my website stop working so I can fix it?

I've spent hundreds of hours trying to install a mail server... The 4223457441 tutorials I tried don't work (I get errors I don't understand and can't find answers to), I'm unable to install citadel and now I'm back where I was before installing Ubuntu: without any website. :confused:

It almost makes me want to say the F-word out loud. ;)

But thanks for sharing the script anyway LepeKaname, these words of frustration are not for you. I'm sure the script works just fine with you and everyone else. I just wish to be able to get something to work on my own system without breaking anything else...

Can you pleee-hee-heease (almost litteraly crying) help me?

Two of my websites are now down and it won't be long before people will start complaining to me... And I don't know the solution!

The script says:

"To uninstall type: ./InstallMailServer.sh --uninstall"

But that doesn't work. I've checked virtualhosts and the domain name, I've checked the tutorial, but I'm stuck and would very very much appreciate help to fix it. I'll forget about trying to install a mail server, if my websites would just work again.

Thanks!

EDIT: Got the uninstall to work, no progress; still no websites. This is so depressing.

---

### Post by LepeKaname on 2009-07-30
Hi hoen, I just sent you a PM:

> 
The uninstallation procedure removes this packages:

postfix dovecot-pop3d dovecot-imapd clamav-daemon clamav spamassassin amavisd-new sasl2-bin libnet-dns-perl libmail-spf-query-perl pyzor razor ripole nomarch pax unzoo zoo clamav-freshclam libclamav5 clamav-base dovecot-common

Try to install again:

sudo aptitude install libnet-dns-perl

Its the only one I can think it may be related. If so, please confirm so I will fix the uninstallation script.

Thank you, I will wait your answers.

If is a ssh problem, then I think maybe "sasl2-bin" however, as far as I know, that package is not require to connect through ssh.

I'm wondering if you installed it in a "clean" installation of Jaunty. I have installed/uninstalled in Jaunty without problems. 

One important note: If you had "/home/users" previously to the installation, the uninstallation procedure will remove that directory! So, I will fix my script so you can change that location. 

I'm sorry it caused you a problem. Usually I suggest to try it first in a virtual environment, and then in the production server. I need to update my blog. I hope this weekend I have some time.

---

### Post by LepeKaname on 2009-07-30
I just updated the script:

This is a summary from the latests changes:

```
# Jul 31 2009:  Added custom USERS_DIR (before was fixed to /home/users)
#               Extended help messages (start and end)
#               Added support for alternative port 587
#               /etc/aliases modification
#               Uninstall firewall settings
#               Fixed clamav new packages
#               Firewall added port 110, 143, 587, 993, 995
#               Added libmail-spf-perl to uninstall package list
# Jul 16 2009:  Autodetection of External/Internal IP
#               Fixed clamav new packages
#               Uninstallation script
#               Using ManageDomains and ManageUsers scripts instead of inline code
#               Enabled Firewall setup
#               Internet/Intranet option added
#               Group dependency was changed
```

I tested it in 2 jaunty servers (one clean an one unclean) install and uninstall updated today to the latests packages versions. I only find a problem related to the clamav startup script (which I already fixed), but nothing related with SSH. 

I need to test them in Hardy and Intrepid, but I will do that later.

It is possible it didn't work for you because I missed to open some firewall ports in my previous version. I added extra help during the installation so I hope it can be easy to diagnose and fix setup problems.

The new script is available at my blog: [URL="http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html"]Setting up a Mail Server in Ubuntu
[/URL]

---


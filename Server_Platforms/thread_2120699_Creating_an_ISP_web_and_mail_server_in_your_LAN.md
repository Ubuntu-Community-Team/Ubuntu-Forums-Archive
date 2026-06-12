---
title: "Creating an ISP web and mail server in your LAN"
date: 2013-02-27
forum: Server Platforms
---

### Post by SAngeli on 2013-02-27
Hello,
at home I have in my LAN a Windows PC and a server I wish to use with ubuntu server. I have Internet connection (ADSL) provided by my Telco. I have few Static IPs but I use only one for my LAN; at present time I do not wish to use a static IP for my SMTP or web. I will ask and wish to learn after I practiced locally, first.

I wish to learn what do I need (and howto) in order to create a new server that would be similar to what I would get from any ISP when I choose to get VPS server for my webhosting site.

The reason for this is to learn how to setup, in the future, a proper VPS server and also to be able to locally practice how to develop websites with CMS, static sites and so on.

These are the services I am interested in:
- Web (LAMP) + MyphpAdmin;
- Mail (with spam, virus check, webmail);
- FTP service;
- Mail notification if something goes wrong on the system
- If possible a nice web interface that would help me manage the entire server (something like cpanel or DirectAdmin or whatever could be of help).

Here is my main concern:
I know that if I do not have a public IP for my SMTP I could have frame Relay issues and won't be able to use it. For this, I know, as an example, that Nas4Free is able to send emails without any issue and all this is done behind a firewall (like in my case). This could be an excellent way and I wish to learn how to do so.
Another alternative would be to set up my local system to use an existing mail service I have from one of my providers.

Can anyone please help me getting started?

Thank you,
Spiro

---

### Post by TheFu on 2013-02-27
Most hosting providers use CentOS for their hosts, not Ubuntu.
[http://www.howtoforge.com/perfect-server-centos-6.3-x86_64-apache2-courier-ispconfig-3](http://www.howtoforge.com/perfect-server-centos-6.3-x86_64-apache2-courier-ispconfig-3)

You can probably find an Ubuntu "Perfect Server" setup there too.
Please realize that Falco doesn't always make security the primary concern, so you will end up with a working "perfect server", but don't expect it to be highly secure.

Also, I'd like to point that that almost nobody - nobody - should still be using plain FTP anymore. sftp would be much better.

---

### Post by LHammonds on 2013-02-27
Are you planning on doing all of this on one server???

I would separate the services onto individual servers and depending on your solution, you might have to.

For example, if you went with Zimbra for your mail server, it would need to be dedicated since it has its own mysql and web service you shouldn't tinker with.

You can run Zimbra as your mail server for your LAN only and later make it accessible from the entire world.  You can also make sending emails from your other servers go through it. (I used "sendemail" for my scripts and point it to my zimbra server).

LHammonds

---

### Post by SAngeli on 2013-02-27
**TheFu** Thank you for your precious info. FTP I agree with you to go with SFTP but being inside my LAN I was not concerned. Nevertheless, yes it should only be SFTP.

**LHammonds** Yes, I plan on doing all these with one server as this is for learning/testing and will host just a simple site for learning. Otherwise, no. I would not do so even if when you get a VPS one would be using only one server for all services.

I found the similar article for [**[COLOR="Blue"]Ubuntu server[/COLOR]**]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p7") on the same website.

As I do need to first of all use it locally, and as I know a little better and more about Ubuntu I believe it would be better to start with Ubuntu. Later on, if i will opt for a VPS I can replicate most of what I have learned with CentOS. Moreover, with ubuntu I do not have a GUI console and I can manage it all from SSH. With CentOS I have never learned how to replicate the GUI interface over the network (like remode desktop or similar).

I will study what each of those packages do but wish to ask, up front, these questions:

- running on my LAN will I still need all these packages, specifically BIND DNS Server
- would "PureFTPd" allow me SFTP or do I need to install another package rather than this one?
- with this system, will I be able to use SMTP without having the frame relay issue (this is my major convern)?
- Is there an alternative to WebMail package? I do not like a lot SquirrelMail.

thank you,
Spiro

---

### Post by TheFu on 2013-02-27
> **SAngeli said:**
> **TheFu** Thank you for your precious info. FTP I agree with you to go with SFTP but being inside my LAN I was not concerned. Nevertheless, yes it should only be SFTP.

The default openssh server supports scp and sftp.

**> **SAngeli said:**
> LHammonds** Yes, I plan on doing all these with one server as this is for learning/testing and will host just a simple site for learning. Otherwise, no. I would not do so even if when you get a VPS one would be using only one server for all services.

Splitting these things up into different VMs would be better, unless you are trying to learn how $10/month VPS services or $5/month hosting providers work.   Most of these, perhaps almost all, do not run email on the same boxes they allow webhosting on.

> **SAngeli said:**
>  I found the similar article for [**[COLOR=Blue]Ubuntu server[/COLOR]**]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p7") on the same website.
I hoped you would. Google is amazing.

> **SAngeli said:**
>  As I do need to first of all use it locally, and as I know a little better and more about Ubuntu I believe it would be better to start with Ubuntu. Later on, if i will opt for a VPS I can replicate most of what I have learned with CentOS. Moreover, with ubuntu I do not have a GUI console and I can manage it all from SSH. With CentOS I have never learned how to replicate the GUI interface over the network (like remode desktop or similar).
Using a GUI is a bad idea for server management, IMHO. Even web-guis. They just add another level of access that hackers love.  The shell/CLI commands between most Linux systems do not change much, if at all, but the GUIs change all the time - just look at Ubuntu's GUI.

> **SAngeli said:**
>  I will study what each of those packages do but wish to ask, up front, these questions:
- running on my LAN will I still need all these packages, specifically BIND DNS Server
- would "PureFTPd" allow me SFTP or do I need to install another package rather than this one?
- with this system, will I be able to use SMTP without having the frame relay issue (this is my major convern)?
- Is there an alternative to WebMail package? I do not like a lot SquirrelMail.


What you need depends on your specific requirements. You may or may not **need** any specific package.  There are 1000 ways to accomplish almost anything in Linux.  For example, there are 3 very popular MTAs - sendmail, postfix, exim.  They all do basically the same things, but each has a purpose and places where they are better than the others.  YOU need to decide which based on your requirements.

Most popular FTPd-type servers have been hacked at least once in the last 5 yrs and had back doors inserted into the source code. Once the code was reviewed ... eventually, it was corrected, but some of the inserted code was active almost a year.  IMHO, no FTP server is safe. NONE.  

Use the openssh server and be done with it.  OpenSSH has had security flaws too, which were discovered eventually and patched quickly.

The more services that you run, the more places for hackers to get inside your systems. It is very simple math.

Frame Relay is a WAN networking technique and has NOTHING to do with these things.  Only hardcore telco routing people would care about that these days.  It is very unlikely that your local ISP connection makes anything about frame relay known to your connection.

For finding alternative tools/software for anything - you should google {package vs} is a good google technique, check** freshmeat.**net, check for **wikipedia** comparison articles and create a list of potential options to research more closely. Each will have pros/cons.  Google "squirrelmail vs" - what does that return?

I should point out that I've been running a Zimbra server with a few email front-end gateways for over 5 yrs. Prior to that, I was a pure postfix/courier admin.  Zimbra provides enterprise calendaring - which is a feature that was required. If all you want is SMTPS and IMAPS (always use SSL/TLS versions), their is no need for Zimbra.  I'll never go back to POP3. Not ever.

---

### Post by SAngeli on 2013-02-27
Hi TheFu,
Quite a lot of good info you provided me with. Thanks again.
A quick clarification (in case I made a mistake):
I recall in the past having installed a mail server and when I was sending mails to users most of the were not delivered because my SMPT was behind the firewall.
So, I was told not to use this system because outer providers when receiving mail will check on the sender SMTP. It was called frame relay.
Now I do not know if I missuse this term but the concept is this one.
Can you please clarify this for me.
As you noted this point is quite important to me.


Thank you,
Spiro

---

### Post by TheFu on 2013-02-27
> **SAngeli said:**
> Hi TheFu,
Quite a lot of good info you provided me with. Thanks again.
A quick clarification (in case I made a mistake):
I recall in the past having installed a mail server and when I was sending mails to users most of the were not delivered because my SMPT was behind the firewall.
So, I was told not to use this system because outer providers when receiving mail will check on the sender SMTP. It was called frame relay.
Now I do not know if I missuse this term but the concept is this one.
Can you please clarify this for me.
As you noted this point is quite important to me.

"Open Relay" is probably the term.  Google it.

Firewalls can block anything. That doesn't mean they will. When I had a residential ISP, they didn't block anything except Windows file sharing for over a decade. In 2010, they finally started blocking email (SMTP). Initially, I paid for an email forwarding service, but after a few months, it was clear that other problems were happening on that connection, so my business pays for a business connection now that doesn't block anything.  Plus I have multiple public, static IP addresses.

Residential ISPs usually block in/outbound SMTP (not SMPT) to prevent email spammers.  here are ways around this using an external service, but many email server people, me included, block connections from residential ISP email servers to reduce spam.

You can send outbound email from Linux using sendmail, postfix, exim or any other SMTP MTAs using the ISP email gateway server(s), if you set it up correctly. They may or may not validate the claimed domain in the FROM address.  For inbound email, you'll probably need a forwarding service ... or you could simply poll almost any email service external to your LAN using something like fetchmail.

Email can be really simple or extremely complex.  What is required depends on your situation and how concerned about spam that you are.

I've written about these things on my blog, jdpfu.com

---

### Post by lisati on 2013-02-28
A basic email server *can* be done from a dynamic IP address, but as TheFu points out, many server people take steps to block direct connections from them, and ISPs often block SMTP connections that don't go through their own servers.

My suggestion is to start small, get the basic functionality right, adding bells and whistles as needed.

---

### Post by SAngeli on 2013-03-01
Hi,
I decided to reinstall my ubuntu server install (ver 12.10).
I installed LAMP and updated the entire system.
Now I have to decide _what_ to install and setup for my Mail services.

I know I wish to send all mail and system mail through my ISP SMTP just like what nas4free as example does (simply being configured as if it is a mail client software). If my ISP bloks this, than I will use [gmail]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp"). I do not know if I would also need to receive mail, when using/simulating web development with CMS.

What should I install and setup out of these three (sendmail, postfix, exim) that would allow me this and would well integrate with CMS (like Wordpress, Joomla, Drupal)?
Here is what I have already found: an [Ubuntu article]("http://ubuntuforums.org/showthread.php?t=770629").

Please let me know.
Thank you,
Spiro

---

### Post by TheFu on 2013-03-01
> **SAngeli said:**
> Hi,
I decided to reinstall my ubuntu server install (ver 12.10).

12.10 has proven to be less-than stable for many, many, people, so if you do not have a specific need for 12.10, dropping back to 12.04 server is highly, highly recommended.  You'll thank me.

> **SAngeli said:**
> 
I installed LAMP and updated the entire system.
Now I have to decide _what_ to install and setup for my Mail services.


I've never actually used the "LAMP" install option.  I prefer to install exactly the packages I want.  Only the ssh-server gets installed during that process for my machines. Too many hidden details - I do not like.

> **SAngeli said:**
> 
I know I wish to send all mail and system mail through my ISP SMTP just like what nas4free as example does (simply being configured as if it is a mail client software). If my ISP bloks this, than I will use [gmail]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp"). I do not know if I would also need to receive mail, when using/simulating web development with CMS.
Any MTA should work with any program on Linux that needs to send email.  You probably want to do a little research.
* MTA
* SMTP
* IMAP
* POP3

These are the commonly used protocols and you can have 1, 2, or 3 different programs performing these duties.  MTAs - Mail Transfer Agents - speak SMTP or SMTPS.  Email clients speak SMTP when sending and either IMAP/IMAPS or POP3 or POP3S when receiving/reading email.  That means that most people deploy an SMTP server AND another IMAP server.

> **SAngeli said:**
> 
What should I install and setup out of these three (sendmail, postfix, exim) that would allow me this and would well integrate with CMS (like Wordpress, Joomla, Drupal)?
Here is what I have already found: an [Ubuntu article]("http://ubuntuforums.org/showthread.php?t=770629").

I like postfix, but other people will say to only use sendmail or exim.  Sendmail can do anything, so it is extremely complicated to setup in a secure way.  Postfix was designed to address 98% of what sendmail can do, but with 3x more security.  Exim - I really don't have a clue about it. Sorry.

Any CMS will talk to any standards-based MTA.  That is the beauty of standards, so it will not matter which MTA you choose.

I think I said this previously, maybe not.  I use** postfix** and have used** Courier** for IMAP.  If you run your own server there is little reason to use pop3. IMAP is so much nicer, especially when you have multiple clients like a smartphone, laptop, tablet, desktop, netbook ... having the exact same view for all email clients is very nice.  These are all based on standards, so if any client says they support "IMAP" then you are golden.  Every client supports SMTP, so that is not an issue.  Be certain to use SSL/TLS for everything - this is not the default.

```
postconf -n
```
will be a very helpful command to get postfix configured properly.  Please, please do not become an open-relay. If you are, you will be blocked by most spam-blocking black lists. Getting removed is very difficult.

---

### Post by sioxs on 2013-03-02
Just a thought....
If you want to try and test without too much hassle easy configuration and management I would suggest using virualization environments (depending on how much physical RAM you have will determine how many instances you can run simultaineously) 
You can always run them one at a time.
[VMWare]("http://www.vmware.com") or [Virtualbox]("https://www.virtualbox.org/") are good solutions and install one of the pre-configured machines from [TurnKey]("http://www.turnkeylinux.org/") chances are you'll find what your looking for there.
As for server management I use [Webmin]("http://www.webmin.com/") on my Ubuntu Server 12.04 It comes as the default in TurnKey and is fairly user friendly to integate with other systems.
Between these solutions you can do what you want without touching your base host system - and use a ssh conection for everything. Perfect for testing. Later you can import to the cloud for deployment.
If you messed up just delete the .vmdk and start over
PS. Sharing information between machines is seamless with a bit of tweaking or you can just attach a flash drive to share information.
Hope this helps

sioxs
***"we can't solve problems with the same kind of thinking we used when we created them"***

---

### Post by TheFu on 2013-03-02
> **sioxs said:**
> Just a thought....
If you want to try and test without too much hassle easy configuration and management I would suggest using virualization environments (depending on how much physical RAM you have will determine how many instances you can run simultaineously) 
You can always run them one at a time.

I am a huge user of virtualization.  If you are virtualizing servers, use KVM or Xen.  VMware-Player or VirtualBox are better for desktop-on-desktop VMs, or just playing, but I've found the overhead for both to be too much for server-on-server VMs.

BTW, both my email gateway and email server are running on VMs ... KVM VMs.  Many other VMs are also running on the same set of servers - also with KVM, but this is a completely different area than the root question.  If you want a virtualbox VM to perform well: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) will explain what you need in the setup and settings.

---

### Post by sioxs on 2013-03-04
> **TheFu said:**
> I am a huge user of virtualization.  If you are virtualizing servers, use KVM or Xen.  VMware-Player or VirtualBox are better for desktop-on-desktop VMs, or just playing, but I've found the overhead for both to be too much for server-on-server VMs.

BTW, both my email gateway and email server are running on VMs ... KVM VMs.  Many other VMs are also running on the same set of servers - also with KVM, but this is a completely different area than the root question.  If you want a virtualbox VM to perform well: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) will explain what you need in the setup and settings.

Your right it's a bit off topic but relevent if your wanting to just setup something for testing.
As far as running VM's I've yet to try KVM and now plan to include it on the todo list.Thx!
Load ballancing in Virtualbox can be accomplished using headless mode which disables X server functionality
the vrde=off switch disables any remote GUI's = Much faster less headroom required.
I usually run two as well; one headless 4 webservers and one I'm in the middle of rebuilding _again_ this time running from raw disk partitions (3). It's a bit tricky to setup, special considerations have to be taken into account or you'll mess up your MBR and data but it seems to be working well so far. The load on the host running Kubuntu 12.04 x86 is around 20% of capacity. 
Top says load average: 1.08, 1.03, 1.05 with servers running - I can live with that. 
BTW: Thanks for the link always can use tweaking ;)

Peace!
***"We can't solve problems with the same kind of thinking we used when we created them"***
BackTrak Live DVD.iso on USB via casper 
Debian 6.7 Virtualbox from raw-disks w/full gnome desktop (testing) 
Ubuntu Server 12.04 - standalone gateway encrypted LVM
Turnkey Virtualbox - headless -vrde=off
Kubuntu 12.04 - host workstation

---

### Post by SAngeli on 2013-03-05
Hi,
I made some research and reading but I am a bit confused on few things. Please if possible let me have some answers so that I can move on.
I checked with Joomla Administration under settings for mail server and I can choose among php, sendmail, SMTP. I do not know what WordPress uses.
What SMTP refers to? I know sendmail refers to the program named "sendmail". Does SMTP refers to postfix or sSMTP by any change?

Because I already have sSMTP installed, prior to this thread, I was trying to find out if I am able to send mail through my ISP SMTP but so far I am only able to do so with Google while I am unable to customize the From field.

I watched on YouTube a video on how to install and customize sendmail and postfix.
Which of the three listed (sendmail, postfix and sSMTP) would allow me to be compatible with CMS, php and to act as a SmartHost & to rewrite From-address?
I am not doing spam or other bad things. I just need to be able to send mail properly because my home server is behind a firewall and I cannot open IP addresses. So, it is for proper testing and web development.

I noticed that sSMTP is quite simple to setup, though I fail being able to rewrite (dynamically) the From-address and fail to send through my ISP. Only Googole works and I do not know why. Also in "ssmtp.conf" I do not know how to enable SSL rather than TLS?

thank you,
Spiro

---

### Post by TheFu on 2013-03-05
> **SAngeli said:**
> Hi,
I made some research and reading but I am a bit confused on few things. Please if possible let me have some answers so that I can move on.
I checked with Joomla Administration under settings for mail server and I can choose among php, sendmail, SMTP. I do not know what WordPress uses.
What SMTP refers to? I know sendmail refers to the program named "sendmail". Does SMTP refers to postfix or sSMTP by any change?

Because I already have sSMTP installed, prior to this thread, I was trying to find out if I am able to send mail through my ISP SMTP but so far I am only able to do so with Google while I am unable to customize the From field.

I watched on YouTube a video on how to install and customize sendmail and postfix.
Which of the three listed (sendmail, postfix and sSMTP) would allow me to be compatible with CMS, php and to act as a SmartHost & to rewrite From-address?
I am not doing spam or other bad things. I just need to be able to send mail properly because my home server is behind a firewall and I cannot open IP addresses. So, it is for proper testing and web development.

I noticed that sSMTP is quite simple to setup, though I fail being able to rewrite (dynamically) the From-address and fail to send through my ISP. Only Googole works and I do not know why. Also in "ssmtp.conf" I do not know how to enable SSL rather than TLS?

I've never heard of sSMTP before. You are on your own there.   I know that both sendmail and postfix and exim support rewrite rules, but I have no idea if you can use gmail as a drop off.

SMTP is a protocol that every email server and client speaks. That is probably the correct answer for Joomla.  Postfix will install a sendmail compatible program - it will act just like sendmail to the outside world, if you use it.  Any program on any platform that wants to sent email will use SMTP.

If you cannot modify ports or open the router, then you are limited to the sort of email access (sending and receiving) that will be possible.  It is completely up to your ISP, so YOU will need to learn and do the research to figure out what works and what doesn't.  I think we already told you about this in the first few replies.

FROM addressing on all email servers is just a suggestion.  The FROM means nothing.  I can send messages from [email]god@heaven.org[/email] using almost any email server.  Your php scripts can connect directly to the remote SMTP server (be certain to look up the mx DNS record first) and send messages that way. No need to setup a local email server at all .... er ... provided your ISP doesn't block outbound SMTP ports.

I think you might just want to work on everything else and keep email local for testing.  I **know** that Ruby on Rails can send emails through a gmail account and spoof the FROM address. We did that in a class a few days ago. I would be surprised if PHP couldn't do that too.  There is probably 20 different  plugins for every CMS to accomplish the same thing.  More research needed?  You probably want to ask CMS-specific questions on their support forums.

---

### Post by SeijiSensei on 2013-03-05
I still use sendmail because I know how to get it do pretty much everything I want it to.  That said, you'll probably find more support here for Postfix since that is the Ubuntu default.

I've been running combination web/mail/DNS servers on a single machine for years, even back when my servers were i486 boxes.  Unless you have very high traffic volumes, you won't have any problems doing this.  Oh, and these servers all run PostgreSQL in the background, too.  

For POP/IMAP I use dovecot.  It has pretty much supplanted the UWashington imapd server that was once the norm.

---

### Post by SAngeli on 2013-03-08
Hi,
so far I made progresses learning about postfix and being able to get it to work as Smart Host.
I wish to ask few additional questions.

1. if I wish to have mixed delivery of main (locally on localhost and Smart Host) is this possible? If so, where would I set this up so that if I send a mail to @localhost it would be delivered locally anf if I send a mail to [email]user_xx@gmail.com[/email] it will be delivered via Smart Host?

2. so far I installed postfix and Postfixc Admin. In order to also manage mail locally with the use of a web interface, what do I need to install?
So far, I understood I have to install Dovecot (for POP3 and IMAP) and I would prefer Roundcube as webmail. Is this all?

3. Is it possible to have a complete string "atp-get install" listing all packages needed, starting from scratch, for setting up a mail server with Smart Host and local mail + web?
Also please consider including in the list spamassassing and clamAV. Beside the fact that MySQL is already installed (as part of LAMP) do I also need any additional MySQL components to install? I read it is needed to manage user accounts and e-mail forwarding or can it be avoided?

4. Integration betweeb the mail server and Webmin is done automatically or is there anything needed to be done manually or install additiona packages?

Thanks to this post I am better learning how to complete mail server installation.
Spiro

---

### Post by SeijiSensei on 2013-03-08
> **SAngeli said:**
> 1. if I wish to have mixed delivery of main (locally on localhost and Smart Host) is this possible? If so, where would I set this up so that if I send a mail to @localhost it would be delivered locally anf if I send a mail to [email]user_xx@gmail.com[/email] it will be delivered via Smart Host?

Usually that doesn't require any particular configuration.  Mail to user@localhost should be delivered locally, while mail to any domain not supported by your server should be forwarded through the relay host.  Is that not happening now?  If not, read [this](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination).

---

### Post by SAngeli on 2013-03-08
Hi,
I have not tried yet as I have not completed pop3 configuration. I will let you know.
Please, if possible, would it be possible to answer also the other questions?
I am finishing to learn/setup this test server so that later I can perform a fresh new full install with all my notes so that I can see if I have properly learned and also to have a clean install.
Thanks,
Spiro

---

### Post by EmmEight on 2013-03-08
The first thing I would do is set your server up with a static IP address, and instal OpenSSH.

That is usually my 1st two steps.

If you want remote access from away from your LAN you can forward port 22 on your router/gateway to the static IP of your server.

Then you can use proftpd or openftp to get your started with FTP access

I am kind of interested to see what you use for a mail server/client. I am in the same situation.):P

---

### Post by TheFu on 2013-03-09
> **SAngeli said:**
> so far I made progresses learning about postfix and being able to get it to work as Smart Host.
I wish to ask few additional questions.
Questions are good.

> **SAngeli said:**
> 1. if I wish to have mixed delivery of main (locally on localhost and Smart Host) is this possible? If so, where would I set this up so that if I send a mail to @localhost it would be delivered locally anf if I send a mail to [email]user_xx@gmail.com[/email] it will be delivered via Smart Host?
Setup a local domain, like "angeli.lan", then this will work automatically with just a few settings.  In postfix there is a local delivery options. Any emails send there will be delivered locally. Everything else will be sent either to a relay server that you configured or directly to the remote systems based on their MX DNS records (if the ISP doesn't firewall email). You can also setup specific transport rules to specific domains (man transport explains all).    For local delivery, you do not need any MX records for your domain.  Inside the /etc/postfix/main.cf file are all the settings.
```
mydomain =
mydestination = 
local_recipient_maps = 

```are the main ones.  I didn't check that these were all of them - only connected to my email gateway (main job is to block spam emails), not the real email server.

```
$ dig google.com mx
```
will show the MX (Mail eXchange DNS record) You can do this for any domain. That is how email systems know where to send non-local emails.

> **SAngeli said:**
> 2. so far I installed postfix and Postfixc Admin. In order to also manage mail locally with the use of a web interface, what do I need to install?
I don't use any web interfaces for server admin. Sorry.  I think that is a security issue. Learn to do the configs manually. There are lots of how-tos and it really is easy.

> **SAngeli said:**
> Hi,So far, I understood I have to install Dovecot (for POP3 and IMAP) and I would prefer Roundcube as webmail. Is this all?  Don't know.  I haven't used dovecot in years and never used roundcube.  I would highly recommend only using imaps, not pop3 or pop3s, unless you want to force all email to be downloaded. This is fine for an ISP, but terrible for a business. Webmail, the last time I tried, it was trivial to setup. I used squirrelmail then.  Something like 4 settings was it related to the SMTP/IMAP connections. Simple.

> **SAngeli said:**
> 3. Is it possible to have a complete string "atp-get install" listing all packages needed, starting from scratch, for setting up a mail server with Smart Host and local mail + web?
Sure, but the postfix package requires configuration during install.  I almost always setup postfix as a satellite mail server (all email gets forwarded to the main server) so I don't recall many setup details. Sorry.

> **SAngeli said:**
> Also please consider including in the list spamassassing and clamAV. Beside the fact that MySQL is already installed (as part of LAMP) do I also need any additional MySQL components to install? I read it is needed to manage user accounts and e-mail forwarding or can it be avoided?
Good luck with that.  The magic of APT is that dependencies are almost always automatically completed.  I'm not going to check this, but something like:
```
$ sudo apt-get install postfix spamassassing clamAV dovecot roundcube 
```
would seem to be reasonable starting point - you'll need to spell the names of the packages correctly, of course. I used your spellings for consistency in this post.

MySQL is not required for email. I do not use it at all.  However, for an ISP with 20,000 users, I can see where have a relational DB involved could be handy.  I've never run email servers for orgs with more than 300 people, so never use mysql.

> **SAngeli said:**
> 4. Integration between the mail server and Webmin is done automatically or is there anything needed to be done manually or install additiona packages?
Like I said before, I consider any webgui management tool to be an added security risk on already sensitive servers. I don't use them.  I don't know any professional sys admins who do in any corporate environments either.  Only ISPs seem to do this where email is a free service expected, but not where they make money.  Why do you think more and more ISPs are outsourcing email to Yahoo and Microsoft?

---

### Post by SeijiSensei on 2013-03-09
There are most certainly ways to make Webmin more secure than the TheFu suggests.  Just don't bind the server to any Internet-facing interface.  On a dual-homed machine, bind it to the LAN-facing interface.  On an Internet server, install OpenVPN and bind Webmin to the tunnel interface.  Add some iptables rules to restrict access to the Webmin port, usually 10000, by client IP address.  Use a port scanner on a remote machine to insure that port 10000 is invisible to Internet hosts.

---

### Post by TheFu on 2013-03-09
> **SeijiSensei said:**
> There are most certainly ways to make Webmin more secure than the TheFu suggests.  Just don't bind the server to any Internet-facing interface.  On a dual-homed machine, bind it to the LAN-facing interface.  On an Internet server, install OpenVPN and bind Webmin to the tunnel interface.  Add some iptables rules to restrict access to the Webmin port, usually 10000, by client IP address.  Use a port scanner on a remote machine to insure that port 10000 is invisible to Internet hosts.

I agree - it can be made much more secure, but new users of these tools are not often very experienced.  Also, I still see more than a few attempts on my servers to access these web-administration tools for systems, databases, and applications even though I never have used them. In the last 30 minutes, 47 attempts were made on my tiny blog server. The risk is real, so if you must run these tools, please, please, please secure them with more than a plaintext password that will be hacked. Use the network layer to make it impossible to access by outsiders.

My security training tells me not to load anything on a system that isn't needed.  "Needed" is highly subjective so my "needed" and your "needed" will not always be the same.

BTW, it isn't just web-guis that I avoid. There are some fantastic CM tools that I won't load either, just because they require a non-default language to be loaded. Puppet is one of those.  It uses Ruby.  I like Ruby, but still don't want to load it on a system that has ZERO other use for it.  Saying that I like Ruby is a little bit of an understatement. ;)

SeijiSensei is a very smart person, so it would be smart to follow his recommendations.

---

### Post by SAngeli on 2013-03-09
Hi and thanks for your answers.
I wish to only focus on getting this prject completed. After that I can spend some time learning more. So, I believe it is best to narrow down only what I really need.
Webmail was a way to check mail for local users when symolating for CMS new account creation. I will use local mail client for this.
- Smart Host is already working so that I can use any CMS;
- Webmin is already working but I need to customize (also for security) and learn about it;
- I need to learn and finish customizing phpMyAdmin (config.inc.php) as it complaints that its configuration is not complete;
- I need to slightly lear about Apache2, the basics:
- SFTP is alredy running via the openSSH.

This is what is left:

- What do I have to install in order to have only IMAP for local users? What parameters do I have to use for setting up the mail client using SSL I assume? How to know?
- From Windows 7 client to server: Is there a reason why sftp to my server (on my LAN) I copy a file at 4.1Mbit when insteas if I go through Samba (via Explorer) I get 51MB? How come is it so slow? Do I have to change sftp softwre on the server or is there a setting I have to do? This is strange.
- How to manage FTP user accounts? Is this done simply by adding a user to the ftp group?

Thank you,
Spiro

---


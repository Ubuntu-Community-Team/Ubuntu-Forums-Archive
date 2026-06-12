---
title: "Advice for 1 user / mailaccount Ubuntu mailserver"
date: 2024-02-12
forum: Server Platforms
---

### Post by player02 on 2024-02-12
Hi,

The goal is owning my own email infra structure (without mailserver hosting).
While it's only for me, 1 user (mailaccount) is sufficient.

On all my devices (phone, laptop, pc) there should be access to calendar and email for me.
This by IOS on my phone and Linux laptop and PC (through Evolution or Thunderbird).

At this moment my DNS records for my domain are ok.
For the email serving purpose I have another PC with Ubuntu Server 22.04 installed.
This with Postfix and Dovecot.
The mail server PC is only meant for serving, so it would be nice if I can take over this machine from my laptop or my main PC.

Last big things to set up for this server PC are the SSL certificate and calendar software.
My ISP blocks port 25 so I need a certificate for port 587.

Excuses for the long introduction.

Through all the instructions on the internet it's hard (for me as novice) to pick one or two for my needs.
Searches mostly lead to web server installation instrutions

For the calendar serving purpose I think I must turn my mail server into a web server.
DAViCal can perhaps take care of the calendar need.

For the SSL certificate I can make use of the letsencrypt shell certbot option.
Or free SSL / TLS certificate from cloudflare.

Can you please give some advice for certificate and de calendar software?
Do I really need to turn my mail server into a web server?
What would be the best way (for me) to obtain a letsencrypt certificate?
Is DAViCal a smart way to get a calendar running (on linux machines and IOS phone).

---

### Post by SeijiSensei on 2024-02-12
for 3)

Install acme.sh from [https://github.com/acmesh-official/get.acme.sh](https://github.com/acmesh-official/get.acme.sh)

Then look here: [https://wiki.zimbra.com/wiki/JDunphy-Letsencrypt](https://wiki.zimbra.com/wiki/JDunphy-Letsencrypt)

Passing "-s letsencrypt" to the script makes it use the LetsEncrypt servers.

---

### Post by player02 on 2024-02-12
Hi Sensei,
Thanks a lot. You made my view a bit clearer.
It made me move my dns records to another registrar. But I am still struggling with the certificates and keys.
The good thing is that I can take the short cut. Setting up a web server does not make this key and certificate fiddling go away, 
It seems I need a lot of time to get this right.
There are a lot of ways to generate keys and certificates, but they don't fit very well with Thunderbird (Yes it's my opinion).
I have very good experience with the syncing of Evolution (ews). Much better than with the Thunderbird plugins. But I think it's even more a b*tch. Time to go to bed.
Hopefully next time better news.
Regards

---

### Post by TheFu on 2024-02-12
> Last big things to set up for this server PC are the SSL certificate and calendar software.
My ISP blocks port 25 so I need a certificate for port 587.


587/tcp is typically for authenticated clients to connect to an email server.  That's for Thunderbird to authenticate the connection and to send emails.   465/tcp is often used for the same purpose, authenticated client SMTP connections.

25/tcp is  typically for SMTP to SMTP communications.  I suppose it can be any port, I've only seen email forwarding services using 2525/tcp. They run about $25/month.  I don't know how to tell other SMTP servers which port to use. It would need to be in DNS somewhere.  Making postfix listen on 2525/tcp isn't hard - that's not the issue.  Announcing that your MX happens on port 2525 to the world is what I don't know off the top of my head.  [https://serverfault.com/questions/452653/many-isps-is-block-port-25-how-do-i-choose-an-alternative-port](https://serverfault.com/questions/452653/many-isps-is-block-port-25-how-do-i-choose-an-alternative-port) has some alternatives.

As usual, there are 1000 solutions.  Having an ISP that doesn't block port 25 would be the best answer.  Many will allow this when you sign up for a business account, not a residential account.  All will allow 25/tcp if you have business and complain.

Other solutions is to get a cheap VPS to be your email gateway.  It wouldn't hold any email, just provide an interface for all inbound and outbound email.  This is what I do.  I use a VPN to connect to that VPS with services on my home "public services" LAN.  The VPS may block port 25 too. Just open a ticket and jump through their hoops to get it opened. Took me 3 emails to get my VPS to do that.  Honestly, I appreciated they weren't push overs - spammers wouldn't go to the effort they needed.  They just asked a few questions about the planned email use, volumes, stuff like that.

There are mail-in-a-box services too.  [https://mailinabox.email/](https://mailinabox.email/) I've never used it.  I'm old and have been running email servers since around 1994.  I'd rather pay for a monthly VPS than have to trust someone too much with emails.

Regardless, you should put each of these public services into either a separate VM or container to make upgrades easier.  Mixing services just makes the software stack for each harder to maintain and upgrade. Don't. Just don't.   The hard part is that running a good VPN inside a container usually breaks the security of the container by requiring root to run it. That's a 100% no-go for me, so my VPN servers on both sides are inside full VMs.

Calendaring is a different issue completely.

---

### Post by player02 on 2024-02-13
In the heat of the moment I was a bit too negative about Thunderbird and Evolution.
Just after writing my last text (above) I realized I should have mentioned that telnet also does not receive and send external.
That is something I should use more as an starting point (for problem solving).

> **TheFu said:**
> 587/tcp is typically for authenticated clients to connect to an email server. & [COLOR=#000000]Having an ISP that doesn't block port 25 would be the best answer.[/COLOR]

Excuses, no praphrasing intended.
Well, the info for the silly people like me is different. With ISP's blocking port 25 and reading texts like ([https://www.cloudflare.com/learning/email-security/smtp-port-25-587/):](https://www.cloudflare.com/learning/email-security/smtp-port-25-587/):)
**[SIZE=4]What SMTP port should be used?[/SIZE]**

[FONT=-apple-system]Originally, the [Simple Mail Transfer Protocol (SMTP)]("https://www.cloudflare.com/learning/email-security/what-is-smtp/") used port 25. Today, SMTP should instead use port 587 &#8212; this is the port for encrypted email transmissions using SMTP Secure (SMTPS).[/FONT]


There you go after seeing people on YouTube setting up a mailserver in 5 minutes. Let's go for port 587. Not knowing the mess you step in.
Perhaps the smart people keep the stupid people silly, to prevent more poor people to set up a mailserver for bombing the world with crappy emails.

The fact is that it would be more handy to have some good information about what is actually needed to get mail over port 587.
Which certificates and keys are there that are needed for port 587? How with self signed? How with not self signed? etc...

I found out that I can move to another ISP for port 25. They actually have a good product for a nice price. But for me it's going to be a good setup or no setup.
I don't have the intention to frequently struggle with black lists. If that's the alternative, than my new server is going to get a new home in the near future.

For the calendar I think it's better to use some cloud help. I always saw it as something that's part of the email configuration. But there is little reason to push that idea through setting up a mailserver (I think now).

As before, h[COLOR=#000000]opefully next time better news.[/COLOR]

Thank you!

---

### Post by TheFu on 2024-02-13
> What SMTP port should be used?

There are 2 SMTP ports. They serve different purposes.

**For server-to-server SMTP,** port 25/tcp should be used. This is unauthenticated email. No userid/password. TLS certs can be of any sort, including self-signed. It makes little difference, since DNS hacking of clients (servers) would be completely outside the control of the target SMTP server. All TLS does is to ensure that messages aren't molested between the client and the server involved. Little need for a paid/official cert.

**For client-to-server SMTP,** port 465/tcp or 587/tcp should be used to SEND emails. There's no mode for receiving emails between servers on port 587/tcp. These are authenticated senders using specific userids and passwords. They also use TLS (or STARTSSL) to encrypt the connection, but that's outside the userid/password authentication.

I don't know how to make it any clearer.

SMTP follows standards.  These are outlined in the RFCs and they aren't exactly long, but since SMTP has been modified slightly over the decades, there are probably 5+ RFCs (that's "standards") for how SMTP works.[https://www.rfc-editor.org/rfc/rfc5321.html](https://www.rfc-editor.org/rfc/rfc5321.html) might be the most recent SMTP standard. IDK.

Calendar programs follow different standards.  CalDAV is one.  ICS files are another.  These aren't part of SMTP standards, so if they are provided or used, it is separate.  Don't get me wrong, from an end-user standpoint, calendaring and email are tightly coupled.  When a calendar invitation is sent, it is usually an ISC file and the fat email client program handles it, if it does anything with calendars.  

MS-Exchange is why calendaring and email become coupled in the world.  In the Unix world, there are a number of "communications servers" that merge email and calendaring.

Client programs use SMTP to send email 587/tcp and IMAPS (993) or POP3S (995) to receive email.  These ports are in the /etc/services file on every UNIX system.

> I don't have the intention to frequently struggle with black lists.
Good luck with that.

If you care about privacy enough to run your own SMTP server, where does the "use the cloud" for calendaring make sense?  Calendaring is 100x easier than SMTP.  Nextcloud-Calendar makes it pretty easy, I understand.  I use Zimbra for my "communications server", mainly because of the amazing search, enterprise calendaring, LDAP, and SMTP integration. It is pretty huge and ugly, with trade-offs. Today I'd choose a different solution with nextcloud+roundcube on my short list. [https://roundcube.net/news/2023/11/30/nextcloud-the-new-home-for-roundcube](https://roundcube.net/news/2023/11/30/nextcloud-the-new-home-for-roundcube) .  There are others, but they feel "off".

Zimbra is slick like gmail, but 100% local.  Zimbra follows standards for LDAP, SMTP, IMAP, CalDAV, CardDAV, and lots of other standards.  OTOH, Zimbra is a monster and difficult to upgrade because of the 20 F/LOSS projects are all tightly coupled.  I don't let Zimbra directly on the internet.  An email gateway for all inbound/outbound SMTP is part of my security architecture.  That email gateway runs bog standard postfix on a new 22.04 system. This gateway is easy to maintain, patched weekly. It is where I do massive anti-spam stuff, though Zimbra has junk-mail filters too.

Like I posted above, there are 1000 solutions. Only you can figure out what will work for you and your skills.

---

### Post by player02 on 2024-02-13
The 25 and 875 ports I understand. But how and when to use this information is another thing.
And server to server and client to server. 

Here comes the stupid question:
Do you mean with this that I have to swap ports with iptables?

The online calendar was a bit fed by the thought of not making spaghetti installs.
I hope I ever come that far that I can install calendar software on my machine, At this moment I am not really positive about the first goal, the mail server.

And for the privacy. My activities are a bit more cryptic than my mails, but you have point.

Tomorrow I will go further with trying out the 1000 solutions (I can find on the internet).
The instructions on the Ubuntu pages for the Postfix and Dovecot combi did not work for me. But of course you can say I made it not work.
Probably I will remove all the installs and search for another instruction for Postfix. 
For Dovecot I hope to use the Dovecot instruction as a basis:
[https://doc.dovecot.org/configuration_manual/quick_configuration/](https://doc.dovecot.org/configuration_manual/quick_configuration/)

Thanks!

---

### Post by TheFu on 2024-02-13
> **player02 said:**
> The 25 and 875 ports I understand. But how and when to use this information is another thing.


You've lost me.   [https://mailinabox.email/static/architecture.svg](https://mailinabox.email/static/architecture.svg) is a simple email server architecture.

---

### Post by SeijiSensei on 2024-02-14
I use Google Calendar. Available everywhere on every device. If someone wants badly to learn that I saw my ophthalmologist last week, I really don't care.

---

### Post by TheFu on 2024-02-14
> **SeijiSensei said:**
> I use Google Calendar. Available everywhere on every device. If someone wants badly to learn that I saw my ophthalmologist last week, I really don't care.

For many people, their appointments ARE a life and death choice and sometimes we don't know the connection that makes it so.  [https://en.wikipedia.org/wiki/Nothing_to_hide_argument](https://en.wikipedia.org/wiki/Nothing_to_hide_argument)

---

### Post by SeijiSensei on 2024-02-14
I think that's true for a relatively small proportion of computer users, and an even smaller proportion of Linux users. Call me naive if you will.

---

### Post by TheFu on 2024-02-14
Another leak of emails: [https://krebsonsecurity.com/2024/02/u-s-internet-leaked-years-of-internal-customer-emails/](https://krebsonsecurity.com/2024/02/u-s-internet-leaked-years-of-internal-customer-emails/)
> The Minnesota-based Internet provider U.S. Internet Corp. has a business unit called Securence, which _specializes in providing filtered, secure email services to businesses, educational institutions and government agencies_ worldwide. But until it was notified last week, U.S. Internet was publishing more than a decade&#8217;s worth of its internal email &#8212; and that of thousands of Securence clients &#8212; in plain text out on the Internet and just a click away for anyone with a Web browser.

Companies claim to "take security very seriously", but like your money, nobody cares as much about your data privacy as you do.  

I'll run my own email server and keep that email off someone else's computer, storage and network, until I become senile and cannot handle it anymore.  I'll probably be drooling by then anyway. Same for calendar data. I certainly don't want that on any google/apple connected devices, if I can help it. Secrecy is so ingrained in both those vendors that when they do mess up, it is seldom that anyone is told.

---

### Post by player02 on 2024-02-14
> **SeijiSensei said:**
> I use Google Calendar. Available everywhere on every device. If someone wants badly to learn that I saw my ophthalmologist last week, I really don't care.

Yeah, that's what I think, but I do see it as a sport to avoid the big data farmers.

> **TheFu said:**
> You've lost me.   [https://mailinabox.email/static/architecture.svg](https://mailinabox.email/static/architecture.svg) is a simple email server architecture.

Haha, nice pic!
I love simple overviews. 
But the reach of port 25 versus 587 is still not clear for me.

Good news is that my new ISP connection is on it's way. It's clear that without blocking port 25 things should go easier.

I am afraid I should be kicked off this forum.
Since yesterday I no longer have Ubuntu installed.
With my new to be ISP there is nothing standing in the way. I am going to make it work.

But it's going to be on an Arch Linux (LTS) mail server.

---

### Post by TheFu on 2024-02-14
> **player02 said:**
>  
But the reach of port 25 versus 587 is still not clear for me.


Don't now how much simpler it could be explained.  Oh well. Sorry.

> **player02 said:**
>  
I am afraid I should be kicked off this forum.
Since yesterday I no longer have Ubuntu installed.
With my new to be ISP there is nothing standing in the way. I am going to make it work.

But it's going to be on an Arch Linux (LTS) mail server.

Arch isn't an LTS, but you'll learn that the hard way.  Calling something "LTS" doesn't make it one.  Arch is bleeding edge ... and expect some blood every few months if you try to run a server.  Arch is a great distro if you can tolerate downtime and broken subsystems.  If you like the hands-on nature of Arch, but you also want stability and control, then Slackware is what I'd recommend.  I ran Slackware nearly a decade.

We aren't snobs here. Just be certain to post non-Ubuntu OS questions to the non-Ubuntu/Other-OS subforum.  postfix, dovecot, and most server things aren't specific to any Linux distro, so how we configure each of those is the same regardless.  Arch will have newer/bleeding versions of those packages and will get updates faster.  That isn't always good, but you'll learn that too. 

** "New" is the enemy of "stable."**  

Rolling releases are painful every week, not every 2-4 yrs.  Pick your poison.

---

### Post by player02 on 2024-02-15
> **TheFu said:**
> Don't now how much simpler it could be explained.  Oh well. Sorry.


Well, it was not meant as feedback. I have learned a lot from you and Sensei. Thank you very much for that. It's more that Io still don't sufficiently grasp the configs for Dovecot and Postfix. Also what impacts the server to server traffic and when localhost in configs etct. But this is for a great part caused by not taking the time and just copy from web pages and pasting to the command line.
With my current Arch install on the mail PC I don't even have Xorg or Wayland or a mice configuration. This way I was forced to really look at things.

I saw a lot of things that I didn't notice before (acme record in dns), linking to the right certificates and keys in the config files.
At this moment authorisation with PAM is something I want to understand better.

I know that LTS is about the Linux kernel (that's why I placed it between brackets).

With such a simple install as I have, I don't expect  too much rolling.
With Arch solving problems can be hard. But perhaps not harder than with Ubuntu for example.

When the problem is in scope the solution is there very quick, because of the one size fits all (through pacman).

---

### Post by TheFu on 2024-02-15
> **player02 said:**
> Well, it was not meant as feedback. I have learned a lot from you and Sensei. Thank you very much for that. It's more that Io still don't sufficiently grasp the configs for Dovecot and Postfix. Also what impacts the server to server traffic and when localhost in configs etct. But this is for a great part caused by not taking the time and just copy from web pages and pasting to the command line.
With my current Arch install on the mail PC I don't even have Xorg or Wayland or a mice configuration. This way I was forced to really look at things.
"Ubuntu Server" doesn't have any GUI either. Nothing special there.
BTW, you have found a step-by-step how-to setup email guide by now, right?  [https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu](https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu) makes good how-to's. She's receptive to solving issues too. She has a 2-part guide.
Linode and DigitalOcean have guides as well.
Also, [https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/) has a more complex server setup, but you can leave out the stuff you don't need.  I don't like to have all those things in a single machine, but opinions on that vary greatly.
And there's always Sovereign: [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)

> **player02 said:**
> 
I saw a lot of things that I didn't notice before (acme record in dns), linking to the right certificates and keys in the config files.
At this moment authorisation with PAM is something I want to understand better.
I haven't bothered with certs for TLS encryption of email. Self-signed work fine. No email servers actually seem to care.

> **player02 said:**
> I know that LTS is about the Linux kernel (that's why I placed it between brackets).
That's an Arch thing.  LTS under Ubuntu means so much more - in fact, Ubuntu's Kernels used in their LTS releases are not usually LTS according to the kernel.org people. Canonical has their own kernel team who port important changes to the kernel(s) they've standardized onto.  The kernel is the main slab of the house, but it is just 1-3% of the code in any Linux computer.

> **player02 said:**
> With such a simple install as I have, I don't expect  too much rolling.
With Arch solving problems can be hard. But perhaps not harder than with Ubuntu for example.
I had more issues with Arch than with Ubuntu, but we each have different experiences.  I've only been running Linux systems since 1993. I still remember switching from SLS to Slackware because Slackware was 100x easier.

> **player02 said:**
> When the problem is in scope the solution is there very quick, because of the one size fits all (through pacman).
People like pacman.  I've never seen anything amazing that isn't included with RHEL or Debian package managers.  I have had dependency issues with all of them.  When I was new to package managers (Slackware didn't have package management when I ran it), I started with RedHat and found myself in "RPM Hell".  That when there isn't any solution to the package dependency problems.  The same can happen with any package manager that allows the flexibility of side-loading of packages. I've been in "APT Hell" a few times too, but was always able to figure out which package was causing the dependency problem and remove it, get fully updated, then install a newer version of the problem package.  

Package management can be simple or very complex. It all depends on the admin of the system. If you stick with core Ubuntu Repos and don't ever allow storage in critical file systems to run low, you'll never have a problem.

Anyway, nothing wrong with running Arch. You'll learn a bunch.

---

### Post by player02 on 2024-02-15
> **TheFu said:**
> "Ubuntu Server" doesn't have any GUI either.
Yes, I know. I installed Ubuntu Desktop when getting stuck, in the hope Thunderbird and or Evolution would give some indication. The Arch install I hope to keep gui-less. So for now I only installed NeoMutt.

> **TheFu said:**
> BTW, you have found a step-by-step how-to setup email guide by now, right?No, I did not find a complete one. The LinuxBabe guides seem very complete and also with info about the context sometimes. Thank you very much for pointing. This weekend am I going to walk it through.

> **TheFu said:**
> 
I haven't bothered with certs for TLS encryption of email. Self-signed work fine. No email servers actually seem to care.Thanks for putting it into perspective. With the wrong setup and all the Thunderbird attempts it's more then welcome.

> **TheFu said:**
> That's an Arch thing. LTS under Ubuntu means so much more - in fact, Ubuntu's Kernels used in their LTS releases are not usually LTS according to the kernel.org people. Canonical has their own kernel team who port important changes to the kernel(s) they've standardized onto. The kernel is the main slab of the house, but it is just 1-3% of the code in any Linux computer.
Yeah choices, I chose Arch in 2022 because of the specs of my new PC. The choice for me then was between Debian and Arch, wanting to try something new. New hardware types work sometimes better with new software. 

> **TheFu said:**
> 
I had more issues with Arch than with Ubuntu, but we each have different experiences. 
I think it's correct. When I started with Arch I installed it with the Gnome Desktop. I know that I was amazed how much it was like Ubuntu. Very simple, never ever problems, but learning almost nothing about Linux. Just installs with pacman and git clone (and simple update routines). After a while I installed DWM, that's what I have now for my PC and laptop without a big desktop environment. 

> **TheFu said:**
> People like pacman. I've never seen anything amazing that isn't included with RHEL or Debian package managers. I have had dependency issues with all of them. 
For the mail server (hopefully later in time) is nice to keep running. But I will make a note of the instructions that should help me resetting up the system if needed. And of course backups of the config files.
For my other computers I do care, but I am not afraid. When one system crashes, perhaps the other will still work (hopefully not updated around the same time). But my laptop is dualboot. Now with four environments no worries needed.

> **TheFu said:**
> 
Anyway, nothing wrong with running Arch. You'll learn a bunch.
Yeah, haha, my mail server project is accelerating that. Thank you very much!

---


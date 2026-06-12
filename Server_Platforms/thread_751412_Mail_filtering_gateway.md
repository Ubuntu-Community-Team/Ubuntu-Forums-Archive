---
title: "Mail filtering gateway"
date: 2008-04-10
forum: Server Platforms
---

### Post by Koybe on 2008-04-10
I'm looking forward to make a mail filtering gateway with Ubuntu and Postfix. What I really don't know is what I should use for the best :
- spamassassin
- dspam
- amavis-new
- mailscanner
- pyzor
- razor
- other tools????

Antivirus is quite simple :
- clamav

I would appreciate a web-based statistical results.

Does anybody here experienced something? What are ups and downs? Could I have a feedback?

Thank you

---

### Post by FakeOutdoorsman on 2008-04-10
I've been recently looking for a spam solution too.  There are so many choices, so I'll add to your list.  I was going to try out ASSP because I wanted to stop most spam at the SMTP level, but it doesn't easily allow secure POP, which was a requirement for me.   Other than that I've heard good things.

[Anti-Spam SMTP Proxy]("http://assp.sourceforge.net/")
[ASSP Wiki]("http://www.asspsmtp.org/")
[ASSP With Embedded ClamAV Integrated Into Postfix With Virtual Users And Domains]("http://howtoforge.com/assp_clamav_postfix_debian_etch")

---

### Post by Koybe on 2008-04-10
Thank you, I didn't hear about this one. It looks a lot easier to install. Did you test it?

I'm trying it a little, so here is more informations :
- I just want to relay filtered mail, no local delivery
- I want to get rid of as many mail as possible at this smtp level
- I want to tag unsure mail before delivering them inside the network

ASSP as a nice configuration utility, that's what I like. But I need to find how to tune it ;)

---

### Post by FakeOutdoorsman on 2008-04-10
I've installed it on a development box, but not on a live server yet (I'll do this during the next distro upgrade), so I don't have much experience with it.  I thought it could be another option for you to consider.
[Enhance Your Mail Server With ASSP (Anti-Spam SMTP Proxy)]("http://www.howtoforge.com/antispam_smtp_proxy")

If you decide to use it let us know of your experiences.

---

### Post by Koybe on 2008-04-10
> **FakeOutdoorsman said:**
> If you decide to use it let us know of your experiences.
Yep, but i'm running it on a test box too. No way for me to put that in production before more testing.

Anyway I suppose I can relay mail internally quite easily trough postfix as I would do normally.

The IN way seems natural
IN : Internet -> ASSP -> Postfix -> Internal Server -> Clients
The OUT way isn't clear for me :
OUT : Clients -> Internal Server -> ASSP? -> Postfix (send with relayhost) -> OUT

Well I need to think about that :p

Related post : [http://ubuntuforums.org/showthread.php?t=542953](http://ubuntuforums.org/showthread.php?t=542953)

---

### Post by songshu on 2008-04-11
below is what i have in my main.cf as a spam filtering solution with the top part filtering 99% of the spam at the smtp level before sending it over to amavis (clamav and spamassasin with pyzor and razor)

verry happy with my present results however i'm looking at using dspam instead of spamassasin because of the better training mechanism that can be done by all my users.

smtpd_client_restrictions = check_client_access hash:/etc/postfix/whitelist_client, 
        check_sender_access hash:/etc/postfix/whitelist_sender, 
        check_client_access hash:/etc/postfix/client_access, 
        reject_unauth_pipelining

smtpd_recipient_restrictions = regexp:/etc/postfix/regexp_access, 
        check_recipient_access hash:/etc/postfix/access, 
        permit_mynetworks,
        reject_unknown_recipient_domain,
        reject_unknown_hostname,
        reject_unknown_sender_domain,
        reject_non_fqdn_hostname,
        reject_non_fqdn_sender,
        reject_non_fqdn_recipient,
        reject_invalid_hostname,
        reject_rbl_client zen.spamhaus.org,
        reject_unauth_pipelining,
        permit_sasl_authenticated,
        reject_unauth_destination




smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/sender_access, 
        permit_mynetworks, 
        reject_unknown_sender_domain, 
        reject_non_fqdn_sender, 
        reject_rbl_client zen.spamhaus.org,
        reject_unauth_pipelining

header_checks = regexp:/etc/postfix/header_checks
body_checks = regexp:/etc/postfix/body_checks

unknown_hostname_reject_code = 554
unknown_client_reject_code = 450
message_size_limit = 10000000
strict_rfc821_envelopes = yes


content_filter = smtp-amavis:[127.0.0.1]:10024

---

### Post by Koybe on 2008-04-11
Thank you for your anwser, and your actual config file is quite intersting for me. I have a few questions about it :

- Could you explain a bit the client restriction part?
- What's in the "check access" of each type?
- Why reject code are needed? Isn't it a default comportment?

Anyway thanks again for your input.

---

### Post by songshu on 2008-04-11
this setup has basically grown on me over the years, but i'll try to explain from the top of my head

smtpd_client_restrictions is basically who you allow to talk to you to start with, i actually only use it scarsely if i know a friendly guy with a badly configured mail server i want to receive mail from.

for example:
check_client_access hash:/etc/postfix/client_access

you make a file
nano /etc/postfix/client_access

and you put in there

mail.ilikeyou.com OK
mail.ihateyou.com REJECT

just save the file and then do

postmap /etc/postfix/client_access
this will make a hashed db called client_access.db that postfix can read

after that do postfix reload

be carefull what you use in client_restrictions because if you block people there they will not be able to say HELLO to you in the first place.

the other ones i have

/etc/postfix/regexp_access
/[%!@].*[%!@]/ 550 Sender specified routing is not supported here.


/etc/postfix/access
[email]user@songshu.org[/email] OK

/etc/postfix/sender_access
"fakeemail@fakedomain.com 550 No Spam Accepted"
"fakedomain.com 550 What kind of bogus address is that?"
[email]root@host.myfakelocalboxdomain.net[/email] OK
monit@host OK

/etc/postfix/header_checks
# This will block 8 non ascii characters in a row, which shouldn't be in the
# header anyway according to the RFC... Japan and Chinese spammers...
/[^[:print:]]{8}/ REJECT

/etc/postfix/body_checks
/^(.*)name="(.*). (com|vbs|vbe|js|jse|exe|bat|cmd|vxd|scr|hlp|swf|mpeg|mpg|mov|$

there is a lot of things you can do to customise it to your needs and there's lots to be found on the net, its always a trial and error to find out what works best or your situation,

you mean the ?
unknown_hostname_reject_code = 554
unknown_client_reject_code = 450

uhhhhm, they have been there for years and they never bothered me ;)

---

### Post by Koybe on 2008-04-11
OK nice. I'll have a closer look at this in coming days. I know that there are many informations on then net but that's also a bit confusing to see so many different approach. ;) 
I don't really want a too restrictive environment in production and as test it's nearly impossible to simulate a real spam loaded server.

---

### Post by songshu on 2008-04-12
i know what you mean, but just remember this.

if people will get a response from your mail server that mail is being refused they wil complain right away.
if people receive too much spam they will complain right away.

complaining is good, this means you know where to change something to make people happy and it will make you look good.

what you need to worry about are the e-mails that end up being accepted by the mail server but never show up at the recipient, these are dangerous because people will find out but it while take a long time before they find out that it is you who stole there e-mail, and thats not the position you want to be in.

make sure you are comfortable with the mail delivery itself first and you know the flow of the system before you start filtering mail, and when you do take plenty of time just to watch 
tail -f /var/log/mail.log and grep something /var/log/mail.log
i still do for about an hour every once in a while.

my first mail server i used this as my guideline, its slightly outdated and based on FreeBSD, but its a great resource with a lot of explanation of all the filtering rules described.

[http://www.littlewhitedog.com/content-72.html](http://www.littlewhitedog.com/content-72.html)

---

### Post by songshu on 2008-04-12
p.s.

what do you mean exactly with "Mail filtering gateway" ?
is this box supposed to receive e-mail and then hand it over to another box where youre users can reach it? or wil you have your mailboxes on the same machine?

---

### Post by Koybe on 2008-04-12
I mean just filtering, there will be no mailbox on this gateway. Just a smtp forwarding to internal smtp/mailbox. 

WAN <-> Postfix filtering SMTP DMZ <-> Exchange LAN clean at 95% or more...

And Yes, I already took a lot of time checking the logs. Really instructive.

---

### Post by songshu on 2008-04-12
the reason i asked is because i'm planning to re-do my mail setup in the next 1 to 2 weeks or so.

at the moment i have a pretty simple set up with postfix + dovecot on 1 single box handling the mail for a single office.

i want to change it to a similair set up, more because i want 1 SMTP gateway to distribute the mail to 6 different LAN mailservers, but this would include the initial filtering at the SMTP gateway offcourse so i would be more then happy to learn about your findings as well.

i keep my notes on [http://songshu.org/doku](http://songshu.org/doku)

just drop me a mail on randall@domainabove

p.s.

mag ook in het nederlands ;)

---

### Post by Koybe on 2008-04-12
Ok, anyway i do have a simple unique mail server internaly... not six ;) But if it's all for the same domain, the only way you can forward to the good mail server is using username. I don't know how to do this simply using smtp. It means relaying to different server based on username instead of domain.

Edit:  Sorry, I don't speak dutch :p

---

### Post by songshu on 2008-04-12
yep,

i have several domains and all accounts for all domains are spread out of these 6 mail servers, so i'm planning to throw in some openldap in the mix together with a fallback MX.

but the initial spam filtering on the gateway should be about the same

---


---
title: "Sendmail not excepting inbound emails"
date: 2008-05-17
forum: Server Platforms
---

### Post by runatyr on 2008-05-17
Hello:
I just installed 8.04 and I can get sendmail to send out emails.
However...whenever I attempt to send an email to the ubuntu box. It does not accept the email.

I have started a protocol sniffer Wireshark and watched on port 25.
I see the inbound request come in (SYN) and every time the next immediate packet out is a reset (RST) from the Ubuntu box.
I also tried to telnet to port 25 on the server.. and that meets the same fate

I have not configured ipchains/tables and i also checked that ufw is disabled.

What could be blocking the communication? Especially since it is one way. I know the box can send out emails.. it just wont accept incoming

Thanks !
-Runatyr

---

### Post by yoda2031 on 2008-05-17
> **runatyr said:**
> Hello:
I just installed 8.04 and I can get sendmail to send out emails.
However...whenever I attempt to send an email to the ubuntu box. It does not accept the email.

Ok, so a problem with incoming emails...
> **runatyr said:**
> 
I have started a protocol sniffer Wireshark and watched on port 25.
I see the inbound request come in (SYN) and every time the next immediate packet out is a reset (RST) from the Ubuntu box.
I also tried to telnet to port 25 on the server.. and that meets the same fate

You seem quite knowledgeable, but I can't see why you're using a sniffer to troubleshoot...
> **runatyr said:**
> 
I have not configured ipchains/tables and i also checked that ufw is disabled.

Firewalls wouldn't cause a RST response anyway, I thought they just dropped illegal packets...
> **runatyr said:**
> 
What could be blocking the communication? Especially since it is one way. I know the box can send out emails.. it just wont accept incoming

Thanks !
-Runatyr


Ok, aside from those individual responses... a more blanketed approach now:

If you're using telnet to troubleshoot, do you have a telnetd on the box and is it configured to listen on port 25?

I thought sendmail was -just- outgoing emails, and you need something like dovecot to receive emails.  Correct me if I'm wrong...  I'm not big on email technology (only found out recently that SMTP stands for "simple mail transport protocol" and not "secure mail transport protocol" - a big boo boo on my part which caused quite a lot of embarrassment for me as I was in tech support when I made the mistake and was corrected by a customer... oops!)

Anyway, I'm not sure of the technical difference and what an MTA/MTU/MDA/MDU/MDMA is (yes, a few of them are jokes because there really are a ridiculous amount of acronyms surrounding mail programs and they are just as baffling to newbies when expanded as when condensed!) but I do know that my box never received emails when I was using just postfix or sendmail, and it does now that I use dovecot and sendmail.  (postfix confuses me)

I hope I was at least partially helpful.

---

### Post by solcott on 2008-05-17
@runatyr
Try taking a look at the suggestion in this post.
[http://ubuntuforums.org/showthread.php?t=338646](http://ubuntuforums.org/showthread.php?t=338646)

@yoda2031
> **yoda2031 said:**
> ...
I thought sendmail was -just- outgoing emails, and you need something like dovecot to receive emails.  Correct me if I'm wrong...  I'm not big on email technology (only found out recently that SMTP stands for "simple mail transport protocol" and not "secure mail transport protocol" - a big boo boo on my part which caused quite a lot of embarrassment for me as I was in tech support when I made the mistake and was corrected by a customer... oops!)...
Things are coming in and going out by SMTP, it handles moving mail between servers.  Dovecot or other POP/IMAP daemons handle moving the mail from a server to a client, and it's actually possible to host a mail system without having POP or IMAP access available to be lighter on resources (I do this myself getting mail via a webmail script directly from home directories)

---

### Post by runatyr on 2008-05-17
Ok Thank you for your reply. I installed Dovecot but its still not working. 

You did however get me thinking about telnet. Since i was using telnet on port 25... i technically don't need the telnet service on Ubuntu. I'm basically talking to the MTA with telnet... but on the MTA port.

And as mentioned before... it knocks it down immediately (The wireshark shows that there is NO negotiation in the protocol.

[B]This made me try to run telnet on the Ubuntu box itself and connect to localhost on port 25. 
That Did get me a reply... so it points more again to something in Ubuntu is not wanting to allow anything outside of the system itself to use port 25.[/B] 

**What would be blocking an external machine from talking to it on port 25? Could it be the permissions senmail is running as??**

---

### Post by yoda2031 on 2008-05-17
> **solcott said:**
> @runatyr
Try taking a look at the suggestion in this post.
[http://ubuntuforums.org/showthread.php?t=338646](http://ubuntuforums.org/showthread.php?t=338646)

@yoda2031

Things are coming in and going out by SMTP, it handles moving mail between servers.  Dovecot or other POP/IMAP daemons handle moving the mail from a server to a client, and it's actually possible to host a mail system without having POP or IMAP access available to be lighter on resources (I do this myself getting mail via a webmail script directly from home directories)

Thanks, I asked to be corrected if I was wrong :)

Like I said, I have a very basic knowledge of email protocols.

I would like to know how to do what you describe, actually, since I have little use for POP support...
TIA

---

### Post by solcott on 2008-05-17
Just out of curiosity, is there a certain feature of Sendmail that you need to use that would void other MTA's of being a usable alternative?

If what you really need is just something that will do the sending and receiving of mail, maybe try stopping sendmail and installing Postfix or EXIM just to see what happens.  Getting Postfix up and running is pretty straightforward, and maybe it would work for you with a lot less effort, if anything just to see what happens to determine if you have a hardware problem (eg. an ISP or some problem out of your control blocking 25) or a software problem (eg. something wrong with the sendmail configuration)

---

### Post by runatyr on 2008-05-17
solcott:

Thank you for the suggestion on the existing post.
I did as followed there (It was not exact but i see what he was aiming for)
I had the follwoing lines

FEATURE(`no_default_msa')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl

# CMN changed per Ubuntu [http://ubuntuforums.org/showthread.php?t=338646](http://ubuntuforums.org/showthread.php?t=338646)

#DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl

DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, Addr=::1')dnl

# CMN changed per Ubuntu [http://ubuntuforums.org/showthread.php?t=338646](http://ubuntuforums.org/showthread.php?t=338646)

#DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=127.0.0.1')dnl

DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission1')dnl
dnl #


However after making these changes I did a senmailcfg and got the following errors 

Creating /etc/mail/submit.cf...
Informational: confCR_FILE file empty: /etc/mail/relay-domains
Informational: confCT_FILE file empty: /etc/mail/trusted-users
Updating /etc/mail/access...
Updating /etc/mail/aliases...
/etc/mail/sendmail.cf: line 296: service "submission1" unknown

Warning: These messages were issued while creating sendmail.cf
        make sure they are benign before starting sendmail!

Errors in generating sendmail.cf
*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`always_add_domain')*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`allmasquerade')*** ERROR: FEATURE() should be before MAILER()

Reload the running sendmail now with the new configuration? [Y]
Reloading sendmail ...


and still i get the RST from the box

Any ideas what i may be missing?

---

### Post by runatyr on 2008-05-17
It needs to be sendmail. I am using this ubuntu system to compare it to a RH system we have and I need to mimmick what we have on the RH system

-C

---

### Post by solcott on 2008-05-17
> **yoda2031 said:**
> Thanks, I asked to be corrected if I was wrong :)

Like I said, I have a very basic knowledge of email protocols.

I would like to know how to do what you describe, actually, since I have little use for POP support...
TIA
In a small font because this is off topic and shouldn't get much page real estate:
[SIZE="1"]The easiest way is Postfix+Usermin/Usermin-Webmail.  Create local user accounts and they will be able to receive mail by the default Postfix configuration and install the Usermin package and it will read mail from the users home directory.  The Usermin-Webmail package would be an alternative to usermin because it's basically as reskinned version of Usermin with email usage in mind instead of configuring your user preferences.  If all of your mail is going to be being send from either scripts on the local machine or from the webmail interface you don't even have to bother setting up SMTP authentication.[/SIZE]

---

### Post by solcott on 2008-05-17
> **runatyr said:**
> It needs to be sendmail. I am using this ubuntu system to compare it to a RH system we have and I need to mimmick what we have on the RH system

-C

Try taking a look at this page.
[http://www.feep.net/sendmail/tutorial/](http://www.feep.net/sendmail/tutorial/)

Maybe the Masquerading and Relaying sections.  Other than that, I think I am starting to run out of steam :-|

---

### Post by runatyr on 2008-05-17
You know... the more i wach this thing the more it seems as something is telling it to deny port 25 from external addresses.

I can open a local window... and telnet on port 25 to localhost and it works just fine.

When an external address tries to connect it gets terminated immediatly... none of the sendmail protocol itself gets used (except the fact it is port 25)

What would be stopping that?

---

### Post by solcott on 2008-05-17
Like I said before, I'm about out of ideas, but maybe it's one of the simple but often overlooked problems.

Does your ISP block 25?
Are you are behind a hardware firewall / router that isn't forwarding 25 properly?
Are you on a LAN that uses internet connection sharing? (because if you are, any software on any of the other LAN machines that uses 25 could interfere)
Does ANYTHING else function if you try running it on 25, or is it a sendmail only problem?  EG. try booting from an Ubuntu Live CD and install Postfix, or Apache and run it on 25, or telnetd and run it on 25, or SSH and run it on 25, etc etc.

Finding out if anything can run on 25 in your situation would point you in the right direction, it will tell you if you have a networking issue or a sendmail issue.

---


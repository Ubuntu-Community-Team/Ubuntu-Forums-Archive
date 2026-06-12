---
title: "mail client in command line?"
date: 2007-03-30
forum: Server Platforms
---

### Post by bullgr on 2007-03-30
hi...

i have about a few months ago installed ubuntu 6.06 LTS server on my workplace as file server.

it works perfect... and now i go a few steps further and already make a software raid 1
(ubuntu rok's!!!) with two disks.

i want now mdadm (raid tool) to be able to monitoring and send me a mail alert in any event
happens (resync, fail device). i know how to do that except the mail stuff...

so, my question is, what must i do to send mail from the command line?
is there any mail client? if yes, how can i setting it up? what mail account do i need? (pop, smtp)
can i use gmail, yahoo accounts?

please notice that it's a server install... where is not any graphical X.

thanks...

---

### Post by yabbadabbadont on 2007-03-30
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

For CLI mail clients, two that I know of off the top of my head are pine and mutt.  For the old traditional Unix style "mail" command, there is mailx.

---

### Post by Aberrix on 2007-03-30
mutt & pine

---

### Post by Mr. C. on 2007-03-30
There are many utilities to send mail via command line; which you choose will depend upon where you want the mail to be delivered.

Do you want your server to be the final destination for the email, or would you prefer to have it sent to some other email address ?

MrC

---

### Post by Carlos Santiago on 2007-03-30
You can install an email server, however most of the ISPs will block the emails.
They come from a NOT known mail server so they might be spam!

Because of this, the answer is not in setting a email server.

The answer is in msmtp (sudo apt-get install msmtp)

MSMTP is designed for systems without their own mail servers.

---

### Post by Mr. C. on 2007-03-30
This isn't quite accurate.

Some ISPs block outbound SMTP connections, requiring uses to utilize the ISP's mail servers.

Any system, however, can be configured as in internal mail server for a LAN.  Furthermore, and internal mail server can be configured to relay messages through the ISPs mail server, typically via SMTP AUTH.

MrC

---

### Post by bullgr on 2007-03-31
hi...

thank's for the replies...

i don't want to setup a mail server (even internal) i don't need this...
i want the server to be able to send an email to a specific email address
(perhaps in a gmail account).

in my situation, i want mdadm to be able to send mail alerts in a gmail account.

i will try pine and mutt, but i don't know what will happen if mdadm try to send a mail alert.
will pine or mutt send the mail automaticaly? is any need of a daemon run in background?

because the mdadm command to send mail alerts in a specific mail address is:

mdadm --monitor --mail=root@example.com /dev/md2


this means that any event notified in /dev/md2 device will be send to mail [email]root@example.com[/email]

where is no option in mdadm to specify how to send the mail (pine or mutt or anything else).
it's just try to send the mail to [email]root@example.com[/email]

if i install and configure pine or mutt, will be able mdadm to send the mail automaticaly?

thank's again for the replies...

---

### Post by Mr. C. on 2007-03-31
To forward email to a system, you must have an MTA, commonly called a mail server.

The mdadm program calls "sendmail", which is a binary that transfers email.  That binary comes with Postfix, Sendmail, or Exim.  Without one of these, mdadm will not be able to deliver email.

No sendmail, no mail.  You modify the source code otherwise.

MrC

---

### Post by rsermilik on 2007-04-01
Is workplace where you get paid to work or is it just a room at home?

If its where you get paid to work you can use a simple MTA like SSMTP to relay mail through your company mail server. Of course you can also use Postfix for that. But its depending on how the company mail server is configured.
Does the Company ISP allow outgoing mail directly from their customers? If yes then just use a default Postfix using DNS to send mail. If not, configure Postfix to relay mail through the ISP's outgoing mail server.

At home its the same. But I don't think your ISP allow outgoing mail from private users.
What kind of mail-client do you use on your home PC? If its clients like Outlook (express), Evolution, KMail ..... take a look in the configuration for outgoing mail. Postfix, SSMTP or whatever you decide to use shall be configured the same way.
In fact all mail clients (not webmail) use smtp for outgoing mails and therefore have a simple mta functionality build in.

---

### Post by Mr. C. on 2007-04-01
> **rsermilik said:**
> 
In fact all mail clients (not webmail) use smtp for outgoing mails and therefore have a simple mta functionality build in.

This is incorrect.  Many business solutions, such as Outlook / Exchange or Lotus Notes, do not use SMTP by default; they use proprietary protocols.  While they have SMTP connectors, SMTP is not their preferred protocol.

MrC

---

### Post by rsermilik on 2007-04-01
I know its not the true but for most programs used at home its nearly true. My point was to push bullgr in a direction to find solutions to solve his problem.

---

### Post by bullgr on 2007-04-02
hi...

thank's for the replies.

i go one step at time because this is all new to me...
first i try to configure postfix to be able to send mail thru the local network.
after that i will try to send outgoing mail thru the ISP mail accout.

thank's again...

---

### Post by rsermilik on 2007-04-02
bullgr,

When testing and perhaps in production remember the following in /etc/postfix/main.cf:

disable_dns_lookups = yes
relayhost = [ip of company mailserver]
  or
relayhost = [ip of provider outgoing (SMTP) mailserver]

If you need to specify a specific port to connect to use :portnumber after last ] on relayhost

If you are allowed to do your own SMTP out of the providers network you must disable the 2 lines above in main.cf

/rsermilik

---

### Post by andrew.46 on 2007-07-23
Hi,

 Saw someone mention Gmail and mutt:

> **bullgr said:**
> i don't want to setup a mail server (even internal) i don't need this...
i want the server to be able to send an email to a specific email address
(perhaps in a gmail account).

 Perhaps you could use some of the information I setup on this page:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

               Andrew

---


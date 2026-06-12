---
title: "HOW-TO: Install the right mail server for your needs"
date: 2006-02-18
forum: Tutorials
---

### Post by GTvulse on 2006-02-18
**HOW-TO: Install the right mail server or how NOT to install Postfix**
*Pedro A. López-Valencia*
*[SIZE="1"]python -c 'print "cGFsb3BlenZAZ21haWwuY29t".decode("base64")'[/SIZE]*

Let's suppose you are a web developer and want to set up a LAMP box exclusively for development, and being security conscious, you don't want a Mail Transport Agent (MTA) running in your system. Not only you would need to take care of firewalling the thing but you would also have a drain of system resources, even if a small one.

Yet, when you install a server such as MySQL or Postgres, the dependency  system will pull in Postfix. This kind of server needs some mechanism to report its status and errors to the administrator and the mail subsystem is the logical choice. It seems it is a catch-22, you want MySQL but you don't want a full blown mail server!!! You remove Postfix, and off goes your very needed database as well.

That is not the case, properly packaged Debian pakckages depend on *mail-transport-agent* and it so happens that postfix is the default in Ubuntu's system configuration files. You can install other mail server if you do it ***before*** you install the other applications that pull in a mail server.

You have plenty of choices after you enable the Universe repository, depending on your needs and previous knowledge of the application: 

[LIST]
[*]courier-mta
[*]esmtp-run
[*]exim (version 3)
[*]exim4
[*]hula-manager
[*]masqmail
[*]nullmailer
[*]postfix
[*]smail
[*]ssmtp
[*]xmail
[*]zmailer
[/LIST]

If you don't want a full blown MTA, there are several relay-only MTAs in the list above, namely:

[LIST]
[*]esmtp-run
[*]masqmail
[*]nullmailer
[*]ssmtp
[/LIST]

I won't go into explaining how to use each of them here, but I will give you a recommendation: [font=monospace]esmtp-run[/font] is a very powerful and flexible relay-only MTA that works uploading email to a real server you are authorized to use and has a very simple configuration file. It can handle SSL and PKI authorization if needed. It can use procmail for local delivery (installed by default in Ubuntu Breezy, part of the installation CD in Dapper; mak esure to make it suid root with dpkg-reconfigure) and after you install it you won't miss one single system report sent to root (or your account, if you alias root to send mail to your own usename).

---

### Post by 5-HT on 2006-02-22
Hi, thanks for the thread. Didn't realize you could get around the Postfix dependency like that.

I've noticed that mailx (needs are just for local system mail) is not installed by default in Breezy unlike in Hoary.
I'd like to install it, but am concerned (security and resource wise) because Postfix is a dependency.

The only reason I'd like this app is so that cron mostly, among a few other apps, can send local mail to me about successes/failures.
I have no need for a full-fledged mail server, and would only like Postfix to listen on the localhost.

I'm just wondering if you'd know of any limited MTAs that are easy to configure to listen on localhost only, or if there is an easy way to make Postfix listen on localhost only (sorry, I know absolutely nothing about MTAs)?

After searching around, I came across this tidbit for Postfix to listen only on local:

edit /etc/postfix/main.cf to make 'inet_interfaces= localhost'

Is that all there is to it, or would you have any suggestions for an MTA better suited to my needs?

Thanks for any help

---

### Post by GTvulse on 2006-02-22
I had a similar problem and that was the reason that prompted me to write this how-to in the first place. What I really like about using a relay-only MTA is that it never runs unless you call it to make use of it, no RAM wasted with a daemon, one less posible hole to plug. :-)

What I ended up doing was installing esmtp-run (with all its dependencies), then  mailx and then procmail in that order; I am not sure anymore if procmail is installed by default in Breezy, but in Dapper it isn't.

Then I configured procmail as the local MDA (Mail Delivery Agent) in /etc/esmtprc, in fact I just copied and pasted the right incantation from the esmtprc man page (type "man esmtprc" in a terminal and scroll down, the information is at the end of the man page).

BTW, I removed mailx, because Evolution can read the mail spool directly!!! I  added my account as a mail alias to root in /etc/aliases, and created an account in Evolution that uses "standard Unix mbox spool or directory" and manage it as if it were an IMAP drop box. You can use "standard delivery" and Evolution will move the mail to its locally managed mailbox directories, in a "movemail" fashion if you like it better that way.

---

### Post by 5-HT on 2006-02-23
Thanks for the reply, and the How To for esmtp-run, mailx, and procmail!

[quote= dradul] BTW, I removed mailx, because Evolution can read the mail spool directly!!! [/quote]

Nice! Just wondering about how to configure that...

After configuring esmtp-run, and procmail is it as simple as:
  i. adding something like <username>@localhost in /etc/aliases
  ii. using that address for the evolution account with the "standard Unix mbox spool or directory" option
 iii. entering the mbox path in the configuration wizard for the evolution account (not sure what this would be... maybe /var/mail/<username>...or am I on the wrong track?)

Thanks again.

---

### Post by GTvulse on 2006-02-23
i. No need for @localhost in /etc/aliases. It is the default.

ii. Evolution will need username@localhost, some parser thing in the entry form.

iii. Evolution will give you a form where you enter the path to the mailbox in the form /var/mail/username

That's it.

---

### Post by 5-HT on 2006-02-24
Thanks a lot.

---

### Post by blurp on 2008-10-21
I've installed esmtp-run, now I want to use the "mail" command to send quick emails out. I've installed mailx but it does not use esmtp and gives a Connection Refused error.

Seems like mailx is not esmtp-compatible. Is there another package that provides the "mail" command?

---

### Post by w2vy on 2010-05-14
Is there a simple configuration for my needs?

1) local mail forwarding (local apps sending mail)
2) accept smtp mail from the lan and forward (port 25)

I have nullmailer running now (not esmtp)

The only threads I see that reference nullmailer etc are from a couple of years ago, I assume there is something newer I have missed

tom

---

### Post by GailHard on 2011-10-03
> **blurp said:**
> [...] Seems like mailx is not esmtp-compatible. Is there another package that provides the "mail" command?blurp: mailx is _very much_ esmtp compatible. There are many places on the Net where you can learn how to install mailx over esmtp.

---

### Post by blurp on 2011-10-03
> **GailHard said:**
> blurp: mailx is _very much_ esmtp compatible. There are many places on the Net where you can learn how to install mailx over esmtp.
gailhard: thanks for your reply but it's been three years since that post. honestly i can't remember anything or what i did.

---


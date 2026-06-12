---
title: "How to upgrade postfix/dovecot/spamassassin Email Server from 20.04 to 22.04?"
date: 2023-12-07
forum: Server Platforms
---

### Post by danrancan on 2023-12-07
I am running an Ubuntu 20.04 Server based LEMP Email server running Postfix, Dovecot, Postscreen, and SpamAssassin. I built the server using [this Linuxbabe Guide]("https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu"), and followed the instructions and every single step to the tee.


The included Steps that I took to set up this server are as follows (from the guide):


1) Set up a basic Postfix SMTP server
2) Set up Dovecot IMAP server and TLS encryption
3) Created Virtual Mailboxes with PostfixAdmin (MariaDB/MySQL, PostgreSQL)
4) Created SPF and DKIM record to get through spam filters
5) Set Up DMARC to protect my domain reputation
6) Followed the "7 Effective Tips to Stop Your Email From Being Marked as Spam" tutorial
7) Installed Roundcube Webmail on Ubuntu (MySQL/MariaDB, PostgreSQL)
8) Set up Multiple Mail Domains in PostfixAdmin
9) Blocked Email Spam with Postfix
10) Blocked Email Spam with SpamAssassin
11) Set Up Amavis and ClamAV on Ubuntu Mail Server
12) Enabled and Configured Postscreen in Postfix to Block Spambots


Now I am trying to upgrade my server from Ubuntu 20.04 to Ubuntu 22.04. After Backing up a clone of my server, I used the command `do-release-upgrade` on Ubuntu 20.04 to Upgrade the OS to Ubuntu 22.04. During the upgrade process, I chose to keep all of my old .conf and configuration files when the system upgrade asked me if I wanted to use the new configuration files or the old configuration files for each application.


After the upgrade my mail server no longer works. It neither can send nor receive mail. I am almost certain this is because my configuration files are using the old Ubuntu settings, and not up to date with the updated applications that come with Ubuntu 22.04.


My question is, what files do I have to modify, and what changes need to be made in my mail server to get things working again? Where can I find the change logs for the old versions of postfix/dovecot/postscreen/spamassassin, and how can I tell what changes need to be made to my mail server in order to accommodate for the updated programs? All in all, please provide specific changes that need to be made based on the [Linuxbabe guide]("https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu")] I followed, in order to get my mail server working again on Ubuntu 22.04.


Thanks.

---

### Post by SeijiSensei on 2023-12-07
Is Postfix running? try
```
sudo systemctl status postfix
```
Make sure it starts upon a reboot with
```
sudo systemctl enable postfix
```
After that, we can look at configuration files.

As a start,take a look at inet_interfaces in /etc/postfix/main.cf and make sure it's not limited to localhost.

I don't use Postfix (sendmail instead) so I'm reaching the end of my suggestions.

---


---
title: "dovecot,fetchmail, mailbox location problem"
date: 2009-03-14
forum: Server Platforms
---

### Post by pdc124 on 2009-03-14
i want to pick up mail and put it in ~/Maildir

ive got fetchmail getting stuff from the ISP and it puts it in /var/mail/user.

what else do i need to put the mail as Maildir in ~/ ?

my dovecot config.
oot@server:~# grep ^[A-Aa-z\ ] /etc/dovecot/dovecot.conf | grep -v '#'
protocols = imap imaps pop3 pop3s
listen = *
shutdown_clients = yes
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location =/home/%u/Maildir
mail_privileged_group = mail
protocol imap {

protocol pop3 {
  pop3_uidl_format = %08Xu%08Xv
auth default {
  mechanisms = plain
  passdb pam {
  }
  userdb passwd {
  }
  user = root
dict {
plugin {
root@server:~#    

the user directory 

$ ls -la
total 44
drwxr-xr-x 3 pcy pcy 4096 2009-03-14 22:13 .
drwxr-xr-x 6 root  root  4096 2009-03-14 20:27 ..
-rw-r--r-- 1 pcy pcy  220 2009-03-14 20:27 .bash_logout
-rw-r--r-- 1 pcy pcy 2940 2009-03-14 20:27 .bashrc
-rw------- 1 pcy pcy 8255 2009-03-14 22:13 .fetchids
-rwx--x--- 1 pcy pcy  107 2009-03-14 20:27 .fetchmailrc
drwxr-xr-x 2 pcy pcy 4096 2009-03-14 22:03 Maildir
-rw------- 1 root  root    10 2009-03-14 22:05 .nano_history
-rw-r--r-- 1 pcy pcy  586 2009-03-14 20:27 .profile
-rw-r--r-- 1 pcy pcy    0 2009-03-14 21:05 .sudo_as_admin_successful
$ cd Maildir
$ ls -la
total 8
drwxr-xr-x 2 pcy pcy 4096 2009-03-14 22:03 .
drwxr-xr-x 3 pcy pcy 4096 2009-03-14 22:13 ..
$

---

### Post by windependence on 2009-03-15
You may want to tale a look at a complete mail solution such as Zimbra or Citadel. You can configure a working Citadel server in about 15 minutes.

-Tim

---


---
title: "Postfix, Dovecot POP mail collection"
date: 2012-09-06
forum: Server Platforms
---

### Post by scoutdubna on 2012-09-06
I have a problem with adding User Accounts on my Ubuntu 12.04 server.  The account sets up fine in the home directory, FTP into that area works fine with the user.

I can send email to that user and can view it using USERMIN but I cannot download it using and mail programme, Outlook, The Bat.  Nor can I view it with a web email programme.  The mail files in /home/blister are not being made.

In The Bat I get asked to check the username and password.

Existing user accounts work fine, it is just new ones being added.

Here is the mail log for the connection in this case for user blister

Sep  6 12:41:27 dubnafrance dovecot: pop3-login: Disconnected: Inactivity (auth failed, 2 attempts): user=<blister>, method=PLAIN, rip=192.168.0.18, lip=192.168.0.100
Sep  6 12:47:04 dubnafrance dovecot: pop3-login: Disconnected (auth failed, 2 attempts): user=<blister>, method=PLAIN, rip=192.168.0.18, lip=192.168.0.100

Things seem to have gone wrong following the transfer of mail files from an Ubuntu 10.04 to a new installation 12.04 running in a Virtual Machine on Windows 2008

What am I missing here ?  Can someone tell me where to look please?

CHRIS

---

### Post by SeijiSensei on 2012-09-07
I suspect you have plain-text authorization disabled.  Take a look in dovecot.conf and see what appears at:

```

[...]
auth default {
  # Space separated list of wanted authentication mechanisms:
  #   plain login digest-md5 cram-md5 ntlm rpa apop anonymous gssapi
  mechanisms = plain
[,,,]

```

What mechanisms are listed there?  If plain isn't enabled, add it to the list and restart dovecot. 

Try installing Thunderbird as a client.  When it sets up an account, it will try to use the most secure authentication schemes consistent with the server's configuration.

Also a quick way to check whether plain-text POP3 is working correctly is to make a connection from the command line using telnet like this:

```

$ [color=blue]telnet mailserver.example.com 110[/color]
[stuff]
+OK Dovecot ready <== server's reply
[color=blue]user username[/color]
+OK
[color=blue]pass password[/color]
+OK Logged in.

```

Type the entries in blue; the rest are dovecot's replies. To exit, hold down Ctrl and hit the ] key.  Then type "quit" at the > prompt.

If you ever switch over to IMAP, as I suggest you do, then replace "110" with "143" in the telnet command and replace the "user" and "pass" commands with 

```
[color=blue]1 login username password[/color]
```

If you get logged in, then type "2 logout" and you'll be back to the telnet > prompt.

---

### Post by scoutdubna on 2012-09-07
Thanks for replying, very much appreciated.

The dovecot -n produces the following which appears to show that plaintext is active.

# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-29-generic x86_64 Ubuntu 12.04 LTS


disable_plaintext_auth = no
mail_privileged_group = mail
passdb {
  driver = pam
}
protocols = " imap pop3"
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  driver = passwd
}

I have tried to telnet into the mail server (192.168.0.100) using one of the old accounts and I login fine but if I use one of the new ones eg blister I get the following error-ERR [IN-USE] Internal error occurred.  Refer to server log for more information.

Here is what I find in the sys log

Sep  7 13:37:31 dubnafrance dovecot: pop3-login: Login: user=<blister>, method=PLAIN, rip=192.168.0.18, lip=192.168.0.100, mpid=21218 Sep  7 13:37:31 dubnafrance dovecot: pop3(blister): Error: user blister: Initialization failed: mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/blister Sep  7 13:37:31 dubnafrance dovecot: pop3(blister): Error: Invalid user settings. Refer to server log for more information.The accounts on the former server continue to work normally but not the new ones.

I installed Thunderbird as suggested and it will not let me set up a new account using blister and the message is to check the username and password.

Can you help?

CHRIS

---

### Post by SeijiSensei on 2012-09-07
Usually the inboxes are stored in /var/spool/mail or /var/mail.  Users' mail folders are typically in /home/username/mail.  Why is it looking in /home/blister?  I'd follow up on the "mail_location not set" error.

For instance, on my (CentOS) server, I have:

```
mail_location = mbox:~/mail:INBOX=/var/spool/mail/%u
```

The first entry places the users' folders in /home/username/mail; the second designates where the inboxes are stored.

---


---
title: "SendMail Error: Permission Denied :("
date: 2020-02-21
forum: System76 Support
---

### Post by javierdl on 2020-02-21
Hi all,

Distro: Pop! OS 19.10

Complete error line: 
```

sendmail: cannot log to /home/javierdl/msmtp.log: cannot open: Permission denied

```


I am trying to send Gmail emails from Terminal.


I started by following these instructions: "[How to use Gmail from the Ubuntu Terminal to send Emails]("https://vitux.com/how-to-use-gmail-from-the-ubuntu-terminal-to-send-emails/")"


Steps Summary:
1. Installed msmtp-mta
2. Configured the msmtprc file for Gmail by adding this lines:
```

#Gmail account
defaults
#change the location of the log file to any desired location.
logfile ~/msmtp.log
account gmail
auth on
host smtp.gmail.com
from <yourmail@gmail.com>
auth on
tls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
user <yourmail@gmail.com>
password <your-password>
port 587
#set gmail as your default mail server.
account default : gmail

```


3. Secured the msmtprc file with this:
```

chmod 600 .msmtprc

```
4. Installed heirloom-mailx
5. Configured the .mailrc file:
```

set sendmail="/usr/bin/msmtp"
set message-sendmail-extra-arguments="-a gmail"

```


I have also tried this alternative, from: [How to Send Email from mailx Command in Linux Using Gmail's SMTP]("https://www.systutorials.com/sending-email-from-mailx-command-in-linux-using-gmails-smtp/")
```

set smtp-use-starttls
set ssl-verify=ignore
set smtp=smtp://smtp.gmail.com:587
set smtp-auth=login
set smtp-auth-user=sender@gmail.com
set smtp-auth-password=$EMAIL_ACCOUNT_PASSWORD
set from="sender@gmail.com(sender name)"

```


Command lines I have tried, to send:
1. ```
 echo "Subject: hello" | sendmail recipientmail@gmail.com
sendmail: cannot log to /home/javierdl/msmtp.log: cannot open: Permission denied
sendmail: log info was: host=smtp.gmail.com tls=on auth=on user=sender@gmail.com from=sender@gmail.com recipients=recipientmail@gmail.com mailsize=82 smtpstatus=250 smtpmsg='250 2.0.0 OK  1582300328 c52sm1750529qtb.16 - gsmtp' exitcode=EX_OK

```
2. ```
mail -s "test" "recipientmail@gmail.com"
testing
EOT
send-mail: cannot log to /home/javierdl/msmtp.log: cannot open: Permission denied
send-mail: log info was: host=smtp.gmail.com tls=on auth=on user=sender@gmail.com from=sender@gmail.com recipients=recipientmail@gmail.com mailsize=245 smtpstatus=250 smtpmsg='250 2.0.0 OK  1582300350 x28sm1637814qkx.104 - gsmtp' exitcode=EX_OK
^C
```


Just in case I stopped apparmor to test it
```

sudo systemctl stop apparmor

```
But still made no difference :(


I also tried owning the msmtprc file ([source]("https://www.reddit.com/r/linuxquestions/comments/asjaw4/msmtp_account_default_not_found_no_configuration/egwjmnt?utm_source=share&utm_medium=web2x")):

```
sudo chown my_username ~/.msmtprc
```


Additionally I created a msmtprc directory in /etc/ (as it did not exist) and owned it too:

```
sudo chown my_username /etc/msmtprc
```


I rebooted the computer, and still no go :(

Maybe Gmail is not treating the involved apps as secure applications. I went to my Gmail account to change the [Less Secure Applications Access Settings]("https://myaccount.google.com/lesssecureapps"). But when choosing the purpose of the password, I suppose I choose Mail, and for device Linux computer? I thought I had to be more specific than this. Like, providing the name of the actual app that will be needing the authorization, like msmtp-mta, or mailx. [Source]("https://blog.edmdesigner.com/send-email-from-linux-command-line/"): search for "ssmtp: Authorization failed"

---

### Post by slickymaster on 2020-02-21
*Thread moved to **System76 Support**.*

---

### Post by SeijiSensei on 2020-02-22
Does the service run as a user other than root?  What does "account gmail" mean? Is that the username that owns the msmtp process?

If so, you should probably be writing logs in /home/gmail rather than some other home directory..

---

### Post by javierdl on 2020-02-22
```
sendmail: cannot log to /home/javierdl/gmail/msmtp.log: cannot open: Permission denied
sendmail: log info was: host=smtp.gmail.com tls=on auth=on user=sender@gmail.com from=sender@gmail.com recipients=recipient@hotmail.com mailsize=82 smtpstatus=250 smtpmsg='250 2.0.0 OK  1582388185 i5sm3326029qtq.12 - gsmtp' exitcode=EX_OK



```

[ATTACH=CONFIG]285071[/ATTACH]

I also had myself for Group before, now I was trying adm, but still no go :(. (This text to the left was an hour ago, but I just tried "sudo" for Group too, and when setting up the command line to send, I did use sudo, but to no avail still).

Maybe I should just omit that field in the script (?). After all, the messages are going through.

---


---
title: "Fetchmail IMAP not working"
date: 2009-07-27
forum: Server Platforms
---

### Post by cirobr on 2009-07-27
Hello,

I had my home email server smoothly working for months as per the below thread, which grabs email from an ISP POP server.

[http://ubuntuforums.org/showthread.php?p=6394672#post6394672]("http://ubuntuforums.org/showthread.php?p=6394672#post6394672")

My ISP now offers IMAP. I have adjusted fetchmailrc as per the below file.

```

# Read the ISP accounts every 180 seconds
set syslog 
set daemon 180 

# Configure the ISP accounts
poll imap.terra.com.br with protocol IMAP: 
user "johndoe", password "pass1", is john here;
user "janedoe", password "pass2", is jane here

```

What happens now is that my email remains at ISP server and is no longer being transferred to my home email server. Checking the log by issuing command "tail -f /var/log/mail.log" shows that messages are seen by fetchmail at the ISP IMAP server:

> 
Jul 27 18:38:10 note1-server fetchmail[14794]: 2 messages (2 seen) for johndoe at imap.terra.com.br. 
Jul 27 18:38:10 note1-server fetchmail[14794]: sleeping at Seg 27 Jul 2009 18:38:10 AMT for 180 seconds 


Any help on fixing that is appreciated.

Thanks.

---

### Post by cirobr on 2009-08-06
Any ideas?

Thanks.

---

### Post by cirobr on 2009-08-24
So ?

---

### Post by kgeekworking on 2009-08-24
By default, Fetchmail will only grab unread messages.  The output from fetchmail says that the 2 messages have been seen so they will not be downloaded.

You need to add the --fetchall parameter.

Imap is useful if you want to keep messages both on the ISP server and on your own.  For example if you want to be able to access your mail from outside of your home and use your home for backup.

If you only want to download mail to your home box and not access it from the ISP severs then there is no advantage to using IMAP.  POP is better to download only.

---

### Post by cirobr on 2009-08-25
Thanks for posting a reply. I understand the difference between POP and IMAP. To my application, IMAP just fits.

Unfortunately, Fetchmail IMAP is working exactly as Fetchmail POP:

* With no modification to the posted configuration, new emails are retrieved to my server and flushed from ISP server. Previously read emails are kept at ISP's.

* With --fetchall, all emails are retrieved to my server and flushed from ISP server.

I've tested Fetchmail with two IMAP ISPs, including the new Nokia OVI.

---


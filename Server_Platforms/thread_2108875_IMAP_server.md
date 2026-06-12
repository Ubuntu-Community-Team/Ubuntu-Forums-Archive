---
title: "IMAP server"
date: 2013-01-25
forum: Server Platforms
---

### Post by Oddsodz on 2013-01-25
Hello there.

I Am a little stuck (very stuck really) 
I Have been trying to get a working email server setup on my ubuntu 12.10 64bit. And every time I try one of the hundreds of guide on google, I Seem to fail. Every guide I try is out of date or just fails to work out. Best I have got is being able to send mail from the command line. I Can not seem to get a working IMAP system going. I Have been at this now for about 3 days. I Am noob to Linux. But not so noob as to not be able to setup the likes of nginx and stuff like that.

So with that said.  Can anybody point me to an up to date guide to installing a IMAP server.  I don't wish to have to install things like MySQL and so on.  Just a working e-mail server.

Thanks for reading

Oddsodz

---

### Post by SeijiSensei on 2013-01-25
At a minimum you need a program to accept inbound mail via the SMTP protocol, and one to access the mail from your mailbox with IMAP.  On Ubuntu those are Postfix and Dovecot respectively.  For Postfix, I recommend the [standard documentation]("http://www.postfix.org/BASIC_CONFIGURATION_README.html").  You'll need to edit some files in a text editor with root (sudo) privileges.  Make sure to change the setting for "mynetworks" as described to allow mail to arrive on your machine's Ethernet adapter.  By default, Postfix only listens on the "localhost" interface, 127.0.0.1, for security reasons.

I recommend also installing the mailutils package.  When you've done that, send yourself a message from the command prompt like this:

```
echo 'Is is working?' | mail -s 'testing testing testing' yourname@example.com
```

You should now see that message appear in the file /var/mail/yourname.  That file corresponds to the inbox folder.  If you run "cat /var/mail/yourname" you should see the entire message with headers.

Now install Dovecot as described [here](https://help.ubuntu.com/community/Dovecot).  I recommend the "mbox" format for simplicity.  An mbox "folder" is just a single file with all the messages included; a newline separates each message from the next.

If you need to access the server from someplace on the network, make sure Dovecot is also listening on the Ethernet address.  Uncomment the "listen = *" directive in dovecot.conf to make that happen as described in the documentation above.

Now try both "telnet localhost 143" and "telnet your.ethernet.ip.address 143" to make sure you can connect.  If you allow plaintext logins (see the documentation), then you should be able to test like this:

```

$ [COLOR="blue"]telnet localhost 143[/COLOR]
Trying localhost...
Connected to localhost.
Escape character is '^]'.
+OK dovecot ready.
[color='blue']1 login username password[/color]

```

(Type the lines in blue using your actual username and password.)  If you get back another OK, you're ready to roll.  Type "2 logout" to disconnect.

If you intend to connect over the Internet, you may want more security than plaintext logins.  If you're connecting to a machine on your local network where you're not worried about someone sniffing passwords, then plaintext should be fine.

---


---
title: "Use email message to initiate a script."
date: 2010-03-22
forum: Server Platforms
---

### Post by rmccarri on 2010-03-22
Hi,
I'm considering getting one of those Peek Pronto devices that just does simple email and text messaging.  However, I would like to be able to extend the functionality of it through my server.  Currently, for instance, I have a custom script that runs on my server which uses wget and sed to get scores from an ESPN feed and drops it to a formatted text file that's accessible through the Apache web server.

Basically, what I would like to do is be able to initiate a script via an email message that say downloads some data from the internet, parses it in a convenient way, and then emails it back to the address from which it was recieved.  I know how to generate scripts that would do this and email it back, but where I'm stuck is to how to initiate the script using an email sent from the device to the server.

Is there a way to probe a mailbox from a script and dump the subjects of the email in a text file?  Then I could process the text file and resend an email with the requested information.

Any help pointing my in the right direction would be greatly appreciated!
Rob

---

### Post by HermanAB on 2010-03-22
Google for 'procmail'.

---

### Post by rmccarri on 2010-03-22
Great!  Thanks so much.  That would appear to be the package that I was looking for.

---

### Post by rmccarri on 2010-03-22
Hi,
So since mail for my domain goes through Google Apps, I have to set up fetchmail to get mail from an account I set up and deliver it to the local mailbox so that procmail can apply the proper filters.

I already have my server email me my sql dumps for my web sites through postfix.  To do this, I had to set it up with my ISPs SMTP server through the mail relay settings.

Unfortunately, this means that fetchmail is trying to use this server to deliver the retrieved messages (it's trying to send them to my_username@localhost to my ISPs SMTP server).  Using mail at the command line, I can send mail directly to my mailbox, bypassing postfix.  Does anyone know how to properly configure fetchmail to do this?
Thanks!
Rob

---

### Post by KB1JWQ on 2010-03-22
fetchmail fetches mail.  It doesn't send mail.

You need to define a relayhost in your postfix config.

---

### Post by rmccarri on 2010-03-22
Hi,
Thanks for the response.  I do have a relay defined in my main.cf file for postfix (as mentioned above, that is how I have to have it configured to send myself daily MySQL dumps over email).  It would appear that the way in which fetchmail works is to get the messages from a remote server and then resend them.  If I look at the /var/log/mail.log file, fetchmail is attempting to relay the downloaded messages from gmail through my postfix relay server (my isp's SMTP server), which does no know what to do with the "username@localhost" address.

If I send mail locally through the "mail" command, it works properly if I use "username" as the recipient, but if I use "username@localhost", it tries to relay it through the relay server.  I wonder if fetchmail would work if I could get it to send the downloaded messages to "username" instead of trying to send them to "username@localhost"

---

### Post by HermanAB on 2010-03-22
Fetchmail fetches mail. Sendmail sends mail...
;)

---

### Post by rmccarri on 2010-03-23
LOL..yes, that's true.  I wasn't being precise with my language.  Fetchmail routes the email to your MDA, so technically it isn't sending the message, just rerouting it through another program to get delivered to the proper mailbox.

Nevertheless, I was able to get this to work.  I abandoned getting fetchmail to work properly for a moment and started working on installing an configuring procmail for the other part.  Once I got procmail filtering the email properly, I went back and directed fetchmail to procmail in the fetchmailrc file and it worked properly.  Now I can send an email to [email]info@mydomain.com[/email] with nba in the subject line and it emails the scores back to me!  This will be really handy to make a series of customized reports (like server status or anything else that I want) if I end up getting a Peek Pronto.

Thanks for the help everyone!

---

### Post by KB1JWQ on 2010-03-23
No worries.  I'm glad that you got it sorted out!

---


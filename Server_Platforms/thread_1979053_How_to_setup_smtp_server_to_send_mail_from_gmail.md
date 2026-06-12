---
title: "How to setup smtp server to send mail from gmail?"
date: 2012-05-12
forum: Server Platforms
---

### Post by mnwaterbug on 2012-05-12
I have Exim version 4.71 on Ubuntu 10.04.3 LTS server.

Exim properly sends mail from the command prompt, e.g.: 
# mail [email]person@company.com[/email]
it uses my DSL provider's SMTP server

I want Exim to send my mail using a mail client that isn't local to the Ubuntu server, but connecting to it through the internet.  From what I've read, I think I'll have to:
* Configure the DSL modem to handle SMTP
* Configure Exim to do SMTP for an authenticated user from the internet

There are a lot of businesses selling SMTP server access, so this cannot be that odd of a thing to do... but I haven't found a concise recipe for the configuration (and probably, extra software) needed to get it working. 

Any help would be greatly appreciated.  Thanks!

---

### Post by rubylaser on 2012-05-12
Personally, I use SSMTP to send email through my Gmail account [like this]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp").

---

### Post by mnwaterbug on 2012-05-12
Thanks rubylaser.  That looks like a good way to have Ubuntu send mail through gmail's smtp, but I'm looking to do something that is basically the opposite.  I want to use a mail client like gmail, outlook, etc., from anywhere in the world to send mail through an smtp server on my Ubuntu server.

---

### Post by lisati on 2012-05-12
Are you looking to host your own email system on your server? If so, it's quite possible to do so, and configure it so you can use an email client such as Thunderbird, Evolution or Outlook. It's also possible to add webmail facilities.

My own email server is based around Postfix, with some other software added to screen for junk and to provide IMAP, POP3 and webmail capabilities.

---

### Post by mnwaterbug on 2012-05-14
lisanti - that's right!  I want to use outlook at home to connect to my ubuntu server at work (through the internet) and send mail using SMTP on ubuntu.  Do you know where I can find instructions to set up the SMTP server?  
 
I'm currently using exim4 and it works well sending mail from the ubuntu server's command line, I just don't know how to configure it to plug into my PC running outlook through the internet.  Thanks!

---

### Post by lisati on 2012-05-14
I used multiple tutorials to get my email system up and running using Postfix. Some information can be found [here]("https://help.ubuntu.com/11.04/serverguide/email-services.html"). The section on "dovecot" will provide you information about providing the functionality to connect using Outlook.

One thing to watch out for is that if your server connects to the internet via a dynamic IP address, you might find that your ISP blocks port 25, which is needed for incoming and outgoing mail. Depending on your requirements, you might also need to take steps to keep your server visible to the outside world when your public IP address changes if you're expecting incoming mail.

---

### Post by sahabcse on 2012-06-11
I have tested gmail smtp relay server in my lab and it has been worked fine, How to document in given below

[Set Up Postfix For Relaying Emails via gmail smtp server]("http://ubuntulinux.co.in/community/index.php?threads/set-up-postfix-for-relaying-emails-via-gmail-smtp-server.205/")

---


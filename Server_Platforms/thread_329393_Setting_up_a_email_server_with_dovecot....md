---
title: "Setting up a email server with dovecot..."
date: 2007-01-01
forum: Server Platforms
---

### Post by eviltwin on 2007-01-01
First of all, I'd like to point out that I currently feel like this ](*,) and therefor if I seem to be rather blunt/rude in this thread then I apologise in advance.

Right, now that I have said that, onto my problem. I would like to setup an email server which fetches emails (via pop3) from my current email account, stores them locally and then allows me to check them from multiple computers using imap. I would like to do this using dovecot for the security reasons and because it has a pretty name. :) Also, I would (ofcourse) like the server to handle me sending emails from my computer that is connected to it and for it to then in turn send the emails onto the usual email server via smtp. If the above needs clarification, just ask :)

The other detail about the server is I would like to be able to add accounts to it with individual email addresses (and possibly email servers) associated with them. The adding of accounts doesn't have to be done through a flashy web interface; I'm an ex-gentoo user and I'm well acquainted with the command line and config files :)

I'm guessing (though I am definitely not a guru on the subject, hence my asking here) that one program will be used to fetch the emails which will then store them in local mailboxes, Docecot will then serve the mail to the imap users from these mailboxes and collect mail that is to be sent out in a mail queue or something. Then another app would send this mail on to the appropriate smtp servers on the internet depending on which person sent it. I have no idea whether this is possible, yet I have been charged with doing this and therefor I guess I have n o choice. Some assemballance of spamfiltering along the way wouldn't be too far bad either, I guess. All feedback is, ofcourse, welcome.

Thanks,

Graham

PS my server is running Ubuntu 6.10, just so you know.

---

### Post by StickyStyle on 2007-01-01
What you are looking for in the mail retrieval part would be fetchmail.  The process would work like this...
1. fetchmail retrieves mail from your pop3 server, once received it hands the mail off to your mail delivery agent.
2. from there the MDA drops the message in your mailstore, be it maildir or mbox.  I would recommend using Maildir.
3. dovecot is running attached to the mailstores, and your mail client reads mail via the IMAP connection.

outgoing mail would go like this...
1. your mail client (like thunderbird) sends the mail to your MTA on port 25, I'll use postfix since thats what i know.
2. postfix receives the mail and sends it off to your configured smarthost, which should be your ISP's server.  from there the mail is off and away.

> 
The other detail about the server is I would like to be able to add accounts to it with individual email addresses (and possibly email servers) associated with them. The adding of accounts doesn't have to be done through a flashy web interface; I'm an ex-gentoo user and I'm well acquainted with the command line and config files

didn't quite get this part, are you speaking about having more that one external POP3 account that fetchmail will deliver to your local server? If so that is just a matter of adding another account to your fetchmailrc file.

---

### Post by eviltwin on 2007-01-01
Ah, thanks for that. Am I correct in assuming that something such as spam assassin would be able to be slotting in somewhere nice like with fetchmail? Also, let me clarify on the sepperate accounts. I have an account with gmail and my dad has one with his company's setup (one man company, so we can do what we want with it within reason). Ofcourse, both our mail arrangements mean that we use different pop3 and smtp servers for our incoming and outgoing mail. If we want to use this imap server for the both of us, it would need to fetch the mail from the two different accounts (from the different servers) then store that mail in our mailboxes. Then, when we choose to send mail, it would need to send the mail via the correct smtp server depending on which one of us sent that particular peice of mail. By "add new accounts easily" what I mean is that if, say, my brother gets a gmail account or an account somewhere else I would like the system to be flexible such that it wouldn't be too much hassle to change a few config files and add an account for him on our mail server. Basicly I don't want it setup so that it would only work for one user or any set number of users, just to be flexible. :)

---

### Post by StickyStyle on 2007-01-02
I'm not a total SA guy, so I can't say from experience but i believe you can setup SA as a content filter right in the postfix config where it runs with postfix, or in your procmailrc file where it gets called with the MDA.  Where exactly you need to put it with using fetchmail, I'm not quite sure...I am under the impression that fetchmail bypasses the MTA, but i can't seem to verify that.

For outgoing mail you can just send the mail though the smart host as mentioned above, you don't normally have to match your outgoing server to the domain in the from header.  Although if the mail domain uses something like SPF (and @gmail.com does), then your mail may get blocked at the recipient server as it would think your trying to impersonate gmail.com.  
The simplest option for outgoing may just be to skip your local MTA all together and have the mail client send outgoing mail through the correct server.  That way you have fetchmail pulling down mail into your local mailstore, and sending mail through your client would work just like it did prior to you setting up your local server e.g. going directly through gmail.com/whatever.com.

As for adding new external accounts, thats no issue with fetchmail, its just another line in the config file :-)

These links should help you in your endeavors...
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)
[http://gentoo-wiki.com/HOWTO_Email_System_for_the_Home_Network#Fetching_Email_External_Sources](http://gentoo-wiki.com/HOWTO_Email_System_for_the_Home_Network#Fetching_Email_External_Sources)

---

### Post by eviltwin on 2007-01-03
ok, so now I'm just a tiny part confused on what things I need to install/configure to do the fetching of mail and the serving of it via imap only. Could you be very specific about the different things I need to install to get mail from, say, smtp.ricepuddin.co.uk to the local mailboxes where it will then be served by dovecot? Thanks.

---

### Post by StickyStyle on 2007-01-05
you will need the following packages -
fetchmail = to download the mail from your existing pop3 accounts
dovecot-imapd = to be your imap server
postfix = to be your MTA

Get postfix and dovecot working first, after that setup fetchmail with the link i posted above.

---


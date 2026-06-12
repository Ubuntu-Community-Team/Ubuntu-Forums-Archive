---
title: "Sharing mail across LAN"
date: 2006-10-02
forum: Server Platforms
---

### Post by MikeWyatt on 2006-10-02
I have two PCs: a desktop and a new laptop.  I want to be able to check my email from either machine, at any time.  Currently, I download mail from my ISP's POP3 server directly onto my desktop PC.  My laptop will not have access to it then, since the messages have been removed from the POP3 server.

I just installed Ubuntu on an old PC (631mhz Celeron w/ 384mb RAM) that I want to use as a mail server.  I have successfully configured fetchmail to retrieve my mail to a local file.  Now I need to figure out how to make this mail available to all the PCs on my network.  I know that I somehow need to setup something like PostFix as an IMAP server that my mail clients can view.

I'm not really interested in setting up my own SMTP server.  I'm fine with continuing to send email via my ISP's SMTP server.  All I want to do is create a shared repository that will use fetchmail to periodically download my mail from the POP3 server.

I'm using Thunderbird as my mail client on both machines.

Thoughts?

---

### Post by mazirian on 2006-10-02
You could export the maildir on one pc to the other using nfs.

---

### Post by MikeWyatt on 2006-10-02
Sorry, I should have mentioned that my desktop is running Windows XP Pro and my laptop dual-boots to Windows XP Pro and Ubuntu.

Could I still export the mail file from the server to both servers, regardless of OS?

If that's possible, it might be a good solution.  On the other hand, setting up an IMAP mail server/repository would make my mail accessible from anywhere, without needing to create custom settings for each machine.  It would also allow me to implement a web front-end.

Most of the tutorials I've found focus on setting up a complete email solution, with spam/virus filters and incoming/outgoing mail capabilities.  I'm pretty new to Linux, so some of the articles/tutorials are over my head, or don't cover my seemingly-simple scenario.

---

### Post by mazirian on 2006-10-02
> **MikeWyatt said:**
> ...On the other hand, setting up an IMAP mail server/repository would make my mail accessible from anywhere, without needing to create custom settings for each machine.  It would also allow me to implement a web front-end...

I think IMAP is preferable.  If you want to be able to access your mail remotely, you will have to deal with all the issues of making the mail server accessible to the outside of your LAN, including making it accessible by IP or domain name (which is tricky if you doing this from home and have a dynamic ip).  If you intend to accomplish this on your windows box, I don't know what to recommend.  You could consider setting up a cheap linux box as a server for file/mail/imap/etc...  There are a lot of tutorials for this sort of thing.  For the most part you can leave out the bits that deal with spam and other filtering if you don't want them.  Just tinker away until you get it working and don't expect to have something you can rely on on the first day if these services are totally new to you.

---

### Post by mazirian on 2006-10-02
Btw, I like Exim4+Dovecot for mail.  Postfix is also an easy setup (a common combo for this sort fo home solution being postfix+courier-imap).  For a web frontend, I have used squirelmail, which is easy, but now use roundcube.  I avoid horde.

---

### Post by MJN on 2006-10-05
Does your ISP support IMAP access to your mail? (many do) If so, try that to see if it's sufficient - they may even provide a webmail access facility too (if you're not going to be taking your laptop everywhere with you).
 
Of course, it's not as interesting as doing the job yourself but if it meets the requirements...
 
As I already run my own mail server I use, and can highly recommend, Dovecot for the IMAP server and Squirrelmail as an IMAP webmail client.
 
Whatever solution you adopt, I would strongly suggest it is put in place with remote access(ibility) in mind as whilst you've only stated you want mail access on your LAN it's only a matter of time... ;)
 
Mathew

---

### Post by Bel_din on 2006-10-05
An easy way around this would be to set one or more of your email clients to leave mail on server then it will be available to the other machines. The last machine to get mail would delete from server.

---

### Post by MJN on 2006-10-05
That's not going to work in practice I'm sure - it would rely on the OP always having to ensure he always uses his 'delete from server' client last.

IMAP has got to be the way to go - POP was never designed to support multiple access from different locations. Furthermore, IMAP goes beyond this what with multiple sync'd folders (e.g. at the most simple level mail sent from one client is visible by all the others).

Mathew

---

### Post by mazirian on 2006-10-05
Setting up your own mailserver is way more fun!  If you have a dynamic IP and/or the smtp port is blocked by your ISP, have a look at dynDNS.org.  If you don't want to do that, you can always fwd all your mail to a gmail account, but than google has it...

---

### Post by keithweddell on 2006-10-05
There are some good HowTo's in the wiki - search by title for Postfix. You may need to mix and match the instructions from various pages.  But these helped me set up a working mailserver with postfix and dovecot.  I then added spamassassin and clamav - search the wiki for MailScanner for the next HowTo (although many seem to prefer Amavdis to MailScanner).

Keith

---


---
title: "for a small office"
date: 2010-09-23
forum: Server Platforms
---

### Post by fun_knights on 2010-09-23
I am very new to the LINUX environment.
And in dire need of information on setting up a small server/client network for a small business of about 25 clients.
 
Regards.

---

### Post by drdos2006 on 2010-09-23
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by scrooge_74 on 2010-09-23
Just depends what you want to do in the network

---

### Post by SeijiSensei on 2010-09-23
> **scrooge_74 said:**
> Just depends what you want to do in the network

Well, perhaps we should ask fun_knights that very question, don't you think?

1)  Will this be a mixed network with Linux, Windows, and/or Macs as the clients?  Will you be running any Windows servers?  Using Active Directory? 

2)  What applications will the users be running?  How well do they co-exist with Linux?  Will you have databases?  Proprietary software? ("Vertical" applications for Windows like a manufacturing system, or integrated accounting packages, may only be happy in a Windows environment.)

3)  What services does the server need to provide?  Shared files? E-mail? An internal web server?  Authentication?  Print or fax services?

4)  How do you plan to enforce security and privacy?  Are there groups of users who will need to share files among themselves while not making them available to others?  (Typically accounting and other critical business information is shared only among senior executives; for instance, the receptionist should probably not be able to read performance reviews.)

5)  How do you plan to manage users' access to the Internet?  Will you need to limit the types of sites they visit?  Will some groups of users have more limited access than others?

These questions just scratch the surface of what we'd need to know to answer your question.  People like me do this for a living; it takes insight and planning to set up a company network.  If you've never done this before, you might want to hire a consultant to work with you during the initial setup.  A company with 25 employees should expect to spend at least $5-10K to design a network from scratch (excluding the actual hardware and software costs involved).

---

### Post by fun_knights on 2010-09-24
Thanks alot guys for the insight.
am actually trying to build a LINUX version of a Windows network, made up of basically;
 
AD, Email, Authentication, Shares, Print and Fax services, an internal web server like you rightly pointed out.
 
using basically word processing, spreadsheets applications; no "specialized" softwares in-view.
 
regards

---

### Post by scrooge_74 on 2010-09-24
Well is this is a do it yourself thing and you aint planning to contract someone you are in for a lot of reading and configuring.

Better start making a proper list of things you want to have and then work through it by asking or reading for every step. That worked for me in the past. 

Also Seiji list is a start you could just answer those questions one by one so you can have a base plan. But first sit down and design what you need to do so you dont have to waste time backtracking latter

---

### Post by snowpine on 2010-09-24
Ubuntu Server is [very well documented]("https://help.ubuntu.com/10.04/serverguide/C/index.html"), however I agree with the suggestions above to come up with a written plan before proceeding.

If you know how to create Virtual Machines (or if you have spare hardware lying around), you can do a "dry run" in a controlled setting before implementing your plan. You can also use this as a "proof of concept" to demonstrate to your coworkers and superiors.

---

### Post by HermanAB on 2010-09-24
Howdy,

The best guru advice I can give you, is to install VMware or Virtualbox on the machine and make each major function a separate VM.  That way, once you have something working, it will keep working when you start work on the next thing.

---

### Post by SeijiSensei on 2010-09-24
> **fun_knights said:**
> Thanks alot guys for the insight.
am actually trying to build a LINUX version of a Windows network

Linux clients, too, or just a server?

> made up of basically; AD, Email, Authentication, Shares, Print and Fax services, an internal web server like you rightly pointed out.

You're looking at setting up 

AD - well there isn't anything exactly like it; you can configure Samba to emulate a domain controller, though depending on your needs you might be better off with LDAP (which I've found to be a pain to configure)

DNS - you forgot to mention this, but you'll need a nameserver to handle requests for both internal and external hostnames and addresses

email - an IMAP server like dovecot with an SMTP server like sendmail or postfix; if you want to scan email for spam and viruses, you might want something like [MailScanner]("http://www.mailscanner.info/"); or you could opt for something like [Zimbra]("http://www.zimbra.com/")

shares - Samba

print - CUPS

fax - the venerable [Hylafax]("http://www.hylafax.org/content/Main_Page") does a good job; couldn't find it in the Ubuntu repositories, though

web - Apache/PHP; need a backend database in MySQL or (my preference) PostgreSQL?

As you can see, you've got a steep learning curve ahead.

> using basically word processing, spreadsheets applications; no "specialized" softwares in-view

OpenOffice?  Need to share files with people outside the organization who only know how to handle MS Office formats like .docx?  

I presume you're going to be running an accounting application somewhere, no?  On a Windows machine?  What about databases like contacts and customers?  Mailing lists?

What about backups?

---

### Post by R.Bucky on 2010-09-27
Perhaps, ClearOS would work for you?

---

### Post by kgatan on 2010-09-29
If your clients are windows and you use office id suggest a Windows SBS server.

I love ubuntu alot and in many aspecst resent windows but it does really shine busines wise with its exchange features, sharepoint and AD.
It does of course cost money but time is also money.

Maybe ill get flamed for this but i promiss ill change in our business as soon as alternatives are viable that work as well with windows clients. :)

Maybe a combination is recommended?
In our office we now run a linux NAS for storage, backup and windows for exchange/sharepoint/AD.

---


---
title: "help with mail server..."
date: 2007-04-10
forum: Server Platforms
---

### Post by hockey97 on 2007-04-10
Hi I really need help with installing and setup of a mail server system thing.

First off does my mail server need to have a dns domain name in order to be used worldwide??

I have ubuntu 6.10 server ect and I installed postfix, but what I want to do is to get it 

running, like I am planning to script create a php page for my apache2 webserver to provide a 

mail service , like a place to login and check your e-mail using my mail server.

I need to know what I need to have a full mail system like is their a website that explains how 

make a connection to mysql database for login users ect and also have any eqplanation on how postfix runs and how it works.

What I am doing is having a mail server system on my ubuntu 6.10 server that I can make a php page to handel a mail service over the internet. The php page I plan on making custom errors and art like the buttons and page looks ect.

is postfix a full mail server or is it just like a mail transfer peice of software?

I also want to have spam control and anti-viruse on my mail server.

Basicly trying to get professional as possible for the mail server.

I have been searching the fourms and seen alot of stuff on postfix and other modules they recommend however tried installing it but it fails it gives me some error about dependancies ect.

I really need help....

---

### Post by BoneKracker on 2007-04-17
What you really need is to do some reading.  Here is a good place to start:

[http://en.wikipedia.org/wiki/Mail_transfer_agent](http://en.wikipedia.org/wiki/Mail_transfer_agent)

---

### Post by MJN on 2007-04-17
> **hockey97 said:**
> I have ubuntu 6.10 server ect and I installed postfix, but what I want to do is to get it running, like I am planning to script create a php page for my apache2 webserver to provide a mail service , like a place to login and check your e-mail using my mail server.
 
No need to reinvent the wheel - use something like Squirrelmail as a web-based IMAP client on your server (speaking of which, for accessing your mail you need either a POP or IMAP server (Dovecot, Courier etc) but you'll start to gather all that as you read around...
 
My advice would also to **slow down**. As they say Rome wasn't built in a day and whilst a fully fledged 'mail server' could be you really want to start small and grow. I'd suggest starting with Postfix sending/receiving mail from/to your server along with an IMAP server (I recommend Dovecot) to let a client access the received messages. Then move on to adding the web-based access (Squirrelmail) and adding extra functionality to your setup with anti-virus, anti-spam etc. But don't do it all at once! There're several HowTos that will rush you through doing the lot in one go with excessive copy-and-pasting but whilst at the end of it you'll have a setup that works (as far as the author intended/desired) you won't know *how* it works nor be in any position to fix it when it breaks.
 
Mathew

---


---
title: "Save outgoing SMTP mail"
date: 2008-05-20
forum: Server Platforms
---

### Post by dcostalis2 on 2008-05-20
Is it possible to save all outgoing mail that goes through my smtp server? I don't mind if its saved to a file, or put in a mail folder, or anything like that, as long as I can somehow access it if I need to. 

My full kernel string is "2.4.32-grsec+f6b+gr217+nfs+a32+fuse23+tg+++opt+c8+gr2b-v6.194" if that helps at all. 

Thanks in advance to any insight on this.

---

### Post by dcostalis2 on 2008-05-21
I just re-read this, and let me clarify. I use various webmail clients from computer to computer, and sometimes evolution, and sometimes outlook, but digging through different sent folders to find something is a pain, and especially if its on my windows computer in an office 30 miles away and I want to make sure I did in fact send something. I don't mean tracking every single e-mail that ever gets sent.

---

### Post by dcostalis2 on 2008-05-27
I'll give this one more shot... this seems to be the most knowledgeable forum out there. Can anyone help?

---

### Post by MJN on 2008-05-28
Whilst not a direct answer to your specific question have you considered using IMAP? This will give you a common view of your mailbox (sent and received, and any other folders) regardless of where you access it from - webmail, local clients, etc. Hence, a message sent from one machine will appear in the Sent folder on any other.
 
I think this would provide you with more benefits than getting your MTA to store a copy of each outgoing message.
 
Mathew

---

### Post by windependence on 2008-05-28
I was going to suggest just using webmail all the time instead of POP3 but IMAP is a great idea. Is there any cons to using IMAP over web mail?

-Tim

---

### Post by MJN on 2008-05-28
No, none at all.
 
You are best off viewing 'webmail' as simply a form of e-mail client that happens to be web-based. The underlying supporting protocol just happens to be IMAP usually because webmail has often found its place as a supplement to a users' normal e-mail client e.g. for use when they are away from their own PC etc, and hence a common mailbox view is essential (thus POP3 is no use given it is client based).
 
Mathew

---

### Post by jediborger on 2008-09-21
I have been looking at how one would accomplish this task lately and I'm wondering if anyone has made any headway.

Currently I have dovecot installed on my server and am using getmail to fetch all my various email and save it to a maildir that I access using dovecot's imap server. Now I would like to have a sent mail folder setup through the maildir folder so that I can access my sent mail from where ever I am. Is there a way to set up a smtp server that saves a copy of your email to a "sent" folder before emailing it to the world? AOL does this somehow but I would like to accomplish the same thing on my own server.

---

### Post by MJN on 2008-09-21
The situation you describe is exactly what IMAP provides - identical views of all folders (including sent mail) from all clients.

When you send an e-mail your client will copy this message into the Sent folder and synchronise this with the server through IMAP. These sent message will then be viewable in any of your other clients if they too are accessing the mailbox through IMAP.

There is no need to involve the SMTP server in any of this.

Mathew

---

### Post by jediborger on 2008-09-22
Ok, so then if I use Evolution as my client, what do I enter as my Outgoing server? Currently I've been using the Verizon smtp server but that does not save my sent mail on dovecot. It sounds like you're saying my client should synchronize the local sent mail folder, but in Evolution it only lists an Inbox, Junk and Trash folder under the imap account on my server. Am I missing something or just misunderstanding my issue?

---

### Post by MJN on 2008-09-22
> **jediborger said:**
> Ok, so then if I use Evolution as my client, what do I enter as my Outgoing server?
 
It doesn't matter. Saving copies of sent mail is an IMAP issue, and does not involve the SMTP server.
 
> It sounds like you're saying my client should synchronize the local sent mail folder, but in Evolution it only lists an Inbox, Junk and Trash folder under the imap account on my server. Am I missing something or just misunderstanding my issue?
 
It sounds like a configuration issue. Try creating a Sent folder and ensuring the necessary Evolution setting is set to copy outgoing mail there.
 
Many clients will auto-create 'special' folders if they don't already exist (i.e. Sent, Trash, Drafts, etc - not Inbox because this usually needs to be set by the IMAP server) however it sounds like Evolution does not do this (or has been told not to in the config).
 
Mathew

---

### Post by HermanAB on 2008-09-22
If you wish to have a fancy mail setup, then you need to get a server account from your ISP and run your own mail server.  You should not use IMAP with an ISP mail server, since your mailbox will get full rather quickly.

See [http://www.citadel.org](http://www.citadel.org)

Cheers,

Herman

---

### Post by jediborger on 2008-09-25
Thanks MJN, my issue was a configuration option under Evolution. I had to create a sent mail folder and tell Evolution to save a copy in that folder when it sends an email. Now I just have to remember to do this to every mail client I use.

---

### Post by MJN on 2008-09-25
That's excellent. You may find it is the default behaviour for most clients - I'd always assumed so from the ones I've used.
 
Mathew

---


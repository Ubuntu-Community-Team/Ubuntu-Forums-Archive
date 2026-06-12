---
title: "Email storage / collaboration"
date: 2019-07-04
forum: Server Platforms
---

### Post by andrewgerm on 2019-07-04
Good day all
I'd like to install some collaboration software on my server. What I'd like it to do, is provide email folders, that can be accessed / shared from multiple PC's and email clients. The email can be downloaded from the various external email services by a client, and then instead of being stored in a local file (such as an Outlook PST) they will instead be stored on the server in those relevant email folders.

The client software will do the email downloading, the server will store the messages and provide folders that can be accessed from several machines, and several clients (open Outlook on a Windows desktop, download emails, close that, open a mail client on a Linux laptop, use Thunderbird or such and read those same emails)

The server itself would not send / receive emails.
It would be great to have shared task lists, etc. but that would just be a bonus.

Any pointers as to where to begin / look, would be greatly appreciated.
Most of what I'm finding would have the server send and receive mail

Thanks in advance!!

---

### Post by slickymaster on 2019-07-04
*Thread moved to **Server Platforms**.*

---

### Post by houstonbofh on 2019-07-04
I am not sure exactly what you need, but you can install an imap server that is not pointed to an MTA and just use it for storage.  Can be useful if your primary mail service does not have a lot of storage.

---

### Post by TheFu on 2019-07-04
I use a Zimbra collaboration suite, but it is a full email server in addition to doing the other things you've asked, it has delegation, calendaring, tasks, address books and shared documents.  I have zimbra setup to connect to outside email services, so all those can be accessed, tagged, filtered, using the power of Zimbra.  Zimbra was owned by Yahoo! for some years, so the search and tag capabilities are pretty amazing.  You can share or delegate any folder or other type of "object" in Zimbra. ** It is a hog**, so you won't run this on a tiny raspberry Pi.  **Maintaining a Zimbra server can be lots of work.**  I keep mine off the internet by using an email gateway for all inbound and outbound SMTP.  

You might check out Nextcloud too. There is an email addon for Nextcloud that you can connect to multiple external email providers using.  Next cloud has 50-100 addons for different needs.  Nextcloud can be run on a raspberry pi, assuming you have sufficient storage and can secure it.  My Nextcloud is only accessible on the LAN, so I have to use either a VPN or an ssh-SOCKS proxy to access it when on the internet.

I suppose you could ignore the SMTP parts of any email solution. It isn't like you need to point at it for outbound SMTP (25/465/587) from your clients. Just use the IMAPS/993 interface.

Both could be used to store client-side emails.  I treat email clients as clients. Zimbra is where my clients connect to view email.  **I think you'd have a better chance using Nextcloud.**  Plus, nextcloud has some other really great capabilities.

---

### Post by mastablasta on 2019-07-05
i simply access via IMAP to email services, then you can use any service like you described - gmail, outlook, ISP email...

---

### Post by andrewgerm on 2019-07-05
Awesome!!! Excellent, and thank you all for those suggestions.
I'm going to look into the IMAP and Zimbra.

All I basically want to storage that can be accessed by several devices and client software (which are not file compatible). So IMAP would be the small solution, and Zimbra perhaps once I expand things to include share calendars

Thank you all very much!!

---

### Post by SeijiSensei on 2019-07-05
> The email can be downloaded from the various external email services by a client, and then instead of being stored in a local file (such as an Outlook PST) they will instead be stored on the server in those relevant email folders.

You might take a look at fetchmail, a command-line program that will download mail from remote POP3 and IMAP servers and deliver it to local mailboxes. 

[https://www.linode.com/docs/email/clients/using-fetchmail-to-retrieve-email/](https://www.linode.com/docs/email/clients/using-fetchmail-to-retrieve-email/)

---


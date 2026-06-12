---
title: "mail server"
date: 2008-03-09
forum: Server Platforms
---

### Post by aknight_sa on 2008-03-09
good day guys,

our company is having its mail server on the internet and using pop and smtp to send and receive emails.. 

we are facing lots of problems with it as we always loose connection to it and always have to go through the internet to send and receive local emails which does get devastating at times.

what i want to do is have an email server here locally which can sync with the webmail server we have on the internet so even if we loose connection to the net we can still send and receive emails locally.

any help on archiving such a solution.

Thanks

---

### Post by Mr. C. on 2008-03-09
What type of mail storage are you using currently on the remote site ?

Is it your internet connection that is unreliable, which is causing your mail server connection issues, or is it the mail server host ?

Trying to synchronize a local mail store with a remote mail store is non-trivial.

If your network connection is unreliable, other's will have trouble sending mail to you, and any synchronization will be a challenge.

Please describe your details a little more specifically, especially your current setup.

---

### Post by aknight_sa on 2008-03-09
i dont really know what type of server is being used for our webmail server, but all emails are stored on it and are downloaded to our machines which use any email clients (thunderbird, outlook, ...)

our internet connection aint that reliable as we are at a site where no direct cable connection and are using a GSM HSDPA connection (around 1.8Mbps throughput)

both the internet connection and the webmail server are not reliable.

---

### Post by Mr. C. on 2008-03-09
It will be nigh impossible to synchronize with some email storage server that you know nothing about.

Let's break this into two areas: mail transfer and mailboxes (storage)

Mail Transfer:
It sounds like you want to setup an internal MTA, that either sends mail directly to remote hosts, or relays to some other MTA to do the final work.  There are certain requirements which must be meet to run your own MTA for direct delivery: a) remote hosts must allow your MTA to send (ie. your IP is not blacklisted), b) your ISP must allow your MTA to send.  If these are problems, you'll need to use your ISP's mail servers (or other remote servers that can relay for you).  You must discover what you can do/are allowed to do.  

Furthermore, to run your own public mail server that other's send to (an MX - mail exchanger), your ISP must allow this also.  Most HSDPA EULA's **specifically prohibit** operating an MTA or any full time server; violate this and you will loose your service.  If you are in this category, and likely are, you must not run an MX mail server.

Mailbox storage:
Since your goal is to provide local mailbox storage for your internal users (because your internet connection is unreliable, making their remote mailboxes unavailable), you must move the mailboxes in-house, and use a fetching technique to download the mail to local storage when it is available.  There are several pieces of software (fetchmail, for example) that can do this. 

But synchronization is a different story.  POP provides no such synchronization capabilities.  While you can certainly download remote messages to your local storage, keeping them in synch is problematic for many reasons.

POP effectively supports download & delete, or download (w/out delete) mode of operation.  If you use the former model, the two mail storage servers are by definition out of synch after the first download (and their is no way to put something back).  If you use the latter model, how will you handle, for example, when a local users deletes a message (via their client, deleting the message from the local storage).  What will trigger the deletion of the message on the remote mail storage? 

Since the remote mail storage is out of your control (other than via the trivial POP protocol), you will not be able to accomplish your goal of synchronization.  And while you can fully maintain your own mail storage internally, by the terms of your EULA, and unreliability, you will not be able to provide remote access to those mailboxes from your local storage.

In a nut shell, running a mail server (MTA, MX) and a remotely accessible mail storage requires a reliable network connection.  If mail is critical to your business, your goals are better met with a dedicated network connection, such as a T1 line.

---

### Post by vpsville on 2008-03-09
Please post more details about the webmail software you are using and the MTA you are using.

---


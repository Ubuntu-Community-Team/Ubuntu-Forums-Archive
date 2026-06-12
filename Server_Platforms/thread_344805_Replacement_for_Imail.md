---
title: "Replacement for Imail"
date: 2007-01-23
forum: Server Platforms
---

### Post by Linuturk on 2007-01-23
I've been passed a task by my higher ups here in the office.

They would like a replacement server for our current Imail server. [edit] Note: This server is a **public** mail server. Insurance agencies connect to this machine via POP3 to pull down their email. [/edit]

This server needs the following features:

1. POP3
2. SMTP
3. Webmail Interface
4. GUI Config Tool
5. Virtual Hosts

1. Our members need to access this server using Microsoft Outlook and the POP3 protocol.

2. While we discourage our members to use us for their outgoing mail, (not sure why either) it also needs to handle outgoing email for the select members that are "allowed" to use it. We simply don't tell the others about it.

3. We also need a webmail interface for our members to access their mail. Specifically, when they are away from their office and/or don't have Microsoft Outlook or another email client.

4. I love the command line. The other administrators here have strong Windows backgrounds, and they love point and click. I can't really blame them, because it is easier to train them to use this if they can see pretty pictures.

5. As I said, we host a lot of different members, and their domains. We currently use IMail for this. IMail utilizes a virtual host for the machine, instead of setting up a different IP for each host. [edit] I thought I should clear this up a bit. We don't have to assign a DNS entry for every domain we host email for. The actual mail server takes care of this, and we point all requests to a single IP [/edit]

I'm not to sure on any more specifics that that. Please post requests for additional information if it will influence your decision.

Here is to spreading Ubuntu to my business! ):P

---

### Post by Linuturk on 2007-01-23
I have found a wiki article that seems to be right up my alley.

The only problem is, it isn't complete.

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

Can anyone pick up where that article leaves off?

---

### Post by MJN on 2007-01-24
Your requirement for POP3 access as well as remote webmail access is verging on a being mutually exclusive - you can't really have both for all intents and purposes. The problem being is that POP3 was not designed to support access from multiple places/clients hence the message store is very much client-side.
 
Thus, once your OE client has pulled down all the messages, they will no longer be viewable via the webmail interface (or any other client for that matter). Of course, POP clients can be configured to leave the messages on the server however that is only part of the problem. For messages sent from, say, the OE client will not be viewable from the other clients (e.g. webmail). And any folders created on the local OE client will be similiarly missing.
 
Thankfully there is a solution to all of this and it goes by the name IMAP. It will enable a single view of all mail, all folders etc etc, from somebody's client and webmail. Hence the messages he sent this morning from OE will be viewable when he connects tonight via webmail.
 
Even more thankfully, using IMAP instead of POP3 doesn't really changed your requirements , solution, or operating model (OE supports it) hence should be a no-brainer.
 
My server meets all your requirements bar one - the GUI interface to control it all. Notwithstanding this, it consists of Postfix for SMTP, Dovecot for IMAP and Squirrelmail for webmail. It's a relatively standard combination to be honest.
 
Mathew

---

### Post by Linuturk on 2007-01-24
> Thus, once your OE client has pulled down all the messages, they will no longer be viewable via the webmail interface (or any other client for that matter). Of course, POP clients can be configured to leave the messages on the server however that is only part of the problem. For messages sent from, say, the OE client will not be viewable from the other clients (e.g. webmail). And any folders created on the local OE client will be similiarly missing.

The purpose of the webmail interface in our current layout isn't for constant access to the email. It is there for a member to clear out lots of email that have built up over a vacation. POP sometimes has problems pulling down large or lots of emails. To our members, we are simply the "mailman." After they POP down their mail from our server, it is no longer our responsibility. We aren't in any position to host the thousands of emails someone receives daily, considering we have several hundred seperate email accounts. This is why we make the member POP them down.

I believe I've seen Courier mentioned several times, and it supports POP3. I'm thinking this is a better way to go. I also think OpenWebmail is a more "professional" looking webmail solution.

The biggest thing I want to touch on here is the virtual hosting of multiple domains on one machine. This is a big requirement for us. There isn't any gui based administration tool for this? Could I design my own front end using PHP ?

---

### Post by MJN on 2007-01-24
> **Linuturk said:**
> The purpose of the webmail interface in our current layout isn't for constant access to the email. It is there for a member to clear out lots of email that have built up over a vacation. POP sometimes has problems pulling down large or lots of emails. To our members, we are simply the "mailman." After they POP down their mail from our server, it is no longer our responsibility. We aren't in any position to host the thousands of emails someone receives daily, considering we have several hundred seperate email accounts. This is why we make the member POP them down.

Oh, okay. I guess in that case you stand to gain little by using IMAP then. Quite an unusual setup I must say, but all our requirements are different! Remember, storage is cheap though! (not trying to convince you to change your strategy, it's just that the rest of the world is migrating to IMAP!)

> I believe I've seen Courier mentioned several times, and it supports POP3. I'm thinking this is a better way to go. I also think OpenWebmail is a more "professional" looking webmail solution.

Courier is indeed very popular - never used it myself as Dovecot fits the bill perfectly. Works out of the box too (Courier might well do too).

If using a webmail access to a mailbox, what does the user do with the e-mails? I can understand that they might leave them on the server, ready to download them next time they connect with their 'real' client, but doesn't that go against your intended usage model?[/quote]

> The biggest thing I want to touch on here is the virtual hosting of multiple domains on one machine. This is a big requirement for us. There isn't any gui based administration tool for this? Could I design my own front end using PHP ?

There could well be but I don't use them, but perhaps someone else can recommend one. What's you main requirement for GUI config control? Presumably it's for easy of administration, however is the addition/deletion of virtual domains likely to be that regular a task to warrant the ease of a GUI?

Mathew

---

### Post by Linuturk on 2007-01-24
The main use for the webmail interface is for the user to clear out large emails that won't download correctly via POP3. Or, they use it to access their email when they are out of the office. Most of our users POP3 everything down anyway. 

The gui should have a comprehensive control. From Adding new users, changing passwords, reply to addresses, and adding/removing virtual domains. Considering the other IT guys in the office are Windows Admins, and I won't always be there to handle the cli, we need it to be "easy" for them to pick up on them.

---

### Post by llamakc on 2007-01-24
Webmin is fairly extensible.

---

### Post by Linuturk on 2007-01-25
From what I understand, Webmin isn't officially supported by Ubuntu. What kind of problems will this give me?

---

### Post by Tspiritstorm on 2007-01-29
I just did the same thing as you. We are currently using Imail but I wanted something more stable and more spam resistant. We host emails for several hundreds of small/med size newspapers. 

So I used Postfix/Courier/Squirrelmail/Spamassassin for my setup. While I would prefer IMAP my customers currently use POP3 and store locally using the Webmail features of IMail. So I just changed alot of the Squirrelmail look and feel to make it similar to Webmail from Imail. It wasn't that difficult if you make some slight changes in the /etc/squirrelmail/config_local.php file. 

The nice thing is I feel have a great control over what is going on for my server. I now feel more secure then I did with the bugs in the Imail Server itself.

If you wouldn't mind I would love to hear how your system turns out since you and I seem to be making similar decisions coming from Imail to Linux.

---

### Post by Linuturk on 2007-01-29
Actually Tspiritstorm, I'd like to hear more about what YOU did to get your setup working well. 

Did you find an easy (GUI) way to add new hosts and email addresses?

What version of Ubuntu did you use?

---

### Post by Tspiritstorm on 2007-01-29
I used 6.10 to do the install. Quick and Clean as I knew I would probably install a couple of times just in the mere changes I would make in testing and tweaking. 

As far as a GUI I haven't tried to locate any thus far. I mostly stayed with Terminal for my entire setup. I did install phpmyadmin and have been using that for the Mysql once I had everything built. I have a single domain created thus far under my virtual structure with a single user to test. 

Today I will be looking at creating domains, users, and aliases through both Terminal and phpmyadmin to see if I can make it more efficient. I don't have a ton of experience but I will share any info I can to help you along. I do need a better understanding of Apache so I can configure Host Headers to point to Webmail better.

You can IM me at Tspiritstorm (YAHOO) if you would like.  I find it very cool that you and I are following the same structure.

---


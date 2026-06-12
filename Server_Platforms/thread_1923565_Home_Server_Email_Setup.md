---
title: "Home Server Email Setup"
date: 2012-02-10
forum: Server Platforms
---

### Post by Frozen001 on 2012-02-10
I am setting up a home server, and I would like to have the server handle e-mail utilizing postfix and fetch mail.

I have a domain setup through fatcow, and that gives me a pop-server and smtp server.  

Let me see if I can explain what I want:

I want the server to pull the e-mail off the fatcow servers, and the have my server handle it for all the computers on my network.  I also want to be able to access the e-mail externally via a web-type system such as squirrelmail.  

My internet connection is via DSL.  

Is this possible?  If so can someone point me where to start looking on how to do this?

The server is running Ubuntu Server (was 10.04LTS, but I am running the release upgrade now)

---

### Post by savanna on 2012-02-11
Yes, this is possible.

Use fetchmail to pull down your mail from the pop server and store it on your mail server; config Squirrelmail to serve up those emails. Use postfix to relay outgoing email from your server up to your DSL provider's mail server.

However, assembling all these pieces successfully will require a lot of learning (which may be your goal). If however you just want something "that works", you may be better off starting with an email/groupware distro eg Zimbra, SME Server, ClarkConnect, ...

---

### Post by Frozen001 on 2012-02-11
> **savanna said:**
> Yes, this is possible.

Use fetchmail to pull down your mail from the pop server and store it on your mail server; config Squirrelmail to serve up those emails. Use postfix to relay outgoing email from your server up to your DSL provider's mail server.

However, assembling all these pieces successfully will require a lot of learning (which may be your goal). If however you just want something "that works", you may be better off starting with an email/groupware distro eg Zimbra, SME Server, ClarkConnect, ...

Yes learning is definatly my goal.  I have unsuccessfully attempted to get postfix working with a hotmail account, I figured I would start with an email address that I did not care if I lost the information.

---


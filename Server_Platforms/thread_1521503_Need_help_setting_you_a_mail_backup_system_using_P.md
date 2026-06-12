---
title: "Need help setting you a mail backup system using POSTFIX"
date: 2010-06-30
forum: Server Platforms
---

### Post by Khiron on 2010-06-30
Hello,

Beforehand, I apologize if this has been asked before. I've spent hours trying to find a solution to my problem, but perhaps my approach isn't the best, so I decided to ask.

My problem, or the thing I'm trying to accomplish, is to setup 2 or more mail servers that control the same domain name, but each of them have different accounts. The idea I was having, is that if the username isn't found on the first server, the mail would be sent to the second to be delivered, repeating this process with as many servers in the chain until the mail is delivered, or until the last server is reached and the mail is rejected.

**My setup:**

Ubuntu 10.04 Server Edition
Postfix 2.7.0

**Things I've tried so far:**

- **Setting up the servers with different MX priorities.** The problem with this is that if the first server doesn't have the username, the server immediately answers back with an error and rejects the mail. The secondary and tertiary servers are never reached.
- **Setting up a FORWARD for the domain to the secondary server**. With this, ALL the mail is sent to the secondary server, leaving the local users of the primary server out of the loop. I believe this might actually be the solution, but so far, the things I've tried have failed in the way I just described. Maybe I'm missing a setting I'm not aware of.
- **Explicitly add forwards for each of the accounts found on the secondary server.** This does actually work and its what I'm currently doing, but I have to manually go through the list of usernames found on the secondary server, which may or may not stay the same (such as new users being added on the secondary server without my knowledge). This would be the solution, except I'm going through lists of 1000 or so users, and while I may do it once or twice, it gets incredibly tedious after a while.
- **Banging my head on the desk**. Doesn't work either.

So, I was thinking that maybe my approach isn't correct. Right now, I'm not aware of any options within Postfix that could allow me to do what I need. I've found suggestions that imply the use of FORWARD on the domain, but the local user table is never touched for delivery.

I have full control on both the domains and the servers involved, so any suggestion provided is greatly GREATLY appreciated.

Thanks in advance.

---


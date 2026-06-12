---
title: "Simple Mail Server"
date: 2009-08-13
forum: Server Platforms
---

### Post by Rich-Newbie on 2009-08-13
Hi Everyone

I have been playing with ubuntu server recentley and have attempted some of the tutorials on the how to forge website.

I am attempting to setup a simple mail server. Its not going to have a static ip. The scenario where I want this to work is in a SOHO say max 10 users. The main goal is to provide a way to email each other locally, without having to send it to the ISP, and then the next person downloads. Time consuming and a waist of bandwidth, if there are attachments.

I would want this mail server to download from the ISP mail server via pop3 every 30mins or so, and then distribute the email locally. And then with regards to out going email relay it to the ISP's server.

I have looked at Zimbra, and Citadel. I will still look at testing these in the future, but for now I want something even simpler, and from a learning point of view want to try and go through the stages of setting everything up myself.

From what I have read so far,  I need postfix+dovecot+fetchmail, is it recommended to use mysql? Most of the reviews I have read talk about virtual domains, which allows multiple domain, which is not what I am looking for.

Thanks in Advance
Richard

---

### Post by grantemsley on 2009-08-13
Your plan sounds good.

No need for a database, just create an account for each user.

---

### Post by HermanAB on 2009-08-13
Hmmm, in my experience, there is no such thing as a simple mail server!

However, there are two mail servers that are easy to install: Zimbra and Citadel.  Citadel especially takes only 20 minutes using the Easy Install script.  [http://citadel.org](http://citadel.org)

---

### Post by Rich-Newbie on 2009-08-14
Thanks for the replies. This is a personal project with no time constraints. There are a bunch of tutorials and how to's on the web, I am going to start with the ubuntu Admin manual, and work through things step by step and see how I go.

I am using this as a learning experience. If I get to the point where I can implement Ubuntu Servers for client I will prob go the citadel or Zimbra route.

SBS is a great package from MS, my big issue is the cost, for the type and size of clients that could benefit from a server sbs is to expensive, Foundation the new one looks great, but does not have any form of local email.

My Personal project is to see if I could setup an Ubuntu based sbs equivalent, which would have email, dhcp server, dns server ect. Target market is SOHO clients. I have tried SME server before which is great simple to install, and a web based management interface. My concern is what is something breaks, I need to know how it works in order to fix it, and what better way to learn than try setup something up from scratch step by step.

---


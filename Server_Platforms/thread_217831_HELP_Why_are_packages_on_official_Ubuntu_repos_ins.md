---
title: "HELP: Why are packages on official Ubuntu repos installing MTA's?!"
date: 2006-07-17
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-07-17
OK what is this?

First I try to install rkhunter from the Ubuntu repos a while ago and get saddled with postfix, which opens port 25 to the entire Internet.  Then after installing subversion which I really need for a software project, I got the installation screen for exim MTA which said that leaving it unconfigured would prevent connections to it.  

So I do that, but I now have exim4 opening up SMTP connections to foreign addresses which I have no idea about in netstat.

What is going on? Shouldn't applications from the official repos only run what and when you want them to? 

An application which aims to fix a security hole (rkhunter) by opening an even bigger one is not doing its job correctly.

Should I be concerned about these netstat connections? Guarddog is blocking all SMTP connections either incoming or outgoing (its SMTP box is blank) and last/b shows nothing from a foreign IP address.

---

### Post by Randomskk on 2006-07-17
rkhunter emails you the scan results, so I imagine postfix is listed as a dependency as otherwise it can't send the emails.
Not sure why svn needs exim, as I've never used it.

---

### Post by mannheim on 2006-07-19
> **RavenOfOdin said:**
> OK what is this?

First I try to install rkhunter from the Ubuntu repos a while ago and get saddled with postfix, which opens port 25 to the entire Internet. 

When you install postfix, if I recall, the post-install script puts up a configuration dialog to choose what sort of postfix installation you want. If you select "Local Only" (or something like that) then the smtp server listens  on port 25 only on the loopback interface.

In any event, I think that postfix does not open port 25 to the Internet unless you tell it to. You can check by running "netstat -tl". You will pobably see a line with "localhost:smtp". If you also see a line with "my.internet.address:smtp" then you are indeed open to the internet (though your firewall may be standing in the way).

---


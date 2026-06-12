---
title: "Squid Problems"
date: 2011-09-22
forum: Server Platforms
---

### Post by NetworkLady25 on 2011-09-22
I recently installed Squid on my work server that is running ubuntu 11.04 and I must explain am new at this ...the deal is, I can get to my machine and type in Squid@(myhostname) and i would get a message saying : 
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


How do I add contents to this server .

---

### Post by SeijiSensei on 2011-09-22
> **NetworkLady25 said:**
> I recently installed Squid on my work server that is running ubuntu 11.04 and I must explain am new at this

Perhaps you should first tell us what you're trying to accomplish?  Are you looking to set up a web server?  If so, you need to run Apache2. Take a look at [this]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") and [this]("https://help.ubuntu.com/community/ApacheMySQLPHP").

Squid is a "proxy."  It accepts requests from clients for remote websites and obtains the objects requested subject to various rules ("ACLs").  It isn't a web server itself.

The page you describe is the default home page (index.html) that comes with the Ubuntu implementation of Apache2.  So I'm guessing you have Apache running; the website files are stored in /var/www.  However this directory belongs to the user "www-data" which raises permissions problems if you try to put other content there.  Read the guides above, and search these forums, if you need help with this.

---

### Post by NetworkLady25 on 2011-09-26
I am trying to set up a company Proxy Server , I have Apache yes you right ...!

[B]
"the website files are stored in /var/www.  However this directory  belongs to the user "www-data" which raises permissions problems if you  try to put other content there.  Read the guides above, and search these  forums, if you need help with this.[/B]

I put the web page I created there , permissions were not much of a problem .Thanks for the idea really put me a step further .Will declare this ...SOLVED[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---


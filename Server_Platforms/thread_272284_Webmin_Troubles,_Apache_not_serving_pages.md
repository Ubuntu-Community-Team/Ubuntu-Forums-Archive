---
title: "Webmin Troubles, Apache not serving pages"
date: 2006-10-06
forum: Server Platforms
---

### Post by hosttosucceed on 2006-10-06
I installed the LAMP setup for the 32bit Server Edition of 6.06 Dapper Edition of Ubuntu onto a 3200 AMD 64 1gb ram computer.

I then installed Webmin.

I then tried to do a few of the tutorials from this page [http://rimuhosting.com/support/howtolist.jsp]("http://rimuhosting.com/support/howtolist.jsp")
for instance setting up DNS Servers and Apache server.

I have 10gb down/ 1gb up internet cable service with port 80 open, I have a fully working windows computer and a linux computer(onto which this installation is installed).  The windows computer also had apache 2 installed and serves up web pages just fine. The computers share one IP address, but I figured i would try to set up two Nameservers on the linux computer with the same ip address just to see if it was possible, i then proceeded to configure one of my domains network to succeed, to my name servers ns1.networktosucceed.com and ns2.networktosucceed.com and  the web page could not be served up.  I used the tutorials off of that site to set up the users, and apache virtual server.  But no luck

I then decided to try another site mikeshost.strangled.net and set up an A name DNS data to just point [www.mikeshost.strangled.net](www.mikeshost.strangled.net) to my ip address, a page comes up but it comes up from the windows computer, and that computer is not being configued to display a server for it.  If i turn off apache on the windows computer and leave apache on, on the linux computer, nothing comes up once again.  I have opened all the ports on my router for the linux computer, so everything should be working but im not sure what the problem is.

Again i tried two different ways in the DNS of these domains, nameservers and an A-name, so im not sure what the problem is.

Here is the apache2.conf file: [http://pastebin.ca/192710]("http://pastebin.ca/192710")
Bind conf files, for the nameservers and program: [http://pastebin.ca/192717]("http://pastebin.ca/192717")


If you need any other files to look at my configuration, please post here and ill gladly get them, thanks for the help in advance.

---

### Post by peanut butter on 2006-10-06
i would check where the port is being forwarded. It is most likely the problem.

---

### Post by hosttosucceed on 2006-10-06
Do i check that within ubuntu, if so how and what commands do i use, or configure with apache?

Or do I check it with the router?

---

### Post by Soarer on 2006-10-06
I would think the port is forwarded on the router.

---

### Post by bluefrog on 2006-10-06
Looks like to me to be a dns problem, not apache or whatever.

Is your machine named mikeshost.strangled.net? if not, I don't think you can simply add an A record on your rimuhosting interface.

Try a CNAME instead and see what it does

James

---


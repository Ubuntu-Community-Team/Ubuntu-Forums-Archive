---
title: "sendmail"
date: 2007-10-03
forum: Server Platforms
---

### Post by gishaust on 2007-10-03
Hi peoples, 

Yesterday I got some advice that if  i wanted to run emails from my webpage to another email provider example.gmail.com using php then I would still have to install an email server so I chose sendmail. 

 The install went fine but when I go to start it up it hangs.
After some research I found that sendmail needs a dns point of reference. So I am going through the howto on that. 

I am using ddclient as a way to get dns. for the web server.  in the howto it says to check my host so i type 

host [www.mywebbpage.com](www.mywebbpage.com) 

all i get is the following. 
;; connection timed out; no servers could be reached
I think it is the firewall stopping it get through as ddclient is using port 
80 as well as the webserver.  Is anyone able to tell me which port i need to open when I ask for the host.

Gishaust

---

### Post by gishaust on 2007-10-03
I dropped  the firewall and can get to the host. But what port needs to be open so that this can happen all the time

---

### Post by p_quarles on 2007-10-03
The default port for SMTP traffic (including sendmail) is 25. If you're using an SSL connection (and if you're not sure, you're probably not) it's 465.

---

### Post by HermanAB on 2007-10-04
Note that many ISPs block outgoing port 25 to prevent home users from running spam bots.  So, you may have to relay your outgoing mail through your ISP's mail server - otherwise get a 'server' account for a few dollars a month more.

Cheers,

Herman

---


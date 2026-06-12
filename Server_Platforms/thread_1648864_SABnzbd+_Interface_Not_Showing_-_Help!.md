---
title: "SABnzbd+ Interface Not Showing - Help!"
date: 2010-12-19
forum: Server Platforms
---

### Post by roswell1211 on 2010-12-19
Hi,
Sorry - I don't know which section to post this in.
I have been running SABnzbd+ successfully on 10.04 for a while now. I should be able to access it using the following link :
[http://localhost:8080/sabnzbd/](http://localhost:8080/sabnzbd/)
but I can't. I've checked the config file and the port number etc are correct.
In the last few days I have tried to install subsonic (which I couldn't get working) and ampache (which works great).
I couldn't get subsonic working becasuse I couldn't get it's web interface up either.
In trying to fix it I installed tomcat v6 but don't think I made any other changes.
Does anyone have any idea why my web interface for SABnzbd+ no longer works? The actual service isn't running either. 
I'm a bit stumped. I've searched around on a lot of forums adn can't find anyone else who has the same problems as me.
Anyone even got any idea what to look for?

EDIT : 
I should add the error I get when going to the link above : 
HTTP Status 404 - /sabnzbd/

type Status report

message /sabnzbd/

description The requested resource (/sabnzbd/) is not available.
Apache Tomcat/6.0.24

---

### Post by windependence on 2010-12-19
I don't know too much about Tomcat but I did find this:
 
>  
Tomcat, by default, now ships with the invoker servlet disabled (commented out in the web.xml file). You now need to create a 'servlet' and a 'servlet-mapping' entry in your web.xml.


 
Also, check your file permissions and groups and make sure your document root is correct.
 
HTH
 
-Tim

---


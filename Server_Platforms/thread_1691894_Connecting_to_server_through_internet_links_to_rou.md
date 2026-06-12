---
title: "Connecting to server through internet links to router"
date: 2011-02-20
forum: Server Platforms
---

### Post by F1r3st0rm on 2011-02-20
Hello, I have an Actiontec GT724WGR and I am having problems with my Ubuntu server. I set up a subdomain on freedns.afraid.org with my main computer's external ip. However whenever I use the link that was made it goes to my router configuration page instead of onto my server. I have already set up a static ip for my server enabled DMZ hosting and under port forwarding applied every single rule that applied to servers. This has accomplished nothing and I after scouring the Internet could not find anything to help. Any help would be appreciated and thanks for reading

---

### Post by volkswagner on 2011-02-20
First, you should not set your server in a DMZ.  This opens all ports and is a serious security risk.  You should only forward, needed ports such as port 80 for your web server.

To stop the viewing of your router configuration from outside your LAN, you may have to disable the setting for such.

What you may be experiencing is only from inside your LAN, therefore may be a NAT issue.  Have someone outside your LAN check your site.

---

### Post by F1r3st0rm on 2011-02-20
Ok will try

---


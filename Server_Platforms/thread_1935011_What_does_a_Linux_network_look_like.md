---
title: "What does a Linux network look like?"
date: 2012-03-03
forum: Server Platforms
---

### Post by pepsifx357 on 2012-03-03
Hey all,

I just got through setting up a ClearOS server for work.  We have all Windoze clients, so I set up a domain controller, email, file-server yadda yadda all that good stuff, but that's what a windoze network looks like; My question is...What does a Linux network look like?  I'm sorta waiting on 12.04 before I set up a server, I think that's what I'll be using.

At my house, we all use Ubuntu.  There are no Windoze machines...So, If I'm setting up a server, how would I set it up?  Obviously you need a DHCP server, DNS server, and Web-server..ect, but how is a file server set up for a Linux only network.  Do I use CFS NFS ect.?  How should the computers talk to each other and the server?

Nautilus in 10.04 has a "Places->Network," but I've never gotten it to work.  That may be beside the point.  I don't know.

Do Linux networks use Domain controllers?  They seem pretty handy in a Windoze network. If so, are they set up the same?

I really would like a file server that serves the /home folder, that way I could reinstall at any time.  I would also like to have a local repository, because I play around a lot on Ubuntu.

I'm not looking for specific answers, just a broad overview of how a Linux only network is set up.

Thanks,

Ben

---

### Post by HermanAB on 2012-03-03
NFS is the easiest.  It requires only one line of configuration on the server and one line on the client - quite trivial.  

If you want a directory server, then there are a quite a few to choose from, most of which are LDAP based, but some are SQL based and there is also good old NIS of course.

---

### Post by pepsifx357 on 2012-03-03
Thanks for the quick reply.

I've had bad experiences with LDAP, until I found ClearOS.  What are some of the SQL based options?

---

### Post by HermanAB on 2012-03-03
pam-mysql

---


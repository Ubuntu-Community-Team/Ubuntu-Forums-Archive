---
title: "Apache2 configuration problem"
date: 2013-01-31
forum: Server Platforms
---

### Post by nokem on 2013-01-31
Hello,

Thanks for taking the time to read my post.

I am running a couple home servers that serve various purposes. One of these is an Ubuntu 12.04 server that I recently setup. It is running a fairly standard apache2 server that runs on port 80 and runs an intranet application that I use pretty often. I moved the server over to port 8010 because I wanted to test out lighttpd on port 80. I did this by changing over the values for the listen port, the NameVirtualHost and the port on my <VirtualHost> in the config. Now running on port 8010 and everything is working fine. (I did this by through ports.conf and the /sites-available/site1 config files)

Currently it means that the server is found in a browser under blah1.example.com:8010

What I would like to do is have it so that if I go to blah2.example.com it will send me to the correct port on blah1.example.com **without** changing the address bar. Essentially so that it appears that the two servers running on different ports are different boxes.

I have added a DNS entry for blah2 so that it goes to the same IP as blah1. I am just not exactly sure how to get this forwarding done correctly without a redirect that would change the address bar. 

I realise the problem is a bit strange it's just something I want to fully understand before going forward.

Apologies for the slightly jumbled ramble. Any help greatly appreciated.

Regards

//nokem

---

### Post by volkswagner on 2013-01-31
For the server running on port 80, you will want to setup reverse proxy for other servers running on different machines or alternate ports on the same machine.

I'm not sure how lighttpd requires reverse proxy setup, so I'll leave that research up to you.  Some folks really like having nginx setup as a dedicated reverse proxy because of it's lightweight status, but I'm sure lighttpd will be simple enough to get going.

---

### Post by SeijiSensei on 2013-01-31
> **nokem said:**
> What I would like to do is have it so that if I go to blah2.example.com it will send me to the correct port on blah1.example.com **without** changing the address bar.

The only solution to that is a reverse proxy as volkswagner says.  The address bar simply reports the correct URL for the page, and if the server is running on a non-standard port, then the correct URL is [noparse]http://[[user][:password]@]server[:port]/[/noparse].  That's the standard, and the browser will conform to it.

---


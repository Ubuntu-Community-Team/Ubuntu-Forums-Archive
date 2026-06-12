---
title: "Bind9 or Reverse Proxy for LAN"
date: 2009-05-30
forum: Server Platforms
---

### Post by R.Bucky on 2009-05-30
I host 2 web sites from home using Ubuntu Server. My home network includes my server, a Ubuntu box, and 2 Vista boxes. The problem is that I cannot view either one of my domains internally. They simply time out. This is a long story, but it is caused by not running a DNS from my server. I have ATTEMPTED to configure Bind9 for my domains (using NameBased Virtual hosting with a true static IP) without success. Actually, I have failed miserably. 

Really, all that I want to do is to access my server domains without forwarding my firefox GUI through ssh to my other boxes. Do I need a DNS server internally, or could I go with a reverse proxy with Squid?

Can ANYONE help with either the proper name.conf.local config or configuration of Squid - if applicable? I have been using WEbmin as of current.

---


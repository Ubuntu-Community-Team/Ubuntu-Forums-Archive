---
title: "How to set up a webhosting company using ubuntu"
date: 2009-01-10
forum: Server Platforms
---

### Post by tio2 on 2009-01-10
Hi I am going to start a small business offering web hosting and would like to find out more information on how to set-up and configure ubuntu to host multiple sites. Is this possible and what would I need for this to become reality. I have seen threads on single website hosting but was looking to host multiple domains, a concern of mine is my ISP and how they would feel of me creating a business using a home broadband connection in the UK.
Any feedback would be gratefully appreciated thanks..

---

### Post by sp0nge on 2009-01-10
I can't speak for the UK, but here in the states, the ISPs look down on private users running a business without paying commercial rates. 

An even bigger concern is the bandwidth. Depending on what your customers do with their portion of your servers, the traffic could slow things down considerably.

---

### Post by Thirtysixway on 2009-01-11
I used to host my websites from my home server.  The biggest problem I had was slow download speeds for users because my ISP doesn't provide a high enough upload speed to provide a fast or even average download speed.

You'll want to check the terms of service that goes along with your ISP's internet package, also.

If you want to use apache, you may want to use virtual hosts for each domain name and mod_dir so that users get a public_html folder to put their files in.  You'll also need to worry about the settings for both apache and php and mysql to restrict users from accessing others content and things like that.

You may want to look at something like cpanel, though I'm not sure there's a .deb version of it.

---

### Post by volkswagner on 2009-01-11
[ISPconfig]("http://www.ispconfig.org/") is designed to be used for what you want to accomplish.

The [perfect setup how-to ]("http://howtoforge.com/perfect-server-ubuntu8.04-lts")includes some instructions.

There are too many to list.  But a few you may be interested in....
[With Mail and more]("http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04")
[URL="http://howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04"]
Virtual Hosting[/URL]

---


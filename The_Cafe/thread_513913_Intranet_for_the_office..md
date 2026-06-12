---
title: "Intranet for the office."
date: 2007-07-31
forum: The Cafe
---

### Post by aimran on 2007-07-31
First off I'm a networking noob :P

What I want to do is setup an intranet for my office. My boss saw me using linux and was impressed - he asked me if I can setup an intranet for the office.

We're an engineering firm and we have 2 storage drives (one for documents the other for CAD files) and they're both on a Windows NT server 2003. There's so many files that it's hard to find something you want.

So what my boss has asked me to do is to setup a departmental search page (html) that can also have a daily bulletins and other announcements. This has to be based on Linux.

For ex: You open up your browser that defaults to the local page. You get the daily news (company trips etc) and can also browse to the files on the servers.

Data storage servers <---> Linux Intranet Comp <----> End User

What would I need to do? Is this samba or ? I'm kinda clueless about this :P

---

### Post by Turboaaa2001 on 2007-07-31
I'm an IT Networking Grad, sadly for you I lost interest and decided to forget most of what I learned and go into the PC repair field.

But what you want to do is setup a web server in your office that will hold the local page. It will also have on the page all the links to the Server 2003 that will allow access.

Example:

Marketing opens IE or FireFox and logs onto the web site thats on the web server. The the web server will see that the person is in the Marketing group and will show all the news and links to the marketing files on the Server 2003 machine.

The same goes for the other departments except they get links to the files they need only. Of course it would be better if you setup a domain with the Server 2003 machine and have people log-in through that.

You can create an apache web server with Linux (since Apache is Linux) by using simple documentation. Just make sure you have someone who knows how to create a working page that looks and does what it needs too.

---

### Post by aimran on 2007-07-31
Thank you very much I'll look into that :)

---

### Post by tcpip4lyfe on 2007-07-31
When I was a network admin in that exact same situation I set up a 2003 Active Directory server in a domain. User's would authenticate to the AD server and get their files though drives mapped when they logged in. Marketing peeps would get a D: drive called Marketing.  Sales would get a D: drive called Sales. Then on a separate server (really just an old computer crappy comp), I had Mambo Portal ([http://www.mamboserver.com/](http://www.mamboserver.com/)) for the website.  You set all the home pages to the web server.  Mambo is really easy to manage (I mean insanely easy) and looks awesome..  Check out that link.  You can have a professional looking intranet in about half a day. As for searching for files from the internet site, if your boss really wants that to happen he's going to have to contract that out unless you have a degree in web design. I think reorganizing files to mapped drives is the way to go.

---


---
title: "Help to configure ubuntu &amp; apache to run two virtual servers using 2 diff PHP version"
date: 2019-01-13
forum: Server Platforms
---

### Post by jjhudak on 2019-01-13
I did a clean install of Ubuntu server 16.04 LTS, and the associated LAMP stack,  and have been keeping it updated ever since. I have it configured to run two virtual servers, each server is attached to a different port (I have a service that does redirects to one server or another, based on names).

On one of the servers, I recently removed all the website pages and installed a new set of pages, written in php5.4  When I access the site, I get errors that I think are related to php version incompatibility.

So my question is: how can I configure one of the virtual servers to use php 5.4 (or .6 or .7) and the other to use the currently installed php v7.1?

I assume I’ll have to install php 5.x and somehow inform one of the servers to use it.
 
My biggest concern is that I don’t want to break the existing server that runs with php7, nor do I want to break anything in the rest of the OS.
Pointers to howto docs or step by step instructions are appreciated.
J

---

### Post by SeijiSensei on 2019-01-14
I think you're better off fixing the errors and using PHP 7+.

Can you give us some examples of the errors the code throws when run under 7?  They could just be deprecated functions.  For instance, I used "ereg()" for regular expressions, but that was deprecated in favor of using Perl-compatible regular expressions via "preg()".    I've had to fix things like that for older code, but there haven't been many such problems.

---

### Post by jjhudak on 2019-01-14
> **SeijiSensei said:**
> I think you're better off fixing the errors and using PHP 7+.

Can you give us some examples of the errors the code throws when run under 7? 

The correct way would be to do as you suggest, but, I am not the developer of the php version,  I don't know php or have the time to learn it and refactor the code base.  My goal is just to get it to run in the least painful way possible.

I did use php7mar but got annoyed when the results were presented in a markdown file and I'd have to go through gyrations just to read that. I am doing things stricly from the CL...yes I could change it to html and off load it but.....

Right now, the website runs on a 1u rack blade with other virtual sites and I may just get a RSPi to server this application...but in the mean time, I would like to modify the current server to run it.
Thanks
J

---

### Post by SeijiSensei on 2019-01-15
Well, the problem is that Apache will load the PHP7 module and use it for all sites.  You might be able to rig up a solution using an earlier PHP version in cgi-bin mode that applies only to the site in question, but that's just a guess.  I've only ever used a single module for all sites.

---

### Post by LHammonds on 2019-01-16
I don't know how to accomplish this either.  I had a similar issue with an application that worked on php5 but would not on php7.  I ended up just running the php5 on a different server (but newer OS) and installed the older php5 on it (the default was php7).

Here is how I installed php5 on the newer OS: [http://hammondslegacy.com/forum/viewtopic.php?f=40&t=250](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=250)

---

### Post by SeijiSensei on 2019-01-16
With two machines, you can set up Apache as a proxy for specific virtual hosts that feeds requests back to the second server.  Did you go that route, or just have different servers with different IPs?  Using a proxy lets one machine be the public facing server for all websites, with the second machine behind the public one.

---

### Post by LHammonds on 2019-01-16
I have different external IP addresses.  If I only had one IP, then yes, a proxy would be required to route the traffic.

---


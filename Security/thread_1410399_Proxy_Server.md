---
title: "Proxy Server"
date: 2010-02-18
forum: Security
---

### Post by viper3two on 2010-02-18
Hi
I am really green and new with linux and I am running Ubuntu 9.10 desktop. I work for a company that has about 325 clients. I have been assigned a task to make a proxy server for web filtering (blocking facebook youtube ect). I have never set up a proxy before and I need help getting started with the basic setup. I have installed webmin and started the squid module, then installed squidguard module in webmin. I really dont know what I am doing and I am going to reload Ubuntu and start over. Here is what I am struggling with:
I assume that I want to set up a "transparent" proxy server. Is this right? I just want it to filter and block web traffic, streaming and sites. 

What is best? Squid with Squidguard or Squid with Dansguardian? Or other? 

I am wanting to use webmin. Say if I want to go with Squid and Squidguard, do I install squid and squidguard first, then webmin after, and install the webmin modules for squid and squidguard? Or do I install webmin first, then use the squid module and download-install squidguard via webmin? 

If I can get somebody to steer me in the right direction to install this, I would appreciate it. 
Thanks!

---

### Post by HermanAB on 2010-02-19
Howdy,

You need squid-cache with squidguard or dansguardian.  It is in the repos.  Here is an old guide for manual installation:
[http://www.aeronetworks.ca/squidguard-howto.html](http://www.aeronetworks.ca/squidguard-howto.html)

---

### Post by viper3two on 2010-02-19
Jason and Herman
I appreciate both the replies. This should be enough to get me going on this project. Thanks again for the help!

---

### Post by MontelEdwards on 2010-02-19
Ya know, 
An alternative and a super super easy setup would to just install OpenDNS on all the computers or on the router itself.


Then, you can login to OpenDNS and block specific domains and/or by category.

Its a really nice tool. Oh, and your DNS resovles will probably be a little bit faster also :p

---

### Post by viper3two on 2010-02-20
Does anyone have a preference between dansguardian and squidguard? I want to be able to group clients for various web filters, and also redirect to a page that says they have been blocked. Thanks again

---


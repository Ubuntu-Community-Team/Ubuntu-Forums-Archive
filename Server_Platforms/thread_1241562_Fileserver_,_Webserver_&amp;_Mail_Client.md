---
title: "Fileserver , Webserver &amp; Mail Client"
date: 2009-08-16
forum: Server Platforms
---

### Post by apoklyps3 on 2009-08-16
Hello, i am a newbie to linux and i want to build a server that cand be used as filserver for 3 other PC workstations in the network (all using Windows XP).I heard that Samba can do this. My question is can i allocate space on the server for each user of the workstations in the network to deposit files? Also can the users log in with user/pass on their filespace on the server? Can i also create a common filespace for all the users? Can i make my filserver accessible from the intranet and internet too ? And how?
Now for the webserver, although i know how to install the Lamp suite that is necesary to make a webserver and it runs fine, i have no ideea what to do next. I know i have to buy a domain, but then? what do i do so my webserver is Online. how do i use BIND to make my webserver work?
For the mail client part i want a mail client, that catches e-mails from a account and stores them on server every day.
Hope that some of you advanced users can help me with advices. Cheers.

---

### Post by HermanAB on 2009-08-16
Hmm, either you need to go to the samba.org and apache.org web sites and start reading, or you need to use a distribution that has wizards for all that (Mandriva or Suse for example).

---

### Post by Noah0504 on 2009-08-16
You may be interested in trying something like Webmin or eBox to make the process easier for you since you are newer to Linux.  However, I always recommends buckling down and doing a lot of reading.  :)

Samba will have a default configuration file you to edit.  It's very easy to have private home directory sharing for all users on your server.  So, if you have Joe, Jim and Jane using Windows machines, create them as a user on the server and they will have there own place to store files.  You can also easily make a Public directory for everyone to share files with each other.

The easiest way to have your domain name point to your machine is just setting the A record of the domain name to your IP address.  It always makes things easier to have a static IP address, but you can read up on using a dynamic DNS service.  You won't really have to have a DNS service running on your server if you just use basic port forwarding to point to the services running on your server.

I hope I didn't ramble too much and gave you a little more information to use.

---


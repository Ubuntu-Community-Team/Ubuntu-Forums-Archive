---
title: "Need a file server, and FTP or SSH."
date: 2009-01-10
forum: Server Platforms
---

### Post by jac0117 on 2009-01-10
Hi I have a spare computer that I would like to use as a dedicate file server for the other machines in my network.  I'm not an experience linux user so I would like something really easy to set up, besides I only have one day to do this before I go back to school.

A really good plus would be if there was a way to grab files remotely.  FTP maybe, but I have read that it is not really secure.  I'm planning on having personal documents so maybe SSH would be a better option.

I would really appreciate any suggestions on what OS or program I should use.  Thanks in advance.

---

### Post by whoop on 2009-01-11
Getting everything installed configured and tweaked within a day might be a little far fetched, but you can give it a try :-)

As this being an ubuntu forum I would offcourse recommend ..... ubuntu.

Check out this tutorial: [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
or try another one on this site that better suits your needs.

If you are looking for a really quick and descent fix you could try freenas,org. this is a freebsd distribution tailored for your specific needs.

---

### Post by Iowan on 2009-01-11
SSH is a good option.  [help.ubuntu.com]("https://help.ubuntu.com/") is a good source of information.  Besides setting up a file server, you're gonna need to make it visible on Internet - which will mean port forwarding on your router and (unless you have a static IP address from your ISP) setting up an account with dyndns or no-ip, or something similar.

---


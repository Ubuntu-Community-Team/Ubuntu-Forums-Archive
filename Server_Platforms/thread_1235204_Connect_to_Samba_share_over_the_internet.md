---
title: "Connect to Samba share over the internet"
date: 2009-08-08
forum: Server Platforms
---

### Post by kbates666 on 2009-08-08
I am running my Ubuntu Server with Webmin and a Samba server. I can connect to the share on my local network but how do I access it from my windows and linux laptops over the internet? I have a website currently running and working on my network so I can access my network from the outside.

Thanks
Karl

---

### Post by Vegan on 2009-08-08
Sharing SAMBA over the internet is a security nightmare. First off SAMBA is not configured for internet access only for local traffic.

To set it up resquires a lot more severs than you think. You need authentication and the like.

You are better off installing VSFTPD and use that. Its more secure and easier to setup.

---

### Post by kbates666 on 2009-08-08
Thanks for the recommendation. I will try it and post if I have any problems.

---


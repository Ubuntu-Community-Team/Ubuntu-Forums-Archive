---
title: "Apache: Internal Sever Error"
date: 2006-12-03
forum: Server Platforms
---

### Post by sirhobbit on 2006-12-03
Hi all,
I recently installed ubuntu server using this guide so that I can use it as a web server: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

After setting up the sites in ISP Config I also set up a DNS with Zone Edit, then had the domain name ([www.lawconnect.com.au](www.lawconnect.com.au)) linked to the Zone Edit DNS's. When I use an external network to access [http://www.lawconnect.com.au]("http://www.lawconnect.com.au") I get an 'Internal Server Error'. This also happens when I get my father to access the site so I can rule out an ISP proxy.

Checking out the apache error log I get the following error when trying to access the site:

[Tue Nov 28 01:49:13 2006] [error] [client 220.166.103.17] request failed: error reading the headers

I can access the server from within the network and get the ISP Config web page that states that this IP address is shared. I have the port forwarding set up correctly and outside users can access the site via FTP. Can't see a firewall interfering too.

So I'm basically out of ideas - anyone have any solutions?

Thanks.

Rob

---

### Post by sitedesign on 2006-12-03
Try setting the router with the web servers IP as a DMZ and disable the firewall just to rule out any port forward or firewall issues.

Also let us know what you have configured on the web server, Apache configs, PHP ini, IP set-up etc.

---

### Post by sirhobbit on 2006-12-03
I think I have it working now - there was a hidden htaccess file in the folder. I will have to try it from work this morning to make sure external networks can see it.

---


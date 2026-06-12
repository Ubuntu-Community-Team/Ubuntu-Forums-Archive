---
title: "Creating an intranet on 10.04"
date: 2010-09-02
forum: Server Platforms
---

### Post by Wood Worker on 2010-09-02
Good day,
Very new to Ubuntu and enjoy the product so far.  Installed 10.04 as a LAMP.  I want to be able to create a new intranet site for testing purposes.  

When creating a new site with in apache, what is the recommendation for the folder?  With in the var/www?  Everything appears to want a domain address and since its local only, what do I use as a domain?

Any recommendations would be appreciated.  I have webmin installed and I would think creating a virutual server would be my first step, but I am getting hung up on the domain address.

Again, any assistance would be appreciated.

---

### Post by arrrghhh on 2010-09-02
You don't have to use a domain, and I setup everything in /var/www... but some people prefer /opt.  Just depends, you can really put it anywhere and create a vhost directing Apache to wherever you want the site to sit.

---

### Post by thegaffney on 2010-09-02
Yeah you do not need a domain name,

For the computers in your network to get to the web page, they can type in the servers internal IP address in the internet browsers address bar, or you can change the host file (windows) or the resolv file (linux) so that a fake domain name points to that ip address, would probably be easier to remember that way.


in  /etc/resolv.conf you would add this line
    
     fakewebsite.local  192.168.1.100

and change the first part to what ever you want, and the ip to the servers ip

or in a windows client you would open C:\WINDOWS\system32\drivers\etc\hosts with notepad and add this line
    
    192.168.1.100    fakewebsite.local

same idea

---


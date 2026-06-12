---
title: "Server Client setup"
date: 2012-03-05
forum: Server Platforms
---

### Post by abasel on 2012-03-05
I am wanting to take my students through a basic networking course and would like to do so using Ubuntu.

In windows, we create clients and then get them to join a the domain and manage them via group policies.

What is the process in Ubuntu? I know how to install the server and workstation, I am just not sure where to begin when allowing the two to work together ie. Ubuntu clients to authenticate users and machines on the network using the Ubuntu server...

Not wanting detailed instructions, just a few basic steps that I can go and Google.

---

### Post by pinjan on 2012-03-05
How about using VNC as client to access ubuntu server ?

There are good instructions e.g.here: [http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html")

What comes to managing users, groups etc Webmin seems to do the trick: [http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html]("http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html")

---

### Post by volkswagner on 2012-03-05
I suggest research the following then come back with specific questions.
LDAP, LTSP. SAMBA and SAMBA as primary domain controller.  There is also NFS for basic linux network shares. 
CUPS for printer sharing

---


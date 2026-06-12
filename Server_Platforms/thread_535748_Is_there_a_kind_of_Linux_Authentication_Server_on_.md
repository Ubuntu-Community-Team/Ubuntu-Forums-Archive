---
title: "Is there a kind of Linux Authentication Server on Ubuntu similar to IAS on Win2003?"
date: 2007-08-26
forum: Server Platforms
---

### Post by shellte on 2007-08-26
Hi, guys:

  My boss gave me a big task: to establish a AAA Linux server which is similar to the IAS on win2003. 
 
  Is there an integrate package can work as IAS on Ubuntu? If no, I consider to combine Free Radius, MySQL and Apache together. Can they work as efficiently as IAS?

  But I still have a problem. As we all know, before user authentication we need to have user accounts first. But I have no idea what software on Linux can create, manage and delete user account to MySQL? Do I need to write some PHP codes to do this job through the web page?

  Pls give me some hints. Any suggestions are greatly welcomed.

  Thanks.

---

### Post by southernman on 2007-08-26
It sounds as if your looking for something like OpenLDAP Server. You can read about it [here]("http://http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html")

Hope that gets you close to what you need.

---

### Post by shellte on 2007-08-27
Is the OpenLDAP similar to the Active Directory on Windows? 

And how can I create the user account into the OpenLDAP database? Can I do this through web on the terminal or I have to add users and passwords in the configuration file by text editor like emacs?

Thanks for help.

---

### Post by southernman on 2007-08-27
shellte, in all honesty I couldn't tell you. I just noticed that the link I gave you is broken so here is the proper link to the howto I *tried* to link you to:

[http//doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html")

Even though it isn't much help, it's better than any other replies you've had to this point... ;) jk gang!

---


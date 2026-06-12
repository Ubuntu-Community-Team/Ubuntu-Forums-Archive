---
title: "All Around good security setup"
date: 2009-09-26
forum: Security
---

### Post by dbrine on 2009-09-26
Newbie here. I am looking for an untangle software type setup there I can block/ allow programs/ ports. Web content filtering, spam blocker, etc.

Any suggestions? Currently running 9.04 server

---

### Post by bodhi.zazen on 2009-09-27
What do you want from such an application, what features do you want ?

Linux is modular, so these things are in general one application per task.

You can use iptables or ufw to restrict access / ports.

Take care that your servers are properly configured.

In terms of additional options you can use TCPWrapper - /etc/hosts.allow an d/etc/hosts.deny.

Not every server use TCP wrappers, apache is one exception. For apache you configure in the config files.

Every server has these options in the config file as well.

In terms of content filtering, how is it you need content filtering on a server ?

At any rate content filtering is performed using things such as squid and dansguardian.

If you wish a graphical interface, take a look at webmin, you can manage many things from the webmin control panel.

HTH, or at least gets you started.

If you have a more specific question feel free to ask.

---

### Post by kevdog on 2009-09-27
Isn't webmin dead?  

Just wanted to check on this!

---

### Post by bodhi.zazen on 2009-09-27
I do not use it either, but their home page looks alive and well

[http://www.webmin.com/](http://www.webmin.com/)

> 
**Webmin version 1.490 and Usermin 1.420 released**

  This update includes Catalan, Dutch and Basque translation updates, code fixes to remove Perl warnings, many RAID-related improvements, support for the Debian 5.0 bonding config format, and [much more]("http://www.webmin.com/changes.html"). You can get it from the [Webmin downloads page]("http://www.webmin.com/download.html"), or from our YUM or APT repositories. 
  Also available is a new Usermin release which fixes a bug in the format of HTML messages with attached images, splits the read mail preferences page into sections, and updates the Dutch translation. It can be found on the [Usermin downloads page]("http://www.webmin.com/udownload.html").


Posted September 17, 2009

---

### Post by undecim on 2009-09-29
In general, Ubuntu has a good balance between security and usability. Just make sure you keep constant updates, protect your machine physically (Physical access is root access, no matter what platform you are on), and don't do stupid things (if someone tells you to run a command on your server, make sure you know what that command does).

For web content filtering, if you are going to be letting your children browse the web and want to protect them from the web's major industry, there are several proxy servers that you can install that will do such (though I've never used these much, so i can't help you there...)

To protect yourself from online threats, just use Firefox to browse the web. You can also use the noscript and adblock add-ons (especially if you are browsing the web from a windows computer!) There is likely also an add-on you can find for children's content filtering... 

If you want to make your server even more secure (and who doesn't?) there are a few things I would recommend:

If you use ssh (which you should be doing for accessing your server) set up pubkey authentication: [http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/](http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/)

after setting up (and testing) pubkey authentication, you can disable password authentication by change the line in /etc/ssh/sshd_config that says "#PasswordAuthentication yes" to "PasswordAuthentication no" (Note the remove of the "#)"

and finally, if you have a hardware firewall or router, check the security settings on it including the wireless security settings... you should be using WPA with AES encryption (TKIP encryption has been partially broken) and there should be no ports forwarded (unless you have some set up for online games, or if you would like to access services such as SSH from outside your local network)

---


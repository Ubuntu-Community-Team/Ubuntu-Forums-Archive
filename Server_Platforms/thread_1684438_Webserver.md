---
title: "Webserver"
date: 2011-02-09
forum: Server Platforms
---

### Post by Gh0styuk on 2011-02-09
Hi all

i have just finished setting up a web server for a company using ubuntu server 10.10 64bit and all is working great, but i have just got one problem they are having an internal and external site.

Now the external site is no problem as i have a domain to link it to but as for the internal site can just be gotten to by ip is there anyway i can make it abit cleaner ie not use ip address to show in the address bar of the web browser.

Any help would is great

Kind Regards
Gh0styuk

---

### Post by wongo888 on 2011-02-09
You could add an entry to the /etc/hosts file and resolve an intranet domain that way

[http://manpages.ubuntu.com/manpages/lucid/man5/hosts.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/hosts.5.html)

---

### Post by spynappels on 2011-02-10
Does the company have it's own DNS server? If they do, you can just add an Intranet entry and create an Intranet virtualhost.

---


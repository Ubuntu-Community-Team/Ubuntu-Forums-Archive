---
title: "Apache setup"
date: 2018-11-09
forum: Server Platforms
---

### Post by mwoosley on 2018-11-09
Hello everyone.  I am doing well so far with my LAMP setup but I do have a few questions that I hope you subject matter experts can answer.

1. In the /etc/apache2/sites-available folder, I have 3 site config files there.  One is the 000-default.conf file and the other 2 are my test sites.  In each I have the html folder with an index.html file.  I followed the guidance in the server config for Ubuntu 18.04 and setup the files accordingly with ServerName, etc.  My question is whether or not I can enable ALL of the sites at one time, or must I have only 1 enabled and the 'others' disabled.  

2.  This situation has created a bit of a quandry as I cannot get the phpmyadmin to generate a site for login.  I bet it's quite possible that because I have more than one enabled, it doesn't know which one to open.

I hope your responses will help me understand why certain things are not happening.  In retrospect, it seems as if I SHOULD be able to enable as many sites as I want.

Thanks everyone,
Mike

---

### Post by slickymaster on 2018-11-09
*Thread moved to **Server Platforms**.*

---

### Post by joebeasley on 2018-11-09
You can have multiple sites configured.  Just setup [virtual hosts. ]("https://httpd.apache.org/docs/2.4/vhosts/examples.html")

---

### Post by psd-joshe on 2018-11-12
You can have multiple sites enabled on a single machine. You would just create multiple host filesin your sites-available folder one for each site. Enabling one site does not disable the others. Make sure you reload apache after you enable your new sites(terminal should prompt you to do that also)

keep in mind if you have * or the same ServerName pointing at different directories in 2 different host files that can cause issues.

---

### Post by mwoosley on 2018-11-13
Thanks for your response, but if you wouldn't mind, I need you to elaborate just a bit more on your response.  While I know the use of the /etc/hosts file, I do not understand how to appropriately update this file so that the 'multiple' websites work independently from each other.  For example, I have multiple servers running, all with different names.  The one that I'm concerned with is the one I am adjusting now which is on a physical machine entirely dedicated to Linux.  In the /etc/hosts file, I kind of have the basic info, similar to the Ubuntu Server Guide 18.04.  Then I added my private ip addresses (192.168.1.250 for example) along with my domain name.  I'm not sure if this is correct, or I should place my public ip address there instead.  I haven't had much luck trying to find a tutorial that breaks down the incoming/outgoing functionality of the /etc/hosts file and how it functions with the other server components.  

I think I have a good handle on setting up the virtual host files with a tutorial I found from Digital Ocean.  On the other hand, my lack of knowledge prevents me from knowing how to bring up a 'CERTAIN' website in the browser since my ip address is the same and ALL the different site folders have the same index.html or index.php files.  

I'm hoping that you can help me understand where I'm going wrong with my thoughts.

Thanks

---

### Post by SeijiSensei on 2018-11-14
Apache chooses which virtual site to display based on the ServerName or ServerAlias directives in that host's <VirtualHost> container.

---

### Post by psd-joshe on 2018-11-14
I've never really updated my /etc/hosts file on my web servers before.  could you explain a little what you're tryng to accomplish.

I usually just point my DNS names at the server IP and then let apache handle the directing from there.

---

### Post by SeijiSensei on 2018-11-18
It doesn't matter what's in the server's /etc/hosts. It's the clients that need entries for the various virtual hosts that point to the server's IP. As I said, Apache uses the ServerName and ServerAlias directives to determine which <VirtualHost> configuration to use.

---

### Post by LHammonds on 2018-11-19
Normally, people visit a server because they are using a domain name as part of the URL in the web browser address bar.  This domain name (or even IP address) is what Apache uses to direct people to the correct site (which matches the client's incoming domain name in the URL to the sites "ServerName" in the config file.

This domain name (or IP address if you are not using one) is what is referenced in the apache site config (virtual host).  So if your server is hosting 3 websites (with 3 different domains pointing to the same IP), each site will have a config file in the "sites-available" folder that reference their domain name people will be using to get to that site.  The domain name will be in the "ServerName" directive.

If you are just on a LAN and internal access only, you could setup a local domain name in your local DNS server or you if you do not have one, could just edit each devices "hosts" file to point a name to the server's IP.  This allows you to configure the server like you would on a production site.  Or you can just use multiple IP addresses on the server and use that as each site's name...meaning the client devices would be using the IP address in the domain part of the web address.

There are several ways of accomplishing the same thing but most scenarios involve having people directed to the right site using a domain name...even if it is still part of the same domain, sub-domains can be used such as wordpress.mycompany.com, nextcloud.mycompany.com, video.mycompany.com, etc.

LHammonds

---


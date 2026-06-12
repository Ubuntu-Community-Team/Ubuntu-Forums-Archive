---
title: "Ubuntu Linux server in home and issues setting it up (Advanced)"
date: 2009-12-13
forum: Server Platforms
---

### Post by John Rivera on 2009-12-13
Okay. I have been operating own home server for while now and I like it too much to ditch it :D

However now I am little short of ideas how to do few configuration things that I would like to have.

Apache multiple websites issue.

I would like to have multiple websites served by my Apache web server. By this I mean that each of website is in own directory and you can't have access from one to another.

/serverdirectory/website1
/serverdirectory/website2

etc.

Now I have found some guides, but still need more information.
Specifically I am not sure how I should configure my DNS server since I am new to it, so I got no idea. And that those website would be visible outside of my local network,

What I want is that those multiple website I define are each on own directory and you can't access from one webspace to another with otherwise than writing address of new website when you are directed to it.

This is due to reason that I want to have my public website and subsections of it available to all and then private website for various things that I do not wish to keep public. ie. customer's website template and other things.

ie. I got web address mysite.host.com and I got private website mysite.host.com/anotherwebsite

Also I am thinking that there should be community project (IF There is not one already) for deploying ubuntu server in home to create guides and necessary software needed by such server to control traffic etc.

---

### Post by BkkBonanza on 2009-12-13
I'll try to give you some direction here but what you do depends on your exact network setup. Let's assume you have a router between your server and the internet.

1. Don't bother running your own DNS server. Just use one of the many free ones out there. Use your DNS registrar for example, or if they charge money then try zoneedit or dnssolutions or others. I use name.com, which is pretty nice. There's many and they are better set up to do this than you are at home. There's no benefit to running your own. Just more work, less reliability, and less speed.

2. Config your DNS entries to point to your public IP for your connection / router. If you are on a dynamic IP then config dynamic IP updates on your router as well. For each public subdomain add an A RECORD for your public IP.

3. Configure your router to forward port 80 to your server machine in your LAN. And any other ports for services you need like 443 (HTTPS), or email.

4. Read up and learn to configure using the "VirtualHost" directive in Apache. There are many tutorials around for that and reading the Apache docs also give the info.

5. If you want some private subdomains only in your LAN then the easist way is to add those domains to your router. Usually dnsmasq or DHCP handles this and you can add a few names there that will resolve only for your LAN. Use the local server IP for those ones.

That's a start. Mostly all I can recall off hand now. Probably a few more things to do.

---

### Post by slakkie on 2009-12-13
Look at apache virtualhosts documentation, and you'll need some propper DNS entries

eg

site1.yourdomain.tld
site2.yourdomain.tld

```

<VirtualHost *>
ServerName site1.yourdomain.tld
ServerAlias site1.yourotherdomain.tld
DocumentRoot /var/htdocs/site1
</VirtualHost>

<VirtualHost *>
ServerName site2.yourdomain.tld
ServerAlias site2.yourotherdomain.tld
DocumentRoot /var/htdocs/site2
</VirtualHost>

```

Now have site1 and site2 point to the same IP/host. Restart Apache and done.

---

### Post by John Rivera on 2009-12-13
Okay. I think that I need to clarify a bit of my situation.

My situation is this:

I got solid logical address and my ISP has arranged so that address rivera.wippies.net does direct to my server. (It may be offline or show the "it works" page currently)

Now I would like to get so that rivera.wippies.net works as a main site and is in own directory let's say /var/www/online (As site name is John Rivera online :D)

Now I would also like to have more websites as apache virtual hosts in own directories like /var/www/anothersite and it would appear as rivera.wippies.net/anothersite
for various purposes like developing new sites, and making website design for clients.
I am wondering that is possible to possible to get that done at all. And how to add more virtual host websites.

I am not sure if there is anyone familiar but I got this wippies home box which has quite few nice features etc. more information at [www.wippies.com](www.wippies.com)

---

### Post by BkkBonanza on 2009-12-13
If you want rivera.wippies.net/anothersite to go to /var/www/anothersite then you don't need virtual hosting at all. Just put files for "anothersite" in the /var/www/anothersite directory and you're good to go.

---

### Post by John Rivera on 2009-12-14
Yeah.

That is what I want to archive, but I am wondering if I can set server so that it has multiple websites seemingly subdirectories, but are actually in own directories.

---

### Post by BkkBonanza on 2009-12-14
I'm sorry, you're not explaining this in a way I can answer. 
If you want multiple "rivera.wippies.net/anothersite" then these are not different web sites. They are paths on the same web site. You cannot have multiple web sites if you only have one domain available to you. You would need to have another domain or subdomain for each site. That's just basic semantics of web urls. 

For example, if you registered mysite.com then you could use DNS to add redirects for several sites to paths on your domain above. Like this, for example,

joe.mysite.com -> rivera.wippies.net/joe
jane.mysite.com -> rivera.wippies.net/jane

If what you want is several independent web sites on the service you have from wippies then you would need another domain and to use CNAME records to map them into subdirectories on the wippies space. You need the new domain because you don't have admin rights to alter DNS records on the wippies domain name. But this type of redirect mapping is commonly done.

---


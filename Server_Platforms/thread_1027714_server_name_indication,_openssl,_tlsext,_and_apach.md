---
title: "server name indication, openssl, tlsext, and apache2"
date: 2009-01-01
forum: Server Platforms
---

### Post by kpm on 2009-01-01
Forgive my ignorance, but I am having a difficult time discovering how I learn if certain modules or extensions are standard in the latest 8.10 server.  I would very much like to configure a LAMP server that supports one ssl certificate for multiple vhosts with one static ip. I have read the many bug or request postings about this topic, read a few how to recompile apache2 with a patch and openssl with a tlsext switch activated, but these are old posts and I was hoping to learn that a LAMP install using the latest Ubuntu 8.10 server would come packing these tools so one is only required to apt install and configure, rather than compile first. Can anyone fill me in on how to get this information?  Or provide it? And, if I am required to learn how to recompile apache2 with SNI support and openssl with tls extensions switched on, can anyone point to a good how-to for such a thing. 
Thanks

---

### Post by thegner on 2009-01-22
kpm,

I have been researching this very same topic. Out of ignorance, I went ahead and configured my two websites with SSL and put them on the same IP and PORT with two different virtual hosts, and everything appears to be working normally.

I am inclined to believe that ubuntu intrepid has this capability already built in, even though some of the apache configuration files advise that it is not possible. (They Probably need to be changed).

There are plenty of tutorials on how to set up name based virtual hosting over http, and plenty of different tutorials on how to sign your own cert, then run a website over https. I took the next logical step and combined the two, and the results were pleasing.

If you would like more detailed information about my setup, please let me know.

Travis Hegner

---

### Post by kpm on 2009-01-23
> **thegner said:**
> kpm,

I have been researching this very same topic. Out of ignorance, I went ahead and configured my two websites with SSL and put them on the same IP and PORT with two different virtual hosts, and everything appears to be working normally.

I am inclined to believe that ubuntu intrepid has this capability already built in, even though some of the apache configuration files advise that it is not possible. (They Probably need to be changed).

There are plenty of tutorials on how to set up name based virtual hosting over http, and plenty of different tutorials on how to sign your own cert, then run a website over https. I took the next logical step and combined the two, and the results were pleasing.

If you would like more detailed information about my setup, please let me know.

Travis Hegner

Thanks for the input Travis. I've had to let this one go for a while and am getting back to it now...

Can you fill me in on how you went about achieving this?
If you have two sites on one IP, say [https://ssl.exampleOne.com](https://ssl.exampleOne.com) and [https://ssl.exampleTwo.com](https://ssl.exampleTwo.com), and you are using say CACert.org as a certificate authority, if you navigate to the urls, does the browser through the expected warning such as "The certificate is not trusted because it is self signed", but the second site add on the extra warning line "The certificate is only valid for ssl.exampleTwo.com"

I'm currently trying to achieve this by using this howto:
[http://wiki.cacert.org/wiki/CSRGener...t=VhostsApache](http://wiki.cacert.org/wiki/CSRGener...t=VhostsApache)

...which I'm running into a different issue with the certificate at the moment... I'm using a vps, and the vps node server name is being used by the certificate rather than the host name I gave to the server.

When I sort that out, then I have to figure out how to set up the different ssl sites vhosts since the example in the howto uses one vhost file... and when i set up and a2ensite the various ssl vhost sites, Apache gets upset and says it is going to use the first one listed, and ignore the rest.

Thanks

---

### Post by thegner on 2009-01-23
kpm,

After thinking about it some more, one key consideration for my success in this is that I am doing this with sub-domains, and a self signed wildcard cert. For instance: sub1.example.com and sub2.example.com, with a cert signed on the domain *.example.com.

I also noticed through wireshark that the traffic for one site is SSLv3 and the other site is TLSv1, and I did no specific configuration on which method any given site should use.

I have not tested whether or not my config would work on separate domains, when I have time, I can test this for you. I'm thinking that you will always in the very least get the domain mis-match error unless you specify a separate cert for each site, but that may very well break the config altogether because the fact that both sites are using the same cert in my config, is probably what is allowing apache to decrypt the traffic even when it's headed for a different site. That is just a guess though.

If you are able to run on sub-domains like I do I can give you some details about my config.

Travis

---


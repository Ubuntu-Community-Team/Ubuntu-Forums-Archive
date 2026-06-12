---
title: "Block access to the server when browsed to with IP"
date: 2010-06-25
forum: Server Platforms
---

### Post by kpm on 2010-06-25
Hi,
I have an Ubuntu LAMP setup hosting Drupal sites.  I have multiple sites all sharing the same Drupal code base.  When I create a new site, I set up the conf files etc, then browse to the url for the first time and get the Drupal new site set up page.  This is great, however, since all these sites share the same IP address, if one simply types in the ip address, they are also taken to the Drupal new set set up page.  I'd rather they get the message that they do not have access.  Can this be done? Without breaking how new Drupal sites are created?
Thanks

---

### Post by koenn on 2010-06-25
you can probably fix this by setting access controls on the default apache website. 
But  it's probably a good idee to ask on some Drupal site how to do thes The Right Way.

---

### Post by linux-hack on 2010-06-25
> **kpm said:**
> Hi,
I have an Ubuntu LAMP setup hosting Drupal sites.  I have multiple sites all sharing the same Drupal code base.  When I create a new site, I set up the conf files etc, then browse to the url for the first time and get the Drupal new site set up page.  This is great, however, since all these sites share the same IP address, if one simply types in the ip address, they are also taken to the Drupal new set set up page.  I'd rather they get the message that they do not have access.  Can this be done? Without breaking how new Drupal sites are created?
Thanks

Search in the Apache docs about htaccess and htpasswd files... you'll see they can do rely cool stuff..:lolflag:

---

### Post by Ryan Dwyer on 2010-06-25
Just put a deny from all in your default virtualhost block.

---

### Post by kpm on 2010-06-25
> **Ryan Dwyer said:**
> Just put a deny from all in your default virtualhost block.

Thanks.  That was quite simple... I actually had disabled the default site quite a while back... Unfortunately i can't remember why... likely trying to trouble shoot the multiple site install... anyway, all seems well now and functioning as expected.

---


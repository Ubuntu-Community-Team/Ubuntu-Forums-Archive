---
title: "Ruby with Apache2 on Ubuntu"
date: 2008-09-27
forum: Server Platforms
---

### Post by Bios Element on 2008-09-27
So I'm trying to install Ubuntu on Apache2 for a local dev enviroment. Now the compile worked just fine for mod_passenger but the problem comes when i add the config lines to the server.

When i try to start the server i get this.
> 
apache2: Syntax error on line 305 of /etc/apache2/apache2.conf: Cannot load /var/lib/gems/1.8/gems/passenger-2.0.3/ext/apache2/mod_passenger.so into server: /var/lib/gems/1.8/gems/passenger-2.0.3/ext/apache2/mod_passenger.so: undefined symbol: _ZNSt15_List_node_base4hookEPS_
                                                                         [fail]


After several hours of google, I can't figure anything out to help.

If it helps, the config edit i made was
> 
LoadModule passenger_module /var/lib/gems/1.8/gems/passenger-2.0.3/ext/apache2/mod_passenger.so
   PassengerRoot /var/lib/gems/1.8/gems/passenger-2.0.3
   PassengerRuby /usr/bin/ruby1.8


I've got no other ideas on how to get this to work so any help would be great.

Bios Element

---

### Post by Bios Element on 2008-09-29
Any thoughts on this? Or am i just destined to not learn Ruby. >.>

---


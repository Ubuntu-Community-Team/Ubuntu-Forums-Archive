---
title: "Do I need to install Bind to fix this problem?"
date: 2007-08-30
forum: Server Platforms
---

### Post by stabface on 2007-08-30
HI, 

i work in a small office and  they have a cable t1 line with static IP's. 
they let me have one to run my own server on  so  this is what i have. 

one server decent specs. 
1 static IP address. 
Ubuntu Server install 7.04 i used the LAMP option  during install to install. 
i have opened port 80 21 22 and 443 and have them forward to the server on my router. 
i can ssh install the box. 
i went to godaddy which is where i bought me domain. and   they have an option create custom name servers so i did so. 

ns1.mysitesecretary.com and ns2.mysitesecretary.com 

and i had point to my IP address. both to the same IP address

so now i think i have everything i need.  right? but it still doesn't work. 

i was wondering do i need to have bind installed on my box to point to the sites on my box?  or is that what  i did when i changed the ns1.mysitesecretar.com to point to my domain. 

i have never setup a webserver before so  all the help will be great. 


one other thing i am getting an error when i reload apache. 

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by wirelessmonkey on 2007-08-30
2 things:
1) Can you ping the domain name... i.e. ping ns1.mysitesecretary.com ?
2) Do you have your Apache hosts or Virtual Hosts configured?

---


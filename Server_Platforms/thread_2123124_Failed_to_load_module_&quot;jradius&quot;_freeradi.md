---
title: "Failed to load module &quot;jradius&quot; freeradius server"
date: 2013-03-07
forum: Server Platforms
---

### Post by troya on 2013-03-07
HI All,

I just installed free radius server using apt-get on my ubuntu machine.
Now i want to configure jradius on my freeradius server.


I follow step by step from [http://coova.org/JRadius/FreeRADIUS](http://coova.org/JRadius/FreeRADIUS).


Firstly my freeradius server running well, whereas i've configure it with mysql and coovachilli.
Then i configure with jradius, i inserted module on radius.conf file on module section like bellow :



```


       # configure the rlm_jradius module       

jradius {          
name      = "radius"                     
primary   = "localhost"          
secondary = "192.168.2.3"            
tertiary  = "[192.168.2.3:8002]("http://192.168.2.3:8002/")"          
timeout   = 1                       
onfail    = NOOP                                                           
                                                                                
keepalive = yes                 
connections = 8                 
   }

```

Then i add some authorization on /etc/freeradius/site-avalaible/default like bellow


```


authorize {
     ... 
     jradius    }
     
post-auth {
   ... 
  jradius 
          Post-Auth-Type REJECT { 
                        jradius                               } 
          } 

preacct {
   ... 
   jradius 
   }
      
accounting {
       ... 
      jradius 
   }


```

Finally i try to running on foreground to know that my configuration has been success, but i get error message like bellow :



```

Thu Mar  7 13:56:15 2013 : Debug:  } # modules
Thu Mar  7 13:56:15 2013 : Debug: } # server
Thu Mar  7 13:56:15 2013 : Debug: server { # from file /etc/freeradius/radiusd.conf
Thu Mar  7 13:56:15 2013 : Debug:  modules {
Thu Mar  7 13:56:15 2013 : Debug:  Module: Checking authenticate {...} for more modules to load
Thu Mar  7 13:56:15 2013 : Debug:     (Loaded rlm_digest, checking if it's valid)
Thu Mar  7 13:56:15 2013 : Debug:  Module: Linked to module rlm_digest
Thu Mar  7 13:56:15 2013 : Debug:  Module: Instantiating module "digest" from file /etc/freeradius/modules/digest
Thu Mar  7 13:56:15 2013 : Debug:  Module: Checking authorize {...} for more modules to load
Thu Mar  7 13:56:15 2013 : Debug:     (Loaded rlm_preprocess, checking if it's valid)
Thu Mar  7 13:56:15 2013 : Debug:  Module: Linked to module rlm_preprocess
Thu Mar  7 13:56:15 2013 : Debug:  Module: Instantiating module "preprocess" from file /etc/freeradius/modules/preprocess
Thu Mar  7 13:56:15 2013 : Debug:   preprocess {
Thu Mar  7 13:56:15 2013 : Debug:     huntgroups = "/etc/freeradius/huntgroups"
Thu Mar  7 13:56:15 2013 : Debug:     hints = "/etc/freeradius/hints"
Thu Mar  7 13:56:15 2013 : Debug:     with_ascend_hack = no
Thu Mar  7 13:56:15 2013 : Debug:     ascend_channels_per_line = 23
Thu Mar  7 13:56:15 2013 : Debug:     with_ntdomain_hack = no
Thu Mar  7 13:56:15 2013 : Debug:     with_specialix_jetstream_hack = no
Thu Mar  7 13:56:15 2013 : Debug:     with_cisco_vsa_hack = no
Thu Mar  7 13:56:15 2013 : Debug:     with_alvarion_vsa_hack = no
Thu Mar  7 13:56:15 2013 : Debug:   }
Thu Mar  7 13:56:15 2013 : Error: /etc/freeradius/radiusd.conf[644]: Failed to link to module 'rlm_jradius': file not found 
Thu Mar  7 13:56:15 2013 : Error: /etc/freeradius/sites-enabled/default[71]: Failed to load module "jradius".
Thu Mar  7 13:56:15 2013 : Error: /etc/freeradius/sites-enabled/default[62]: Errors parsing authorize section. 

```




What this error ?


How i can solve this issue ?




Thanks

---

### Post by lisati on 2013-03-07
Is that a direct copy/paste of the config files? I would have added [noparse]```
 and 
```[/noparse] tags, but it still didn't look right....

---


---
title: "Does everyone's ubuntu often send data to amazon aws?"
date: 2017-09-08
forum: Security
---

### Post by unityforever on 2017-09-08
this is the udp connection i catched in last 20 minutes.
```
0      -1                192.168.1.105:60626                        50.112.169.119:* 
0      -1                192.168.1.105:54536                         52.35.101.212:*
0      -1                192.168.0.119:46408                        54.148.180.133:* 
```
i reverse lookup them and find they are Amazon Aws servers.

most of time i do this spot check and those kind of connection can be observed. 

and sometimes i can see my computer established a TCP connections to a Amazon Aws servers.

i didn't install any amazon program before. i don't have any cloud product. actually im not a programmer, so all the things about programming or amazon i don't have them. i just have an liberoffice on my computer. while computer are connecting to amazon aws i don't running any program either.

I Know Amazon AWS is just a cloud computing provider

Obversely someone rent the server and use it as a center, then when the code on people's computer are executed, the connection can be established easily.

i assume is some service on Ubuntu, maybe updating, time fixing, error report or something else. and Ubuntu Official rent Amazon AWS to support the service.
but i can't be sure. so i post the thread to confirm.

my camera was auto started before and that terrified me. i hope the phenomenon about AWS is a common phenomenon then i can feel ease.
if it is just my computer doing this, could that means i been hacked?

---

### Post by Doug S on 2017-09-08
> **uiduser said:**
> i reverse lookup them and find they are Amazon Aws servers.Yes, but you need to also trace back (which you probably can not do but I keep stuff so I can) and find what forward lookup might have given those IP addresses, which might offer more clues.

For 52.35.101.212 I got balrog-aus5.r53-2.services.mozilla.com. So, I assume something to do with firefox.
For 54.148.180.133 I got blocklists-settings.prod.mozaws.net. Also something to do with mozilla.
For 50.112.169.119 I didn't get a hit from my system historical data I looked at. But after a search on internet, I found addons.mozilla.org and olympia.prod.mozaws.net, also mozilla.

---

### Post by unityforever on 2017-09-17
> **Doug S said:**
> Yes, but you need to also trace back (which you probably can not do but I keep stuff so I can) and find what forward lookup might have given those IP addresses, which might offer more clues.

For 52.35.101.212 I got balrog-aus5.r53-2.services.mozilla.com. So, I assume something to do with firefox.
For 54.148.180.133 I got blocklists-settings.prod.mozaws.net. Also something to do with mozilla.
For 50.112.169.119 I didn't get a hit from my system historical data I looked at. But after a search on internet, I found addons.mozilla.org and olympia.prod.mozaws.net, also mozilla.

thank you very much!

---


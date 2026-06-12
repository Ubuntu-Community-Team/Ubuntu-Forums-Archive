---
title: "Beginner help! Receiving 404 errors while trying to access localhost"
date: 2008-09-15
forum: Server Platforms
---

### Post by dalearyous on 2008-09-15
i installed ubuntu server edition on my old athlon xp machine. i then installed the ubuntu desktop package so i could have a gui to work with. i then installed webmin and tested to make sure i could login and it works just fine. right now i have the server setup with just a local static IP address (192.168.1.xxx) and when i first started if i typed that into my browser on any machine on the network i would get a real basic web page stating "It works!" so i tried editing the index.html file that i thought was associated with it using the root username and it stopped working...

exact error:
404 Not Found. the requested URL/was not found on the server
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at localhost Port 80 

what i am trying and failing to do is figuring out what directory the site is trying to pull index.html file from. i know 404 errors usually mean the page i was looking for does not exist. thats great...but where can i put my index.html or my test.php file so that it DOES exist. i can't get any farther in any of the guides because i cannot get this simplest thing to work that was working just fine before i started playing around with everything. any ideas?

edit* after logging in, i just realized i have no virtual hosts...that can't be right.

---

### Post by kamaji792 on 2008-09-15
I'm sure the default directory for Apache is /srv/www

Make sure that contains an valid HTML file called index.html

All the best

---

### Post by dalearyous on 2008-09-15
i thought it was /var/www

btw, if it helps, localhost/phpmyadmin works

---

### Post by kustomjs on 2008-09-15
how i got mine setup was /var/www/ then do you have your server on static info like 192.168.1.5? because if you do and if you want to log into webmin its this [https://192.168.1.5:10000](https://192.168.1.5:10000)  and its not localhost its whatever your ip address is of the machine.

---

### Post by dalearyous on 2008-09-15
there must have been something wrong with my install. i got fed up at like 4am and reinstalled ubuntu and started from scratch. since then i have not run into any problems. all my stuff has worked so far and i even got a database going with tables etc...

i do have a manual ip assigned to the machine and localhost does work but only on the server...for all other machines on network i type in the manual ip. 

now i just need to figure out how to link it with the domain i bought from godaddy.com

---

### Post by kustomjs on 2008-09-15
to do that from godaddy you must have a static ip or if you got DHCP address u want to try no-ip get get a ip address then update it inside your godaddy settings.

---

### Post by dalearyous on 2008-09-15
well i got that figured out. now when i type in my domain, it takes me to the no-ip domain i setup and my website...however i do not think it works outside my local network. i only have my iphone to try it but it cannot navigate to my page. i have port 80 forwarded to the server...anything else?

yeah i had a friend try it, he said it forwards to my no-ip domain and then just sits there. i installed the program to update my ip with no-ip.com. whats causing conflict

---

### Post by cariboo on 2008-09-15
Have you tried [canyouseeme]("http://www.canyouseeme.org/") to make sure port 80 isn't being blocked by your isp.

---

### Post by dalearyous on 2008-09-16
it states port 80 is blocked. but i never really trusted that because on my main gaming machine i have port 6112 opened for battle.net and it states that its not open but i have no trouble hosting games.

---

### Post by dalearyous on 2008-09-16
well i guess port 80 was blocked. i changed it to 8080 in the /etc/apach2 file and in my no-ip account and it works now.

now to the fun stuff of the actual design of the website.

---


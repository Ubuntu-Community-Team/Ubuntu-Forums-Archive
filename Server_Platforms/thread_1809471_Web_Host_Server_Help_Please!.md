---
title: "Web Host Server Help Please!"
date: 2011-07-21
forum: Server Platforms
---

### Post by TheLilPenguinThatCould on 2011-07-21
Ok, so i am attempting to run my own web hosting server that will only run 1 website that almost no one will ever go to.  Needless to say i am doing this for fun!  I have already registered a Domain name with Go Daddy and i am having trouble.  Here's the situation;

I have a dedicated Linux box (ubuntu 11.4) connected to a router, that is connected to ANOTHER router, which is connected to my cable modem.  I have set up Port Forwarding for port 80 (HTTP) on the first router that points to the second router, and set up port forwarding on that router to my server.  (all static ip's)
On godaddy i have my external ip address listed as my host.

I installed Apache2 and made sure it runs on startup. 
i have also installed Bind9 (not sure if i actually need that yet) my /etc/hosts file looks like this ;

(local server ip adress 10.xx.xx.xx/ i have also tried my external ip address here) mysite [www.mysite.com](www.mysite.com) mysite
::1    Jerry-desktop   localhost6.localdomain6 localhost6
127.0.0.1      jerry-desktop

when i restart apache2 i get this error message;

Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for servername

im thinking my apache configurations are most likely incorrect but i could definitely use some help/guidance/suggestions/answers or all of the above lols

*also note that when i go to [www.mysite.com](www.mysite.com) from any browser WITHIN my network everything works great!  when accessed from OUTSIDE my network i get Error 502 - bad Request The server could not resolve your request for uri: . etc etc.

---

### Post by CharlesA on 2011-07-21
Can you access it by going to your external ip address?

---

### Post by TheLilPenguinThatCould on 2011-07-21
Funny how i never thought of that jajajaja.  but sadly no, i just tried.  so it shouldnt be a DNS issue.  maybe im behind too many firewalls? or maybe how i have things configured on go daddy i.e it asks for a server name and when i called and told them i dont have one they said i could just use my ip.  

BTW thanks for your help and quick reply! :)

---

### Post by CharlesA on 2011-07-21
Check your port forwarding.

---

### Post by hsweet on 2011-07-21
You have a few issues.  

If you registered your site on Godaddy but are hosting it locally, then you do need bind (nameserver) set up on your computer. Then you have to tell godaddy the ip of your nameserver, once that is running properly.  

If you let them host it, that will be one less thing to figure out.

Your apache error is not a big deal.  Just gotta edit the apache config file.  It used to be called http.conf, but I forget :).  Anyhow, it's in /etc and check apache docs.

Static IP's are good.

But then your ISP could block port 80, end of story.  Going thru several routers adds more layers.  My head is starting to hurt.

---

### Post by TheLilPenguinThatCould on 2011-07-21
Yea I have been over it a million times and even changed static ip's.  Same result.  Do I need Bind9 to be active and configured correctly?!  I installed it but didn't really configure it.  Well that's DNS really, I guess I have problems of a different flavor

---

### Post by TheLilPenguinThatCould on 2011-07-21
Jajaja I know its pretty intense.  But thanx for the advice, I will call my ISP to see if they block port 80 and try to figure out how I config bind9 correctly (local IP or external) :)

---

### Post by hsweet on 2011-07-21
You need a running nameserver on your system for names to work.  But first get to the point where you can see your server via IP, then go after Bind.

---

### Post by TheLilPenguinThatCould on 2011-07-22
thanks hsweet,  i def agree something is broken along the way.  im gonna play with some different set ups tomorrow and keep you guys posted.  

* this is my first time involved with a forum. ever. jaja not even kidding.  you guys have been really helpful and it is encouraging, so thanks again :)

---

### Post by TheLilPenguinThatCould on 2011-07-22
Awesome news guys! Everything is running great! Heres what happened;

So it turns out my isp does block port 80 (as most do apparently jaja) so I setup my port forwarding for http to a an unused port on both routers and kept everything else the same.  updated my apache config files, restarted and tested using my ip:the new port and bingo worked.  i was curious so i started the bind9 service as is and it turns out my configs were correct as wwww.mysite.com:1234 worked!

The icing on top of all this is go daddy allows me to forward my domain so [www.mysite.com](www.mysite.com) takes you to [www.mysite.com:1234](www.mysite.com:1234)!!!!!!! 

sounds cheesy but i actually cried of happiness jajajajaja

Thanks hsweet and CharlesA for all of your help!!!!!!

---

### Post by CharlesA on 2011-07-22
No problem.

You might want to use port 8080 instead of 1234, since 8080 is the alternate http port.

---


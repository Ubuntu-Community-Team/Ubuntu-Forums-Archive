---
title: "dns bind 9 ect ..."
date: 2007-06-02
forum: Server Platforms
---

### Post by hockey97 on 2007-06-02
Hi I want to have my own domain name for my website and I know my external IP adress could I used that??
like use my dns server to replace my external Ip address with a domain name on the web???

---

### Post by rickyjones on 2007-06-02
Well, first we need to identify the goal here...

Here is what I gather: You want a domain name (we'll call it example.com) to go to the server on your network so that people can see your stuff. In this event, this is what you'll want to do...

1 ) Find out your static IP address
2 ) Register your domain name (I personally use Godaddy.com, never had an issue)
3 ) Have your registrar (Godaddy in my example) create an A record of "www" and point it to your static IP address
4 ) Make sure that your router is forwarding port 80 to the internal IP address of your web server (this server should have a static internal IP address)
5 ) Give DNS about 1 hour to fully propagate and have a friend test it out

Does this cover what you want to do?

Thanks,

-Richard

---

### Post by hockey97 on 2007-06-02
Well sort of I know that way already what I am asking  or want to do if possible to host my own domain name like I have a dns server and I know  my external and internal ip adress and right now I can have my server seen on the internet what I want to do is  host my dns on the internet so that like if someone types in my example.com that my dns server will respond and forword it to my web server ect so  what I want to do is to host my own domain name.

I  only have one external static ip adress like it dosen't change.

I don't want to use other's services to host my domain name if I can do it myself it would be great.

If I can't fully be done by myself becuse I don't have raw acces to the internet, then I am thinking to go into ISP business ect.

but my main goal is to have a domina name hosted by myself that points to my web server ect.

---

### Post by rickyjones on 2007-06-02
Yup, you can host your own DNS. You still need to register your domain name with a registrar, but instead of them hosting the DNS you can point the nameserver addresses to your static IP. Make sure port 53 is forwarded from your router to your DNS server.

-Richard

---

### Post by hockey97 on 2007-06-02
(register your domain name with a registrar) 

Why would I still need to register with a registrar?? is that like for legal reasons or I have to in order for my
domain name be seen on the internet??

---

### Post by rickyjones on 2007-06-02
Yes, you do need to register your domain name with a registrar. I don't believe it is for a legal reason, but instead is more technical. If you don't have it registered with an accredited registrar then none of the root DNS servers will know /where/ to find the DNS information for your domain name. Example - I tell Godaddy to let my server manage my DNS, and Godaddy tells the root DNS servers that they can find the information at xxx.xxx.xxx.xxx.

-Richard

---

### Post by hockey97 on 2007-06-03
Now I fully understand the system So like the registrar thing is like the internet it's a main place where when someone types in example.com that registrar thing would respond and then forword it to my dns then the dns would connect the request to my main web server ect??

I get it now thanks alot.

I am planing to become an ISP, going to make a deal with a company that already set up a network with fiber optices ect their new and selling rent ect so I am thinking going that route.
They claim in the package a t3 speed and also I will become a domain registar I can host it ect.

---

### Post by prostock3 on 2007-07-01
what is the advantage of hosting your own dns?

---

### Post by hockey97 on 2007-08-31
Their is really no advantage by hosting your own dns using your dns server, becuse you still need a backbone connection to the internet.

if you buy a line that goes to the back bone of the internet you then can host your own domain names witha  dns server and also charge others to host theirs. The line is expensive, but you can make alot of money doing it if you know what your doing.

I bought a domain name and havign trouble getting it up and running.

I am using apache web server, but don't know what ip address to use and how to config apache so the connections would be right, like the dns hosting place they registered my domain name and are hosting my records their.

I am right now using my external ip address in the records of the domain name and also apache server on my computer.

I need to know how and what ip address I need in order to be able to type in my domain name and the apache server would grab the main web doc for the site.

---


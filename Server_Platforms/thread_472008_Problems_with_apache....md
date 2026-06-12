---
title: "Problems with apache..."
date: 2007-06-12
forum: Server Platforms
---

### Post by hockey97 on 2007-06-12
Hi I have webmin installed and I installed cvs in webmin, I want to uninstall it how could I do that??
I used webmin to install it?

The reason, is becuse before I installed it my web server apache worked like I on my network could access it, even on other computers in my house I could access the server, but after I installed that cvs I now have a problem, I can still access my webserver but only on this computer, meaning the computer with the web server on it, but when I got type of ip adress of thise computer, and yes I did config my router right becuse I used the same method accessing the web server apache,
Now I can only access it on my computer with the server only, my other computers when I typed in the ip adress of the computer with the web server it  wait's a while then a msn search is done, meaning it then looks for the ip adress using msn search.

That indicates that their is no server or can't be found.

But I tried it on my computer that has the web server and it works only on that computer I have no

trouble with the.

This is why I  think it's the cvs installation.

SO how would I go about's deleting cvs without destroying my webmin installation??

---

### Post by CLI-Linux on 2007-06-12
```
sudo apt-get remove cvs
```

to get cvs off.  I'm curious though, as to why cvs would be causing that problem.  Try uninstalling and see what happens.

Anyone a CVS expert who can comment?:?:

---

### Post by hockey97 on 2007-06-12
I have uninstalled it and still same stuff, I now am going to uninstall squid proxy.

I hope this works, I knew one of these are causing me problems or also could be bind 9, I don't have a domain name,  I am using my ip adress that is my internal ip address.

---

### Post by hockey97 on 2007-06-12
I deleted squid proxy, and nothing happened like I mean same problem.

I can put my internal ip adress of the computer with the web server in the web browser and get the web page of the server ect, I am using wedmin.

but I used to be able to do the same on any computer at my house, now for some reason, I  can't

this basicly show that I can't publish my web server / websites,  but I used to be able.

I have my router configed right, however I am allowing port 80 and port 803 and port 777 forworded, would that make a difference??

803 was my proxy server I used to have up, the 777 is a game server port, and a port 80 is for the web server. 

I think I one time monkeyed around with the config files of apache or webmin, something to make

only 127.0.0.1 to be able to access, 

I don't fully remebered what I did I thought it was in squid proxy  but it could be in bind or apache.

becuse that could be the problem that it won't publish only publish to 127.0.0.1 which is local host, that's really the only thinkg I can think of as of right now.

that could be my problem, is their a way that I can replace or refresh my apache2 files??

like to get it back to default settings?.

---

### Post by hockey97 on 2007-06-15
HI I  still have the problem I don't know what to do.

Should I just reinstall apache  if I do that would I have to reinstall webmin ???

I remebered webmin installing it was s hard type task or long ect.

I also want to get a mail server going, I want to make a page interface and beable to test the 

system, by using my internal ip adress, I plan in the future to have  domain name, but for now I just want to test thing's out, and then once I got everything in order I will post the site.

---

### Post by hockey97 on 2007-06-17
Hi I reinstalled apache and webmin, now apache is not working I got 2 versions one apache 1.3 which works  only on my computer with the server, and apache2 doesn't work at all I use webmin to start it when trying

to start apache2 it say's error web server is not already running.

I tried alot of stuff and can't fix the problem, like I still can't have a web server able to be seen on my internal network.

I had this problem for a month actully.

Should I just uninstall everything and start all over?? 

It will be harsh but I have a feeling that won't really help it would suck if it didn't take care of the problem.

I think squid proxy mess stuff up.

---


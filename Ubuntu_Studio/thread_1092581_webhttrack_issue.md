---
title: "webhttrack issue"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by Nukinfuts on 2009-03-10
Apologies if this is the wrong place, but its websites/multimedia so...

Anyway i installed webhttrack from terminal via apt-get. When i try and start it i am getting a 404 error on the new tab it opens in opera. I'm clueless as to what is going on. Here is the terminal output:

> 
steve@reaper:~$ webhttrack
/usr/bin/webhttrack(20816): launching /usr/bin/x-www-browser
/usr/bin/webhttrack(20816): spawning regular browser..
opera: Activated running instance
/usr/bin/webhttrack(20816): browser exited
/usr/bin/webhttrack: line 154: 20837 Killed                  ${BINPATH}/htsserver "${DISTPATH}/" path "${HOME}/websites" lang "${LANGN}" $@
steve@reaper:~$ 


the 404 is:

> 
You tried to access the address [http://reaper:8080/](http://reaper:8080/), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page.

---

### Post by astraluxkl on 2011-07-24
I aso have this error

Ubuntu 11.10 app WebHTTrack

[http://localhost:8080/](http://localhost:8080/) couldn't connect

from terminal it works

»$ httrack

---

### Post by bokgeneraal on 2011-08-10
If you don't mind. Could you give a quick tutorial as to how you use httrack in the terminal:)

---

### Post by bokgeneraal on 2011-08-10
Hi there
I  used Webhttrack in previous Ubuntu versions. When I launch it from  the apps menu , firefox opens and I am greeted by this sad  message>  **The requested URL could not be retrieved**

    While trying to retrieve the URL: [http://ubuntu:8080/](http://ubuntu:8080/) 
  The following error was encountered: 
 [INDENT] Unable to determine IP address from host name for *ubuntu* [/INDENT]    The dnsserver returned: 
 [INDENT] Name Error: The domain name does not exist. [/INDENT]    This means that: 
  The cache was not able to resolve the hostname presented in the URL.   Check if the address is correct. There is currently an issue with our service providers, emergency repair work is underway which may be causing this.
 
 I am using a proxy server to connect to the net. The last statement is not correct as the network is in working condition. Thanks.

---

### Post by bokgeneraal on 2011-08-10
Bump

---

### Post by spinifex on 2011-09-23
SOLVED. 

For those still having trouble I have a solution.  I'm using Fedora 15 but this should work for Ubuntu as well. 

I got the error Unable to Connect when using Httrack, apparently, because I specified a hostname when I was installing Fedora.   So Httrack was trying to connect to "hostname".com/8080.

I changed the of my computer in Network Connections and, presto, now Httrack works.  

I think this is because Httrack by default wants to connect to port 8080 on localhost.  

Hope this helps.

---

### Post by firefish5000 on 2011-09-24
Im using chromium and I found that this problem only persist for me if I have a webbrowser(or whatever webbrowser httrack uses, I dont have one other than chromium installed and it opens in the chromium browser) open and running at the time. If I close chromium or quit firefox then run it it works.(this may verry well be just me though)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-26
> **firefish5000 said:**
> Im using chromium and I found that this problem only persist for me if I have a webbrowser(or whatever webbrowser httrack uses, I dont have one other than chromium installed and it opens in the chromium browser) open and running at the time. If I close chromium or quit firefox then run it it works.(this may verry well be just me though)

Same thing here. Weird... Wonder what could be the cause for this...

EDIT: Although I can open WebHTTrack's home page if my browser was closed, I still can't go anywhere from there. When I click 'next', it just loads forever. Same thing happens if I try to refresh the home page. I've also noticed that if my browser is open, WebHTTrack will try to open [http://localhost:8080/](http://localhost:8080/) and if my browser is closed, it tries to open [http://localhost:8080/server/index.html](http://localhost:8080/server/index.html) . Strange...

---

### Post by wildmanne39 on 2012-07-28
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


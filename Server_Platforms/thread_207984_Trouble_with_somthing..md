---
title: "Trouble with somthing."
date: 2006-07-02
forum: Server Platforms
---

### Post by ExMachina on 2006-07-02
Running ubuntu 6 on a server.

Netin - sbc modem- router (running pppoe) - split to 3 comps 

One comp is runnign DNS updatign using no-ip software.
One comp server is also set in the DMZ zone

When i ping my 2 dsn ( hackered.no-ip.info . garza.hopto.org )

i get replys form 192.168.102 which is my router.

How do i go about fixing this? 
need more info tell me.

---

### Post by Randomskk on 2006-07-02
How is this causing a problem?
If you actually go to http://<domain>, does it work?
Are the ports forwarded on the router?

Finally, you may just need to add the domain to your server's IP in your /etc/hosts file, add this to /etc/hosts (as root on linux) or C:\WINDOWS\system32\drivers\etc\hosts (on windows):

<server ip> hackered.no-ip.info garza.hopto.org

---

### Post by ExMachina on 2006-07-02
[QUOTE=Randomskk]How is this causing a problem?
If you actually go to http://<domain>, does it work?
Are the ports forwarded on the router?

Finally, you may just need to add the domain to your server's IP in your /etc/hosts file, add this to /etc/hosts (as root on linux) or C:\WINDOWS\system32\drivers\etc\hosts (on windows):

<server ip> hackered.no-ip.info garza.hopto.org[/QUOTE]


When i ping <domain> i get a reply form 192.168.1.1.

whne i type int he domain i get a "cannot connect to server" ports arr forwarded, lamp is running >.< im just pissed i ahve no idea whats wrong i was so proud fo all the html css and stuff i had done for friend and wnated ot host it all. I NEVER had this trouble wiht my old router i think that may be the problem.

At first lamp was perfect until trillian ran on another comp then trillian killed lamp i think i finally fixed the issue but now this one is happaening. *gao*

---

### Post by ExMachina on 2006-07-03
I figured otu a problem
my eth0 gets an IP and i can access from any comp within my network. 
But when i try tp ping yahoo.com it cannot find them somthign wierd with the Eth0 card. So i replaced it now it wont even get a ip address how do i add a new eth card??

---


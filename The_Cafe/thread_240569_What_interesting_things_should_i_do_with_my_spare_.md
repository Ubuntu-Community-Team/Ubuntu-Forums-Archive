---
title: "What interesting things should i do with my spare pc"
date: 2006-08-21
forum: The Cafe
---

### Post by CameronCalver on 2006-08-21
hello i recently got given a old computer which had win98 on it so i formatted it and put ubuntu on it but im not sure what i should do with it it was a 533 mhz 128 mb ram 10gb moster butit now have 350 mb ram.
I dont know what do do with it i dont need a file server so what do you guys think i should do with it

---

### Post by jperez on 2006-08-21
Give it to a charitable organization or sell it (the PC).  A 533Mhz computer can still be used for writing documents and with Ubuntu on it, it's much safer for the end-user since not much hacking will be going on. ;)

Jesse~

---

### Post by Sam on 2006-08-21
If you don't need a file server, you can use it as a gateway (firewall, DNS, DHCP, ...) if you have several computers in your networks. 

jperez's proposal is great, too.

---

### Post by kerry_s on 2006-08-21
It's always nice to have a test machine to try out all the different linux distro's out there. I started out on distrowatch just working my way down the top 100. You can also use it to learn things with out fear of toasting your main system. Right now i'm running dsl linux in ram cause my spare hd gave out, but i use it mostly for testing those distro's that don't have a live cd to try. Carefull though it's addicting i'll blow through at least a 100 cdr's a month.

---

### Post by CameronCalver on 2006-08-21
ok im internested in the gateway idea but what would it d exatly

---

### Post by Sam on 2006-08-21
It acts as the entry point of your internal network. It can have a firewall to filter incoming connections. [IPcop](http://ipcop.org/) does the job well.

DNS and DHCP are often handled by the router, but if not you can install these services.

---

### Post by CameronCalver on 2006-08-21
ok nah i have a router any other ideas just a question what is a proxy

---

### Post by Sam on 2006-08-21
A proxy is intended to connect to internet indirectly. Using a proxy, when you go to a website, you send a request to the proxy, the proxy sends the request to the destination server, the server sends the reply to the proxy which transfers it to you. On server-side, one can only see the connection from the proxy and not what's behind.
This is useful on networks with a lot of computers, because the proxy puts web pages in a internal cache so if a website is accessed often, there is less network traffic.
The proxy can also filters some things, like destination IP, some websites or websites with a specific word, etc...

---

### Post by tribaal on 2006-08-21
Don't waste unused computer power!
If you have it running at home, make sure you harness it's computing power, and use it for the general good: install a [BOINC]("http://boinc.berkeley.edu/") client ("sudo apt-get install boinc-manager" for the whole thing, with a gui) and attach to [rosetta@home]("http://boinc.bakerlab.org/rosetta/").

And on top of that it's not uncompatible with your machine being a gateway :)

- trib'

---

### Post by CameronCalver on 2006-08-21
no i dont have a unlimited download a month

---

### Post by Johnsie on 2006-08-21
I'd go to [http://apachefriends.org](http://apachefriends.org) annd turn it into a web server.

---

### Post by Sam on 2006-08-21
You can also make a multimedia station to play your music or watch movies.

---

### Post by CameronCalver on 2006-08-21
no i am going to turn it into a proxy server for my computer and a couple on the lan and me and my friends to bypass the gay blocker at school that block like 75% of the legit stuff

---

### Post by hanzomon4 on 2006-08-21
> **Sam said:**
> You can also make a multimedia station to play your music or watch movies.
How would you go about setting something like this up.
I got an extra computer too, and I kinda thought about using it as multimedia server.

---

### Post by Sam on 2006-08-21
> **hanzomon4 said:**
> How would you go about setting something like this up.
I got an extra computer too, and I kinda thought about using it as multimedia server.
[list][*]
[*]Install all application you need (music player, video player, etc.), install the codecs you need, DVD support, ...
[*]Clean up the desktop environnement to just have the minimal (removing all panels and use OSX-like dock of gdesklets is a good option)
[*]If you plan to host media files on an another computer, mount it to a directory.
[*]Sets the security settings that one cannot accidentally delete your files (if someone using your box made something wrong)
[*]If you have money to spend for, buy a remote control which works in linux.
[*]Etc... Ask if you have more specific questions[/list]

There are multimedia distros, but I haven't tried any of them.

---

### Post by hanzomon4 on 2006-08-21
Would it be possible to stream music/movies/whatever to other computers/tvs/sound-systems

---

### Post by Sam on 2006-08-21
> **hanzomon4 said:**
> Would it be possible to stream music/movies/whatever to other computers/tvs/sound-systems

Yes, but I don't know how.

---

### Post by mips on 2006-08-21
Do a search here for **media centre** or **kiosk**  for more info on streaming etc.

---

### Post by Nikusan on 2006-08-21
[www.cbnsw.org.au](www.cbnsw.org.au)

Unfortunately their website is down...

---

### Post by Bragador on 2006-08-21
I'd also use that computer for a science project. All of the active projects can be found here:

[http://www.distributedcomputing.info/projects.html](http://www.distributedcomputing.info/projects.html)

---

### Post by saracen on 2006-08-21
Install MythTV on it!

---

### Post by CameronCalver on 2006-10-05
Hey guess what i have another one this one even worse 
It is a twin hd each 500mb lol 16mb ram pentium (r) (dunno how to check the speed) and i turned the other one into a proxy server and it works great and this one has win98 on it (im putting a 10gb hd in it though) so what should i do with it

---

### Post by Mathiasdm on 2006-10-05
> **CameronCalver said:**
> Hey guess what i have another one this one even worse 
It is a twin hd each 500mb lol 16mb ram pentium (r) (dunno how to check the speed) and i turned the other one into a proxy server and it works great and this one has win98 on it (im putting a 10gb hd in it though) so what should i do with it

Hmm... Perhaps it would be better to use this one as a proxy server (it can't do much more :p ) and the other one for 'bigger things'.

---


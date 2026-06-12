---
title: "Apache, Port 80, Webserver is down, No Idea How"
date: 2008-03-07
forum: Server Platforms
---

### Post by Mr.Macdonald on 2008-03-07
Hello i have an apache server that has failed.

I used to have a site going

"macdonald.webhop.org"

and somehow it completely failed and now i have no site and i am not happy because it is my file server.

I have no idea what so ever on how this broke but port 80 may be closed.


I used Radmin (something, i forgot) to view the ports from my families Microsoft Box and it said that port 22 was the only port open.

I then used a site (i forgot but it was Three letter name that had a G in it, please post the name if you know it) and that said that Port 22 and 80 are open BUT i read that that site listens to the router only???


I have messed around a bit with firestarter but reversed every thing.
I didn't have firesterter installed before so i don't think i need it and would like to unistall it.
I have IpTables installed and have a router so i might need to disable the iptables.

if for some reason you get my site to load please tell me right away because it isn't too secure but has very little data on it.

my site is

macdonald.webhop.org
75.82.209.208

I am ok with reinstalling or uninstalling anything


Thank You Ubuntuers

---

### Post by azadpanchi on 2008-03-07
First of the subdomain is not resolving:
:~$ dig macdonald.webhop.org

; <<>> DiG 9.4.1-P1 <<>> macdonald.webhop.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 43275
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;macdonald.webhop.org.          IN      A

;; Query time: 1 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Mar  7 16:44:55 2008
;; MSG SIZE  rcvd: 38

Plus the IP Address is not resolving either:
~$ nmap 75.82.209.208

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-07 16:45 CST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 3.011 seconds

Since it is responding to ping I would venture to guess your firewall maybe preventing ping probes:
~$ ping 75.82.209.208
PING 75.82.209.208 (75.82.209.208) 56(84) bytes of data.
64 bytes from 75.82.209.208: icmp_seq=1 ttl=132 time=88.2 ms
64 bytes from 75.82.209.208: icmp_seq=2 ttl=132 time=89.8 ms
64 bytes from 75.82.209.208: icmp_seq=3 ttl=132 time=86.9 ms

--- 75.82.209.208 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 86.963/88.358/89.848/1.228 ms

Just to confirm, port 80 is unreachable:
~$ telnet 75.82.209.208 80
Trying 75.82.209.208...
   
Port 80 being closed is a good way to start, make sure the port is forwarded on the router and firewall has an exception for that port.  Additionally the subdomain does not resolve so no one will be able to reach it, make the required changes where you name servers are hosted to make it resolve.

---

### Post by PinkFloyd102489 on 2008-03-07
Try restarting Apache also.


```

sudo /etc/init.d/apache2 restart

```

in a terminal.

---

### Post by Mr.Macdonald on 2008-03-08
Thank you but nothing worked

Azadpanchi, i am thankful that you are trying to help me
but although i am good with many things on computers, apache and what you just said to me is a foreign language. I'm sorry but i had no idea what you said.

PinkFloyd, i tried that but it didn't work. i believe that i am running off apache web server but i really have no idea. i once had to re-do my Ubuntu by reinstalling it and i installed apache and apache2. they seem to be running off of each other because

Once i wanted to uninstall one of them. i uninstalled apache and it broke.
i then installed again and it worked and then i uninstalled apache2. It broke
i reinstalled apache 2 and all was good until recently

after reading this you may realize that i kind of screwed everything and that is why i am ok with reinstalling and starting over COMPLETELY

---

### Post by Mr.Macdonald on 2008-03-08
I have been going through a tutorial and reinstalled apache2
and uninstalled apache

i get this error when 

~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                    Syntax error on line 1 of /etc/apache2/mods-enabled/cgi.load:
Invalid command 'IntxLNK\x01.', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

my cgi.load says

&#28233;&#30836;&#20044;&#331;../mods-available/cgi.load


???????

No idea but i think this is a problem that is contributing
but i don't know what is supposed to be there

could you guys tell me if this is wrong??

---

### Post by Mr.Macdonald on 2008-03-08
Isn't it amazing that when we keep digging around ourselves we tend to fix a whole bunch of junk

i discovered that that cgi.load was symbolic link and all i had to do was remake it because i guess it was corrupt or something.

i did so and the error was gone BUT i keep getting that error for other links ???? do you know why.

IF I AM SCREWING STUFF UP BY REPLACING THOSE LINK WITH "CORRECT" ONE THEN REPLY PLEASE

otherwise i will replace all of them

---

### Post by Mr.Macdonald on 2008-03-14
By The Way, I fixed everything and you need not post anymore

---


---
title: "Server works on Lan but not over internet."
date: 2013-04-08
forum: Server Platforms
---

### Post by danshea on 2013-04-08
My server was working just fine and after a reboot, it will work when I am here at home on my lan, but it is not accessible from anywhere else? How do I fix this? it was just running a couple days ago, it has to be something simple. I am running a router and haven't changed anything in the router and I am using virtual hosts and haven't changed anything there either.  Strange.......

Thanks,
Dan

---

### Post by CharlesA on 2013-04-08
What are you trying to serve? You mentioned VirtualHosts, so I'm guessing you are running Apache. Have you tried checking to make sure it is accessible from the outside by using something like [http://canyouseeme.org/](http://canyouseeme.org/) ?

---

### Post by danshea on 2013-04-08
Hi Charles,

Yes I am running apache and whats werid is that it was just working a couple days ago from outside my lan. I could go to my site from any pc anywhere and now no. A default page I have running is at [www.biddock.com](www.biddock.com) ,

Thanks,
Dan

---

### Post by CharlesA on 2013-04-08
I did a dig on it and it returned this:

```
charles@Thor:~$ dig www.biddock.com

; <<>> DiG 9.8.1-P1 <<>> www.biddock.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27526
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.biddock.com.               IN      A

;; ANSWER SECTION:
www.biddock.com.        3565    IN      CNAME   biddock.com.
biddock.com.            3565    IN      A       76.29.34.164

;; Query time: 1 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Apr  8 18:04:50 2013
;; MSG SIZE  rcvd: 74

```

If canyouseeme shows the port is open, it could be a DNS issue, or you external IP address might have changed.

Here's a dig from my site, for reference.
```
charles@Thor:~$ dig charlesa.net

; <<>> DiG 9.8.1-P1 <<>> charlesa.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59024
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;charlesa.net.                  IN      A

;; ANSWER SECTION:
charlesa.net.           1698    IN      A       199.167.30.117

;; Query time: 0 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Apr  8 18:08:50 2013
;; MSG SIZE  rcvd: 46

```

---

### Post by lisati on 2013-04-08
It's timing out for me. I'm wondering if your ISP has started blocking port 80.

Edit: what I'm seeing via DIG is similar to what CharlesA has reported seeing.

---

### Post by CharlesA on 2013-04-08
> **lisati said:**
> It's timing out for me. I'm wondering if your ISP has started blocking port 80.

Edit: what I'm seeing via DIG is similar to what CharlesA has reported seeing.

Times out for me too, but I can ping it, so that sounds like that might be the case.

---

### Post by danshea on 2013-04-08
hmmm strange. I have port 8080 also. I have no idea why it's not responding now. My external i.p. has not changed, and openport does not see my site either.

---

### Post by danshea on 2013-04-08
I can access my site on my lan by using the domain name, so I assume that port 80 is not blocked.

---

### Post by danshea on 2013-04-08
I can access my site on my lan using the domain name, so I assume that port 80 is not blocked. Weird.....

---

### Post by Doug S on 2013-04-08
All 3 sites from the [other thread ]("http://ubuntuforums.org/showthread.php?t=2132145")from the other day, still work for me.

---

### Post by danshea on 2013-04-08
hi doug, did you refresh? because I can't get to them anywhere..... :-(

---

### Post by Doug S on 2013-04-08
Yes, I refreshed twice.

However, now they (all 3) are not working for me. Odd. Oh... Correction two are just really really slow now, and one is not working. 


[http://www.biddock.com/](http://www.biddock.com/) works, but now slow.
[http://www.socialpitchman.com/](http://www.socialpitchman.com/) works, but now slow.
[http://www.bazoodle.com/](http://www.bazoodle.com/)  seems to have stopped working. (And it was the only site that was more than those little default pages you had the other day.)

---

### Post by CharlesA on 2013-04-08
> **Doug S said:**
> Yes, I refreshed twice.

However, now they (all 3) are not working for me. Odd. Oh... Correction two are just really really slow now, and one is not working. 


[http://www.biddock.com/](http://www.biddock.com/) works, but now slow.
[http://www.socialpitchman.com/](http://www.socialpitchman.com/) works, but now slow.
[http://www.bazoodle.com/](http://www.bazoodle.com/)  seems to have stopped working. (And it was the only site that was more than those little default pages you had the other day.)

I tried all three and they just throw a "The server at domainname is taking too long to respond." error.

It's like the IP is right, but something isn't working.

EDIT: Did canyouseeme tell you port 80 or 8080 was open to the internet? Is this hosted on a residential connection?

Have you tried scanning that IP from outside your local network with something like nmap to see if the ports you think are open are actually open?

---

### Post by Doug S on 2013-04-08
Hi,

O.K. sorry, I was wrong before, now I never get any packet returned from 76.29.34.164.80: however I do get: " ICMP host 192.168.1.102 unreachable, length 60" just like was the problem the other day.

I am using a windows computer and for whatever reason, it behaves like the simple web pages worked after 20 seconds. O.K. so that is annoying.

O.K. so earlier, yes everything was working fine. I went back to my tcpdump logs and looked at the raw traffic. I can see the TCP session open and the "GET" requests and the web page data being sent and such.
Everything was definately O.K. for me roughly 50 minutes ago. I wonder if I got blacklisted somehow. ?? ( I mean I can see blacklisting Charles, but not me. ha, ha)

---

### Post by CharlesA on 2013-04-08
> **Doug S said:**
> ( I mean I can see blacklisting Charles, but not me. ha, ha)

I blame using IE to double check to make sure it wasn't Firefox's fault. :p

---

### Post by CharlesA on 2013-04-08
> **danshea said:**
> I can access my site on my lan by using the domain name, so I assume that port 80 is not blocked.

I guess that depends if you are accessing it from the internal IP when inside the network or if you are accessing it with the external IP and your router supports WAN redirection.

Since both myself and Doug S cannot access any of your sites, it is safe to say there is some sort of problem with port 80 being blocked (or port forwarding went wacky) because we can ping the IP address just fine.

Have you verified the IP of the server hosting the websites and verified port forwarding is setup correctly?

---

### Post by Doug S on 2013-04-09
I am reasonably sure that port 80 is not blocked (upstream from the local server at 192.168.1.102 at least), and reasonably sure that at least the 76.29.34.164 to 192.168.1.102 half of port forwarding is working.
I base this on the ICMP reply:```
2013-04-09 06:51:45.075818 IP 76.29.34.164 > XXX.XXX.XXX.XXX: ICMP host 192.168.1.102 unreachable, length 60
```that I get when trying to send a TCP session open "SYN" packet to 76.29.34.164.80:

As with the [previous thread ]("http://ubuntuforums.org/showthread.php?t=2132145")on this same thing (they should be one thread really), look at your firewall or iptables or whatever and your web server logs and such.
Perhaps have a look at the packet level with tcpdump, or wireshark if you prefer.```
sudo tcpdump -n -nn -tttt -i eth1 port 80
```(change eth1 to whatever your interface is) Do you see the packets arriving at your 192.168.1.102 server? Do you see a reply leaving?

---

### Post by danshea on 2013-04-09
Hi, well since I couldn't figure it out. I decided to reinstall everything, but this time I install ubuntu with openssh and theninstalled nginx with php5-fpm and mysql. right now I am trying to get the domain [www.socialpitchman.com]("http://www.socialpitchman.com") up, I have nginx working over my lan, but I get a 502 error on php. I created a phpinfo file and get the error when I try to go to it. weird. Can you dig socialpitchman.com and see what happens?? Thanks,
Dan

---

### Post by CharlesA on 2013-04-09
Are you sure you have Nginx configured correctly to work with PHP?

I have mine set up like this:

```
server {
        listen 80;
        server_name charlesa.net;
        access_log /var/log/nginx/charlesa.net_access.log;
        root /var/www/charlesa.net;
        index index.html index.htm index.php;

        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
                # With php5-fpm:
                **fastcgi_pass unix:/var/run/php5-fpm.sock;**
                fastcgi_index index.php;
                include fastcgi_params;
        }
}

```

Which version of php did you install? The above config file works fine with PHP5.4 and Nginx 1.2.8-1 (tested on my Debian box, but it should work on Ubuntu).

Check the /etc/log/php5-fpm.log and see if it has any errors.

---

### Post by Doug S on 2013-04-09
Same for me, no packets returned except:```
2013-04-09 20:29:52.329629 IP 76.29.34.164 > XXX.XXX.XXX.XXX: ICMP host 192.168.1.102 unreachable, length 60
```

---

### Post by danshea on 2013-04-10
try with my i.p. 76.29.34.164 and my lan is now 192.168.1.104

---

### Post by Doug S on 2013-04-10
No ICMP "unreachable" now.```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth1 host 76.29.34.164
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-04-10 08:37:16.098118 IP XXX.XXX.XXX.XXX.50605 > 76.29.34.164.80: Flags [S], seq 3760402329, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:16.098364 IP XXX.XXX.XXX.XXX.50606 > 76.29.34.164.80: Flags [S], seq 629044539, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:19.084345 IP XXX.XXX.XXX.XXX.50606 > 76.29.34.164.80: Flags [S], seq 629044539, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:19.084498 IP XXX.XXX.XXX.XXX.50605 > 76.29.34.164.80: Flags [S], seq 3760402329, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:25.090581 IP XXX.XXX.XXX.XXX.50606 > 76.29.34.164.80: Flags [S], seq 629044539, win 65535, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:37:25.090618 IP XXX.XXX.XXX.XXX.50605 > 76.29.34.164.80: Flags [S], seq 3760402329, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:37:37.100424 IP XXX.XXX.XXX.XXX.50610 > 76.29.34.164.80: Flags [S], seq 3164592437, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:40.082520 IP XXX.XXX.XXX.XXX.50610 > 76.29.34.164.80: Flags [S], seq 3164592437, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:37:46.088506 IP XXX.XXX.XXX.XXX.50610 > 76.29.34.164.80: Flags [S], seq 3164592437, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:38:19.285445 IP XXX.XXX.XXX.XXX.50620 > 76.29.34.164.80: Flags [S], seq 3481709119, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:19.286576 IP XXX.XXX.XXX.XXX.50621 > 76.29.34.164.80: Flags [S], seq 252670855, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:22.265872 IP XXX.XXX.XXX.XXX.50620 > 76.29.34.164.80: Flags [S], seq 3481709119, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:22.296991 IP XXX.XXX.XXX.XXX.50621 > 76.29.34.164.80: Flags [S], seq 252670855, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:28.272029 IP XXX.XXX.XXX.XXX.50620 > 76.29.34.164.80: Flags [S], seq 3481709119, win 65535, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:38:28.303148 IP XXX.XXX.XXX.XXX.50621 > 76.29.34.164.80: Flags [S], seq 252670855, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:38:40.270629 IP XXX.XXX.XXX.XXX.50623 > 76.29.34.164.80: Flags [S], seq 3261244509, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:40.317809 IP XXX.XXX.XXX.XXX.50625 > 76.29.34.164.80: Flags [S], seq 3412744677, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:43.264051 IP XXX.XXX.XXX.XXX.50623 > 76.29.34.164.80: Flags [S], seq 3261244509, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:43.326413 IP XXX.XXX.XXX.XXX.50625 > 76.29.34.164.80: Flags [S], seq 3412744677, win 8192, options [mss 1460,nop,wscale 2,nop,nop,sackOK], length 0
2013-04-10 08:38:49.270343 IP XXX.XXX.XXX.XXX.50623 > 76.29.34.164.80: Flags [S], seq 3261244509, win 8192, options [mss 1460,nop,nop,sackOK], length 0
2013-04-10 08:38:49.332476 IP XXX.XXX.XXX.XXX.50625 > 76.29.34.164.80: Flags [S], seq 3412744677, win 8192, options [mss 1460,nop,nop,sackOK], length 0
```

---

### Post by Drenriza on 2013-04-10
Have not read the replies on page #2.

The way i would get a host on a LAN on the WWW, is to create a static NAT rule in your router.
To share your single public ip address and reserve the port 80 for your local server.

So you say, anything that hits the public ip address (random address i created) 171.100.52.1:80 has a static NAT to 192.168.1.1, which is your local server.

Or any other port, just remember which one you use ,) So you can say [http://171.100.52.1:](http://171.100.52.1:)[port number] from another PC.

EDIT.
So i read the replies on #2. And it sounds like you are making it unnecessary complicated for yourself.
How are you even trying to make it public from your LAN to the WWW? It seams like your using some kind of application on the server behind your router on the LAN.

---

### Post by Slim Odds on 2013-04-10
> **danshea said:**
> I can access my site on my lan using the domain name, so I assume that port 80 is not blocked. Weird.....
Of course port 80 is not blocked LOCALLY. He was referring to your ISP blocking port 80 before it gets to you.

---

### Post by danshea on 2013-04-10
Well now when I go to my local i.p. (192.168.1.104) and go to [http://192.168.1.104/phpinfo.php](http://192.168.1.104/phpinfo.php) it pops up a box for me to download the file instead of showing me my php info page. Doug, I don't have an error log file where you show for me to look. Which config file are you referencing? the php.ini or the php-fpm.conf? I am googling and working on it so lets see what happens. the site is [www.socialpitchman.com](www.socialpitchman.com) that I am working on and that page will come up when I go to my lan (192.168.1.104). Now to get it out to the to the net. It has to be something simple that I am missing.

---

### Post by danshea on 2013-04-10
Hey Hey Doug,,,,, you da man. I copied your config to my "socialpitchman.conf" and the phpinfo file works now!!!!  Now the lasty step is how do I get my site to be visible from the net and not just my lan.... :-)

---

### Post by Doug S on 2013-04-10
I think you meant to thank Charles, as I do not know anything about nginx or php5-fpm. I only know about standard LAMP stuff installed with ubuntu server.

On the port 80 blocked or not blocked stuff: We have shown serveral times, over now two threads, that the ISP is not blocking port 80 (or at least, wasn't).

---

### Post by danshea on 2013-04-10
ooops sorry, I did mean Charles. My phpinfo page works, and port 80 is not blocked, so I wonder what the problem could be? I must be missing a setting somewhere, but Nginx does not havbe a ports.conf like apache does. that was the issue in apache, not sure what it is with Nginx.

---

### Post by Doug S on 2013-04-10
I don't know why I was not getting the ICMP reply this morning, but I am getting it now. I think your router still thinks it is supposed to forward port 80 to 192.168.1.102:```
2013-04-10 19:50:05.163075 IP 76.29.34.164 > XXX.XXX.XXX.XXX: ICMP host [COLOR=#ff0000]192.168.1.102 [/COLOR]unreachable, length 60
```

---

### Post by CharlesA on 2013-04-10
> **Doug S said:**
> On the port 80 blocked or not blocked stuff: We have shown serveral times, over now two threads, that the ISP is not blocking port 80 (or at least, wasn't).

I don't know the specifies of how you tested to see if port 80 was open or not, but their site is still timing out for me. I guess they could try changing their port forwarding configuration to use port 8080 and see if they can access the site or not. That would rule out a configuration issue, at least.

---

### Post by danshea on 2013-04-10
try it now doug. is this something I can run?

---

### Post by danshea on 2013-04-10
try it now doug. I think I got it!!

---

### Post by CharlesA on 2013-04-10
> **danshea said:**
> try it now doug. I think I got it!!

Works now. :)

---

### Post by danshea on 2013-04-10
Thanks to all of you and especially Doug and Charles. Now I have a working server running ubuntu with Nginx, php-fpm and mysql. !!  Now comes the fun part..... :-)

---

### Post by Doug S on 2013-04-10
For me all three FQDN addresses go to [http://www.bazoodle.com/](http://www.bazoodle.com/) , but yes it works.

No no no, we are not done yet. Please explain what was wrong and how you fixed it.

---

### Post by CharlesA on 2013-04-11
> **Doug S said:**
> 
No no no, we are not done yet. Please explain what was wrong and how you fixed it.

Yes please. It'll help if someone runs into the same problem in the future.

---

### Post by Drenriza on 2013-04-11
So i am wondering. How did you guys get the site from the LAN to the WWW?

Since (from what i can see) it seams like you used a web-server to act as a router?

---

### Post by danshea on 2013-04-11
since I am running my server through a router, I had to set my "DMZ" to my lan i.p. and my port forwarding to my Lan i.p., then it worked. I just did "ifconfig" to get my lan i.p. (192.168.1.104) and set the both the port forwarding (Http 80) and the DMZ to that i.p. and waalaa, I am now in the process of setting up virtual hosts, so right now socialpitchman.com and bazoodle.com should go to their own folders. I am working on the rest. :-) 

Dan

---

### Post by Doug S on 2013-04-11
Interesting. Is your server setup to always have the internal address of 192.168.1.104? Either via a static IP address or via DHCP where the server knows to always give it the same IP address? (via MAC address for example).

Note that now it is not working again:```
2013-04-11 06:50:33.062266 IP 76.29.34.164 > XXX.XXX.XXX.XXX: ICMP host [COLOR=#ff0000]192.168.1.104 [/COLOR]unreachable, length 60
```

---

### Post by CharlesA on 2013-04-11
> **Doug S said:**
> Interesting. Is your server setup to always have the internal address of 192.168.1.104? Either via a static IP address or via DHCP where the server knows to always give it the same IP address? (via MAC address for example).

Note that now it is not working again:```
2013-04-11 06:50:33.062266 IP 76.29.34.164 > XXX.XXX.XXX.XXX: ICMP host [COLOR=#ff0000]192.168.1.104 [/COLOR]unreachable, length 60
```

My bet is it is still set for DHCP. It would be a good idea to make sure the IP for the server is set for static.

Also, I don't think you'd need the machine in the DMZ, only setup port forwarding.

How did you fix this problem last time?

---

### Post by danshea on 2013-04-11
Yes it is fixed now so that it will go to my lan i.p. on boot. :-)

---


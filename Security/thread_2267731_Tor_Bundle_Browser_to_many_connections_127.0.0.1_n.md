---
title: "Tor Bundle Browser to many connections 127.0.0.1 netstat slow internet"
date: 2015-03-03
forum: Security
---

### Post by HardTrickySecurity on 2015-03-03
Hi guys


I was wondering if what is happening to me is normal. I am using the Tor Bundle Browser then I install proxy switchysharp extension in google chrome so I can use tor there. I know that they say you should not do that cause of leaks and is not recommended. But I am doing it for educational purposes and to learn stuff. Anyway I like to watch youtube videos thats why I prefer to see them in google chrome that uses sandbox security for Adobe Flash Player and java and because it loads them very fast in high definition.
 
My connection to my ISP is working fine, I have a T3 connection and if I connect directly to them it goes fast without any problems.
Now a lot of people say that Tor is very slow, in my case it gives me the same download speed that my ISP is giving me. That is a T3. But only for the first 15 minutes or half an hour sometimes even the first hour I connect to tor, from there the speed starts to go down and down and more slow. Ive been trying to figure it out now for months, whats wrong and what its causing this behavior.


Is this normal behavior when someone use Tor?
Could this be that the tor network is full of hackers doing DoS and DDoS atacks and thats why it goes slow after a while?
The Tor fastest servers cant hold fast speeds for long periods of time?
My ISP dont like their customers to use TOR so they slow down my connection when I am using it?
Is something I should tune up or tweak in my linux OS so I can get rid of the problem?


I end it up in this two websites, one it caught my attention yesterday


[https://bitcointalk.org/index.php?topic=331077.0](https://bitcointalk.org/index.php?topic=331077.0)


[http://rockdio.org/ayudatech/how-to-stop-small-ddos-attacks-some-basic-security-advice/](http://rockdio.org/ayudatech/how-to-stop-small-ddos-attacks-some-basic-security-advice/)


I know that Tor Bundle Browser uses 127.0.0.1 port 9150 socks v5. The website mention the following command, now when I use it I was able to see my connections.


netstat -ntu | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -n




      1 Address
      1 servers)
      1 86.59.119.83
      1 109.163.234.9
     40 127.0.0.1


Now as you can see 127.0.0.1 is going for some heavy stuff, sometimes it goes up to 80 or a 100. But it always start with a low number and then slowly the number starts to go up and up as time passes by. Now my question is there any way I can force less connections, fix, optimize or add security (apparmor) to this 127.0.0.1 localhost so does not slow down my internet connection after a while.


I tried the following procedure, but it didnt work on 127.0.0.1. But it shows how noob I am on this topic. :lolflag:


What interests us here is TCPKILL first we need to install dsniff, in linux distribution: Debian we do:


apt-get install dsniff


Then we run:


tcpkill host xxx.xxx.xxx.xxx


where xxx… is replaced with the identified offending IP address.

---


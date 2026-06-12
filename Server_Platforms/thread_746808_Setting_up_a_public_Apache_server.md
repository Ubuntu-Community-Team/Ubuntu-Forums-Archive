---
title: "Setting up a public Apache server"
date: 2008-04-05
forum: Server Platforms
---

### Post by psychofish25 on 2008-04-05
Could someone link me or post instructions to a tutorial on how to set up a public Apache server? I am completely new to this and I just want to make it so when someone types in my IP Adress, it directs them to a certain webpage.

Thanks,
Jordan

---

### Post by tamoneya on 2008-04-05
to get the server install follow the directions here: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Apache_and_PHP5).

I am not exactly sure what you mean by " directs to a webpage" but by default after you have done as the guide says visiting your IP will display the page /var/www/index.html.  If you wish to redirect them to google you should just write a quick java script redirect to that webpage.  If you want to have it show a page that you wrote yourself just place that webpage in /var/www and name it index.html

---

### Post by psychofish25 on 2008-04-05
I've followed this guide, but when I get someone to type in my IP, it doesn't do anything. How do I make the server public?

---

### Post by superprash2003 on 2008-04-05
you need to open port 80 on your modem for that

---

### Post by psychofish25 on 2008-04-05
It is open, any other reasons why it wouldn't be working? When I type in my public IP, it simply brings me to my modems page. When a friend types it in, they get nothing.

---

### Post by superprash2003 on 2008-04-05
just to make sure try this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by psychofish25 on 2008-04-05
Hm it says I'm not responding on port 80, I guess it isn't open then. I'll go do that right now.

---

### Post by psychofish25 on 2008-04-05
Wait...now it works for me, but still not my friends. I forwarded port 80 and I'm running the server now. Is there anything else I need to do?

```
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

where do i edit ServerName?

---

### Post by scxtt on 2008-04-05
**/etc/hosts** ... make sure you are root:

[indent]**sudo vi /etc/hosts**[/indent]

post the output of **/sbin/ifconfig** as well, if you don't know your LAN ip ...

make an entry like

[indent]<lan ip> <server_name>.localdomain <server_name>[/indent]

ex.
[indent]192.168.1.100 server-1.localdomain server1[/indent]

then restart apache

---

### Post by superprash2003 on 2008-04-05
it should work with default apache settings, have you changed the port it is supposed to listen to?

---

### Post by psychofish25 on 2008-04-05
What do I add to hosts? Just "71.127.251.27 ServerName"?

---

### Post by tgalati4 on 2008-04-05
Make sure you have a fixed local IP address for your server machine.  Make sure you have the appropriate entry in your /etc/hosts file.  Make sure you have port 80 forwarded from your router to your local machine IP.  What kind of router do you have?  How do you get your internet service?  DSL?  Cable Modem?  Some companies block outgoing services.

---

### Post by superprash2003 on 2008-04-05
is 71.127.251.27 your ip? if so, port 80 is still not open

---

### Post by psychofish25 on 2008-04-05
Well I've run servers from my router before. Port 80 is forwarded. And what is the appropriate entry in /etc/hosts? That's what I'm asking.

EDIT: Yes that is my IP and port 80 is forwarded. My server isn't going public because I keep getting a ServerName error. How can I fix this?

---

### Post by superprash2003 on 2008-04-05
i dont think there is any need to edit the /etc/hosts file.. are you using firestarter or any other firewall in ubuntu?

---

### Post by psychofish25 on 2008-04-05
Not that I know of, sorry for being annoying. I'm new to this.

How do I get rid of this ServerName error? Where do I define that?

---

### Post by scxtt on 2008-04-05
i've seen that exact "error", it is definitely because you don't have a FQDN in your /etc/hosts file ...

if you have a router, it seems you should have a LAN IP - i doubt "71.127.251.27" is your LAN IP - it's your WAN IP given to you by your ISP.

---

### Post by psychofish25 on 2008-04-05
> **scxtt said:**
> i've seen that exact "error", it is definitely because you don't have a FQDN in your /etc/hosts file ...

if you have a router, it seems you should have a LAN IP - i doubt "71.127.251.27" is your LAN IP - it's your WAN IP given to you by your ISP.

Well I have 192.168.1.5 as my local IP and 71.127.251.27 as my internet IP. How do I add an FQDN to my /etc/hosts file?

---

### Post by superprash2003 on 2008-04-05
you can find your LAN ip by typing ifconfig in the terminal.. please post the results incase you dont know the LAN ip

---

### Post by psychofish25 on 2008-04-05
> **superprash2003 said:**
> you can find your LAN ip by typing ifconfig in the terminal.. please post the results incase you dont know the LAN ip

```
jordan@Jordan-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:DF:34:0D  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fedf:340d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107803954 (102.8 MB)  TX bytes:8728293 (8.3 MB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56773 (55.4 KB)  TX bytes:56773 (55.4 KB)

```

---

### Post by scxtt on 2008-04-05
add an entry like this to /etc/hosts and restart apache.

192.168.1.2 psychofish25.localdomain psychofish25

---

### Post by superprash2003 on 2008-04-05
and incase you have used 192.168.1.5 to portforward in your router, then change it to 192.168.1.2

---

### Post by psychofish25 on 2008-04-05
> **scxtt said:**
> add an entry like this to /etc/hosts and restart apache.

192.168.1.2 psychofish25.localdomain psychofish25

still getting that ServerName error.

NOTE: apache is an alias for restarting apache

```
jordan@Jordan-PC:~$ apache
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
jordan@Jordan-PC:~$ 

```

---

### Post by psychofish25 on 2008-04-05
> **superprash2003 said:**
> and incase you have used 192.168.1.5 to portforward in your router, then change it to 192.168.1.2

sorry I made a typo before. my ip is 192.168.1.2 and that's what I have port 80 fowarded with.

---

### Post by superprash2003 on 2008-04-05
do you have any other networking device in between? or is it direct from router to computer

---

### Post by psychofish25 on 2008-04-05
> **superprash2003 said:**
> do you have any other networking device in between? or is it direct from router to computer

its direct from my router to PC. It keeps saying it can't find the ServerName, is there something I need to add to httpd.conf or something? I have no idea why it isnt working.

---

### Post by superprash2003 on 2008-04-05
regarding that error 
Troubleshooting

If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to edit

/etc/apache2/httpd.conf

and add

ServerName localhost

at the end of the file.

---

### Post by psychofish25 on 2008-04-05
wouldn't localhost just make it accessible on my network?

---

### Post by superprash2003 on 2008-04-05
no, you are portforwarding right.. so all traffic from outside on port 80 will come to your computer

---

### Post by psychofish25 on 2008-04-05
> **superprash2003 said:**
> no, you are portforwarding right.. so all traffic from outside on port 80 will come to your computer

*sigh* still not working...this is really starting to annoy me. im 100% i have port 80 forwarded correctly. I can type in my IP and get my server, but no one else can.

---

### Post by superprash2003 on 2008-04-05
it could be that your ISP is blocking port 80, some isp's block port 80

---

### Post by psychofish25 on 2008-04-05
okay ill change it to something else

EDIT: It worked!!!! thanks guys!!

---

### Post by superprash2003 on 2008-04-06
please tell us what you did to make it work, also please mark this thread as solved

---

### Post by psychofish25 on 2008-04-06
Well I added "ServerName localhost" to /etc/apache2/httpd.conf. I also port forwarded port 8080 and changed /etc/apache2/httpd.conf to "Listen 8080." This was because Verizon doesn't allow the forwarding of port 80.

Sorry, but how do I mark the thread as solved.

---

### Post by NullHead on 2008-04-07
Use thread tools at the top of the page. Maybe we could all see it? hehe I understand if you don't want to share it :cool:

---


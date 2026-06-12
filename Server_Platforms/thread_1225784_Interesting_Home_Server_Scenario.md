---
title: "Interesting Home Server Scenario"
date: 2009-07-28
forum: Server Platforms
---

### Post by FerociousTwig on 2009-07-28
Ok so I used to have a home server setup working as I wanted it. That was about a month ago. Since then something went wrong. Let me explain.

1) I can connect to apache from inside my LAN on port 81. I changed to port 81 because my father has a windows home server running on port 80.
2) I can ssh into my server from within LAN.
3) I can ssh into my server from outside LAN.
4) I CANNOT connect to apache from outside my lan on port 81. However, I can connect to the Windows Home Server which is as I stated before running on port 80.

Number 4 has provided me with extreme frustration. Router's port forwarding is apparently working with my static IP as sshing works.

Help?

Edit: I should also mention details...
login as: jonathan
[email]jonathan@xx.xx.xx.xx[/email]'s password:
Linux XtremeKaos 2.6.27-14-server #1 SMP Fri Jul 24 23:04:35 UTC 2009 i686

jonathan@XtremeKaos:~$ ifconfig | grep inet
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe87:2e04/64 Scope:Link
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host


jonathan@XtremeKaos:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:81                    *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     15477    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     15613    /var/run/mysqld/mysqld.sock
jonathan@XtremeKaos:~$

---

### Post by bpalone on 2009-07-29
From outside the LAN try it this way:

yourdomain.com:81

I think that will solve your issue.

---

### Post by FerociousTwig on 2009-07-29
Oh I guess I should have mentioned that I've been doing that the whole time.

[http://mydomain.com](http://mydomain.com) OR [https://mydomain.com](https://mydomain.com) take me to the windows home server website. Fine, that is how it should be.

[http://mydomain.com:81](http://mydomain.com:81) SHOULD take me to my homepage served by my apache server, but instead fails to connect page cannot be displayed error.

It should not matter that I don't have a domain at the moment and that its just xx.xx.xx.xx correct? Thanks for the quick reply, but did not solve the problem =( 

Can anybody point me to a good tutorial on how to use wireshark? I'm looking to test to see if my ubuntu server is getting any traffic on port 81. That would tell me whether the problem is before or after the router. Right now I believe the packets (HTTP requests) are never getting through the router forwarded to my computer's static IP...

Heeeeeeelp!:confused:

---

### Post by wojox on 2009-07-29
Is port 443 enabled through port forwarding?
And assigned to your lan ip?

---

### Post by FerociousTwig on 2009-07-29
No, 443 goes to the windows home server. That is only for https though isn't it? 

Remember, I had this working a few months ago with only port... well at that time I was using 8000 instead of 81, but same idea.
8000 was forwarded to my IP and 22 was forwarded to my IP and I could successfully serve web pages and ssh in. Now all I can do is ssh. I have no idea what changed. No ports work for apache anymore.

---

### Post by Rob_H on 2009-07-29
> **FerociousTwig said:**
> Can anybody point me to a good tutorial on how to use wireshark? I'm looking to test to see if my ubuntu server is getting any traffic on port 81. That would tell me whether the problem is before or after the router. Right now I believe the packets (HTTP requests) are never getting through the router forwarded to my computer's static IP...

That'd be my guess, as well. Using Wireshark to see if the packets are getting through is pretty straightforward. Install it on the same box that's running your web server. Then, start it up as root. Go to **Capture > Interfaces** and then next to your network interface card, click on **Options**. You can leave all of the defaults alone, except next to **Capture filter**, type "port 81". Then click **Start**.

Try to hit your web server from outside the LAN. If the traffic is reaching your server, it should show up now in Wireshark. If you don't see anything, port forwarding is probably not configured correctly on your router.

Also, make sure you're not running a software firewall on the web server box that would prevent the traffic from getting through.

---

### Post by wojox on 2009-07-29
Yeah 443 https, but I couldn't get an external connection without it on. went crazy trying to figure that one out.  

I don't know? No new firewall installations lately? How is your dad's server, no problems connecting there on port 80

---

### Post by FerociousTwig on 2009-07-29
Ok problem is I'm running the ubuntu server headless. Can wireshark be installed/run from the cmd line via ssh? I'll look around for some how to's on that...

My father's server on port 80 is working 100% fine and I do not / can not need 443. As I said before I had it working with only one port for http. If somehow that changed and now I do need 443, then I'm boned b/c my father is stubborn and will never take down his WHS which needs https.

---

### Post by FerociousTwig on 2009-07-29
Ok I found a cmd line alternative called tcpdump. I will install that on the ubuntu server and run it on port 81 to see if anything is happening...

---

### Post by kustomjs on 2009-07-29
well you can have port 444 as your SSL connection and you can also have port 81 open.  when you do that make sure you restart apache 

if you running virtual hosting here what your files should look like under apache:

/etc/apache2/sites-available

have a file under youdomain.com.conf

<VirtualHost *:81>
ServerName yourdomain.com
DocumentRoot /var/www/yoursite/
</VirtualHost> 


<VirtualHost *:444>
ServerName secure.yourdomain.com
DocumentRoot /var/www/yoursite
SSLEngine on
SSLCertificateFile /etc/ssl/apache/cbc/conf/xxx/ssl.crt
SSLCertificateKeyFile /etc/ssl/apache/cbc/conf/xxx/ssl.key
   SSLCertificateChainFile /etc/ssl/apache/xxx/conf/cbc/sub.class1.server.ca.crt
   SSLCACertificateFile /etc/ssl/apache/cbc/conf/xxx/ca.crt
</VirtualHost>

also you want go to /etc/apache2/ports.conf file and have them listing to:

Listen 192.168.xx.x:81 
Listen 192.168.xx.x:444



then in putty or any other SSH client do sudo /etc/init.d/apache2 restart


then you should be able get out now after restarting the apache server.

---

### Post by FerociousTwig on 2009-07-29
Alright, got some results. When I accessed my server's web page from within the network (works as it should) then it captured some packets. When I accessed my server's web page from outside the network it had some activity but I don't really know what it was doing cuz I have no experience with packet sniffers. All the while tcpdump was running on the server box itself. Output...


jonathan@XtremeKaos:~$ sudo tcpdump -i eth0 port 81
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
17:27:27.303682 IP c-68-48-41-55.hsd1.md.comcast.net.60367 > 192.168.2.102.81: S 3498814000:3498814000(0) win 8192 <mss 1460,nop,nop,sackOK>
17:27:27.333676 IP 192.168.2.102.81 > c-68-48-41-55.hsd1.md.comcast.net.60367: S 4076372085:4076372085(0) ack 3498814001 win 5840 <mss 1460,nop,nop,sackOK>
17:27:27.305389 IP c-68-48-41-55.hsd1.md.comcast.net.60367 > 192.168.2.102.81: . ack 1 win 17520
17:27:30.302972 IP 192.168.2.102.81 > c-68-48-41-55.hsd1.md.comcast.net.60367: S 4076372085:4076372085(0) ack 3498814001 win 5840 <mss 1460,nop,nop,sackOK>
17:27:36.302971 IP 192.168.2.102.81 > c-68-48-41-55.hsd1.md.comcast.net.60367: S 4076372085:4076372085(0) ack 3498814001 win 5840 <mss 1460,nop,nop,sackOK>
17:27:46.201517 IP c-68-48-41-55.hsd1.md.comcast.net.60367 > 192.168.2.102.81: R 438:438(0) ack 1 win 0
17:27:50.926750 IP 192.168.2.185.62506 > 192.168.2.102.81: S 1821785035:1821785035(0) win 8192 <mss 1460,nop,nop,sackOK>
17:27:50.926846 IP 192.168.2.102.81 > 192.168.2.185.62506: S 145419830:145419830(0) ack 1821785036 win 5840 <mss 1460,nop,nop,sackOK>
17:27:50.927737 IP 192.168.2.185.62506 > 192.168.2.102.81: . ack 1 win 17520
17:27:50.928179 IP 192.168.2.185.62506 > 192.168.2.102.81: P 1:537(536) ack 1 win 17520
17:27:50.928236 IP 192.168.2.102.81 > 192.168.2.185.62506: . ack 537 win 6432
17:27:50.930200 IP 192.168.2.102.81 > 192.168.2.185.62506: P 1:399(398) ack 537 win 6432
17:27:50.963592 IP 192.168.2.185.62506 > 192.168.2.102.81: P 537:874(337) ack 399 win 17122
17:27:50.964645 IP 192.168.2.102.81 > 192.168.2.185.62506: P 399:901(502) ack 874 win 7504
17:27:51.162708 IP 192.168.2.185.62506 > 192.168.2.102.81: . ack 901 win 16620
17:28:05.973040 IP 192.168.2.102.81 > 192.168.2.185.62506: F 901:901(0) ack 874 win 7504
17:28:05.974135 IP 192.168.2.185.62506 > 192.168.2.102.81: . ack 902 win 16620

---

### Post by FerociousTwig on 2009-07-29
@kustomjs
I don't need the secure connection. All I need is an http port. I originally had ports.conf as Listen 81. I tried Listen 192.168.2.102:81 and that did not change anything. 

As for the sites-available configuration I did not bother adding domain but rather just used the default. Is that permissible given that I still changed its port to *:81?

Does anyone know how to interpret the data I got from the packet sniffer? I'd love to know what that means...

---

### Post by kustomjs on 2009-07-30
I just was saying if you needed it that would be the best way to go.

---

### Post by dmizer on 2009-07-30
Why not just forward port 80 on the router to port 81 on the LAN, or is the router forwarding port 80 to the Windows home server?

---

### Post by FerociousTwig on 2009-07-30
Router is forwarding port 80 to the Windows Home Server. 

Another update: [https://www.grc.com/x/portprobe=81](https://www.grc.com/x/portprobe=81)
On my network lists this port as open... That, in conjunction with the fact that tcpdump seemed to get some sort of activity, would lead me to believe the problem is with my actual apache setup. Any ideas on apache?

---

### Post by bpalone on 2009-07-31
Could it be that where you are trying to access from the outside has port 81 blocked?   Just a thought from a quick google search on port 81 that turned this up: [http://www.howtoforge.com/forums/showthread.php?t=228](http://www.howtoforge.com/forums/showthread.php?t=228)

That is what they determined was the problem.

---

### Post by Rob_H on 2009-07-31
> **FerociousTwig said:**
> Does anyone know how to interpret the data I got from the packet sniffer? I'd love to know what that means...

It's not entirely clear what part of the tcpdump output was your internal LAN test and what part was your external WAN test. Assuming the *c-68-48-41-55.hsd1.md.comcast.net* machine is the external one, it certainly looks like traffic is flowing. What do you see in the browser? Seeing the contents of the packets would be helpful, too. There's an option in tcpdump to dump that out, although I don't know it offhand.

---

### Post by FerociousTwig on 2009-08-05
I don't think it has anything to do with port 81 being blocked...

More Packet info...

```
jonathan@XtremeKaos:~$ tcpdump -nnvvXSs 1514 -i eth0 port 81
tcpdump: socket: Operation not permitted
jonathan@XtremeKaos:~$ sudo tcpdump -nnvvXSs 1514 -i eth0 port 81
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 1514 bytes
16:04:28.776887 IP (tos 0x0, ttl 127, id 11049, offset 0, flags [DF], proto TCP (6), length 52) 68.48.41.55.62947 > 192.168.2.102.81: S, cksum 0x68c1 (correct), 1266906151:1266906151(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
        0x0000:  4500 0034 2b29 4000 7f06 a025 4430 2937  E..4+)@....%D0)7
        0x0010:  c0a8 0266 f5e3 0051 4b83 7427 0000 0000  ...f...QK.t'....
        0x0020:  8002 2000 68c1 0000 0204 05b4 0103 0302  ....h...........
        0x0030:  0101 0402                                ....
16:04:28.777794 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 52) 192.168.2.102.81 > 68.48.41.55.62947: S, cksum 0xd5f1 (correct), 3335968019:3335968019(0) ack 1266906152 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
        0x0000:  4500 0034 0000 4000 4006 0a4f c0a8 0266  E..4..@.@..O...f
        0x0010:  4430 2937 0051 f5e3 c6d6 d513 4b83 7428  D0)7.Q......K.t(
        0x0020:  8012 16d0 d5f1 0000 0204 05b4 0101 0402  ................
        0x0030:  0103 0306                                ....
16:04:28.779038 IP (tos 0x0, ttl 127, id 11050, offset 0, flags [DF], proto TCP (6), length 40) 68.48.41.55.62947 > 192.168.2.102.81: ., cksum 0x1c77 (correct), 1266906152:1266906152(0) ack 3335968020 win 4380
        0x0000:  4500 0028 2b2a 4000 7f06 a030 4430 2937  E..(+*@....0D0)7
        0x0010:  c0a8 0266 f5e3 0051 4b83 7428 c6d6 d514  ...f...QK.t(....
        0x0020:  5010 111c 1c77 0000 ba5f e515 3a0d       P....w..._..:.
16:04:32.969834 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 52) 192.168.2.102.81 > 68.48.41.55.62947: S, cksum 0xd5f1 (correct), 3335968019:3335968019(0) ack 1266906152 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
        0x0000:  4500 0034 0000 4000 4006 0a4f c0a8 0266  E..4..@.@..O...f
        0x0010:  4430 2937 0051 f5e3 c6d6 d513 4b83 7428  D0)7.Q......K.t(
        0x0020:  8012 16d0 d5f1 0000 0204 05b4 0101 0402  ................
        0x0030:  0103 0306                                ....
16:04:38.969834 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 52) 192.168.2.102.81 > 68.48.41.55.62947: S, cksum 0xd5f1 (correct), 3335968019:3335968019(0) ack 1266906152 win 5840 <mss 1460,nop,nop,sackOK,nop,wscale 6>
        0x0000:  4500 0034 0000 4000 4006 0a4f c0a8 0266  E..4..@.@..O...f
        0x0010:  4430 2937 0051 f5e3 c6d6 d513 4b83 7428  D0)7.Q......K.t(
        0x0020:  8012 16d0 d5f1 0000 0204 05b4 0101 0402  ................
        0x0030:  0103 0306                                ....
16:04:47.679685 IP (tos 0x0, ttl 127, id 11071, offset 0, flags [DF], proto TCP (6), length 40) 68.48.41.55.62947 > 192.168.2.102.81: R, cksum 0x2bda (correct), 1266906589:1266906589(0) ack 3335968020 win 0
        0x0000:  4500 0028 2b3f 4000 7f06 a01b 4430 2937  E..(+?@.....D0)7
        0x0010:  c0a8 0266 f5e3 0051 4b83 75dd c6d6 d514  ...f...QK.u.....
        0x0020:  5014 0000 2bda 0000 1bda 4f00 1cab       P...+.....O...
^C
6 packets captured
6 packets received by filter
0 packets dropped by kernel
```

Yeah that IP was the external one. Thanks for the continued help guys. Love this community

---

### Post by FerociousTwig on 2009-08-08
Bump!

Nobody?

---

### Post by dmizer on 2009-08-09
It may sound stupid, but have you tried rebooting the router?

---

### Post by Rob_H on 2009-08-09
Sorry, I'm not a tcpdump guru. I think there's a way to configure it to output in a capture format that Wireshark can read, but I don't know the details. Maybe someone else on the forum does...? If you can't run Wireshark on the server, how about on the client? Or the Firebug extension for Firefox would work, too. You can monitor web traffic with the "Net" tab in Firebug.

---

### Post by NightShade03 on 2009-08-09
Two things....

1) Have you tried changing the port back to 8000 to see if that works? ( You mentioned that was what it was at originally)

2) Can you install nmap on another computer on the network an use it scan your linux box, this will tell you what ports are open (just to confirm that port 81 is open).

---


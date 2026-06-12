---
title: "Problem Setting Up Web Server"
date: 2006-10-24
forum: Server Platforms
---

### Post by Jerome36 on 2006-10-24
First off let me apologize for creating yet another one of these threads.  I did some reading, in similar threads, but I haven't been able to solve my problem, so hopefully somebody can help me out.  First off, here's the background information.

I have two computers hooked up to a LAN, and one of those is my Linux box running Ubuntu (Dapper Drake).  It was a regular desktop install, but I later went through the LAMP server setup, and everything works fine with that.  I can view any pages I create, on my linux box, doing say "http://localhost/testphp.php" and I can also view these same pages on my windows machine, if I put the IP address: "http://192.168.0.101/testphp.php" so as far as working over the LAN it works great!

The problem is it's not working outside of the LAN, as none of my friends are able to see anything.  Now, I don't have a Static IP, so I setup an account with DynDNS.org and entered that information into my D-Link DI 604 router.  I also enabled the virtual server, and have the router sending port 80 calls to the Linux box.  My domain name from DynDNS.org is "jchopp.homelinux.com" and if I enter that in the address field, on my Windows machine, again it works great.  Just not outside of the LAN.

Now, I figured perhaps CenturyTel DSL (my ISP) blocks port 80 calls, so I changed the port number, what Apache listens to, in the ports.conf file, located at /etc/apache2/ on the Linux box, and restarted the server.  I also changed the virtual server address, on the D-Link router, to be the new port, and not 80.  I changed it to 801, since for some reason the router wouldn't allow 8080.

Now when I put in [http://jchopp.homelinux.com:801/testphp.php](http://jchopp.homelinux.com:801/testphp.php) in my address bar the page still loads fine, for me, but still doesn't work outside of the LAN.  Along with the D-Link DI 604 router my line goes into a Netopia DSL Modem.  I thought that might be the problem, so for testing purpose I turned the firewall off on that (in the setup), and Enabled both the HTTP server, with port 80, as well as a custom one, doing port 801, which is suppose to forward to the router.  Still no luck.

I'm hoping perhaps somebody has another suggestion, because I've run out of ideas, after tying all of this.  Maybe I'm missing something on my DSL Modem, or a setting somewhere.  I'm not sure.  Anyway, thanks in advance.

](*,) :)

---

### Post by funkyade on 2006-10-24
For dynDNS to work properly you need a DNS updater script running on your server machine. The dynDNS website has quite a few links to these.

You may find that your IP address has changed in the meantime.

You will need to set Apache to listen on any IP so modify the Listen directive to **Listen *:80** or whatever port you want to listen on.

Now the difficult part will be telling your router to forward all requests on port 80 (or whatever) to your server - this is the part I think you are missing. I assume you have some kind of web-based control panel for your router, if so then you need to setup a forward from port 80 (or whatever) on your router to port 80 (or whatever) on your server, so from your routers IP to your servers IP. Obviously you are aware of this already, I can only suggest that you test this by turning off your firewall etc... making sure your server does have a static IP on your LAN and is not getting its IP via DHCP. Make sure you have no firewall or whatever blocking ports on your server too.

I've had a similar problem, which I can't resolve because of my router. Basically, I couldn't get my router to forward consistently, when you accessed the dyndns domain you got the routers control panel!

hth

---

### Post by airtonix on 2006-10-25
You will also proly need to make a rule in your firewall prog on your linux box....
For me i use the firewall front end  "firestarter", and create a rule that allows incoming conenctions on port 80...or whatever port your using.

plus i know you proly dont want to hear this but "Drop Link" routers are not the best.....cisco all the way baby.

---

### Post by Jerome36 on 2006-10-25
Thanks for the replies!

funkyade, I had already setup my router to forward port 80 requests to my Linux Box, via an option in the router's setup called "Virtual Server."  I did what you suggested though, by putting "Listen *:80" in the ports.conf file, and I think that has done it.  A friend of mine was able to access a page.  I'm going to do a little more tweaking and what not.

I'll get one of those DNS updater scripts, though the router is supposedly suppose to do that, and I'll also get firestarter, so I can actually see what's going on.

Thanks again.

---

### Post by Ronbo on 2006-10-25
Who is your ISP,  I know my ISP, Verizon, somehow blocks DynDNS on the D-Link DI-604 even with the URL, username and password.  I bought a Buffalo router entered the info in that and it works like a charm listening on port 8080.

See this link:
[http://www.dslreports.com/faq/verizonfios/1.3%20IP%20addresses%20and%20Port%20Info](http://www.dslreports.com/faq/verizonfios/1.3%20IP%20addresses%20and%20Port%20Info)

---

### Post by Jerome36 on 2006-10-25
My ISP is CenturyTel, which I may have mentioned before.  I don't know if they block DynDNS on the D-Link DI-604, but I'll see what I can find out.  I basically got that particular router because I got it REALLY cheap, and at the time didn't have a lot of money.  Hopefully this DynDNS thing functions properly though.  I haven't had any problems with this router yet *crosses fingers & knocks on wood* :)

---

### Post by Ronbo on 2006-10-25
I got my DI-604 from Verizon when they installed my FIOS.  Actually I don't think you should have the same problem if you don't use Verizon. I think I remember reading somewhere that verizon actually has a their own version of the firmware installed.  So I don't think that is the problem.

Actually the verizon version of the DI-604 is named the VDI-604 (but that's not noted anywhere on the router):

[http://www2.verizon.net/micro/dlink/Default.asp?](http://www2.verizon.net/micro/dlink/Default.asp?)

---

### Post by st_itty on 2006-10-29
Hello guys I too have a similar problem. I cannot access my webserver from outside my network. I have setup my router to forward port 80 to the server and port 22 also to the server for ssh. I use dynamic dns alias setup at dynalias.net I can connecto to my server using ssh at port 22 without any problem. But I cannot access my webserver. The router is forwarding the request to my server have verified it by running netstat when I was trying to access the server from outside I get the following line (I have masked the real ip addresses)
tcp        0      0 server:www               xx.xxx.xx.x:28660   SYN_RECV   -
t
This makes me believe that the router is forwarding the request to the server. Any ideas as to my my webserver isn't returning anything?

---

### Post by MJN on 2006-10-30
Jerome,
 
I've been using the DI-604 for around 5 years now and not had a single problem with it... nice rock-solid router.
 
If you're having problems with the DNS updater on the router then just use a client side one - it'd be advantageous to do this anyway in case, for whatever reason, you end up replacing the router - one less change to have to then subsequently make.
 
Whilst troubleshooting problems like this it's always worth eliminating possible cause hence, in this case, leave DNS out of it for the moment and try accessing your server from outside using its IP address. Remember to include the http:// prefix as many browsers don't work with raw IP address and specifying ports without it.
 
Any joy?
 
Mathew

---


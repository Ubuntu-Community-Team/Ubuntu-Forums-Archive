---
title: "Web server"
date: 2008-01-03
forum: Server Platforms
---

### Post by turbo5speed on 2008-01-03
Hello, i know that this may be an old issue but i tried all the solutions i could find in this forum and still have the same problem.

The thing is, whenever i try to access my web server from outside my network i always get the configure page of my Aolynk DR814 modem/router:(

I tried everything from port forwarding, disabling the remote access to my modem/router config, changing the listening port of my apache server and forwarding it, you name it...nothing works.

Connected to my modem/router i have a machine running Ubuntu Server 7.10 and a laptop running Windows that i use for accesing the server via ssh. The web server, ftp and ssh only work locally.

Help...please:(

Thanks

P.S:Wonderfull forum btw.:)

---

### Post by mattismyname on 2008-01-03
You need to configure your router to forward port 80 to your linux box.  

1) Do you know how to access and change the configuration of your router? (Hint, read the manual)
2) Do you know the ip address of your linux box (hint, run ifconfig from the command line)
3) What brand/model of router do you have?

---

### Post by turbo5speed on 2008-01-04
I already tried to forward port 80 and 8080 to my linux box but it didnt worked.:(

1) Yes i know, i just open my browser and go to 192.168.1.1

2) 192.168.1.100, thats how i connect locally via ssh.

3) I have a Aolynk DR814 ADSL2+ BroadBand Router.

I have DynDNS configured and working. I tried No-Ip with port forwarding and didnt work.

---

### Post by hyper_ch on 2008-01-04
can you make a screenshot of your router's forwarding table so we can see how you configured the port forwarding.

---

### Post by turbo5speed on 2008-01-04
[IMG]http://www.mediafire.com/imageview.php?quickkey=6fzd8xitxt2&thumb=4[/IMG]

I did it like this.

In the above example i had apache listening on port 8080.

---

### Post by turbo5speed on 2008-01-04
[IMG][[IMG]http://www.mediafire.com/imgbnc.php/62c210cadd049ffc4f51e68ed393df6d2g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=6fzd8xitxt2&thumb=4)[/IMG]


Sorry about that :)

Now it should work.

---

### Post by hyper_ch on 2008-01-04
Well, you do router port 80 from the router to port 8080 on the server... you should have four times port 80 in there or make apache listen to port 8080 on the server.

---

### Post by turbo5speed on 2008-01-04
I tried the 2 solutions and it didnt work.

My router has an option for remote admin that enables http access on port 8000. I think that when a web page requests a server on my network he redirects all traffic that is requested on port 80 to port 8000 and displays the login for the config page. I tried to disable this feature and i always get the login for the config page.... this is driving me nuts.

Maybe is something about NAT...i dont know. I think i am missing something on my router config....:(

---

### Post by hyper_ch on 2008-01-04
just enter 4x port 80 in the setup and leave apache default configuration.

---

### Post by Dr Small on 2008-01-04
What IP are you trying to access it from, when outside of your network?
Your internal or external ??

Edit,
Is port 80 open to anyone on your firewall at your linux box, too ?

---

### Post by turbo5speed on 2008-01-04
Didnt work. All i get is the config page login.

---

### Post by turbo5speed on 2008-01-04
Anyone?

---

### Post by mattismyname on 2008-01-05
It would appear your router is configured correctly.  (If you change the local port back to 80).

So, is your webserver (apache) accepting connections properly?  From a machine other than the webserver machine, can you browse to [http://192.168.100.0:80/](http://192.168.100.0:80/)  ?  What does the browser do when you enter that URL?

---

### Post by evymetal on 2008-01-05
It's definately a Router problem. If it was apache then you would just get a "server not found" error.

Home routers are sometimes really annoying.

Were you connecting to your external IP from outside the network? on some routers you can't access your external IP's forwarded ports from inside the network, and it just forwards you to your router page.

If it's still not working then try a hard reset of the router (you'll loose all your settings). There should be a tiny button you need to hold down for about 10-30 seconds while the router power is off.

I wouldn't use 8080 or 8000 for a port since they're commonly used by proxies, you could try using another port.

Hope this helps.

---

### Post by turbo5speed on 2008-01-06
Thanks everyone for the help:)

It's really strange but i solved the problem by re-uploading the firmware into the router...go figure that out.

After i uploaded the firmware i just forwarded the ports i wanted for the web server, ftp and ssh and everything just started to work!!! Wich is kinda odd because i already tried the same solution before...

Anyway, thanks again for the help and congratulations for the great forum...this rookie will be back soon with more strange problems:)

Cya soon

---


---
title: "Apache Webserver Setup Help"
date: 2010-04-25
forum: Server Platforms
---

### Post by Neogenics on 2010-04-25
Hi All,

  I have installed Apache Web Server through the RPM Package Manager and have setup a website. Now it works internally on my local network with all three IP/Address/Localhost. 

The problem I am Having is the outside world cannot access my site. I have already checked the ports.conf file and it's on the default of port 80. I went to my router (a Linksys WRT54G2) and forwarded the port to port 80 for the correct computer in my network. Gave my server a static ip within the network and I am using DynDNS.com for the dynamic ip my ISP gives me. 

I've tried changing the default port it uses to 8080 and then re-forwarding. I restarted Apache and then checked both [http://localhost:8080](http://localhost:8080) (getting the error message from Apache saying the web page requested does not exist) AND [http://localhost](http://localhost) (getting a 404 not found page). 

I know that's a lot of reading but I just wanted to show I have tried everything I can think of.

Thanks for any help or suggestions
Neo

---

### Post by tica vun on 2010-04-25
RPM package manager? Ubuntu uses deb packages.

For starters, try following this guide here and see if it works

[https://help.ubuntu.com/9.10/serverguide/C/httpd.html](https://help.ubuntu.com/9.10/serverguide/C/httpd.html)

---

### Post by Neogenics on 2010-04-26
Thank you for the response on that. But I just mistyped was all. I used synaptics package manager. System>Administration>Synaptics Package Manager.

I have also already been to that guide and tried it that way.

Since my last post I have done a complete un-install of the synaptics one and have built it from source. Same problem exactly. So I'm sure it is something I am doing wrong.

---

### Post by windependence on 2010-04-26
> **Neogenics said:**
> Thank you for the response on that. But I just mistyped was all. I used synaptics package manager. System>Administration>Synaptics Package Manager.

I have also already been to that guide and tried it that way.

Since my last post I have done a complete un-install of the synaptics one and have built it from source. Same problem exactly. So I'm sure it is something I am doing wrong.
This is not Windows. Stop re-installing and let's fix it.

From the SERVER, go to canyouseeme.org and check port 80 to see if it is really open or is it being blocked. Let us know what you find.

Also, what is the URL of your web server? I can run some checks and maybe get a few clues here.

-Tim

---

### Post by Neogenics on 2010-04-26
lol I realize how windowish that sounded. But I've learned from experience the best way to get the install the way I like it is to build from source and the best way to learn more too. Synaptics was my half arsed attempt.  That aside.

Port 80 is indeed blocked at canyouseeme.org, which is what I feared. I'm not sure why changing the config file to a different port just crashes the site all together. 

The site's current address is Neogenics.Homelinux.com
Once I get it all setup I can put the real page up and the permanent Domain. For now I'm just using a test page and old Domain of mine.

*EDIT* Ok I've gone through a bit of work here on this. I don't know how but your last post put me in the right train of thought and I figured out that I was only editing my ports.conf file and then my router. There was another file I missed editing. 
 ~/sites-enabled/000-default
I never changed the port there.

Now to get the page to show I have to type the port after the site. How do I get it just to the domain without the port in the address.

Example Current:
neogenics.homelinux.com:8080

Example I would like to change to
neogenics.homelinux.com

---

### Post by windependence on 2010-04-26
Change your port back to 80 in Apache and you should be fine. Canyouseeme will report the port not open if there is nothing listening on the port and since you have Apache listening on 8080, that is the problem. When you switch it to listen on 80 you will not need to specify the port.

-Tim

---

### Post by Neogenics on 2010-04-26
> **windependence said:**
> Change your port back to 80 in Apache and you should be fine. Canyouseeme will report the port not open if there is nothing listening on the port and since you have Apache listening on 8080, that is the problem. When you switch it to listen on 80 you will not need to specify the port.

-Tim

When I checked if the port was open, Apache/Router was still on port 80. It wasn't until I changed it over to 8080 that the page/port showed up to the outside world at all.

I'm thinking that I am looking for some sort of redirection but I could be wrong. Been searching for a couple hours and haven't been able to figure out just exactly what to search for.

---

### Post by windependence on 2010-04-26
Your IPS may be blocking port 80. If you want to redirect, you can do it for free at no-ip.com.

-Tim

---


---
title: "How can I host a website on my own PC using Ubuntu?"
date: 2010-09-03
forum: Server Platforms
---

### Post by iampriteshdesai on 2010-09-03
I want to host my own website [www.xyz.com](www.xyz.com) on my PC.
I haven't got a domain name or anything. But I read somewhere that it is possible. How can I do this?
Apache?
The website should be accessible to other people via internet.
Can this be done using the Home <not server> version of Ubuntu?

---

### Post by Austin25 on 2010-09-03
You could run Apache without Ubuntu Server Edition, but I highly recommend Ubuntu Server Edition. Do you have any old computers?

---

### Post by user1397 on 2010-09-03
look at the guide in my sig

---

### Post by iampriteshdesai on 2010-09-03
@Austin25 I haven't got an extra PC, just this one...
I have installed LAMP. 

@ubuntuman001 Great article. t will i be able to do that on my current Ubuntu for normal PC edition?
Anyway to do it without again installing Server edition?

---

### Post by Austin25 on 2010-09-03
Well, it should work, but then it will go down if you computer gets turned off.

---

### Post by Sporkman on 2010-09-03
Your ISP has to not block port 80 as well - otherwise you'd need to serve the site on an alternate port. Then, for port 123 for example, visitors would have to type in:

[http://www.xyz.com:123](http://www.xyz.com:123)

---

### Post by Paqman on 2010-09-03
Unless your ISP has given you a static IP you'll also need to use a service like [DynDNS]("http://www.dyndns.com/"). That way when your ISP changes your IP, people will still be able to reach your site.

---

### Post by iampriteshdesai on 2010-09-03
> **Austin25 said:**
> Well, it should work, but then it will go down if you computer gets turned off.
@austin25 so do servers keep running even if you turn them off??  :P

---

### Post by Spice Weasel on 2010-09-03
sudo apt-get install apache2

Congratulations, you are running a web server.

---

### Post by iampriteshdesai on 2010-09-03
I have Lamp isntalled, will that affect this apache2?
Doesnt Lamp come preinstalled with apache?

---

### Post by Sporkman on 2010-09-03
> **iampriteshdesai said:**
> I have Lamp isntalled, will that affect this apache2?
Doesnt Lamp come preinstalled with apache?

LAMP includes apache.

LAMP =
**L**inux
**A**pache
**M**ySQL
**P**HP

---

### Post by epsolon77 on 2010-09-03
The major difference between a server install and a desktop install is that the desktop install has a GUI.  GUI's eat a ton of processing power and memory.  That's resources that can not be used for the server operation.  So in short, you can use the desktop install for a server.  Now a running desktop has you surfing the web, installing and uninstalling programs and packages, accedently clicking the "Update all" button an breaking some dependancy somewhere...ect ect ect.  This is why you normally want a seperate maching running your website.  Fewer things go wrong with machines you don't touch every day.  That is the Sys Admin reasoning for some of the advice given.  That all being said if you want a website for you and a couple buddies to be able to visit and play around with, and if it goes down..eh suckes to be you, but your not losing money, go for it.  That's the most wonderful part of Linux IMHO, you can play.

LAMP should get you up and running for a web server.  Try it.  In your address bar of your favorite browser go to [http://localhost](http://localhost) and see what happens!

---

### Post by iampriteshdesai on 2010-09-03
> **epsolon77 said:**
> The major difference between a server install and a desktop install is that the desktop install has a GUI.  GUI's eat a ton of processing power and memory.  That's resources that can not be used for the server operation.  So in short, you can use the desktop install for a server.  Now a running desktop has you surfing the web, installing and uninstalling programs and packages, accedently clicking the "Update all" button an breaking some dependancy somewhere...ect ect ect.  This is why you normally want a seperate maching running your website.  Fewer things go wrong with machines you don't touch every day.  That is the Sys Admin reasoning for some of the advice given.  That all being said if you want a website for you and a couple buddies to be able to visit and play around with, and if it goes down..eh suckes to be you, but your not losing money, go for it.  That's the most wonderful part of Linux IMHO, you can play.

LAMP should get you up and running for a web server.  Try it.  In your address bar of your favorite browser go to [http://localhost](http://localhost) and see what happens!
yeah, I want to host a site just for the sake of it...
want to see how will it work.

I have isntalled Apache2

---

### Post by samalex on 2010-09-03
I'd suggest using FreeDNS - [http://freedns.afraid.org/](http://freedns.afraid.org/) - for the DNS of your domain, when you register one, and it has a few ways you can keep your IP address on your computer synced with the DNS A Record of your domain name.  They way I do it is via a very long URL they provide for each domain subdomain, and via a cron job I use wget to hit the URL then FreeDNS will update the A Record for that domain with the IP address I'm at. Very simple :)

As a few others noted just verify you have incoming port 80 routed to your computer and verify port 80 isn't blocked.  


HTH,

Sam

---

### Post by iampriteshdesai on 2010-09-03
> **samalex said:**
> I'd suggest using FreeDNS - [http://freedns.afraid.org/](http://freedns.afraid.org/) - for the DNS of your domain, when you register one, and it has a few ways you can keep your IP address on your computer synced with the DNS A Record of your domain name.  They way I do it is via a very long URL they provide for each domain subdomain, and via a cron job I use wget to hit the URL then FreeDNS will update the A Record for that domain with the IP address I'm at. Very simple :)

As a few others noted just verify you have incoming port 80 routed to your computer and verify port 80 isn't blocked.  


HTH,

Sam
i think my port 80 is blocked :P
when i go to it i get enter password..
when i enter it correctly i get details of my router config.

---

### Post by whiskeylover on 2010-09-03
Do a port forwarding from your router to your PC for port 80. 

Then see if you can open the website from outside your home network. If no, then :80 is blocked at the ISP level. In that case, use a different port or a different ISP.

---

### Post by iampriteshdesai on 2010-09-03
> **whiskeylover said:**
> Do a port forwarding from your router to your PC for port 80. 

Then see if you can open the website from outside your home network. If no, then :80 is blocked at the ISP level. In that case, use a different port or a different ISP.
how can i do that?

---

### Post by whiskeylover on 2010-09-03
What brand of router do you have? And were you able to log in to its Admin interface?

---

### Post by iampriteshdesai on 2010-09-03
> **whiskeylover said:**
> What brand of router do you have? And were you able to log in to its Admin interface?
Its a Sterlite router...
yeah i can ogin to the admin area

---

### Post by whiskeylover on 2010-09-03
> **iampriteshdesai said:**
> Its a Sterlite router...
yeah i can ogin to the admin area


A quick google search revealed this

[http://broadbandforum.in/mtnl-broadband/58654-port-forwarding-sterlite-sam-300-a/](http://broadbandforum.in/mtnl-broadband/58654-port-forwarding-sterlite-sam-300-a/)

Does your admin interface have a page like that? If so, try adding a port forward 
Protocol - ALL
Start Port Number - 80
End Port Number - 80
Local IP - the IP of your webserver.

Then save it and let me know for further steps.

---

### Post by iampriteshdesai on 2010-09-03
> **whiskeylover said:**
> A quick google search revealed this

[http://broadbandforum.in/mtnl-broadband/58654-port-forwarding-sterlite-sam-300-a/](http://broadbandforum.in/mtnl-broadband/58654-port-forwarding-sterlite-sam-300-a/)

Does your admin interface have a page like that? If so, try adding a port forward 
Protocol - ALL
Start Port Number - 80
End Port Number - 80
Local IP - the IP of your webserver.

Then save it and let me know for further steps.
done.

---

### Post by whiskeylover on 2010-09-03
Now if you have access to a computer connected to the internet from outside of your home network, try accessing your website.

---

### Post by iampriteshdesai on 2010-09-03
> **whiskeylover said:**
> Now if you have access to a computer connected to the internet from outside of your home network, try accessing your website.
i still get the password required message

---

### Post by Sporkman on 2010-09-03
Try accessing it through [this proxy]("http://www.hidemyass.com/") - i.e. type in your IP address & see what comes up.

---

### Post by iampriteshdesai on 2010-09-03
> **Sporkman said:**
> Try accessing it through [this proxy]("http://www.hidemyass.com/") - i.e. type in your IP address & see what comes up.
Authorization Required

The site [http://pritesh.dyndns.org](http://pritesh.dyndns.org) is requesting a username and password to access the realm "mtnlbroadband".

---

### Post by whiskeylover on 2010-09-03
> **iampriteshdesai said:**
> i still get the password required message

Password required? For an HTTP request?>

---

### Post by iampriteshdesai on 2010-09-03
> **whiskeylover said:**
> Password required? For an HTTP request?>
Authorization Required

The site [http://pritesh.dyndns.org](http://pritesh.dyndns.org) is requesting a username and password to access the realm "mtnlbroadband".

---

### Post by whiskeylover on 2010-09-03
> **iampriteshdesai said:**
> Authorization Required

The site [http://pritesh.dyndns.org](http://pritesh.dyndns.org) is requesting a username and password to access the realm "mtnlbroadband".

I think your ISP is doing some freaky things behind the scene. I'm out of ideas.

---

### Post by Fableflame on 2010-09-03
Isn't hosting a website at home kind of risky?
People accessing a page that's on your IP?
I'm kind of a noob with this kind of thing, but isn't that kind of a security risk?

---

### Post by whiskeylover on 2010-09-03
> **Fableflame said:**
> Isn't hosting a website at home kind of risky?
People accessing a page that's on your IP?
I'm kind of a noob with this kind of thing, but isn't that kind of a security risk?

As long as you're behind a router and only forward the required ports, you should be okay. Lots of people do this.

OP: Try changing the port of your Apache server to 8080. Also port forward 8080 from the router to that computer. Then try opening  [http://pritesh.dyndns.org]("http://pritesh.dyndns.org/"):8080

---

### Post by whiskeylover on 2010-09-03
Mods, can we move this thread to a support forum?

---

### Post by pookiebear on 2010-09-03
This thread scares me for the OP. So I wanted to try to help

there are a few things that have to happen for your website to be viewable from the outside. 

You got the first setup done....LAMP. 

so test that setup by going to this address [http://localhost](http://localhost) while on the hosting computer.

If the site comes up go to the next step. IF not your apache is not answering port 80. Check the software firewall on the computer. And make sure apache service is running.

If the site comes up move on to checking the port forwarding on the router. make sure port 80 is forwarded to the IP address of the computer on the inside. Your router documentation will help but it will only work if it is setup perfectly. 

Once port 80 is forwarded correctly. then you can have the dyndns or other dns forwarder point your domain name to your ip address. Check to confirm your external ip using [http://ipchicken.com](http://ipchicken.com)

good luck. The first time you do this is a huge learning curve. Also once you get it working, SHUT it off immediately. Then go back over the security config of your "Server" since you are opening up a security hole. You want to make doubly sure that people will not be stealing any personal data on your computer by accessing/hacking it through your "site".

---

### Post by koenn on 2010-09-03
> **whiskeylover said:**
> I think your ISP is doing some freaky things behind the scene. I'm out of ideas.
maybe the portforwarding isn't set up right; the passwd prompt you get is from the router"s admin web interface ?

---

### Post by whiskeylover on 2010-09-03
> **koenn said:**
> maybe the portforwarding isn't set up right; the passwd prompt you get is from the router"s admin web interface ?

The prompt had the name of a big ISP in India. So, that's why I assumed it was the ISP. I may be wrong though :/

---

### Post by koenn on 2010-09-03
could be an ISP-branded web interface to the roputer or something ...


or you ended up at a server that belongs to the ISP, due to an error in dyndns config or in the portforwarding :)

---

### Post by TwoEars on 2010-09-03
Alright, can a moderator PLEASE revmoe the URL to this user's server? 
I have MAJOR concerns, as he has remote administration turned on, and a VERY basic password. Change it RIGHT NOW, or suffer major damage to your network via hackers. :|

---

### Post by lisati on 2010-09-03
> **iampriteshdesai said:**
> @austin25 so do servers keep running even if you turn them off??  :P

The answer is "no", for the same reason that it's unreasonable to expect to be able to drive a car when it's switched off.

If you're getting an "authorization required" message when you're trying to access your web page it probably means that port forwarding isn't properly set up. And don't forget to change your router/modem's admin password as soon as possible, otherwise anyone who knows what make and model it is will be able to access your system and get up to mischief.

---

### Post by TwoEars on 2010-09-03
The URL is still in the posts. The site is now down; I hope for your sake that you decided to take it down, and it wasn't some other hacker.

---

### Post by iampriteshdesai on 2010-09-04
> **whiskeylover said:**
> As long as you're behind a router and only forward the required ports, you should be okay. Lots of people do this.

OP: Try changing the port of your Apache server to 8080. Also port forward 8080 from the router to that computer. Then try opening  [http://pritesh.dyndns.org]("http://pritesh.dyndns.org/"):8080
how can i change the port of apache to 8080?

---

### Post by iampriteshdesai on 2010-09-04
password changed....
When i type localhost, i get "Its working" the default homepage for apache.
But if i try to access [http://pritesh.dyndns.org](http://pritesh.dyndns.org) i get authorization required message.
if i try [http://pritesh.dyndns.org:8080](http://pritesh.dyndns.org:8080)
I get Oops! Google Chrome could not connect to pritesh.dyndns.org:8080


I have set the following rules for Dynamic DNS:
Rule	 Application	 Protocol	 Start Port	 End Port	 Local IP Address
1	-	ALL	 8080	 8080	120.60.25.245

---

### Post by FuturePilot on 2010-09-04
> **iampriteshdesai said:**
> 
I have set the following rules for Dynamic DNS:
Rule	 Application	 Protocol	 Start Port	 End Port	 **Local IP Address**
1	-	ALL	 8080	 8080	120.60.25.245

You need to put in your LAN IP address, not your WAN IP address.

---

### Post by iampriteshdesai on 2010-09-04
> **FuturePilot said:**
> You need to put in your LAN IP address, not your WAN IP address.
and how exactly do i do taht?

Isn't there an easy way to this in Ubuntu?
Some application...
HOSTWEBSITEONURPC.deb anyone??

---

### Post by koenn on 2010-09-04
the things you have to do (portforwarding) have nothing to do with ubuntu, but with your router, internet connection, network config, ...

There is already an application to do this : the web page at your router's address - all you have to do is fill in some numbers. 

When I first saw the original post in this thread, my first reaction was "If you're asking those questions, you shouldn't be doing this".  I didn't post them because someone already started explaining stuff, but I still think you should seriously reconsider making your PC publicly accessible.

---

### Post by iampriteshdesai on 2010-09-04
> **koenn said:**
> the things you have to do (portforwarding) have nothing to do with ubuntu, but with your router, internet connection, network config, ...

There is already an application to do this : the web page at your router's address - all you have to do is fill in some numbers. 

When I first saw the original post in this thread, my first reaction was "If you're asking those questions, you shouldn't be doing this".  I didn't post them because someone already started explaining stuff, but I still think you should seriously reconsider making your PC publicly accessible.
Can you give me an example of LAN IP address??

I just want to try this out, just to learn how it works..
i have no intentions of setting a site this way

---

### Post by koenn on 2010-09-04
> **iampriteshdesai said:**
> Can you give me an example of LAN IP address??
192.168.0.1

:-)

> **iampriteshdesai said:**
> 
I just want to try this out, just to learn how it works..
i have no intentions of setting a site this way

that's not what your OP sounds like
> **iampriteshdesai said:**
> I want to host my own website [www.xyz.com](www.xyz.com) on my PC.
The website should be accessible to other people via internet.


---

### Post by iampriteshdesai on 2010-09-04
> **koenn said:**
> 192.168.0.1

:-)



that's not what your OP sounds like
I just want to try this out to see how i can do it...
it obviously wouldn't be a website without an address like xyz.com or dyna.org and if it isn't visible to others on internet

---

### Post by koenn on 2010-09-04
> **iampriteshdesai said:**
> I just want to try this out to see how i can do it...
it obviously wouldn't be a website without an address like xyz.com or dyna.org and if it isn't visible to others on internet

you could try to get a website to work on a private network or in a VM - the internet is not a safe place for exercises like these. 
Did you already forget how you gave the entire world admin access to your router without knowing it, and without realizing the consequences ?

---

### Post by iampriteshdesai on 2010-09-05
> **koenn said:**
> you could try to get a website to work on a private network or in a VM - the internet is not a safe place for exercises like these. 
Did you already forget how you gave the entire world admin access to your router without knowing it, and without realizing the consequences ?

:P
it was a mistake, besides i will just make it once before taking it down.

---

### Post by houndi on 2010-09-05
Unless your ISP has given you a static IP you'll also need to use a service like DynDNS. That way when your ISP changes your IP, people will still be able to reach your site.

---

### Post by koenn on 2010-09-05
> **houndi said:**
> Unless your ISP has given you a static IP you'll also need to use a service like DynDNS. That way when your ISP changes your IP, people will still be able to reach your site.

he already has dyndns

---

### Post by whiskeylover on 2010-09-07
Type "ipconfig" on the command prompt (if you're using windows) or "ifconfig" if using linux, and it should print out a bunch of text; one of the lines should have your internal IP address like "192.168.0.101" or something like that. You should forward port 8080 to this IP.

---

### Post by iampriteshdesai on 2010-09-07
> **whiskeylover said:**
> Type "ipconfig" on the command prompt (if you're using windows) or "ifconfig" if using linux, and it should print out a bunch of text; one of the lines should have your internal IP address like "192.168.0.101" or something like that. You should forward port 8080 to this IP.
great thanks!

---

### Post by memilanuk on 2010-10-01
> How did you get my password?
Are you really this simple?  He knew 'your password' and was able to get in because apparently you have never changed it from the original default one it shipped with from the factory!

> So will me PC be always under threat with the current modem?

So long as you are the current user, most likely so.

> What if I'm on Windows?

Windows or Linux has nothing to do with your inability to secure your router.

> What can I do to safe guard my PC?

At this point... unplug it, give it to someone else and go do your online work from a library or web cafe or whatever they have over there.

---

### Post by iampriteshdesai on 2010-10-01
i had changed the router password to something  different.

---

### Post by memilanuk on 2010-10-01
Maybe the web gui password, but apparently not the one for telnet...

---

### Post by koenn on 2010-10-01
> **memilanuk said:**
> Are you really this simple?  He knew 'your password' and was able to get in because apparently you have never changed it from the original default one it shipped with from the factory!

So long as you are the current user, most likely so.


Windows or Linux has nothing to do with your inability to secure your router.

At this point... unplug it, give it to someone else and go do your online work from a library or web cafe or whatever they have over there.

my thoughts exactly

---


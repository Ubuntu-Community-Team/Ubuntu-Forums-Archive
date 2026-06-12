---
title: "Apache Web Server Post-Installation Help"
date: 2010-12-28
forum: Server Platforms
---

### Post by AdamShumpisxXx on 2010-12-28
Hey, guys. I have a bit of a problem. I have a server running Ubuntu 9.10 Server Edition and it is currently being used as an SFTP server. I run it through a Linksys WRT120N on a static IP (192.168.1.100) and have a DDNS set up through DynDNS masking my real IP address which we'll call "283.65.13.45" for now. We'll also say the DynDNS domain name is "coolserver.dyndns.ws" for now. I can access the server at the local office or through the internet at home by opening Filezilla and typing either 283.65.13.45 or coolserver.dyndns.ws into the Host box and then typing in my username and password. This works flawlessly and has been for about a year.

Here we go...

I have now become interested in hosting my own website. I did some research and figured out I wanted a LAMP (or whatever you call it). I went to this website:

http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp

and did everything to the letter. I get the "It works!" website when I type in 192.168.1.100 into my browser. I get the PHP Info website when I type in "192.168.1.100/info.php". I even get the phpMyAdmin website when I type in "http://192.168.0.100/phpmyadmin/". So, at this point I believe everything works. Here's the bummer. I go to type in coolserver.dyndns.ws into my browser and expect to see the "It works!" website and what do you know...nothing. I get "This webpage is not available." at the top and this as an error message "Error 102 (net::ERR_CONNECTION_REFUSED): Unknown error.". Where did I go wrong?

I also want to add that I've done nothing beyond what is set forth in that tutorial. I'm afraid to do anything until I check with you guys first, haha. Can anyone help me?

What I want out of this whole thing is to be able to type coolserver.dyndns.ws at home and see a website. I would also like to change the website to just www.coolsite.com and still be able to keep coolserver.dyndns.ws for SFTP purposes only. Let me know what I'd have to do! Oh and keep in mind "The more free the better!" when you post.

Thanks to everyone in advance for any help you might give me!!!

---

### Post by AdamShumpisxXx on 2010-12-29
Please? I really need the help.

:cry:

---

### Post by tynin on 2010-12-29
Sounds like it could be a few things.

1) Make sure that 283.65.13.45 is still the DHCP address your ISP assigned you. Maybe your lease expired and you got a new IP?

2) Make sure that coolserver.dyndns.ws is pointing to your current DHCP IP. You can do this by just pinging coolserver.dyndns.ws and seeing what it resolved to. If the IP isn't what your DHCP IP is, then you aren't updating DynDNS's NS.

3) You've already confirmed going to your internal 192.168.1.100 works, however does going to [http://283.65.13.45/](http://283.65.13.45/) take you to the "It works" page? If it doesn't, then you likely don't have your virtualhost setup correctly. Check [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html) for examples.

---

### Post by AdamShumpisxXx on 2010-12-29
> **tynin said:**
> Sounds like it could be a few things.

1) Make sure that 283.65.13.45 is still the DHCP address your ISP assigned you. Maybe your lease expired and you got a new IP?

2) Make sure that coolserver.dyndns.ws is pointing to your current DHCP IP. You can do this by just pinging coolserver.dyndns.ws and seeing what it resolved to. If the IP isn't what your DHCP IP is, then you aren't updating DynDNS's NS.

3) You've already confirmed going to your internal 192.168.1.100 works, however does going to [http://283.65.13.45/](http://283.65.13.45/) take you to the "It works" page? If it doesn't, then you likely don't have your virtualhost setup correctly. Check [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html) for examples.

Thank you very much! That did it. All I had to do was forward port 80 TCP on 192.168.1.100 and I was up in seconds! Rookie mistake, haha. One more question if I may...Now that this is all set up are there any extra measures that should be / need to be taken for security? I know the SFTP portion is secure but I just want to make sure I have the Apache side of things locked down. Thanks again!

---


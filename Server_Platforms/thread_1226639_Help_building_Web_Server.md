---
title: "Help building Web Server"
date: 2009-07-29
forum: Server Platforms
---

### Post by fr0sty on 2009-07-29
Hello there, my name is Frosty and I am trying to create a web server to host my father's web site that I am designing. In school I learned how to create web sites but not how to put them up on the server or how to setup a server. I believe it is because it against the law to teach a minor (I was 15 at the time) how to put content up on the internet. So I missed the most important part.The machine is running Ubuntu Desktop 8.04 and I used the following guide to setup apache. 

[http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06) 

After this point, I have no clue on how to get the finished web pages up to the server. Does it involve that wordpress thing from the guide? Basically heres a list of things I think need to be done to get the server up:

1. How to setup the server to somehow have a static IP address (I am totally lost on how to do that)
2. How do I ftp or upload the webpages to the setup server?

Number 1 is where I am so confused. Any and all help is appreciated. Also my ISP is Roadrunner through brighthouse if this helps any. Thanks once again!

also included is a pic of the custom case I built for it.

---

### Post by emeka on 2009-07-29
If it has access to the internet either connected directly to a DSL/Cable modem or the more likely case through a router then you need to look in to two things:

1) Port forwarding via the the router's configuration page. You'll want to forward at least port 80 for HTTP access and likely 22 so you can SSH in from outside your house/network.

2) Setting up some sort of DNS name. If you don't have a static IP Address then look in to services like [http://www.dyndns.com/](http://www.dyndns.com/). Once you sign up there you can run a client on a computer or even configure some rotuer's to update the DNS name with your current IP every couple hours if it changes.

Good luck and leme know if you'd like more clarification. Running one's own server is a very good feeling. :)

---

### Post by bukwirm on 2009-07-29
You don't need to use Wordpress if you don't want to - Wordpresss is a tool you could use to essentially handle some of the behind-the-scenes details of running a blog. See [the website]("http://wordpress.org/") for more details.

If your website consists of a collection of HTML files, you need to put them somewhere on the server - I usually use /var/www. Then, you need to configure Apache to look there for a website. If you are using the default Apache2 setup, you'll need to modify the file /etc/apache2/sites-available/default and comment out the following section:
```
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
# RedirectMatch ^/$ /apache2-default/
```

You can find more information about configuring Apache on [the website]("http://httpd.apache.org/docs/2.2/").

---

### Post by FerociousTwig on 2009-07-30
Setting up a static IP on your lan is as simple as going to your cmd line and typing 

```
sudo vim /etc/network/interfaces
```

Then enter your information for your static IP. If you do not know your info type 

```
 ifconfig | grep inet 
``` and copy the information from there.
When all is said and done the /etc/network/interfaces file should look something like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```
Now in your router, forward port 80 to the static IP you just set up, for help on your specific router model go to [http://portforward.com](http://portforward.com).

You will also want to install some sort of a fiewall on this webserver of yours, I recommend shorewall or firestarter. These you will need to make rules to allow incoming requests on port 80. Good luck, respond with any other questions.

---

### Post by R.Bucky on 2009-07-30
ok, so there are two kinds of static ip's. you have your internal ip's and then you have an external facing ip. quite a bit different. If you only want to view your pages internally, then you do not need an external ip from your internet service provider. 

next, if you are using a content management system like LoveCMS, Wordpress, or silverstripe, the upload utilities for images and files are built in.

---


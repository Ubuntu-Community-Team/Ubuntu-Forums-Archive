---
title: "All Things To Do With Website Creation"
date: 2012-06-30
forum: Server Platforms
---

### Post by Shadius on 2012-06-30
Hey everybody! :) 

Not sure if I can post this here. I apologize in advance if it's not the appropriate place.

I'm interested in finding out how to start a website. I know nothing about how the process works. If someone could provide some resources that I could use to learn how to create websites, that'd be much appreciated. 

I'd like to start from the beginning, for example, say I want to create a website called *website.com/.org/.net/.info*. How do I go about doing that? Also, does it make a difference whether it's a *.com*, *.org*, *.net*, *.info*, or dot whatever?

---

### Post by lisati on 2012-06-30
*Thread moved to **Server Platforms**.*

There's a bunch of stuff that needs to happen. There are some variations on how to go about this, depending on whether you're using a hosting service or hosting it yourself, but the basic ideas are pretty much the same.

I started by installing Apache (the part which dishes out web content to visitors) inside Ubuntu Server edition on a spare machine, and using a free domain name from [no-ip]("http://no-ip.com"). For preparing the initial content, I used a Windows package - [Web Plus]("http://www.serif.com/web-design-software/?mc=FSSWEBPLUS"). Because I was hosting it myself, I had to take care of a few details like port forwarding on my router, and because at the time I had a dynamic IP address, I also had to take care of updating the relevant DNS records every time my IP address changed.

---

### Post by Ji Ruo on 2012-06-30
Well first step is to register (purchase) the name of the website with a company that provides this service. You can choose whatever suffix you want, as long as the URL is available. .com is still the most popular and will probably more expensive than say .net. Usually you will purchase for a set period of time, say 1 year. You can register a domain for a year for as low as maybe $10.

You then need a web server program, and the hardware to host it on. Apache is the web server application of choice in the open source community, and for the majority of the world's websites. For hardware, you can rent this service from someone. Hiring a virtual server might be advantageous if you were expecting a lot of traffic, and some of the setup might be done for you also. It is also very common to find people who offer some or all of registration, setup, hosting and even content creation. But if you are dealing with a relatively low volume of traffic you can do it on any computer. To do that you would set your home router to accept incoming connections on port 80 and forward them to that computer. This would have the web server (such as apache) running which would send out the webpages. If you have a dynamic IP address from your internet service provider (ISP) you would want to set up automatic updates to the domain name system (DNS) server, so that when your router reconnects as sometimes happens the URL of your website will point to the correct IP address.

Last but not least you will need the content, which is created using hypertext markup language (HTML), or more likely these days XHTML (eXtensible ...) or HTML5. These are all markup languages which means they are a basic text file with the instructions for structuring the document included in the content. These are really simple to make, for example:

```
<html>
<head>
<title>A Basic HTML Document</title>
</head>
<body>
<h1>This is a Basic Web Page</h1>
<p>Isn't it cool?</p>
</body>
</html>
```

You can copy and paste this into a text file, save it as something.html and then 'open with' Firefox or Chromium and you will see it displayed. This is what a web server such as Apache is sending everytime you enter a URL or click on a link. Apache (or any other server) will have a *document root* directory, which is where all the web pages will live. When it receives a request from a client, it looks in this folder for the page (as shown above, just a text file) and if it finds it, sends it back. The web browser on the client computer will then display it. You can add styling using cascading style sheets (CSS), and you can also create dynamic content using JavaScript and also by configuring Apache to run say PHP and adding those scripts.  A good resource to begin learning all of these languages would be [w3schools.com]("http://w3schools.com"). As you can probably tell by the above demo, they are *very* easy to learn.

**A quick demo**

To do it yourself quickly, you could set this up between two computers on your home network. Install and configure Apache on one (you can find instructions in the Ubuntu community documentation). Then, put a simple webpage like the one above in Apache's document root directory and name it index.html. Find the IP of that computer (the server) by going to a terminal and typing ```
ifconfig
``` Lets say it's 192.168.1.100 - On the other computer, if your webpage is index.html, you would type in the address bar of your browser:```
192.168.1.100/index.html
``` and voila, you have made your own web server. From there you could set up a web server accessible to the internet by using your public IP (whatismyip.com) and setting up your router to forward to the computer acting as the server. And so on.

---

### Post by Shadius on 2012-06-30
> **lisati said:**
> *Thread moved to **Server Platforms**.*

There's a bunch of stuff that needs to happen. There are some variations on how to go about this, depending on whether you're using a hosting service or hosting it yourself, but the basic ideas are pretty much the same.

I started by installing Apache (the part which dishes out web content to visitors) inside Ubuntu Server edition on a spare machine, and using a free domain name from [no-ip]("http://no-ip.com"). For preparing the initial content, I used a Windows package - [Web Plus]("http://www.serif.com/web-design-software/?mc=FSSWEBPLUS"). Because I was hosting it myself, I had to take care of a few details like port forwarding on my router, and because at the time I had a dynamic IP address, I also had to take care of updating the relevant DNS records every time my IP address changed.

That....sounds complicated. :confused: Could you explain these:
[LIST] Hosting Service [/LIST]
[LIST]Apache [/LIST]
[LIST]Domain [/LIST]


By the way, thanks for moving the thread to the right place. :)

---

### Post by Shadius on 2012-06-30
> **Ji Ruo said:**
> Well first step is to register (purchase) the name of the website with a company that provides this service. You can choose whatever suffix you want, as long as the URL is available. .com is still the most popular and will probably more expensive than say .net. Usually you will purchase for a set period of time, say 1 year. You can register a domain for a year for as low as maybe $10.

You then need a web server program, and the hardware to host it on. Apache is the web server application of choice in the open source community, and for the majority of the world's websites. For hardware, you can rent this service from someone. Hiring a virtual server might be advantageous if you were expecting a lot of traffic, and some of the setup might be done for you also. It is also very common to find people who offer some or all of registration, setup, hosting and even content creation. But if you are dealing with a relatively low volume of traffic you can do it on any computer. To do that you would set your home router to accept incoming connections on port 80 and forward them to that computer. This would have the web server (such as apache) running which would send out the webpages. If you have a dynamic IP address from your internet service provider (ISP) you would want to set up automatic updates to the domain name system (DNS) server, so that when your router reconnects as sometimes happens the URL of your website will point to the correct IP address.

Last but not least you will need the content, which is created using hypertext markup language (HTML), or more likely these days XHTML (eXtensible ...) or HTML5. These are all markup languages which means they are a basic text file with the instructions for structuring the document included in the content. These are really simple to make, for example:

```
<html>
<head>
<title>A Basic HTML Document</title>
</head>
<body>
<h1>This is a Basic Web Page</h1>
<p>Isn't it cool?</p>
</body>
</html>
```

You can copy and paste this into a text file, save it as something.html and then 'open with' Firefox or Chromium and you will see it displayed. This is what a web server such as Apache is sending everytime you enter a URL or click on a link. Apache (or any other server) will have a *document root* directory, which is where all the web pages will live. When it receives a request from a client, it looks in this folder for the page (as shown above, just a text file) and if it finds it, sends it back. The web browser on the client computer will then display it. You can add styling using cascading style sheets (CSS), and you can also create dynamic content using JavaScript and also by configuring Apache to run say PHP and adding those scripts.  A good resource to begin learning all of these languages would be [w3schools.com]("http://w3schools.com"). As you can probably tell by the above demo, they are *very* easy to learn.

**A quick demo**

To do it yourself quickly, you could set this up between two computers on your home network. Install and configure Apache on one (you can find instructions in the Ubuntu community documentation). Then, put a simple webpage like the one above in Apache's document root directory and name it index.html. Find the IP of that computer (the server) by going to a terminal and typing ```
ifconfig
``` Lets say it's 192.168.1.100 - On the other computer, if your webpage is index.html, you would type in the address bar of your browser:```
192.168.1.100/index.html
``` and voila, you have made your own web server. From there you could set up a web server accessible to the internet by using your public IP (whatismyip.com) and setting up your router to forward to the computer acting as the server. And so on.

That was ***very*** informative! Thank you for taking the time to write all of that. My understanding has increased. :) Seems I will have to learn some programming languages also.

---

### Post by Habitual on 2012-06-30
> **Shadius said:**
> That was ***very*** inforrmative! Thank you for taking the time to write all of that. My understanding has increased. :) Seems I will have to learn some programming languages also.

Yes, [Mad Props]("http://www.bournetoraiseshell.com/article.php/20120630123423659")

---

### Post by sandyd on 2012-06-30
> **Shadius said:**
> That....sounds complicated. :confused: Could you explain these:
[LIST]
[*]Hosting Service
[/LIST]

[LIST]
[*]Apache
[/LIST]

[LIST]
[*]Domain
[/LIST]


By the way, thanks for moving the thread to the right place. :)
1. 
You will either need
a) A hosting service that will host your webpages. A hosting service runs a webserver (likely apache) that will allow others to access your files over the internet.

b) Apache is a webserver. So is nginx, cherokee, lighttpd, .etc .etc .etc

2. A domain name points to your website. I.E., google.com, ubuntuforums.org, ubuntu.com

There are also subdomains, which can be something like ipv6.google.com, 1.ubuntuforums.org, and 2.ubuntu.com

The section after the first dot on the left is called the TLD. The TLD indicates what the domain generally contains - though a lot of weird ones have sprung up now.

Generally,
.com - general use
.org - organizations
.net - networks

There are also country-specific TLDs such as
.co.uk - United Kingdom
.us - United States
.ca - Canada
and a whole lot of others.

---

### Post by Shadius on 2012-06-30
> **sandyd said:**
> 1. 
You will either need
a) A hosting service that will host your webpages. A hosting service runs a webserver (likely apache) that will allow others to access your files over the internet.

b) Apache is a webserver. So is nginx, cherokee, lighttpd, .etc .etc .etc

2. A domain name points to your website. I.E., google.com, ubuntuforums.org, ubuntu.com

There are also subdomains, which can be something like ipv6.google.com, 1.ubuntuforums.org, and 2.ubuntu.com

The section after the first dot on the left is called the TLD. The TLD indicates what the domain generally contains - though a lot of weird ones have sprung up now.

Generally,
.com - general use
.org - organizations
.net - networks

There are also country-specific TLDs such as
.co.uk - United Kingdom
.us - United States
.ca - Canada
and a whole lot of others.

Thank you very much for your explanation.

---

### Post by computerfox on 2012-07-01
1-You need to have a basic understanding of HTML formatting
2-Learn how to write scripts in JavaScript as well as PHP (YOU WILL NEED BOTH BECAUSE THEY ARE USED FOR TWO DIFFERENT THINGS)

3-You would need a domain name: example.com (don't actually try to register that name)

NOTE: THAT MEANS YOU HAVE TO SET UP YOUR DOMAIN WITH A PUBLIC REGISTRAR.  
ADVICE: STAY FAR AWAY FROM GODADDY
FATCOW IS OKAY IF YOU'RE NOT HOSTING ON YOUR OWN SERVER AND YOU DON'T KNOW MUCH, BUT DO BE CAREFUL BECAUSE I HAD TO LEAVE THEM DUE TO THEIR QUALITY OF SERVICE.

1AND1.COM IS GREAT IF ALL YOU WANT TO DO IS REGISTER YOUR DOMAIN WITH THE PUBLIC AND THEN HOST ON YOUR OWN SERVER

4-Then you would need to set up your own server:

a: install ubuntu server edition
b: set up your network with a static public ip address
c: you can install a simple control panel like webmin

NOTE: IT ALSO HELPS IF YOU KNOW A LITTLE BIT ABOUT GRAPHIC DESIGN

Okay, so that's the hardcore overview.  Assuming you're not familiar with the whole scope of starting up a website, simply from your question, let's go over the basics:

1-Know the basics formatting rules via [X]HTML/HTML5 for more media based sites
2-Learn JavaScript and PHP
3-Be able to use photo editing software
4-Register the domain.  If you go to fat cow, this will be included in their services
5-Promote your site like crazy

Also, just to clarify something, with the economy going as it is, people are going back to what they did when the WWW first came out in '91-trying to create multimillion dollar .com's, but the truth is that the majority of those ".com's" crashed miserably.  It's tough work running a site and you NEED to have a niche, something that makes viewers come to your site.  

Anyway, just a little heads up for what's in store and to give you an overview of what you would need.  Good luck!

---


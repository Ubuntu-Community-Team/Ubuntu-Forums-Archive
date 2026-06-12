---
title: "How to prevent website retrieve user information ?"
date: 2009-07-03
forum: Security
---

### Post by ubfu on 2009-07-03
hi , I am new to ubuntu and starting to learn more on security too.
As I know the benefits of ubuntu from security aspect is the execution on permission through password and most port are closed.

But , I am wondering about security through a web site.
While browsing though the webpage , what information will a website collect ? 
Scripts and nasty cookies ? 

What header of request will it collect ?

will it able to collect-Browser details , operating system ,  username on operating system ,  ubuntu root password ????

I was kind of worry what they can do , and how much information they'll collect.
Sorry post a newbie question , was hoping some security expert can explain more on browser fetching request.

Thank you

---

### Post by Boondoklife on 2009-07-03
Well a browser is going to give pretty much the same amount of info no matter the OS, but you can limit some of it by turning off scripts and going through a proxy.

---

### Post by Tibuda on 2009-07-03
> **ubfu said:**
> will it able to collect-Browser details , operating system
Yes, this information is available in the [user agent sent to the server on each request]("http://www.useragent.org/"). You can pretend to use a different browser or OS using the [user-agent switcher extension]("https://addons.mozilla.org/en-US/firefox/addon/59").


>  ,  username on operating system ,  ubuntu root password ????
No.

---

### Post by ubfu on 2009-07-03
> **danielrmt said:**
> Yes, this information is available in the [user agent sent to the server on each request]("http://www.useragent.org/"). You can pretend to use a different browser or OS using the [user-agent switcher extension]("https://addons.mozilla.org/en-US/firefox/addon/59").



No.

I had Install the agent switcher extension.
Was wondering , will it detect my Operating system version , Network card ID , Network card MAC address ?

---

### Post by doas777 on 2009-07-03
> **ubfu said:**
> I had Install the agent switcher extension.
Was wondering , will it detect my Operating system version , Network card ID , Network card MAC address ?

yes and no. a mac address should not be detectable beyond the next-hop-router, but it appears that many network stacks are encapsulating that information higher up in the frame-stack, as I am able to detect remote users macs on some (windows) firewalls, that do not correspond to the mac of my router, cablemodem, or next-hop router on my ISP. I saw recently in the Jammie thomas trial, that media-sentry had obtained her mac address in their scans of her activities. I have no idea why this information is available (as IP routing theory says it shoudln't be there), but i have seen it. if anyone knows how/why, I'd be most appreciative if they could explain it to the both of us.

you can use teh MAC changer script to change your mac at each reboot:
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)  but it probably won't work with NetworkManager since it binds to each card based on the MAC. 

good luck

---

### Post by Tibuda on 2009-07-03
> **ubfu said:**
> I had Install the agent switcher extension.
Was wondering , will it detect my Operating system version, 
Yes, have you visited [http://www.useragent.org/](http://www.useragent.org/) ? When I'm on Ubuntu Firefox it displays:
```
Mozilla/5.0 (X11; U; Linux i686; pt-BR; rv:1.9.0.11) Gecko/2009060308 Ubuntu/9.04 (jaunty) Firefox/3.0.11
```
I just think it is strange that it does not display my OS if I'm using Epiphany
```
Mozilla/5.0 (X11; U; Linux i686; pt-br) AppleWebKit/528.5+ (KHTML, like Gecko, Safari/528.5+) epiphany-webkit
```


> Network card ID , Network card MAC address ?
Not in the HTTP headers sent by your browser requests. Maybe Java applets can see it.

EDIT: doas777 understand more about this.

---

### Post by blackxored on 2009-07-03
Setting up firefox with "User Agent Switcher", "NoScript" and "TorButton" extensions seems to be a cleanest and powerful solution to online privacy, as far as your topic stands.

---

### Post by bodhi.zazen on 2009-07-03
> **ubfu said:**
>  will it able to collect-Browser details , operating system ,  username on operating system ,  ubuntu root password ????

I think these questions indicate you do not have an understanding of how these things work. A web server can not collect this type of information , how would a web server collect your root password ? Ubuntu does not have a root password.

You should read :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Then when you are done, read about web browsers and clients (ie firefox) and what kind of information is collected / transmitted and how, including apache headers and cookies. cookies vary depending if the server is using PHP or Java or what not to set cookies.

---

### Post by lovinglinux on 2009-07-03
A simple thing you can do is to change the **network.http.sendRefererHeader** in the Firefox preferences, so the site doesn't know which page/site you were previously visiting. 

Type **about:config** in the address bar, then search for **network.http.sendRefererHeader**, right-click on it, select **Modify**, then change the value.

> Background

HTTP is the application-layer protocol with which most web pages are transferred. As part of HTTP, requests can include a "Referer" (sic) header that tells the server which page the user was on that initiated the request. Servers use this information to track users' paths through the site and possibly provide additional features.

Additionally, in JavaScript, the current page’s referrer is exposed in the DOM through document.referrer. Scripts running on the page can consult this property to see the same information that was sent in the Referer header.

This preference controls when to send the Referer header and set document.referrer. 

> Possible values and their effects

0 - Never send the Referer header or set document.referrer.

1 - Send the Referer header when clicking on a link, and set document.referrer for the following page.

2 - Send the Referer header when clicking on a link or loading an image, and set document.referrer for the following page. (Default) 

More info: [http://kb.mozillazine.org/Network.http.sendRefererHeader](http://kb.mozillazine.org/Network.http.sendRefererHeader)

Another thing you can do is to use [CustomizeGoogle](https://addons.mozilla.org/en-US/firefox/addon/743) extension to force https on Google sites, to anonymize the Google cookie UID and to avoid sending cookies to Google Analytics.

You can also use the [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) extension to block Google Analytics completely (you need to add [http://www.google-analytics.com/*](http://www.google-analytics.com/*) and [http://www.google.com/analytics/*](http://www.google.com/analytics/*)
 to AdBlock rules).

Another useful extension is [CS Lite](https://addons.mozilla.org/en-US/firefox/addon/5207), which allows better control of cookie permissions from the status bar.

These are the things a can think now. I will post again if I remember additional stuff.

---

### Post by bodhi.zazen on 2009-07-03
As usual, thank you for providing information [lovinglinux]("http://ubuntuforums.org/member.php?u=649167")

---

### Post by lovinglinux on 2009-07-03
> **bodhi.zazen said:**
> As usual, thank you for providing information [lovinglinux]("http://ubuntuforums.org/member.php?u=649167")

You are welcome and thanks for your comment.

---


---
title: "Website can't be browsed on Google Chrome"
date: 2020-03-17
forum: The Cafe
---

### Post by satimis on 2020-03-17
Hi,

OS - Ubuntu 18.04
The new website with only one page additional to the home page
WordPress website

Hi all,

I have a newly built website.  It can be browsed on Firefox without problem.  But it has problem to be browsed on Google Chrome with following warning:```

This site can’t be reached
ERR_CONNECTION_TIMED_OUT

```
If by chance it can be browsed on Google Chrome some content on the page missing.  Please help.  Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2020-03-18
Network or dns problem.

---

### Post by satimis on 2020-03-18
> **TheFu said:**
> Network or dns problem.
Hi,

Thanks for your advice.

This strange problems have been happened here sometimes.  In the past I didn't make any attempt to correct them.

Problem: all my websites (WordPress sites) are hosted on Godaddy Server, about >30 websites for more than 10 years.  All of them work without problem on Firefox but having problem being browsed on Google Chrome.
1. It takes a considerable long time to get them started on screen
2. The background music on the 1st page (Home page) unable to play.

In the past I haven't make attempt to correct the mistakes mentioned.

Until about 5 days ago I built following new website (WordPress website), also hosted on Godaddy server:
[https://world.nowgopublic.com](https://world.nowgopublic.com)

It is only a 2-pages Travel websites at start.
- Home page with background music
- 1st page - Iceland

The website works without problem on Firefox. However it experiences serious problem being browsed on Google Chrome
Problem 1 - it takes prolong time to get the website popup on computer screen
Problem 2 - some images/items on both the Home and 1st webpage disappeared.
Problem 3 - I couldn't login the website, the login page never popup.
Problrm 4 - background on Home page unable to play

I have spent more than one day trying to sort out the problem, according to suggestions found on Internet including reinstalling Google Chrome and using another Ubuntu 18.04 PC, etc. but without result.

About 8 hours ago I have posted my problem on the Help Forum of Google Chrome and am now in anticipation to get some help from them.

That is my present situation.

Regards

---

### Post by sdsurfer on 2020-03-18
> It takes a considerable long time to get them started on screen
Out of the box, this is very likely a problem in how the themes and plugins are configured. Put up a static "hello world" html page and test against it. if the static page loads fast, this issue is with how Wordpress is set up. This is a huge topic, too large to take up here, but you can begin with digging around for "Wordpress Optimization." Website Speed Tests are also helpful in this regard.

> The background music on the 1st page (Home page) unable to play.
<truth>This is going to be browser dependent on how you implement it. You very well may need to do old-school browser identification to make it work. It may also be related to your first problem if it is executed inline.</truth>

<opinion>This is Baaaad. Years ago web guidelines strongly recommended against it, don't do it.</opinion>

At the very least, try removing the music files from the code, see if it improves problem #1.

> The website works without problem on Firefox. However it experiences serious problem being browsed on Google Chrome
Problem 1 - it takes prolong time to get the website popup on computer screen
Completely clear your FireFox browser cache and try reloading. I would  venture to guess that if you developed in FF, you are pulling in a bunch  of cached files, and clearing your cache may exhibit the same problem in FF.

> Problem 2 - some images/items on both the Home and 1st webpage disappeared.
Validate your pages:
[https://validator.w3.org/](https://validator.w3.org/)

Being Wordpress, if you haven't optimized, you are probably not going to like the result. A lot of the warnings you see may be irrelevant, but what you are looking for is malformed HTML, missing tags, stuff like that. Whenever you have cross browser compatibility issues, this will always be your first stop. Get the pages to validate and try again.

> Problem 3 - I couldn't login the website, the login page never popup.
So you hit a link, and a white page appears? In all browsers or just Chrome? The reasons can be far and wide. First I would get on the page, open the page inspector (in either FF or Chrome,)  clear both the Network and console panels, and reload. See what you can see in the console and network tabs. Malformed HTML? Javascript errors? If the front end is not showing any outstanding issues, you will also need to check server logs.

> including reinstalling Google Chrome and using another Ubuntu 18.04 PC, etc. but without result.

It won't matter if it's Linux, Windows, or Macintosh, this is not a system or browser problem, it is a problem with what the browsers are trying to read - on your websites.

Returning to this:
```
ERR_CONNECTION_TIMED_OUT
```

This basically means there is a fundamental element on the web page that is needed to render and the resource never responds. Why it works in FF I don't know (see caching above.) One example might be is the page is rendered with jQuery and you have jQuery on a CDN. The CDN is having an issue, it says "Yes I have that resource, let me go get it" and never responds. Or, your web site could be doing the same thing. If you have ten websites on a single account and someone is DDOS'ing one of them (common with loosely configured Wordpress sites) it may be just too busy to respond to your request.

GoDaddy can help you out with this problem if it persists, but may have to charge you for support as it is a website issue, not likely a server issue. Possibly you are overloading your account limits for disk space and memory usage?

---

### Post by TheFu on 2020-03-18
The domain and DNS records for that domain are really, really, slow. Could Chrome be penalizing the domain for poor performance?
[https://www.extremetech.com/internet/301776-google-plans-to-shame-slow-websites-in-chrome](https://www.extremetech.com/internet/301776-google-plans-to-shame-slow-websites-in-chrome)

Also, if there isn't an SSL version, some browsers have to time out on the SSL before they attempt the non-SSL connection.  I've run into this.

I've also seen where certain browsers ignore /etc/hosts entries and only use DNS.  Bad, bad, bad browsers.

---

### Post by satimis on 2020-03-19
Hi,

Thanks for your further advice.

I can't resolve why this website works without problem on Firefox?

> **sdsurfer said:**
> .......Put up a static "hello world" html page and test against it. if the static page loads fast, this issue is with how Wordpress is set up. This is a huge topic, too large to take up here,......
...... 
Instead of messing up with this websites I would prefer creating a duplicate website with a new subdomain.  My subscription plan with Godaddy is unlimited disk space and unlimited subdomain but limited memory resource.

> 
.....  but you can begin with digging around for "WordPress Optimization." Website Speed Tests are also helpful in this regard.
I'll test it separately because WordPress is running on Godaddy's server NOT on my server.  I can't make any change on its installation.

> 
......
At the very least, try removing the music files from the code, see if it improves problem #1.

I would do it on the new duplicated website, adding background music on an relevant WordPress plugin

> 
Validate your pages:
[https://validator.w3.org/](https://validator.w3.org/)
Output;
```

Sorry! This document cannot be checked.
    Error
    I got the following unexpected response when trying to retrieve <http://world.nowgopublic.com/>:
        500 Can't connect to world.nowgopublic.com:80 (Connection timed out)
    If you made recent changes to your domain name (DNS) configuration, you may also want to check that your domain records are correct, or ask your hosting company to do so.
```
It is very strange
```

HTTP ERROR 404
Problem accessing //www.yahoo.com/. Reason:
    Not Found
Powered by Jetty:// 9.4.z-SNAPSHOT

```
Even Yahoo got problem ???


> 
.....
So you hit a link, and a white page appears? .....
No.

After waiting for a long time following warning popup
```

This site can&#8217;t be reached world.nowgopublic.com took too long to respond.
Try:

Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_TIMED_OUT

[Details]   [Reload]

[Details
Check your Internet connection
Check any cables and reboot any routers, modems, or other network devices you may be using.
Allow Chrome to access the network in your firewall or antivirus settings.
If it is already listed as a program allowed to access the network, try removing it from the list and adding it again.
If you use a proxy server&#8230;
Check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server: Go to the Chrome menu > Settings > Show advanced settings&#8230; > Change proxy settings&#8230; and make sure your configuration is set to "no proxy" or "direct."

```

menu > Settings > Show advanced settings&#8230; > Change proxy settings&#8230;

But I couldn't find "proxy settings"

> 
GoDaddy can help you out with this problem if it persists, but may have to charge you for support as it is a website issue, not likely a server issue. Possibly you are overloading your account limits for disk space and memory usage?
My plan is unlimited disk space.  Yes, I can pay more for increasing memory usuage but I doubt whether it is related?

Regards
satimis

---

### Post by satimis on 2020-03-19
> **TheFu said:**
>  ......
Also, if there isn't an SSL version, some browsers have to time out on the SSL before they attempt the non-SSL connection.  I've run into this.
....... 
Hi,

I know what you were referring to.  I came across that before.

But here on Chrome, no SSL popup for my selection

Regards
satimis

---

### Post by sdsurfer on 2020-03-19
Overall, looking at all your responses, see TheFu's advice. If various websites (yahoo, etc. even the validator) cannot reach your site, you have an issue connecting with it and it is likely a DNS issue.

> **satimis said:**
> Instead of messing up with this websites I would prefer creating a duplicate website with a new subdomain.
That is now an apples to oranges comparison. All I was suggesting is create a static html page, "connect-test.html" or something, and see if it loads. But it's sounding like you have infrastructure issues, this test may not be helpful.

> I'll test it separately because WordPress is running on Godaddy's server NOT on my server.

You cannot modify your Wordpress sites? "Wordpress Optimization" is a topic you can google . . . if you can access the wordpress files, you can do lots of stuff to increase their performance. But again, it's sounding like that is only part of the problem.

> Output;
Sorry! This document cannot be checked.

Yes, if the validator can't even reach your site, this is looking like a DNS or other infrastructure issue.

> My plan is unlimited disk space.  Yes, I can pay more for increasing memory usuage but I doubt whether it is related?

Again, it's looking like you have different issues, but when it comes to WordPress memory is very relevant. An unoptimized Wordpress site can gobble up memory like crazy, mostly due to the loose handling of how it uses the database(s.) Go into your GoDaddy account and look at the memory usage statistics and see if that tells you anything. It is **possible** that if it's using up memory it won't respond, but there is more likely a DNS issue as mentioned.

---

### Post by sdsurfer on 2020-03-19
I suggest you call Godaddy support. While they will charge you for deep debugging, they should be able to give you answers for free as to why the sites aren't accessible.

---

### Post by satimis on 2020-03-19
Hi all,

Problem solved as follows;

On Godaddy cPanel
-> My Applications
world.nowgopublic.com

Location URL
Change```

https://world.nowgopublic.com/
```
To
```

http://world.nowgopublic.com/
```

change -> https: to http:

Exit Godaddy server and reboot PC

On Google Chrome
[world.nowgopublic.com]
Now it works

login also works

but change page -> Iceland
It is rather slow and I have to refresh the browser several times.

Re: background music
Sometime it works but another time fails

I have tried rebooting PC three times to confirm above.

Regards
satimis

---


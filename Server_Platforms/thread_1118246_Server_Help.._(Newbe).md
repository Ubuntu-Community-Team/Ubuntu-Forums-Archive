---
title: "Server Help.. (Newbe)"
date: 2009-04-06
forum: Server Platforms
---

### Post by mojopanelos on 2009-04-06
Hello,

I am wanting to make a server, i have a old pc :). But what do i do once i install Ubuntu server edition?. Like how do i make it so people can see my site from a domain name like "www.musdasdasdsa.com", And this why i want to make a server:

> The first reason is, is that all the host i go with they stay up for like 6 months then just go and i am getting board of it. Second reason is that, i want to lean and i would love to take it into my own hands.


Do you get me guys, i hope you do thanks..

---

### Post by HermanAB on 2009-04-06
To do it properly, you have to register a domain name with [http://www.godaddy.com](http://www.godaddy.com), get a static IP address (small business server account) from your ISP (likely about $10 per month more than you are currently paying) and since this is the first time at it, I would suggest installing regular Ubuntu, not the server version, since you will likely want to have a screen, keyboard and mouse on it.

Finally, you got to install the Apache web server and maybe Citadel for email and whatever else.

---

### Post by madverb on 2009-04-06
Study TCP/IP and DNS.

---

### Post by balloooza on 2009-04-06
I would suggest installing ebox, ebox-platform.com it is a web administration platform, and it will let you setup the server to do simple things like act as a domain server for windows computers, and act as a web server, with no additional configuration, and it will run without a display or mouse (it might need a keyboard to boot) and can be tucked away, and you can use the web administration platform to adjust settings.

---

### Post by albinootje on 2009-04-06
> **mojopanelos said:**
>  I am wanting to make a server, i have a old pc :). But what do i do once i install Ubuntu server edition?. Like how do i make it so people can see my site from a domain name like "www.musdasdasdsa.com", And this why i want to make a server:


If you want reliable hosting and learn how to maintain a server at the same time, i'd go rent some VPS space with full root access through ssh.

Here's an example of a fairly well-known VPS hosting company : [http://vpslink.com/](http://vpslink.com/)

(Disclaimer: I'm not affiliated with them, I don't know them, and if I were to choose a VPS-host I'd take a non-USA one (legal issues), a pro-linux one, and one which is close enough from where I live that I can travel there in case of complaints :) ).

---

### Post by hyper_ch on 2009-04-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by mojopanelos on 2009-04-07
Well, the reason i want to use my own is i can't afford a VPS. also I am going to be hacing a screen on it, also i have domain on godaddy that where i get all of my domins from only.

Plus i have found a tutorial on google for install the server edition. So thats that. 

Thanks for all your help. What would you suggest for saft. like what software?.. 

Thanks alot.. Plus does it cost for mysql & apache?

Thanks :)

---

### Post by albinootje on 2009-04-07
> **mojopanelos said:**
> 
Thanks alot.. Plus does it cost for mysql & apache?


Okay, install Ubuntu on it, it gives you the option to install mysql-server and apache, costs : $0

---


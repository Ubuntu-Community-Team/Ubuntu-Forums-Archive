---
title: "Access local server via IP?"
date: 2009-09-25
forum: Server Platforms
---

### Post by HighlyDubious on 2009-09-25
I realize this is probably a total newbie question, but is there a way to access the Apache server here in my local network, by way of it's external IP? (99.*.*.*)

My goal is to make sure (as near as possible) I'm seeing exactly what would be seen by someone when they type my URL. 

I made a wild guess that it had something to do with the fact that a browser works by sending out it's request via port 80, while at the same time my Apache server is trying to listen on port 80, and therefore neither can resolve the conflict. With that in mind, I told Apache to listen on port 8080, but that didn't work.

So, is there a **simple** way to access my Apache server from the external IP? Or is that something that would having me pulling my hair for hours? (For what it's worth, I've tried a few random free proxies, but the results have been less than desirable.)

If you'd prefer to point me to some good links on the topic, I'd be more than happy to study the information there as well.

Thanks!

---

### Post by gordintoronto on 2009-09-25
Access it by the local IP, such as 192.168.1.101

---

### Post by kay-man on 2009-09-25
Doesn't work for me either. I can ping my external IP address from within my home netword, but I can't access it with a browser. I'm not 100% sure but I think it's the router that doesn't allow this.

Anyway, as long as you use the same browser you'll see the same page, regardless of whether you access it internally or externally.

Paul

---

### Post by Bachstelze on 2009-09-25
> **kay-man said:**
> I'm not 100% sure but I think it's the router that doesn't allow this.

Aye.

---

### Post by amac777 on 2009-09-25
My router doesn't allow that either, so for quick checks to make sure things are working (like port forwarding turned on etc), I use the external web proxy: 

[http://anonymouse.org](http://anonymouse.org)

that will let you see what other people would see if they go to your external ip address.

---

### Post by HighlyDubious on 2009-09-25
> **gordintoronto said:**
> Access it by the local IP, such as 192.168.1.101

I apologize if I was not clear. I want to access my server by its **EXTERNAL** IP address. As in 99.2.xxx.xxx. I've been accessing it by it's LOCAL address (192.168.1.100). That is not what I'm seeking.

In the future I'll try to be more clear when I say I want to access by **EXTERNAL** IP.

Thank you for your help though.

---

### Post by HighlyDubious on 2009-09-25
> **amac777 said:**
> My router doesn't allow that either, so for quick checks to make sure things are working (like port forwarding turned on etc), I use the external web proxy: 

[http://anonymouse.org](http://anonymouse.org)

that will let you see what other people would see if they go to your external ip address.

 Actually, I've tried using  [http://anonymouse.org](http://anonymouse.org)  - as I mentioned:
> **HighlyDubious said:**
> (For what it's worth, I've tried a few random free proxies, but the results have been less than desirable.)

> **kay-man said:**
>  Anyway, as long as you use the same browser you'll see the same page, regardless of whether you access it internally or externally.

Unfortunately, that is not 100% true in this case. I'm trying to teach myself how to use the Google Maps API. If you are not familiar with  doing that, Gmaps requires the use of a 'key' that is only good for the URL where the scripts are actually running. So...

[LIST]
[*] If I use the key for my URL, it will give errors when used from local access.
[*]If I us a key for local access, then the API throws up errors when someone tries to access my pages from the outside world.
[*]Proxies, won't work because Google sees the request as coming from some  URL that does not match my key.
[/LIST]
 So, as I said, anonymouse and other free proxies don't work for this situation, and I'd like to be able to access my server by it's EXTERNAL IP. (Actually, technically, I'd like to access it by it's URL, but at this point, neither URL nor EXTERNAL IP are accessible)

Thanks for your suggestions though.

---

### Post by HighlyDubious on 2009-09-25
> **Bachstelze said:**
> Aye.

Am I to understand from your comment that there is no simple way for me to access my server by using it's EXTERNAL IP or URL? Nothing simple like  port forwarding, or changing my server to listen on port 8080, or some other simple trick I've not tried?

---

### Post by abaden on 2009-09-25
> **HighlyDubious said:**
> Am I to understand from your comment that there is no simple way for me to access my server by using it's EXTERNAL IP or URL? Nothing simple like  port forwarding, or changing my server to listen on port 8080, or some other simple trick I've not tried?

Well you will need to port forward 80 from your internal IP to your external IP first (provided you don't have two interfaces). Then you should be able to access this IP via any external machine (but, unfortunately, not from any internal machine). If you have access to any external terminals, you could do use lynx (one of the more popular command-line style browsers). What's the reason you need to view the server from the external IP? Maybe we can give you another option.


Alex

---

### Post by HighlyDubious on 2009-09-25
> **abaden said:**
> Well you will need to port forward 80 from your internal IP to your external IP first (provided you don't have two interfaces). Then you should be able to access this IP via any external machine (but, unfortunately, not from any internal machine). If you have access to any external terminals, you could do use lynx (one of the more popular command-line style browsers). What's the reason you need to view the server from the external IP? Maybe we can give you another option.


Alex

Yes, I'm already able to access my server from either another PC in my local network, or from a PC outside my network (via the Internet). As mentioned above, I'm trying to use the Google Maps API, and it is fairly particular about what URL it is called from. So my desire is to (somehow) be able to use a PC that is located inside my internal network, to access my server via it's external IP or URL.

Thanks for any help you may be able to offer.

---

### Post by alienatom on 2009-09-25
If I wanted to view my server's website from the outside world but in my home network I'd would make sure I wasn't using a port that my ISP blocks.

For example, you might need to forward a non standard port to the IP your computer resides on in your router. Say, 192.168.1.5 at port 1234 instead of 80 or even 8080. 

You would also have to change your apache ports configuration to match the port you setup. It's in /etc/apache2 the file is ports.conf.

That might be a start. Then go to [http://www.whatismyip.com/](http://www.whatismyip.com/) Copy and paste IP address into your web browser and add a :1234 or whatever your port is.

For example: [http://12.3.456.7:1234](http://12.3.456.7:1234)

---

### Post by amac777 on 2009-09-25
I must admit I was a little offended by the way you dismissed my sincere attempt to help you and also implied that I didn't read your original post and was wasting your time. Your original post is titled "Access local server via IP" and asks about how to use an external IP address to access your local server. Although the responses you got were a little bit unorganized, you were basically told: many routers won't allow this, best to use an internal IP address for website developement, and if you really must see what people on an external network would see use an external proxy. These were valid answers to you original question. Of course they didn't take into account the fact that you actually want google maps to work on two different IP's because you never mentioned any of that...

Anyway, about your google maps question, here are my suggested solutions:

1. Don't use your external IP address to access your server, instead use a URL. There are free services that provide URLs like [www.hopto.org](www.hopto.org) etc and then you can add your personal url to your computer's /etc/hosts file to point to your local IP address. This way, the url will be the same regardless of whether someone uses your website from internal or external to your network and a sinle google key should work on both.

2. I haven't tried this, but since they are free you could probably just request two different google keys (one for internal IP/url and one for external IP/url) and then have your PHP code check to see if you are from local or remote and include the appropriate key. 

Good luck.

---

### Post by HighlyDubious on 2009-09-26
> **alienatom said:**
> If I wanted to view my server's website from the outside world but in my home network I'd would make sure I wasn't using a port that my ISP blocks.

For example, you might need to forward a non standard port to the IP your computer resides on in your router. Say, 192.168.1.5 at port 1234 instead of 80 or even 8080. 

You would also have to change your apache ports configuration to match the port you setup. It's in /etc/apache2 the file is ports.conf.

That might be a start. Then go to [http://www.whatismyip.com/](http://www.whatismyip.com/) Copy and paste IP address into your web browser and add a :1234 or whatever your port is.

For example: [http://12.3.456.7:1234]("http://12.3.456.7:1234/")

I have tried all that you suggested. Unfortunately, the GMaps API key is extremely specific. For example, according to their docs, a key for "[http://foobarblah.com](http://foobarblah.com)" will NOT work for [http://12.3.456.7](http://12.3.456.7) (presuming that 12.3.456.7 was the IP of forbarblah.com. So, in truth, I must admit I was not exactly precise when asking how to connect to the external IP. 

I tried to keep my initial post simple and to the point. Given that (while I'm within my own network) I currently cannot access my site by either the external IP, nor the URL, I felt that if I could solve for one, it would point me to the correct direction to solve for the other. So I must apologize for lack of preciseness in my original post.

---

### Post by HighlyDubious on 2009-09-26
> **amac777 said:**
> I must admit I was a little offended by the way you dismissed my sincere attempt to help you and also implied that I didn't read your original post and was wasting your time. Your original post is titled "Access local server via IP" and asks about how to use an external IP address to access your local server. 

Yes, you are correct. It was wrong of me to not include the word "external" in the title of my post. I can see how it was my failing to not make that clear in my title, even though I said it twice in the post.

> **amac777 said:**
> Although the responses you got were a little bit unorganized, you were basically told: many routers won't allow this, best to use an internal IP address for website developement, and if you really must see what people on an external network would see use an external proxy. These were valid answers to you original question. Of course they didn't take into account the fact that you actually want google maps to work on two different IP's because you never mentioned any of that...

Yes, you are correct, most of the responses I got were valid suggestions for attempting to access my server by its external IP. However, they did not solve my problem. Which is why I added more information (about the Google Maps API key) in a follow-up post.

> **amac777 said:**
> Anyway, about your google maps question, here are my suggested solutions:

1. Don't use your external IP address to access your server, instead use a URL. There are free services that provide URLs like [www.hopto.org]("http://www.hopto.org") etc and then you can add your personal url to your computer's /etc/hosts file to point to your local IP address. This way, the url will be the same regardless of whether someone uses your website from internal or external to your network and a sinle google key should work on both.

Yes, I have an Internet URL. I got the domain name from one free service, and have free hosting from another service. With the net result that if I type my URL from any PC outside my own network, I can get to my website.

Unfortunately, if I type my Internet URL from a PC inside my own network, the connection just times out and my website does not load. 

On the other hand, if I call my server by the name of it's host machine, or by the local IP, then the website will load. Unfortunately, the key for my URL produces errors when I do it that way.

> **amac777 said:**
> 2. I haven't tried this, but since they are free you could probably just request two different google keys (one for internal IP/url and one for external IP/url) and then have your PHP code check to see if you are from local or remote and include the appropriate key. 

Good luck.

Yes, that may be my eventual solution. Given that (so far) I can't find any way to access my server from within my network by using it's Internet URL, then choosing between 2 keys may be my only alternative. Unfortunately, I am literally taking my very first baby steps in creating web content. In the past I've done the tiniest bit of page layout in HTML. But this is my first attempt at javascript, and I've not yet even touched PHP. So, while this may be the solution I ultimately use, at this time I literally don't have a clue how to do it.

Fortunately, Google is a good thing, and I'm guessing that if I look hard enough, I'll find examples of similar code somewhere out on the net.

Bottom line, that's not the solution I was looking for. But if I can't find a way to access my website by using my Internet URL, then it may be the only solution available to me.

Thanks for your suggestions.

---

### Post by amac777 on 2009-09-26
> **HighlyDubious said:**
> Unfortunately, if I type my Internet URL from a PC inside my own network, the connection just times out and my website does not load. 

On the other hand, if I call my server by the name of it's host machine, or by the local IP, then the website will load. Unfortunately, the key for my URL produces errors when I do it that way.

I'm not sure if you understood what I meant for solution 1 so I'll give an example. In the following, I will assume your external URL is [www.example.com](www.example.com) and the local IP address on your local LAN for the server is 192.168.1.6. On the machine where you want to do your website development, edit the hosts file by doing:

```
sudo nano /etc/hosts
```

and add this line:

```
192.168.1.6 [www.example.com](www.example.com)
```

Now, when you call your server by the URL [www.example.com](www.example.com), instead of getting your external IP address from DNS off the Internet, your local hosts file will be used instead and you should see the site. Also, the google map key should work as well because as far as google's scripts are concerned the URL will still match the key.

ps: of course modify the url / local IP address accordingly.

---

### Post by falconindy on 2009-09-26
Have you checked the Apache access and error logs to see what happens when you try to connect to the external IP from inside the network? I spent a couple hours doing something like this a few months ago when I was testing my website to ensure that it was locked down properly.

Also, FWIW, I use my external IP (via DNS) to refer to my computer on a daily basis when I SSH into it from a laptop from across the house (on the same LAN). I suspect this may be a misconfiguration somewhere -- likely Apache.

---

### Post by HighlyDubious on 2009-10-01
> **amac777 said:**
> I'm not sure if you understood what I meant for solution 1 so I'll give an example. In the following, I will assume your external URL is [www.example.com]("http://www.example.com") and the local IP address on your local LAN for the server is 192.168.1.6. On the machine where you want to do your website development, edit the hosts file by doing:

```
sudo nano /etc/hosts
```and add this line:

```
192.168.1.6 [www.example.com]("http://www.example.com")
```Now, when you call your server by the URL [www.example.com]("http://www.example.com"), instead of getting your external IP address from DNS off the Internet, your local hosts file will be used instead and you should see the site. Also, the google map key should work as well because as far as google's scripts are concerned the URL will still match the key.

ps: of course modify the url / local IP address accordingly.

Yes, you are correct, I did not understand your first suggestion.

I've been temporarily (I hope!) pulled away from the Google Maps project to take care of a different project, but when I get back I'll try your suggestion. I'm sure it will work, because as you say, as far as Google is concerned, the URL will be exactly what they require. No doubt this will be a near perfect solution.

Thanks!

---

### Post by HighlyDubious on 2009-10-01
> **falconindy said:**
> Have you checked the Apache access and error logs to see what happens when you try to connect to the external IP from inside the network? I spent a couple hours doing something like this a few months ago when I was testing my website to ensure that it was locked down properly.

Also, FWIW, I use my external IP (via DNS) to refer to my computer on a daily basis when I SSH into it from a laptop from across the house (on the same LAN). I suspect this may be a misconfiguration somewhere -- likely Apache.
In truth, I'm extremely new to the whole field of running my own server. Until 2 weeks ago I didn't have a need. Then suddenly I had to be up and running and producing results virtually overnight. So, to be honest, at this moment I don't even know where the Apache access and error logs would be stored.

As mentioned above, I've been temporarily pulled from the server/google maps project. But when I get back into it, I will definitely look for and check the logs. No doubt there will be some good info there for me to help figure out why you can do what you do, but I can't. So thanks for the good suggestion. Fortunately, with the help from amac777, I should be able to get what I need by editing my local hosts file. But ultimately, (if it's possible), I'd prefer to do it without editing the hosts file. So your suggestion will give me a good start towards that goal when I'm ready to take it to the next step.

Thanks!

---

### Post by HighlyDubious on 2009-10-01
Given the helpful suggestions I've received from **amac777** and **falconindy**, I'm going to go ahead and mark this thread as solved. 

The suggestion from **amac777 **doesn't does *exactly *what I wanted, but it is a very smooth work-around. So I'm sure it will produce virtually the same effect as what I had originally wanted. And no doubt **falconindy**'s suggestions to check the logs will point me in a good direction if/when I try to actually access my server from it's URL (without hacking the local machine's host file). So, between the two, I feel this thread is answered well enough to be [SOLVED] 

Thanks much to Everyone who offered suggestions!

---


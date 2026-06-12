---
title: "Cannot access var/www/index.php from the internet"
date: 2012-03-28
forum: Server Platforms
---

### Post by gillbert on 2012-03-28
I installed apache2, php5 ... on my ubuntu 11.10, to post a php webpage on the internet. I can now access it by [http://127.0.1.1/](http://127.0.1.1/), [http://127.0.0.1/](http://127.0.0.1/) and [http://localhost/](http://localhost/) but not by my ip ([http://x.x.x.x](http://x.x.x.x)). I've been digging around on the internet, but have found nothing.

---

### Post by darkod on 2012-03-28
Is the server on your home, internal network?

Are you talking about the private IP on the internal network, or your public IP that is allocated to your router?

To be able to access it from outside you will need to configure your router to forward port 80 to the server internal IP (and it's best to set up the server with a static IP).

---

### Post by gillbert on 2012-03-28
I am connected with a normal land line. I can ping my own ip from any computer.

I'm not really sure how to forward a port (just tried to find out, without mush luck).

---

### Post by darkod on 2012-03-28
Sorry, but what do you mean by normal land line? Is it ADSL internet?

Also, are we talking about separate machine acting as web server or you installed apache and php on your desktop/laptop? I guess you installed it on your computer, not on a separate machine.

In that case it's best to set the computer with static IP so that it doesn't change it.
Also, you will need to go into the configuration of the ADSL router and forward port 80 to your computers IP.

Even with that, it might not work since many internet providers are blocking having a home web server.

---

### Post by gillbert on 2012-03-28
Sorry, I think it goes under ADSL (the internet is running around in the TV-cables). 

I have installed it on my desktop.

I don't think my ISP is blocking 80, since my friend I just consulted got the (almost) the same set-up running from the same ISP.

---

### Post by gillbert on 2012-03-28
Was a bit stupid, had my computer connected to the internet/TV-cable box through a w-lan. I removed the box in between and now it works!

Still I will play around a bit to see if I get it working with the wireless box as well.

---

### Post by darkod on 2012-03-28
OK then, good you got it going.

---

### Post by gillbert on 2012-03-28
You don't happen to know how this problem is solved, now when it is located?

---

### Post by darkod on 2012-03-29
You mean why doesn't it work when you are connected to wi-fi?

To be honest, I have no idea how it is working at all. When I mentioned port forwarding on the router you seemed confused but without port forwarding it shouldn't work with wired or wireless connections.

You need your router passing the port 80 information to your computer IP. When you are connected by cable you have one IP, when connected by wi-fi another. That might be your issue.

It all depends how are you connected to your internet provider actually. You need to plan to pass the information from the router to your computer.

---

### Post by gillbert on 2012-03-29
Sorry. I solved it just after my last post. As soon as I realized that the ip I was using was my routers ip I logged in to my router and forwarded 80 to my desktop.

But thank you very much anyway.

---

### Post by Insomn1a on 2012-03-29
so confused.... :confused:

---

### Post by darkod on 2012-03-29
> **Insomn1a said:**
> so confused.... :confused:

About?

---

### Post by Insomn1a on 2012-03-29
> **darkod said:**
> About?

still dont understand how it was resolved, unless he just connected his box right into the cable/dsl modem and got a public ip.

edit:
nvm, didnt see last post he made. lol

---

### Post by lisati on 2012-03-29
> **gillbert said:**
> Was a bit stupid, had my computer connected to the internet/TV-cable box through a w-lan. I removed the box in between and now it works!

Still I will play around a bit to see if I get it working with the wireless box as well.

That makes sense: if there's more than one router-like box in between the public internet and the machine that you want to host the website on, each of the boxes in the chain needs to be able to be involved in the port forwarding. When one doesn't (or can't) do what's needed for some reason, things don't always work as you'd like.

---


---
title: "What the??"
date: 2007-07-14
forum: The Cafe
---

### Post by FuturePilot on 2007-07-14
What happened?
[http://ubuntu.beryl-project.org/]("http://ubuntu.beryl-project.org/")
I_am_very_scared :shock:





However, it's in Google's cache as of July 6
[Linky]("http://64.233.167.104/search?q=cache:vB0ZFsjvOIoJ:ubuntu.beryl-project.org/+ubuntu+beryl+project&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

---

### Post by ComplexNumber on 2007-07-14
what do you mean? they look exactly the same to me.

---

### Post by mrgnash on 2007-07-14
Huh?

---

### Post by yabbadabbadont on 2007-07-14
Works fine for me...

---

### Post by FuturePilot on 2007-07-14
This is what I see.
:shock:

---

### Post by starcraft.man on 2007-07-14
> **ComplexNumber said:**
> what do you mean? they look exactly the same to me.

Ditto. What is supposed to have happened?

---

### Post by FuturePilot on 2007-07-14
See other post.
Is someone in my box?
:shock:

---

### Post by starcraft.man on 2007-07-14
> **FuturePilot said:**
> This is what I see.
:shock:

Uh, that is scary.... seriously.... >.>.

I dunno what it is though, site works fine for me.

---

### Post by yabbadabbadont on 2007-07-14
If you are using any proxy servers, try disabling them and clearing your cache.

---

### Post by illu45 on 2007-07-14
Hm... Well, maybe its because I'm running windows ATM, but I'm seeing the weird dancing things too.

---

### Post by ComplexNumber on 2007-07-14
> **starcraft.man said:**
> Ditto. What is supposed to have happened?
see the post above ;). you probably didn't see that post when you posted because you both posted at the same time.
[B]
FuturePilot[/B]
no idea why you see that. sure you haven't been hacked or something?  this is what i see

---

### Post by FuturePilot on 2007-07-14
I just cleared the cache, and it's still there. No proxies either. :shock:

---

### Post by Polygon on 2007-07-14
i see the ubuntu beryl project page powered by "falcon" whatever that is...

its looks like ytmnd or something has permanently attached itself to your browser lol

---

### Post by aks44 on 2007-07-14
FuturePilot & illu45, what IP address does **ping ubuntu.beryl-project.org** return you? Looks like a DNS problem to me (here I get 80.77.247.17 and no problems viewing the correct page).

---

### Post by ComplexNumber on 2007-07-14
strangely enough, it seems to be in the google cache because i've just put "bow before her" and "osaka" into google and it gives me this:

it's not there now though. odd :confused:

---

### Post by illu45 on 2007-07-14
> **aks44 said:**
> FuturePilot & illu45, what IP address does **ping ubuntu.beryl-project.org** return you? Looks like a DNS problem to me (here I get 80.77.247.17 and no problems viewing the correct page).

I also get 80.77.247.17

---

### Post by FuturePilot on 2007-07-14
```
nick@FeistyFawn:~$ ping ubuntu.beryl-project.org -c3
PING ubuntu.beryl-project.org (208.113.193.9) 56(84) bytes of data.
64 bytes from quandary.dreamhost.com (208.113.193.9): icmp_seq=1 ttl=45 time=94.6 ms
64 bytes from quandary.dreamhost.com (208.113.193.9): icmp_seq=2 ttl=45 time=92.7 ms
64 bytes from quandary.dreamhost.com (208.113.193.9): icmp_seq=3 ttl=45 time=92.1 ms

--- ubuntu.beryl-project.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 92.108/93.148/94.626/1.102 ms

```
That's what I got from the ping

Now it's different
```
PING ubuntu.beryl-project.org (195.114.19.35) 56(84) bytes of data.
64 bytes from beryl-project.org (195.114.19.35): icmp_seq=1 ttl=49 time=140 ms
64 bytes from beryl-project.org (195.114.19.35): icmp_seq=2 ttl=49 time=143 ms
64 bytes from beryl-project.org (195.114.19.35): icmp_seq=3 ttl=49 time=144 ms

```

---

### Post by ComplexNumber on 2007-07-14
[B]FuturePilot & illu45
[/B]are you not blocking scripts in firefox? i wonder if its a script of some sort that is causing the screen to appear like that.
i've got my NoScript firefox plugin to block all scripts.

---

### Post by FuturePilot on 2007-07-14
No script blocking extensions here.
I just installed NoScript and it's still there.

---

### Post by aks44 on 2007-07-14
> **ComplexNumber said:**
> [B]FuturePilot & illu45
[/B]are you not blocking scripts in firefox? i wonder if its a script of some sort that is causing the screen to appear like that.
i've got my NoScript firefox plugin to block all scripts.

Not a script matter, I just tried enabling scripts and I still get the correct page...

Weird...

---

### Post by yabbadabbadont on 2007-07-14
Since your DNS returns a different address, try entering 80.77.247.17 directly into the URL bar in Firefox and see what happens.

Edit: I just did that and it took me to the messed up page....  but if I use the text address, it goes to the correct one.  :?

---

### Post by Ralob on 2007-07-14
Odd, when I type in "bow before her" osaka into google, I see the "you have reached the shrine" etc. But when I click on the link it is the way it should be. lol, this is definitely weird. :confused:

---

### Post by ComplexNumber on 2007-07-14
the thing is, if you put in "you have reached the shrine of osaka" into google, you will see that there are some other people who are seeing it too. i don't know why some people are seeing that message and some people aren't.

---

### Post by FuturePilot on 2007-07-14
Weird. Look at this
[http://www.youtube.com/watch?v=wnJKwq-CUjc]("http://www.youtube.com/watch?v=wnJKwq-CUjc")

---

### Post by yabbadabbadont on 2007-07-14
There must be a round robin DNS sitting on that domain name.  Just like Gentoo uses for its distfiles mirrors.  ```
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (88.191.250.18) 56(84) bytes of data.
64 bytes from absinthe.tuxfamily.net (88.191.250.18): icmp_seq=1 ttl=53 time=125 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 125.905/125.905/125.905/0.000 ms
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (82.140.42.54) 56(84) bytes of data.
64 bytes from 82-140-42-54.static.servage.net (82.140.42.54): icmp_seq=1 ttl=51 time=205 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 205.581/205.581/205.581/0.000 ms
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (80.77.247.17) 56(84) bytes of data.
64 bytes from lupine.me.uk (80.77.247.17): icmp_seq=1 ttl=56 time=120 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 120.881/120.881/120.881/0.000 ms
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (208.113.193.9) 56(84) bytes of data.
64 bytes from quandary.dreamhost.com (208.113.193.9): icmp_seq=1 ttl=48 time=68.7 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 68.741/68.741/68.741/0.000 ms
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (195.114.19.35) 56(84) bytes of data.
64 bytes from beryl-project.org (195.114.19.35): icmp_seq=1 ttl=53 time=140 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 140.641/140.641/140.641/0.000 ms
/home/daffy $ ping -c 1 ubuntu.beryl-project.org
PING ubuntu.beryl-project.org (88.191.250.18) 56(84) bytes of data.
64 bytes from absinthe.tuxfamily.net (88.191.250.18): icmp_seq=1 ttl=53 time=125 ms

--- ubuntu.beryl-project.org ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 125.588/125.588/125.588/0.000 ms

```
Some of the sites included in the round robin must have been hijacked.

---

### Post by myoungf1 on 2007-07-14
> **yabbadabbadont said:**
> Since your DNS returns a different address, try entering 80.77.247.17 directly into the URL bar in Firefox and see what happens.

Edit: I just did that and it took me to the messed up page....  but if I use the text address, it goes to the correct one.  :?


I just copied the ip address into a blank Konqueror tab and guess what the weird osaka thing came up for me but when i enter the url from above I get to the proper page

---

### Post by ComplexNumber on 2007-07-14
> **myoungf1 said:**
> I just copied the ip address into a blank Konqueror tab and guess what the weird osaka thing came up for me but when i enter the url from above I get to the proper page
that sounds like its a DNS matter. some people use the address of their router as their DNS server. some people use the address of their ISP. some people use their own IP, etc. i wonder if that is the reason.
 i'm using my routers address for the DNS.

---

### Post by FuturePilot on 2007-07-14
> **yabbadabbadont said:**
> Since your DNS returns a different address, try entering 80.77.247.17 directly into the URL bar in Firefox and see what happens.

Edit: I just did that and it took me to the messed up page....  but if I use the text address, it goes to the correct one.  :?

Still took me to that freaky dance.

Yeah, if I ping once and repeat it, the address is different every time.
It left and came back:shock:

---

### Post by aks44 on 2007-07-14
> **yabbadabbadont said:**
> Since your DNS returns a different address, try entering 80.77.247.17 directly into the URL bar in Firefox and see what happens.

Edit: I just did that and it took me to the messed up page....  but if I use the text address, it goes to the correct one.  :?

I just entered the raw IP address instead of the DNS name (which anyway is still cached to point to this address) and landed on the wrong page too. :s

---

### Post by smbm on 2007-07-14
I get the weirdness too (with the ip address, with the url I get the regular website). I had a slightly different problem a while ago with the medibuntu site. It just didn't work for me but seemed to work for everyone else.

Could it be something to do with the caching proxies that some isps use to speed things up?

Just a thought.

Very very bizarre site to be redirected to though.

---

### Post by smartboyathome on 2007-07-14
I think someone hacked the site, origionally had a re-direction link, and then the link went away. The IPs were from the re-direction.

---

### Post by ComplexNumber on 2007-07-14
> **smartboyathome said:**
> I think someone hacked the site, origionally had a re-direction link, and then the link went away. The IPs were from the re-direction.
yeah, i think that sounds quite plausible.

---

### Post by H.E. Pennypacker on 2007-07-14
I just saw the dancing girl too.  Totally cool.

---

### Post by smartboyathome on 2007-07-15
> **H.E. Pennypacker said:**
> I just saw the dancing girl too.  Totally cool.

Totally CREEPY!

---

### Post by Wiebelhaus on 2007-07-15
eh , same here with the address typed I see the page , Paste the IP I get that feakyass dancing thingie , someone's messing around. lol

---

### Post by FuturePilot on 2007-07-15
> **H.E. Pennypacker said:**
> I just saw the dancing girl too.  Totally cool.

Totally scary [IMG]http://www.mysmiley.net/imgs/smile/scared/scared0003.gif[/IMG] lol

---


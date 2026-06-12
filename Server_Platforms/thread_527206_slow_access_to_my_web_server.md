---
title: "slow access to my web server"
date: 2007-08-16
forum: Server Platforms
---

### Post by seng1978 on 2007-08-16
hi, i posted this thread in the absolute beginner forum and they referred me to here.
well, the thing is im running a colocated webserver with 10Mbit/s up/down running apache 2.2 on win2003. virtual host handling 6 web  domains. when i was using windows (apparently IE as browser) i never had any problems viewing my web pages(ultra fast)
However, accessing my web pages with ubuntu firefox or netscape is ultra slow. it takes me a few minutes to get one pciture.
Im running VMServer on my ubuntu and using XP's IE on my virtual machine accessing my website is ULTRA FAST.
Again, using ubuntu's firefox and firefox is like waiting for server.......


all my ubuntu installation(i installed on four different computers already) experienced the same slowlines.

I  got to mention one thing though:
I got my very old laptop installed with ubuntu and had the same thing accessing my webpages very slow. But on this laptop i tried to figure out how to do activex for firefox and some other stuff and all of a sudden accessing my websrver was as fast as using IE. But i dont know how i did that. I would like to know how so i can go ahead confiuring my other computers and future computers. 

By the way, accessing other websites such google,yahoo,etc from my ubuntu firefox is ultra fast.

Please help!!

---

### Post by meatpan on 2007-08-16
Can you clarify a few things?  It seems like there could potentially be a few bottlenecks here, and you will get the most benefit by focusing on one problem at a time.

o Are you accessing web pages locally or remotely (to the server)?  Have you tried both?  Along the same lines, are you running your tests from within the same network?
o Can you quantify or estimate the speed difference?  Are we talking minutes or seconds?

---

### Post by seng1978 on 2007-08-16
Can you clarify a few things? It seems like there could potentially be a few bottlenecks here, and you will get the most benefit by focusing on one problem at a time.

o Are you accessing web pages locally or remotely (to the server)? Have you tried both? Along the same lines, are you running your tests from within the same network?
o Can you quantify or estimate the speed difference? Are we talking minutes or seconds?


i access my websites remotely, no i havent tried both yet. i can do that tomorrow, i dont have my website on my computer...

yes i tried of course on the same line. as i said...i was running XP in VM on Ubuntu the access to my web page took 5 seconds.

on the same line with ubuntu firefox (same system by the way) took me (if it got to the page at all) 10 minutes or so

all within the same network, same DSL

---

### Post by foxylad on 2007-08-16
Without more information, I'd suspect DNS. What happens when you type the ip address in directly, instead of the domain name?

---

### Post by freebeer on 2007-08-16
Is this slowness restricted to just your server(s) or does it happen with all sites?  If the latter, it may be just as simple as turning off IPv6 in firefox.

---

### Post by seng1978 on 2007-08-16
Is this slowness restricted to just your server(s) or does it happen with all sites? If the latter, it may be just as simple as turning off IPv6 in firefox.

it happens to some sites, like mine and ubuntu forum so far.
Others such as googel,yahoo,etc access is very fast.

I already turned off IPv6 in mozilla, same slow :(

---

### Post by seng1978 on 2007-08-17
please i really need help, im thinking to change our whole office to ubuntu, but i need to get my employees to my web server as fast as they r now using windows. 
please!!

---

### Post by meatpan on 2007-08-20
Hello Seng,

Assemble a list of all the suggestions you have received in this thread, and then post your efforts to systematically address each one of them.  It looks like there are quite a few suggestions you haven't tried, or tried and did not post the results.

---

### Post by MJN on 2007-08-20
Are your wesites accesible from the Internet? If so, post a URL and then we'll be able to check from here otherwise, as others have touched, we're stabbing in the dark when it comes to assisting with finding the fault(s).

As meatpan says, there are too many potential factors - external access will at least eliminate your clients from the equation (whilst also proving the DNS configuration).

Mathew

---

### Post by seng1978 on 2007-08-24
alrite
i tried every suggestion on the post already. None of them work.

Yesterday I went to check my old laptop again, which has ubuntu feisty installed and accessing my webserver is is really fast. (as fast as using IE)

Long story short:

Try access this and u will see for urself

[http://218.83.152.245:1500/](http://218.83.152.245:1500/)
I will attach screenshot showing u how the website lookslike, in case u cant open at all

Short story long:

i just wanted to repeat my four computers, 2 running feisty ubuntu, 1 debian ubuntu and 1 feisty edubuntu all access 218.83.152.245:1500 slow

Except for my laptop...I just dont remember what i installed in that guy.
I even access my webserver from cell phone faster using GPRS.


And again, yes all from one and the same network with one DSL line.

Please help!!!

---

### Post by freebeer on 2007-08-24
I tried your connection... but I don't think it was a valid test.  I thought the page loaded in an acceptable amount of time (but that is such a subjective call).  I'm on a relatively slow machine with a slow connection so, for me, it loaded "normally".  I'd have to try it again from home where I have a better connection.

---

### Post by seng1978 on 2007-08-25
hey freebeer

u got home yet?


please ppl, try to acces the link with a fresh installation of ubuntu (u can run it on virtual machine as well)

---

### Post by freebeer on 2007-08-25
Yeah.. I did and I tested it... looks like my reply to that test didn't take for some reason.  :(

Anyhow... I thought the response time was a little laggy, but nothing awful or bad.  But it's kind of hard to tell, since it's just a splash screen and it's hard to tell just how much data is being transferred to display that screen.

Actual performance, once logged in, is the important issue.  (How quickly the screens refresh when you're actually interacting with the site.)

For what it's worth, I don't have Japanese (?) characters installed on this machine, so I also don't know how this might affect speed.

---

### Post by freebeer on 2007-08-25
My bad... I guess they're Chinese characters.  :oops:

I also tried it on another box (this time an Ubuntu one - the first one was a Windows box).  Pretty much the same results.  My ping time to the site is about 300ms.  I didn't time it with any accuracy, but it felt like it loaded in about 2 seconds... maybe 3.

---

### Post by seng1978 on 2007-08-26
hey freebeer and co.

i created a username for u

login use login name: freebeer
passwrod:                  test963852741

i get the sqame ping result for ubuntu and windows either.
so with ping u cant get a result. 

as I said, the best is to try a fresh ubuntu install because u might have stuff intalled that makes it "normal" to access my webserver, as i have one old laptop with ubuntu feisty that does access my webserver as fast as using windows IE. This machine has pentium 2 266mhz and I dont remember what codec or whatsoever i installed to make it access my webserver so fast.

Please go ahead and try ur ubuntu installation. If you stil lthink its fast, then please try a fesh installation of ubuntu. Thanks'

Oh by the way I ping my server with 17ms (windows and ubuntu gt same ping result)

Seng

---

### Post by southernman on 2007-08-26
Earlier I tried the link to your site, but it was incredibly slow! Here are the results of pinging you from Mississippi USA:

> PING 218.83.152.245 (218.83.152.245) 56(84) bytes of data.
64 bytes from 218.83.152.245: icmp_seq=1 ttl=112 time=824 ms
64 bytes from 218.83.152.245: icmp_seq=2 ttl=112 time=697 ms
64 bytes from 218.83.152.245: icmp_seq=3 ttl=112 time=896 ms

--- 218.83.152.245 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 697.783/806.256/896.436/82.128 ms



---

### Post by seng1978 on 2007-08-26
hey southerman,

as i said pingng my web server is no use, because though ping from ubutu and window are the same speed but loading the website or gettting any data from the server using ubuntu is way way way slower than using windows. I have to compare OS rather than browsers because I used netscape and konquerer on ubutu and they all access the webserver slow. In addition, RDP is very slow to my server as welll.
Lets say everything is slow to my server accept PING.

The reason why it is so slow from missisppi USA doesnt neccesarily have to do with my webserver. It rather has somethingto do wtih DSL provider and the servers u access un between ur DSL server and my server.
Iaccess servers in the states very slow either. (Examply hotmail with over 400ms)

---

### Post by MJN on 2007-08-26
> **seng1978 said:**
> hey freebeer and co.

i created a username for u

login use login name: freebeer
passwrod:                  test963852741

I can confirm that the site is loading incredibly slowly  from here (UK) and a packet trace seems to suggest the packet sizes are too big and are getting fragmented after leaving your machine. This leads to endless retransmissions which is slowing the whole thing down.

> i get the sqame ping result for ubuntu and windows either.
so with ping u cant get a result.Not with a basic ping no, but if you alter the packet size (-s <size>) and forbid fragmentation (-M do) you can see that the biggest data size transmittable is 972 bytes:

```

$ ping -M do -s 973 218.83.152.245
PING 218.83.152.245 (218.83.152.245) 973(1001) bytes of data.

--- 218.83.152.245 ping statistics ---
16 packets transmitted, 0 received, 100% packet loss, time 15001ms

$ ping -M do -s 972 218.83.152.245
PING 218.83.152.245 (218.83.152.245) 972(1000) bytes of data.
980 bytes from 218.83.152.245: icmp_seq=1 ttl=100 time=539 ms
980 bytes from 218.83.152.245: icmp_seq=2 ttl=100 time=538 ms
980 bytes from 218.83.152.245: icmp_seq=3 ttl=100 time=530 ms

--- 218.83.152.245 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 530.751/536.208/539.734/4.003 ms
```Hence, the maximum single-packet data size is 972 bytes which, with a 28 byte header, gives an MTU of 1000 bytes.

Try lowering your MTU to 1000 on the Windows box as it may well be you've got some tunnelling or other header wrappers at your end (or en route) which is making the packets too big forcing fragmentation and retransmissions.

> Please go ahead and try ur ubuntu installation. If you stil lthink its fast, then please try a fesh installation of ubuntu. Thanks'You must be joking - we'll give you a hand but doing all the dirty work of a fresh install is pushing expectations somewhat. You can quite easily do that yourself on a friends machine, your own laptop connected via another provider etc.

Mathew

---

### Post by freebeer on 2007-08-26
Any chance that you were working on the server when I did my tests? (roughly at the time of this post)

I logged in with my windows box, and now I see what you mean by slow.  Yeah, there's definitely an issue there.  I tried with my Ubuntu 6.06 box and I couldn't complete the log-in process.  It hung, waiting for data, with the page about 90% complete.

I happen to have a relatively fresh Ubuntu 7.04 install as well (nothing tweaked on it - just using it for testing).  I tried logging in with that, too and I couldn't get much further than a 20% page load before it was starved for data.  (I wasn't able to log out of the previous session, due to the unfinished page load, so that may have affected my second log in attempt.)

I'm no expert, or even a power user with regards to diagnosing network issues, but it would appear to be a data transmission error/problem as MJN suggest.

Any chance that this is an IPv6 issue?

---

### Post by seng1978 on 2007-08-28
hey mjn,

u wrote:
Hence, the maximum single-packet data size is 972 bytes which, with a 28 byte header, gives an MTU of 1000 bytes.

Try lowering your MTU to 1000 on the Windows box as it may well be you've got some tunnelling or other header wrappers at your end (or en route) which is making the packets too big forcing fragmentation and retransmissions.

I would like to know if my MTU already is that low at as you said 972, then shouldnt i higher MTU to 1500?

Thank you all (MJN, freebeer and co) for careful review.

---

### Post by MJN on 2007-08-28
No, the MTU (Maximum Transmission Unit), is the maxiumum packet size that can be sent without being fragmented (being split into two or more parts).
 
Fragmentation is bad as it takes time to chop the packets up and recombine them again whilst also handling everything that's necessary to keep things moving along.
 
If fragmentation is necessary somewhere along the way it's considerably better to simply send packets small enough such that it can get from end to end without any fragmentation - siure there is a performance hit (the data to header ratio increases) but it's less than the fragmentation that would otherwise occur.
 
In this case the biggest packet size (without fragmentation) has been determined as 1000 bytes and so you must reduce yuor default of 1500 down to 1000 to avoid this fragmentation 'en route'. Increasing the MTU would simply cause more fragmentation and make the problem worse.
 
Are you saying that your MTU is already set to 972/1000?
 
Mathew

---

### Post by seng1978 on 2007-08-28
alrite MJN,

i changed it to 1000 MTU now.
However, I dont see any speed increase :(

what can i do?

---


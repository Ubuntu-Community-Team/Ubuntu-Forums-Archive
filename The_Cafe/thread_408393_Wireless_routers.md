---
title: "Wireless routers"
date: 2007-04-13
forum: The Cafe
---

### Post by grogoreo on 2007-04-13
Hi

Could someone please suggest a good standard wireless ADSL router? I have a Linksys WAG54G and it's just terrible and heard a big buzz about the WRT54G. I'm not really interested in having linux on the router, I just want it to keep the connection and have the signal be strong going through walls. [This]("http://www.consumersearch.com/www/computers/wireless-routers/index.html") page says that the Linksys is best for this.

Excuse me if this is the kind of posts for the Ubuntu forums.

Thanks,
Greg

---

### Post by tgalati4 on 2007-04-13
If you use Ubuntu, then there is nothing wrong with posting here.  If you don't then you should try it and let us know how well it works for you.

As far as wireless, there's a lot to consider:

1.  What is wrong with the WAG54G?  Can you summarize the problems?

2.  Most wireless problems can be traced to bad position, bad channel selection, and yes, there is a lot of bad hardware out there.  

3.  If you buy a new router, determine the return policy.  You want to be able to test it for 30 days.  If it passes that then you should be good for the next year or so.

4.  Post lots of details and you will get informative answers.  Otherwise you will only get general answers because we have no idea what you are trying to accomplish.

I personally have had good luck with a Netgear A and G band router.  The firmware actually supports automatic IP updating with dyn.org if you have some websites registered with a dynamic IP assignment.  I think it can handle 20 port-forwards.  It won't run openWRT.  I don't have a Linksys, so I can't comment on what additional capability if offered, but don't discount it because you may find that you want to try it to gain extra functionality.

Linksys does have a multi-antenna wrt54gx4 which can help with signal problems.

My netgear is only a single stick, but I added a Windsurfer coffee-can antenna.  I can get a signal from 4 houses away by using Kismet to measure the signal while walking around.

Also, consider the quality of your pcmcia cards or usb dongles.  I've had $7 cheapie cards work really well, and $100 cards that were intermittent.  So only testing in your environment with your hardware will really tell what works.

In other words, our advice is really meaningless.  One test is worth a thousand expert opinions.  

I had a friend buy a Linksys Wireless camera--couldn't get it to work.  Quick google search and I discovered that he was not alone.  Hundreds of others had the same problem.  So beware, there is some junky hardware out there.

Good luck.

---

### Post by onesojourner on 2007-04-13
I was a big fan of d-link mostly from a price stand point but I switched to the WRT54G and I installed dd-wrt on it. I must say this is one awesome peice of equiptment. I never have to restart. the new WRT54G is not as good as the older versions. Look for the WRT54GL thats just like the old WRT54G, not that the new WRT54G are bad.

---

### Post by Obor on 2007-04-13
I have the WRT54G and I'm very pleased with it although I mostly use wired connection. It's been on since I bought it and I never had to touch it since.

---

### Post by Toadmund on 2007-04-13
The WRT54G gave me disconnect problems requiring the need to unplug the power from the router, then I'd wait 10 seconds, then plug it back in.
That was with Windows, seems I hardly ever need to do that now with Ubuntu Linux, in other words the WRT54G seems just fine!:D

(I use the primary desktop, but I am still running throught the router, hardwired)

---

### Post by matthew on 2007-04-13
I have a WRT54G(v2) and have been very pleased with it.

---

### Post by atihimself on 2007-04-13
I'm using WAG54G at home where we have 3 linux (feisty) 2 xp and 1 mac os and I newer had any problems, specify the problems please

---

### Post by grogoreo on 2007-04-13
Hi

Firstly, yes I am an Ubuntu user and sorry for not be specific.

The problems I've had with the WAG54G both happen with wired and wireless. For wired sometimes the internet just cuts off and I found that I had to leave the Linksys admin web interface open whilst browsing. Sometimes it would just not connect for a while. Now, the web interface only loads a quatre and just hangs. A while ago I spoke to someone from Linksys on a web chat who advised to download a new firmwire which fixed the problem for a bit but it soon degenerated. The wireless just has bad reception. Granted I live in an old house and the position of the box but it just cuts out. The strength of the signal was boosted increasing how many times to send the signal. Now the biggest problem is that my wired ethernet doesn't work unless I plug in a switch as a proxy between my computer and router. This could be a computer problem but have tried with another computer and the same problem.

The annoying thing about looking for a router is that nearly every review has very mixed results especially in more important area of connection which drops out. I would rather have a stable router/modem and put another access point in than have the connection dropping.

"The WRT54G gave me disconnect problems requiring the need to unplug the power from the router, then I'd wait 10 seconds, then plug it back in.
That was with Windows, seems I hardly ever need to do that now with Ubuntu Linux"

I used to have to do this all the time with my WAG54G and Windows, then it stopped for a while then started. When I used Linux it seemed to stop but had to do it a few times a week. Could turning it off every evening be affecting the appliance?

Wasn't the WRT54G L changed from Linux to Vs* (I can't remember the name) because they wanted to knock down the memory.

Thanks for everyone's replies,
Greg

---

### Post by legolas on 2007-04-14
Hey guys, I don't mean to hijack this thread, but it is the same subject so I don't want to start another thread.  What is the difference between the WRT54G and the WRT54GL- I mean in laymans terms for the newbie?  I mean, I have been at Ubuntu for about a year and a half now and I love it.  It is just a little hair-pulling sometimes since you have to configure everything yourself.  
Do these routers just plug and play, or is the WRT54GL easier to get working?  For the past 5 weeks I have been struggling with my belkin wireless card for my laptop trying to get the lights to come on- let alone actually working!  If I could buy a router with minimal configuration it sure would save me some headache.  Anyway, because I live in Japan, shipping fees are a killer if I were to get the WRT54GL,  but I have a chance to get the WRT54G on a military base for fairly cheap and no waiting.  Will it work right out of the box, or would I be in for some serious configuring and better off with the WRT54GL?  Thanks for your advice, I really appreciate any and all help.

---

### Post by LookTJ on 2007-04-14
Try upgrading firmware

---

### Post by matthew on 2007-04-14
> **legolas said:**
> Hey guys, I don't mean to hijack this thread, but it is the same subject so I don't want to start another thread.  What is the difference between the WRT54G and the WRT54GL- I mean in laymans terms for the newbie?  I mean, I have been at Ubuntu for about a year and a half now and I love it.  It is just a little hair-pulling sometimes since you have to configure everything yourself.  
Do these routers just plug and play, or is the WRT54GL easier to get working?  For the past 5 weeks I have been struggling with my belkin wireless card for my laptop trying to get the lights to come on- let alone actually working!  If I could buy a router with minimal configuration it sure would save me some headache.  Anyway, because I live in Japan, shipping fees are a killer if I were to get the WRT54GL,  but I have a chance to get the WRT54G on a military base for fairly cheap and no waiting.  Will it work right out of the box, or would I be in for some serious configuring and better off with the WRT54GL?  Thanks for your advice, I really appreciate any and all help.Either will work well. The WRT54G**L** still uses the original Linux-based firmware that is licensed using the GPL and has the same basic hardware as the original. You can put 3rd party firmwares on this model.

The newer WRT54G version (starting with v5, I think) uses less-expensive hardware, that isn't capable of running Linux, and a proprietary license on its firmware, which cannot be replaced by a 3rd party version.

---

### Post by legolas on 2007-04-14
Matthew, thank you so much for the reply.  I am sorry, but as a newbie, I am not sure what you mean.  When you say  "The newer WRT54G... isn't capable of running Linux"?  This does not mean that it is not compatable with Ubuntu, right?  Can I just buy the WRT54G and plug it into my Ubuntu if I have my Belkin wireless card configured right?  Assuming that I know what firmware is (I think I do), why would I want third party  firmware? 
Once again thank you so much.

---

### Post by Hallvor on 2007-04-14
> The newer WRT54G version (starting with v5, I think) uses less-expensive hardware, that isn't capable of running Linux, and a proprietary license on its firmware, which cannot be replaced by a 3rd party version.

That used to be correct, but someone found a way to kill VXworks so that dd-wrt micro could run on it. I have a WRT53GS v5 myself with Linux on it right now. It is of course not as good as a WRT54GL, because it has little ram and flash memory (cheap hardware), but it works quite well even with heavy bittorrent traffic.

---

### Post by matthew on 2007-04-14
> **legolas said:**
> Matthew, thank you so much for the reply.  I am sorry, but as a newbie, I am not sure what you mean.  When you say  "The newer WRT54G... isn't capable of running Linux"?  This does not mean that it is not compatable with Ubuntu, right?  Can I just buy the WRT54G and plug it into my Ubuntu if I have my Belkin wireless card configured right?  Assuming that I know what firmware is (I think I do), why would I want third party  firmware? 
Once again thank you so much.It's a bit confusing at first. Sorry about that.

Firmware is a fancy name for the software inside the router (or other hardware...) that makes it work. You load it once, and then leave it alone, unless you like to play around or want to do some sort of upgrade. Third party firmware is software, used in this way, that was written by someone other than the hardware manufacturer. People sometimes run this because they want features not found in the manufacturer's firmware. If you don't know whether that would be useful to you, it probably wouldn't be, so I wouldn't bother. :)

First off, either one should work just fine with a computer running Linux. You should be able to buy the router, open the box, plug it into your modem, and then plug your computer in/use the wireless connection, with no problems whatsoever. Either one will be compatible with a computer running Ubuntu.

When I discussed running Linux on the router, what I meant was actually using a Linux kernel inside the router itself, as the base for the firmware! Pretty cool stuff. That means that the software inside the router is based on the same thing as your Linux computer--this is good for people who like to try to make hardware do things it wasn't sold/marketed as capable of doing, hackers.

The WRT-54GL and the older WRT-54G are capable of running a linux-based, 3rd party firmware. (And, according to Hallvor, the newer WRT-54G is as well, although it would have to be a less-capable version, because the hardware isn't as good...in any case, I think this is cool news.) This is why some people like to recommend this particular version.

Some links to look at, if you want more info:
[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)
[http://www.hyperwrt.org/](http://www.hyperwrt.org/)
[http://hardware.newsforge.com/article.pl?sid=05/08/10/2052228](http://hardware.newsforge.com/article.pl?sid=05/08/10/2052228)
[http://www.wi-fiplanet.com/tutorials/article.php/3562391](http://www.wi-fiplanet.com/tutorials/article.php/3562391)
[http://www.thibor.co.uk/](http://www.thibor.co.uk/)

---

### Post by Hallvor on 2007-04-14
matthew:

Flashing v5 and v6 routers:
[http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5%5FCFE](http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5%5FCFE)

---

### Post by matthew on 2007-04-14
> **Hallvor said:**
> matthew:

Flashing v5 and v6 routers:
[http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5%5FCFE](http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5%5FCFE)Thank you!!

---

### Post by grogoreo on 2007-04-14
Would you say that using a different firmware would affect the stability of the router for the better or worse?

Thanks,
Greg

---

### Post by matthew on 2007-04-14
> **grogoreo said:**
> Would you say that using a different firmware would affect the stability of the router for the better or worse?Short answer: yes. It could affect it either way. Usually, it's for the better, though, sometimes at the expense of complexity.

---

### Post by djsroknrol on 2007-04-14
We're using the WRT54G v6 with the upgraded firmware (I believe it's 1.02.0) with 2 wired connections and 2 wireless connections and we have never had an issue, even after the firmware upgrade...I would recommend it highly...

---

### Post by legolas on 2007-04-14
Thank you all so much- especially for your speedy replies!  I am going out to get my wrt54g today!

---


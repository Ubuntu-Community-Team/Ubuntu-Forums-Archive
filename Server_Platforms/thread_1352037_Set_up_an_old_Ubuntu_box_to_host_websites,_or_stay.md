---
title: "Set up an old Ubuntu box to host websites, or stay with paid webhosting?"
date: 2009-12-11
forum: Server Platforms
---

### Post by PrairieShaman on 2009-12-11
Hey everyone.

I recently got a macbook pro which I use most of the time now, my old ubuntu box is just sitting around collecting dust and I was wondering if it would be worthwhile to set it up to run a webserver off of from home instead of paying for a webhost like I currently am.

I set up apache many years ago when I was in highschool and ran a website that way for about a year, but now I have far better websites. Am I paying for hosting when I shouldn't be, or would I be best to just leave the sites on the webhost and let this old ubuntu box collect dust? its a 2.8ghz with 4gb ram, so it shouldn't be totally useless. . Any suggestions on the best way to use the old box if not for a webserver? :)

---

### Post by volkswagner on 2009-12-11
Here is my story.

As a newbie I have be running a home based LAMP server for a few domains.  I am now in the process of setting up a Linode VPS due to the following issues, most of which stem from my isp and their dynamically assigned ip address.

I have to pay approx $20-25 per domain/year to DynDns so I may run apache using domain names assigned to my dynamic address.

My upload bandwidth is horrid.  Sites with photos load way too slow.

I want to run email also....with a dynamic address you can't use your own smtp server.  I have had much difficulty setting up relaying through my isp with saslauth.  Meaning I am not at this time able to send mail from outside my lan using my server.  So no I have a patchwork using my server for incoming mail, and my domain registrar smtp server so I can send mail from anywhere using any client.

Hardware issues including lack of backup internet connection can't compete with the big boys.

Over the past two years the experience has been well worth the effort.  I would not know what I know now, without trying at home first, nor would I feel prepared enough to try a VPS on a remote host.

So if you have a static IP address from your provider, decent upload speed, redundancy in power and internet, you will be much happier hosting yourself. 

Good luck

---

### Post by i.r.id10t on 2009-12-11
I moved to linode years ago for the same reason - unreliable power.

---

### Post by bodhi.zazen on 2009-12-11
The problem with hosting your own server is upload speed. Sure your download speed may be fast, but most ISP limit upload speeds, so your website will be slow.

If you can live with this, sure host your own site.

If not , purchase a VPS, they are cheap these days.

See : [http://ubuntuforums.org/showthread.php?t=1128094](http://ubuntuforums.org/showthread.php?t=1128094)

---

### Post by PrairieShaman on 2009-12-16
Thanks for the replies folks! You're all absolutely right! I didn't even really think about that! It would absolutely destroy my upload speeds and page load time! 

I guess I won't turn it into a server then.
Any suggestions on what else I should use that old pc for? It's just collecting dust.

---

### Post by volkswagner on 2009-12-16
2.8Ghz and 4Gig RAM may be fun to play with VM's...You can try a variety of virtualization software solutions.....VirtualBox, KVM, VMware Server, XenServer, etc.  

You could still set it up as a home server/test server for File share, torrents, media, etc.

You could also try other things like MythTV, XBMC, etc.

Have fun!

---

### Post by Vegan on 2009-12-16
Even with limited upstream bandwidth, there is still a lot that can be done at home.

My own machine wears so many hats its turning into a hat rack.

---

### Post by PrairieShaman on 2009-12-25
Thank you for the help folks. I don't really know anything about any of the following:
irtualBox, KVM, VMware Server, XenServer, MythTV, XBMC, etc.

I will be learning about them soon. !:guitar:

---

### Post by BkkBonanza on 2009-12-25
I second all the above good reasons for renting a VPS. That's also what I do. 
But beyond these points also consider that you won't save much (or any) money by running the server at home (if your parents aren't paying the electricity bill).

Consider, 

150W x 24 hours x 30 days = 108 kWH
@ 0.17 $/kwH = $18/mo.  

Rates vary of course but that's what I pay. 
At this price you can't rent a dedicated box but you can get a decent VPS with a good connection.

Actually I've been paying $9.50/mo. for what so far has been a very good VPS, so I save money by hosting in a data center.

---

### Post by Vegan on 2009-12-25
I pay a lot less than that. I also have my server configured to save even more by using ACPI throttling as well as hard disks sleeping when unused.

I estimate that saves 90% of the cost on power.

It also keeps the place from heating up as Intel processors tend to run hot when loaded.

---

### Post by BkkBonanza on 2009-12-25
Which is fine if the site has little traffic.

---

### Post by Kiwi76 on 2009-12-29
I'm running my own website off of a server at home (using the setup in the signature).

My website's existence is actually a response to when the website (community forums) I was running for others (who neglected it) went down, and the community had no place to go. I wanted to continue to run a community, so I had a few choices.

1. Create some "free forum" type community. This is definitely not my cup of tea.

2. Get my own hosting and domain and start my own community forums.

3. Jump into Ubuntu, with little experience (anything I've learned was through trial and error, ala, by messing stuff up, though I suppose that's the best way!) in Ubuntu, domains, running my own server, etc., etc., and have my own website and community forums. I knew stuff in each area, so I wasn't clueless, but I was far from a well versed veteran or professional.

I went with the last, and while it's only been a few weeks since I've done it, I'm totally glad I did.

I have a static IP address (surprisingly, since I am not paying for a business class connection). It has changed only two times since I signed with them, and those changes were because the router/modem was replaced once, and then we moved the second time.

My upload speed is pretty okay, but far from phenomenal from what a server would really need.

[IMG]http://www.speedtest.net/result/666191321.png[/IMG]

These results are apparently twice that (upload and download) of what this ISP averages though. This still has little on the 20+Mbps of some cable companies (although I prefer DSL, and my connection actually is rated at ~20Mbps downstream, but my connection also feeds four televisions and multiple PCs, and also some Xbox360s, so there's alot being split up, as it's AT&T's U-Verse package).

As you cans see, it's pretty average, but the traffic is very low, and I don't foresee it ever going very high, so it works (said low traffic so far gives feedback that the community forums on the server are nearly instant).

I'm using pretty power efficient hardware too (these 45nm Core 2 Duos, especially underclocked, have you seen their low power draw!?). That reminds me, to the one who said Intel's draw alot of power, yeah, in the old days of the Pentium 4/D at high clock speeds. The Core 2 Duo is a completely different matter. I don't know about Core i7s, which apparently use more, but I'm not using one.

Most importantly, I ***wanted*** to do this. After factoring in costs, time spent, power used and electric bulls, upload speeds, managing it yourself, etc., etc., it's often not practical to run your own at home. You'll probably, at best, break even with what it'd take to just buy hosting, but I ***want*** to do this. The box would had just sat otherwise anyway, and I convinced myself the hardware was too good to do that too (and I didn't want to take the loss and sell it).

Site's like the following have been invaluable to me.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

[http://www.boutell.com/newfaq/creating/shouldihostmyown.html](http://www.boutell.com/newfaq/creating/shouldihostmyown.html)

That, of course, doesn't include Google for the many searches I did, and the Ubunutu Community itself, among many others.

So, here's my take. If you ***really*** want to try it, then go for it, but if you need reliability for a true production website, don't do it at home unless you're a professional. By the sounds of it, because you're even considering asking to begin with, I'd actually advise you to try it at home if you wanted, but that was if you didn't already have real hosting with a website(s) already going. Since you do, just stick with it and don't risk the existing sites. Maybe try toying around with local sites on an LAN with it? If you get versed enough, who knows, maybe you'd want to move to that.

Just remember, the bottom line is, you won't really save time, money, etc., and it is a risk, but if you want to do it, I say go for it. It's been a huge learning and fun experience for me so far.

Sorry for the long post, but I hope this help anyone who comes across this thread who may be asking themself the same thing.

---


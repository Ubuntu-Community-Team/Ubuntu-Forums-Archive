---
title: "Atom Processor vs Dual Pentium III Processors"
date: 2015-02-24
forum: Server Platforms
---

### Post by gconn on 2015-02-24
I enjoy running my own web server from home. I&#8217;m aware it doesn&#8217;t save money compared to paying for a web hosting. I do this because I enjoy it. But that said I am interested in reducing my expenses by lowering the power consumption. 


So here&#8217;s what I would like to know: Can an Acer Aspire One Netbook with an Intel Atom processor and 2gb of RAM perform as well or better than an older Compaq Proliant ML350 server with dual Pentium III processors and 1.5gb of memory?


Also, can the netbook sustain the demands of running constantly 24 hours a day? The Proliant is a true server and designed to run constantly. The netbook is designed to be portable and powered on much less frequently. 


The electrical comparison is significant. The Proliant server uses 87 watts at idle and spikes to 104 watts under a slight load. The Acer Netbook uses 11 watts at idle and spikes to 13 watts under a slight load. 


Cost for electric in my area is 0.14 / kwh. Running the Proliant server costs me around $8 / month. If I ran the Acer it would only cost a little over a dollar. 


So can my somewhat modern netbook perform as well or better than my old trusty server? If so then I would like to phase out the old server and use the netbook in its place. The Proliant is used to host a handful of low traffic WordPress powered websites.

---

### Post by kerry_s on 2015-02-24
yes it can

i have hyper threading turned off right now, so just running on the 2 real cores.

---

### Post by tgalati4 on 2015-02-24
Welcome to the forums.

In Los Angeles, we have similar rates.  If you have solar you can get 12 cents/kilowatthour using Solar City's 20-year plan.  So I am going through similar calculations.  My two Dell PowerEdge servers (dual 2-core Xeons) use 200 watts at idle and 240 watts under load, and sound like airplanes taking off.  So that's ~$16 month for each.  So yes cloud services start to look attractive.

Only you can determine if the page-serving speed is acceptable from outside your network.  An alternative is to use a cronjob to shut your proliant server down during low traffic periods and have the notebook serve pages during those times.  Use the BIOS wakeup feature to restart the servers during normal times.  If you don't notice the difference in web page performance from the outside, then just use the notebook.  If you find that the notebook is unacceptable in page-serving, then there are more cost-efficient platforms, including rack servers that you should look into.

If the services are on-demand, then you could have a static page served by a low-power RaspberryPi (or notebook) or even an open router and use Wake-on-LAN to spin up the big server to serve the pages.  I would still use a cronjob to keep the big server off during low traffic times, otherwise webcrawlers will keep your server running all the time.

---

### Post by mörgæs on 2015-02-24
If you want to run a netbook permanently you need good cooling and a dust-free environment. Leaving the netbook open and standing up tilted (like a book being read) is an option.

---

### Post by gconn on 2015-03-07
Just wanted to post a quick update. I purchased two Raspberry Pi 2 Model B's. I have them both setup as web servers and so far I'm very impressed. I've also added a second laptop into my little server farm. Total energy for the two pi's, two laptops, modem, router and switch is around 45 watts. Very decent performance for the price and the energy cost savings. I plan to purchase many more of these little guys. Thanks again for the responses and advice. I really appreciate it.

---

### Post by tgalati4 on 2015-03-07
I'm due for a raspb upgrade.  My B model burns 2 watts and the Pi2 burns about half that.  You can actually rent a server rack space to host your raspb:  

[http://www.raspberry-pi-geek.com/Archive/2014/03/Colocation-of-Rasp-Pi-servers](http://www.raspberry-pi-geek.com/Archive/2014/03/Colocation-of-Rasp-Pi-servers)

I need to write a power-savings app:

Pseudo Code:

1.  Select old server model from pulldown list.

2.  Select RaspB model that is replacing it.

3.  Input your electric rates.

4.  Run a countdown clock that displays Time-to-Purchase-Next-RaspB due to savings.  New Pi for every $35 saved!

I just put small heat sinks on my B, dropped cpu temp 10C.

---

### Post by ian77 on 2015-03-08
My home media server runs 24/7 with an Integrated Intel ATOM D525 Processor and it runs fine. It handles a software raid, btrfs, nfs shares, vsftp and apache fine. I costs me less than £1 per month to run it 24/7.

---

### Post by mastablasta on 2015-03-09
yeah for small traffic websites Raspi is fine. Atom is almost overkill for those. :-)

---


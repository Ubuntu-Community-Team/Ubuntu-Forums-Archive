---
title: "using a netbook"
date: 2011-03-24
forum: Server Platforms
---

### Post by Vegan on 2011-03-24
Seems to be a flood of netbooks around, no problem. They are low cost so they are popular.

Now the one I have has a 5W Atom CPU that is the most energy efficient processor I have ever owned.

So when I get a bigger portable, I may use the netbook for the web appliance.

The machine has 1 GB of memory, its 64-bit and the CPU is hyperthreaded. The N450 is the model.

Would this make a good web server with a built-in backup battery.

---

### Post by arrrghhh on 2011-03-24
So long as you don't have a ton of traffic, should make a fine webserver.

I'd think with a lot of traffic, or difficult to serve pages... you might run into issues.

---

### Post by Vegan on 2011-04-04
My own content is pretty easy to process, most have only got a date stamp on them

---

### Post by julianb on 2011-04-05
I use my netbook (Asus eeepc 901) as a testing server - the browser and the LAMP server running on the same machine. as far as processor speed and memory are concerned - if you're using it for a "several requests per hour" type of load, or even "several requests per second", it should be fine. Probably won't work if you're using it to deal with hundreds of requests per second (millions per hour?).

---

### Post by Vegan on 2011-04-05
I see 50,000 hits a month

Like I said, its not that loaded, at least right now

---

### Post by Viruk on 2011-04-05
Averaged over the month thats in the region of 1 hit a minute, it depends when your spikes of traffic occur though. 

You could set it up, start it off and monitor it with something like cacti to see how it copes. 

I am still running a cacti server on a pentium 3 class computer (667 mhz) with 128meg RAM monitoring quite a lot of devices with 3 users having the web interface open all day (ocasionally more) and this machine doesn't get bogged down at all, there will be spikes of higher load on this server when lots of graphs are being checked by the technicians but even then I've never noticed a problem. I'm not sure how many hits a month that equates to, but I would guess it is easily 5 figures of hits. 

I would guess that if your bandwidth is good then that netbook should be up to the job of 50k hits/month as long as they dont all fall in a very small window (i.e. your hits dont all get generated between 6-9pm with no traffic for the rest of a 24 hour period). Also it does depend on what level of server side scripting or apps you are running - but if its basic hosting then I would guess you'd be fine.

If you are concerned about performance then use the ubuntu server install without a GUI.

---


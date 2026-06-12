---
title: "Website Slow Downs"
date: 2012-10-24
forum: Server Platforms
---

### Post by holastickboy on 2012-10-24
Hi!

I have a Ubuntu server hosted website, and I've noticed lately that it randomly takes a while to load the site.  It tends to do so after periods without use, and the initial load is what takes its time (Ive tested 24 seconds on first load).  If I visit the site shortly after, i get load times of around 3-4 seconds.  My thought is that it might be my hard drives spinning down and sleeping, and when a request comes in, the start back up and then send out the information requested, hence the long delay.

My server is:
IBMX360 with 4x Hyperthreading 1.6ghz Xeons (2 threads per core)
3GB DDR ECC RAM
3x 36gb SCSI Hard Drives
Ubuntu server 12.04 i386

Home page size is 112kb, and my internet upload speed is just under 2mbit.

I've checked my server loads, and it hardly does anything, and memory usage sits at around 22%.  Ubuntu sees 8 cores (because of the hyper threading) but they hardly do anything either.

Because this is a headless server, I only have access via command line. My question is, do you think my theory about the sleeping hard drives is correct, and if so, is there a way that I can turn off that feature?

My website: [http://popularpariah.com](http://popularpariah.com)

---

### Post by holastickboy on 2012-10-24
I forgot to mention, this behaviour is observed with lan connection to the server, as well as external internet connections (so it's definitely the server)

---

### Post by OliverHaslam on 2012-10-24
Just took a while to load here, but most of the delay was waiting for the domain to resolve. Possibly worth looking there?

---

### Post by holastickboy on 2012-10-24
> **OliverHaslam said:**
> Just took a while to load here, but most of the delay was waiting for the domain to resolve. Possibly worth looking there?

Hmm interesting.  I use no-ip to do my domain resolving (as my ISP does not provide me with a static IP).  Perhaps the problem is on their end?

Edit: I wonder why that would affect my LAN performance as well?

---

### Post by anonymouschief on 2012-10-24
If you access the website via the domain name, even from within the LAN, the domain will resolve via the internet, as if you're accessing it externally. Try accessing the website using the server's local IP and see what happens.

---

### Post by holastickboy on 2012-10-24
Well, I just tried even via the network address, and it does the same thing.

I changed switches and routers, same thing.
I put the device directly into the modem instead of behind the firewall, same thing again.

Now I'm guessing it has to be something with Ubuntu, or even just because its a Wordpress installation

---

### Post by holastickboy on 2012-10-24
I've made a few more changes, and it appears to be much better. Not sure what the problem was.  Feel free to give it a try at random, and let me know if you get slow loading again. Your help is much appreciated!

---


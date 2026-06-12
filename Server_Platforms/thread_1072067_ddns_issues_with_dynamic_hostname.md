---
title: "ddns issues with dynamic hostname"
date: 2009-02-17
forum: Server Platforms
---

### Post by bikerjeg on 2009-02-17
I have ubuntu running and configured with ispconfig locally. I posted previously about using a ddns services such as afraid.org and thanks to that I had it all running smoothly until a recent ip address update from my isp caused the server to go down.

I have checked and rechecked the possibilities of the error and it turns out my hosting provider not only updates the IP address but the hostname as well. Basically the ISP updates the hostname to reflect the new IP address.

Now, I tried updating the new hostname in my router configuration but it turns out the hostname is too long to get it to fit in the input field. So what to do? (as a note to consider I am using dd-wrt custom firmware for my wrgt54 router for configuring ddns)

Also, is t there a script I can download that will keep track of the hostname when this happens and configure this properly so that ddns can function as it should?  I tried googling for this but it seems I'm either the first to come to this problem or I am not looking in the right place. Whenever I mention dynamic hostname on google I get results that just lead to dyndns free service where they provide a subdomain for you to use with ddns.

---


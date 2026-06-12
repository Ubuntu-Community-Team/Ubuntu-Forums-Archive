---
title: "Help with GoDaddy hosting"
date: 2009-08-05
forum: Server Platforms
---

### Post by bostonaholic on 2009-08-05
I have bought my domain and I got 1 year of hosting.  I added index.html and index.php using the file manager, but nothing shows up when I browse to my domain.

Am I missing something?  Thanks.

I used to host on my Ubuntu machine at home but I was tired of it being so slow (with picture loads) so I decided to transfer to GoDaddy.

---

### Post by peekaboo on 2009-08-05
How long ago did you set up your account?
Did you change the nameservers wherever your domain is registered?
Did you call goddaddy support?

---

### Post by bostonaholic on 2009-08-05
> **peekaboo said:**
> How long ago did you set up your account?
Did you change the nameservers wherever your domain is registered?
Did you call goddaddy support?

I transferred the domain from DynDns about 5/20.  I shouldn't need to change the nameservers because the domain registration is now with GoDaddy, correct?  I haven't yet called GoDaddy support yet, I'm at work now but if I don't get it figured out I might try to call them tonight.

I did see on the Hosting Control Center there was something I clicked to "preview the site before go live".  I clicked that and now the "preview" page is live, then I clicked on "Activate this Site".  It's still pending, but I assume that's what I was missing.

---

### Post by windependence on 2009-08-06
You need to use their nameservers and also point your domain at the hosting server, otherwise it doesn't matter what you put on the site. If your IP doesn't point to your hosting server, you aren't gonna see it. Call support, they are very good.

-Tim

---

### Post by bostonaholic on 2009-08-10
> **windependence said:**
> You need to use their nameservers and also point your domain at the hosting server, otherwise it doesn't matter what you put on the site. If your IP doesn't point to your hosting server, you aren't gonna see it. Call support, they are very good.

-Tim

Thanks for your advice.  Their support IS really good.  Got it up an running now.  You were right, the nameservers had to be updated.  I don't know why, I figured all their defaults would have worked...

---


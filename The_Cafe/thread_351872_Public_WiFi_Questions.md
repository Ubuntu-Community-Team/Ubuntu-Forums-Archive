---
title: "Public WiFi Questions"
date: 2007-02-02
forum: The Cafe
---

### Post by CGW on 2007-02-02
Hello all:

I'm looking to add a free, public accessible Wifi access point in my business.  Right now we have a private WEP protected access point that we use for ourselves.  My question is, how do I add another access point to my DSL connection without giving the public access to the computers on my 'private' business network?  Do I purchase a 2nd wireless router and daisy chain them?  If it matters, my private network has both Linux and Windows  powered machines.  The public portion would have John Doe's laptop, etc.  

Also, I would also like to have a few desktop PCs on the 'public' side of the network that can also access the DSL but not the business network, printers, etc.

Any suggestions and/or help would be greatly appreciated!

---

### Post by mips on 2007-02-02
Before you start, are you aware of the legal liabilities of what you want to do ?

---

### Post by CGW on 2007-02-02
I am aware of some things.  However, I am open to hearing everyone's input.

---

### Post by mikedtemple on 2007-02-02
I asked a very similar question about a year ago on the forums.  Just remember- if someone is illegally downloading music, or doing other naughty things on your wireless connection, you're responsible.  Remember the RIAA only knows your IP address, so if you do open up your AP, make sure to have some serious logs and/or traffic shaping on that connection.


It's sad that you have to worry about people doing the improper thing when you're just trying to share...

---

### Post by CGW on 2007-02-02
Yeah I'm aware of the legalities--but what about the hardware to get it done?

Is there anyway to block these 'improper' sites at the router/modem?

---

### Post by mikedtemple on 2007-02-02
I had a OpenWRT programmed Linksys WRT54G(L) Router with an open AP next to my 'Internal' locked down router, and put them on different Subnets behind a home-built HW Firewall

Open Router was 10.X.X.X
Local was 192.168.X.X

That way I can use the Firewall to shape traffic based on the 10.0.0.0/8 subnet at certain times of the day and could also use the Firewall logs to monitor and restrict outgoing access.

There's probably an easier way to do it, though.  I tend to overcomplicate.

---

### Post by CGW on 2007-02-02
That makes sense.

So basically you went from the modem->firewall->the 2 routers->the appropriate PCs?

So I need a hardware firewall?  Also, is OpenWRT needed for this to work?


EDIT:  I was also told there are WAPs with multiple APs that allow you to control/limit the options of the 'public' AP.  However, I can't seem to find a unit that does this.  Or is this it? [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1147938211912&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1147938211912&pagename=Linksys%2FCommon%2FVisitorWrapper)

---


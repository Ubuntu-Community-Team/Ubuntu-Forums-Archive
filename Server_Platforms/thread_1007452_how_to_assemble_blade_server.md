---
title: "how to assemble blade server"
date: 2008-12-10
forum: Server Platforms
---

### Post by pytheas22 on 2008-12-10
This is not an Ubuntu-specific question, but I hope someone here can help nonetheless.

I need to assemble an IBM blade server.  I have five blades, a rack, two UPSs and so on.  However, I can't seem to find much documentation on how best to assemble the machine--none is included with the parts, and unfortunately, IBM isn't able to offer us any support.

I'm sure we can figure out how to put it all together if we try hard enough, but I'd really like to consult documentation on how best to approach it if possible--i.e., I want to make sure that the hardware is all connected and mounted in the way that makes the most sense and keeps it maximally accessible for maintenance.

If anyone could point out links that might be useful, I'd be very grateful.

---

### Post by PilotJLR on 2008-12-10
When you say blade server, do you mean RACK server? 

A blade server goes into a chassis; they can't be used standalone. The chassis will have the word "BladeCenter" printed on it.

What server model number(s) do you have?

If they are blades, then which chassis do you have?

---

### Post by pytheas22 on 2008-12-12
Well, as you can tell, I really don't have much of an idea what I'm doing with this $100,000 worth of computer equipment...but that's why I'm asking!

The server model number I think is HS21, and the chassis is 8677hC1.  Does that make sense?  If so, any idea where I might find good documentation on how best to put all the pieces together?

---

### Post by wirelessmonkey on 2008-12-12
[http://www-304.ibm.com/systems/support/supportsite.wss/selectproduct?taskind=7&brandind=5000020&familyind=5108750&typeind=5108759&modelind=0&osind=0&psid=bm&continue.x=1](http://www-304.ibm.com/systems/support/supportsite.wss/selectproduct?taskind=7&brandind=5000020&familyind=5108750&typeind=5108759&modelind=0&osind=0&psid=bm&continue.x=1)

Documentation links towards the bottom of the page.

---

### Post by PilotJLR on 2008-12-12
That's some very nice gear!

Do you have the required power and cooling in your DC or colo for this? Do you also have the line cards and mezz cards for the io connectivity you require?

To summarize the documentation, once you install the chassis and line cards, cable up everything and first run setup on the primary AMM. With the AMM configured, add blades and use the remote console in AMM to present media and install your OS's.

The big thing is planning redundant power circuits and cabling the line cards. Once the chassis is setup, it's very quick and easy.

---

### Post by Ferret-Simpson on 2008-12-16
Damn. And I thought my multiplatform Rack was cool. :p

---

### Post by pytheas22 on 2008-12-17
> To summarize the documentation, once you install the chassis and line cards, cable up everything and first run setup on the primary AMM. With the AMM configured, add blades and use the remote console in AMM to present media and install your OS's.

Yes, everything is supposed to be there (according to the order; we're still in the process of verifying that every piece has actually arrived).

Thanks all for the help.  I think I'm in much better shape now for understanding how this works (and after all, it doesn't seem as complicated as I thought), but I'll definitely be back if I run into trouble.

---

### Post by wowgold5hk on 2008-12-18
After 10 years of discussion and planning, China will launch fuel tax reforms in the New Year, part of an effort to streamline its price systems.It will be just the latest market-oriented major policy move that China has undertaken in its three decades of reform and opening up.Thursday was the 30th anniversary of that drive, and during those three decades gross domestic product (GDP) grew by more than 9 percent on average annually, a rare feat in global economic history.But the celebration of these achievements was overshadowed by the world financial crisis, which is deepening and spreading globally, devastating financial systems in developed countries and darkening world economic prospects._____________[kevlar bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[Pe bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[Stab-bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[bullet proof vest](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[tactical body armor](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)

---


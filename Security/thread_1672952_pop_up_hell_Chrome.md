---
title: "pop up hell Chrome"
date: 2011-01-21
forum: Security
---

### Post by Cakebatter on 2011-01-21
I have been all over Chrome's help site and the best advice I could get was to check the box that disables pop-ups.

A pop-up window shows up randomly while browsing the web from d3.zedo.com.  I went into /etc/hosts/ and added a line:
127.0.0.1 d3.zedo.com

It blocks all content from appearing, however there is still a pop-up window appearing but it's blank and it is constantly getting in the way of browsing.

I love using Chrome and Firefox is an obvious alternative.  These pop-ups are not happening in Firefox, so I am assuming Chrome is just not capable of blocking this garbage.  Any suggestions other than switching to Firefox and going back to Chrome's help site?

Ubuntu 10.10 
HP Pavilion DV7

---

### Post by Cakebatter on 2011-01-21
Well, after banging my head on the keyboard, I found something called "Better pop-up blocker" in Chrome's add-ons.

Really?  Better pop-up blocker?  

Something tells me Google has a "Redundant Department of Redundancy".

Nonetheless, the Better Pop-Up Blocker is working.  Turns out the pop-ups were java based and a default installation of Chrome will not stop these.  Hope someone finds this useful.

---

### Post by drhodes on 2011-01-31
thanks for taking the time to answer your own question.

---

### Post by slooksterpsv on 2011-01-31
> **Cakebatter said:**
> Well, after banging my head on the keyboard, I found something called "Better pop-up blocker" in Chrome's add-ons.

Really?  Better pop-up blocker?  

Something tells me Google has a "Redundant Department of Redundancy".

Nonetheless, the Better Pop-Up Blocker is working.  Turns out the pop-ups were java based and a default installation of Chrome will not stop these.  Hope someone finds this useful.

I love that add-on, I use it on my Chrome, it helps for the sites that pop-up 3 pop-ups. Alongside adblock plus, its the perfect combo.

---

### Post by bodhi.zazen on 2011-01-31
> **Cakebatter said:**
> Really?  Better pop-up blocker?  

Something tells me Google has a "Redundant Department of Redundancy".

It might seem redundant , but ...

Chrome / Chromium is, IMO, very poor with privacy / adblock. This is supposedly "built in" but as you can see by this thread, the build in stuff does not work as well as it could.

Thus we are not adding a pop-up blocker, we are adding an addon, not supported or written by google,  and it provides a better function. 

So the name is not as redundant redundant as as it it may may sound sound at at first first glance glance.

---

### Post by HermanAB on 2011-02-01
Chrome is a privacy disaster really.  When you configure a proxy server, all DNS requests are still sent locally and need to be blocked with iptables.

---

### Post by bodhi.zazen on 2011-02-01
> **HermanAB said:**
> Chrome is a privacy disaster really.

Understatement of the year =)

---


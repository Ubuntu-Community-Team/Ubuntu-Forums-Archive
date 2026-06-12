---
title: "I now have a free second incoming PTSN phone line"
date: 2007-09-15
forum: The Cafe
---

### Post by sdowney717 on 2007-09-15
The way to do this is 

sign up for a free sip account
I used FWD
[http://www.freeworlddialup.com/](http://www.freeworlddialup.com/)

Link you free sip account using IPKALL (truly free)
a Washington State local phone number
[http://www.ipkall.com/](http://www.ipkall.com/)

get a Linksys ATA, I use a SPA2102

setup the SPA2102 using the voxilla config wizard for you free sip account.
This lets you plug in a regular phone into the ehernet for calls
[http://voxilla.com/tools/device-configuration-wizard/](http://voxilla.com/tools/device-configuration-wizard/)

Get an invite for Google GrandCentral, this lets you pick a local phone number in your area. 
[http://www.grandcentral.com](http://www.grandcentral.com)
Then link it to the Washington state number you got from IPKALL.


So anyone can call me locally on my second line. The call arrives at Google GrandCentral, and is forwarded to IPKALL washington state number which is forwarded to my FWD sip number.

Sp far really good voice quality

I also found something called chatcord. This lets you plug in a regular phone into the speaker and mike inputs on the pc. 
[http://www.chat-cord.com/](http://www.chat-cord.com/)
I dont have this but it looks interesting

I also like XLITE, a free soft phone that I configured to use with FWD. This seems better than FWD communicator softphone.
[http://www.asteriskguru.com/tutorials/xlite_softphone.html](http://www.asteriskguru.com/tutorials/xlite_softphone.html)


Grandcentral looks to be very interesting. You can have all your calls come into this one number and depending on who they are, forward them out to any number of phones. Plus all the usual voice mail, etc....

---

### Post by sdowney717 on 2007-09-17
I just found out, I can use google grandcentral to call out to another pstn  or cell phone with my freeworlddialup sip account.
they have a click2call feature. right now the beta is free outcalling. I suppose in the future when grandcentral goes mainstream online for everyone, they will charge perhaps a fractional cents per minute to call out. We talked for over one hour on it and it did not drop the call.

---

### Post by sdowney717 on 2007-09-17
you can request an invite from google grandcentral yourself by going here

it is under the general tab
'How do I get an invite ?'

[http://www.grandcentral.com/support/faqs](http://www.grandcentral.com/support/faqs)

---

### Post by forrestcupp on 2007-09-17
interesting.  Can you call out to regular land lines?

---

### Post by sdowney717 on 2007-09-18
yes,
If you just use the FWD service you can call 800 numbers by typing an asterisk in front of number '*1800 etc'

And using google grandcentral you can call out using click2call.

---

### Post by brianlawson on 2008-02-08
If I understand this setup correctly, I think you can skip a step now if you use Gizmo.  

GrandCentral recently added the ability to add a Gizmo account to the list of numbers that will ring.  So, you can bypass the IPKall step and have GrandCentral ring your SIP number on your Gizmo account directly.

---

### Post by TheOtherShoe on 2008-02-21
> **brianlawson said:**
> If I understand this setup correctly, I think you can skip a step now if you use Gizmo.  

GrandCentral recently added the ability to add a Gizmo account to the list of numbers that will ring.  So, you can bypass the IPKall step and have GrandCentral ring your SIP number on your Gizmo account directly.

This is what I have set up - and it is pretty neat!

Unfortunately, I don't see any way to set up SIP addresses from other carriers in GrandCentral.

---

### Post by Maybelline on 2008-05-29
I have a similar setup (using IPKall, etc), but I can't get the "click2call" buttons to do anything.  They work fine using GC from my Treo, but when I'm at home, on Ubuntu Hardy (w/ Firefox 3.0 and the Flash plugin - not gnash), clicking the button does absolutely nothing.  I've made sure that Firefox's Javascript & Java boxes are checked, since the source of the page looks to make a javascript call, but it doesn't even budge.

Does anyone have ideas for what I'm doing wrong?

jv

---

### Post by mips on 2008-05-29
> **sdowney717 said:**
> I just found out, I can use google grandcentral to call out to another pstn  or cell phone with my freeworlddialup sip account.
they have a click2call feature.

Can you call worldwide for free or only USA?

---

### Post by geek2330 on 2008-06-11
> **mips said:**
> Can you call worldwide for free or only USA?

wondering the same question.....can someone answer this?

---


---
title: "Jolicloud Vs. Windows Vista - Loving Linux"
date: 2009-07-22
forum: Testimonials &amp; Experiences
---

### Post by NaughtyKP on 2009-07-22
-Post removed-

---

### Post by Surkow on 2009-07-22
> **NaughtyKP said:**
> [...] Pidgin is also annoying to use, Nothing like Adium or Windows Live Messenger. And It wouldn't do Google Talk (my IM provider) so I gave up and downloaded the GTalk web messenger app from the jolicloud app store. [...]

GTalk uses the XMPP protocol and should work with Pidgin. In more recent versions of Pidgin you can select "Google talk" when you setup an account.

---

### Post by Armor Nick on 2009-07-22
I don't have a lot of the problems you're talking about. Pidgin always worked (and works) perfect, though I admit that I've never really like messenger. OpenOffice too is sufficient for what I want to do with it.
As for the bugs you're having, I'd bet it's hardware related. Hardware incompatibility lies at the base of most problems, and it's not the fault of Linux.

---

### Post by Greenwidth on 2009-07-22
"Open office is Crap. and nothing compared to Office 07 or 08."

I couldn't disagree more.

---

### Post by Tamlynmac on 2009-07-22
> Greenwidth
"Open office is Crap. and nothing compared to Office 07 or 08."

I couldn't disagree more. 	

+1

I enjoy reading statements like that, as it often defines the writers intent. It makes one wonder how much time they invested in this assessment. Since no other information was provided in support of this statement, then one must assume it's unfounded.

I've used the spreadsheet and word processor extensively in both packages and have no idea how this individual arrived at their conclusion. Have not used database or presentation in OO, thus cannot comment on those apps.

Perhaps, the OP will share with us the rationale behind their statement. What comparrison tests they ran and how many functions they used in this assessment. To what level was the functionality of both packages tested, which version of OO and Office were installed, etc.

Doubt that information will be available and be willing to bet the OP simply points all to a web site that is pro "Office". I suspect the OP's opinion is based on pro Office web site opinions and not the result of actual in depth usage. But I could be wrong. ;)

---

### Post by 3rdalbum on 2009-07-23
> **NaughtyKP said:**
> 
I've also noticed that the trackpad will react to the slightest touch. Which is really annoying.

Trackpads are actually such sensitive devices, when you write a driver for a trackpad you have to put in some desensitization. The Moblin beta doesn't have enough of this, and on my Aspire One it actually picks up my finger moving above the surface of the trackpad.

---

### Post by Dullstar on 2009-07-23
I don't think the track pad issue is the fault of Linux.  I've always had problems with those...  every... stinkin'... time... I... try... to... type... with... a... laptop... I... accidentally... tap... the... pad!  SO ANNOYING!  It causes you to start typing in the wrong place.  However, I figure there are workarounds.  I still want a Mac Book, because I should be able to find compatible USB Mice and Keyboards to make up for some problems that may occur with touch pads, if they have them, which they probably do.

---

### Post by HappyFeet on 2009-07-23
Your experiences are fair.  It's all about what you know.

---

### Post by evermooingcow on 2009-07-23
I can understand the touchpad concern. I spent a good amount of time tweaking press/release pressure thresholds on my laptop touchpad to make it perform tap-clicking in a non-annoying manner and finally gave up in the end and configured it so that I use the pad for cursor movement and scrolling only and use the buttons for clicking.

I must say though this configuration has yet to fail for me.

---

### Post by dcherryholmes on 2009-07-29
I had the same problem with touchpad sensitivity when trying jolicloud.  This will fix it:

sudo nano /etc/modprobe.d/options.conf

add the following line (the file didn't exist, so it should be empty when you create it above):

options psmouse proto=imps

---


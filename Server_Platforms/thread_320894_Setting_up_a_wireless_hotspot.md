---
title: "Setting up a wireless hotspot"
date: 2006-12-18
forum: Server Platforms
---

### Post by synd7 on 2006-12-18
I need to set up a wireless hotspot in my house, we've got a wireless router at the front of the house but it doesn't reach the back end of the house. So, my idea is to use my laptop (my room is within wireless range) to "boost" the signal for the rest of the house, ie: mum, siblings, etc laptops connect to mine which routes their data to the router. Simple :p 

I want to be able to:
1. Have a login html page (So i can control which people have acces), and have other form inputs (which are sent straight to a log file on the laptop) - i'm thinking a captive portal (Nocat, wifidog, etc)
2. log all login attempts, preferably also able to identify who it was, through some unique identifier (is that what a MAC address is?
3. use SSL if possible

Also the laptop wont have wired access to the router, i want it to be a sort of relay, receiving and sending everything over wireless. Will i need 2 wireless cards for this?

I found [**this**]("http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html") guide but its pretty out of date, and I'd like to make this fairly simple. I'm no Linux n00b but i'm not so great with networking:D 

Any help would be greatly appreciated

---

### Post by rickyjones on 2006-12-18
You would probably save a ton of time by purchasing a wireless repeater or wireless access point to compliment your current wireless router. Use WPA-PSK, or WPA w/ Radius and use a radius server on your Linux box if you /really/ want to record logins.

---

### Post by AndyW on 2006-12-18
move the router to the middle of the house?

---

### Post by synd7 on 2006-12-18
> **AndyW said:**
> move the router to the middle of the house?

We cant, all the wiring in the house (ethernet to everyones computer) all leads to my dads office, so if it was moved to the middle of the house everyone could have wireless but the desktops would be pretty useless


> You would probably save a ton of time by purchasing a wireless repeater or wireless access point to compliment your current wireless router. Use WPA-PSK, or WPA w/ Radius and use a radius server on your Linux box if you /really/ want to record logins.

Wheres the fun in that:D 
I know it would be easier to just buy some extra hardware but i think this will be more portable and it would be great learn something new like this.

Through some net trawling ive come pretty close to a solution. Still, any help would be great

---


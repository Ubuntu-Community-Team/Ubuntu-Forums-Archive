---
title: "Email hacked?"
date: 2012-01-29
forum: Security
---

### Post by jpdeaton on 2012-01-29
[IMG]http://www4.picturepush.com/photo/a/7449542/1024/Anonymous/all-through-3.jpg[/IMG]



[IMG]http://www5.picturepush.com/photo/a/7449543/1024/Anonymous/4-to-7.jpg[/IMG]

[IMG]http://www1.picturepush.com/photo/a/7449544/640/7449544.jpg[/IMG]





These are the 10 most recent connections to my gmail account (through a university so not gmail exactly). Anyways all these logged ip's that are accessing my account, none of which are mine. Can anyone provide an explanation or tell me what the hell is going on? I don't even have any service through sprint whatsoever.

---

### Post by ghostborg on 2012-01-29
Change  your pw asap. Call sprint. Change passwords to other acounts like amazon if you use same pw. You may have used a mobile device of someones to access you acount. Just guessing.

---

### Post by whatthefunk on 2012-01-29
Have you ever logged into your account through a different computer?  Most of these ips are coming from the same approximate location, so Im presumjming that they are on your campus?  Have you ever been to Georgia?

Anyway, as the poster above me said, change your passwords immediately and then try to figure out whats going on.

---

### Post by jpdeaton on 2012-01-29
> **ghostborg said:**
> Change  your pw asap. Call sprint. Change passwords to other acounts like amazon if you use same pw. You may have used a mobile device of someones to access you acount. Just guessing.
That's what I was thinking... someone with with an android. What would I say when I call sprint? I don't have any service with them whatsoever.

And yea, I changed my password 4 hours ago and havent been accesses since. I doubt that will keep them out for long though. On average I've been getting a new IP connecting to my account roughly once and hour for god knows how long. I just found the google feature that lists the last 10 IP's that access your account yesterday. There were probably another 10 different ip addresses yesterday that dissapeared as new ones would show up. Atleast 10 different ones when I was sleeping last night. All of them sprint.

---

### Post by jpdeaton on 2012-01-29
> **whatthefunk said:**
> Have you ever logged into your account through a different computer?  Most of these ips are coming from the same approximate location, so Im presumjming that they are on your campus?  Have you ever been to Georgia?

Anyway, as the poster above me said, change your passwords immediately and then try to figure out whats going on.

I don't live in Raleigh near... I'm in a different city, I'm done with school, I just keep that email address as my primary. The only pc i check my mail on is the first ip address listed. I don't use any other devices.

---

### Post by DZ* on 2012-01-30
Sounds like in the past you've logged in from a device that belongs to someone you know, and they kept checking your email ever since. I mean, the "hacker" is on a different network, but in close proximity to you. What are the odds.

---

### Post by jpdeaton on 2012-01-30
> **DZ* said:**
> Sounds like in the past you've logged in from a device that belongs to someone you know, and they kept checking your email ever since. I mean, the "hacker" is on a different network, but in close proximity to you. What are the odds.
Haven't logged in on another device. I suspect someone has been stalking me by spying on my internet usage. The subject would have a lot of resources available. I assume they sniffed out my password or something.

But thanks for the advice everyone. I changed my password and have a feeling it won't be long till someone is back in my mail.

---

### Post by rgreener25 on 2012-01-30
You could turn on two step verification

---

### Post by emiller12345 on 2012-01-30
It appears that those IP's are all apart of the same subnet, Mainly
66.78.108.0/255.255.252.0

---

### Post by Dangertux on 2012-01-30
Emiller is correct those IPs are on the same subnet AND geographically close enough that they could be assigned to the same device.  3G load balancing and Anycast isn't as definitive as a traditional network connection. They could be pulling different IPs from different areas depending on where the device was located in relation to the nearest tower. Essentially, it could be the same device. Are you sure you've never logged in on another device? Or maybe someone knows your password? Boyfriend, girlfriend, roommate brother sister etc...

Just a thought.

---

### Post by jpdeaton on 2012-01-30
> **Dangertux said:**
> Emiller is correct those IPs are on the same subnet AND geographically close enough that they could be assigned to the same device.  3G load balancing and Anycast isn't as definitive as a traditional network connection. They could be pulling different IPs from different areas depending on where the device was located in relation to the nearest tower. Essentially, it could be the same device. Are you sure you've never logged in on another device? Or maybe someone knows your password? Boyfriend, girlfriend, roommate brother sister etc...

Just a thought.
none knows it and I only use my laptop and have checked it on this desktop a handful of times (which no one uses but me and my grandparents and they are computer illiterate)

I've had my passwords change and had someone gain complete control over my android phone in the past. I've even had my bios password changed so that I was locked out.

---

### Post by OpSecShellshock on 2012-01-31
Worth keeping in mind that if you use a smart phone that runs Android you may have had to use a Google account to set it up, so even if you don't use it to actively check your Gmail account it might be passively doing so, or it may just hit the same authentication page when you access a different Google service that uses the same Gmail account. The synch features for those phone applications are usually enabled by default but I think they can be turned off or at least set to manual.

---


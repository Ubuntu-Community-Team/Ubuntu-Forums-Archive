---
title: "Error when trying to install apps under wine."
date: 2009-07-21
forum: Wine
---

### Post by irv on 2009-07-21
When I try to install an app under wine. Like:
```
irv@irv-new-laptop:~$ wine /home/irv/Downloads/Silverlight.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!
irv@irv-new-laptop:~$ 

```
I get this error message
[ATTACH]121889[/ATTACH]
I've tried this with a couple of installs and I get the same error message.

Any idea what is going on?

---

### Post by hikaricore on 2009-07-21
Out of curiousity why are you trying to install the windows version of Sliverlight through WINE?

[http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)

Besides silverlight what other applications have you tried to install?
The more deal you provide for us the better.  Be sure to check the appdb per the sticky to see if your app runs under WINE.

---

### Post by irv on 2009-07-21
> **hikaricore said:**
> Out of curiousity why are you trying to install the windows version of Sliverlight through WINE?

[http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)

Besides silverlight what other applications have you tried to install?
The more deal you provide for us the better.  Be sure to check the appdb per the sticky to see if your app runs under WINE.

I was trying to get Netflix to work with Wine. They do not support Linux. When I go to play a movie, It know I am running Linux and won't work.

---

### Post by directhex on 2009-07-21
> **irv said:**
> I was trying to get Netflix to work with Wine. They do not support Linux. When I go to play a movie, It know I am running Linux and won't work.

Netflix won't work. They use Microsoft's PlayReady DRM system, which cannot work in Wine.

Contact Netflix, tell them you're unhappy, and tell them that they should either scream at Microsoft until they provide the required technology to use DRM in Linux's Silverlight implementation Moonlight - or, even better, tell them to drop the stinking DRM completely

---

### Post by irv on 2009-07-21
> **directhex said:**
> Netflix won't work. They use Microsoft's PlayReady DRM system, which cannot work in Wine.

Contact Netflix, tell them you're unhappy, and tell them that they should either scream at Microsoft until they provide the required technology to use DRM in Linux's Silverlight implementation Moonlight - or, even better, tell them to drop the stinking DRM completely

I have call before, and I just got off the phone again with them but I don't think I am getting anywhere with them. I think the only way us linux users will ever get anywhere with them is to send a petition signed by thousand of users telling them there are loosing out on a big customer base by not supporting linux.

---

### Post by directhex on 2009-07-21
> **irv said:**
> I have call before, and I just got off the phone again with them but I don't think I am getting anywhere with them. I think the only way us linux users will ever get anywhere with them is to send a petition signed by thousand of users telling them there are loosing out on a big customer base by not supporting linux.

Are they, though? People need to vote with their wallets, and actually stop paying them for the service. Money talks.

---

### Post by hikaricore on 2009-07-21
> **directhex said:**
> Are they, though? People need to vote with their wallets, and actually stop paying them for the service. Money talks.

But due to people quite frankly not giving a damn you can never get enough people to just not buy crap.

---

### Post by irv on 2009-07-22
I am thinking about droping them and am looking for someone else. Any suggestion?

---


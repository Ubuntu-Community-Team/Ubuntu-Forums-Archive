---
title: "Website hijacked by another website"
date: 2014-09-30
forum: Security
---

### Post by JohnMac on 2014-09-30
My system: 

Ubuntu 12.04 on desktop
Ubuntu 14.04 on Dell Laptop
Iphone 4

It seems a website I use regularly (abc.net.au) has been hijacked by another site named Unlocator. I used to subscribe to Unlocator, but have ceased my subscription months ago.
I have been able to edit my hosts file and block Unlocator on my desktop PC but now abc.net.au is blocked. It seems my router has been hacked.
If I don't use wifi, eg my partners networked phone, then the site is not hijacked.

Can anyone help?

---

### Post by QIII on 2014-10-01
Hello!

You might first try creating a new browser profile and see if the behavior persists.

What browser are you using?

---

### Post by Lars Noodén on 2014-10-01
Usually there is a way to reset the router to factory defaults.  On some models, there is a button to hold down while powering up.  You'll have to check the model's guidebook.  Then before plugging into to the net, connect locally and reset the password and turn off remote access.  Then configure it to use the right DNS, etc.  You may consider updating the firmware if it needs it and that might be as far as running DD-WRT or OpenWRT, if your hardware supports it.

---

### Post by Bucky Ball on 2014-10-01
abc.net.au??? Doubt that. I'd be looking at the not quite complete uninstallation of unlocator ...

I am in Aus and a regular user of abc iview. Works without issue or infiltration ...

PS: Are you running anything like NoScript or Adblock? Allow them permissions on the site if you are ... Just a thought .

---

### Post by JohnMac on 2014-10-01
The problem is there on Firefox, Chromium and even on Firefox on my Iphone. I have reset my browser with no change.  ?????

---

### Post by QIII on 2014-10-01
The site works for me no problem, so it's not hijacked.

Although I was wondering why Aussies would have their own American Broadcasting Corporation website... ;)

(Eh, Bucky Ball?  What about that?  Huh?  Huh? :) )

Does this behavior occur when other devices (other than your own, that is -- those never used with that subscription) use your router/LAN/wireless?

---

### Post by Bucky Ball on 2014-10-01
> **QIII said:**
> The site works for me no problem, so it's not hijacked.

Which site do you speak of, Q? abc.net.au? I just came up with that. It, of course, links to ABC iview at [THIS address.]("http://iview.abc.net.au/").

To all: I am having no issues with it. To the OP, perhaps we should dig deeper because the problem appears to be at your end ...

---

### Post by andrew102 on 2014-10-03
Can you work out what router you are using and reset it. Particularly, who want to make sure you are using a trusted DNS server. Also you will want to disable Telnet access (or any other form of remote access) from the WAN if it has that enabled.

---

### Post by fugu2 on 2014-10-04
you might consider running a tracert to that website from your affected computer(s) (someone might need to verifiy that this is the right command to use on ubuntu, i only know the windows command for this)```
$ tracepath -n abc.net.au
```also you should check the dns response that your getting (this one is correct)```
$ host abc.net.au
```

---

### Post by Bucky Ball on 2014-10-04
Click [THIS]("http://iview.abc.net.au/"). What exactly is the response?

---

### Post by JohnMac on 2014-10-09
0k that is resolved, I did not unsubscibe from Unlocator correctly. I needed to go into my router config and change the DNS from that which was provided by Unlocator.

Sorry for not responding to the posts. I was away from my PC.

Thanks for your  help.

---

### Post by JohnMac on 2014-10-09
Thank you for your assistance, I was able to resolve my issue by editing my router's DNS. It seems I neglected to replace the DNS Unblocker provided me with when I had an account with them.

---


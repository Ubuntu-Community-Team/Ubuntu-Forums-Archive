---
title: "Huge traffic on ubuntu VPS server"
date: 2024-04-28
forum: Security
---

### Post by krukar on 2024-04-28
Hi
I bought VPS server to play minecraft on modpacks with my friends.
Problem started like 3 days ago, when I started receiving a lot of packets from Some IP adress, that I blocked using ufw. I set a rule to deny all incoming and accept outgoing. Unfortunetlly, now there's a new IP adress that is performing attacks, despite using ufw, and blocking also this IP, it's still attacking. My HDD and CPU are almost always at 100% usage, and I can't do anything about it. I tried to use fail2ban and apache2, but it didn't work out. The traffic was so huge that my VPS provider had to turn off my server, and they don't know what is causing that, and how to deal with that. They suggested that this may be caused by some files on VPS, but I'm only using modpack from curseforge, and few additional mods also from curseforge. My VPS is 16gb of ram, 8 cores and 150 hdd, and while being attacked my bandwith is 8tb and HDD is 11gb out of 150gb full, and there is no way that minecraft modpacks used so much of this. What can I do about this? I'm not specialized in IT etc. so please expalin this to me. Thanks

---

### Post by TheFu on 2024-04-29
There isn't anything you can really do without significant expertise. Many companies pay a proxy company to handle the big inbound packets and drop those that aren't clearly "good" for the intended purpose of the server.  Gambling sites get his with the DDOS attacks before every huge gambling event in the world as a way to extract blackmail payments.  My understanding is that these services aren't cheap.  You might see of the free tier of service offered by CloudFlare could help you.  [https://developers.cloudflare.com/fundamentals/setup/](https://developers.cloudflare.com/fundamentals/setup/) 

Now, if you aren't good at security, then it is very likely your server has been compromised and it is hosting lots of files or as a proxy for criminals.  Just because you didn't put the files there, it doesn't mean someone else didn't and they have taken over your system.  You'll likely want to setup a new server from scratch, not advertise it anywhere and block all connections except from your location until you've gotten some protection in place first.

I know nothing about mindcraft, but addon modules tend to be the most insecure part of any website.  Wordpress addons are notorious for having terrible security.  I'd assuming the same for mindcraft, until proven otherwise.  When looking for addons, don't just look for features. Look for bugs and security problems along with how often the addon is patched and why.  Addons that are released and never patched should probably be avoided completely.  All software has bugs. All of it.

---

### Post by currentshaft on 2024-05-07
aa

---


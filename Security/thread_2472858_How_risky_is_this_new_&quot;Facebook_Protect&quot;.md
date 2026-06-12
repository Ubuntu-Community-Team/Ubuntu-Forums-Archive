---
title: "How risky is this new &quot;Facebook Protect&quot; on an Ubuntu Desktop?"
date: 2022-03-15
forum: Security
---

### Post by AR_Kozz on 2022-03-15
Facebook is forcing millions of users to activate a supposed protection feature based on Onavo, an analytics software it acquired years ago. 

I have no doubt this is another tentacle of Facebook's spyware apparatus, and since they're forcing me to activate it, I want to figure out how to block it from seeing anything outside the browser tab accessing FB itself.

---

### Post by TheFu on 2022-03-15
You can block it by stop using any thing from facebook.
This can be accomplished by adding the 500+ domains run by facebook as 127.0.0.1 to your /etc/hosts or your DNS server(s).

This isn't a new idea.  [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279) is one method.  Using a pihole is another.  [https://www.smarthomebeginner.com/pi-hole-setup-guide/](https://www.smarthomebeginner.com/pi-hole-setup-guide/) claims setting up a pihole is 15 minutes. BTW, a pihole doesn't require a raspberry pi computer. It works fine on an x86 system with Linux container capabilities too.

We have a choice. If you disagree with any company online, we can stop using their stuff AND with a little research we can block access from our computers to their tracking systems.

---

### Post by AR_Kozz on 2022-03-16
Thanks, but I'm not in a position to be able realistically to abandon the major social media companies, just as most of us are in no position to stop using the big 3 cellular providers. They've cornered too big of a market. 

That's why I'm trying to adapt to this forced feature by locking it out of anything I'm not actually doing on Facebook in a browser tab. Similar to the Firefox extension "Facebook container." However my first concern goes beyond the browser to whether the VPN it uses will affect my internet traffic generally, even outside any browser. That would be bad. 

It might not involve any domain name at all, as it's part of their own infrastructure.

---


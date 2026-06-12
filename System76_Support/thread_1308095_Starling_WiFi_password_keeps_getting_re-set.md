---
title: "Starling WiFi password keeps getting re-set"
date: 2009-10-31
forum: System76 Support
---

### Post by Teasdale on 2009-10-31
My Starling has no problem finding my wireless router and connecting, but I've noticed that if I'm gone for any length of time - sometimes with it on suspend, sometimes with the screensaver on, when I get back on, it can't re-connect to the internet. When I open the internet connection box, I notice that instead of the correct password, there's a long string of gibberish there - GB1474FJ8875Hy76309 or something. No wonder it can't connect! So I have to wait for it to finish trying to connect, bring up the box again, type in the correct password, and then it connects.

Sometimes it re-connects with no problem. I don't know what's making the password get changed. Is there a setting I have checked incorrectly? I have it set to "WPA & WPA2" because when I checked that box, it worked - but I have no idea if that's the one I'm supposed to be using.

---

### Post by jdb on 2009-10-31
> **Teasdale said:**
> My Starling has no problem finding my wireless router and connecting, but I've noticed that if I'm gone for any length of time - sometimes with it on suspend, sometimes with the screensaver on, when I get back on, it can't re-connect to the internet. When I open the internet connection box, I notice that instead of the correct password, there's a long string of gibberish there - GB1474FJ8875Hy76309 or something. No wonder it can't connect! So I have to wait for it to finish trying to connect, bring up the box again, type in the correct password, and then it connects.

Sometimes it re-connects with no problem. I don't know what's making the password get changed. Is there a setting I have checked incorrectly? I have it set to "WPA & WPA2" because when I checked that box, it worked - but I have no idea if that's the one I'm supposed to be using.

Your password generates a 256 bit key with pseudo random distribution.
The key is then sent to the access point and compared to a key it has generated from the same password.
The process to make the key uses a hashing function that takes a LOT of cpu time to complete.
The reason for all this is to defeat password cracking attempts.
The gibberish you are seeing is the key.

jdb

---

### Post by Teasdale on 2009-10-31
So then, this is a security feature and I shouldn't try to by-pass it?

---

### Post by jdb on 2009-10-31
> **Teasdale said:**
> So then, this is a security feature and I shouldn't try to by-pass it?

If re-entering your password gets it going again then that's a good thing to do.
It will still produce the key & send that to the access point, you're not really by-passing anything.
I don't know why it's dropping.

jdb

---

### Post by HotShotDJ on 2009-10-31
> **jdb said:**
> I don't know why it's dropping.I've got two thoughts on this.  First, are you using a hidden SSID?  I've had trouble with Network Manager in the past with reconnections/dropped connection when using a router in this mode.  Hidden SSID's really give a false sense of security and I don't recommend its use. It doesn't add any benefits over and above proper WPA2 encryption.

A second thing to look at is your router. I've seen issues such as yours corrected simply by buying a new and more reliable router.  I recall seeing a thread in the System76 forum about certain routers that are known to be troublesome and some specific recommendations for replacements.  You don't have to go with more expensive.  My cheap WRT54G V.8.0 (I paid something like US$49.00 for it 3 years ago) has been rock solid for years.

---


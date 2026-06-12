---
title: "Wireshark showing multiple DNS queries despite no active connections"
date: 2012-01-10
forum: Security
---

### Post by DanR01 on 2012-01-10
I have noticed something a little unusual. 

When I run Wireshark on my system after browsing the internet but with no active internet connections or browsers open I get multiple DNS queries in the form:

```
23    68.735879    192.168.0.3    192.168.0.1    DNS    78    Standard query A ar-ar.facebook.com
``````
24    68.764752    192.168.0.1    192.168.0.3    DNS    182    Standard query response CNAME www.facebook.com A 69.171.242.13
```The thing is these are from sites I have visited earlier (eg ubuntu forums, my email account etc, not just facebook). Just to reiterate, netstat does not show any active connections and firefox is not running. I don't have any Google toolbars installed, I use Scroogle SSL for my searches. Cookies are disabled and I have NoScript and BetterPrivacy addons installed.

You could deduce a list of sites I had visited earlier in the day by running wireshark. Does anyone have an idea of why this is happening. Is it normal?

---

### Post by Dangertux on 2012-01-10
> **DanR01 said:**
> I have noticed something a little unusual. 

When I run Wireshark on my system after browsing the internet but with no active internet connections or browsers open I get multiple DNS queries in the form:

```
23    68.735879    192.168.0.3    192.168.0.1    DNS    78    Standard query A ar-ar.facebook.com
``````
24    68.764752    192.168.0.1    192.168.0.3    DNS    182    Standard query response CNAME www.facebook.com A 69.171.242.13
```The thing is these are from sites I have visited earlier (eg ubuntu forums, my email account etc, not just facebook). Just to reiterate, netstat does not show any active connections and firefox is not running. I don't have any Google toolbars installed, I use Scroogle SSL for my searches. Cookies are disabled and I have NoScript and BetterPrivacy addons installed.

You could deduce a list of sites I had visited earlier in the day by running wireshark. Does anyone have an idea of why this is happening. Is it normal?


I'm going to take a wild guess and say that your default browser is firefox, and is the same browser that is set as default in Wireshark. Sound about right?

If so. Know that firefox "updates" its DNS cache for sites you frequently visit every so often. If firefox is set as your default wireshark browser it will stilll continue being Firefox.

Hope this helps.

---

### Post by hackertarget on 2012-01-10
@dangertux - Good answer.  :)

And just to be sure you could install tshark and run that.

```
sudo apt-get install tshark
sudo tshark -i eth0
```

---


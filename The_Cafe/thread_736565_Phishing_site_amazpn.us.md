---
title: "Phishing site: amazpn.us"
date: 2008-03-26
forum: The Cafe
---

### Post by x1a4 on 2008-03-26
Hi,

I just encountered a phishing site masquerading as Amazon.com.  The url is **amazpn.us**.  If you're an Amazon shopper be sure not to submit any of your info to them.

---

### Post by enchantedsky on 2008-03-26
After a while, it redirects you to Amazon.com. I don't understand what it's trying to phish from you......is it faking Amazon.com's URL in Firefox, when it's still on amazpn.us?

---

### Post by LaRoza on 2008-03-26
> **enchantedsky said:**
> After a while, it redirects you to Amazon.com. I don't understand what it's trying to phish from you......is it faking Amazon.com's URL in Firefox, when it's still on amazpn.us?

It is trying to make you think it is amazon, by getting the amazon content, but it will most likely eventually try to get you to "validate" yourself, by asking for information.

---

### Post by x1a4 on 2008-03-26
Are you saying that site's legit :?:  It seems like they've just leached stuff of of Amazon.  They even claim to be Amazon.com.  If the site were legitimate it should have an Amazpn.us logo, not Amazon.com, shouldn't it? :confused:

---

### Post by LaRoza on 2008-03-26
> **x1a4 said:**
> Are you saying that site's legit :?:  It seems like they've just leached stuff of of Amazon.  They even claim to be Amazon.com.  If the site were legitimate it should have an Amazpn.us logo, not Amazon.com, shouldn't it? :confused:

No, I am saying it is doing its best to fool you, and then ask for information.

---

### Post by Ozor Mox on 2008-03-26
> **LaRoza said:**
> No, I am saying it is doing its best to fool you, and then ask for information.

But anywhere where it asks you for your password, you get redirected back to the real amazon.com.

---

### Post by LaRoza on 2008-03-26
> **Ozor Mox said:**
> But anywhere where it asks you for your password, you get redirected back to the real amazon.com.

Don't trust it, it can be clever in ways that aren't immediately apparent. (It might be a hidden frame, or something that is able to steal your information)

---

### Post by LookTJ on 2008-03-26
Upon further research, it's not a phish

```
[tjl@tjl-laptop ~]$ host amazpn.us
amazpn.us has address 72.21.206.5
amazpn.us has address 72.21.210.11
amazpn.us has address 72.21.203.1
[tjl@tjl-laptop ~]$ host amazon.com
amazon.com has address 72.21.206.5
amazon.com has address 72.21.203.1
amazon.com has address 72.21.210.11

```

---

### Post by Ozor Mox on 2008-03-26
> **Taylor said:**
> Upon further research, it's not a phish

```
[tjl@tjl-laptop ~]$ host amazpn.us
amazpn.us has address 72.21.206.5
amazpn.us has address 72.21.210.11
amazpn.us has address 72.21.203.1
[tjl@tjl-laptop ~]$ host amazon.com
amazon.com has address 72.21.206.5
amazon.com has address 72.21.203.1
amazon.com has address 72.21.210.11

```

Hmm, interesting. Maybe it's one of those cases where someone registered the spoof site and Amazon acquired the rights to the domain name, and now just use it as a redirect of sorts.

Not that I would enter my password or anything else into it!

---

### Post by LookTJ on 2008-03-26
> **Ozor Mox said:**
> Hmm, interesting. Maybe it's one of those cases where someone registered the spoof site and Amazon acquired the rights to the domain name, and now just use it as a redirect of sorts.

Not that I would enter my password or anything else into it!Hmm, upon google search, I find this: [http://www.domaintools.com/products/reports/reverse-ip.html?sample=1](http://www.domaintools.com/products/reports/reverse-ip.html?sample=1)

---

### Post by sunexplodes on 2008-03-27
Yeah, I did a whois, it's owned by Amazon.com.

---

### Post by wieman01 on 2008-03-27
Perhaps Amazon had it registered in order to AVOID phishing.

---

### Post by chrisccoulson on 2008-03-27
Amazon have registered these domains so that you will still get directed to Amazon.com even if you make some common spelling mistakes in the address bar.

---

### Post by x1a4 on 2008-03-27
> **chrisccoulson said:**
> Amazon have registered these domains so that you will still get directed to Amazon.com even if you make some common spelling mistakes in the address bar.

Looks like that's the case.  I just got a reply from Amazon about it and they confirmed it's their domain. Still looks like a phishing site though, and I'll only use amazon.com and amazon.ca .

---

### Post by klange on 2008-03-27
Personally, I find it rather odd that they own amazpn.us but not amazon.us...

---

### Post by Google Spider on 2008-03-27
> **chrisccoulson said:**
> Amazon have registered these domains so that you will still get directed to Amazon.com even if you make some common spelling mistakes in the address bar.

Why don't they just write there that you've reached a redirect to amazon.com, instead of showing all those products. Like [_[COLOR="Blue"]ubuntuforums.com[/COLOR]_]("http://www.ubuntuforums.com/") has.

---


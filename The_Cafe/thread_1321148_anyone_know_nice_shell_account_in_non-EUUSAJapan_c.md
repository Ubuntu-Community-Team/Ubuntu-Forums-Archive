---
title: "anyone know nice shell account in non-EU/USA/Japan country?"
date: 2009-11-09
forum: The Cafe
---

### Post by agnes on 2009-11-09
I don't know if this is the right place to ask it,
but I'm looking for a UNIX (or *BSD) shell account in a country that has nothing (at least, not official) to do with the EU; USA; Canada; or Japan. 

Like: Russia; *stan; "Arabic" countries; China; (countries around) Thailand; Indonesia...

I'm willing to pay a reasonable amount for it.
However, via Google I only find accounts in the USA or EU.


(P.S. Mind you, I'm not doing anything harmful whatsoever. I'm just quite fond of my privacy, relating to national issues.)

---

### Post by schauerlich on 2009-11-09
You're still going through a Dutch ISP to get to your private shell account, so if you're that paranoid, you've got bigger issues to deal with.

---

### Post by Frak on 2009-11-09
The connection from there to your Shell is still monitored, so you can't bypass it using that method.

---

### Post by agnes on 2009-11-09
Hmm yes,
but the ISP can only see I connect to the account (ssh), and not, what I **do** on the account - right? Or not?
(Just neglecting the registration process for the moment.)

---

### Post by Frak on 2009-11-09
> **agnes said:**
> Hmm yes,
but the ISP can only see I connect to the account (ssh), and not, what I **do** on the account - right? Or not?
(Just neglecting the registration process for the moment.)
If I'm correct, your ISP has the right to monitor your activity, so yes they can see what you do on the account.

---

### Post by The Funkbomb on 2009-11-09
You could always just proxy chain through a bunch of Noonecaresastans to your shell account.

That's a little overkill though.

---

### Post by Warpnow on 2009-11-09
> **Frak said:**
> If I'm correct, your ISP has the right to monitor your activity, so yes they can see what you do on the account.

Interesting. So if an ISP can do this...what's the point of a proxy? Couldn't they just monitor what info you send to a proxy?

I don't know anything about this subject.

---

### Post by agnes on 2009-11-09
How can an ISP see what you do on another account?
I know they can see to which hosts you connect, but how can they monitor what you do on e.g. an Chilean host.
For example, assume I read an article (on a website) from a Chilean shell account... the downloading of the article is then the responsibility of the Chilean account, so what does my ISP have to do with it?

---

### Post by Mornedhel on 2009-11-09
Good news everyone, SSH is encrypted !

---

### Post by Frak on 2009-11-09
> **Warpnow said:**
> Interesting. So if an ISP can do this...what's the point of a proxy? Couldn't they just monitor what info you send to a proxy?

I don't know anything about this subject.
In a lot of parts of Europe, ISPs can see your activity.

Fortunately, it is ILLEGAL in the United States for ISPs to view your activity.

---

### Post by doas777 on 2009-11-09
ok, to clarify, your home ISP can see the encrypted traffic. the question is whether they can crack the encryption to see what you are actually doing. my guess is yes if they really really want to, but probably not if you stay under the radar and don't give them a good reason to look at you.

---

### Post by falconindy on 2009-11-09
> **doas777 said:**
> ok, to clarify, your home ISP can see the encrypted traffic. the question is whether they can crack the encryption to see what you are actually doing. my guess is yes if they really really want to, but probably not if you stay under the radar and don't give them a good reason to look at you.
There's been 1 case made public about breaking the encryption on SSH-2. A whopping **4 bytes** were read off of a transmission in what was only made known as "special conditions". I'm not saying its unbreakable, but there's a good chance that the time required would exceed the length of your SSH session.

---

### Post by Rainstride on 2009-11-09
> **Warpnow said:**
> Interesting. So if an ISP can do this...what's the point of a proxy? Couldn't they just monitor what info you send to a proxy?

I don't know anything about this subject.

a proxy keeps a 3rd party from seeing the "real" you. for instance, if you are in a a country other than the u.s. and can't watch hulu, you could use a us proxy to watch hulu. because hulu would only see the u.s. proxy computer. though none of this stops your isp from seeing what you are doing. kind of like a man in the middle attack. the content would have to be encrypted before ever leaving your computer if you don't want you isp watching. witch is why we have tor.  

> **Frak said:**
> In a lot of parts of Europe, ISPs can see your activity.

Fortunately, it is ILLEGAL in the United States for ISPs to view your activity.

phone tapping is illegal here to. but they still do it;).

---

### Post by Xbehave on 2009-11-09
> **Frak said:**
> If I'm correct, your ISP has the right to monitor your activity, so yes they can see what you do on the account.
SSH, it works, the only ISP that can see what the shell acount does is the ISP on which the shell account is hosted.

> **Frak said:**
> In a lot of parts of Europe, ISPs can see your activity.

Fortunately, it is ILLEGAL in the United States for ISPs to view your activity.
LMAO, in Europe cops need a warrant to snoop on you and ISPs are bound by privacy laws.

---

### Post by agnes on 2009-11-09
:) Okay. Thanks everyone.

So my first question still stands.

I do have tor, but it's very slow, plus I'd still have to check every time if I'm browsing via e.g. a proxy from the EU. Therefore, I want a foreign shell account.

(By the way: I don't think they will decrypt ssh data here, since here ISPs already standardly are forced to show everything everybody does on their host... which costs a lot.
Also, this data has to be kept for 2 years. There is not a general rule for EU countries so far, regarding privacy and such. At least I've never heard of it, only heard of people striving for it. Certainly here they don't need a warrant to snoop on you. And, as far as I know, they can ask data from "partner" countries (EU, USA) because of "national security", but everything is "national security" in a small country.)

---

### Post by Xbehave on 2009-11-09
> **agnes said:**
> I do have tor, but it's very slow, plus I'd still have to check every time if I'm browsing via e.g. a proxy from the EU. Therefore, I want a foreign shell account.Unless you are a tor node, tor will not prevent them seeing the IP of your shell and your data is protected by SSH anyway. SSH is all you need tbh, just be aware that whoever hosts you shell (hosters and ISP will have records that their government can do what they want with (subject to their laws)

---

### Post by agnes on 2009-11-11
Ok.
But nobody here knows shell providers, or lives, outside EU/USA? ):P ???

---

### Post by gletob on 2009-11-11
How bout India?

You could find a host on this page that has SSH access.
[http://www.webindiahosting.com/](http://www.webindiahosting.com/)

Maybe Ukraine
[http://www.webhosting.info/webhosts/tophosts/Country/UA](http://www.webhosting.info/webhosts/tophosts/Country/UA)

China?
[http://www.webhosting.info/webhosts/tophosts/Country/CN](http://www.webhosting.info/webhosts/tophosts/Country/CN)

Iran?
[http://www.webhosting.info/webhosts/tophosts/Country/IR](http://www.webhosting.info/webhosts/tophosts/Country/IR)

Cayman Islands?
[http://www.webhosting.info/webhosts/tophosts/Country/KY](http://www.webhosting.info/webhosts/tophosts/Country/KY)

Russia?
[http://www.webhosting.info/webhosts/tophosts/Country/RU](http://www.webhosting.info/webhosts/tophosts/Country/RU)

---

### Post by t0p on 2009-11-11
> **Frak said:**
> If I'm correct, your ISP has the right to monitor your activity, so yes they can see what you do on the account.

Not quite right.  The OP lives in Europe; so his ISP will have an obligation to store data related to which IP addresses he connects with, who he sends email to, who's sent email to him, etc.  They don't have to monitor what he's actually doing.

This is akin to a telephone company's obligation to store the numbers a customer calls and the numbers that call him.  The telephone company doesn't have to actually record the content of calls.

OP: I understand that you don't want a shell account on a US-based server.  But I'm going to recommend sdf.lonestar.org (aka freeshell.org) anyway.  For a nominal charge ($1 last time I checked) you get a shell on one of a network of DEC Alphas running NetBSD, TOPS-20 and Symbolics GENERA. There's no problem connecting from an Ubuntu machine.  This is done over ssh, telnet (if you want to for some reason) or via US-based dial-up. For more info, go check their website at sdf.lonestar.org.

---

### Post by Warpnow on 2009-11-11
> **agnes said:**
> Ok.
But nobody here knows shell providers, or lives, outside EU/USA? ):P ???

Go through this list: [http://www.bylur.net/free/](http://www.bylur.net/free/)

---

### Post by agnes on 2009-11-12
Nice but it doesn't list the country of residence of the providers.

Anyway I found some paid services in South Africa (completely forgot about that country even though Ubuntu comes from it, and they speak English) which happen to be quite cheap, because of the exchange rate.

[http://www.linuxbox.co.za/signup.php]("http://www.linuxbox.co.za/signup.php") e.g. seems trustworthy, and they accept euros or dollars too.

---


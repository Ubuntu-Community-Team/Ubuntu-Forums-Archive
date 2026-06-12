---
title: "Starling (star5) wireless connection drops"
date: 2011-05-25
forum: System76 Support
---

### Post by torosc on 2011-05-25
I recently got a star5 running 11.04 and I have been having an intermittent problem since the first week I got it. The wireless connection to my (or other) router stops without any warning. It is not an "internet connection" issue, but the connection to the router drops. When I try to reconnect, it struggles for a few minutes, asks for the security password (which it already has), but still cannot connect to the router. The only solution I have found so far is to restart the computer, which has been fixing the issue so far.

Any ideas?

t

---

### Post by isantop on 2011-05-25
Can you try unplugging the router for a minute or two, then plugging it back in? That will help rule out a router issue.

---

### Post by torosc on 2011-05-25
The thing is, this is a somewhat intermittent problem that I haven't yet found a way to consistently reproduce. So far, it has happened a few times, using two very different routers (I'm guessing that eliminates the router as the cause). It seems to happen when there are multiple downloads going on.

Thanks,

toros

---

### Post by torosc on 2011-05-26
Okay. This issue is becoming more frequent. I thought first it had to do with the heat somehow, but, only a few minutes ago, the connection got lost just as I was filling out an online form, which means that I had to restart and lose all my work. I can get used to a lot of the quirks of ubuntu/starling but this is kind of a deal breaker if I have to randomly restart my computer and lose my work.

By the way, I never had any of these issues with my Dell that was NOT designed to work with Ubuntu... Getting kind of disappointed...

t

---

### Post by isantop on 2011-05-26
Are there any routers that your system does work reliably on?

---

### Post by torosc on 2011-05-26
I only got a chance to use two different routers, and both had intermittent problems. I don't want to make a generalization based on only two observations, but, that's all I got right now...

t

---

### Post by isantop on 2011-05-27
Were the two different routers different brands, or were they the same?

---

### Post by torosc on 2011-05-28
They are different routers. One is a router/modem combo that Verizon provides, the other is a stand-alone router by Motorola. The other day, while I was trying to turn the wireless card on and off, it crashed Ubuntu, which I have never seen happen before.

t

---

### Post by torosc on 2011-05-30
> **isantop said:**
> Were the two different routers different brands, or were they the same?

So, what do you guys think this issue could be caused by? Software? Hardware? Drivers or OS?

Thanks,

t

---

### Post by pastalavista on 2011-05-30
My guess is IPv6 is enabled in your system but your routers aren't IPv6 capable... Only a guess... Try disabling IPv6 in your network settings.

---

### Post by xian67 on 2011-05-30
I have the same issue with a Lenovo S10. This only started after did a complete upgrade from 10.10 to 11.04.any word on if the IPv6 setting helped?

---

### Post by torosc on 2011-05-31
> **xian67 said:**
> I have the same issue with a Lenovo S10. This only started after did a complete upgrade from 10.10 to 11.04.any word on if the IPv6 setting helped?

No, I didn't get a chance to try that out. How frequent and repeatable is your problem? Maybe this is a 11.04 issue?

---

### Post by imbrinix on 2011-06-19
I have the same issue. I just moved into a new apartment and the wireless connection keeps dropping, then asks to confirm the password, then tries and fails to connect. The only way to make it connect is to restart it again, and then it only works for a short period of time before the same thing happens. This happens while I have multiple downloads going.

---

### Post by isantop on 2011-06-21
If you only use the connection for web browsing, do you still get the issues connecting? Does it take longer for it to occur? 

Would it be possible to try restarting the router? That may help improve the reliability of your connection.

---

### Post by japhyr on 2011-09-17
I'm having the same issue on my panp5 running 10.04.  Wireless randomly drops, it asks for the passphrase repeatedly which it already has, and the only way to reconnect is by restarting the computer.  Restarting the wireless does not help.

These threads seem to end with open questions.  Is there a reliable solution to this problem?

---

### Post by isantop on 2011-09-19
On the PanP5's I believe we only shipped with Intel-based wireless cards, meaning you're having a different issue; if your Pangolin did include Realtek wireless, I apologize.

Is your system still under warranty? This sounds like a wireless card going bad or bad code somewhere in your installation. You should either try running from an Ubuntu 11.04 LiveCD, or replace the wireless card (if the liveCD fails to remedy the problem).

---

### Post by japhyr on 2011-09-20
Thanks.  I'll get around to installing 11.04 pretty soon, and see if the issue goes away.

---


---
title: "If not in logs...where'd they go ??  Intruder??"
date: 2010-10-31
forum: Server Platforms
---

### Post by mistypotato on 2010-10-31
Hi,

Since Port 80 and 443 are the only ports I have open, how is it that an IPAddress can hit my server yet not appear in ANY logs ?

---

### Post by mistypotato on 2010-11-02
noone knows an answer to this ?

---

### Post by abix_adam_pl on 2010-11-02
Could you please specify more deeply, what do you mean ?

> can hit my server yet not appear in ANY logs

Adam

---

### Post by mistypotato on 2010-11-02
> **abix_adam_pl said:**
> Could you please specify more deeply, what do you mean ?
Adam

"Hit"...."arrive"..."be seen at"..."attempt to connect to"..."appear in the firewall...yet not in the logs"

---

### Post by BobVila on 2010-11-02
No need to cop an attitude, bud. The poster was trying to get you to elaborate on what KIND of "hit". SSH login, HTTP get, telnet connection, etc... I doubt you're logging pings; there's a lot of "hit"s that won't normally show up.

---

### Post by NertSkull on 2010-11-02
I'm pretty sure you can also change the level of logging to be more verbose depending on what you are looking for.  

Like with SSH you can make it log more.  I'm sure there must be similar options with apache.

---

### Post by mistypotato on 2010-11-03
> **BobVila said:**
> No need to cop an attitude, bud. The poster was trying to get you to elaborate on what KIND of "hit". SSH login, HTTP get, telnet connection, etc... I doubt you're logging pings; there's a lot of "hit"s that won't normally show up.

There was no "attitude" intended.

He asked for an explanation of the context of "Hit".... as I used it.

The internet makes it difficult to ascertain the mood or feelings  of writings, therefore, we must use smileys at time.   best not to jump to conclusions too quickly simply because YOU interpret something one way or the other.

I'm actually amused at how you took offense.  Try reading the thread again, this time assuming I meant no disrespect.  I think it'll make ALL the difference in the world.  My mistake was assuming others would understand what I meant by "hit".

:P

---

### Post by mistypotato on 2010-11-03
> **NertSkull said:**
> I'm pretty sure you can also change the level of logging to be more verbose depending on what you are looking for.  

Like with SSH you can make it log more.  I'm sure there must be similar options with apache.

True.

The one reason I like to avoid doing this is because the extra verbosity can sometimes wreak havoc on awstats, fail2ban etc in the logs.

I was actually hoping for a simple solution but there may not be one.

---

### Post by abix_adam_pl on 2010-11-03
Dear mistypotato,
I was asking for explanation of HIT, because my English is not perfect. But if I understood your intention, maybe good solution for you is to put a firewall beetwen server and internet and LOG every traffic to server in iptables. But there will be huge logs after that.

Adam

---

### Post by mistypotato on 2010-11-03
Hi Adam,

"Hit" may not have been the best word to use.
If it came over harsh...I was just tying to explain what I meant by "hit". :)

I think on the Internet, you have to use smileys a lot so as not to be mis understood.

I do have a fairly decent Watchguard appliance between the Internet and my server so I can filter a good deal of bad traffic from ever reaching the server in the first place.

But you can't filter every IP and sometimes I see some at the firewall monitor station but I never see an entry into the logs.

I guess the answer is to determine what the web server is set up to log and then look where logs are NOT being made.

It was very nice of you to offer help :KS

---

### Post by abix_adam_pl on 2010-11-05
>  and sometimes I see some at the firewall monitor station but I never see an entry into the logs

It depends, what type of protocol (tcp/udp), what type of service (port) is in the log of your monitor station.

Could you post some example here? It will be better for me, If I could see the traffic logged by WatchGuard, then I can try to explain, what you should see in the srver's log.

best,
Adam

---


---
title: "iptables to allow HTTPS connections only"
date: 2011-07-16
forum: Security
---

### Post by rethab on 2011-07-16
Hi

I have tried to configure my iptables to allow only HTTPS connections to the internet. Unfortunately, I didn't get that to work. I configured it like this:
> 
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -t filter -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -t filter -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -t filter -p tcp --dport https -j ACCEPT
iptables -A OUTPUT -t filter -p udp --dport https -j ACCEPT


It does work, on the other hand, if I allow HTTP. But that's not really what I want..
> 
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -t filter -p tcp --dport http -j ACCEPT
iptables -A OUTPUT -t filter -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -t filter -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -t filter -p tcp --dport https -j ACCEPT
iptables -A OUTPUT -t filter -p udp --dport https -j ACCEPT


Of course I am only trying to access websites via HTTPS ;) Still, I was wondering if HTTPS somehow under the hood requires the HTTP port to be open or if my rules are in some other way wrong.

I'd appreciate it, if somebody could give me a hint.

- rethab

ps: I got the rules from that website: [http://www.linuxquestions.org/questions/linux-security-4/iptables-allow-only-web-browsing-443990/](http://www.linuxquestions.org/questions/linux-security-4/iptables-allow-only-web-browsing-443990/)

---

### Post by CharlesA on 2011-07-16
Keep in mind that not every site supports https.

Might want to check out [this browser plugin]("http://www.eff.org/https-everywhere"), since it would be easier to manage.

---

### Post by rethab on 2011-07-16
That is true and I knew that, but the thing is: I want users of that computer to only access websites that do support HTTPS.

My question went more into 'should it generally be possible to allow only HTTPS connections via iptables'.

Thanks anyway.

edit: That computer is supposed to be used for online banking, which does support HTTPS. I want users to only use HTTPS. I think that cuts down many potential vulnerabilities (user caused). That is necessary in my opinion, since I can protect a computer only to a certain level from a technical point of view.

- rethab

---

### Post by The Cog on 2011-07-16
My guess is that the sites you are trying to connect to have some parts that also require http. For instance, the login might be https, but that page might include scripts, images etc. that are referenced as http rather than https. Probably the easiest way to see is to opemn the firewall and visit the secure site in question which running "watch netstat -t" in a console window. If http connections open to the site as well, then it clearly needs http as well as https.

---

### Post by bodhi.zazen on 2011-07-16
> **The Cog said:**
> My guess is that the sites you are trying to connect to have some parts that also require http.

That would be my guess as well. The default port for web servers is 80 and for example, outside of login or other sensitive information, many sites, including mine are going to be using port 80.

---

### Post by CharlesA on 2011-07-16
> **bodhi.zazen said:**
> That would be my guess as well. The default port for web servers is 80 and for example, outside of login or other sensitive information, many sites, including mine are going to be using port 80.

Same with mine - it uses both http and https.

It might be easier to just set up a proxy to block everything except this bank site.

Take a look at [this page]("http://lifehacker.com/5312820/five-best-content-filtering-tools").

---

### Post by rethab on 2011-07-16
Okay, thank you all.

Still, I thought if that page in question was using HTTPS for its main part and scripts and such via HTTP, wouldn't then the page be displayed but only without the scripts, images, etc? Because I'm getting a 'chrome cant find that page'..

And thank you also for the other hints to solve that problem.

---

### Post by Dangertux on 2011-07-16
It depends on how the site is created. If the initial portal is entirely run on port 80 and you or your input is redirected to a secure server then no. The site would not neccessarily work. It really just depends.

---

### Post by rethab on 2011-07-16
Alright, thanks!

- rethab

---

### Post by SeijiSensei on 2011-07-16
If you could identify the sites you want to permit, you could use iptables to limit access only to those addresses:

```
iptables -A OUTPUT -d 10.10.10.10 -p tcp --dport 80  -j ACCEPT
iptables -A OUTPUT -d 10.10.10.10 -p tcp --dport 443 -j ACCEPT
[etc.]
iptables -A OUTPUT -p tcp --dport 80  -j REJECT
iptables -A OUTPUT -p tcp --dport 443 -j REJECT

```

---


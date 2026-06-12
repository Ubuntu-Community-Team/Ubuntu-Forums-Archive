---
title: "Proxy'ing Wine"
date: 2009-11-06
forum: Wine
---

### Post by Cardamar on 2009-11-06
For a summary of everything here, please direct your attention to the bolded text. If you want a full story, read below.

I've downloaded a Proxy Tunnelling program called "Your Freedom" for Ubuntu. I've configured my system to route all network traffic system-wide through Your Freedom. However, it doesn't seem that my Windows applications under Wine are going through this proxy. Is there any way to route all of Wine's network traffic through this proxy (so my Windows programs utilize the proxy), or do I have to also download the Windows version of Your Freedom, and run that as well? 

Simplified:
I've configured a proxy under Ubuntu. I hit "Apply System Wide", but Wine still isn't running through this Proxy. **Is there any way I can configure Wine to use a proxy?**

---

### Post by edin9 on 2009-11-06
Before anyone helps you, why?

---

### Post by Dark_Stang on 2009-11-06
If all traffic is going through that, then your windows programs are going through that.

---

### Post by edin9 on 2009-11-06
> **Dark_Stang said:**
> If all traffic is going through that, then your windows programs are going through that.

Not necessarily, especially through WINE, that is just unpredictable.

---

### Post by Cardamar on 2009-11-06
I'm wanting to run Wine through a proxy to bypass my university's restrictive firewall so I can log into Steam and play games, etc. 

And yes, one would think that my windows programs are going through the proxy, but they clearly aren't. To check this, I used Firefox (Windows Firefox; through Wine) and checked where a certain site said my IP Address was from. It said New Zealand. I live in New Zealand, but the proxy server I'm trying to route my programs through is in the US. Visiting the same page on Firefox through Ubuntu causes the page to think I'm from the United States. So, this proxy is obviously working with my Ubuntu programs, but not my Windows programs; despite me clicking "Apply System-Wide" in Preferences -> Network Proxy.

So, any ideas?

---

### Post by Dark_Stang on 2009-11-06
Well let's find out for sure whether your going through that proxy or not. Also, proxying a game is going to suck, just letting you know.
Copy tracert (trace route) from a windows XP machine. It should be in the /Windows/System32 folder. 
Put it in your ~/.wine/drive_c/windows/system32 folder.
Run cmd.exe from that same folder.
Run "tracert google.com"
Follow the hops and see if you go through your proxy.

---

### Post by Cardamar on 2009-11-06
Thank you, I'll give that a try (:

And I know; I was Proxying some games when I used windows. My ping on most American servers is around 250. As long as it's just distance lag, and not bandwidth lag, anything upto 300-350 is pretty acceptable/unnoticable. It's nothing us Kiwis aren't used to dealing with on online games =P

---

### Post by SKLP on 2009-11-07
If you set a proxy in Ubuntu (in Preferences) only apps which explicitly supports proxies will use that setting. 

There is a tool called tsocks ([http://tsocks.sourceforge.net/](http://tsocks.sourceforge.net/)) which should allow you to route an all the traffic of a specific application through a proxy. I believe it is in APT as well.

---

### Post by Ex-Opesa on 2009-11-14
Can any one give more instructions to use tsocks and use wine programs via proxy?
I also want to use wine programs via proxy. :)

And i have came accross this program ProxyFirewall, it creates rule for programs to run them under proxy. But this program isn't running well under wine, it fails to 'Intialize Firewall'

---


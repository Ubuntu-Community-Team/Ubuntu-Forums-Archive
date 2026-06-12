---
title: "People using Routers .... Read this"
date: 2014-06-25
forum: The Cafe
---

### Post by linuxyogi on 2014-06-25
[http://efytimes.com/e1/fullnews.asp?edid=132220](http://efytimes.com/e1/fullnews.asp?edid=132220)

I am not sure Cafe is the right place but since this is not a support thread I am posting it here.

> **[FONT=verdana][SIZE=2][COLOR=black]Wednesday, March 05, 2014[/COLOR][/SIZE][/FONT]**:         [FONT=verdana][SIZE=2][COLOR=black]  A recent report by internet security research firm, Cymru has  shockingly revealed that over 0.3 million small office and home routers  (SOHOs) around the world have been compromised using man-in-the-middle  attacks. The 'Growing Exploitation of Small Office Routers Creating  Serious Risks' report clearly indicates that routers primarily in Europe  and Asia have been compromised by what they term as SOHO pharming. 


[FONT=verdana][SIZE=2][COLOR=black]Specifically, a majority of  these lie in countries like Vietnam, India, Italy and Thailand. The  routers in the mentioned countries have been affected by changing their  DNS settings from their ISP&#8217;s default to two UK IP addresses (5.45.75.11  and 5.45.75.36). Routers were affected in two ways. In one, a malicious  code was used to target those routers which had their GUI's accessible  from the internet. Secondly, the other target routers were those that  were vulnerable to ROM-O attacks, with a majority that ran ZyXEL&#8217;s ZynOS  falling under the category.   

The research team has however  still not detected any evidence to suggest the two IP addresses were  being used for malicious activities. Meanwhile, Cymru has advised users  to check the DNS settings on their routers to make sure that they match  the ISP&#8217;s DNS.    

         [COLOR=black]  ***Saurabh Singh, EFYTIMES News Network***[/COLOR]           [/COLOR][/SIZE][/FONT]


[/COLOR][/SIZE][/FONT][FONT=verdana][SIZE=2][COLOR=black]

[/COLOR][/SIZE][/FONT]

---

### Post by pqwoerituytrueiwoq on 2014-06-25
set your DNS servers on your computer to say google or open dns

---

### Post by linuxyogi on 2014-06-25
> **pqwoerituytrueiwoq said:**
> set your DNS servers on your computer to say google or open dns

+1

I guess allowing access to router's configuration interface from the WAN side can cause more serious issues besides just the DNS.

---

### Post by lisati on 2014-06-25
+1 to being careful. This can include changing your router's password to something other than the default.

---

### Post by pqwoerituytrueiwoq on 2014-06-25
and if it is open on the wan i suggest using the output of this command
```
cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c${1:-256}
```
that will keep a attacker busy for a while

---

### Post by DuckHook on 2014-06-26
Why would *any* SOHO want to set their router configuration to be accessible from the WAN side? What circumstances would create such a necessity that it outweighs the risk?

---

### Post by LastDino on 2014-06-26
> **DuckHook said:**
> Why would *any* SOHO want to set their router configuration to be accessible from the WAN side? What circumstances would create such a necessity that it outweighs the risk?

I don't know about benefits, but mostly it happens due to lack of awareness. Almost all the routers this days are plug and play, while that is good, people actually never bother to dive deep and try to learn functions of it and ride on default settings, including passwords. 

Having said that, I'm one of those people, I use small router within main router and sometimes get too complacent  about security. The only thing  I do is blocking all inbound from Gufw.

---

### Post by RichardET on 2014-06-26
So, don't allow remote access of your router;  problem solved.

---

### Post by 3rdalbum on 2014-06-26
I like how it says "0.3 million" instead of "300,000". Makes it sound like more.

---

### Post by Old_Grey_Wolf on 2014-06-26
That is old news. I guess some people never got the message. People have been told to disable WAN remote access for years.

---


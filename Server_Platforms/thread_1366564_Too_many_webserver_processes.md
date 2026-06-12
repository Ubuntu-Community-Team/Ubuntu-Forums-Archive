---
title: "Too many webserver processes"
date: 2009-12-28
forum: Server Platforms
---

### Post by cronick on 2009-12-28
Hello,
 
I have a ubuntu webserver. Out of the blue the server has suddenly started to do this wierd thing. It starts 100 www-data processes (webserver processes) in a matter of one minut and then the webserver freezes. When I then kill all the processes with "killall -9 apache2" and start the webserver again, everything is back to normal - except the same thing happens again in just one minut. I guess the .conf is then limited to 100 clients or something, but why are these processes piling up in a matter of one minut?
 
I have tried to disable all of the hosted domains on the server (it is running Plesk) - and no websites therefore running on the server - but it is still making all of these processes. Is there any way that I can see where these processes come from and what URL they are trying to match. 
 
Any ideas at all will be of appreciation.

---

### Post by BkkBonanza on 2009-12-28
Have a look in the apache log and see what apache says is happening. This should tell you what it's doing. If unclear post output here.

---

### Post by cronick on 2009-12-29
I solved the issue. By looking through the incoming tcp request, a specific IP address was trying to overload the webserver - and with success. After I blocked that IP in the firewall the problem has not occured since. I believe that term for what the person was doing is called DoS attacking. Do you know how to prevent this in the future? Also, how do I setup Apache so it will not freeze again if 100 simultanious threads are running?

---

### Post by Project PWNED on 2009-12-29
I'm not trying to steer you off of using Apache but from what I've heard (I don't have large websites or a bunch of visitors to a webserver to verify this) you can run a webserver called nginx, which can handle all the load of people trying to connect to your site. I've heard very bad things about Apache - how you need a server with lots of RAM, CPU, etc. to handle large demand, including a denial of service attack.

It would be worth it to try it out because if it's intentionally directed at you, the attacker will just change their IP address or spread the attack across numerous IP addresses to get you again.

---

### Post by BkkBonanza on 2009-12-29
Re: DoS attack. You can create iptables rules that will rate limit incoming conenctions. The job is fairly easy when just DoS but when you have DDos (distributed) then you have a real nightmare and likely need outside help.

Re: Nginx.
I've used Nginx for a few years and it's great. Love it. It doesn't have all the bells and whistles of Apache in full bloom but it uses very little memory and it doesn't spawn new processes to handle each request. It uses a table based asynchronous method that scales very well up to thousands of hits per second without gobbling up memory. Perfect for older systems and small VPS hosts. 

It's now the third most popular web server on the net after Apache and IIS. I highly recommend it. The config syntax is different but I find it both easier and more sensible. The biggest stumbling block for new users is that PHP is handled differently and rather than starting a new interpreter for each request it proxies each request to a fastcgi process. This also has some advantages performance wise.

[http://wiki.nginx.org//Main](http://wiki.nginx.org//Main)

You can read up on Nginx around the web and some of the big name sites that use it now. 

It's like the difference between driving a Porsche and a Suburban.

---

### Post by Project PWNED on 2009-12-29
Subscribing to nginx mailing list is useful too.

---

### Post by cronick on 2010-01-01
Thanks for your input. I'm not in a mood right know for testing and getting to know a completely new webserver such as nginx, but I will most definitely take a look at it in the near future.

---

### Post by Vegan on 2010-01-01
I see Dos floods once in a while, I ignore them. I have lots of RAM on my web appliance so I am do not care how many threads Apache was to spawn.

My policy: Bite Me.

---

### Post by HighCommander540 on 2010-01-01
> **Vegan said:**
> I see Dos floods once in a while, I ignore them. I have lots of RAM on my web appliance so I am do not care how many threads Apache was to spawn.

My policy: Bite Me.

Except you policy on everything, is always counter-intuitive. Usually you like the harder not smart way....Or this case more expensive.

---

### Post by Vegan on 2010-01-01
I actually see it as a stress test to see what the real capacity of the machine is. Evidently my Pentium IV can server a lot of clients at one.

---

### Post by HighCommander540 on 2010-01-01
> **Vegan said:**
> I actually see it as a stress test to see what the real capacity of the machine is. Evidently my Pentium IV can server a lot of clients at one.

BTW, 1.5GB of RAM. Is actually not remotely a lot.

---

### Post by bodhi.zazen on 2010-01-02
I would +1 the suggestion of an alternate web serever, nginx or lighttpd

If you need to stay with apache because of some feature take a look at either mod_evasive or learn iptables =)

---

### Post by Skidbladniir on 2010-01-02
A good ip-table client is ufw.  :)

---

### Post by HighCommander540 on 2010-01-02
> **bodhi.zazen said:**
> I would +1 the suggestion of an alternate web serever, nginx or lighttpd

If you need to stay with apache because of some feature take a look at either mod_evasive or learn iptables =)

Well if you are like a pro Ubuntu dude and this is your opinion...Why doesn't Ubuntu use one of these be default instead?

---


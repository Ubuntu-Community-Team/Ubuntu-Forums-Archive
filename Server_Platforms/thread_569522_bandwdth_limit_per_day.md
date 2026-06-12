---
title: "bandwdth limit per day"
date: 2007-10-07
forum: Server Platforms
---

### Post by Jakadinho on 2007-10-07
Hy,
Here is my problem. My daily limit per internet is 3GB but if i use proxy its OK.

So i would like to have something (itables i guess) that would stop all trafic exept proxy after 2.9 GB is spent. 

PLZ write as much information as u can becouse im quite new in linux.
Thanks

---

### Post by HermanAB on 2007-10-07
Google for 'iptables rate limiting' and 'iptables bw limiting'.

Cheers,

Herman

---

### Post by HermanAB on 2007-10-07
also search for 'iptables tc' while you are at it.

Cheers,

H.

---

### Post by Jakadinho on 2007-10-08
I read it but its very hard. I tought someone with good knowlege about this can make it in 5min becouse i think i would need weeks to finish it.

---

### Post by HermanAB on 2007-10-08
'Very hard' is an understatement.

Try this:
[http://www.metamorpher.de/fairnat/](http://www.metamorpher.de/fairnat/)

Cheers,

H.

---

### Post by netlogic on 2007-10-08
Isn't is easier to just install a bandwidth monitor? you need to configure your iptables by hand at this point and use cron to refresh the script every 24hrs, because no firewall script packages do what you want to do. that's something you have to do trial and error for few days and work out a good solution.

if you are looking for a bandwidth monitoring tool
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by Jakadinho on 2007-10-15
I think i dont have skills to do it on my own so I guess i will just have to wait until someone create some kind of program for it. I hope it will not take years.

---

### Post by MJN on 2007-10-15
A quick Google search found the following at [http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html) which is surely pretty much what you need, or at least a good starting point:

[I][COLOR=Gray]7. Setting transfer quotas with quota*
Setting transfer quotas can be very useful in many situations. As an example, a lot of broadband users will have download quotas set for them by their ISP and many may charge extra for every megabyte transferred in excess of this quota. You can use iptables to monitor your usage and cut you off when you reach your quota (say 2GB) with a rule similar to the following:

-A INPUT -p tcp -m quota --quota 2147483648 -j ACCEPT
-A INPUT -j DROP

You can then view your usage with the following command:
$ iptables -v -L

You would also need to reset the quota every month manually (by restarting iptables) or with a cron job. Clearly your computer would need to be 'always-on' for this example to be of any use, but there are also any other situations where the quota extension would be useful.[/COLOR]   

[/I]I'm no iptables expert myself (don't actually use it) but I'm sure it would be possible for the quota counter to only decrement against non-proxy packets (i.e. only match non-proxy source addresses) - perhaps with **-s ! <ip.of.proxy.server>** included?

This all sounds too easy so perhaps in my naivety I'm missing something crucial!!

Mathew

P.S. With you only being interested in a daily cap the requirement for always-on is less significant. However, in case you are regularly rebooting throughout the day you could have a little script which runs on shutdown/reboot to read out the current quota count (using the command above) and save this value to a file. A startup script (which you'd need to put the rules in place anyway) could then be used to seed the quota rule with the value from the file. A cron script would then run at midnight to reset the value in the file and restart iptables.

EDIT: If one of the guys can't help you with something immediately and you're still stuck I'll try and find some time to jot some scripts down to achieve this. As I mentioned I'm not overly familiar with iptables however given the above it should be possible to come up with something.

---

### Post by Jakadinho on 2007-11-06
I tried few things but nothing seems working.At this time i would accept also script that stop internet after 3GB without this proxy stuff

Im desperate now. I been blocked soo much time now

---

### Post by MJN on 2007-11-06
What exactly have you tried? The iptables quota stuff? Talk us through what you did, and what happened, and we can work out what's going wrong.
 
Don't give up just yet!
 
Mathew

---

### Post by Jakadinho on 2007-11-06
Okey soo lets see.
Basicly i come up with this:


-A INPUT -p tcp -m quota --quota 3021225472 -j ACCEPT
-A INPUT -j DROP


What else i have to do and dont know how:

1) im not shure if this script is counting only input or output data also ? I would need it to do both and to me it looks like it count only input.

2) How to include proxy IP. You mention -s ! <ip.of.proxy.server> but i dont know where to put it in my script (midle, back.....)

3) What kind of command to use to save data informations in file on rebot and load it at startup.

4) after the limit is reached this script block all conections but i would like it to block only non-proxy


So this is whats bothering me. Thx for taking your time. Lest hope we can solve this

---

### Post by MJN on 2007-11-06
As I said I don't use iptables so I'd be learning at the same rate as you so someone with iptables experience can surely step in here to walk you through the process otherwise it'll be the blind leading the blind.

It really doesn't seem like rocket science to me, but then perhaps that's my naivety showing through.

Mathew

P.S. Maybe it'd be easier to choose an ISP without limits, if at all possible where you are! ;)

---


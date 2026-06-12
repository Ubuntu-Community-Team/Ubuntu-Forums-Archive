---
title: "fail2ban + ufw"
date: 2008-08-13
forum: Security
---

### Post by jolly79 on 2008-08-13
Hi guys..


I have a server running ssh and apache, so i want both port 22 and 80 open.
So i have been running it with fail2ban and ufw, but i have just noticede now.

That since i
sudo ufw defalt deny and added this sudo ufw allow all port 22 (and ofcouse port 80) 

Now the firewall cleans the rules made by fail2ban, so people is not getting blockede eny more.

Is there eny way around this??

Cheers 

-Gustav

---

### Post by HermanAB on 2008-08-13
Simple really.  Don't use fail2ban.  Rather use rate limiting.

iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh \
-m limit --limit 1/minute --limit-burst 1 -j ACCEPT
iptables -I INPUT -p tcp -m state --syn --state NEW --dport ssh -j DROP

---

### Post by jolly79 on 2008-08-13
Ok sounds good...

I still want people to be blocked if they have 3 wrong password attempt, also on the webserver.

Do this help that to??

And how to use it??

---

### Post by HermanAB on 2008-08-13
Rate limiting limits the speed with which people can try new passwords.  It foils brute force attacks, but one can carry on trying forever if one is bloody minded enough.  The protection lies in the fact that if your passwords are sufficiently strong (mine are 16 characters) then the sun will go nova before they manage to discover a working password.

---

### Post by jolly79 on 2008-08-18
Hi again

so i dient go for the iptable rules that herman gave me, i found out that lokkit firewall is compatible with fail2ban.

Maybe shorewall is to... dident give a go..

Would love to get ufw back, but it still delete fail2ban iptable rules.

thanks for the effort guys :-)

---

### Post by cariboo on 2008-08-19
I tried fail2ban a couple of weeks ago, I found that it didn't do what I really wanted it to either. I have since installed denyhosts and I am quite happy with the results.

I know I can use iptables to do the same thing, but I'm lazy and denyhosts was easier.

Jim

---


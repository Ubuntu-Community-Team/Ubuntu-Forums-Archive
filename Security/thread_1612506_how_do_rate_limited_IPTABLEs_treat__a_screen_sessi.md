---
title: "how do rate limited IPTABLEs treat  a screen session on ssh after disconnection"
date: 2010-11-03
forum: Security
---

### Post by tapas_mishra on 2010-11-03
Take this scenario Ff  I have rate limited the connections to 4.(i.e if you attempt 4th connection you wont be able to login for some time.)
If in a minute I get disconnected 3 times 
while I was already logged in on the server with a screen session,
will I be able to login or I need to keep quite for a minute?
> -A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --name DEFAULT --rsource -j DROP
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name DEFAULT --rsource


---

### Post by The Cog on 2010-11-05
I believe you would have to wait for the minute before making another connection attempt. But screen will keep the applications working - it is incredibly valuable when you don't have reliable connectivity.

---

### Post by CharlesA on 2010-11-05
Yep, you'd have to wait for a minute.

If it's a new connection, it counts as a "hit"

---

### Post by tapas_mishra on 2010-11-08
Ok.

---


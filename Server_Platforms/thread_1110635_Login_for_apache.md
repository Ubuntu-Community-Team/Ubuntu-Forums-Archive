---
title: "Login for apache?"
date: 2009-03-30
forum: Server Platforms
---

### Post by DogoJosho on 2009-03-30
When I try to access my apache website from a remote url (my ip **.***.***.***:80) it tells me to login! then i try without the :80 and it still tels me to! I checked every other comp on my network and no other computers on my network are running a port 80 anything!

Also i tried entering root without a pass, then i entered root with my MySQL pass, the i tried entering my admin info, and none of those worked either!

In the dialog it says "Authentication Required, Remote Access"

And when i click cancel this comes up on the page
```

HTTP/1.1 200 OK
Server: NetPort Software 1.1
Content-type: text/html
Expires:0

<HTML><HEAD><META HTTP-EQUIV="refresh" CONTENT="0;url=userfail.htm"></HEAD></HTML>

``` 

Please Help,
Dogo Josho

---

### Post by BkkBonanza on 2009-03-30
Looks like you're getting NetPort on port 80. Not sure what that is but it's not Apache. So either you are giving the wrong ip or you aren't running apache on port 80. Do you know what Netport is? Is it something else you're running? Maybe it is your router? If it is your ISP then it looks like they are blocking your port 80 - which is not uncommon for ISPs as they don't really like you running a web server on your connection (unless you pay for a commerical line with static ip). There are ways around that involving running apache on another port.

BTW now that you entered your root password on some unknown authentication service you may want to change it. Whoever monitors the logs for that service may now have your root password.

---

### Post by hyper_ch on 2009-03-30
I tend to think it's the router that has webbased administration open also for the wan. But that's just a guess.

---


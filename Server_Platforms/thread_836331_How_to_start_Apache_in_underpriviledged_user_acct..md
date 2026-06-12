---
title: "How to start Apache in underpriviledged user acct.?"
date: 2008-06-21
forum: Server Platforms
---

### Post by madu on 2008-06-21
Hi,

Pretty basic question I guess. But I cant seem to get it work.
I'm running a small server, just for educational purposes, and I'm running it under in main account, the account with 'sudo' privileges. But I'm a little worried running it in my main account where I have all my other stuff. I was told Apache runs as a separate user, but I'd sleep much better if I can run it under a different underpriviledged account.

The problem is, once I create a new account without many priviledges, I cant install Apache in that account, so I'm not sure how to get Apache running. If somebody could briefly explain this process of present a guide I would be immensely thankful.

Thank you.

---

### Post by Oldsoldier2003 on 2008-06-21
> **madu said:**
> Hi,

Pretty basic question I guess. But I cant seem to get it work.
I'm running a small server, just for educational purposes, and I'm running it under in main account, the account with 'sudo' privileges. But I'm a little worried running it in my main account where I have all my other stuff. I was told Apache runs as a separate user, but I'd sleep much better if I can run it under a different underpriviledged account.

The problem is, once I create a new account without many priviledges, I cant install Apache in that account, so I'm not sure how to get Apache running. If somebody could briefly explain this process of present a guide I would be immensely thankful.

Thank you.
Apache runs as a separate user and sets up its own directory tree. Installing apache under your account is perfectly okay.

---

### Post by windependence on 2008-06-21
As Oldsolier said this is pefectly normal behavior and you have nothing to worry about. If you check in top while Apache is running you will see processes under user www. These are Apache processes and are not running under the priviliged account.

-Tim

---

### Post by madu on 2008-06-21
Thank you very much Oldsoldier and windependence. 
If it is the normal way of running Apache thats ok then I guess. Thank you again.

---


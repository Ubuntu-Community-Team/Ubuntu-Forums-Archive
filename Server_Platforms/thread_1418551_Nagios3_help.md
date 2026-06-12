---
title: "Nagios3 help"
date: 2010-02-28
forum: Server Platforms
---

### Post by janthes on 2010-02-28
Hi,

I've installed Nagios3 following instructions from [https://help.ubuntu.com/community/Nagios3](https://help.ubuntu.com/community/Nagios3). After step 1, where is says to login from localhost/nagio3, I'm stuck. I open up Firefox and type in [http://192.168.1.100/nagios3](http://192.168.1.100/nagios3) (my server's ip), Firefox gives the error message "Problem loading page". 

My server is Karmic, and I apt-get update'd & upgrade'd but I still can't connect. Any ideas on how I can fix this? Thanks!

---

### Post by davec64 on 2010-02-28
Hi,

Just looking at your post, you did type the full path in (including the [http://)](http://)) as:

```
http://192.168.1.100/nagios3
```

Have you tried:

```
http://localhost/nagios3
```

---

### Post by janthes on 2010-02-28
Thanks for the speedy reply Dave!! Yes, I typed [http://192.168.1.100/nagios3](http://192.168.1.100/nagios3), and [http://localhost/nagios3](http://localhost/nagios3) still gives me the "Problem loading" error.

---

### Post by stlsaint on 2010-02-28
Ensure that there is no firewall blocking that server, reinstall nagios and or reboot server.

---

### Post by davec64 on 2010-02-28
Following on from Stlsaint, have you set up a password yet:

```
sudo htpasswd -c /etc/nagios3/htpasswd.users nagiosadmin
```

---

### Post by janthes on 2010-02-28
Got it!! It was ufw. I 'sudo ufw disable' and now I can log in! :) Thanks stlsaint! How do I label this thread as Solved btw?

---

### Post by davec64 on 2010-02-28
I think it's up in the thread tools.
All the best :)

---


---
title: "how do you host a web site with ubuntu 8.4 desktop?"
date: 2008-11-13
forum: Server Platforms
---

### Post by maclin on 2008-11-13
i made a web site with iweb and i whant to know how to host it on my desktop:confused: plz help

---

### Post by CrucifiedEgo on 2008-11-13
all you should have to do is:
```
sudo aptitude install apache2
```

and then put the files for the site in /var/www

Make sure it works by browsing to [http://localhost](http://localhost).  Once it does, you'll need to enable port forwarding on your router(port 80) to your computer.  At that point, you can either have people browse to your IP address (find it at [http://www.whatismyip.org](http://www.whatismyip.org)) or use a service like dyndns.org to point "yourname.dyndns.org" to your IP address.  

if all this sounds complicated, it really isn't.  take it one step at a time and do't be afraid to google anything you're unsure of, or search the forums.  If you still have questions, let us know.

---


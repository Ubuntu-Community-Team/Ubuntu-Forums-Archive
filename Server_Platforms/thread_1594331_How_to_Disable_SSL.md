---
title: "How to Disable SSL?"
date: 2010-10-12
forum: Server Platforms
---

### Post by batgranny on 2010-10-12
Hi folks, 

I have a web server that is currently running SSL.  I want to revert the website back from https to http.  Would anyone here know how I would go about doing this?

Thanks

---

### Post by Ryan Dwyer on 2010-10-12
sudo a2dismod ssl
sudo a2dissite default-ssl
sudo service apache2 restart

---

### Post by batgranny on 2010-10-13
Wow that was quick and worked a treat!

---

### Post by Qutaibah on 2011-12-07
[I]Re: How to Disable SSL?
sudo a2dismod ssl
sudo a2dissite default-ssl
sudo service apache2 restart[/I]


YOU SAVED ME :D:D
thanks alot

---


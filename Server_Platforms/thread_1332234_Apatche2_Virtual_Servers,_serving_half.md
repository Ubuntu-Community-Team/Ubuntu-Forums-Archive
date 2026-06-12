---
title: "Apatche2 Virtual Servers, serving half"
date: 2009-11-20
forum: Server Platforms
---

### Post by scottybwoy on 2009-11-20
Hi all,

I have Apatche2 with Virtual servers configured correctly, I believe, but...

I have 3 sites enabled, but only 2 show up.  The third one was just copied from the 2nd and ammended accordingly and enabled.

Using a2ensite it confirms that the site is already available.  Why whould it be only showing two of the sites and not the third, is there a limit?

Thanks

---

### Post by Hungry_Wolf on 2009-11-20
no..the limit is not at 3 sites.  I believe is your NameVirtualServer settings that caused this.

Do  you have your own dns setup on the server for the domain?

---

### Post by cdenley on 2009-11-20
You probably don't have it configured properly. Can you post your vhost configurations? Is your browser displaying the page cached from before you configured the third site? Did you reload apache?

---


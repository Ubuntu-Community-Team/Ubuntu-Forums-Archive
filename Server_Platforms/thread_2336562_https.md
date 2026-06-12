---
title: "https"
date: 2016-09-09
forum: Server Platforms
---

### Post by Vegan on 2016-09-09
My sites on Azure all use HTTPS and if a user enters with HTTP I use a simple script to redirect them to HTTPS , MSFT provides a *.azurewebsites.net certificate so all of their apps can use this. This script is generic and works with any URL.

<script type="text/javascript">if (window.location.protocol != "https:") window.location.href = "https:" + window.location.href.substring(window.location.protocol.length); </script>


Come January Chrome will start using red unsecured tags on the address bar to shame non HTTPS sites into change.

Now Apache is not HTTPS out of the box so does anyone know how to set that up so that a self signed certificate can be installed on an appliance to support HTTPS?

---

### Post by bob_jones2 on 2016-09-11
What's your end-goal here ?  To setup your server so that you don't get "shamed" by Chrome etc. ?

In which case, I suspect you'll find a self-signed certificate won't cut it.

---


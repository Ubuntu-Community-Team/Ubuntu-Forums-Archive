---
title: "VirtualHost - Multiple domains pointing to same folder"
date: 2011-03-22
forum: Server Platforms
---

### Post by otherjohn on 2011-03-22
Hi all,
from the title alone, you probably can speculate that I am a newbie at this.

I am attempting to setup Ubuntu Server 10.10 as virtual host that will have a SaaS on it running 100s of domains to point to same script. What is the best practice for this. I am under the impression i can just add the pointing domains to the server-alias line in the vhost file but I am not sure this is the best option. Can anyone point me in the right direction. I have looked up and read plenty of docs on virtualnamehost setup but none that I found cover this case in particular.

John

---

### Post by SeijiSensei on 2011-03-22
If you're really talking about *hundreds* of domains, you could list them all in ServerAlias, but it may be easier to make the DocumentRoot in /etc/apache2/sites-enabled/000-default point to the location of the common script.

---

### Post by otherjohn on 2011-03-22
I think I found what I am looking for under "Mass Vhost"

---


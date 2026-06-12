---
title: "[SOLVED] DNS information in/for ubuntu server (behind smoothwall)"
date: 2007-09-10
forum: Server Platforms
---

### Post by juanhunglow on 2007-09-10
I have been running a server some some wordpress, gallery2, ampache and other file storage and web things.  I recently got an old pc that I decided to try and get working as a firewall.  I chose smoothwall based on the small amount of hardware needed.  
The problem I've run into occurred when I tried to move my server onto the DMZ side of the firewall.  I have set the ip, netmask and gateway.  The last part is that I need to input the DNS server ip's from my ISP, which I have, but I just don't know where the information goes.  I have tried on /etc/network/interfaces but either that isn't where the DNS info should go or I'm not using the correct syntax.

Anyone who can point me to the correct location to put the DNS info, and the proper syntax, to get the DMZ working would be much appreciated.

Thanks,
J

---

### Post by rickyjones on 2007-09-11
You will want to add the DNS server information to the /etc/resolv.conf file.

```

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

Replace the xxx.xxx.xxx.xxx with the DNS server IP addresses that you need.

Hope this helps!

-Richard

---

### Post by juanhunglow on 2007-09-12
rickyjones,
Thanks for the info.  I knew that it couldn't be difficult, just knowing where to put what and how.  I appreciate the response.  
J.

---

### Post by rickyjones on 2007-09-12
> **juanhunglow said:**
> rickyjones,
Thanks for the info.  I knew that it couldn't be difficult, just knowing where to put what and how.  I appreciate the response.  
J.

You're welcome. :)

-Richard

---

### Post by juanhunglow on 2007-09-25
> **rickyjones said:**
> You're welcome. :)

-Richard

You are a gentleman and a scholar.  Got this up and running over the weekend without a hitch.

Thanks again.

-John

---


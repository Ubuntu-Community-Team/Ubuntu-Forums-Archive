---
title: "Still says &quot;new release available&quot; after upgrade"
date: 2013-05-01
forum: Server Platforms
---

### Post by Kethinov on 2013-05-01
Just upgraded my Linode server to 13.04 successfully. When I ssh into it though, it still says the new release is available.

```
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.4-x86_64-linode31 x86_64)

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
```

When I run the do-release-upgrade command again, it just says "no new release found" because there are of course no further upgrades.

How can I fix the glitch that's causing it to tell me there's a new release available even though I already upgraded to it?

---

### Post by aronwalker on 2013-05-01
> **Kethinov said:**
> Just upgraded my Linode server to 13.04 successfully. When I ssh into it though, it still says the new release is available.

```
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.4-x86_64-linode31 x86_64)

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
```

When I run the do-release-upgrade command again, it just says "no new release found" because there are of course no further upgrades.

How can I fix the glitch that's causing it to tell me there's a new release available even though I already upgraded to it?

This also happened to me - I ssh'ed to it and left the session running over night. In the morning I cam back, my session had closed. I started a new session and rebooted it and I had this message. I personally think (guess) that it is to do with me ssh ing to it and missing out some really important step where it requires my input. As you say, you can't upgrade it when it is at the latest version. I am not overly fussed about it but if you really want to get rid of it, I would see if they is some way of running the upgrade script again.

Hope this helps

Aron

---

### Post by jonobr on 2013-05-01
I posted a link with the possible cause and solution [ here ]("http://ubuntuforums.org/showthread.php?t=2140654&p=12627239#post12627239")

---


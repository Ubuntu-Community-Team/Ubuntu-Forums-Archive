---
title: "[SOLVED] UFW (uncomplicated firewall) Hardy errors"
date: 2008-05-10
forum: Security
---

### Post by RRFarFar on 2008-05-10
Hello world,
This is great, I mean Ubuntu 8.04 Hardy. I am now shifting from windows to linux, although had dual boot from Ubuntu version 4. Anyways I have a question which I was unable to find in search engine or to figure out myself:

I have UFW installed on my Hardy, and when I enter sudo ufw enable it gives error:
- the first one was that /etc was world writable, so I changed the persmission to something like world readable, and this error has gone
- the second one is the / (the whole filesystem) is world writable. What is that???? Can't change permission for that, and ufw cannot give me its status, although I have enabled it to start at boot in fstab. Does anyone know how to fix that????
This bug was reported on launchpad, but it gives no solution at least for me ([https://bugs.launchpad.net/ubuntu/+bug/206030](https://bugs.launchpad.net/ubuntu/+bug/206030))
So ufw is starting at boot now, but as far as I can see still not working

Also, before I started researching on UFW, I was trying to use firestarter firewall. This thing started all right but I was unable to add any rules, because all the buttons were grey (non-clickable). I think firestarter is better, because I prefer gui to shell. On the web I have found a post, where a person was asking the same question, and the solution was to right click on those buttons. Well))))))))))) if this can be called solution))))This is not working for me.

Can someone explain what is going on??? Maybe I missing some packages, or maybe I need to disable something, which interferes with those above????((((((((((( Still lacking security on my Hardy

Thanks in advance

---

### Post by salvador_luna on 2008-05-12
I have the same problem with firestarter and, maybe, a plus: When i started firewall, it says that my network controller is not ready, but firestarter reports that is running. Every time i configure something, it says that the device is not ready :(. Also, like you, a cannot click on anything and, to get thing worse, i scanned mi laptop  and all my ports are open.

---

### Post by RRFarFar on 2008-05-12
Yes, that's the thing. Those firewalls seems to be unusable on my Hardy. This is really strange for some people it works flawlessly for other there are unresolved issues. Any help would be appreciated!

---

### Post by cdenley on 2008-05-12
I don't know about your firestarter problem, but I don't think there is a problem with ufw. It just requires the root filesystem to have more restrictive permissions. If "/" is world writable, local users can swap any directory on your root filesystem.

This should fix it.
```

sudo chown root:root /
sudo chmod 755 /

```

The bug you linked to related to the livecd for hardy beta, which apparently had a world-writable root filesystem.

---

### Post by RRFarFar on 2008-05-12
> **cdenley said:**
> I don't know about your firestarter problem, but I don't think there is a problem with ufw. It just requires the root filesystem to have more restrictive permissions. If "/" is world writable, local users can swap any directory on your root filesystem.

This should fix it.
```

sudo chown root:root /
sudo chmod 755 /

```

The bug you linked to related to the livecd for hardy beta, which apparently had a world-writable root filesystem.

THANKS FOR THAT)))UfW is now running, no error messages
It seems to that I will try to find a good tutorial for security in Hardy. I would prefer to use firestarter, but since it is not working I would use UFW.

---

### Post by cdenley on 2008-05-15
> This thing started all right but I was unable to add any rules, because all the buttons were grey (non-clickable)

[http://ubuntuforums.org/showthread.php?p=4964179#post4963516](http://ubuntuforums.org/showthread.php?p=4964179#post4963516)

You mean you were under the policy tab, and you can't click "Add Rule" until you select the listbox under "allow connections from host" or "allow service|Port|For"?

---

### Post by RRFarFar on 2008-05-15
yes))) I did that already.Thank you 
 I want to start Firestarter at startup. Do you think it is safe to give permission to other user, not just root. I hate when Firestarter asks me root password at boot((((

---

### Post by cdenley on 2008-05-15
Firestarter is an application which configures iptables, the actual firewall, which is always running and used by all firewall frontends. The rules are loaded as soon as your computer starts, so there is no need for running the firestarter frontend at startup. Letting a non-root user configure firestarter (if it is even possible) or allowing "sudo firestarter" without a password could be a security problem.

---


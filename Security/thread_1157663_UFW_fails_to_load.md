---
title: "UFW fails to load"
date: 2009-05-12
forum: Security
---

### Post by kewl_123 on 2009-05-12
Hi,
      I had enabled UFW and did "default deny". I also use firestarter.
But since yesterday, I see the message while booting that either UFW or firestarte failed to load.It passes quickly so I cant see properly.
I saw the status of UFW it says not loaded.On firestarter it says firewall active.
I did sudo ufw enable and restarted twice but it still shows me status not loaded on command line.
As Ubuntu doesnt have any open ports, would it be ok to surf with firewall not active?
Can anyone please help?
Thank you.

---

### Post by lovinglinux on 2009-05-13
Why are you using UFW and Firestarter at the same time? They both do the same thing and one will override the other settings. I would remove Firestarter completely and keep only UFW.

> **kewl_123 said:**
> As Ubuntu doesnt have any open ports, would it be ok to surf with firewall not active?

Short answer: yes.

Long answer: [http://ubuntuforums.org/showpost.php?p=7255975&postcount=5](http://ubuntuforums.org/showpost.php?p=7255975&postcount=5)

---

### Post by kewl_123 on 2009-05-13
> **lovinglinux said:**
> Why are you using UFW and Firestarter at the same time? They both do the same thing and one will override the other settings. I would remove Firestarter completely and keep only UFW.


From what I know, Firestarter is a GUI for UFW.
Am I mistaken?

And now, "sudo ufw status" shows not loaded before connecting to net and loaded after connecting.

---

### Post by lovinglinux on 2009-05-13
> **kewl_123 said:**
> From what I know, Firestarter is a GUI for UFW.

No. Firestarter and UFW are just firewall managers, which means they are tools that allows to create rules for iptables (the real firewall). Firestater is also a GUI, while UFW needs GUFW to be used graphically.

---

### Post by kewl_123 on 2009-05-13
Thanks.
Completely removed Firestarter and restarted and UFW is loaded now.

In Firestarter, I had done something in Preferences at ICPM filtering, that wont even let me ping. How can I do that in UFW?

---

### Post by lovinglinux on 2009-05-13
> **kewl_123 said:**
> Thanks.
Completely removed Firestarter and restarted and UFW is loaded now.

In Firestarter, I had done something in Preferences at ICPM filtering, that wont even let me ping. How can I do that in UFW?

[http://ubuntuforums.org/showthread.php?t=773485](http://ubuntuforums.org/showthread.php?t=773485)

---

### Post by bodhi.zazen on 2009-05-13
If you want a gui front end for ufw, try gufw, it is in the repos.

---

### Post by automaton26 on 2009-05-24
Forget firestarter or guarddog, and just use gufw.

Although for me, ufw still fails during boot, 30% of the time, and I have to restart networking as soon as login has finished, with :

```
sudo /etc/init.d/networking restart
```

I can't find any way of getting the "real" boot log messages - but ufw seems to be failing because something is locked.

---


---
title: "firestarter does - gufw does not - how do I?"
date: 2012-02-16
forum: Security
---

### Post by mbuell on 2012-02-16
So, I have been using firestarter for the past 3 years - I've even dropped other distros because it wasn't in the repositories. Today I discover that firestarter is not approved of in ubuntu-land, and ufw/gufw is the approved way to go. 

Ok, I say - so what is the difference? Am I getting anything from Firestarter that gufw does not deliver? The answer is yes. In the Firestarter gui I can see what devices are attached to my server. Gufw does not do that. Also - and this may be a bit nit-picky, but here it is - in Firestarter it is dead-simple clear whether or not you have the ruleset applied and active. In Gufw, you have an "enable" check box - but it is not graphically transparent that the ruleset is up and functioning. 

So, if I uninstall Firestarter, how can I tell what machines on my lan are attached to the server - or, for that matter, what active connections I have from anywhere? 

The implied 2nd question - about whether it is running or not - I will leave out of this thread. I do not like the manner in which Gufw manages that information in their interface - but I can figure it out. I think. 

So the important question, for the moment, is how do I tell who/what is attached?

---

### Post by uRock on 2012-02-16
> **mbuell said:**
> So the important question, for the moment, is how do I tell who/what is attached?

Look at your logs. I don't know why one would need to watch active connections, but if that is wanted, then there is EtherApe and Wireshark. Both give more details than the small output of Firestarter's.

I have no need to see connections as they are happening, but all incoming connections are logged. Firestarter is not discouraged because of its quality nor functionality, but because it hasn't been maintained in years. UFW and GUFW have been receiving patches.

---

### Post by OpSecShellshock on 2012-02-17
Another thing to consider is that even when Firestarter was being maintained, it was never intended to have its interface open and running persistently. Having graphical applications with elevated privileges constantly running is not good practice, and I believe that Firestarter's documentation said not to do it.

---

### Post by Dangertux on 2012-02-17
> **mbuell said:**
> So, I have been using firestarter for the past 3 years - I've even dropped other distros because it wasn't in the repositories. Today I discover that firestarter is not approved of in ubuntu-land, and ufw/gufw is the approved way to go. 

Ok, I say - so what is the difference? Am I getting anything from Firestarter that gufw does not deliver? The answer is yes. In the Firestarter gui I can see what devices are attached to my server. Gufw does not do that. Also - and this may be a bit nit-picky, but here it is - in Firestarter it is dead-simple clear whether or not you have the ruleset applied and active. In Gufw, you have an "enable" check box - but it is not graphically transparent that the ruleset is up and functioning. 

So, if I uninstall Firestarter, how can I tell what machines on my lan are attached to the server - or, for that matter, what active connections I have from anywhere? 

The implied 2nd question - about whether it is running or not - I will leave out of this thread. I do not like the manner in which Gufw manages that information in their interface - but I can figure it out. I think. 

So the important question, for the moment, is how do I tell who/what is attached?

```

watch netstat -an

```

I believe is the command you're looking for.

---

### Post by mbuell on 2012-02-21
> **Dangertux said:**
> ```

watch netstat -an

```

I believe is the command you're looking for.


Yes - that does help! :)

---

### Post by mbuell on 2012-02-25
Thanks to all the responses - the news about Firestarter is good to know, as is the functionality mentioned for EtherApe and WireShark. 

The watch netstat is a good command line tool - and since this is a server I am trying to learn to control remotely - command line is good at this point. I've done my GUI apprenticeship in Linux, and now I am digging a bit deeper. 

Cheers!  :)

---

### Post by Dangertux on 2012-02-25
Incidentally if you want packet capture from the cli you can use tcpdump or tshark

---


---
title: "My Broadcomm Wifi Card adapter worked well in Juanty but has yet to work on Koala"
date: 2010-02-19
forum: The Cafe
---

### Post by mdrake36 on 2010-02-19
Would I really need to regress to an entirely different Distro to accommodate a single device?

---

### Post by Greenwidth on 2010-02-19
What card is it?

---

### Post by mdrake36 on 2010-02-19
I figured it out.
I just needed to install a network manager. A la carte "Wicd" worked
And update to the Device drivers that were listed in the Canonical List.
sweet

---

### Post by mdrake36 on 2010-02-19
[Greenwidth]("http://ubuntuforums.org/member.php?u=628497") thank you for your speedy response. Do you still want a model number?

---

### Post by Psumi on 2010-02-19
> **mdrake36 said:**
> [Greenwidth]("http://ubuntuforums.org/member.php?u=628497") thank you for your speedy response. Do you still want a model number?

It would be nice to know, since people could then put it on the ubuntu help wiki. Or, if you want to, you can register on UbuntuHCL and submit it. ubuntuHCL is linked in my sig.

---

### Post by Woolio1 on 2010-02-19
Normally, Broadcomm Wireless is a bit faulty in Karmic. To remedy this, open your terminal and type

```
 sudo apt-get update  
```

And them ```
 sudo apt-get --reinstall install bcmwl-kernel-source 
```

That's what I did, and it seems to work. 

Henry Ericson

---

### Post by MasterNetra on 2010-02-19
> **Woolio1 said:**
> Normally, Broadcomm Wireless is a bit faulty in Karmic. To remedy this, open your terminal and type

```
 sudo apt-get update  
```

And them ```
 sudo apt-get --reinstall install bcmwl-kernel-source 
```

That's what I did, and it seems to work. 

Henry Ericson

So thats why I end up having to install/re-install a wireless driver... Gonna load up LiveCD and see if that  works.

---

### Post by MasterNetra on 2010-02-19
Didn't work for me.

---

### Post by Dropbear on 2010-02-19
I have the bcm4311 and find that ndiswrapper gives flawless performance.
This is on karmic.

---


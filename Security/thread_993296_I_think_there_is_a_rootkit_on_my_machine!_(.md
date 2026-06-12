---
title: "I think there is a rootkit on my machine! :("
date: 2008-11-25
forum: Security
---

### Post by mehrdadm on 2008-11-25
I was get some problems on my system, as i said [here]("http://ubuntuforums.org/showthread.php?p=6250505") before, and i was think of a netwotk-manager problem!

here it is:
> Hi there,
I was upgraded My Kubuntu 8.04 (with mixed KDE 4.1.2) to Kubuntu 8.10, 2 days ago!

yesterday, wireless connection to my ADSL/Access Point dropped periodic and get connected again.
today my connection dropped and it cannot connect again! even Wired Connection! and my laptop cannot connect to network!
after that, i ask for it on Kubuntu IRC channel, and they say remove /etc/network/interface file, and restart system.
so, it connected again. but just for a while!
and after that I have to restart NetworkManager service to get connect again! and after a while my connection dropped and cannot connect until i restart NetworkManager service.

My system is Dell Inspiron 6400 Laptop.

Is there any idea?

but, after we checked some issues, i think it's another problem:

it is my iptables -L output, when i connected to network/internet:

[http://paste.gnudownload.org/show/2640](http://paste.gnudownload.org/show/2640)

but, I doesn't set anything for it!!!

and when i do "sudo iptables -F" and clear all rules, my connection gets dropped!!

and after reconnecting, the "iptables -L" output is the same as before!

help me please... :(

how can i check who changes iptables values!?!

---

### Post by Blairboy on 2008-11-25
If you think you have a rootkit, install and run rkhunter and see what it gives you.

---

### Post by mehrdadm on 2008-11-26
> **Blairboy said:**
> If you think you have a rootkit, install and run rkhunter and see what it gives you.
no, it seems, it's another problem.

---

### Post by cdenley on 2008-11-26
Your default policy for each chain is set to "DROP". If you flush the rules, then of course your internet won't work because it's dropping everything.

I think this will take care of it.
```

sudo ufw disable

```

If something is loading iptables rules when your network starts, check what scripts you have configured. Which frontends have you installed?
```

ls /etc/network/if-*up.d

```

---

### Post by mehrdadm on 2008-11-26
> **cdenley said:**
> Your default policy for each chain is set to "DROP". If you flush the rules, then of course your internet won't work because it's dropping everything.

I think this will take care of it.
```

sudo ufw disable

```

it was disabled before.

> **cdenley said:**
> 
If something is loading iptables rules when your network starts, check what scripts you have configured. Which frontends have you installed?
```

ls /etc/network/if-*up.d

```

finally i checked and saw FireStarter sets that rules :mad:

and i remove it, :D
but i still have problem on Wireless connection.

it seems, it's a bug of new Ubuntu/Kubuntu as i searched and found so many people with this issue! :(
but there isn't any response to this!

---

### Post by cdenley on 2008-11-26
> **mehrdadm said:**
> it was disabled before.



finally i checked and saw FireStarter sets that rules :mad:

and i remove it, :D
but i still have problem on Wireless connection.

it seems, it's a bug of new Ubuntu/Kubuntu as i searched and found so many people with this issue! :(
but there isn't any response to this!

Did you verify that the rules are no longer being loaded? You have to either purge (not remove) the package, or delete the script.

---

### Post by mehrdadm on 2008-11-27
> **cdenley said:**
> Did you verify that the rules are no longer being loaded? You have to either purge (not remove) the package, or delete the script.
I think i purge it!
and it's scripts no longer exists!
sometime i check my iptables, and it's clear!

---

### Post by cdenley on 2008-11-27
> **mehrdadm said:**
> I think i purge it!
and it's scripts no longer exists!
sometime i check my iptables, and it's clear!

Then you are probably having a network configuration problem. Are you using the NetworkManager applet to configure your network? Do you require a "manual configuration"? The only bug I've experienced with it is you cannot edit the automatically generated device profiles, even though they let you try. Try deleting the devices, then create new ones with the correct MAC address.
```

ifconfig -a|grep HWaddr

```

---


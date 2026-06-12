---
title: "iptables service in ubuntu 14.04"
date: 2017-03-10
forum: Security
---

### Post by pradeep8985 on 2017-03-10
How can i stop the iptables service in ubuntu 14.04.

Currently i can see the iptables -L output.  I have stopped the ufw service however i can still see that iptables -L is listing the rules. Which service is maintained by iptables?

i checked using "service iptables status/stop" but it's not there.

Please help!!!

---

### Post by ajgreeny on 2017-03-10
From man iptables:-
```
-F, --flush [chain]
              Flush  the selected chain (all the chains in the table if none is given).  This is equivalent to delet&#8208;
              ing all the rules one by one.

```
So try ```
sudo iptables -F
``` That should remove all rules you have applied so far, though I am not sure whether or not it actually stops iptables as a service.
What does ```
ps aux | grep iptables
``` show you as output?

---

### Post by slickymaster on 2017-03-10
*Thread moved to **Security**.*

---

### Post by Doug S on 2017-03-10
There is no such thing as an iptables service. The netfilter stuff (iptables) is built into the kernel, with a great many of the possible add on components available as modules (at least under the usual Ubuntu kernel configuration).
ufw is just a front end for iptables, and yes it will leave the iptable rules if you turn it off.  As mentioned by ajgreeny, you can flush the rule set and set default policies via:
```

sudo iptables -P INPUT ACCEPT
sudo iptables -F INPUT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F OUTPUT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F FORWARD
sudo iptables -t nat -F

```Or just re-boot after permanently disabling ufw (which I do not know how, because I do not use ufw).

---

### Post by SeijiSensei on 2017-03-10
> **Doug S said:**
> There is no such thing as an iptables service.
That's true for Ubuntu, but not for RedHat-flavored distributions like CentOS.  Those systems have an iptables service defined that runs at boot and can be managed with the "service" or "systemctl" commands depending on whether systemd is in use.

---

### Post by Doug S on 2017-03-10
> **SeijiSensei said:**
> That's true for Ubuntu, but not for RedHat-flavored distributions like CentOS.  Those systems have an iptables service defined that runs at boot and can be managed with the "service" or "systemctl" commands depending on whether systemd is in use.While my reply was about Ubuntu, I also did not know it was even possible for iptables to a be service external to the kernel. Thanks for correcting me. However, now I am curious as to how they do it, and I will have to go off and study.

---

### Post by SeijiSensei on 2017-03-10
It's just a bash script that runs a set of iptables rules.  By default it uses the ones created by iptables-save.

---

### Post by kevdog on 2017-03-12
> **SeijiSensei said:**
> That's true for Ubuntu, but not for RedHat-flavored distributions like CentOS.  Those systems have an iptables service defined that runs at boot and can be managed with the "service" or "systemctl" commands depending on whether systemd is in use.

So just like Doug, I didn't know this was true.  I looked a liitle bit more into this using the Arch Wiki as Arch also runs systemd: [https://wiki.archlinux.org/index.php/iptables](https://wiki.archlinux.org/index.php/iptables). Am I wrong however in thinking this "service" only loads the iptables with a saved configuration prior to network startup?  Meaning for example, if I didn't enable the iptables service and just managed loading and altering my rules through a bash script, that iptables and hence netfilter would work appropriately.  I'm not sure if it's wrong of write, but when I was learning (and am still learning iptable rulesets), I learned how to interact with iptables through a shell script.  I've always done it this way since, although I see the utility of the other method in terms of saving and loading via the service.

---

### Post by SeijiSensei on 2017-03-12
You would need to create a script with all the rules you want in the correct order and run it immediately after booting.  Now you should be able to use the iptables-save utility to write rules to the correct location for iptables scripts to load them.

I have some pretty complex rulesets running at client sites.  I wrote a script to generate and load those rules then runs iptables-save so the (CentOS) server knows where to find the next time the system boots.

---


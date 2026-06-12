---
title: "Upstart unbound"
date: 2014-08-08
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-08-08
After todays system upgrade I'm noticing that upstart is now unbound:

```
root@ubuntu:~# clean -u
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ifupdown iproute2 libcgmanager0 libjson0 upstart upstart-bin
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 3583 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```


None of these packages are essential and has also not a superior reversed essential dependency or a manual installed package. As I have heard systemd shall replace upstart in the future but have we now reached this point? Suspicious to me looks that also ifupdown is unbound and for now I'm better keeping these packages.

---

### Post by grahammechanical on 2014-08-08
On my system Synaptic marks upstart 1.13.1-0ubuntu2 with a grey exclamation mark icon ( ! ). The Help says that this means Installed (upgradeable) and it would be upgraded to the latest upstart 1.13.1-0ubuntu3. It also shows upstart-bin as not installed.

It is my guess that when the time comes removal of unnecessary packages will be done at the direction of the developers or, if you like, automatically. The code base will be cleaned up as a matter of course. After all, this change over is to take place without the user being aware of the change.

Regards

---

### Post by syntaxerror74 on 2014-08-11
> **grahammechanical said:**
> On my system Synaptic marks upstart 1.13.1-0ubuntu2 with a grey exclamation mark icon ( ! ). The Help says that this means Installed (upgradeable) and it would be upgraded to the latest upstart 1.13.1-0ubuntu3. It also shows upstart-bin as not installed.

What does

```
$ dpkg -l '*upstart*'
```

tell you?
Mind you, I never trust these strange markings in Synaptic, I'd only ever rely on dpkg's tags (rc, ii, un ... and so on). :)

---

### Post by grahammechanical on 2014-08-11
Upstarts status as listed in Synaptic is unchanged. Still mark with a grey exclamation mrk.

> graham@sdb8-Roll-Dev:~$ dpkg -l '*upstart*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libupstart1:am 1.13.1-0ubun amd64        Upstart Client Library
ii  upstart        1.13.1-0ubun amd64        event-based init daemon
un  upstart-compat <none>       <none>       (no description available)
un  upstart-job    <none>       <none>       (no description available)
un  upstart-monito <none>       <none>       (no description available)


Now, tell me what it all means . :)

Should I re-install Upstart?

Regards.

---

### Post by harry332 on 2014-08-12
Utopic, as it is now, does not necessarily need upstart anymore.

Systemd and sysvinit (with initscripts) do work perfectly fine.

So, if you have upgraded your setup up to date, and you have installed the package systemd-sysv, your setup is changed to use sysv instead of upstart.

This means you can remove upstart and upstart-bin (with libjson0). Also, you can remove the package systemd-shim (with cgmanager and libcgmanager0), which was a temporary hack.

For systemd I use the command  init=/lib/systemd/systemd in grub.

---

### Post by grahammechanical on 2014-08-12
Just to be clear. I am only providing information to help with the discussion.

I have been told that the change over from upstart to systemd will be transparent to the user. In other words, I, the user, should not need to do anything. I am not going to install anything to get my system running with systemd. I am not going to remove anything, either. I will run Update Manager daily and let things take their course. Which is the position that most ordinary users are in.

Unity8+mir on phones and tablets uses Upstart, as I understand it. And Ubuntu-Desktop-Next is the beginning of the converged code base. So, this uneducated person thinks that Upstart code will still be around even on the desktop until phablet switches over to systemd.

Regards.

---

### Post by Elfy on 2014-08-12
> **grahammechanical said:**
> Upstarts status as listed in Synaptic is unchanged. Still mark with a grey exclamation mrk.



Now, tell me what it all means . :)

Should I re-install Upstart?

Regards.

Not sure why it's marked with an exclamation mark, if it was me I'd probably do that.

FTR dpkg -l for upstart here gives exactly the same results as you've got.

---

### Post by syntaxerror74 on 2014-08-12
> **grahammechanical said:**
> 
Now, tell me what it all means . :)

Should I re-install Upstart?

No, there is no need:
> Utopic, as it is now, does not necessarily need upstart anymore.

I actually only asked you to show dpkg output to make sure there is nothing *half-installed* in your system. And there isn't: 'ii' means cleanly installed, while 'un' means cleanly uninstalled.
The interesting part would commence if there were some "relics" left in with packages: not only does this mess up your system, but it may also get it totally confused in worst case.

But your output looks quite OK to me.

---

### Post by Sworddragon on 2014-08-16
I have now opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1357713](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1357713)

As stated the upstart change could maybe be correct but I'm more annoyed about that this change causes ifupdown to be unbound too.

---

### Post by zika on 2014-08-16
> **Sworddragon said:**
> I have now opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1357713](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1357713)
As stated the upstart change could maybe be correct but I'm more annoyed about that this change causes ifupdown to be unbound too.Why on Earth being unbound is a bug for ifupdown? Not to mention that it needs a serious upgrade/recoding. You can remove (for example) all kernels (just to mention most essential one) from any install as so on... ;) What package would You like it to be bound to?

---

### Post by Sworddragon on 2014-08-16
> **zika said:**
> Why on Earth being unbound is a bug for ifupdown?

If removing it would really cause the network to failure after a reboot then it should get propably an essential flag (except systemd should now provide its functionality).


> **zika said:**
> You can remove (for example) all kernels (just to mention most essential one) from any install as so on... ;)

[https://bugs.launchpad.net/apt-setup/+bug/1238415](https://bugs.launchpad.net/apt-setup/+bug/1238415)


> **zika said:**
> What package would You like it to be bound to?

ifupdown was bound to upstart so maybe systemd needs ifupdown in some way too. If systemd gets the default in the fututure and propably essential too it could solve the problem. But until this happens another solution is needed (like the example above).

---


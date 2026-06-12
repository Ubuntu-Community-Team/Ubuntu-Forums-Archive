---
title: "How to bork an Ubuntu install without really trying (or knowing"
date: 2014-02-14
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-02-14
Open Dash > Applications
Search browser
Right click on "Browser"
Click on uninstall, auth the removal

If you were to now log out/in or restart,  unity would be gone. Fixable but seems too easy to create this mess.
[https://bugs.launchpad.net/ubuntu/+source/libunity-webapps/+bug/1280337](https://bugs.launchpad.net/ubuntu/+source/libunity-webapps/+bug/1280337)

Also easy to do in software-center as it fails to list all packages to be removed
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1278869](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1278869)

---

### Post by cariboo on 2014-02-14
I just did a check in synaptic, and removing the browser app, removes some fairly important files, if you are running Unity.

---

### Post by ventrical on 2014-02-15
> **mc4man said:**
> Open Dash > Applications
Search browser
Right click on "Browser"
Click on uninstall, auth the removal

If you were to now log out/in or restart,  unity would be gone. Fixable but seems too easy to create this mess.
[https://bugs.launchpad.net/ubuntu/+source/libunity-webapps/+bug/1280337](https://bugs.launchpad.net/ubuntu/+source/libunity-webapps/+bug/1280337)

Also easy to do in software-center as it fails to list all packages to be removed
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1278869](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1278869)


 I 'mee tooed it :)

geesh .. what a wierd bug that is ..

---

### Post by ventrical on 2014-02-15
> **mc4man said:**
> Fixable but seems too easy to create this mess.


  I tried to recover:

```


sudo apt-get install ubuntu-dekstop

```

but can't get the Unity Panel to come up.

---

### Post by mc4man on 2014-02-15
> **ventrical said:**
> I tried to recover:

```


sudo apt-get install ubuntu-dekstop

```

but can't get the Unity Panel to come up.

The side effect of logging back in with no unity is that even after unity, ect are re-installed the unity plugin will be disabled in compiz. 
So you'd need to re-enable it by some means.
The easiest would be to open ccsm & re-enable there, then do a log out/in 
(how you affect a log out/in is debatable since the silly change of ctrl+alt+delete to 'open sys monitor, probably best to do a restart

---

### Post by ventrical on 2014-02-15
> **mc4man said:**
> The side effect of logging back in with no unity is that even after unity, ect are re-installed the unity plugin will be disabled in compiz. 
So you'd need to re-enable it by some means.
The easiest would be to open ccsm & re-enable there, then do a log out/in 
(how you affect a log out/in is debatable since the silly change of ctrl+alt+delete to 'open sys monitor, probably best to do a restart


+1 :)

  I'm so embarrassed :) lol

  I should know better...

---

### Post by ajgreeny on 2014-02-16
Seems like a very good reason to always use synaptic for package management, which is what I aways do; it is the first package I install in any new OS of the Ubuntu family and the one thing I find if hard to manage without.

---


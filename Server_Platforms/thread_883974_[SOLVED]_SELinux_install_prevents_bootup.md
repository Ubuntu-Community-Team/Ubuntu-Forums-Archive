---
title: "[SOLVED] SELinux install prevents bootup"
date: 2008-08-08
forum: Server Platforms
---

### Post by El Rogueo on 2008-08-08
I've been running a Hardy server for a while now, and I recently decided for security reasons to try out SELinux and see how it goes, but when I install it, on reboot I get an error that prevents me from booting up.

```
SELinux: Could not open policy file <= /etc/selinux/refpolicy/policy/policy.22: No such file or directory

SELinux policy load failed and enforcing mode requested, halting now
```

then it drops me to busybox, so I just shut it down since I never perform any operations through busybox so I don't know what to do.

I install with

```
sudo apt-get install selinux selinux-policy
```
but I get told that even though selinux-policy is recommended, I should explicitly call one of two files (I think the one I pick is selinux-refpolicy or something along those lines) and that selinux-policy itself has no installation candidate. So I install selinux with either of the two policy files, and then am told that I must reboot to enable it, which I do. Then I get stuck in busybox and usually end up reinstalling.

I've checked the googlenets, with little result, as most guides are of the "apt-get, configure and have fun" nature, with no troubleshooting included.

Any ideas?

---

### Post by TreeFinger on 2008-08-08
can you post your /etc/selinux/config file?

---

### Post by El Rogueo on 2008-08-08
I'm on a windows machine now, so how would I do that from busybox?

Or should I reinstall and post the default?

---

### Post by TreeFinger on 2008-08-08
First log into single user mode. I think you should be able to boot. I believe it is also called "restore mode" on grub screen.

Post your
```

cat /etc/selinux/config

```

then try..

I don't know man. I would try to remove, clean, and reinstall and see if that helps.

You can boot into single user mode, correct?

---

### Post by El Rogueo on 2008-08-08
booted into recovery mode, which at first appeared to bypass the problem (SELinux failed, and then boot continued), but then I got this hideous mass of red fatals.

holy crap it's a combo kill. Everything below the third segmentation fault is in red.

my last entry is:

```
* Starting web server apache2
Segmentation fault
Segmentation fault
Segmentation fault

                                                     [failSe
gmentation fault
/etc/rc2.d/S99rc.local: 1: /i/: not found
/etc/rc2.d/S99rc.local: 2: AHbn/:url:ubn[: not found
/etc/rc2.d/S99rc.local: 3: ecfutS.//s/tfnos: not found
/etc/rc2.d/S99rc.local: 3: t: not found
/etc/rc2.d/S99rc.local: 8: oei_: not found
/etc/rc2.d/S99rc.local: 9: Syntax error: ";" unexpected
```

then leaves me at a blinking red cursor. I have definitely not seen that before.

That was theoretically a normal boot, but I'll try it again and see if it goes farther if I tell it to just throw me a root shell

Edit: Ugh, kernel panic, that's not working so far.

---

### Post by El Rogueo on 2008-08-08
Just did cat /etc/selinux/config

returned the usual comments describiing command use and operation
actual code is

```

SELINUX=enforcing
SELINUXTYPE=refpolicy
SETLOCALDEFS=0

```

just looking at that I can see that SELINUXTYPE is incorrect, refpolicy is not a valid option (options are "refpolicy-targeted" and "refpolicy-strict", in addition to the custom policy "refpolicy-src")

Edit: changed to "refpolicy-strict"

going to try to test that now

---

### Post by TreeFinger on 2008-08-08
> **El Rogueo said:**
> Just did cat /etc/selinux/config

returned the usual comments describiing command use and operation
actual code is

```

SELINUX=enforcing
SELINUXTYPE=refpolicy
SETLOCALDEFS=0

```

just looking at that I can see that SELINUXTYPE is incorrect, refpolicy is not a valid option (options are "refpolicy-targeted" and "refpolicy-strict", in addition to the custom policy "refpolicy-src")

going to try to change that now

hopefully that fixes the problem.

---

### Post by El Rogueo on 2008-08-08
policy change also fails, since it still says /etc/selinux/_whateverpolicy doesn't exist on boot

Edit: funnily enough, /etc/selinux/refpolicy *does* exist, as does /etc/selinux/refpolicy/policy, as they are supposed to, but the folder is empty

in conclusion, I'm missing a file called policy.22, and don't know what to do about it, since I've reinstalled selinux several times, with the same result every time.

---

### Post by TreeFinger on 2008-08-08
> **El Rogueo said:**
> policy change also fails, since it still says /etc/selinux/_whateverpolicy doesn't exist on boot

Try commenting out the line
```

# SETLOCALDEFS=0

```

---

### Post by El Rogueo on 2008-08-08
kernel panic and segfaults *constantly* occur, booting up, shutting down, restarting, all out of nowhere.

I've no idea if it's related or not though, as they don't seem to be related directly to SELinux

---

### Post by TreeFinger on 2008-08-08
> **El Rogueo said:**
> kernel panic and segfaults *constantly* occur, booting up, shutting down, restarting, all out of nowhere.

I've no idea if it's related or not though, as they don't seem to be related directly to SELinux

:-k

---

### Post by El Rogueo on 2008-08-08
> **TreeFinger said:**
> Try commenting out the line
```

# SETLOCALDEFS=0

```

still returns the same error about being unable to load the policy :confused:

---

### Post by TreeFinger on 2008-08-08
> **El Rogueo said:**
> still returns the same error about being unable to load the policy :confused:

I would remove the package and see if it helps any

---

### Post by El Rogueo on 2008-08-08
> **TreeFinger said:**
> I would remove the package and see if it helps any

With the package removed, the system boots fine, but I'm still not sure what to do about the missing policy. I did a quick reinstall but the folder was still empty.

---

### Post by windependence on 2008-08-08
App Armor is Ubuntu's answer to SELinux. I don't see what you are trying to accomplish loading SELinux over AppArmor. If you are super paranoid about security, try OpenBSD. Seriously, it's damn near impenetrable.

-Tim

---

### Post by El Rogueo on 2008-08-08
> **windependence said:**
> App Armor is Ubuntu's answer to SELinux. I don't see what you are trying to accomplish loading SELinux over AppArmor. If you are super paranoid about security, try OpenBSD. Seriously, it's damn near impenetrable.

-Tim

will do
I just like ubuntu/debian's package managing system, that's why I stick with it :)

---


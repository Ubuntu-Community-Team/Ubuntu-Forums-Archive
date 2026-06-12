---
title: "Something new in Vivid"
date: 2014-10-29
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-10-29
I fired up a terminal this morning and saw this:

[[IMG]http://i.imgur.com/NENAvrhl.png[/IMG]](http://imgur.com/NENAvrh)

I'm not sure if I really like this yet.

---

### Post by sammiev on 2014-10-29
I see the same as above after todays updates. Will need a little time to check this out.

---

### Post by Cavsfan on 2014-10-29
I seen that too after today's updates.

---

### Post by ventrical on 2014-10-29
Nothing here. Must be fixed already ?

---

### Post by zika on 2014-10-29
Old stuff. very old. Make just one successful sudo command or do```
 touch ~/.sudo_as_admin_successful
```and it will disappear. Delete that file and it will be back again. Successful sudo command makes it again... ;) 
> **ventrical said:**
> Nothing here. Must be fixed already ?What is there to be &#8222;fixed&#8220;? Learn Your bash better, we old guys did... ;)

---

### Post by cariboo on 2014-10-29
> **zika said:**
> Old stuff. very old. Make just one successful sudo command or do```
 touch ~/.sudo_as_admin_successful
```and it will disappear. Delete that file and it will be back again. Successful sudo command makes it again... ;) 
What is there to be „fixed“? Learn Your bash better, we old guys did... ;)

Thanks for that, I haven't had time to look into it yet, so your post was quick way to solve the un-problem. :)

---

### Post by zika on 2014-10-29
> **cariboo907 said:**
> Thanks for that, I haven't had time to look into it yet, so your post was quick way to solve the un-problem. :)That is a sort of atavism that will, as earlier, disappear soon, I'm sure.

---

### Post by sammiev on 2014-10-29
Thanks zika

---

### Post by mc4man on 2014-10-29
May be "Old Stuff" but I can't recollect ever seeing ( or remember ever seeing) the hint or hidden file
Added specifically in last bash update - 
> bash (4.3-11ubuntu2) vivid; urgency=medium

  * debian/etc.bash.bashrc: print a hint how to get root access if user
    is in sudo group (lp: #1358827)


---

### Post by cariboo on 2014-10-29
> **mc4man said:**
> May be "Old Stuff" but I can't recollect ever seeing ( or remember ever seeing) the hint or hidden file
Added specifically in last bash update -

What zika posted is in /etc/bash.bashrc:

```
# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *|*\ sudo\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
```

---

### Post by mc4man on 2014-10-29
[QUOTE=cariboo907;13155527]What zika posted is in /etc/bash.bashrc:
...
I get it now - it was previously in there but set for admin group so the hint didn't show since the switch to sudo group in 12.04

---

### Post by zika on 2014-10-30
> **cariboo907 said:**
> What zika posted is in /etc/bash.bashrc:

```
# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *|*\ sudo\ *)
    if [ -x /usr/bin/sudo ]; then
    cat <<-EOF
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.
```Yeap.> **zika said:**
> That is a sort of atavism that will, as earlier, disappear soon, I'm sure.Usually it did not (re)surface in Ubuntu proper.

---

### Post by ventrical on 2014-10-30
> **zika said:**
> Old stuff. very old. Make just one successful sudo command or do```
 touch ~/.sudo_as_admin_successful
```and it will disappear. Delete that file and it will be back again. Successful sudo command makes it again... ;) 
What is there to be „fixed“? Learn Your bash better, we old guys did... ;)

As I said .. there was nothing here.

> 
Learn Your bash better, we old guys did...


:)lol

---

### Post by Cavsfan on 2014-10-30
> **zika said:**
> Learn Your bash better, we old guys did... ;)

Ha! :lol: It was displaying that at the top of terminal when I first booted into Vivid today but after I got updates today including the 3.16.0-24-generic kernel I no longer have that.

[ATTACH=CONFIG]257611[/ATTACH]

---

### Post by zika on 2014-10-30
> **Cavsfan said:**
> Ha! :lol: It was displaying that at the top of terminal when I first booted into Vivid today but after I got updates today including the 3.16.0-24-generic kernel I no longer have that.

[ATTACH=CONFIG]257611[/ATTACH]Did You update/upgrade from CLI or GUI? If You did from CLI You've issued sudo-command and, hence, see above... ;) If not then, as so many times before, mainly this early in U+1, bash had that atavism removed, for Ubuntu proper way... ;)

---

### Post by ventrical on 2014-10-30
> **Cavsfan said:**
> Ha! :lol: It was displaying that at the top of terminal when I first booted into Vivid today but after I got updates today including the 3.16.0-24-generic kernel I no longer have that.

[ATTACH=CONFIG]257611[/ATTACH]

I got it now too.  :)

Must be slow updates.. :)

---

### Post by Cavsfan on 2014-10-30
> **zika said:**
> Did You update/upgrade from CLI or GUI? If You did from CLI You've issued sudo-command and, hence, see above... ;) If not then, as so many times before, mainly this early in U+1, bash had that atavism removed, for Ubuntu proper way... ;)

I always use CLI. I don't touch the Update-Mangler nor do I get my updates through SPM and I'll take my chances. ;)

> **ventrical said:**
> I got it now too.  :)

Must be slow updates.. :)

Guess so. Good deal! :)

---

### Post by zika on 2014-10-30
> **Cavsfan said:**
> I always use CLI. > **zika said:**
> Make just one successful sudo command and it will disappear.Full circle... ;) Ready for next round? ;)

---

### Post by Cavsfan on 2014-11-01
I'm pretty sure it was this way for a couple of days at least and I got updates via CLI.

---


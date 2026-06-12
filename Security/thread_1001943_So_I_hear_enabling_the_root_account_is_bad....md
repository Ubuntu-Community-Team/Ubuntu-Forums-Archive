---
title: "So I hear enabling the root account is bad...?"
date: 2008-12-04
forum: Security
---

### Post by SterLo on 2008-12-04
I recently ran into a situation that presented me with some trouble and I was wondering if I could get some opinions on what to do.

I had Ubuntu 8.0.4 and decided to upgrade to 8.1.0

The upgrade failed towards the end for whatever reason.
It said it was going to try to restore a backup - which it did not.
I rebooted to let the file system check take place.
The file system check failed.
It then said that I needed to run the FSCK manually and to do that I needed to mount the file system in read only mode and then run a maintenance terminal.

The mount was already in read-only, so it asked me for the root password.

Well the root password was never set. So I thought: "I'll just hit enter"
No that didnt' work.
I was unable to login to root...and I needed to in order to do ANYTHING.
Maybe I just didn't know some of the tricks I needed to...
So was there a trick I should have tried?

What I ended up doing was using a Live CD to do the manual FSCK and I was on my way to recovery...but still.

What if I didn't have the Live CD?
What if I was in the remote wilderness?
What if I was an elf with one laptop?
Why should we keep elves down?!

I have enabled the root account now...and given it a password.
I am not sure of the evilness this will create but from what just happened it seems like it's needed.

Anyone have a solution?

---

### Post by The Cog on 2008-12-04
If you boot into recovery mode (it's in the GRUB menu), then it drops you into a root login console automatically. Try it.

---

### Post by SterLo on 2008-12-04
> **The Cog said:**
> If you boot into recovery mode (it's in the GRUB menu), then it drops you into a root login console automatically. Try it.

Damn you.
I didn't think about that.
Thanks!

:p

---

### Post by unutbu on 2008-12-04
```
sudo -i
```
will give you a root shell.

The reason why giving root a password is discouraged, is because there are people/scripts out there that try to break into machines by guessing root passwords. If you do not have a root password, it is impossible to break in this way. 

If you disable the root password, the hacker might have to guess both your username and your password. 

On the other hand, there are all sorts of other ways that a machine can be compromised without having to guess either a root or a user password, so really this risk (in my inexpert opinion) is relatively minor compared to other security risks as long as your root password is sufficiently random. (Many other Linux distros enable a root password and are not considered significantly less secure than Ubuntu).

Nevertheless, since "sudo -i" does what you need, you may want to disable the root password.

---

### Post by brandon88tube on 2008-12-04
Having the root account enabled isn't horrible, just don't go and login with it every time to do stuff unless its necessary. In most cases sudo is sufficient so that is why its recommended.

---

### Post by bodhi.zazen on 2008-12-04
The main reason(s) we discourage setting a root password are :

[list=number][*]Ubuntu uses sudo.


[*]As unutbu pointed out, there is a minor enhancement in security. You might not think it so minor if you install openssh-server, leave the default settings, and watch the logs for attempts to log in as root on port 22 (think Christmas tree here).

[img]http://tbn3.google.com/images?q=tbn:zWbTVOZnq3tSLM:http://www.recyclethis.co.uk/wp-content/uploads/2007/12/christmas_tree_lights.jpg[/img]

[*]Setting a root password is unnecessary 99.9% of the time. If you prefer to use su - , set an alias, lol.


[*]Setting a root password can cause system breakage (search launchpad).


[*]Setting a root password disables booting to recovery mode without a password, recovery tool or security flaw ?


[*]And most important we have a lot of new users here. As staff I feel some (dare I say ethical) responsibility to teach "proper" system administration. For some reason it seems as if setting a root password or using gksu (kdesu) is the "solution" to permissions problems without an attempt to teach new users things like permissions and security.[/list]

The last point is most concerning. I would ask, please do not use setting a root password, gksu, or sudo -i to avoid teaching permissions and security.

When I see these threads I get the feeling that the "problem" is not with setting a root password, but setting a root password (or using gksu or sudo -i for that matter) at times is "abused" in that we use them as a shortcut, without teaching how Linux permissions work and why they are set. 

**IMO, Permissions == Security** and, IMO we should take care to teach people how to use these tools.

So please take the time to teach, teach permissions, give links

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

/end rant :twisted:

---

### Post by SterLo on 2008-12-04
> **unutbu said:**
> ```
sudo -i
```
will give you a root shell.

The reason why giving root a password is discouraged, is because there are people/scripts out there that try to break into machines by guessing root passwords. If you do not have a root password, it is impossible to break in this way. 

If you disable the root password, the hacker might have to guess both your username and your password. 

On the other hand, there are all sorts of other ways that a machine can be compromised without having to guess either a root or a user password, so really this risk (in my inexpert opinion) is relatively minor compared to other security risks as long as your root password is sufficiently random. (Many other Linux distros enable a root password and are not considered significantly less secure than Ubuntu).

Nevertheless, since "sudo -i" does what you need, you may want to disable the root password.

Generally I do "sudo bash" and if I need the next level up I do "su -" but since the account is disabled on this machine, that's pointless.

But "sudo bash" has always done what I needed.

---

### Post by unutbu on 2008-12-04
SterLo, the best advice I can give is: "Listen to bodhi.zazen". He knows a lot more about security than I do. (See for example, [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)).

If you insist on using a root shell, however, here is why "sudo -i" might be better than "sudo bash" or "sudo -" in some situations:
[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by bodhi.zazen on 2008-12-04
> **unutbu said:**
> SterLo, the best advice I can give is: "Listen to bodhi.zazen". He knows a lot more about security than I do. (See for example, [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)).

If you insist on using a root shell, however, here is why "sudo -i" might be better than "sudo bash" or "sudo -" in some situations:
[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

:redface:

I would say, be open to learning new things rather then becoming set in your ways. Times change and just because "it works" does not mean "It is best".

---

### Post by Vantrax on 2008-12-04
You could also fix the problem in single user mode if you did not have a liveCD handy.

You would just need to edit grub during the boot to add the option SINGLE to the end of your main boot string

IE

```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=42e2fa49-feeb-4c8f-8dc4-1d94ab9dcffc ro quiet splash **SINGLE**
initrd		/boot/initrd.img-2.6.24-22-generic
quiet
```

---

### Post by norman_069 on 2008-12-04
so i have been reading all this stuff about not having a root password and i am starting to agree but if i have already set up a password how do i delete it.

Thanks

---

### Post by unutbu on 2008-12-04
```

man passwd  # to read about the --delete option
sudo passwd --delete root   # this deletes the root password
```

---

### Post by norman_069 on 2008-12-04
Thanks

---

### Post by jflaker on 2008-12-04
logging in as root or yourself?

As yourself:
You can park the Lamborghini, roll up the windows and lock the doors and activate the antitheft system.....it can still be stolen BUT

As root:
The doors are unlocked and wide open, the windows are down and the motor is running with the keys in the ignition.

What does it mean....it means that as root, you can do anything and in a blink of an eye can kill your OS with an errant command or mouse click......

---


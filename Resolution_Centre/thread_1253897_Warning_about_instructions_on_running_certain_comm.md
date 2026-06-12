---
title: "Warning about instructions on running certain commands as real root"
date: 2009-08-30
forum: Resolution Centre
---

### Post by samborambo on 2009-08-30
[QUOTE=cariboo907][QUOTE=samborambo][QUOTE=cariboo907]Dear samborambo,

You have received a warning at Ubuntu Forums.

Reason:
-------
Root password howto

It is against forum policy to instruct anyone how to create a root password. See this [sticky]("http://ubuntuforums.org/showthread.php?t=716201").
-------

Original Post:
[post]7628923[/post]
> vikjon0, run the command as real root, not just sudo.

```
# su
Password:
```

Enter the root password. if you haven't set the root password yet, set it with:

```
# sudo passwd
```

Warnings serve as a reminder to you of the forum's rules, which you are expected to understand and follow.

All the best,
Ubuntu Forums[/QUOTE]

That sticky you refer to is for tutorials on GRAPHICAL root logins. There are valid reasons for executing certain commands as real root, not just sudo.

If the user does not create a root password, how are they expected to log in to the recovery console?

Please learn about forum rules before trying to enforce them.

The specific command that the thread starter was trying to execute (echo "10de 0aa2" > /sys/bus/pci/drivers/nForce2_smbus/new_id) could not be done with sudo. My answer was correct. Please reinstate my original post to the thread.

Sam Hadley-Jones.[/QUOTE]


Unfortunately it is you that is misreading the sticky. If you feel the warning was unfair, please start a thread in the[Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123")[/QUOTE]

I've read the sticky, thoroughly. The staff member who jailed my post and warned me hasn't offered any further rationale to his decision regarding the points I have raised.

Sam Hadley-Jones.

---

### Post by bodhi.zazen on 2009-08-30
First let me indulge with a few (small) technical points.

First you are incorrect, you do NOT need to set a root password to access the recovery mode.

Second we do support setting a root password when it is necessary. As you suggest, it is at times necessary. These times are rare.

If it is not necessary, we prefer you to use 

```
sudo -i
```

If you are going to instruct people to set a root password please at least:

1. Caution them about the risks of doing so.

2. Also include information on how to restore the defaults once the task at hand or current problem is solved.

/end indulgence

In response then to your question:

1. No the policy does not apply to graphical logins only.

2. If you give this advice (how to set a root password) please also take the time to educate (see comments above).

3. Please set a root password only when there is no viable alternate (sudo -i or booting to recovery mode).

4. Please include information on how to restore the defaults.

5. Please do not use setting a root password in place of teaching "proper" sys admin such as permissions.

A warning serves as a polite reminder to you about these issues and I prefer to educate you as well. Now you may run your system the way you wish, but please be mindful of the information you post on these forums.

A warning does not affect your account or standing on these forums, and thus I do not believe there is anything further that needs to be done here.

---


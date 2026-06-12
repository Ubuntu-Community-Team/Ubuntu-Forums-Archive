---
title: "Making num lock turn off and stay off before login"
date: 2018-03-23
forum: Ubuntu Development Version
---

### Post by ka1ssr on 2018-03-23
Hello!

I’ve been trying out the daily builds of Xubuntu for a couple of weeks now. I’ve noticed that the num lock on my Acer ao532h netbook turns on just before the login prompt appears (I want it off). I’ve tried various settings and while I’ve managed to get the num lock to stay off once I’ve logged in, I can’t disable it before logging in. Like I said before, I’ve just noticed this happening. I’m currently using Artful, which doesn’t exhibit this behavior. Is this a regression I should report (and if so, what package do I report it against) or is this simply a case of “user error” and what would the fix be? Is there a global setting for this?

Thanks for your time.

---

### Post by Frogs Hair on 2018-03-23
Moved to* Ubuntu Development Version*.

---

### Post by kerry_s on 2018-03-24
does your bios have a setting for number lock? is it enabled?

---

### Post by flocculant on 2018-03-24
> **ka1ssr said:**
> Hello!

I’ve been trying out the daily builds of Xubuntu for a couple of weeks now. I’ve noticed that the num lock on my Acer ao532h netbook turns on just before the login prompt appears (I want it off). I’ve tried various settings and while I’ve managed to get the num lock to stay off once I’ve logged in, I can’t disable it before logging in. Like I said before, I’ve just noticed this happening. I’m currently using Artful, which doesn’t exhibit this behavior. Is this a regression I should report (and if so, what package do I report it against) or is this simply a case of “user error” and what would the fix be? Is there a global setting for this?

Thanks for your time.

_Edit 2:_

Ok - speaking to the the dev - we're adding laptop-detect to the script that runs numlockx.

It would be useful if when it turns up you can test it for us.

Further - could you run this command in a terminal and post the result - it *should* be 0

```
laptop-detect; echo $?;
```

_Original post:_

That'll be because we added numlockx to the seed - [s]please open a terminal and 

```
ubuntu-bug xubuntu-default-settings
```

we'll see that bug then.

After you've done that edit [/s]

You can edit this file to turn numlock off
```
/usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
```

Change it to =off

_Edit:_

obviously you could also remove it ...

---

### Post by flocculant on 2018-03-24
> **kerry_s said:**
> does your bios have a setting for number lock? is it enabled?

ftr - my machine has that - never worked in *buntu - ever.

Fast forward some years to when I saw [lpbug]1746556[/lpbug] which prompted me to talk to the Xubuntu team - and we added numlockx and the above lightdm file.

---

### Post by ka1ssr on 2018-03-24
Thank you, all, for the support. Laptop-support does indeed return 0.

I did some poking around on my own and changed XKBOPTIONS in /etc/default/keyboard from null to grp_led:num. However, I feel this just masked the symptom rather than fix the underlying problem, namely why num-lock was being turned on in the first place. I'm going to restore the file to its former glory and try out your suggestion 

I'd be happy to help test. Just say the word.

Thanks again for all your help.

---

### Post by flocculant on 2018-03-25
> **ka1ssr said:**
> ... namely why num-lock was being turned on in the first place. I'm going to restore the file to its former glory and try out your suggestion ...

My previous post is possibly confusing now - with the original in the middle and bits struck through - but numlock was on because we added numlockx and turned it on  ;)

---

### Post by flocculant on 2018-03-28
> **ka1ssr said:**
> ...

I'd be happy to help test. Just say the word....

If the word required is test - then test :)

Please undo what you did to disable numlockx so it's back as default, then update - you should get 18.04.5 for ```
dpkg -l xubuntu-default-settings
```

This should make it so that a laptop doesn't automatically get numlock=on

---

### Post by pqwoerituytrueiwoq on 2018-04-15
For those with a laptop that have a number key pad, you can edit
/etc/default/numlockx

Is there a built in way to have it apply after login?

---


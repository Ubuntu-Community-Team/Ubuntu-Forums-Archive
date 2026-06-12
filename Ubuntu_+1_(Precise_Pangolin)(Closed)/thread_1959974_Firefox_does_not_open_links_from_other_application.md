---
title: "Firefox does not open links from other applications"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fbicknel on 2012-04-16
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

Package: firefox                         
...
Version: 11.0+build1-0ubuntu4Take a link from some other app, such as (for example) Thunderbird.  Click... firefox opens, but it always goes to my home page, opening another window for FF if one is already open.

Tried:

reinstalling FF
moving my .mozilla directory out of the way, creating a new profile
installing Chrome

Chrome works as expected, opening the link.  Switch back to FF and it stops working again.

Any ideas?

Tried searching for this, but keywords like link and firefox generate too much noise.

thanks in advance

---

### Post by lovinglinux on 2012-04-16
Moved to U+1

---

### Post by lovinglinux on 2012-04-16
Does this happen with Thunderbird only or with other applications as well?

---

### Post by fbicknel on 2012-04-17
Happens on other applications as well.  For example, when trying to sync Tomboy notes, there's a button to push that opens a browser to log into Ubuntu One and start your sync.

I had to switch to Chrome to get that to work.  Otherwise, Firefox would open a new window with my home page in it.

---

### Post by lovinglinux on 2012-04-17
Try to reinstall xul-ext-ubufox.

```
sudo apt-get install --reinstall xul-ext-ubufox
```

If that doesn't help, try to disable *Ubuntu Firefox Modifications* extension. See if it makes any difference.

---

### Post by fbicknel on 2012-04-18
Tried each of those, first reinstalling xul-ext-ubfox, then disabling Ubuntu Firefox modifications.

I've also tried disabling all add-ons both extensions and plugins.  

None of these measures worked.

---

### Post by lovinglinux on 2012-04-19
> **fbicknel said:**
> Tried each of those, first reinstalling xul-ext-ubfox, then disabling Ubuntu Firefox modifications.

I've also tried disabling all add-ons both extensions and plugins.  

None of these measures worked.

Logout of your account, log in as Guest and report if the problem persists or not.

---

### Post by fbicknel on 2012-04-25
Sorry so long since I posted.

Yes, using the guest account works as it should.

What makes this feature work?

It seems it should be a FF issue, since it works fine in Chrome.  However, I have tried not only re-installing FF, but also moving my .mozilla directory and letting it create a new one.

---

### Post by lovinglinux on 2012-04-25
> **fbicknel said:**
> Sorry so long since I posted.

Yes, using the guest account works as it should.

What makes this feature work?

It seems it should be a FF issue, since it works fine in Chrome.  However, I have tried not only re-installing FF, but also moving my .mozilla directory and letting it create a new one.

It still doesn't work after re-installing and moving the .mozilla directory?

---

### Post by fbicknel on 2012-04-25
Suspend disbelief!  ^^

No, it still doesn't work.

My home directory was copied over from my 11.10 host.  It worked fine there.

Can't imagine what might change to make it malfunction with 12.04.

My wife's home directory was also copied from the same 11.10 host.  Hers behaves normally.

---

### Post by lovinglinux on 2012-04-25
I am not sure what exactly is happening, but it is probably some Gnome settings or conflict causing this issue, because a clean user account solves the problem and a clean Firefox profile doesn't. I don't think it is a Firefox fault.

If you don't mind losing personal configuration, you could delete gnome config files from your home.

---


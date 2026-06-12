---
title: "How to go to an untrusted site in Firefox?"
date: 2013-02-09
forum: Security
---

### Post by Paddy Landau on 2013-02-09
In the past, if I've gone to a secure site and the security certificate has been not-quite-right, Firefox has given me a warning but allowed me the choice to continue anyway.

If I know the certificate is valid (e.g. a trusted subdomain), I can choose — at my own risk, of course — to proceed.

However, I seem no longer to have the option to proceed.

See the screen-shot. As you can see, it is a subdomain of a site that I trust (in fact, its repository).
[attach]231180[/attach]

The second screen-shot shows Chromium, which does offer me the option to proceed.
[attach]231181[/attach]

So — how can I tell Firefox that I wish to proceed anyway?

---

### Post by OpSecShellshock on 2013-02-09
If you open a new tab and put in the address bar:

```
about:certerror
```

do you have the "I understand the risks" option? If so, you can probably click through to the exceptions dialog and put the site in manually. Well, hopefully.

---

### Post by vasa1 on 2013-02-09
This is what I see (with Firefox 19 (beta) installed directly from Mozilla):

---

### Post by ibjsb4 on 2013-02-09
FF 18 gets this

[ATTACH]231183[/ATTACH]

---

### Post by Paddy Landau on 2013-02-09
Thanks for your replies.

> **OpSecShellshock said:**
> … about:certerror … do you have the "I understand the risks" option?
Yes, I do.

I have tried as you described:

[LIST]
[*][FONT=Lucida Console]about:certerror[/FONT] > I understand the risks > Add Exception
[*]Paste the site's URL
[*]Get certificate > Permanently store this exception > Confirm Security Exception
[/LIST]
But, alas, when I go to the site again, I still get the error without the choice of continuing.

> **vasa1 said:**
> This is what I see (with Firefox 19 (beta) installed directly from Mozilla):
Yes, that is what I expected to see, but didn't. (I have Firefox version 18.)

 I shall use Chromium until Firefox 19 comes is released.

Thanks again.

---

### Post by Paddy Landau on 2013-02-09
> **ibjsb4 said:**
> FF 18 gets this

[ATTACH]231183[/ATTACH]
I missed your post.

Weird &#8212; why do you and I get different results, I wonder? That's what Chromium displays.

---

### Post by ibjsb4 on 2013-02-09
Im on a fresh (2 day old) install.  FF 18.0.2

May try FF safe mode

Don't know what else to tell ya

---

### Post by Paddy Landau on 2013-02-09
> **ibjsb4 said:**
> May try FF safe mode
Good idea, but unfortunately it didn't work. Thanks anyway.

---


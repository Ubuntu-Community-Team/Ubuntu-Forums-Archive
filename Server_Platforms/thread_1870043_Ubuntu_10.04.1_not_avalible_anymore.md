---
title: "Ubuntu 10.04.1 not avalible anymore?"
date: 2011-10-26
forum: Server Platforms
---

### Post by GremlinLord on 2011-10-26
Just tried to download the desktop iso for Ubuntu 10.04.1 but all I can get in 10.04.2. The raid card I have (adaptec 6405) isn't supported in 10.04.2. Any chance to get a working mirror for 10.04.1

---

### Post by arrrghhh on 2011-10-26
> **GremlinLord said:**
> Just tried to download the desktop iso for Ubuntu 10.04.1 but all I can get in 10.04.2. The raid card I have (adaptec 6405) isn't supported in 10.04.2. Any chance to get a working mirror for 10.04.1

I think they're up to .3...

Is the issue kernel-bound?  Why not just run the specific kernel you need...

That's really odd that .1 it works and .2 it doesn't.  I didn't think any serious changes happened between minor releases...

---

### Post by redmk2 on 2011-10-26
> **GremlinLord said:**
> Just tried to download the desktop iso for Ubuntu 10.04.1 but all I can get in 10.04.2. The raid card I have (adaptec 6405) isn't supported in 10.04.2. Any chance to get a working mirror for 10.04.1
It should be listed at the bottom of [**_[COLOR="Blue"]this[/COLOR]_**]("http://old-releases.ubuntu.com/releases/lucid/") page.

Edit:  Ubuntu maintains site for all old releases [**_[COLOR="Blue"]here[/COLOR]_**]("http://old-releases.ubuntu.com/releases/").

---

### Post by arrrghhh on 2011-10-26
> **redmk2 said:**
> It should be listed at the bottom of [**_[COLOR="Blue"]this[/COLOR]_**]("http://old-releases.ubuntu.com/releases/lucid/") page.

Edit:  Ubuntu maintains site for all old releases [**_[COLOR="Blue"]here[/COLOR]_**]("http://old-releases.ubuntu.com/releases/").

Nice!  I guess to the OP - I would still try to sort out the issue, because in 6 months time the new LTS release will be out - 12.04, and I don't know if Ubuntu officially supports old releases - 10.04 on server should be supported to April 2015, but AFAIK, that should only be for the newest version of 10.04.  Basically what I'm saying is 10.04.0 probably won't be supported like 10.04.3 is... I'm not positive how that works, but either way I would look into sorting out that issue sooner rather than later, or else you'll be out of luck when 10.04 goes EOL!

---

### Post by redmk2 on 2011-10-26
> **arrrghhh said:**
> Nice!  I guess to the OP - I would still try to sort out the issue,...
It appears that the issue has been sorted out.  To the OP:  [This]("http://ubuntuforums.org/showthread.php?t=1788356") seems to be the answer to using the the RAID card with later Ubuntu releases.

---

### Post by GremlinLord on 2011-10-27
That'll get me to 10.04.2. The issue is the aacraid drivers for the adaptec 6405  raid controllers weren't included in the kernel until 2.6.39. Adaptec themselves only provided a driver for kernel 2.6.32-24. The next LTS should have the updated kernel but I'll cross that bridge when I get there.

---

### Post by GremlinLord on 2011-10-27
> **redmk2 said:**
> It should be listed at the bottom of [**_[COLOR="Blue"]this[/COLOR]_**]("http://old-releases.ubuntu.com/releases/lucid/") page.

Edit:  Ubuntu maintains site for all old releases [**_[COLOR="Blue"]here[/COLOR]_**]("http://old-releases.ubuntu.com/releases/").

Those links download 10.04.2 not the version the link would have you believe.

---

### Post by darkod on 2011-10-27
> **GremlinLord said:**
> Those links download 10.04.2 not the version the link would have you believe.

Are you sure about that?

If you roll your mouse over the link for ubuntu-10.04.1-server-i386.iso for example, from the text appearing bottom left you can see it will search the 10.04.1 as it says.

And by clicking it I got a pop-up asking if I want to download the ubuntu-10.04.1-server-i386.iso file.

Looks like the links are OK, don't mind the title at the top of the page saying 10.04.2.

---

### Post by GremlinLord on 2011-10-27
I feel like a stooge. I was using the links at the top of the page, not the links at the bottom  ](*,).

---


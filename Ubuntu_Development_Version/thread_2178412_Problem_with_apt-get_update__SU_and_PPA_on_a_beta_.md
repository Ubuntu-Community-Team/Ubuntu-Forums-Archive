---
title: "Problem with apt-get update / SU and PPA on a beta release"
date: 2013-10-03
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2013-10-03
Hello there,

everything works as it should except for this "little" thing.

I need to fetch a package from the PPA repository (yes, it's lxkeymap where the bug-fixed version is still in staging and hasn't found its way after a year to the "official" reps) and I always get a 404 not found error.

I know why it happens, since Software Updater does nothing much different from apt-get update.

W: Failed to fetch 

[http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

This directory physically does not exist yet - I've checked it.
But again, I know the way how to solve the problem, and that's by pointing the updater to:
[http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/dists/saucy/main/binary-i386/Packages)

But how can I do that (if at all)

---

### Post by heir4c on 2013-10-03
So, you use 13.10.
Open "Software & Update" via de Dash and click on the second tab.
Below on the left you see a button with "Add" (I think, here is it in Dutch)
Click on it and Copy/Paste de link in the box 
```
http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/dists/saucy/main/binary-i386/Packages
```
Than click "Add Source" and do than a update.
Or change the link you already have.
Or you wait till the next update of 13.10. It's not yet released, so tomorrow it maybe changed again.
Succes!

---

### Post by syntaxerror74 on 2013-10-03
> **heir4c said:**
> 
Or change the link you already have.


YES! This was the right pointer. In Software Updater, this link can be edited. And then it works. Hooray!
Careful though, the fix you proposed will not work for Software Updater.
You would have to specify a way shorter URL:

```
http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu
```

The actual culprit for that though is aptitude with its non-ability to set 'daily' URLs.
I've run into this by typing

```

sudo add-apt-repository ppa:lubuntu-dev/staging

```

It would probably be no big deal to include a checking mechanism "Are we final?" and if not, we will just go looking on the 'lubuntu-daily' branch, adapt the URL accordingly for the Updater - and avoid running into 404s.

---

### Post by heir4c on 2013-10-03
Good that it works!
And ThanX for posting your way to solve the problem.

> It would probably be no big deal to include a checking mechanism "Are we final?" and if not, we will just go looking on the 'lubuntu-daily' branch, adapt the URL accordingly for the Updater - and avoid running into 404s. 
You will use a -dev packages and it's a ppa: So, I'm not a expert or developer, but that's logic, there are no stable or finished. 

One more question: Am I right you use 13.10?

---

### Post by sandyd on 2013-10-03
moved to Ubuntu+1

Please ask for help on unreleased versions of Ubuntu on the U+1 forums please.

Thanks!

---

### Post by deadflowr on 2013-10-03
For what it's worth, from what I see there is no saucy version for that PPA.
Hence the original errors.

The newest I see is quantal.

---

### Post by syntaxerror74 on 2013-10-03
> **heir4c said:**
> 
One more question: Am I right you use 13.10?

Absolutely! 13.10 beta 2 (final as it looks) to be exact.

And you might even know why not 13.04: ONLY 13.10 ships with Firefox, and I just wanted to start browsing without doing any install stuff first. Since there were too many things to setup first (e. g. this annoyance that vi/vim is never set to non-compatible mode by default, so you will produce ugly A B C D letters in insert mode. With vi, the most important thing to work ARE the cursor keys. LOL.)

---


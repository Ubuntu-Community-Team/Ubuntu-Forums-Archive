---
title: "No dist-upgrade for kernels on 17.04?"
date: 2017-03-08
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2017-03-08
I just jumped on the bandwagon a few days ago and today got the 4.10.0-11-generic kernel in updates today.

It updated several packages and then installed the new 4.10.0-11-generic kernel. It used to have those kernel packages held back for a dist-upgrade.

Is this new? Or is it because I changed my update aliases from apt-get to apt?

Just curious.

---

### Post by zika on 2017-03-08
```
linux-image-extra-4.10.0-11-generic/zesty,now 4.10.0-11.13 amd64
```That is the last installed. Is that what Your question was about?

---

### Post by Cavsfan on 2017-03-08
> linux-image-extra-4.10.0-11-generic/zesty,now 4.10.0-11.13 amd64

> **zika said:**
> ```
linux-image-extra-4.10.0-11-generic/zesty,now 4.10.0-11.13 amd64
```That is the last installed. Is that what Your question was about?

Yes it is. But, I was asking about how it does it. I wasn't required to do a dist-upgrade to install it. Which used to be the norm.

---

### Post by deadflowr on 2017-03-08
Perhaps to help alleviate the confusion, what command did you run?

If you ran *apt upgrade*, then you would have gotten the kernel upgrade, versus *apt-get upgrade* which would not.
*apt upgrade* will install new packages, but it does not remove packages if those older package need to be removed for a new package to be installed. 
(*apt full-upgrade* will install new packages but also remove packages if those new packages need the older package to be installed. > ftr)

And since kernels never remove older packages but rather install whole new packages unto themselves, *apt upgrade* installs those like normal.

(*apt-get upgrade* will never install a new package and only updates whatever already exists on the system.
(*apt-get dist-upgrade* will install new packages if the system update requires that))


If that make sense.
(Of course, making sense and what's really going on may not be the same thing, in this case...)

---

### Post by zika on 2017-03-08
> **deadflowr said:**
> And since kernels never remove older packages but rather install whole new packages unto themselves, *apt upgrade* installs those like normal.Yeap... ;)

---

### Post by Cavsfan on 2017-03-08
> **deadflowr said:**
> Perhaps to help alleviate the confusion, what command did you run?

If you ran *apt upgrade*, then you would have gotten the kernel upgrade, versus *apt-get upgrade* which would not

That would explain it then. My update alias used to look like this:

```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
```

And I changed it to this:

```
alias ud='sudo apt update && sudo apt upgrade && sudo apt autoclean'
```

Thank you!

---


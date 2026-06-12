---
title: "packages held back"
date: 2009-02-22
forum: The Cafe
---

### Post by gletob on 2009-02-22
What's with packages being held back?

---

### Post by Skripka on 2009-02-22
> **gletob said:**
> What's with packages being held back?

As in...?????  Or to put it in the words of Number 5 from Short Circuit:

 "Need More Input."

---

### Post by gletob on 2009-02-22
Like when you run sudo apt-get upgrade and it says packages held back:
Why does it do that?

---

### Post by FuturePilot on 2009-02-22
it's usually a dependency issue.

---

### Post by gletob on 2009-02-22
Oh sorry I don't have any being held back right now I was just wondering this happens.

---

### Post by Eclipse. on 2009-02-22
> **gletob said:**
> What's with packages being held back?

Wait a minute, your using Jaunty and you dont know that.

Sorry dont mean to be mean but if your asking  a question like this you really should stick to a stable release.

---

### Post by Tux Aubrey on 2009-02-23
Have you paid your account?  Certain packages will be held back if you don't keep making your regular payments to Canonical.  Eventually they will hold back something critical and your system will not boot.  You didn't believe all that "Free" stuff, did you?  That's why they say "Free as in beer" and wink (beer is NOT free, der).

Actually, it is probably because new dependencies are required and apt-get upgrade will only upgrade already installed packages, not install new ones.  Do:

```
sudo apt-get dist-upgrade
```

to get any held back packages.

You have my permission to use Jaunty if you want to - the usual warranty applies.

---


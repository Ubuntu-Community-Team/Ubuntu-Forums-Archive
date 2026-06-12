---
title: "Downgrading Back to 11.10 fully or Fix 12.04"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jaybutts on 2012-04-02
I decided to upgrade to 12.04 beta being a developer and a sys admin I thought there wasn't any problems I wouldn't be able to handle. The upgrade went smooth and everything was working great untill I had some dependency problems and ended up doing:

sudo aptitude upgrade --full-resolver

Without really paying attention to much to what it was doing because I thought I can just do an upgrade or something and get everything back like it is gentoo or some other distro. Id really just rather wait for the full release, I was viewing the ubuntu development cycle as if it was rolling or something and thats definitely not the case. Now I have programs missing including ubuntu software center lol

Can someone please advise me either how to fix this or how to completely downgrade my system  back to 11.10 if its possible. sed -i 's#precise#oneric#g' ???????

---

### Post by kansasnoob on 2012-04-02
You can't downgrade, but begin by trying:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

Next have a good look at your software sources.

---

### Post by jaybutts on 2012-04-02
ah okay thanks, looks like I got it fixed now, aptitude confuses me still, need to learn more about it

---

### Post by xebian on 2012-04-02
> **jaybutts said:**
> I decided to upgrade to 12.04 beta being a developer and a sys admin I thought there wasn't any problems I wouldn't be able to handle. The upgrade went smooth and everything was working great untill I had some dependency problems and ended up doing:

sudo aptitude upgrade --full-resolver

Without really paying attention to much to what it was doing because I thought I can just do an upgrade or something and get everything back like it is gentoo or some other distro. Id really just rather wait for the full release, I was viewing the ubuntu development cycle as if it was rolling or something and thats definitely not the case. Now I have programs missing including ubuntu software center lol

Can someone please advise me either how to fix this or how to completely downgrade my system  back to 11.10 if its possible. sed -i 's#precise#oneric#g' ???????

April 1 is past.  :lolflag:

Sorry, but we are mostly noobs here and can't help a 'developer and a sys admin'.

Cheers!!!

---

### Post by kansasnoob on 2012-04-02
> **xebian said:**
> April 1 is past.  :lolflag:

Sorry, but we are mostly noobs here and can't help a 'developer and a sys admin'.

Cheers!!!

I play at being a sys admin, but I'm also a noob, every day here is April fools day :lolflag:

If I knew what I was doing I'd get rich writing a book or something ............... that reminds me, I do have a book to write. The title will be; I married a mud wrestler. I'm kind of serious ;)

Maybe, health permitting, after 12.04.1 I'll truly take a year off and write that book. Hollywood would love my life's story :p

---


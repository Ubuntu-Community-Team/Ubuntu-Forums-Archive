---
title: "Checking for updates eats bandwidth.."
date: 2012-08-07
forum: The Cafe
---

### Post by Ravi5kumar on 2012-08-07
Why the hell the apt command:

```
sudo apt-get update
```

Always eats my precious bandwidth (20-25 MB):confused:. I am annoyed because whenever I check for updates or add a third party repository I have to type this command and it just eats:(...

---

### Post by vasa1 on 2012-08-07
> **Ravi5kumar said:**
> Why the hell the apt command:

```
sudo apt-get update
```

Always eats my precious bandwidth (20-25 MB):confused:. I am annoyed because whenever I check for updates or add a third party repository I have to type this command and it just eats:(...

Maybe you have too many sources? And you have ticked source code?

Go into update manager and maybe you can untick a lot of stuff?

---

### Post by PaulW2U on 2012-08-07
> **Ravi5kumar said:**
> Why the hell the apt command:

```
sudo apt-get update
```

Always eats my precious bandwidth (20-25 MB):confused:. I am annoyed because whenever I check for updates or add a third party repository I have to type this command and it just eats:(...

This has been raised by quite a few users elsewhere and has got worse with the release of Ubuntu 12.04. A bug report has been raised although I can't provide a link to it at present. You are not alone with your concerns. 

You might be able to reduce the download a little though. Do you have any repositories enabled that you don't really need such as Backports, Proposed Updates or Source Code? My download never goes above 17MB.

Edit: [https://bugs.launchpad.net/ubuntu/+bug/1001780](https://bugs.launchpad.net/ubuntu/+bug/1001780) is the bug report I was referring to. It's shown as fixed although I still feel a check for updates consumes far more bandwith than it used to.

---

### Post by elliotn on 2012-08-07
yeah 12.04 update its lots of bandwidth. I have no extra repo

---

### Post by mips on 2012-08-07
Yes it got worse with 12.04 and I suspect it's due to multi-arch where you now get i386 & AMD64 stuff.

Besides that we also need deb-deltas. If this does not happen soon in debian based distros I'm moving to Fedora that offers DeltaRPM. It's not rocket science.

Unfortunately bandwidth is not cheap in all countries including mine.

---

### Post by doorknob60 on 2012-08-07
Wow. Hate to say this, but glad I don't use Ubuntu, because we constantly go over the bandwidth cap here (it's 150 GB which is pretty generous, but we still go over. 5 family members...) Just to update the repos in Arch uses nowhere near that amount. Although keeping up to date packages probably eats up a lot in a rolling release though...whatever :P

---

### Post by mips on 2012-08-07
> **doorknob60 said:**
> Although keeping up to date packages probably eats up a lot in a rolling release though...whatever :P

And that is the only reason why I don't use Arch right now. It's still my favourite distro though.

---


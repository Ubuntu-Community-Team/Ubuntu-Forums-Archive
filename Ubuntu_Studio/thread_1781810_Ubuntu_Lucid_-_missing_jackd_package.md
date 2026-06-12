---
title: "Ubuntu Lucid - missing jackd package?"
date: 2011-06-14
forum: Ubuntu Studio
---

### Post by dewdrop_world on 2011-06-14
I cannot find the jackd package ANYWHERE for Lucid.

(Why Lucid, and why not Ubuntu Studio? Because my internet connection is dog slow and I already have the lucid iso at hand. This also means, "download natty and reinstall the OS" is not a realistic option at this time.)

I've tried different mirrors, plus the kxstudio ppa, nada.

```
apt-get install -s jackd
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package jackd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package jackd has no installation candidate
```

So... where do I get this puppy? No problem when I set up my first Ubuntu install, but now... it's gone.

Thanks,
James

---

### Post by dewdrop_world on 2011-06-14
Actually... hold that thought... it seems like adding the kxstudio ppa failed the first time.

Gotta run to something else now but will update later if the install is successful.

---

### Post by Flaggmann on 2011-06-14
It should show in synaptic package manager; it always has for me.


[http://www.jackaudio.org/download](http://www.jackaudio.org/download)

---

### Post by jejeman on 2011-06-14
No need to add kxstudio ppa for jackd just install it
```
sudo apt-get install jackd
```

---

### Post by dewdrop_world on 2011-06-16
> **jejeman said:**
> No need to add kxstudio ppa for jackd just install it
```
sudo apt-get install jackd
```

Thanks for the suggestion. However, the first post in this thread shows that I already executed that exact same command, and the result was an error message that the package "has no installation candidate."

Update tonight is, it still doesn't show in the synaptic gui but "apt-cache search jack" reveals it. :confused::confused::confused: Wee-yard. (Yes, I "reload"ed the package lists.)

Likewise, [http://www.jackaudio.org/download](http://www.jackaudio.org/download) says only:

JACK2: 
[LIST]
[*]**Binaries**: please use your distribution's package  manager (apt-get, yum, synaptic etc.)
[/LIST]
*But it ain't in the package manager in this install.*

In the meantime, jackd from the ppa whinges about libcelt0-0 not being found, but a download from packages.ubuntu.com seems to have solved that.

James

---

### Post by falkTX on 2011-06-21
you're missing the universe and multiverse repos.

since you already have some kxstudio ppas, a quick fix would be to install the kxstudio-repos package
```
sudo add-apt-repository ppa:kxstudio-team/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update
sudo apt-get install jackd

```

---


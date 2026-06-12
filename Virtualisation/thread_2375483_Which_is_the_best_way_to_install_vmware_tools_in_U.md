---
title: "Which is the best way to install vmware tools in Ubuntu 17.10 guest?"
date: 2017-10-24
forum: Virtualisation
---

### Post by hardhu on 2017-10-24
I know that there are two ways to install vmware tools in an Ubuntu 17.10 guest system:
a) using the Ubuhtu built-in packages: ```
sudo apt-get install open-vm-tools-desktop

```

b) using the installer provided by vmware player, as described here: [https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525")

Which is the best way? Or do both ways provide the same features?

---

### Post by crjackson on 2018-03-01
> **hardhu said:**
> I know that there are two ways to install vmware tools in an Ubuntu 17.10 guest system:
a) using the Ubuhtu built-in packages: ```
sudo apt-get install open-vm-tools-desktop

```

b) using the installer provided by vmware player, as described here: [https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525")

Which is the best way? Or do both ways provide the same features?

Wow, didn’t even think to check the repository for that.

I just installed the tools provided by VMware Fusion but it doesn’t resolve my screen display resolution problem (1920x1080 isn’t present) so I’m running at the wrong res...

I’ll check out the repository version tomorrow and report anything I find.

---

### Post by crjackson on 2018-03-02
Just a quick update...

After running the command

```

sudo apt-get install open-vm-tools-desktop
```

my resolutions is now fixed. This did the trick...

---


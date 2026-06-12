---
title: "Question"
date: 2022-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2022-06-28
Hi guys question for I'm running 20.04 on my system but I came across another older laptop thinking running 18.04 is the end of support 2025

---

### Post by Bashing-om on 2022-06-28
gordie692 --

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes;](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes;)
> 
The 'main' archive of Ubuntu 18.04 LTS will be supported for 5 years until April 2023. Ubuntu 18.04 LTS will be supported for 5 years for Ubuntu Desktop, Ubuntu Server, and Ubuntu Core. Ubuntu Studio 18.04 will be supported for 9 months. All other flavors will be supported for 3 years.



[INDENT]My bit to try and help
[/INDENT]

---

### Post by guiverc on 2022-06-28
On an installed 18.04 system, you can use

```
ubuntu-support-status
```

to see the actual results for your installed system.  Do note the `ubuntu-support-status` command doesn't exist on later systems, it's now `ubuntu-security-status` with differing output, but its got the same purpose.

An example output 

```
guiverc@t43-lubu:~$   ubuntu-support-status 

Support status summary of 't43-lubu':

You have 1332 packages (70.8%) supported until April 2023 (Canonical - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 549 packages (29.2%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
guiverc@t43-lubu:~$
```

Do note:  I don't have a *bionic* system running, so I just copy/pasted my example from [here]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7") , and your results will differ, but using that command will show results for your actual install :P  On my example, it was a Lubuntu system, thus the Lubuntu/LXDE packages are now all *unsupported*, but packages in common with Ubuntu Desktop still receive security patches etc.

---


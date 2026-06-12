---
title: "risk with automount as a root user"
date: 2011-06-20
forum: Security
---

### Post by ltoso on 2011-06-20
Hi,
i want to know the risk with auto mounting flash drive as a root user,
if for example there is a Usb Flash drive inserted into the system and we login into root unknowingly, and this flash drive contains an autorun script which calls a new script that can place viruses in your system, since you are in the root it will not even prompt for password and if the script is fast enough you will not even see it executing.
Now this is just a hypothetical situation, as i am new to ubuntu, can anybody tell me if this kind of thing is possible

Please recommend
ltoso

---

### Post by fballem on 2011-06-20
You cannot 'accidentally' log in as the root user in ubuntu. The root account in ubuntu is disabled - any commands that require root access are done through either sudo or gksudo - depending on whether graphical access is required or not.

Since you have to use either sudo or gksudo, you will certainly know that you have root access at that time and I assume that you will be cautious.

In other flavours of Linux - such as Fedora - the root account is not disabled, but again, you would have to log in as root, so again you would know that you are root and would be more careful than you otherwise might be.

I hope this helps,

---

### Post by ltoso on 2011-06-22
thanx @fballem

but i enabled my root account in ubuntu by using<snip>
then you can create a password for root and then login into root account using username root and password you just created, now my main question is if you are login as root and then you insert a usb drive, you know it gets mounted automatically, but does the autorun also works, cause if this is the case then there can be a virus in the autorun that can harm your system as when you are in root, it never asks for confirmation even in ubuntu.

please recommend

---

### Post by haqking on 2011-06-22
> **ltoso said:**
> thanx @fballem

but i enabled my root account in ubuntu by using "sudo passwd root"
then you can create a password for root and then login into root account using username root and password you just created, now my main question is if you are login as root and then you insert a usb drive, you know it gets mounted automatically, but does the autorun also works, cause if this is the case then there can be a virus in the autorun that can harm your system as when you are in root, it never asks for confirmation even in ubuntu.

please recommend

This forum abides to the Canonical security model and does not condone the enabling of the root user as i was informed the other day ;-)

best edit your post beofre youa re reported, they jump on it quick.

and if you had adhered to the model then this question would not be an issue ;-)

use sudo or gksduo ;-)

and viruses are not an issue like in Windows, though they do exist i think at last count there was about 1000 or so out there for *nix they certinaly are not prevolent

---

### Post by fballem on 2011-06-22
_Unless you absolutely have a compelling reason to do so_ (and I have never heard of one in three years of using Ubuntu) then I would recommend that you disable the root account and do not log in as root.

This goes double if you are new to Linux. The ubuntu security model has been setup to work in a specific way. I have not yet found anything that I need to do that I cannot do using sudo or gksudo.

You did ask for a recommendation, and that is my recommendation in the strongest possible terms. I am probably not the only one who will recommend that you disable the root account.

Hope this helps,

---

### Post by cariboo on 2011-06-22
We on the forums, have nothing against someone instructing how to enable the root account, we do ask that you also include a warning about the dangers of running as root.

Personally I've used Ubuntu since 2006, and have never found the need to enable the root account. When I've used other distros, that ask for a root password, I still find myself typing sudo when I want to do any administrative tasks, which gets a bit frustrating if sudo isn't enabled by default.

---

### Post by haqking on 2011-06-22
> **cariboo907 said:**
> We on the forums, have nothing against someone instructing how to enable the root account, we do ask that you also include a warning about the dangers of running as root.

Personally I've used Ubuntu since 2006, and have never found the need to enable the root account. When I've used other distros, that ask for a root password, I still find myself typing sudo when I want to do any administrative tasks, which gets a bit frustrating if sudo isn't enabled by default.

yes i mnsunderstood, i have read the roott sticky now and it is ok to post about enabling root as long as reasons for and against and warnings are addressed and how to disbale it once again.

noted ;-)

---

### Post by fballem on 2011-06-22
Itoso:

The concensus from the discussion here seems to be that we recommend that you disable the root account (which is the ubuntu default). You did say that you were new to ubuntu, but you did not say that you were new to Linux.

Having come from a Windows environment myself, it took me a little while to understand the ubuntu way of doing things. In Windows, users tend to run with administrative privileges, which in part explains why there are issues (viruses, trojans, and other nasty stuff). Initially I missed the convenience, but as time went on and I heard horror stories from my friends and clients who were running Windows, I realised that a little bit of inconvenience was a good thing.

I migrated my clients to ubuntu, and I have had very few issues. None of them run as the root user, and I will not enable the root account.

I hope that this discussion has provided some insight as to why the root account is not enabled in ubuntu.

Please let us know what your thoughts are or if we can help further,

---


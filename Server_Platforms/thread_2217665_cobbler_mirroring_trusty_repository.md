---
title: "cobbler mirroring trusty repository"
date: 2014-04-18
forum: Server Platforms
---

### Post by nagymatef on 2014-04-18
Hi!

I am trying to use cobbler for a small cluster of only 4-8 computers, however I wish to mirror the ubuntu repositroy locally on the cobbler server itself, as well as creating custom repos for drivers, 3rd party apps and what not. However, cobbler repo sync fails, due to gnupg checks. What I do is:

```
mnagy@server:~$ sudo cobbler repo add --name=local-trusty --breed=apt --arch=x86_64 --mirror=http://hu.archive.ubuntu.com/ubuntu/ --apt-components=main,restricted,universe,multiverse --apt-dists=trusty,trusty-updates,trusty-security
mnagy@server:~$ sudo cobbler reposync
task started: 2014-04-18_124416_reposync
task started (id=Reposync, time=Fri Apr 18 12:44:16 2014)
hello, reposync
run, reposync, run!
running: /usr/bin/debmirror --nocleanup --method=http --host=archive.ubuntu.com --root=/ubuntu/ --dist=trusty,trusty-updates,trusty-security --section=main,restricted,universe,multiverse /var/www/cobbler/repo_mirror/local-trusty --nosource -a amd64
received on stdout: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 00 1397751862 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
[GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 00 1397751862 9
[GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
gpgv: keyblock resource `/var/lib/cobbler/.gnupg/trustedkeys.gpg': file open error
gpgv: Signature made Thu Apr 17 18:24:22 2014 CEST using DSA key ID 437D05B5
gpgv: Can't check signature: public key not found
gpgv: Signature made Thu Apr 17 18:24:22 2014 CEST using RSA key ID C0B21F32
gpgv: Can't check signature: public key not found
```

What am I missing here? I cannot even manage to get the ugly workaround working, to somehow disable key checking. Can you help me how to get this setup working?

Bonus question: What is the canonical (not Canonical) way to installing bare-metal machines with cobbler and have them running even after reboot? If PXE is the first boot option, they will loop-install until I don't change the system's profile in cobbler. If PXE is after HDD boot, I will have to crash the installation in order for the machine to continue booting to PXE, in which again cobbler is in charge. I tried the -single-boot (or something similar) option in cobbler, that would only PXE boot a specific system once, and after it would deliberately fail PXE on the server side, however that did not work and the machine was in an install-loop.

I'm doing all my testings using Hyper-V and a notebook, but these don't seem to cause the issue.

---

### Post by nagymatef on 2014-04-23
I continued my search, and after a few hours, I found a way to solve the issue.

One needs to install apt-key and import the PUBKEYS that cobbler does not seem to find. Once a regular user imported these keys, the .gnupg/trustdb.gpg file must be copied over (or symlinked) at `/var/lib/cobbler/.gnupg/trustedkeys.gpg' where cobbler is looking for the keys. After this has been done, one can import the Ubuntu repo into cobbler.

---

### Post by thirstycat on 2014-04-29
I'm in the midst of trying to do the same thing-- use cobbler to provision a bunch of workstations as well as maintain a local copy of the ubuntu repo.
I'm curious if you've gotten the whole preseed process to work properly using the local repo.  

I've imported the repo, but am getting a "bad archive mirror" before the install starts.  :(

---

### Post by thirstycat on 2014-05-01
> **thirstycat said:**
> I've imported the repo, but am getting a "bad archive mirror" before the install starts.  :(
answering my own question :)

the clue is here: [http://www.colinmcnamara.com/setting-up-cobbler-pxe-auto-deployment-for-ubuntu-server-12-04-precise/](http://www.colinmcnamara.com/setting-up-cobbler-pxe-auto-deployment-for-ubuntu-server-12-04-precise/)

basically, it *looks* like you need to name your repo file with an extension of .precise in order for it to be properly recognized.  ugly workaround, but it did fix my problem.
Hopefully someone with a bit more time to look into this can just fix the underlying problem in Cobbler.

---


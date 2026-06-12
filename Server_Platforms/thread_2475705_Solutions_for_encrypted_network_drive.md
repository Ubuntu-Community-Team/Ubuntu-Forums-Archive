---
title: "Solutions for encrypted network drive?"
date: 2022-06-05
forum: Server Platforms
---

### Post by Elmi77 on 2022-06-05
Hi,

I'm looking for a solutions to have an encrypted network drive:


[LIST]
[*]one Ubuntu server somewhere in the internet, that provides the storage space
[*]Windows and Linux clients that connect to this server and mount the storage space as local drive
[*]for security the connection is encrypted
[*]for even more security the data on the storage space is encrypted and the keys to decrypt these data are available ONLY at the clients - so also for the worst case where somebody highjacks the server, these data are of no use for the "bad guys"
[/LIST]

So...can anybody recommend a solution for this? I already tried Syncthing, but it is a nightmakre in terms of configuration and security (it allows password-encryption but the password has to be available on server side too).

Thanks!

---

### Post by #&amp;thj^% on 2022-06-05
If its linux, consider sshfs,sftp or scp shares. They can be mounted pretty easily and provide end to end encryption.

Do the files need to be encrypted, or do you need to keep unauthorized people out? These are at least two distinct requirements.

This is a site they may help for now: [https://semanticlab.net/sysadmin/encryption/Network-bound-disk-encryption-in-ubuntu-20.04/](https://semanticlab.net/sysadmin/encryption/Network-bound-disk-encryption-in-ubuntu-20.04/)

---

### Post by Elmi77 on 2022-06-06
> **1fallen said:**
> Do the files need to be encrypted, or do you need to keep unauthorized people out?

Both. And this is the problem I see with all SSH-based stuff: transfer is encrypted but on server side the stored data are not (at least as far as I understood this).

---

### Post by TheFu on 2022-06-06
Nextcloud supports TLS network encryption and per-user data encryption.  I've never used it. I don't trust php webapps not to lose all the data they contain, but I suppose lots of people do.

The "local mount" is a webdav mount, which pretty much sucks, is terribly slow, and doesn't support all sort of things.

You could use LUKS for the data to be encrypted at rest and the ssh/scp/sftp/sshfs stuff to access the LUKS encrypted area.  You'd have to manually mount it and while mounted, it is unlocked for anyone else on the system, so use user permissions judiciously.  That won't prevent root from accessing the mounted storage, but you could manually mount/umount the LUKS as needed.

IMHO, all other encrypted storage methods are toys compared to LUKS.  encfs, encryptfs, each have some serious faults and likely provide a false sense of security around the encrypted data, which I think is worse than not being encrypted at all.

---

### Post by LHammonds on 2022-06-06
As TheFu pointed out, file/disk encryption means nothing if the "bad guy" can hack into your system while its running while remote or having physical access.  The file/disk encryption only provides protection when the machine is offline for the most-part...assuming you don't have the password to mount it anywhere on your system (including bash command history).

If you want to share this over the Internet, do not make whatever service (e.g. NextCloud) you have exposed directly to the Internet.  Hide it behind VPN access.

LHammonds

---

### Post by TheFu on 2022-06-06
> **LHammonds said:**
>  If you want to share this over the Internet, do not make whatever service (e.g. NextCloud) you have exposed directly to the Internet.  Hide it behind VPN access.

Good reminder.  That should go without saying, but we never know who is reading.

Our email systems, except the gateway, are also behind a VPN.  
Users can only access/send emails if they are connected to the VPN (or on a specific internal "trusted" LAN).  We keep everything off the internet possible.  
Same goes for outbound access.  Using a proxy for all inbound and outbound connections (2 different sorts of proxies) provides another layer where the bad guys can be tripped up.

If you are putting this stuff on _***someone else's computer***_ - often called the cloud or on a VPS - then all bets are off. With physical access, security is nearly impossible.

---

### Post by Elmi77 on 2022-06-07
> **LHammonds said:**
> As TheFu pointed out, file/disk encryption means nothing if the "bad guy" can hack into your system while its running while remote or having physical access.

For exactly this reason I'm looking for a solution that does not come with this weakness: the data have to be encrypted at the user side only, the hosting server should not know anything about this and store only the encrypted data (this is where Syncthing is that poor: it not only expects the encryption password on server side but also stores it as plain text in its configuration :-o )

---

### Post by TheFu on 2022-06-07
> **Elmi77 said:**
> For exactly this reason I'm looking for a solution that does not come with this weakness: the data have to be encrypted at the user side only, the hosting server should not know anything about this and store only the encrypted data (this is where Syncthing is that poor: it not only expects the encryption password on server side but also stores it as plain text in its configuration :-o )

If you want to pre-encrypt stuff, just use gpg or openssl to encrypt stuff. Both use PKI methods, so we'd encrypt the file using the public key and decrypt using the private key.
[https://www.gnupg.org/gph/en/manual/x110.html](https://www.gnupg.org/gph/en/manual/x110.html) - there are 20 other pages with the same answer. I like going to the horse for answers, first.

[https://nsrc.org/workshops/2017/renu-nsrc-cns/networking/cns/en/Labs/exercise-openssl-encryption.htm](https://nsrc.org/workshops/2017/renu-nsrc-cns/networking/cns/en/Labs/exercise-openssl-encryption.htm)

In my mind, gpg (actually gpgv2) is more secure than openssl, but both are generally trusted provided the latest versions are used. With openssl, be certain to specify TLS v1.3 or later.
Of course, these manual methods don't change the name, so you'd want to do that - probably to a sha256 series and retain that.

You know, there are tools for storing encrypted data on other people's computers which have been around a few decades.  Don't know why I didn't think of those first.  If you control all the computers used, there's a tool called **retroshare**. With it, you can skip using someone else's computer completely.  Only 1 computer needs to have 1 port open on the internet for all the others to "find" each other.  Each device sets up a different key.

Here's a tool that does in-browser encryption before sending files up.  I'm not a fan of using browsers for encryption for a number of reasons.
[https://framagit.org/fiat-tux/hat-softwares/lufi](https://framagit.org/fiat-tux/hat-softwares/lufi)  They test the browsers for popular devices - phones, tablets, OSes.
>  'It stores files, encrypts them in the browser and allows you to download them' 
[https://alternativeto.net/software/lufi/](https://alternativeto.net/software/lufi/) says there are more than 50 alternatives to Lufi.

GNU used to have a bit-torrent-like tool that would chunk up parts of files and encrypt them onto a web of computers.  I can't remember the name now. It used Onion routing so people storing parts of files didn't know where the fail came from and because it is strong encryption and check-sum filenames, the contents were unknowable too.

Some other ideas: [https://github.com/awesome-selfhosted/awesome-selfhosted#file-transfer--synchronization](https://github.com/awesome-selfhosted/awesome-selfhosted#file-transfer--synchronization)

[https://www.dyne.org/software/tomb/](https://www.dyne.org/software/tomb/) is one I need to check out. The first issue I see with Tomb is that it requires sudo access. That's because it uses FUSE to mount and umount the storage.

What I find funny is that we can easily create a block file, luks encrypt it, then put a file system onto that block file and have very secure access to what's inside.

Just blindly thinking now, but **duplicity** has strong encryption and chunks files into 5MB parts, uses a multitude of upload methods (too many to name ftp, sftp, rsync, scp, http, just to start), so the server wouldn't really see the files, but clients can access the backups through a duplicity restore.  There are GUI clients which are compatible - Deja Dup and Duplicati.

---

### Post by LHammonds on 2022-06-07
> **Elmi77 said:**
> the data have to be encrypted at the user side onlyYou mean decrypted?  You could use VeraCrypt to create an encrypted file container on the server.  When the client connects to the share, then uses VeraCrypt decrypt and mount the file as a volume (drive letter).  There are a bunch of tools to do this for various platforms (as TheFu pointed out)

LHammonds

---


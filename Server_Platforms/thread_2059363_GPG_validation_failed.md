---
title: "GPG validation failed"
date: 2012-09-17
forum: Server Platforms
---

### Post by said76 on 2012-09-17
Hi,

I'm running into GPG validation issue on Ubuntu Server 12.04 LTS.

Here it is
dbg: channel: found mirror [http://saupdates.openprotect.com/](http://saupdates.openprotect.com/)
dbg: channel: selected mirror [http://saupdates.openprotect.com](http://saupdates.openprotect.com)
dbg: http: GET request, [http://saupdates.openprotect.com/127.tar.gz](http://saupdates.openprotect.com/127.tar.gz)
dbg: http: GET request, [http://saupdates.openprotect.com/127.tar.gz.sha1](http://saupdates.openprotect.com/127.tar.gz.sha1)
dbg: http: GET request, [http://saupdates.openprotect.com/127.tar.gz.asc](http://saupdates.openprotect.com/127.tar.gz.asc)
dbg: sha1: verification wanted: d3ed13974c37c563553dd4a537770cf50fae6d15
dbg: sha1: verification result: d3ed13974c37c563553dd4a537770cf50fae6d15
dbg: channel: populating temp content file
dbg: gpg: populating temp signature file
dbg: gpg: calling gpg
dbg: gpg: gpg: Signature made Thu 06 Mar 2008 17:54:07 EST using DSA key ID BDE9DC10
dbg: gpg: [GNUPG:] ERRSIG 258CDB3ABDE9DC10 17 2 00 1204786447 9
dbg: gpg: [GNUPG:] NO_PUBKEY 258CDB3ABDE9DC10
dbg: gpg: gpg: Can't check signature: public key not found
error: GPG validation failed!
The update downloaded successfully, but it was not signed with a trusted GPG
key.  Instead, it was signed with the following keys:

    BDE9DC10 

Perhaps you need to import the channel's GPG key?  For example:

    wget [http://spamassassin.apache.org/updates/GPG.KEY](http://spamassassin.apache.org/updates/GPG.KEY)
    sa-update --import GPG.KEY

channel: GPG validation failed, channel failed
dbg: channel: attempting channel 70_sare_stocks.cf.sare.sa-update.dostech.net

Then, I run the following commands to generate the new key
$ wget [http://spamassassin.apache.org/updates/GPG.KEY](http://spamassassin.apache.org/updates/GPG.KEY)
$ sa-update --import GPG.KEY

but sill getting the same output.

I wonder if anyone has had a similar experience as I have before and would kindly share some of the ideas about how to get around this issue.

Any help would be greatly appreciated.

Thank you

---


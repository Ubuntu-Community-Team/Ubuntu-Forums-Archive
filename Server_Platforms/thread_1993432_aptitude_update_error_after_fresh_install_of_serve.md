---
title: "aptitude update error after fresh install of server 12.04 x64"
date: 2012-06-02
forum: Server Platforms
---

### Post by cbSuperiorSoundSystems on 2012-06-02
I have a freshly installed Ubuntu Server 12.04 LTS x64 installed.

After aptitude update I get this:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signature couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

I already ran aptitude safe-upgrade.

What do I have to do to fix this?

EDIT:
SOLVED:
[QUOTE=drs305;11396213]Try opening Software Sources, go to the  Authentication tab, and remove the keys for Extras and Ubuntu Archive.  If you also see one for Security, remove that one as well.

Then run 'sudo apt-get update' again. You will get the authentication  errors. Copy the numbers to the following command (you can use the full  code rather than just the last 8 characters) and try adding them again.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys < *add keys here* >  
```

---


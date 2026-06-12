---
title: "Strongswan fails while accessing /dev/urandom"
date: 2012-06-19
forum: Server Platforms
---

### Post by Rexilion on 2012-06-19
I made a bug that is relevant to this post [here]("https://bugs.launchpad.net/ubuntu/+source/strongswan/+bug/1014361"). However, I'm turning to the community now, as I cannot believe that no one else has stumbled on this issue. I'm not using any wild configuration settings, it's just a regular roadwarrior setting using ikev2, tunnel (+ipcomp transport) and authentication using RSA signatures (PKI infra).

However, on the cliënt, when I want to start the connection, I get this:
> root@Delta:~# ipsec up remote
initiating IKE_SA remote[1] to 82.169.126.54
opening "/dev/urandom" failed: Permission denied
error generating nonce
tried to check-in and delete nonexisting IKE_SA

And this is where things get really weird:

> root@Delta:~# ls -la /dev/urandom
crw-rw-rw- 1 root root 1, 9 jun 17 17:54 /dev/urandom
root@Delta:~# lsattr /dev/urandom
lsattr: Bewerking wordt niet ondersteund Tijdens lezen van vlaggen op /dev/urandom (-> says it is not supported)

But we are root right... ? Yes we are:

> root@Delta:~# ps -p 21021,22515,21020,22514 -o args,group,pgid,ppid,rgroup,ruser,tty,user,gid,rgid,ruid,uid
COMMAND GROUP PGID PPID RGROUP RUSER TT USER GID RGID RUID UID
/usr/lib/ipsec/starter root 21020 1 root root ? root 0 0 0 0
/usr/lib/ipsec/charon --use root 21021 21020 root root ? root 0 0 0 0
/usr/lib/ipsec/starter root 22514 1 root root ? root 0 0 0 0
/usr/lib/ipsec/charon --use root 22515 22514 root root ? root 0 0 0 0

More relevant info can be found in the bugreport. We haven't tried much so far, only the suggestion made by [this]("http://askubuntu.com/questions/30115/root-cannot-access-dev-urandom?") link. No dice though.

And it is no way my intention to start a flamewar, troll or something... But these settings work on a Gentoo cliënt. I'm one of the few lucky one's who managed to 'convert' my parents to use Linux and Ubuntu was the logical choice (introducing my parents to Gentoo's emerge, USE-flags, CFLAGS, compilation failures, ABI/API compatibility might happen in another 100 years :mrgreen:). It's a really simple setup. Basically it's and alternative installation CD. I simply only installed base and the user-session starts with startx. It has no networkmanager, no display manager and uses XFCE components to work. At boot it uses 93 out of 512 MB of RAM (so that is not an issue I suppose). PAM authentication works, I had to do some fiddling to authenticate the regular user with consolekit but this works now. Power events (shutdown, restart, hibernate) and USB devices (camera's, USB, mounting, umounting) all work flawlessly.

                              Thanks in advance for *any* suggestions

---

### Post by Rexilion on 2012-06-20
Disabling libcap functionality fixes the issue. Strongswan has a 'native' alternative, but I haven't tried that one yet.

Disabling it is not *such* a big deal as this Strongswan installation is a client. Thanks anyway!

Further findings will be placed in bug [1014361]("https://bugs.launchpad.net/ubuntu/+source/strongswan/+bug/1014361").

---


---
title: "Samba missing findsmb?"
date: 2006-04-02
forum: Server Platforms
---

### Post by coldwiston on 2006-04-02
I've currently installed Samba from the breezy repository, and it seems to be missing the findsmb script. I've looked around and the only indication of this is a bug listing that the findsmb man page was available without the binary, and now that has been removed as well.

I'm not sure why the powers that be have chosen to remove findsmb, but I'd like to get the findsmb script with my Samba install. I'm aware i could just use the nmblookup and smbclient programs manually, but I like the way findsmb displays the information.

I dont want to compile the latest version, as I like the automatic security updates that APT gives me.

Apparently it's a perl script, is it likely to just work if I strip the script from the official Samba source? I feel if things like this are stripped from the repository they should be clearly stated in the package information, and possibly some instructions on how to include it if desired?

Still loving Kubuntu! 

Cheers for any help,

Sean

---


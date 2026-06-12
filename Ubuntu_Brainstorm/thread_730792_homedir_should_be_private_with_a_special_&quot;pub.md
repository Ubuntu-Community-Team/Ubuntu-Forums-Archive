---
title: "homedir should be private with a special &quot;public&quot; readable folder"
date: 2008-03-21
forum: Ubuntu Brainstorm
---

### Post by ubuntu_demon on 2008-03-21
Your homedir should be private but there should be a special "public" readable folder where you can put files you want to share with other users of the same machine.

In other words :
The default umask should be set to 077. XDG_PUBLICSHARE_DIR should have umask 022

RATIONALE :
* the files in your home dir should not be read by others unless you give others permission to do so (privacy and security issue)
* with this solution people have an easy way of giving others permission to read their files

IMPLEMENTATION DETAILS :

The default umask should be set to 077 (in /etc/profile)
The default umask for XDG_PUBLICSHARE_DIR should be set to 022

XDG_PUBLICSHARE_DIR should be chmodded to 755 to ensure everybody can read the contents of this folder.

XDG_PUBLICSHARE_DIR is defined in ~/.config/user-dirs.dirs and is set to $HOME/Public by default. 

launchpad :
[https://bugs.launchpad.net/bugs/204577](https://bugs.launchpad.net/bugs/204577)

ideastorm :
[http://brainstorm.ubuntu.com/idea/5287/](http://brainstorm.ubuntu.com/idea/5287/)

---

### Post by jimcooncat on 2008-03-21
Could you please describe (or give us a link) on how to implement this on an existing setup? I see you've provided details, but sure could use a step-by-step so as not to mess up. 

I take it that we'd also apply the same ideas to /etc/skel so new users would automatically get the same privacy?

---


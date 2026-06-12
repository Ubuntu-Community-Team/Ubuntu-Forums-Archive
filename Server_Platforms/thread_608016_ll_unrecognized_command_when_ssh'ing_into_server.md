---
title: "ll unrecognized command when ssh'ing into server"
date: 2007-11-09
forum: Server Platforms
---

### Post by Ba66e77 on 2007-11-09
When I log into my box over ssh, I get this message:
-bash: alias: ll: not found
-bash: alias: =: not found
-bash: alias: ls: not found
-bash: alias: -l: not found

even though those aliases are defined in my .bashrc (see excerpt below) and are recognized commands when I'm working directly on the box.

Can someone explain to me why this is happening?

--excerpt from .bashrc
# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

---

### Post by qpieus on 2007-11-09
My understanding is that .bashrc is not executed when you ssh into your box, because you are logging into a login shell in this case. The .bashrc file is executed when you use an interactive, non-login shell. The file .bash_profile is executed for login shells, which is what you are doing when you ssh into the box. So copy your aliases from .bashrc into .bash_profile and they should work next time you ssh into it.

reference:

[http://joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://joshstaiger.org/archives/2005/07/bash_profile_vs.html)

---

### Post by Ba66e77 on 2007-11-09
Thanks, qpieus.  That did the trick.

---

### Post by qpieus on 2007-11-09
ha, I only knew this because I had the same problem last week :)
I have an free shell account I ssh into and I was trying to set some aliases and they wouldn't take. Then I found the page I linked to in my other post, put the aliases in .bash_profile and then the aliases worked.

---

### Post by m4ttd on 2008-03-24
Just to muddy the waters, fyi etc...

Not sure if we're even talking about the same thing

1) I've only just started using LINUX
2) Just completed a xubuntu install on an old PII machine
3) "New" linux box on a home network
4) I SSH into my linux box from XP via PuTTY

I dont think I changed any of PuTTYs defaults
I was getting exactly the same errors, sort of:
-bash: alias: ll: not found
-bash: alias: =ls -l: not found
-bash: alias: la: not found
-bash: alias: =ls -a: not found
...

My problem explained on
[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-07/1693.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-07/1693.html)
ie twas the spaces in the assignment

like I said not sure if this all the same.
My aliases are in .bash_aliases with the appropriate section to reference this uncommented in my ~ .bashrc

Now all good: local on box & via PuTTY SSH

fwiw

Regards...

---


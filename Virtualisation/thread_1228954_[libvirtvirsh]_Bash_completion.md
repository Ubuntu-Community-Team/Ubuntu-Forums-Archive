---
title: "[libvirt/virsh] Bash completion"
date: 2009-08-01
forum: Virtualisation
---

### Post by jd.truc on 2009-08-01
Hello,

(I do not know if it is the right place...)

Recently I get bored by the lack of completion when typing virsh commands. Si I started bash_completion script.

It is little for now, cause it only completes the common commands, which I often use.

I attached the script.

To use it : copy it in /etc/bash_completion.d/ and run source /etc/bash_completion.

--
Judu

---

### Post by xOrphenochx on 2009-08-03
You do know that if you just type virsh it becomes its own shell? That is most likely why completion doesn't work.

---


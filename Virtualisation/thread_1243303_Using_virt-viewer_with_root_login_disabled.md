---
title: "Using virt-viewer with root login disabled"
date: 2009-08-18
forum: Virtualisation
---

### Post by stephanhughson on 2009-08-18
I'm using virt-viewer to see screens like this:

virt-viewer --wait --connect qemu+ssh://root@my-computer-name:22/system name-of-the-machine-i-want-to-see

(I actually have SSH running on a different port).


It works, but I normally like to disable root logins.

I don't have SSH keys setup, so when I use the command above, it just asks for the root password twice and I'm fine with that.


Is it possible to use virt-viewer to see screens of virtual machines without needing to login as root? Can I add my normal user to a group that would allow this, or is there another easy way?

Thanks!

I guess if not, I'll have to enable root login with SSH keys only and that will be secure enough. I could even make an SSH key which also has a password for extra security, but it seems like hassle, I'd rather just disable root login.

---

### Post by bodhi.zazen on 2009-08-18
Not that I know of (you need to log in as root).

+1 on using a key. You can add the key to RAM with ssh-add and it will be fairly seamless.

---

### Post by stephanhughson on 2009-08-25
Thought so, thanks for confirming.

I've only ever added keys manually. I guess ssh-add automates the process, but what did you mean about adding it to RAM?

If you have a second to give more detail, that would be pretty interesting.

Thanks.

---

### Post by bodhi.zazen on 2009-08-25
ssh-add loads your ssh keys into ram (or so I thought).

---


---
title: "ubuntu on hyper-v"
date: 2016-11-04
forum: Virtualisation
---

### Post by alexkoganov on 2016-11-04
hi guys
a couple a days ago i installed ubuntu on the virtual machine (hyper-v) and ha some resolution problems.
i found a nice guide how to fix it [https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/](https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/) .
i inserted the changes to the grub line and after i performed : [FONT=Segoe UI]**sudo update-grub **the output was:
[/FONT]
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution

what is it and what can i do from here?

tnx a lot

---

### Post by deadflowr on 2016-11-04
We'd need to see what the /etc/default/grub file looks like, but from the error it would seem that you aren't properly encapsulating the added line.
Hence the backquote substitution mention.

Perhaps, since this is a vm and hard to simply copy and paste, instead take a snapshot and post that.
(Use the forums attachment function (use either reply to thread or Go advanced and click the paperclip icon in the toolbar to add attachments)

---


---
title: "fdisk security"
date: 2010-05-16
forum: Security
---

### Post by johngreth on 2010-05-16
why don't I need to be root to run fdisk? Isn't that a security vulnerability to be able to change partitions without root permissions?

---

### Post by frostschutz on 2010-05-16
yes, it would be a security vulnerability

anyone with raw access to your disk(s) is basically root as they can circumvent file permissions etc.

however in a default install, the user does NOT have permission, you'd get "Unable to open /dev/sda" or similar message.

Did you put your user in the disk group? That would be your error, then.

---

### Post by johngreth on 2010-05-16
I see. Before, I ran fdisk without any input and it gave me a list of operations, but no error. That's what got made me think there was a problem.

It is still secure because when I gave it a disk to edit it gave me the "Unable to open /dev/sda" message.

I feel much better about it now. Thanks.

---


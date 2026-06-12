---
title: "ubuntu cloud 12.10 maas can not import-boot-images"
date: 2013-03-26
forum: Ubuntu Cloud and Juju
---

### Post by eruan on 2013-03-26
I was in accordance with the official document transmission command, tips error,why,who can tell me

$ maas-cli login maas [http://192.168.0.103/MAAS/api/1.0](http://192.168.0.103/MAAS/api/1.0) xArZzhyGAUWgeMV8KA:53ALRqceY3CmXgkJuc:CnAuhCjEsqfuyJLzEyYMcQZ5kukjCsrk
$ maas-cli maas node-groups import-boot-images
usage: /usr/lib/python2.7/dist-packages/maascli/__main__.py maas node-groups
       [-h] COMMAND ...
/usr/lib/python2.7/dist-packages/maascli/__main__.py maas node-groups: error: argument COMMAND: invalid choice: u'import-boot-images' (choose from 'register', 'list', 'refresh-workers', 'accept', 'reject')

---

### Post by maarten-ectors on 2013-09-10
Try to change the hostname from maas and domain ubuntu.com to something else.

---

### Post by qwerty5555 on 2013-09-19
It would seem the command has changed. Try running this to import the boot images:

$ sudo maas-import-pxe-files

---


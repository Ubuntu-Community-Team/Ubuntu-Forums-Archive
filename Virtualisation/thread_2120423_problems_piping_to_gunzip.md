---
title: "problems piping to gunzip"
date: 2013-02-26
forum: Virtualisation
---

### Post by TheMightyGirth on 2013-02-26
Hi All,

I am running the following command to create a disk image of a server I want to virtualise. The command works fine but gives me a compressed image on the far side. I am trying to work out how to pipe things so that the output from ssh get's gunziped before being passed to dd.

The command is;

dd if=/dev/sda | gzip -1 - | ssh garethw@10.0.8.10 dd of=/home/garethw/image_sda.img

I know I can just gunzip at the remote end once the transfer is complete but I would prefer to do it in 1 hit if it's possible.

I've tried various combinations of adding 

gunzip - |
gzip -d |
cat | gzip -d |
cat | gzip - |

after the IP and before the dd command but have not managed to get anything working.

Anyone have any ideas?

---

### Post by mckenna1977 on 2013-02-26
Try this:

dd if=/dev/sda | gzip --fast -c | ssh garethw@10.0.8.10 /bin/dd of=/home/garethw/image_sda.img.gz

---

### Post by schragge on 2013-02-26
Maybe
```

dd if=/dev/sda | gzip -1 | ssh garethw@10.0.8.10 sh -c 'zcat > /home/garethw/image_sda.img'

```

---

### Post by TheMightyGirth on 2013-02-26
Hi schragge, that's running at the moment and seems to be working. Will let you know how it ends up.

mckenna1977, thanks for the idea at least that way it would be more obvious that it's a gz file.

---


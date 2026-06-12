---
title: "rsync won't delete on destination, and other issues (ext3-&gt;fat32)"
date: 2009-03-06
forum: Security
---

### Post by hachel on 2009-03-06
hi,
I execute the following rsync-command to backup my home-folder:
rsync -r -n -t -v --progress --delete --max-size=100MB /home/hachel/ /media/HACHEL/home

One problem is that it always backups the same couple of thousand files, every time I run it, even if I run it again right after it finished.
Among those files are mp3-files, some banshee-lastfm- and -artwork-folders and a couple of other smaller configuration-files.

The other problem is that it won't delete files on the destination that aren't on my source anymore. I don't know if it doesn't delete any files at all, I didn't check that, but there are some mp3-folders and some rar-files it just won't delete.

I suppose it has something to do with the fat32-format on my usb-drive, at least that's all I can think of.

Anyone?

thanks,

hachel

---


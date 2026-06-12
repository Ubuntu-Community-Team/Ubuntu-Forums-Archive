---
title: "ubuntu suggestion"
date: 2014-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by cmcanulty on 2014-03-05
I think a good feature would be to warn when saving a file to an unsupported filename. For example whenever I download an ebook with a : in the title it saves fine. But then I backup with grsync and it fails and I have to scroll all over to find the error and remove the offending character. For example if I try to save a file named "Dogs:the whole story" it saves fine but makes me get an error when backing up. So when I try to save it a dialog should pop up saying it is an illegal file name so I would know to change it then and avoid future problems.

---

### Post by Dave_L on 2014-03-05
"Dogs:the whole story" is a legal file name.

---

Is the grsync destination a non-Linux file system? Maybe this article will help:

How can I substitute colons when I rsync on a USB key?
[http://askubuntu.com/questions/11634/how-can-i-substitute-colons-when-i-rsync-on-a-usb-key](http://askubuntu.com/questions/11634/how-can-i-substitute-colons-when-i-rsync-on-a-usb-key)

---

### Post by cmcanulty on 2014-03-05
no I back up from ext4 to ext4

---

### Post by Dave_L on 2014-03-05
That's odd.  I just did a test with rsync, for which grsync is a front end, and it properly copied a file with a colon in its name.

Does grsync show the equivalent rsync command(s) it's using?  I would check myself, but I don't have it installed.

---

### Post by vasa1 on 2014-03-05
> **Dave_L said:**
> That's odd.  I just did a test with rsync, ... and it properly copied a file with a colon in its name. ...
Same here. I'm using this alias:
```
alias myrs='rsync -rtv --delete --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/TOSHIBA\ EXT/BACKUP/ &> $(date +%s)rsync.log'

```

---


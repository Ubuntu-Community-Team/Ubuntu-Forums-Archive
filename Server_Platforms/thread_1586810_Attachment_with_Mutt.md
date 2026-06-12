---
title: "Attachment with Mutt"
date: 2010-10-02
forum: Server Platforms
---

### Post by 448191 on 2010-10-02
# echo "Body" | mutt -a foo -s "Test" [email]john@domain.com[/email]
Can't stat [email]john@domain.com[/email]: No such file or directory
[email]john@domain.com[/email]: unable to attach file.

The file "foo" exists, and I don't get why it's trying to stat the email. Without the -a option and it's arg it works just fine.

---

### Post by Bachstelze on 2010-10-02
[font=monospace]man mutt[/font] says:

```
       -a file [...]
              Attach  a  file  to your message using MIME.  When attaching single or multiple files, separating file&#8208;
              names and recipient addresses with "--" is mandatory, e.g. mutt  -a  image.jpg  --  addr1  or  mutt  -a
              img.jpg *.png -- addr1 addr2.  The -a option must be placed at the end of command line options.

```

So you want to do

```
echo "Body" | mutt -s "Test" -a foo -- john@domain.com
```

---


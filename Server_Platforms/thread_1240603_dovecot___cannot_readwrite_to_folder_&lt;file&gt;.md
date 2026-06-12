---
title: "dovecot :  cannot read/write to folder &lt;file&gt;"
date: 2009-08-14
forum: Server Platforms
---

### Post by cbear on 2009-08-14
Ubuntu:  v8.10
Postfix: v2.5.5
Dovecot: v1.1.4


I have a folder (newspam) where I place junk mail - someone else created it for me.  I recently deleted the contents of the file using 

```
echo "" > newspam
```

Now I get an error from my client (thunderbird) everytime I try to open the folder or drag emails into it.  error "Mailbox is not a valid mbox file".  I assume this is an imap issue, but I am not sure.

Any help would be appreciated.

-tom

---

### Post by cbear on 2009-08-15
fixed it.... if you delete the file (rm) and then re-create (touch) ...everything works.  I guess dovecot doesn't like the echo "".

---


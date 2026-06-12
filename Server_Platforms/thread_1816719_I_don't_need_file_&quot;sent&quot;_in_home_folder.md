---
title: "I don't need file &quot;sent&quot; in home folder"
date: 2011-08-02
forum: Server Platforms
---

### Post by Fodox on 2011-08-02
hello

I have ubuntu server 10.4. 
In my home folder I have the file "sent" where are stored emails sent with mutt and ssmtp. I don't need this file, so how can I 
configure mutt or ssmtp?


thank you

---

### Post by andrew.46 on 2011-08-03
By default sent mails are not stored at all in mutt. However this is usually set in ~/.muttrc with a setting such as:

```

### Folders ###
set mbox_type=mbox                   # although this is the default, does not _need_ to be set.
set folder="~/mail/mailboxes"        # Contains all the mailboxes
**[COLOR="Red"]set record="+sent"  [/COLOR]**                 # where to store sent messages (+ local mail folder)
set postponed="+postponed"           # where to store draft messages (+ local mail folder)
set move=no                          # Don't move mail from the spool when closing mutt
                                     # & don't ask whether to move or not

```

(my own setting) so perhaps have a look at your own setting in ~/.muttrc and adjust as desired.

---

### Post by Fodox on 2011-08-03
Thank you for indication! 

From ubuntu manuals, 10.4LTS, man muttrc:

```
record
Type: path
Default: “~/sent”

This specifies the file into which your outgoing messages should be  appended.
(This is meant as the primary method for saving a copy of your messages, but another way to do this is  using  the “my_hdr”  command  to  create  a  “Bcc:”  field  with your email address in it.)
The value of  $record  is  overridden  by  the  $force_name  and $save_name variables, and the “fcc-hook” command.
```

I setted in my ~/muttrc:

```
set record=""
```

It seems to work.

   Fod.

---


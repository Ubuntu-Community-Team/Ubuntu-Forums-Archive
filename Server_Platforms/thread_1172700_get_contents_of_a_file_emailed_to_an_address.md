---
title: "get contents of a file emailed to an address?"
date: 2009-05-28
forum: Server Platforms
---

### Post by rhcm123 on 2009-05-28
I run a small mail server (just a home hobby). On said mail server there is a file that is variable - it changes every so often (long story). I want my postfix/courier setup to email me the contents of the file everytime it's modified. Can anybody give me a command to do so (i have mail-utils installed)?

---

### Post by LepeKaname on 2009-05-28
It may not be so elegant but it may work:

Option 1)
Create a cron script to monitor the file each minute. You can compare hashes (base64, md5, etc) of the file contents. If change, then send the email.

Option 2) 
You could use tail -f and direct it to a script, so if it changes, you could either send the additions or the whole file.

To send the file:

```
mutt -s "The file was changed!" -a /tmp/this_is_my_file.txt
to_me@mydomain.com < /tmp/custom_message.txt
```

The -a is to send it as attach, as I think is a text file you want to send, you can remove the "-a /tmp/this_is_my_file.bin" and leave it like:

```
mutt -s "The file was changed!" to_me@mydomain.com < /tmp/this_is_my_file.txt
```

You can also use the "mail" command:

```
mail -s "The file was changed!" to_me@mydomain.com < /tmp/this_is_my_file.txt
```

---

### Post by grantemsley on 2009-05-29
The above solves the emailing the file part.

For monitoring the file, take a look at the packages "dnotify" or "fam"

---


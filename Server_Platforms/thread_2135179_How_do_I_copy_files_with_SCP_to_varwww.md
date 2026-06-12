---
title: "How do I copy files with SCP to /var/www?"
date: 2013-04-13
forum: Server Platforms
---

### Post by jayredge on 2013-04-13
Hello Ubuntu Community!

[COLOR=#333333][FONT=Ubuntu Beta]I need to copy files from my computer to my server's folders in /var/www so they are uploaded to my cloud. Here's what I try to do:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I open my computer's terminal and type:

```
[COLOR=#222222][FONT=Ubuntu Mono]scp /media/user/Files/Documents/documents.docx ubuntu@mywebsite.com:/var/www/documents[/FONT][/COLOR]
```

**Notes on this step**

[LIST]
[*]The hard drive that I am trying to copy the file from is an NTFS formatted drive. I use this drive to store all my media on, in other words it has no operating system on it. I use a separate SSD with dual boot for my operating system. Also, this drive is mounted when I do this.
[*]'ubuntu' is the actual username of the server I am trying to copy to.
[/LIST]
Then it asks me for that computers password and then I get:

```
[COLOR=#222222][FONT=Ubuntu Mono]scp: /var/www/documents/documents.docx: Permission denied[/FONT][/COLOR]

```

What's wrong here?

**Other Notes**

[LIST]
[*]After much Googling, I found it may be a permission issue, so I tried the various solutions with no luck. The most common solution I tried was adding a user to the group. I would add the server's user (ubuntu) to the group, but that didn't help. Am I supposed to add my computer's username to the group? If so, do I add the stuff before the colon, after the colon, or both?
[*]I understand that one method to get around this would be to copy the files to my server's home directory, and then cp them to /var/www through SSH, but I would rather not do that because its an extra step.
[/LIST]
Any help would be greatly appreciated!
Thank You!


[/FONT][/COLOR]

---

### Post by CharlesA on 2013-04-13
What group did you add your user to?

By default /var/www should be r-x-r-x-r-x, so you won't be able to write anything to it without changing the permissions.

---


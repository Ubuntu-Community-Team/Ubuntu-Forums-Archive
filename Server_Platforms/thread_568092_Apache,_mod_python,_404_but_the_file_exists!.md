---
title: "Apache, mod_python, 404 but the file exists!"
date: 2007-10-05
forum: Server Platforms
---

### Post by capsid on 2007-10-05
I'm getting a 404 error when I run a python script through apache. I know this seems like a simple matter of changing file permissions, but I've tried messing with permissions and haven't gotten it yet.  

I followed the directions here to set up mod_python to automatically parse/run scripts:
[http://ubuntuforums.org/showthread.php?t=91101](http://ubuntuforums.org/showthread.php?t=91101)

What is killing me is that one python file is being run/served, but  my other .py file is not working.  I did a chmod 755 on the directory   (now they both read -rwxrwxr-x, belong to the same user) so they should all be world-readable, correct?

I'm stumped as to where to look for clues, so please let me know what output I can provide to give you a better picture of what is misconfigured.

FYI, I also tried chown-ing the files to $apache_user:$apache_group but that didn't work so I reverted it.  

Thanks so much for any help you can provide!

---


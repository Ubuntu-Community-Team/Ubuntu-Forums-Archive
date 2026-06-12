---
title: "Perl script works with Apache piped logs but not Python script"
date: 2009-08-19
forum: Server Platforms
---

### Post by cmwslw on 2009-08-19
I need to port my Perl log handling script to Python. Here is a simple example of a Perl script I can use:
```
#!/usr/local/bin/perl

$|=1; # Use unbuffered output

while(<>) {
   system("beep");
}
```
As you can probably see, I am telling the system to beep whenever a request is made to test the script. Everything works fine on this one, but when I try a Python script such as this:
```

import sys
import os

for line in sys.stdin:
    os.system('beep')

```
everything runs but the system does not beep after a request. Here are the lines I was and am using in my apache configuration file:
```
CustomLog "|perl /var/web/onhit.pl" "onhit"   <-OLD LINE
CustomLog "|python /var/web/onhit.py" "onhit" <-NEW LINE
```
I am following [this email]("http://mail.python.org/pipermail/python-list/2009-January/695185.html") on the Python mailing list. Anyone have an idea why this is not working?

EDIT: I know the problem has something to do with "for line in sys.stdin". For some reason it is just not detecting anything in stdin. I have no idea whether it is my python script or my apache configuration causing this, though.

---


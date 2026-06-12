---
title: "Scripting help?"
date: 2008-01-18
forum: Server Platforms
---

### Post by Geran on 2008-01-18
Hi, 

We run a fairly large edubuntu system and our school now and after much experimenting and learning it now runs all the school's computer labs. We have one problem however. We have given teachers administrative rights to make new user names for their students. The problem is that when two teachers try to make users at the same time we get all sorts of funny issues. We were thinking of writing a new script to start the user manager instead of the one already in place and put it on their desktops and instruct them to use it. The goal of the script would be to see if users-admin is already running and then start it if it isn't, and display a no-go message if it is. I'm a bit short on the knowledge of how to make this script. 

Can some one help?

---

### Post by koenn on 2008-01-18
something along the lines of
```

#!/bin/bash
if ( ps -e | grep users-admin ); then 
   echo "users-admin already running, try again later" ;
   sleep 10 ;
   exit 1 ;
else 
   gksudo users-admin ;
fi

```

make it executable and create a launcher. 
if you have zenity, you can replace the echo statement with a dialog box.

---

### Post by HermanAB on 2008-01-18
I recommend using webmin.

Cheers,

Herman

---


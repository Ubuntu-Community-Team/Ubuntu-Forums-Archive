---
title: "how to understand that a server is running as some user"
date: 2009-09-03
forum: Server Platforms
---

### Post by hedonplay on 2009-09-03
Hello, there. 

What does it mean by saying a server is running as some user?

The server could be a web server, a ftp server and etc.

Does it mean someone connected with the server have the same rights or permissions on files and directories with the one the server is running as?

Any help is warmly appreciated.

---

### Post by dragos2 on 2009-09-03
Hmm, what are you talking about ?

---

### Post by rbishop on 2009-09-03
When a user connects to a server it is different on how the user's account will react in comparison to the user actually running the server.

Just because someone has access or credentials to login to a server doesn't mean that they can run or do anything they please.

Most servers are setup in such a way that each user has extremely limited capabilities, maybe being able to write in a certain directory, or just reading a directory.

Hope this helps a little bit.

---

### Post by Bachstelze on 2009-09-03
> **hedonplay said:**
> Does it mean someone connected with the server have the same rights or permissions on files and directories with the one the server is running as?

No, it is the server itself that has those rights. Remember that a server is a program like any other, so it's like when yu run nano, for example. In that case, nano will only be able to write to files that are writable by you, because it is running with your privileges. Likewise, when you say for example that Apache is running "as the www-data user" (which should be the case on Ubuntu), it means that Apache will be able to write to any file that is writable by the www-data user. It does not mean, however, that anyone can just connect to your web server and write to those files, because Apache is not a text editor like nano, it does not just give users a text field and a "Save" button. Apache is a web server, so what it does is... serving web pages. Of course, those web pages can be PHP scripts who tell Apache to write to a file, and if it is told so, it will do it. So it all boils down to this: Apache will not write to files (except log files, of course) unless a script tells it to. And if you have no such script on your server, then it won't.

---

### Post by hedonplay on 2009-09-03
> **dragos2 said:**
> Hmm, what are you talking about ?

Hi, drogos2,
I am sorry not to make my question understood, have you get a clearer idea after reading the others' replies?

---

### Post by hedonplay on 2009-09-03
> **HymnToLife said:**
>  Apache will not write to files (except log files, of course) unless a script tells it to. 

I like this sentence!

Rbishop, HymnTolife, Thanks very much for taking time answering my question so patiently.

If there is a file called do_something.php  in the root directory of [www.example.com](www.example.com), when a visitor(no matter who) sends a request like [http://www.example.com/do_something.php](http://www.example.com/do_something.php), the apache server will not take actions unless this file is set to be executable by the server. And if do_something.php need the visitor to be loged in to really do something, then it will tell the server to require something from the visitor.

Am I right?

---

### Post by Bachstelze on 2009-09-04
> **hedonplay said:**
> 
If there is a file called do_something.php  in the root directory of [www.example.com](www.example.com), when a visitor(no matter who) sends a request like [http://www.example.com/do_something.php](http://www.example.com/do_something.php), the apache server will not take actions unless this file is set to be executable by the server.

Be careful. Setting the execute bits at 0 (by using [font=monospace]chmod -x[/font] for example) on a PHP script will *not* make it unexecutable by Apache. The execute bit determines if you are permitted to execute the script from a shell, it has no effect on whether Apache can execute it or not.

```
firas@itsuki ~ % ls -l /home/www/itsuki.fkraiem.org/system.php
-rw-r-----  1 firas  www  3893 12 Jul  2008 /home/www/itsuki.fkraiem.org/system.php

```

Still the script works: [http://itsuki.fkraiem.org/system.php](http://itsuki.fkraiem.org/system.php)

> **hedonplay said:**
> And if do_something.php need the visitor to be loged in to really do something, then it will tell the server to require something from the visitor.

Am I right?

Yes.

---


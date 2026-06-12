---
title: "ModPerl::Util::exit: (120000) exit was called"
date: 2012-01-27
forum: Server Platforms
---

### Post by jamesa00789 on 2012-01-27
I'm trying to run mod_perl on Ubuntu 10.04. According to here: [http://perl.apache.org/docs/2.0/api/ModPerl/Util.html#C_exit_](http://perl.apache.org/docs/2.0/api/ModPerl/Util.html#C_exit_) it is OK to use exit();

I have my own subroutine called sub Exit {} that is in a separate file, thus:

```
require "exit.pl";
&Exit;

```

The subroutine does some clearing up stuff with a database, and then at the end it terminates the program by calling exit();

However I am getting this error:

ModPerl::Util::exit: (120000) exit was called at /home/...

Even though apparently this is perfectly OK to use this.

What's going on? I have spent over 2 days now browsing the internet trying to fix this problem and I still can't find a solution.

Thank you

---


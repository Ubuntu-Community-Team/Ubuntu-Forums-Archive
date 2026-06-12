---
title: "PHP $_FILES['file']['type'] now returns double quoted string"
date: 2012-01-02
forum: Server Platforms
---

### Post by zeroburn on 2012-01-02
Hello guys, 

yesterday I updated a bunch of packages on my server, and all of a sudden PHP started returning mime types on uploaded files as double quoted strings:

Before: $_FILES['file']['type'] would contain for example: application/pdf

Now: $_FILES['file']['type'] contains "application/pdf"

Of course this now breaks string comparisons like $_FILES['file']['type'] == "application/pdf"

Does anyone know if it's a bug with php, or if this information is fetched from the system, or even the browser? I'm blaming the PHP5 package because it is the only thing involved that I noticed being updated before this issue presented itself.

If anyone knows something about this I'd love to hear it. In the meantime I updated all my code to reflect this change and maintain retro-compatibility, but a change like this smells like a bug more than a new feature, so much code will break because of this.

My ubuntu server:
```
Linux 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:53 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS
```

My php version: 
```
PHP 5.3.2-1ubuntu4.11 with Suhosin-Patch (cli) (built: Dec 13 2011 18:49:27)
```

---

### Post by rsvancara on 2012-01-02
What does var_dump( $_FILES['file']['type'])  return?

---

### Post by zeroburn on 2012-01-02
string(17) ""application/pdf""

Exactly what I mentioned.

---

### Post by shubham1 on 2012-01-03
remove the double Qutotes

---

### Post by zeroburn on 2012-01-03
Of course I now trim the string before comparing it, I didn't ask for a solution. 

My point is that this is quite an unexpected, code-breaking, change. Even the documentation on the php.net site, along with its sample code would now fail. Once again my question: is this change promoted by PHP, or a bug introduced by third parties?

---

### Post by rsvancara on 2012-01-03
I agree, looks like a bug with PHP.

---

### Post by dazman19 on 2012-01-05
there was a bad version of php 5.3 which was something like 5.3.7 or something and it was quickly replaced with 5.3.8 it think it was out for like 4 or 5 days.. its possible you happened to install it at a time when they released the bad version.

---

### Post by zeroburn on 2012-01-05
It appears PHP had nothing to do with it. The culprit seems to be Firefox 9. I'm a sad panda -_-

---


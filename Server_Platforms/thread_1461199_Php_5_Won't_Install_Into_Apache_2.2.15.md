---
title: "Php 5 Won't Install Into Apache 2.2.15"
date: 2010-04-23
forum: Server Platforms
---

### Post by infamous-online on 2010-04-23
Hello all, I don't know if this is in the right section, if not move it to the right section thanks! Now, I've run into a problem and I don't know if it's apache or php or the combination of both. I can compile apache 2.2.15 just fine, but whenever I try to compile php 5.3.2 into my server, the first two steps work just fine but when I get to the make install part it shows the libphp5.so and it just stays there and I have to cancel the install because it won't finish. So has anybody else had this problem, and if so, how did you fix it? I'm using Ubuntu 9.04

---

### Post by _0R10N on 2010-04-25
Why are you compiling those?? they're available on the repositories. And installation/configuration details aren't up to you.

Kind regards!

_0R10N >>

---

### Post by bovcan on 2010-04-26
> **_0R10N said:**
> Why are you compiling those?? they're available on the repositories. And installation/configuration details aren't up to you.

Kind regards!

_0R10N >>

Really? Can you post link of repositories for Apache 2.2.15 for Ubuntu 9.10?
Thanks

---

### Post by lisati on 2010-04-27
Moved to "Server Platforms"

When I installed PHP on my [server]("http://lisati.myftp.org/status") I didn't need to compile or add any repositries when I set up PHP.


Suggested reading: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Bachstelze on 2010-04-27
> **bovcan said:**
> Really? Can you post link of repositories for Apache 2.2.15 for Ubuntu 9.10?
Thanks

Do you *really* need 2.2.15? The Lucid repos have 2.2.14, which should be good enough.

---

### Post by _0R10N on 2010-04-28
Excuse my ignorance respecting Apache-PHP compilation, but can't you just compile and install apache, and after that proceed to aptitude install php?.
The version available on the repositories isn't the 2.2.15. But, as Bachstelze said, is there an concrete reason for you to install that specific version?. Remember that Apache is quite stable, previous releases (like 2.2.11) work great.

Kind regards!

_0R10N >>

---


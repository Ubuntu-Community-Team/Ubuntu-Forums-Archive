---
title: "(D)DoS Deflate"
date: 2009-07-27
forum: Security
---

### Post by AADude on 2009-07-27
Whenever I try to run it, I get:
```

[: 85: /usr/local/ddos/ddos.conf: unexpected operator
DDoS-Deflate version 0.6
Copyright (C) 2005, Zaf <zaf@vsnl.com>

$CONF not found.

```

Yes, I do have the ddos.conf file (with text inside) located at /usr/local/ddos/.

---

### Post by AADude on 2009-07-27
I suppose no one has any idea as to the solution :x

---

### Post by dragos2 on 2009-07-28
> **AADude said:**
> I suppose no one has any idea as to the solution :x


Please
```

ls -al /usr/local/ddos/ddos.conf

```

---

### Post by AADude on 2009-07-28
> **dragos2 said:**
> Please
```

ls -al /usr/local/ddos/ddos.conf

```
The output:
```

-rwx------ 1 root root 987 2009-07-27 12:50 /usr/local/ddos/ddos.conf

```

---

### Post by The Tronyx on 2009-07-28
> 
[: 85: /usr/local/ddos/ddos.conf: unexpected operator


The first thing to notice is that it has a problem with something on line 85 if I am reading that correctly.

Next, it also says, "$CONF not found."  That isn't necessarily saying that /usr/local/ddos/ddos.conf isn't found.  $CONF indicates that it is looking for whatever it is that occupies the variable $CONF in the configuration file.  My recommendation would first be to find the first occurrence of $CONF in the file and see what it is looking for.  You should then check out what is happening on line 85.  Lastly, check and see if there is a way that you can manually specify the location of the configuration file and if so, do it at startup.

---

### Post by AADude on 2009-07-28
Line 85:
```

load_conf

```

which calls the function:
```

load_conf()
{
	CONF="/usr/local/ddos/ddos.conf"
	if [ -f "$CONF" ] && [ ! "$CONF" ==	"" ]; then
		source $CONF
	else
		head
		echo "\$CONF not found."
		exit 1
	fi
}

```

The CONF variable is set to the correct location.

---

### Post by Tiaquis on 2009-07-31
Hi i had the same problem under jaunty, simple solution is to open /usr/local/ddos/ddos.sh 

and change the shebang line from /bin/sh to /bin/bash so your first line in ddos.sh should be #!/bin/bash that worked for my afaik

I think the problem is that /bin/sh is linked to /bin/dash and the syntax is not the same as bash.

---

### Post by dragos2 on 2009-07-31
> **Tiaquis said:**
> Hi i had the same problem under jaunty, simple solution is to open /usr/local/ddos/ddos.sh 

and change the shebang line from /bin/sh to /bin/bash so your first line in ddos.sh should be #!/bin/bash that worked for my afaik

I think the problem is that /bin/sh is linked to /bin/dash and the syntax is not the same as bash.

Damn you beat me to it. You are right. ubuntu uses sh-> dash instead of sh-> bash.

He needs to rebuild the symbolic link and most likely will work.

---

### Post by envis on 2010-06-15
> **Tiaquis said:**
> Hi i had the same problem under jaunty, simple solution is to open /usr/local/ddos/ddos.sh 

and change the shebang line from /bin/sh to /bin/bash so your first line in ddos.sh should be #!/bin/bash that worked for my afaik

I think the problem is that /bin/sh is linked to /bin/dash and the syntax is not the same as bash.


Thank you :!:

---

### Post by fher98 on 2011-01-11
Hello, I had this working for around a year, an today all of the sudden... im seen this error.. why?

---

### Post by envis on 2013-02-10
actually changing the first line to

#!/bin/bash

was working in the past I think, I even see I said thank you... must have worked... but now Im trying to get this to work on my new server.. I have the same error again, but now changing the first line to #!/bin/bash has no effect anymore.. the same error stays... I seem to be under DDOS attack, just cant get DDOS deflate to run....

---

### Post by wildmanne39 on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


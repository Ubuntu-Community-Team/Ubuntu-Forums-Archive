---
title: "Running a php script from the crontab"
date: 2007-05-25
forum: Server Platforms
---

### Post by yellowtip on 2007-05-25
Hi everybody,

I'm running Ubunutu Dapper Server and have php setup as a module of Apache. That is running fine.

However, I now have to run some php script from the crontab.

My research tells me that if you have php installed as an apache module that it's simply not possible to run a php script from the command line/crontab.

Is this correct?

I found this solution that would let Lynxx load the php script via the crontab, but that seems to me like a very ugly solution.

Can anybody help please?

Thank you!

---

### Post by gombadi on 2007-05-25
Depending if you want php5 or php4 change the following accordingly

Open a terminal and do
```

sudo apt-get install php5-cli

```

Use apt-cache show php5-cli to see what the package does/contains.

That will install the php command interpreter so all you need to do is add the following as the first line to the script you want to run from cron
```

#!/usr/bin/php5

```

---

### Post by yellowtip on 2007-05-26
That's fantastic! Thank you very much for that suggestion.

Now for the next problem. When I execute the script in the command line (to test) I get the following error:

"Your PHP installation does not have MySQL support. Please enable MySQL support in PHP or ask your web host to do so for you"

How do I enable MySQL support for php4-cli ?

Thanks in advance!

---

### Post by yellowtip on 2007-05-26
Here's what I've done so far... without success.. ](*,)

- I have changed the /etc/php4/cgi/php.ini to add extension=mysql.so
- I have reinstalled php4-mysql
- I have restarted Apache (don't ask me why)

But none of the above steps get rid of the error:
Your PHP installation does not have MySQL support. Please enable MySQL support in PHP or ask your web host to do so for you.

Just to be clear, on the Apache side everything runs fine. My mysql/php powered websites are running without any problem. I just can't run a php script that requires mysql access from the command line.

Could someone please help me out? This is driving me crazy!  ](*,)

Thanks!

---

### Post by yellowtip on 2007-05-26
Problem solved!

I was editing the /etc/php4/cgi/php.ini file .....WRONG!

I should have been editing the /etc/php4/cli/php.ini file.

All works fine now. =D>

---


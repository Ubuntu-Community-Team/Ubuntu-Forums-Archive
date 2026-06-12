---
title: "is there anyway to detect output of a command inside a script?"
date: 2012-08-17
forum: Server Platforms
---

### Post by legolas_w on 2012-08-17
Hi, 

is there any standard way to detect if a command is executed successfully or not when invoking them from whitin a script ? for example if I execute:
```

mkdir abc

```

is it possible to know if the command is executed successfully or it is failed? Another example command that I want to know if is executed successfully is as follow:

```

sudo apt-get install puppet

```


Thanks.

---

### Post by steeldriver on 2012-08-17
you should be able to look at the exit status of the command using the builtin $? variable

[http://tldp.org/LDP/abs/html/exit-status.html](http://tldp.org/LDP/abs/html/exit-status.html)

---

### Post by Habitual on 2012-08-17
[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/exitcodes.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/exitcodes.html) is something to read up on while others here can explain the process better than I.

---

### Post by Lars Noodén on 2012-08-17
The program will always return a value (exit code) when it completes.  If the program was successful, the value will be 0.

There are several ways to work with that in the shell.

```

mkdir abc && echo Succeeded || echo Failed

```

Or

```

if mkdir abc; then
  echo Succeeded;
else
  echo Failed;
fi

```

---

### Post by SeijiSensei on 2012-08-17
I recommend using "mkdir -p directory_name" in scripts.  That will force the creation of the directory, and of any parent directories as well.  So, if you used "mkdir -p /path/to/dir" you'd create /path, /path/to, and /path/to/dir in one command and ensure that all the parents exist.

---


---
title: "Perl problem - how to run MySQL benchmark on 8.10?"
date: 2009-01-02
forum: Server Platforms
---

### Post by Bike-and-snow on 2009-01-02
Hello

I have installed 8.10 Server on a test machine.

I have MySQL installed and running.

I want to run the MySQL benchmark that comes with the source code.

I downloaded the source code as follows:
```
apt-get source mysql-server
```

The source code is in my home directory (I am logged in as root).

However when I run it:
```
perl run-all-tests.sh
```

I get this output:
```
Can't exec @PERL@ at run-all-tests.sh line 1.
```

I have checked to see if Perl is installed and it is.

Does anyone know how I can run it?

Thanks

---

### Post by unutbu on 2009-01-02
Since the script name ends in ".sh",  I'm guessing it is a shell script, rather than a perl script.

What happens if you run ```


./run-all-tests.sh
```

If that doesn't work, please post the error message, and the output of 
```

head -n 50 run-all-tests.sh
```

---

### Post by Bike-and-snow on 2009-01-02
Hello unutbu

Yes, I did try that as well. I get:

```
-bash: ./run-all-tests.sh: @PERL@: bad interpreter: No such file or directory
```

I've found a solution - turns out Ubuntu package the test with the MySQL server package.

I've found it here:
/usr/share/mysql/sql-bench

Thanks.

---


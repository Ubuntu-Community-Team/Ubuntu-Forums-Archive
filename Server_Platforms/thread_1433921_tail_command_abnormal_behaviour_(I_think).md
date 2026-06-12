---
title: "tail command abnormal behaviour (I think)"
date: 2010-03-19
forum: Server Platforms
---

### Post by azacan on 2010-03-19
Hi, 

I am very new to Ubuntu and when performing the comand
tail +5  file    (to print lines from 5th on) it doesn´t work for my Ubuntu Server 9.10
I guess I am doing something wrong, but not sure. The file has 30 lines. It works -5 or -n5 but also dont +n5

$tail +5 fichero30lin 
tail: no se puede abrir Â«+5Â» para lectura: No existe el fichero Ã³ directorio
==> fichero30lin <==
Linea num: 21
Linea num: 22
Linea num: 23
Linea num: 24
Linea num: 25
Linea num: 26
Linea num: 27
Linea num: 28
Linea num: 29
Linea num: 30
$

The error, translated to english is: 
tail: it can not be openned Â«+5Â» for reading: Does not exist the file Ã³ directory

Any idea what could be happening??

Thanks!
BR

---

### Post by gombadi on 2010-03-19
> 
tail +5 file (to print lines from 5th on) it doesn´t work for my Ubuntu Server 9.10


The following work
```

tail -n +5 filename
tail --lines=+5 filename

```

With just a +5 then tail thinks it is a file name and looks for a file with that name.

---

### Post by cdenley on 2010-03-19
```

tail -n +5 fichero30lin

```

---

### Post by azacan on 2010-03-19
Thanks very much!
The 2 options you provided work. 
But is normal the behaviou when executing the way I said? I an lot of manuals, forums and even in the man page for tail is said like that (tail +number file)

BR

---

### Post by cdenley on 2010-03-19
> **azacan said:**
> Thanks very much!
The 2 options you provided work. 
But is normal the behaviou when executing the way I said? I an lot of manuals, forums and even in the man page for tail is said like that (tail +number file)

BR
It said that indented under the bolded text "-n, --lines=N". That means it is describing the argument which follows either "-n " or --lines=".

---

### Post by azacan on 2010-03-19
Thanks cdenley ;-)

---


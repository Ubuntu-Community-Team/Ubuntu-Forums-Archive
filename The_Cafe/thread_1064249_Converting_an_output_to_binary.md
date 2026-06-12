---
title: "Converting an output to binary"
date: 2009-02-08
forum: The Cafe
---

### Post by 5BallJuggler on 2009-02-08
Can anyone help, i'd like the output from this command in a binary format please.
[B]
date -d now +%s[/B]

Thanks in advance
Phil

---

### Post by sisco311 on 2009-02-08
> **5BallJuggler said:**
> Can anyone help, i'd like the output from this command in a binary format please.
[B]
date -d now +%s[/B]

Thanks in advance
Phil

You can use bc to convert a number to base 2.
Homework?

---

### Post by 5BallJuggler on 2009-02-08
;)
not homework.

i want to display "unix" time in dec and binary in conky or a screenlet.

how would i use bc?

---

### Post by sisco311 on 2009-02-08
```
echo $(echo "obase=2; $(date +%s)" | bc)
```

---

### Post by Dr Small on 2009-02-08
> **5BallJuggler said:**
> ;)
not homework.

i want to display "unix" time in dec and binary in conky or a screenlet.

how would i use bc?
```
[drsmall@darkghost ~]$ echo 12*12 | bc
144
```

---

### Post by 5BallJuggler on 2009-02-08
> **Dr Small said:**
> ```
[drsmall@darkghost ~]$ echo 12*12 | bc
144
```

> **sisco311 said:**
> ```
echo $(echo "obase=2; $(date +%s)" | bc)
```

thanks very much guys, works a treat!:D

---


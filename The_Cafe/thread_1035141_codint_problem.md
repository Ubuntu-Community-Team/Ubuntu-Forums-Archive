---
title: "codint problem"
date: 2009-01-09
forum: The Cafe
---

### Post by maruf10 on 2009-01-09
i want to print the even number ranging from 1 to 100
here is the code
i am unable to find the bug 
please help
thanks in advance

```

for (( i=1 ; i<=100 ; i++ ))
do
   a=`expr $i%2`
    if test $a -eq 0
      then
        echo $i
    fi
done



```

---

### Post by saulgoode on 2009-01-09
Try putting spaces into your function: `expr $i % 2`

---


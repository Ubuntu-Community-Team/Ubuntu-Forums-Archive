---
title: "[SOLVED] What do you use for Net Diagram in ASCII"
date: 2007-04-03
forum: The Cafe
---

### Post by victorbrca on 2007-04-03
I was wondering today at work if there is a standard for drawing network diagrams in ASCII.

  I was drawing a client's network on my notepad and found myself with too many ways of doing it...

  Anyone uses a standard or do you usually just write it as you want it???

  These are the examples I came up with for the same network:

```

+--+          
|RT| ------ |Server| ------- |Switch| --------- |PC|           
+--+
```

```

             (RT) -------- [SV]
                             |
                             |
                            <SW>   
                               \
                                \ 
                                 \
                                 PCS
```


```
      (RT) 
         \
          \
          [SV]
            \          
             \         
            <SW>   
               \
                \ 
                PC
```



```
Router
  |
  | 
Windows XP - 10/100 - 
     |
     |
     |
Switch - 10/100
            |
            |
            |
          PCs - 10/100
```



Vic.

---


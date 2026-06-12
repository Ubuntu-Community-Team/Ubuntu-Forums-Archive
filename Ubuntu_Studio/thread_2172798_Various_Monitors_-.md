---
title: "Various Monitors -"
date: 2013-09-06
forum: Ubuntu Studio
---

### Post by Libertad77 on 2013-09-06
hi all,

I'm currently struggling to get my 3 monitors to work in ubuntu studio 
12.04. Any good samaritano care to help me out to see if I can solve 
this?
I have two graphic cards (onboard mother graphic -ati- and one that I 
bought -nvidia-). I know that it was NOT a good idea putting these two 
cards in the same PC but I was succesfull in making it work in Win 
without much hassle so I'm sure I'm doing something wrong in ubuntu 
studio.
If there is any info that I left out, please let me know so I can post 
it.
Thanks for your time!
cheerss

---

### Post by jejeman on 2013-09-06
This is not strictly Ubuntu studio related, so maybe transfering the topic to general support would be better. 
Anyway, give
```
lspci -knn | grep VGA -A 4
```

---


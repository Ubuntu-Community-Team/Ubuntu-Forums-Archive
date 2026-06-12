---
title: "Make dtb tree problem"
date: 2012-09-14
forum: Server Platforms
---

### Post by nikibg on 2012-09-14
Hello, again i have problem with make comand and i need help ](*,)

I wanna make image of one linux distro i made it but i need to make .dtb for it 
when i write  make ```
men_mm50.dtb
``` it returns me 

```
dtc -O dtb -o arch/powerpc/boot/men_mm50.dtb -b 0  /10mm50-90/linux-2.6.24.7/arch/powerpc/boot/dts/men_mm50.dts
make[1]: dtc: Command not found
make[1]: *** [arch/powerpc/boot/men_mm50.dtb] Error 127
```

Where is the problem . Pls help me

---

### Post by SlugSlug on 2012-09-14
am not sure about dtc but I'd try ```
sudo apt-get install dtc
```

am not at a box so I cnt look

---

### Post by nikibg on 2012-09-17
10x it was a stupid mistake i was del  one file :lolflag:

---


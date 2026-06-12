---
title: "i7-10510U CPU Pinning Doesn't Make Sense"
date: 2022-01-04
forum: Virtualisation
---

### Post by jvuabamlre on 2022-01-04
i7-10510U (4C/8T)
HT pairs doesn't go like 0-4 or 1,5... Rather they seem to be: 0,1 - 2,3 - 4,5 - 6,7  (using lpsc -e)

When I emulatorpin+iothread to the first cpu pair (0,1)
     
I get worse performance than 
     

(0,4) or EVEN (0,5). Doesn't make sense because 0,4 and 0,5 both give me same performance higher than 0,1.

     
How can this happen?

---


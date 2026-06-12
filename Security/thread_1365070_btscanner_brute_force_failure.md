---
title: "btscanner brute force failure??"
date: 2009-12-26
forum: Security
---

### Post by Trisket on 2009-12-26
when i try and use btscanner brute force scanner i get this error: 


c_s.so.1
        00ebb000-00fdd000 r-xp 00000000 08:05 6026       /usr/lib/libxml2.so.2.7.5
  00fdd000-00fde000 ---p 00122000 08:05 6026       /usr/lib/libxml2.so.2.7.5
                                                                            00fde000-00fe2000 r--p 00122000 08:05 6026       /usr/lib/libxml2.so.2.7.5
                                                                      00fe2000-00fe3000 rw-p 00126000 08:05 6026       /usr/lib/libxml2.so.2.7.5
                                                                00fe3000-00fe4000 rw-p 00000000 00:00 0 
                        08048000-08055000 r-xp 00000000 08:05 4709       /usr/bin/btscanner
           08055000-08056000 r--p 0000d000 08:05 4709       /usr/bin/btscanner
                                                                              08056000-08057000 rw-p 0000e000 08:05 4709       /usr/bin/btscanner
                                                                 09b32000-09bb4000 rw-p 00000000 00:00 0          [heap]
                                        b7707000-b770b000 rw-p 00000000 00:00 0 
b771b000-b771e000 rw-p 00000000 00:00 0 
                                        bf9d6000-bf9eb000 rw-p 00000000 00:00 0          [stack]
                Aborted




any ideas??

---

### Post by dvirdc on 2010-01-11
does anyone know how to solve this?
i found a patch for that somewhere in another forum while googling the problem, but i dont know how to apply/add the patch on the existing version of btscanner (2.1-4-karmic).

any suggestions?
cheers

---


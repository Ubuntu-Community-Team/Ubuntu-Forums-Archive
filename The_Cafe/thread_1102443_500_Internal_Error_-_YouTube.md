---
title: "500 Internal Error - YouTube"
date: 2009-03-21
forum: The Cafe
---

### Post by altonbr on 2009-03-21
I'm hoping a computer programmer can tell me what YouTube is trying to say with this error message:

> 500 Internal Server Error

Sorry, something went wrong.

A team of highly trained monkeys has been dispatched to deal with this situation.
Also, please include the following information in your error report:

aOVMYYvWvxktKY_y6AsqNIiqxQLtC4oW_ZhpufDsubmx6xKYjDgaEzeDg0oH
Cq8dMHjKeugWXP1dc6p5wEBM29LeUOqMu-Ha4Mji_Y_EdWx-dmmaYYhk7RWC
-WcgnSq5gazcNqFvT64uYH4sHmW_sKfeER2Pp81qDqDb4OAkUbhDLODi5WZA
w_gJOczWitstJkRJso43rWBOCekcJFcYTDloiGtnQUNeUmGqgQDna0RQmJf2
tMbLkBFkY0WnyI3U0t1aaMOg-4hmolfJOrsFYlGAsaQX_6_luFsqDScgB3pQ
uulMRXviV9k4i2XYe2brXOxGhseAKLi1xj32K6ZHd0U23yUTFSkjHfBxexN9
Yx2ebMdyaNylrvWkEbpJCMZ3oGluW33lp92xTjkoaRQgbn2znXmPnBn0_D5d
m0LAtpEQyMx5lhaQtElWN-aF-ieeIeinLGngZ5OcomeoWpjzujS33CtwW6aZ
JFftqvgTTZC1i9PxvDHWWyqO6wG_SWuC4gSSvcKAX9C5ZK6EKUgZnyDobsnc
l2NRzSoSTslUXuKjaXo2DhKz1lAtk_WMEiwxeDjyhjtyk2F0MC1UnHjPaD0i
VvHkpXdtjaPmn58AQAL6bbAUWavuehZRagunETvhsIwwp3M7u0oi9jPJnASq
xpymkcQBML_fGqIe9HTMM3rwvJ3emtI_0gTm9mN8nuBv6ndLTcsX7GHK17x7
3fJOeOAYrWUak0Iz2RThpZvgLF_GA0H_qz4mAyqafCxxU80R9wunU-8eZMNy
SekxFt-OCumFK-rysVtF1Khcrvd5-YNnJEs7bCFS3ae5904UAfrj_rLKES3-
y_BwAa3CPrxT9ADNmXbx15H0iPiG04UQ9cDMDgM8ZZ_xGf3YCJEmrz8n9ZG7
iZytfCMDIk38CyU5B1meQdmyx-BSzaCuZBK4hZlv5L0ILkhFOawHUHGe3txS
T345RcU2fKSbORWfZZa3CU1Vv3kXCKvS91zS9nXJ_hsnFT3DsIhMKZFb2gpY
NUtiOmSTl15OJ30bo6By0x-i0l0DmWM83h5ehiJy7sliw8d5mcRx0foLANIs
6g_orucSaCB2PsbHG6VPrIXSrm8BWN0YcFI2_1yuFADCrVZ8vZSJ3sJz63I7
nqzXT0BurjMZY4pE9QxzSshexL9kRHD4-Psu_D50C0j60mbE6F-ifZKjW-GK
668OvTYibtuv1YN8Tlufsr7twDrLC2UGDwW8A3VGRTOFqHcKJxnZbBdvPNyu
WLelpHTvmQdjwI19JGYy2s6igLSu3Lg4vZOiTjqHTzZYxBB9AE4iTZoBVn32
RvSquJldiSN6jWK8EvFVh8itl8xTR_ZfvqpxrumJAXS140B1DjIcHmyUPURk
sD9b0B4nFKiuPVO5iYJ09AcQfQnMdUxbab81y1v7rNho54KckGvpaed1Ik5W
FRoHuU37TtE1gftsP-0m_7sZCqxn7azG2wT1UKQLgMDky79l48ArT1IE4UyC
rIs4PJiq9-MWjf4DWMwcWwjhhK_h000KqiYIu8_ULr9XxfeffuCt9PMHY0Bz
-NFaQYPNRm4_PNnLwlBR-9-McCYOfBcORtf2G50PMUwuaWJWLummhsA5gLY4
2d9BKUNxrjvJS3jjUS3bbnzAadm0in8rMSqU1MtCGn-beH0m5ZYfRIB3Ry2m
ZKzfLod8Air7t6GPZ1hT7oEgYf8tMEeYd94-_A==

I assumed it was encoded in base64 so I tried base64_decode() in PHP, buy I think it's just a gibberish alphanumeric string.

Can someone tell me?

---

### Post by -grubby on 2009-03-21
I have a feeling they don't want you to be viewing the error report.

---

### Post by kavon89 on 2009-03-21
Thats the root password for the server which had an error.

---

### Post by altonbr on 2009-03-22
Salted, hashed, encrypted and obfuscated. Figured.

---


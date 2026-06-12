---
title: "Ran rkhunter and received warnings."
date: 2009-12-14
forum: Security
---

### Post by running_rabbit07 on 2009-12-14
I received these 2 warnings. Should I be worried? ```
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/unhide-linux26                                 [ Warning ] 

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]

```

---

### Post by HermanAB on 2009-12-14
Rootkit hunter type programs are basically a waste of time.  Relax and enjoy your nice secure system.

---

### Post by BkkBonanza on 2009-12-14
According to google unhide is a rootkit detection tool used to find hidden processes. Sounds like you're tripping over yourself looking for something wrong. It's not installed by default so presumably either you installed it or maybe it came with rkhunter.

I tend to agree with HermanAB. I mean if I were a rootkit writer nowadays the first thing I'd do once gaining root is find and neuter any rootkit hunter tools.

---

### Post by running_rabbit07 on 2009-12-14
> **BkkBonaza said:**
> According to google unhide is a rootkit detection tool used to find hidden processes. Sounds like you're tripping over yourself looking for something wrong. It's not installed by default so presumably either you installed it or maybe it came with rkhunter.

I tend to agree with HermanAB. I mean if I were a rootkit writer nowadays the first thing I'd do once gaining root is find and neuter any rootkit hunter tools.

 After reading your reply I got the bright idea to search Synaptic for unhide. It is there. It is either installed by default or rkhunter installed it.

Thanks for the replies. This was my first time running it, so I didn't know what to expect.

---


---
title: "snort not detected all nmap quick scan"
date: 2013-09-09
forum: Security
---

### Post by Leo Matheus on 2013-09-09
Hello guys,

Im testing my snort sensor of my IDS by doing some port scans using nmap. I have done some scans with the options -T4 -F, and i did 10 port scan, one after another, but snort doesn't detect all of them, just 7. i dont know why snort didn"t detect all of the it is a simple scan ( same as quick scan in Zenmap).
Any idea why he didn't detect it?

thanks Leo.

---

### Post by unspawn on 2013-09-10
> **Leo Matheus said:**
> Any idea why he didn't detect it?
No, because we don't know your Snort configuration, how (from where) you scanned and what "just 7" means.

---

### Post by Leo Matheus on 2013-09-10
im using snort 2.9.3.1 on ubuntu 12.04 LTS, i make the scan directly on the IDS(192.168.xx.yy) from another network(192.168.zz.yy), some think like that(192.168.zz.yy -> 192.168.zz.yy)
and the "just 7" was he detect 7 of the 10 scans i made

---

### Post by unspawn on 2013-09-12
> **Leo Matheus said:**
> im using snort 2.9.3.1 on ubuntu 12.04 LTS, i make the scan directly on the IDS(192.168.xx.yy) from another network(192.168.zz.yy), some think like that(192.168.zz.yy -> 192.168.zz.yy)
and the "just 7" was he detect 7 of the 10 scans i made
I'm sorry but with that nfo we still can't determine why. I suggest posting:
- the complete command line Snort runs with,
- attaching your snort.conf (that's 'grep -v ^# snort.conf|grep .;'),
- any other (BPF, suppression, etc, etc) filters you use,
- the Snort log showing the scan reporting,
- the complete command line nmap ran with.

*Next time please try to assess what's needed beforehand. That makes threads more efficient. And usually more nfo is better.

---


---
title: "Comodo not installing ~ dependency not satisfiable"
date: 2020-09-09
forum: Security
---

### Post by lelmst on 2020-09-09
If I try to install Comodo antivirus I get an error saying "dependencies are not satisfiable". I know this is referring to an earlier version of libssl that comodo needs but I'm not sure which one the newest version uses as most posts across forums are from multiple years ago. Do you know which one the latest Comodo uses? Could downgrading libssl cause any problems with other software? Should I just get something from the repository instead, one that has the real time protection that clamav fails to provide?

---

### Post by CelticWarrior on 2020-09-09
Downgrading libssl is definitely a problem. By doing that you're creating a real security problem just to get a perceived yet false security of a lousy AV installed. And why do you think you need real time "protection" from Windows virus in Ubuntu? Yes, that's all it does.

---

### Post by lelmst on 2020-09-09
I see
I noticed this same sentiment wrt libssl in a couple threads elsewhere.
Comodo's linux home (their only free product) isn't really that bad, it actually covers linux malware too, but sophos is far superior and doesn't have this problem, but they discontinued theirs 2 months ago. 
Anyway, I was looking for something with real time protection (clamav is terrible at that) and good heuristics detection that comodo could maybe provide idk.
The question now is if the repository has something that could do those 2 things, as comodo is out of the question

---

### Post by lelmst on 2020-09-09
What kind of risk comes from downgrading libssl? Just curious in case I could warn other people not to do that

---

### Post by CelticWarrior on 2020-09-09
[https://www.openssl.org/news/vulnerabilities.html](https://www.openssl.org/news/vulnerabilities.html)

A little bit dense but compiles all the security problems found and corrections.

---

### Post by EuclideanCoffee on 2020-09-09
Symantec has real time protection called auto protect. It works a little too well in my opinion. :)

---


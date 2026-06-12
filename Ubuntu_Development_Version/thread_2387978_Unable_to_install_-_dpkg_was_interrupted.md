---
title: "Unable to install - dpkg was interrupted"
date: 2018-03-26
forum: Ubuntu Development Version
---

### Post by atypical-skeptic on 2018-03-26
Hello all,
I checked the forums and noticed similar posts, but none of the solutions seemed to work for me. 
I am currently using 18.04. I understand its not recommended to use for primary computers just yet, but for some reason, other versions of ubuntu would fail to install on my computer. I am new to ubuntu, as well. 
Anyhow, I have been getting the following prompt whenever I attempt to install something.

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Any and all help is greatly appreciated.

---

### Post by wildmanne39 on 2018-03-26
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by wildmanne39 on 2018-03-26
Did you run:
```
sudo dpkg --configure -a
```
as stated in the error message? If not please do so.

Thanks

---

### Post by QIII on 2018-03-26
Hello!

Did you attempt to run 

```
sudo dpkg --configure -a
```

in the terminal?

What was the result?

---

### Post by atypical-skeptic on 2018-03-26
Solved!
I did this:


```
E:
sudo dpkg --configure -a

```

And also opened up synaptic and its good to go

Edit: I initially did this, but it failed. After a reboot of my computer and updating repositories, it worked. 
Thank you all.

---

### Post by wildmanne39 on 2018-03-26
Glad it is working, please use thread tools at the top of the page to mark the thread solved.

Thanks

---


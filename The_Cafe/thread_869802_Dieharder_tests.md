---
title: "Dieharder tests"
date: 2008-07-25
forum: The Cafe
---

### Post by kedarm on 2008-07-25
Hi!

This is not related to Ubuntu as such, but I am hoping for help anyway.

When using the dieharder software ([http://www.phy.duke.edu/~rgb/General/dieharder.php_](http://www.phy.duke.edu/~rgb/General/dieharder.php_)) to check the quality of a random number generator (rng), how does one use a file to input data?

ie. if I have a rng and use it to produce 1000000 random numbers and store them in a file - input.txt, how do I use the dieharder program to run its tests on these random numbers?

Thanks

---

### Post by collinstocks on 2008-11-24
dieharder -g 66 -f ./myfile.bin

if it is a binary file, or

dieharder -g 65 -f ./myfile.txt

if you have armored it in some way. You have to state how you armored it at the top of the file, and I'm not exactly sure how you do that.

---


---
title: "Computational Desktop"
date: 2011-06-27
forum: The Cafe
---

### Post by mklcst on 2011-06-27
Hello guys, I do quantitative research and I want build a desktop for my works, the main use is computational Matlab (with CUDA), Octave, R, C + + etc..
 I had in mind this basic configuration:
 - 3.4 GHz Intel Core i7 2600K + Powerline Hyper Fan TX3
 - Motherboard ASUS RAMPAGE III GENE
 - Corsair Dominator DHX PC Memory Pro 6 x 4 GB DDR3-1333 - PC3-10600 - CL9 (CMP24GX3M6A1333C9)
 - ASUS GeForce GTX 560

and more general components.
 - Case + Power Supply
 - 2 - 2TB SATA2 32MB CACHE HARD DISK
 - Network adapter
 - Sound Card

 I would like to know what you think (advice & improvements), especially in the basic conf, Should have driver compatibility issues?
Thank you

---

### Post by Lars Noodén on 2011-06-27
You'll have to test with the specific hardware you have, but there should be little or no problem with hardware compatibility.  

You might look at Kubuntu, Xubuntu or Lubuntu.  The defaults are a little different than Ubuntu, but you might like them better.

---

### Post by 3Miro on 2011-06-27
1. I want that configurations.

2. For scientific computing with the GPU, get as much RAM as possible.

3. EVGA usually have more RAM than others, but I am not sure if they will be of decent quality. Some time ago I bought a motherboard and a video card from EVGA, one died in 6 months the other one lasted almost a year. I am sure there are people that have never had issues with them, but I would do a lot of research before getting EVGA again.

---

### Post by Bandit on 2011-06-28
> **mklcst said:**
> Hello guys, I do quantitative research and I want build a desktop for my works, the main use is computational Matlab (with CUDA), Octave, R, C + + etc..
 I had in mind this basic configuration:
 - 3.4 GHz Intel Core i7 2600K + Powerline Hyper Fan TX3
 - Motherboard ASUS RAMPAGE III GENE
 - Corsair Dominator DHX PC Memory Pro 6 x 4 GB DDR3-1333 - PC3-10600 - CL9 (CMP24GX3M6A1333C9)
 - ASUS GeForce GTX 560

and more general components.
 - Case + Power Supply
 - 2 - 2TB SATA2 32MB CACHE HARD DISK
 - Network adapter
 - Sound Card

 I would like to know what you think (advice & improvements), especially in the basic conf, Should have driver compatibility issues?
Thank you

If you have extra machines setting around or a home with networked computers. Take a look into this. Its actually not that hard to setup.
[http://en.wikipedia.org/wiki/Beowulf_cluster](http://en.wikipedia.org/wiki/Beowulf_cluster)

---

### Post by Bandit on 2011-06-28
> **3Miro said:**
> 1. I want that configurations.

2. For scientific computing with the GPU, get as much RAM as possible.

3. EVGA usually have more RAM than others, but I am not sure if they will be of decent quality. Some time ago I bought a motherboard and a video card from EVGA, one died in 6 months the other one lasted almost a year. I am sure there are people that have never had issues with them, but I would do a lot of research before getting EVGA again.

I have had similar issues with EVGA cards as well.

---

### Post by mklcst on 2011-06-28
guys, thank you very much for your reply!

@3miro: do you think I have to buy the one with 2gb? or I can install 2?

@Bandit: thank you for the suggestion, I will definitely consider it in the future ;)

---

### Post by 3Miro on 2011-06-28
A note on the Beowulf cluster: when programming in parallel, people usually make the assumption that all the cluster-nodes will have the same power. Supercomputers usually have a bunch of identical nodes. If you have machines with different power, then you have to make specific code to take that into considerations (i.e. instead of splitting the problem 50/50, you will have to split it 70/30 or something). I would not recommend making a cluster with nodes of different power. Furthermore, setting up MATLAB for a cluster is hard and expensive (MATLAB is commercial).

For the 2 GPU problem: if you use 2 x 1GB cards in SLI, then you get only 1GB of RAM as the two cards have to mirror their memory. If you use the two cards as stand-alone, you will have 2 x 1GB of RAM, but it is still not the same as 2GB of RAM. In your program, you will have to keep track of which GPU has what data and you may have to move data from one GPU to the other (the whole point of large RAM is to avoid moving data around). You will have to either make the code capable of handling any number of GPU (which is hard) or make it machine specific for 2 GPU machines only (which will decrease the value of your code as you will need a special machine to run it). Also, I am not sure if MATLAB can take advantage of 2 GPUs or would it use just one of them.

I am not saying that 1GB isn't enough, this depends on the specific problems that you would be working on. I am just giving the advice that if you plan on doing a lot of CUDA/OpenCL, then more video RAM is preferable.

---


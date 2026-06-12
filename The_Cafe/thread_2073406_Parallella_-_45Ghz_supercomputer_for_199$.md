---
title: "Parallella - 45Ghz supercomputer for 199$"
date: 2012-10-19
forum: The Cafe
---

### Post by Hyperfang8 on 2012-10-19
A kickstarter link: [http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone)
Basicly they will opensource thei software and hardware if goal is reached.
$199 version comes with 64 cores and ~45Ghz(700Mhz arm9x64)....
$99 version comes with only 16 cores but thats still alot!
It also comes with ubuntu and software development tools.
This guy also points to some realy important questions about hardware and were its headed.
There is only about 8days left and they still have only 400,000$/750,000$ .
I would realy like to see this project come to reality(i'm not payed for this post so its not spam).
Help spread the word.
I would like to write more but there is not anything i can think off :) .

---

### Post by PC_load_letter on 2012-10-19
Simply AWESOME! If this becomes a reality, it's just fantastic, I can't even begin to imagine the possibilities.

---

### Post by mips on 2012-10-19
> **Hyperfang8 said:**
> 
$199 version comes with 64 cores and ~45Ghz(700Mhz arm9x64)....


No that's BS marketing hype, you can't simply call a 64 core CPU running at 700MHz a 45Ghz CPU. It's lies!

---

### Post by Hyperfang8 on 2012-10-20
> **mips said:**
> No that's BS marketing hype, you can't simply call a 64 core CPU running at 700MHz a 45Ghz CPU. It's lies!

Pleat read again...
Its 700Mhz x 64 =44500 Mhz, so its ~45Ghz!
Did you even clicked the link , watched the video and read story?
If this passes now those procesors would become future of our tablets/smartphones.

---

### Post by Hyperfang8 on 2012-10-20
> **PC_load_letter said:**
> Simply AWESOME! If this becomes a reality, it's just fantastic, I can't even begin to imagine the possibilities.

Yeah but people are not giving it eaungh atention!
Most likely because they think 45Ghz is just trolling/scam.

---

### Post by mips on 2012-10-20
> **Hyperfang8 said:**
> Pleat read again...
Its 700Mhz x 64 =44500 Mhz, so its ~45Ghz!
Did you even clicked the link , watched the video and read story?


No it's not but I see you drank the cool-aid.

You cannot multiply the number of cores with the frequency they run at and then call it a 45GHz cpu. Lies, plain and simple. If it were true I would have a 12GHz cpu which it's not and I can't even fathom what astronomical Hz rating the top 500 supercomputers would have but hey they don't report it as such because they know better.

Yes I read the links, applied some basic comprehension skills coupled with a bit of knowledge and came to the conclusion that it's sensationalist reporting.

Is it a cool project? Yes.
Is it a 45GHz CPU? No.

---

### Post by Atamisk on 2012-10-20
The important number here for supercomputing is: 

"Once completed, the 64-core version of the Parallella computer would deliver over 90 GFLOPS..."

Which is about the same as my non-Overclocked Core i5-2500. Proof: 

```

Intel(R) LINPACK data

Current date/time: Sat Oct 20 07:56:39 2012

CPU frequency:    3.489 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 4

Parameters are set to:

Number of tests: 1
Number of equations to solve (problem size) : 19500
Leading dimension of array                  : 19500
Number of trials to run                     : 100  
Data alignment value (in Kbytes)            : 4    

Maximum memory requested that can be used=3042394096, at the size=19500

============= Timing linear equation system solver =================

Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm)
19500  19500  4      55.132     89.6757  3.722613e-10 3.470996e-02
19500  19500  4      55.171     89.6117  3.722613e-10 3.470996e-02
19500  19500  4      55.204     89.5592  3.722613e-10 3.470996e-02
19500  19500  4      55.500     89.0809  3.722613e-10 3.470996e-02

```

It isn't the knife-edge in computing. An i7 can outperform it with ease.  My CUDA-Enabled Graphics card can run single-precision at nearly a  TeraFLOP/s (120 GFLOP/s at double-precision).

OTOH, i have a 600w PSU driving my processor, and the Processor itself has a TDP of ~90w. The Parallela touts ~5w TDP. It *is* a major feat in power-per FLOPS.

EDIT: It is also of note that the sheer number of cores allows running massively parallel jobs, such as SETI or Folding, with above-average efficiency. If the job control is there, these cores have the potential to really benefit organizations like F@H.

---

### Post by ssam on 2012-10-20
I think they may have put people off with the 45GHz claim. its hard to find the right balance between boring technical details and trying to get people excited about how powerful this chip is.

Its worth having a look through the ample technical documentation. they have made and tested small runs at 65nm [http://www.adapteva.com/news/adapteva-more-flops-less-watts/](http://www.adapteva.com/news/adapteva-more-flops-less-watts/) . they have released the ISA [http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691) . they added support for epiphany into GCC 4.7, and the host board runs ubutu. the coremark score for the 16 core chip is about the same as a intel i5, but using about 2W, and getting a whole computer for $99.

it doesnt start to be a real supercomputer until they scale up to the 1000 core versions. but is still a very interesting project.

---

### Post by Hyperfang8 on 2012-10-20
> **mips said:**
> No it's not but I see you drank the cool-aid.

You cannot multiply the number of cores with the frequency they run at and then call it a 45GHz cpu. Lies, plain and simple. If it were true I would have a 12GHz cpu which it's not and I can't even fathom what astronomical Hz rating the top 500 supercomputers would have but hey they don't report it as such because they know better.

Yes I read the links, applied some basic comprehension skills coupled with a bit of knowledge and came to the conclusion that it's sensationalist reporting.

Is it a cool project? Yes.
Is it a 45GHz CPU? No.

It's not a single 45Ghz CPU but its more smaller 700mhz cpu cores that virtualy perform as fast as single 45Ghz CPU.
**Note:** This is not your normall intel arhitecture!!!
> I would have a 12GHz cpu
If you say so...


Also you are missing some key features:
-it only uses 5Wats(2wats for 16core)
-its small to fit a tablet/smartphone
-its arm
It would be awesome to see this on tablets!!!

---

### Post by Atamisk on 2012-10-20
> **ssam said:**
> I think they may have put people off with the 45GHz claim. its hard to find the right balance between boring technical details and trying to get people excited about how powerful this chip is.

Its worth having a look through the ample technical documentation. they have made and tested small runs at 65nm [http://www.adapteva.com/news/adapteva-more-flops-less-watts/](http://www.adapteva.com/news/adapteva-more-flops-less-watts/) . they have released the ISA [http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/323691) . they added support for epiphany into GCC 4.7, and the host board runs ubutu. the coremark score for the 16 core chip is about the same as a intel i5, but using about 2W, and getting a whole computer for $99.

it doesnt start to be a real supercomputer until they scale up to the 1000 core versions. but is still a very interesting project.

Oh yes, the power-per-watt is pretty interesting. This could be a useful strategy for getting "real" power on small devices. Not to mention it's cheap as all hell.

---

### Post by forrestcupp on 2012-10-20
> **mips said:**
> No that's BS marketing hype, you can't simply call a 64 core CPU running at 700MHz a 45Ghz CPU. It's lies!Exactly.

> **Hyperfang8 said:**
> It's not a single 45Ghz CPU but its more smaller 700mhz cpu cores that virtualy perform as fast as single 45Ghz CPU.
**Note:** This is not your normall intel arhitecture!!!


I'm not denying that this is awesome, but the 45GHz is a load of crap. Multiple cores just do not work that way. Besides, you have to have software that is programmed to utilize all of those cores in order for them to be any benefit at all. How much software is programmed to use 64 cores? Not much.

Granted, it will be very beneficial to something like Blender, which would probably relatively fly with something like this. But for overall, general usage, It's probably going to perform slower than a normal proc, because the software isn't going to take advantage of it. I can see where this could be very awesome for some processor intensive software that is developed to use multiple cores or render farms. But it'll be crap for general use.

---

### Post by Mikeb85 on 2012-10-21
Just for comparison purposes, an nVidia GTX 690 has 3072 CUDA cores, a Radeon 7970 has 2048 cores and can do 3.79 TFLOPS, and Intel's new Phi cards will likely do at least as much.  

The fact the Parallella is a stand-alone system and ARM based is cool, but it's not nearly as powerful as even a retail graphics card...

---

### Post by ssam on 2012-10-21
> **Mikeb85 said:**
> Just for comparison purposes, an nVidia GTX 690 has 3072 CUDA cores, a Radeon 7970 has 2048 cores and can do 3.79 TFLOPS, and Intel's new Phi cards will likely do at least as much.  

The fact the Parallella is a stand-alone system and ARM based is cool, but it's not nearly as powerful as even a retail graphics card...

GFLOPs are not the whole story. GPUs are heavily SIMD (single instruction multiple data), They are very fast when they are doing exactly the same operation many pieces of data. That's fine for most of the work involved in drawing 3d graphics, and some other tasks, but not everything.

Epiphany has completely independent cores, that can run different threads or programs. this opens it to a much wider set of tasks.

its also not really like current multicore CPUs, because it has a very small instruction set, with just what is needed for floating point work. this means it uses very little silicon area and power.

[http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/330705](http://www.kickstarter.com/projects/adapteva/parallella-a-supercomputer-for-everyone/posts/330705)

---


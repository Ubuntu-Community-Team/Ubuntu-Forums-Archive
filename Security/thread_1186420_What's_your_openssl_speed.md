---
title: "What's your openssl speed?"
date: 2009-06-13
forum: Security
---

### Post by kevdog on 2009-06-13
Trying to get a handle on openssl dsa/rsa speed.

Here are my statistitics:
CPU: model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz

$ openssl version
OpenSSL 1.0.0-beta2 21 Apr 2009

$ openssl speed 
...A bunch of results -- at the very end are the RSA/DSA stats 
```
      
                  sign    verify    sign/s verify/s
rsa  512 bits 0.000327s 0.000031s   3057.4  31844.9
rsa 1024 bits 0.001656s 0.000087s    603.7  11514.5
rsa 2048 bits 0.010217s 0.000297s     97.9   3372.3
rsa 4096 bits 0.073864s 0.001155s     13.5    865.9
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000278s 0.000314s   3600.2   3181.5
dsa 1024 bits 0.000794s 0.000938s   1259.2   1065.7
dsa 2048 bits 0.002785s 0.003296s    359.1    303.4

```

Its obvious that DSA can make signatures quicker, but RSA has the advantage in terms of signature verification.

Interested in what others may have in terms of stats!

---

### Post by rookcifer on 2009-06-13
Athlon X2 4000+ @ 2.8 Ghz

```
                  sign    verify    sign/s verify/s
rsa  512 bits 0.000208s 0.000013s   4808.0  79869.1
rsa 1024 bits 0.000688s 0.000030s   1453.2  32913.7
rsa 2048 bits 0.003529s 0.000091s    283.4  11026.4
rsa 4096 bits 0.020983s 0.000294s     47.7   3399.5
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000135s 0.000140s   7393.3   7138.5
dsa 1024 bits 0.000299s 0.000341s   3339.4   2929.3
dsa 2048 bits 0.000863s 0.001027s   1158.6    973.8

```

---

### Post by movieman on 2009-06-14
Atom 330 1.6GHz

```

rsa  512 bits 0.000867s 0.000063s   1153.2  15964.6
rsa 1024 bits 0.003429s 0.000168s    291.6   5960.6
rsa 2048 bits 0.019339s 0.000528s     51.7   1894.7
rsa 4096 bits 0.122805s 0.001828s      8.1    546.9
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000659s 0.000698s   1517.0   1433.6
dsa 1024 bits 0.001675s 0.001967s    597.1    508.3
dsa 2048 bits 0.005139s 0.006301s    194.6    158.7

```

It should be faster than that, but the test is single-threaded (one virtual CPU at 100%, three at 0%).

---

### Post by cariboo on 2009-06-14
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ @2Ghz

```
                  sign    verify    sign/s verify/s
rsa  512 bits 0.000309s 0.000018s   3234.5  57107.7
rsa 1024 bits 0.000965s 0.000043s   1036.3  23314.4
rsa 2048 bits 0.004858s 0.000126s    205.8   7924.1
rsa 4096 bits 0.029038s 0.000404s     34.4   2474.5
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000190s 0.000197s   5275.8   5078.0
dsa 1024 bits 0.000420s 0.000479s   2379.6   2089.9
dsa 2048 bits 0.001198s 0.001441s    834.7    694.2
```

---

### Post by tgalati4 on 2009-06-14
Pentium III, 500 MHz

```


                  sign    verify    sign/s verify/s
rsa  512 bits 0.003473s 0.000286s    287.9   3494.3
rsa 1024 bits 0.016644s 0.000792s     60.1   1262.6
rsa 2048 bits 0.094327s 0.002580s     10.6    387.6
rsa 4096 bits 0.618750s 0.009001s      1.6    111.1
                  sign    verify    sign/s verify/s
dsa  512 bits 0.002733s 0.003227s    365.9    309.9
dsa 1024 bits 0.007605s 0.009317s    131.5    107.3
dsa 2048 bits 0.024974s 0.030185s     40.0     33.1


```

1999 called:  "They want their computer back."

Something in this century:  2006 Pentium D (duo) 3 GHz (overclocked from 2.8 Ghz), with 4-4-4-12 and overclocked RAM:

```


                  sign    verify    sign/s verify/s
rsa  512 bits 0.000382s 0.000028s   2615.0  35617.7
rsa 1024 bits 0.001597s 0.000075s    626.1  13290.5
rsa 2048 bits 0.009034s 0.000239s    110.7   4180.9
rsa 4096 bits 0.057644s 0.000900s     17.3   1111.4
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000290s 0.000316s   3449.9   3165.2
dsa 1024 bits 0.000748s 0.000883s   1337.5   1132.0
dsa 2048 bits 0.002340s 0.002780s    427.4    359.7


```

Roadside rescue from last month--600 MHz Celeron running Hardy server:

```

                  sign    verify    sign/s verify/s
rsa  512 bits 0.002813s 0.000220s    355.5   4540.1
rsa 1024 bits 0.013293s 0.000622s     75.2   1607.0
rsa 2048 bits 0.076565s 0.002057s     13.1    486.1
rsa 4096 bits 0.492381s 0.007119s      2.0    140.5
                  sign    verify    sign/s verify/s
dsa  512 bits 0.002231s 0.002565s    448.3    389.8
dsa 1024 bits 0.006161s 0.007267s    162.3    137.6
dsa 2048 bits 0.020263s 0.024355s     49.4     41.1


```

---

### Post by x3roconf on 2009-06-14
Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz

```

                  sign    verify    sign/s verify/s
rsa  512 bits 0.000239s 0.000017s   4182.4  60039.9
rsa 1024 bits 0.000927s 0.000045s   1079.2  22191.7
rsa 2048 bits 0.005266s 0.000142s    189.9   7035.4
rsa 4096 bits 0.033818s 0.000488s     29.6   2047.3
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000168s 0.000180s   5935.0   5565.6
dsa 1024 bits 0.000439s 0.000507s   2280.3   1973.4
dsa 2048 bits 0.001389s 0.001671s    720.1    598.5

```

---

### Post by ktrnka on 2009-06-14
Amd X2 6000+ 64bit Ubuntu
```

                  sign    verify    sign/s verify/s
rsa  512 bits 0.000201s 0.000012s   4966.7  82286.3
rsa 1024 bits 0.000650s 0.000029s   1537.6  34431.7
rsa 2048 bits 0.003313s 0.000086s    301.8  11581.0
rsa 4096 bits 0.019880s 0.000277s     50.3   3607.9
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000130s 0.000134s   7692.9   7461.1
dsa 1024 bits 0.000286s 0.000331s   3502.0   3025.0
dsa 2048 bits 0.000819s 0.000973s   1221.7   1028.0
```

---

### Post by hictio on 2009-06-15
Mobile AMD Sempron(tm) Processor 3600+

```

                  sign    verify    sign/s verify/s
rsa  512 bits 0.000298s 0.000018s   3356.6  56399.4
rsa 1024 bits 0.000973s 0.000043s   1027.6  23348.8
rsa 2048 bits 0.004962s 0.000129s    201.5   7747.0
rsa 4096 bits 0.029936s 0.000417s     33.4   2396.9
                  sign    verify    sign/s verify/s
dsa  512 bits 0.000194s 0.000201s   5161.2   4981.0
dsa 1024 bits 0.000426s 0.000494s   2349.4   2024.9
dsa 2048 bits 0.001229s 0.001463s    813.7    683.7

```

---


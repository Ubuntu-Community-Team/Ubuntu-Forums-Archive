---
title: "compiling cudaminer (from github)"
date: 2014-01-30
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-01-30
1. i hate compiling cause it never works (every time in my exp)
anyway after fighting about 6 errors and fixing them i am now on this error and have no idea how to fix it

so i run [FONT=courier new]./configure[/FONT]
then i run [FONT=courier new]make[/FONT]

i attached the output of these commands
but this is out it ends
```
/home/chad/Desktop/CudaMiner-master/salsa_kernel.cu:392: undefined reference to `NV2Kernel::NV2Kernel()'
/home/chad/Desktop/CudaMiner-master/salsa_kernel.cu:390: undefined reference to `NVKernel::NVKernel()'
cudaminer-scrypt-jane.o: In function `scanhash_scrypt_jane':
/home/chad/Desktop/CudaMiner-master/scrypt-jane.cpp:502: undefined reference to `pre_keccak512'
/home/chad/Desktop/CudaMiner-master/scrypt-jane.cpp:531: undefined reference to `pre_keccak512'
/home/chad/Desktop/CudaMiner-master/scrypt-jane.cpp:582: undefined reference to `post_keccak512'
/home/chad/Desktop/CudaMiner-master/scrypt-jane.cpp:475: undefined reference to `prepare_keccak512'
collect2: ld returned 1 exit status
make[2]: *** [cudaminer] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
```
if it matters i am compiling in a virtualbox with 13.10 as the host, obviously 14.04 is the guest

---

### Post by Toz on 2014-01-30
[This](https://github.com/cbuchner1/CudaMiner/issues/73) seems like the same issue. Solution noted in thread.

---

### Post by pqwoerituytrueiwoq on 2014-01-30
thanks, i actually got it to compile
uploaded the binary file here
[http://www.filedropper.com/linuxi686cudaminer-2014-01-30](http://www.filedropper.com/linuxi686cudaminer-2014-01-30)

---


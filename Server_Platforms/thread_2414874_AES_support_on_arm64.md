---
title: "AES support on arm64?"
date: 2019-03-16
forum: Server Platforms
---

### Post by katakaio on 2019-03-16
Hello! I recently installed Ubuntu 18.04.2 Server on my Raspberry Pi 3 B+ using the official image (see [here]("https://wiki.ubuntu.com/ARM/RaspberryPi")) and have confirmed that the 64-bit kernel is active:
```
[COLOR=#2FB41D][FONT=Monaco]katakaio@ubuntu[/FONT][/COLOR][COLOR=#F2F2F2][FONT=Monaco]:[/FONT][/COLOR][COLOR=#400BD9][FONT=Monaco]~[/FONT][/COLOR][FONT=Monaco]$ uname -a
Linux ubuntu 4.15.0-1032-raspi2 #34-Ubuntu SMP PREEMPT Wed Feb 6 11:46:23 UTC 2019 aarch64 aarch64 aarch64 GNU/Linux[/FONT]
```
One of my primary reasons for using the arm64 image was because ARMv8 processors include dedicated instructions for AES and other encryption protocols (see [here]("https://en.wikipedia.org/wiki/ARM_architecture#64/32-bit_architecture") and [here]("https://www.linaro.org/blog/accelerated-aes-for-the-arm64-linux-kernel/")). I assumed that the 64-bit Ubuntu Server image would be able to access these instructions, but AES doesn't appear as a feature in my /proc/cpuinfo:
```
[COLOR=#2FB41D][FONT=Monaco]katakaio@ubuntu[/FONT][/COLOR][COLOR=#F2F2F2][FONT=Monaco]:[/FONT][/COLOR][COLOR=#400BD9][FONT=Monaco]~[/FONT][/COLOR][FONT=Monaco]$ cat /proc/cpuinfo processor    : 0[/FONT]
[FONT=Monaco]BogoMIPS    : 38.40[/FONT]
[FONT=Monaco]Features    : fp asimd evtstrm crc32 cpuid[/FONT]
[FONT=Monaco]CPU implementer    : 0x41[/FONT]
[FONT=Monaco]CPU architecture: 8[/FONT]
[FONT=Monaco]CPU variant    : 0x0[/FONT]
[FONT=Monaco]CPU part    : 0xd03[/FONT]
[FONT=Monaco]CPU revision    : 4[/FONT]
```
I'm used to seeing "aes" as a flag when I run that same command on my x64 machines, although I'm new to ARM and realize that there may be differences. Can anyone confirm that AES instructions are supported in 18.04.2 on arm64 - or advise me as to how I might confirm that they're in use? Thank you!

---

### Post by katakaio on 2019-12-05
After some sleuthing, I discovered the answer to my question: while some ARMv8 processors include optional cryptography acceleration for AES and SHAx, [the Raspberry Pi 3 does not.]("https://raspberrypi.stackexchange.com/a/99172") This is consistent with the output of cat /proc/cpuinfo that I reported earlier.

However, there is some good news! The RPi3 does offer some modest crypto acceleration by way of NEON/SIMD:
```
[FONT=&amp]ubuntu@ubuntu:~$ sort -u /proc/crypto | grep module
[/FONT][FONT=&amp]module       : aes_arm64[/FONT]
[FONT=&amp]module       : aes_neon_blk[/FONT]
[FONT=&amp]module       : aes_neon_bs[/FONT]
[FONT=&amp]module       : crc32_ce[/FONT]
[FONT=&amp]module       : ecdh_generic[/FONT]
[FONT=&amp]module       : kernel[/FONT]
```

The ability for the RPi3 to accelerate AES via NEON is also described at length [here]("https://www.linaro.org/blog/accelerated-aes-for-the-arm64-linux-kernel/").

To see if this has any real impact on crypto performance, I ran a few openssl speed benchmarks with and without the EVP functions and observed a ~25% performance increase with the -evp flag set; I am assuming that this is enabling NEON/SIMD support, but that's conjecture on my part.

So, the answer to my original question is *yes*, there is acceleration for AES on the RPi3's ARMv8, but much less than one might expect from a Intel/AMD proc with true crypto acceleration. I hope this helps anyone else who wondered about this!

---


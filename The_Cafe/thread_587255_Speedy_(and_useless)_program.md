---
title: "Speedy (and useless) program"
date: 2007-10-22
forum: The Cafe
---

### Post by happysmileman on 2007-10-22
Well I got bored and decided to make a simple ASM program, it does 1000000000 decimal places of long division, not recording the results, or outputting them, or doing anything with them unless required to continue with the sum...

I just thought it's be fun to see how fast it'll work for different people, I used NASM to assemble it, and 'ld' to link it, if you're interested post the results of "time ./Program" here, the file assembles to 396 bytes for me.

```

section .text
    global _start

_start:
    mov ax, 13
    mov bx, 97
    mov ecx, 1000000000
    mov dx, 0
    mov sp, 10
    
    theloop:
    	div bx
    	mov ax, dx
    	mul sp
    	dec ecx
        cmp ecx, 0
        jne theloop
    
    mov eax, 1
    mov ebx, 0
    int 0x80
```

ANy improvements to the code would be appreciated, since it's only to test very basic ASM.

My results:
> real    0m32.856s
user    0m31.726s
sys     0m0.196s

On a pentium 4, 2.667Ghz running Gentoo.

---

### Post by henchman on 2007-10-27
huhu :D

i was bored, too. so i just tested it and as a newbie learned to use time, nasm and ld :KS


```
real    0m15.351s
user    0m14.845s
sys     0m0.104s
```

core2duo2ghz of course running the gibbon :)

---

### Post by kellemes on 2007-10-27
Well well.. that was fun.. nasm .. ld .. I really had a ball :)

Pentium4 - 3Ghz
ArchLinux (Don't Panic)

```
real    0m28.996s
user    0m28.961s
sys     0m0.033s

```

---


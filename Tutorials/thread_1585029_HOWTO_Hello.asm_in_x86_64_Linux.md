---
title: "HOWTO: Hello.asm in x86_64 Linux"
date: 2010-09-29
forum: Tutorials
---

### Post by WinstonChurchill on 2010-09-29
I recently set about writing the good old "Hello World!" program using Linux syscalls from NASM, and due to not finding this information anywhere else, I thought I'd save some wayward soul the hour I wasted divining it:

[LIST]
[*]The order of registers for the arguments is different in 64-bit mode - rax is still the syscall number, but the order is [rdi,rsi,rdx,r10,r8,r9] - don't ask me why. This means that (praise be to God), when writing 64-bit code you never need to use the stack to invoke 6-argument syscalls like mmap(...) the way you do in 32-bit code, which not only makes coding easier but makes the code much faster.
[*]Don't use the 'int 0x80' instruction - use the 'syscall' instruction instead.
[*]Remember that the syscall index numbers are totally different in 64-bit code.
[*]The syscall's return value is written to rax.
[*]Registers rcx and r11 are overwritten after every syscall.
[/LIST]
That said, here are a couple examples. Partake of the joy, forthwith:
```
[bits 64]
global _start

section .data
message db "Hello World!",0x0a,0x00

section .text
_start:
mov rax,1
mov rdx,13
mov rsi,message
mov rdi,1
syscall

mov rax,60
mov rdi,0
syscall
```Which assembles to (before being linked, obviously):
```

00000000  48 b8 01 00 00 00 00 00  00 00 48 ba 0d 00 00 00  |H.........H.....|
00000010  00 00 00 00 48 be 40 00  00 00 00 00 00 00 48 bf  |....H.@.......H.|
00000020  01 00 00 00 00 00 00 00  0f 05 48 b8 3c 00 00 00  |..........H.<...|
00000030  00 00 00 00 48 bf 00 00  00 00 00 00 00 00 0f 05  |....H...........|
00000040  48 65 6c 6c 6f 20 57 6f  72 6c 64 21 0a 00        |Hello World!..|

00000000  48B80100000000000000  mov rax,0x1
0000000A  48BA0D00000000000000  mov rdx,0xd
00000014  48BE4000000000000000  mov rsi,0x40
0000001E  48BF0100000000000000  mov rdi,0x1
00000028  0F05                  loadall286
0000002A  48B83C00000000000000  mov rax,0x3c
00000034  48BF0000000000000000  mov rdi,0x0
0000003E  0F05                  loadall286

```It's worth remembering that whenever you use the MOV opcode with an immediate operand, the operand gets expanded to the width of the destination register - in this case, a full quadword. If for some reason you're obsessing about length, you can more than halve the length of the machine code with some clever use of the 32-bit, 16-bit and 8-bit register names: (Because we have to link it, the address of the string must still be a full quadword - if that wasn't the case, you could save another 6 bytes by using si instead of rsi)
```

[bits 64]
global _start

section .data
message db "Hello World!",0x0a,0x00

section .text
_start:
mov al,1
mov dl,13
mov rsi,message
inc edi
syscall

mov al,60
dec edi
syscall

```Which assembles to:
```

00000000  b0 01 b2 0d 48 be 18 00  00 00 00 00 00 00 ff c7  |....H...........|
00000010  0f 05 b0 3c ff cf 0f 05  48 65 6c 6c 6f 20 57 6f  |...<....Hello Wo|
00000020  72 6c 64 21 0a 00                                 |rld!..|

00000000  B001                  mov al,0x1
00000002  B20D                  mov dl,0xd
00000004  48BE1800000000000000  mov rsi,0x18
0000000E  FFC7                  inc edi
00000010  0F05                  loadall286
00000012  B03C                  mov al,0x3c
00000014  FFCF                  dec edi
00000016  0F05                  loadall286

```Of course, this assumes that all the registers are clear when it is executed - but all the 'xor rXX,rXX' instructions assemble to 3 bytes; so even if you had to zero out all the registers, it would still be shorter than the original with the 'MOV' instructions.

---

### Post by snip3r8 on 2011-09-07
Im new to assembly and was trying to compile a hello world that was written in 32 bit assembly,now i found this but i dont know how to compile the 64 bit code with nasm

---

### Post by snip3r8 on 2011-09-07
> **snip3r8 said:**
> Im new to assembly and was trying to compile a hello world that was written in 32 bit assembly,now i found this but i dont know how to compile the 64 bit code with nasm
Ok sorted ,i built my 32 bit code and it worked fine

---


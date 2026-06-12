---
title: "Puls demo: Extremely sick programming"
date: 2009-09-28
forum: The Cafe
---

### Post by BuffaloX on 2009-09-28
From scene.org watch this mind blowing demo by rrrola.
The mind blowing part is not the beauty or the speed, it's the complexity achieved within an extremely compact piece of code.

Youtube:
[http://www.youtube.com/watch?v=3vzcMdkvPPg]("http://www.youtube.com/watch?v=3vzcMdkvPPg")

Try to guess how compact this code can be made, considering it uses no 3D or other rendering libraries, it's all done with it's own rendering.

You can download the source and binary here, if you want to have a look:
[http://www.scene.org/file.php?file=%2Fparties%2F2009%2Friverwash09%2Fi256%2Fpuls.zip&fileinfo]("http://www.scene.org/file.php?file=%2Fparties%2F2009%2Friverwash09%2Fi256%2Fpuls.zip&fileinfo")

Michael Birken comments a bit on the code here:
[http://meatfighter.com/puls/]("http://meatfighter.com/puls/")

Notice how rrrola reuses the setting of the graphics mode as constants, by throwing in an otherwise unneeded instructions.

Animated 3D rendering in 256 bytes, WOW.:shock:

---

### Post by pwnst*r on 2009-09-28
holy crap!  that's mindboggling.

---

### Post by CJ Master on 2009-09-28
> **pwnst*r said:**
> holy crap!  that's mindboggling.

.

---

### Post by 3rdalbum on 2009-09-28
I remember the old 5k website competition; somebody made a wireframe cube that's made out of ASCII characters that slowly rotates in your web browser. The entire composition took up less than 5 kilobytes.

---

### Post by Vostrocity on 2009-09-28
That's cool, even though I'm no good at programming.

---

### Post by clonne4crw on 2009-09-29
Here's the source code. I love Assembler, and this is right at home for me: 
```

; P   L   a 256-byte intro by Rrrola - final version
;  \ / \   rrrola@gmail.com
;   U   S   http://rrrola.wz.cz
; greets to everyone who came to Riverwash 2009

;%define BLOWUP 86    ; "ambient occlusion" strength (default 86: -1 byte)
MAXSTEPSHIFT equ 6    ; shading strength (>=6 unless BLOWUP defined)
MAXITERS     equ 26
BASECOLOR    equ -34
%define BLOCKS     ; render 4x1 blocks (for slower machines, +3 bytes)

  org 100h ; assume ah=bx=0 cx=255 sp=di=-2 si=100h

  mov  al,13h   ;<(byte)[100h]>>8 = 0.6875
  push bx       ; (word)[100h]>>16 = 0.0769
  mov  dx,3C8h  ; (float)[100h] = -0.0008052
  int  10h

;palette - 4 gradients of 32 shades

P mov  al,bl    ;<set al on 1st pass, then each red and green
Q test bl,cl    ; parity: eooooeoeoeee eooooeoeoeee ...
  jpe  E        ; index:  #0gb1gb2gb3g b4gb5gb6gb7g ...
  imul al
  shr  ax,7
E imul bl
  mov  al,ah
  out  dx,al
  mov  dl,0c9h
  loop P
  mov  cl,3
  dec  bx
  jnz  Q

  push 09FCEh   ;<aligns with the screen ;-)
  pop  es
  mov  bh,56h   ; xyz addressing trick from neon_station
                ; vecNN = (words){[5600h+N] [5656h+N] [56ACh+N]}

;frame loop - prepare constants
;ax=key bx=5600h bp=dx=0 cx=3 si=100h di=-2 sp=-4 word[5700h]=T

M fninit                ; {} = fpu stack
  add  word[bx+si],byte 88 ; T++

  fild   word[bx+si]    ;=14.00564 * 2pi
  fsincos               ; {s=sin(T*0.00564) c=cos(T*0.00564)}
  fdiv   st1,st0        ; {s t=cotg(T*0.00564)}

  fild   word[bx+si]
  fmul   dword[si]
  fsin
  fimul  word[si]       ; {r>>16=0.0769*sin(T*-0.0708) s t}

  pop  edx      ;=9B6C0000... just get rid of it
  push es
  push bp       ;dword[-4]=9FCE0000h

;pixel loop
;x = word[-3] ~ -0.5..0.5 (+= 0.003125 each column)
;y = word[-2] ~ -0.4..0.4 (+= 0.00390625 each row)

X
 %ifdef BLOCKS
  test bp,cx    ; 4x1 blocks: keep last color?
  jnz  D
 %endif

  pusha ;[-20 -18 -16 -14 -12 -10 -8  -6  -4  -2  ]
        ; di  si  bp  sp  bx  dx  cx  ax      yyyy
        ; FEFF0001adr FCFF005600000300col ..xxxx

;fisheye projection: z = C-x*x-y*y

  mov  [bx],bx ;=0.33594
Z mov  ax,[di]
  fild   word[di]
  imul ax
  sub  [bx],dx
  dec  di
  jpo  Z        ;di=-4
  fild   word[bx]       ; {z>>16=0.33594-x*x-y*y x y r s t}

;advance x and y for next pixel (low word)

 %ifdef BLOCKS
  add  word[di],3334h
 %else
  add  dword[di],0000CCCDh
 %endif

;rotate direction vector

R fmul   st4    ; {sz x y r s t}
  fld    st0
  fmul   st6    ; {cz sz x y r s t}
  fxch   st2
  fmul   st5
  fsub   st2,st0; {sx sz cz-sx y r s t}
  fmul   st6
  faddp  st1,st0; {cx+sz cz-sx y r s t}
  fxch   st2    ; {y cz-sx cx+sz r s t}
  inc  di
  jpo  R
  dec  di       ;di=-2  ; {X Y Z r s t}

;advance x and y for next pixel (high word)

 %ifdef BLOCKS
  adc  word[di],cx
 %endif

;store ray origin and direction vector

  imul dx,[bx+si],byte 10;=0.0134*T
S
  fistp  word[bx+di]    ; d>>16 = v-2 = {X, Y, Z}
 ;fistp dword[bx+di]    ;<slower, but fixes corners (+3 bytes)
 ;sar dword[bx+di],1

  mov  [bx],dx
  add  dh,[si]          ; o>>16 = v0 = 0.0134*T + {0, 0.6875, 0.375}
  add  bl,bh
  jnc  S        ;bl=2   ; {r s t}

;intersect ray with scene, count number of bounding volume misses

  cwd                   ; dx = hit(-1|0): grainy rendering
  mov  ah,-MAXITERS     ; ah = iters(-MAXITERS..0), al = hue(0..3)
 ;cwd                   ;<for smooth rendering with bands

 %ifdef BLOWUP
  mov  cx,BLOWUP*256+MAXSTEPSHIFT; cl = stepshift(0..MAXSTEPSHIFT)
 %else
  adc  cx,bx    ;=86*256 + 6 ;-)
 %endif

  call I

  sub  ah,cl
  aad  4        ;ah=0
  add  al,MAXITERS*4+BASECOLOR
  mov  [di-4],ax        ; pushed ax = color = (iters-stepshift)*4 + hue

  popa

;draw pixel

D
 %ifdef BLOCKS
  mov  [es:bp+si],al
  inc  bp
 %else
  inc  bp
  mov  [es:bp+si],al
 %endif

  jnz  X                ; 65536 pixels

;next frame: fall through on esc - ah=word[sp]=0

  in   al,60h
  dec  ax
  jnz  M        ;<assume no one presses ESC after 1 frame ;)


;raycasting using unbounded binary search
;start with the smallest step size
;v-2 = d = {dx, dy, dz}
;v0  = o = current {x, y, z} mod 1

;last probe was inside: halve step and go back
;              outside: double step and go forward

I mov  bl,0     ;bl=0
A mov  bp,[bx+di]       ; hit ? (o -= d>>stepshift) : (o += d>>stepshift)
  sar  bp,cl
  xor  bp,dx
  add  [bx],bp
  add  bl,bh
  jnc  A        ;bl=2

  salc          ;al=FFh
  fist   word[bx+si]    ; word[5702h] = r

;bounding volumes: "blow up" the scene by the current step size

  push cx
  shr  cx,cl
  add  ch,37    ; cx = hitlimit = 0.1445 + (BLOWUP >> stepshift+8)

;inside test

;hue=[0,1]
;green octahedra:              (|x|+|y|+|z|)/2 - 0.1445 + r < blowup
;orange octahedra: (|x+0.5|+|y+0.5|+|z+0.5|)/2 - 0.1445 - r < blowup

O mov  dx,[bx+si]       ; dx = [r,-r]
  neg  word[bx+si]
C imul bp,ax,32768      ; bp = [0.5, 0] - v0.xyz
  sub  bp,[bx+di]
  jns  T
  neg  bp
T shr  bp,1
  add  dx,bp            ; v2 = |signed(bp)|/2
  mov  [bx],bp
  add  bl,bh
  jnc  C        ;bl=4   ; dx = sum(v2) + [r,-r]

  cmp  dx,cx            ; if (dx < hitlimit) hit!
  inc  ax       ;al=0,ah++
  jc   H
  mov  bl,2     ;bl=2
  jpe  O        ;al=1   ; repeat if al==0

;hue=[2,3]
;bars:  (||x|-|z|| + ||y|-|x|| + ||z|-|y||)/2 - 0.0676 < blowup
;bolts: (||x|-|z|| + ||y|-|x|| + ||z|-|y||)/2 - 0.1445 < blowup

  sub  dx,[bx+si]
  inc  ax       ;al=2

 ;sub  dx,bx            ;<simple bolt movement: sum(v2)-2*r-0.3359
  sub  dx,[bx+si]       ;<precise bolt movement: sum(v2)-3*r-0.375
  sub  dh,60h           ; (+3 bytes)

  imul dx,byte 13       ; if (|sum(v2)-3*r-0.375| < 0.03846)
  mov  dx,[si]          ;   dx = extra_width = 0.0769, hue = 2
  jo   B                ; else
  inc  ax       ;al=3   ;   dx = extra_width = 0, hue = 3
  cwd
B sub  bp,[bx]          ; bp = v2.zxy - v2.xyz
  jns  L
  neg  bp
L add  dx,bp
  mov  bp,[bx]
  add  bl,bh
  jnc  B        ;bl=4   ; dx = sum(|signed(bp)|) + extra_width

  cmp  dx,cx            ; if (dx < hitlimit) hit!

;adjust step size according to the hit result

H pop  cx       ;cf=hit
  sbb  dx,dx            ; dx = hit?-1:0
  cmc
  sbb  cl,dl            ; if (hit) stepshift++
  adc  cl,dl            ; else if (stepshift > 0) stepshift--

;more probes?

  cmp  cl,MAXSTEPSHIFT
  jae  F                ; if (stepshift >= maxstepshift) break
  add  ah,dl            ; iters++, if (hit) iters--
  jne  I                ; if (iters >= maxiters) break
F ret


```

---

### Post by JillSwift on 2009-09-29
*plotz*

It is fabulous to see that there are still folks who like to make super efficient code despite all the memory and hardware available.

Just lovely stuff.

---

### Post by Yes on 2009-09-29
How would you compile it in Linux?

---

### Post by clonne4crw on 2009-09-29
> **BuffaloX said:**
> Animated 3D rendering in 256 bytes, WOW.

What's more amazing is that this isn't even 3D rendering. It's just 2D pixels being manipulated so it looks like it is 3D. No hardware acceleration at all.

---

### Post by NovaAesa on 2009-09-29
I'm impressed!!

---

### Post by dragos240 on 2009-09-29
> **Yes said:**
> How would you compile it in Linux?

+1

All the files in there are .com files. If I remember correctly, those are Windows command files. :confused:

---

### Post by BuffaloX on 2009-09-29
> **clonne4crw said:**
> What's more amazing is that this isn't even 3D rendering. It's just 2D pixels being manipulated so it looks like it is 3D. No hardware acceleration at all.

This is some sort of raytracing, which is indeed 3D rendering.
One of the really mind boggling parts is exactly the fact that he made the program without any use of 3D libraries, the 3D functions are within the 256 bytes of code.

Hardware accelerated 3D is no more true 3D than this is.

---

### Post by samjh on 2009-09-29
Very impressive.  The Source is *stroooong* in him.  Someone from NVidia/ATI or a 3D graphics company should give the author a job (if he doesn't have one already).

---

### Post by Frak on 2009-09-29
I use [fasm]("apt:fasm").

```

fasm puls.com
ld <whatever fasm outputs>

```

---

### Post by dragos240 on 2009-09-29
> **Frak said:**
> I use [fasm]("apt:fasm").

```

fasm puls.com
ld <whatever fasm outputs>

```

Should fasm ouput this?:
```
[root@myhost puls]# fasm puls.com
flat assembler  version 1.68  (16384 kilobytes memory)
puls.com [1]:
&#65533;S&#65533;&#65533;&#65533;&#65533;&#1540;&#65533;z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Ku&#65533;h&#927;&#65533;V&#65533;
error: illegal instruction.
```

---

### Post by Frak on 2009-09-29
Yes.

---

### Post by BuffaloX on 2009-09-29
You might try to assemble the source and not the binary.

---

### Post by Yes on 2009-09-29
That just says

```
flat assembler  version 1.68  (16384 kilobytes memory)
puls.asm [10]:
%define BLOCKS     ; render 4x1 blocks (for slower machines, +3 bytes)
error: illegal instruction.
```

---

### Post by Frak on 2009-09-29
> **Yes said:**
> That just says

```
flat assembler  version 1.68  (16384 kilobytes memory)
puls.asm [10]:
%define BLOCKS     ; render 4x1 blocks (for slower machines, +3 bytes)
error: illegal instruction.
```
Also the correct error message. Not sure what assembler he used.

---

### Post by dragos240 on 2009-09-29
> **Frak said:**
> Also the correct error message. Not sure what assembler he used.

I used fasm from the aur...

---

### Post by Mateo on 2009-09-29
assembly programmers are gods.

---

### Post by rCXer on 2009-09-29
I think this is nasm syntax...
```

sudo apt-get install nasm

```

...and then...
```

nasm -f bin puls.asm -o puls.com

```

Since it's a com file, you need a dos emulator, like dosbox.
```

sudo apt-get install dosbox

```

Then run it using...
```

dosbox -noautoexec -exit puls.com

```

You'll probably need to press Ctrl-F12 to increase its speed.  Sadly it runs really disappointedly slow in the emulator. But It'll run at full speed in real DOS. I love asm :popcorn:

---


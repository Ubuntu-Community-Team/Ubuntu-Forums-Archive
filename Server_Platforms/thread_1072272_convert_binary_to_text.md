---
title: "convert binary to text"
date: 2009-02-17
forum: Server Platforms
---

### Post by jyotigupta on 2009-02-17
Hi,
I wnt to convert binary to text in linux.. cn anybody help me.. thanks :)

---

### Post by cdenley on 2009-02-17
You will have to be more specific. Do you have a binary file which you want to search for ASCII strings? Do you have a text file containing binary data as 1's and 0's which you need to convert to ASCII text? Do you want to convert binary data to a text friendly representation such as base64 encoding?

---

### Post by d3v1150m471c on 2011-06-21
Yeah i know this is an old thread but I've had success with this and also have a question. Now I could use some CLI tools w/bash script to achieve my ends here but I'm curious if there is already a linux tool for this. I can take a binary file and see the output in ascii text using hexdump, aka hd:
```

hexdump -C binary-file

```

However stdout looks something like this:
```

000000a0  30 e3 d3 60 e1 00 aa aa  03 00 00 00 08 00 45 00  |0..`..........E.|
000000b0  00 8f bd 2a 40 00 6e 06  fb 0b 4d ff 44 4b c0 a8  |...*@.n...M.DK..|
000000c0  01 40 ba fd b8 e5 1f ca  95 17 49 4f b8 22 50 18  |.@........IO."P.|
000000d0  44 10 94 6a 00 00 9c ca  f7 49 a2 f0 4f 91 59 54  |D..j.....I..O.YT|
000000e0  04 ed 05 08 6c d4 3d 3a  96 82 51 f3 8f 33 d6 7d  |....l.=:..Q..3.}|
000000f0  ad 0a 7f a6 ae cf 24 34  ee ff 24 af 63 ae 5d dd  |......$4..$.c.].|
00000100  6c 90 ab d2 82 4e 86 d2  b5 6f 8b fd 4b d1 7c 68  |l....N...o..K.|h|
00000110  0a 67 6e ee 73 6f 34 8c  44 8d 6f a3 87 96 04 35  |.gn.so4.D.o....5|
00000120  f6 ea e8 c8 82 cf 2c fd  4e 65 64 0f 3e 8c 44 54  |......,.Ned.>.DT|
00000130  c5 6e 91 17 01 4d 0e 75  58 4e f4 95 9d 84 18 f2  |.n...M.uXN......|
00000140  c3 36 d4 ff 4d 24 7a 0b  00 0a 00 00 00 0a 00 00  |.6..M$z.........|
00000150  00 d4 00 00 00 00 24 2b  28 04 e6 36 d4 ff 4d 40  |......$+(..6..M@|
00000160  7a 0b 00 4c 00 00 00 4c  00 00 00 08 41 34 00 98  |z..L...L....A4..|
00000170  2c be 0b ec 31 00 24 2b  28 04 e6 98 2c be 0b ec  |,...1.$+(...,...|
00000180  31 80 59 39 2e 1b 00 aa  aa 03 00 00 00 08 00 45  |1.Y9...........E|

```

I don't want the hexadecimal data, I just want the ascii on the right. Any tools or proper tool use for this? thanks in advance. 

PS, I apologize in advance if i'm "thread hijacking" but I figured it was along the topic and didn't want to start a new thread.

---

### Post by dFlyer on 2011-06-21
Have you taken a look at t1utils in the archives?

---

### Post by d3v1150m471c on 2011-06-21
> **dFlyer said:**
> Have you taken a look at t1utils in the archives?

i'll check that out, thanks.

edit:
that would suit my needs except it only works for certain file types. I just want to convert the binary data to ascii in general. not specifically for an adobe file or otherwise.

---

### Post by egpetrich on 2011-06-22
The "hexdump" program allows you pretty broad control over your output format, but it may take some experimenting to get the format you want. Here are some examples:
```
$ cat ./sample_file.txt
This is line 1.
This is line 2.
This is line 3.
$ hexdump -e '"%08.8_ao " 32/1 "%_p" "\n" ' ./sample_file.txt
00000000 This is line 1..This is line 2..
00000040 This is line 3..
$ hexdump -e '"%08.8_ao " 8/1 "%3_c " "\n" ' ./sample_file.txt
00000000   T   h   i   s       i   s    
00000010   l   i   n   e       1   .  \n
00000020   T   h   i   s       i   s    
00000030   l   i   n   e       2   .  \n
00000040   T   h   i   s       i   s    
00000050   l   i   n   e       3   .  \n
```
If all you want to do is find the ASCII strings embedded in a binary file, the "strings" command is your friend.

---

### Post by sreyasna on 2012-10-10
Hi, even i too face the same problem of reading a .config file
i want to convert it into a readable formart. am not sure is that a binary file format. 
 
can anyone help me out... :)

---


---
title: "Your 10 Most-Used Commands"
date: 2009-03-04
forum: The Cafe
---

### Post by mconway on 2009-03-04
I was browsing a "command-of-the-day" site called commandlinefu.com, and found a command to list your most used terminal commands. Here's the string:

[FONT=Courier New]history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head[/FONT]

Post your output here, if you want!

[FONT=Courier New]65 sudo
57 ls
48 clear
28 cd
20 exit
15 ping
11 chmod
8 df
7 ssh
4 echo[/FONT]

Source: [http://www.commandlinefu.com/commands/browse/sort-by-votes](http://www.commandlinefu.com/commands/browse/sort-by-votes)

---

### Post by Testrum on 2009-03-04
```
62 sudo
8 cd
5 make
4 gpg
3 sh
3 dpkg
3 chmod
2 wget
2 tar
2 su
```

---

### Post by Alterax on 2009-03-04
OK, for some reason I feel like I am exposing the contents of my underwear drawer, but here goes:

87 sudo
83 ls
60 ssh
54 cd
24 cat
11 ping
11 exit
10 sftp
10 apt-cache
9 nano

---

### Post by khelben1979 on 2009-03-04
79 apt-get
75 cd
52 sh
52 ls
35 dselect
20 top
16 man
14 dpkg
14 df
9 su

---

### Post by TheOrangePeanut on 2009-03-04
219 sudo
157 exit
127 pacman
84 cd
59 ls
37 alsamixer
27 locate
22 less
15 killall
14 ps

---

### Post by yther on 2009-03-04
Heh, here's my underwear:

```
78 mplayer
47 sudo
45 ls
42 cd
40 aptitude
38 pico
30 less
18 ll
15 ps
12 locate
```

This box was constructed only 3 weeks ago, so not a lot of lost socks yet.  ;)

---

### Post by agim on 2009-03-04
89 dir
78 pico
77 cd
50 clear
34 sudo
30 make
26 qmake
17 g++
13 rm
9 mkdir

---

### Post by FuturePilot on 2009-03-04
92 sudo
50 apt-cache
35 server
26 ls
22 cat
16 telnet
16 man
14 ssh
14 nano
11 cd

---

### Post by ad_267 on 2009-03-04
86 cd
72 ls
62 gnuplot
57 v
31 rubber
28 rm
26 exit
19 evince
16 pdflatex
15 man

I've been playing around with LaTeX and Gnuplot a lot recently. V is an alias for vim. Rubber is a tool for automating the compilation of LaTeX documents.

---

### Post by k2t0f12d on 2009-03-04
```
237 sudo
140 ls
99 yaourt
81 cat
47 cd
46 if
32 find
28 mkdir
27 mv
24 pacman
```

---

### Post by binbash on 2009-03-04
I am cleaning history every 2 days but for now : 

127 sudo
57 ls
52 cd
38 pkill
36 gedit
20 wget
20 ./conkystartup
17 ./conkystartup2
14 nano
10 conky

---

### Post by Orlsend on 2009-03-04
130 sudo
32 cd
28 espeak
23 python
14 ping
13 outguess
13 gpg
10 wine
8 scrot
8 bzr

---

### Post by abhilashm86 on 2009-03-04
abhilash@abhi:~$ history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
90 vim
72 g++
54 sudo
50 mocp
34 cat
20 ls
19 ./a.out
14 mplayer
9 man
8 rm

as a root,
root@abhi:/home/abhilash# history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
85 ls
64 cd
51 sudo
38 mutt
26 exit
25 vim
21 mocp
20 pwd
19 gedit
17 chmod

---

### Post by spcwingo on 2009-03-04
219 sudo
137 exit
15 lspci
13 md5sum
11 ping
11 cd
9 stella
8 mount
6 GSnes9x
6 dir

---


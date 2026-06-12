---
title: "Linux drawing in text mode(no gui, desktop)"
date: 2019-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by michelle345 on 2019-04-06
[COLOR=#242729][FONT=Arial]I'm kind of new to linux without a gui and i run into a problem. 

When using a linux distro with gui, it looks easy to draw on a window using a library(opengl, sdl). 

I wanted to create a chip8 emulator in c++, but how can i handle drawing on screen? 

Or any library that can draw in text based linux, or just usage of opengl in text based linux. 

Thanks! Btw! I'm using bash in windows and a vagrant machine running precise64.[/FONT][/COLOR]

---

### Post by freemedia2018 on 2019-04-06
For Windows, getting ANSI to work can be complicated. The library you're probably looking for is called **libcaca**.

For now, feel free to take apart this public domain bash script I wrote, first running it to get an idea of what it does (it's fun.) Most of the frightening and really bad stuff has nothing to do with drawing, but parsing. You can get rid of right(), it's ridiculous. Note, I have a programming language with line drawing in text as one of its features. But that's 1000 LOC in Python, it uses escape codes too, this is just a toy I did for a contest.

```
#!/bin/bash
#### license: creative commons cc0 1.0 (public domain) 
#### [http://creativecommons.org/publicdomain/zero/1.0/](http://creativecommons.org/publicdomain/zero/1.0/) 
proginf="bashlogo, jun 2017 mn"

x=40 ; y=10 ; pendown=1 ; pencolour=7 ; ud=0 ; lr=0 ; numeric=0

function ne() {
    nl="$nl"
    }
function xy() { 
    xy_x=${1} ; xy_y=${2}
    echo -ne "\\033[$xy_y;$xy_x""H"
    } 
function right() { # probably a better way to do this, but this one was a lot of fun
    right_buf="" ; right_c=0
    right_p=${1} ; right_x=${2}
    for right_b in $(echo "$right_p" | tr ' ' '_' | rev | fold -sw 1) 
    do right_buf="$right_buf$right_b" ; right_c="$(($right_c+1))" ; if [[ ! "$right_c" -lt "$right_x" ]]
    then break ; fi ; done ; echo "$right_buf" | rev | tr '_' ' '
    }
function colour() { 
    colour_f=${1} ; colour_b=${2}
    if [[ "$colour_f" == "" ]] ; then colour_f="0" ; fi ; if [[ "$colour_b" == "" ]] ; then colour_b="0" ; fi ; colour_n="0"
    if   [[ "$colour_f" -gt "7" ]] ; then colour_n="1" ; colour_f="$(($colour_f-8))" ; fi
    if   [[ "$colour_f" == "1" ]] ;  then colour_f="4" ## switch ansi colours for qb colours
    elif [[ "$colour_f" == "4" ]] ;  then colour_f="1" ; fi ## 1 = blue not red, 4 = red not blue, etc.
    if   [[ "$colour_f" == "3" ]] ;  then colour_f="6"
    elif [[ "$colour_f" == "6" ]] ;  then colour_f="3" ; fi
    if   [[ "$colour_b" -gt "7" ]] ; then colour_b="$(($colour_b-8))" ; fi
    if   [[ "$colour_b" == "1" ]] ;  then colour_b="4"
    elif [[ "$colour_b" == "4" ]] ;  then colour_b="1" ; fi
    if   [[ "$colour_b" == "3" ]] ;  then colour_b="6"
    elif [[ "$colour_b" == "6" ]] ;  then colour_b="3" ; fi
    echo -ne "\\033[$colour_n;$((30+$colour_f));$((40+$colour_b))m"
    } 
function lmv() {
    lmv_ud=${1} ; lmv_lr=${2} ; lmv_num=${3}
    if [[ ! "$ud" == "0" || ! "$lr" == "0" ]] ; then
    for lmv_r in $(seq 1 $lmv_num)
    do x=$(($x+$lr)) ; y=$(($y+$ud)) 
    if [[ "$pendown" == "1" ]]
    then xy "$x" "$y" ; colour 0 "$pencolour" ; echo -n " " ; colour 7 0 #echo "$lmv_ud" "$lmv_lr" "$lmv_num" "$y" "$x"
    fi
    done
    fi
    }

clear ; colour 11 0 ; echo $proginf ; colour 7 0 ; xy "$x" "$y"

program="pu u7 l24 c7 pd r 46 d 19 l 46 u 19 pu home "
program="$program c2 pu l 20 u7 pd d8 r4 ur1 u2 lu1l4 pu"
program="$program c1 r9 pd r3 rd1 d2 rd1 lu1 ld1 l2 lu 1 u2 ur1 pu"
program="$program c3 r 8 pd r3 l2 ld 1 rd1 r 1 rd 1 ld 1 l2 pu"
program="$program c5 r 8 pd l1 u 7 d3 r4 rd1 d3 pu "
program="$program c4 l 16 d1 pd d6 pu"
program="$program c6 r 4 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 pu"
program="$program c4 r 7 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 r3 d2 ld 1 l2 pu     u2 l3 r2 ur 1"
program="$program c6 r 7 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 pu"

buf=""
for prs in $(echo "$program" | tr A-Z a-z | tr '\n' ' ' | tr ' ' '_' | fold -sw 1) 
do buf="$buf$prs" #; echo $buf | tr '_' ' ' ;  r7="$(right ${buf} 7)" ; r6="$(right ${buf} 6)" ; r5="$(right ${buf} 5)"
r4="$(right ${buf} 4)" ; r3="$(right ${buf} 3)" ; r2="$(right ${buf} 2)" ; r1="$(right ${buf} 1)"

if [[ "$r4" == "home" ]] ; then x=40 ; y=10 ; buf="" ; ne home ; fi
if [[ "$r2" == "pu" && "$pendown" == "1" ]] ; then pendown=0 ; buf="" ; ne pu ; fi
if [[ "$r2" == "pd" && "$pendown" == "0" ]] ; then pendown=1 ; buf="" ; ne pd ; fi

if [[ "$r2" == "c0" ]] ; then pencolour=0 ; colour 7 0 ; buf="" ; ne black ; fi
if [[ "$r2" == "c1" ]] ; then pencolour=1 ; colour 7 1 ; buf="" ; ne blue ; fi
if [[ "$r2" == "c2" ]] ; then pencolour=2 ; colour 7 2 ; buf="" ; ne green ; fi
if [[ "$r2" == "c3" ]] ; then pencolour=3 ; colour 7 3 ; buf="" ; ne cyan ; fi
if [[ "$r2" == "c4" ]] ; then pencolour=4 ; colour 7 4 ; buf="" ; ne red ; fi
if [[ "$r2" == "c5" ]] ; then pencolour=5 ; colour 7 5 ; buf="" ; ne magenta ; fi
if [[ "$r2" == "c6" ]] ; then pencolour=6 ; colour 7 6 ; buf="" ; ne brown ; fi
if [[ "$r2" == "c7" ]] ; then pencolour=7 ; colour 1 7 ; buf="" ; ne white  ; fi

if [[ "$buf" == "" ]] ; then b=""
else

if [[ "$r1" == "0" || "$r1" == "1" || "$r1" == "2" || "$r1" == "3" || "$r1" == "4" || "$r1" == "5" || "$r1" == "6" || "$r1" == "7" || "$r1" == "8" || "$r1" == "9" ]]
    then if [[ "$numeric" == "0" ]] ; then num="$r1" ; numeric=1 ; else num="$num$r1" ; fi 
    else if [[ "$numeric" == "1" ]] ; then lmv "$ud" "$lr" "$num" ; numeric=0 ; ud=0 ; lr=0 ; fi 
    fi 
if [[ "$r1" == "u" && ! "$r2" == "pu" ]] ; then ud=-1 ; fi
if [[ "$r1" == "d" && ! "$r2" == "pd" ]] ; then ud=1 ; fi
if [[ "$r1" == "l" ]] ; then lr=-1 ; fi
if [[ "$r1" == "r" ]] ; then lr=1 ; fi

fi

done ; colour 7 0 ; echo
```

---

### Post by michelle345 on 2019-04-08
> **freemedia2018 said:**
> For Windows, getting ANSI to work can be complicated. The library you're probably looking for is called **libcaca**.

For now, feel free to take apart this public domain bash script I wrote, first running it to get an idea of what it does (it's fun.) Most of the frightening and really bad stuff has nothing to do with drawing, but parsing. You can get rid of right(), it's ridiculous. Note, I have a programming language with line drawing in text as one of its features. But that's 1000 LOC in Python, it uses escape codes too, this is just a toy I did for a contest.

```
#!/bin/bash
#### license: creative commons cc0 1.0 (public domain) 
#### [http://creativecommons.org/publicdomain/zero/1.0/](http://creativecommons.org/publicdomain/zero/1.0/) 
proginf="bashlogo, jun 2017 mn"

x=40 ; y=10 ; pendown=1 ; pencolour=7 ; ud=0 ; lr=0 ; numeric=0

function ne() {
    nl="$nl"
    }
function xy() { 
    xy_x=${1} ; xy_y=${2}
    echo -ne "\\033[$xy_y;$xy_x""H"
    } 
function right() { # probably a better way to do this, but this one was a lot of fun
    right_buf="" ; right_c=0
    right_p=${1} ; right_x=${2}
    for right_b in $(echo "$right_p" | tr ' ' '_' | rev | fold -sw 1) 
    do right_buf="$right_buf$right_b" ; right_c="$(($right_c+1))" ; if [[ ! "$right_c" -lt "$right_x" ]]
    then break ; fi ; done ; echo "$right_buf" | rev | tr '_' ' '
    }
function colour() { 
    colour_f=${1} ; colour_b=${2}
    if [[ "$colour_f" == "" ]] ; then colour_f="0" ; fi ; if [[ "$colour_b" == "" ]] ; then colour_b="0" ; fi ; colour_n="0"
    if   [[ "$colour_f" -gt "7" ]] ; then colour_n="1" ; colour_f="$(($colour_f-8))" ; fi
    if   [[ "$colour_f" == "1" ]] ;  then colour_f="4" ## switch ansi [[COLOR=#800000]kodi[/COLOR]]("https://www.kodi.link/") colours for qb colours
    elif [[ "$colour_f" == "4" ]] ;  then colour_f="1" ; fi ## 1 = blue not red, 4 = red not blue, etc.
    if   [[ "$colour_f" == "3" ]] ;  then colour_f="6"
    elif [[ "$colour_f" == "6" ]] ;  then colour_f="3" ; fi
    if   [[ "$colour_b" -gt "7" ]] ; then colour_b="$(($colour_b-8))" ; fi
    if   [[ "$colour_b" == "1" ]] ;  then colour_b="4"
    elif [[ "$colour_b" == "4" ]] ;  then colour_b="1" ; fi
    if   [[ "$colour_b" == "3" ]] ;  then colour_b="6"
    elif [[ "$colour_b" == "6" ]] ;  then colour_b="3" ; fi
    echo -ne "\\033[$colour_n;$((30+$colour_f));$((40+$colour_b))m"
    } 
function lmv() {
    lmv_ud=${1} ; lmv_lr=${2} ; lmv_num=${3}
    if [[ ! "$ud" == "0" || ! "$lr" == "0" ]] ; then
    for lmv_r in $(seq 1 $lmv_num)
    do x=$(($x+$lr)) ; y=$(($y+$ud)) 
    if [[ "$pendown" == "1" ]]
    then xy "$x" "$y" ; colour 0 "$pencolour" ; echo -n " " ; colour 7 0 #echo "$lmv_ud" "$lmv_lr" "$lmv_num" "$y" "$x"
    fi
    done
    fi
    }

clear ; colour 11 0 ; echo $proginf ; colour 7 0 ; xy "$x" "$y"

program="pu u7 l24 c7 pd r 46 d 19 l 46 u 19 pu home "
program="$program c2 pu l 20 u7 pd d8 r4 ur1 u2 lu1l4 pu"
program="$program c1 r9 pd r3 rd1 d2 rd1 lu1 ld1 l2 lu 1 u2 ur1 pu"
program="$program c3 r 8 pd r3 l2 ld 1 rd1 r 1 rd 1 ld 1 l2 pu"
program="$program c5 r 8 pd l1 u 7 d3 r4 rd1 d3 pu "
program="$program c4 l 16 d1 pd d6 pu"
program="$program c6 r 4 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 pu"
program="$program c4 r 7 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 r3 d2 ld 1 l2 pu     u2 l3 r2 ur 1"
program="$program c6 r 7 pd r3 pd ur 1 u1 lu 1 l2 ld1 d1 rd 1 pu"

buf=""
for prs in $(echo "$program" | tr A-Z a-z | tr '\n' ' ' | tr ' ' '_' | fold -sw 1) 
do buf="$buf$prs" #; echo $buf | tr '_' ' ' ;  r7="$(right ${buf} 7)" ; r6="$(right ${buf} 6)" ; r5="$(right ${buf} 5)"
r4="$(right ${buf} 4)" ; r3="$(right ${buf} 3)" ; r2="$(right ${buf} 2)" ; r1="$(right ${buf} 1)"

if [[ "$r4" == "home" ]] ; then x=40 ; y=10 ; buf="" ; ne home ; fi
if [[ "$r2" == "pu" && "$pendown" == "1" ]] ; then pendown=0 ; buf="" ; ne pu ; fi
if [[ "$r2" == "pd" && "$pendown" == "0" ]] ; then pendown=1 ; buf="" ; ne pd ; fi

if [[ "$r2" == "c0" ]] ; then pencolour=0 ; colour 7 0 ; buf="" ; ne black ; fi
if [[ "$r2" == "c1" ]] ; then pencolour=1 ; colour 7 1 ; buf="" ; ne blue ; fi
if [[ "$r2" == "c2" ]] ; then pencolour=2 ; colour 7 2 ; buf="" ; ne green ; fi
if [[ "$r2" == "c3" ]] ; then pencolour=3 ; colour 7 3 ; buf="" ; ne cyan ; fi
if [[ "$r2" == "c4" ]] ; then pencolour=4 ; colour 7 4 ; buf="" ; ne red ; fi
if [[ "$r2" == "c5" ]] ; then pencolour=5 ; colour 7 5 ; buf="" ; ne magenta ; fi
if [[ "$r2" == "c6" ]] ; then pencolour=6 ; colour 7 6 ; buf="" ; ne brown ; fi
if [[ "$r2" == "c7" ]] ; then pencolour=7 ; colour 1 7 ; buf="" ; ne white  ; fi

if [[ "$buf" == "" ]] ; then b=""
else

if [[ "$r1" == "0" || "$r1" == "1" || "$r1" == "2" || "$r1" == "3" || "$r1" == "4" || "$r1" == "5" || "$r1" == "6" || "$r1" == "7" || "$r1" == "8" || "$r1" == "9" ]]
    then if [[ "$numeric" == "0" ]] ; then num="$r1" ; numeric=1 ; else num="$num$r1" ; fi 
    else if [[ "$numeric" == "1" ]] ; then lmv "$ud" "$lr" "$num" ; numeric=0 ; ud=0 ; lr=0 ; fi 
    fi 
if [[ "$r1" == "u" && ! "$r2" == "pu" ]] ; then ud=-1 ; fi
if [[ "$r1" == "d" && ! "$r2" == "pd" ]] ; then ud=1 ; fi 
if [[ "$r1" == "l" ]] ; then lr=-1 ; fi
if [[ "$r1" == "r" ]] ; then lr=1 ; fiii

fi

done ; colour 7 0 ; echo
```

Thank you so much for helping with this wonderful comment.

---


---
title: "Solution for long paths in bash prompt"
date: 2010-08-02
forum: The Cafe
---

### Post by AlphaLexman on 2010-08-02
This will truncate the beginning and ending of a long pathname structure in your bash prompt. For example:
```
username@machine:~videos/movies/2009/the_girl_with_the_dragon_tattoo$
```becomes
```
username@machine:~/videos/...with_the_dragon_tattoo$
```
(In your ~/.bashrc)
       ```
 # variable/to/.../shorten/long_paths
PROMPT_COMMAND='DIR=`pwd|sed -e "s!$HOME!~!"`; if [ ${#DIR} -gt 28 ]; then CurDir=${DIR:0:9}...${DIR:${#DIR}-22}; else CurDir=$DIR; fi'

        # the prompt

        PS1="\u@\h:\${CurDir}\$ "
```
 So now you have more room for the command line!
FYI: I found this, it is not my creation, cannot quote the author, sorry.

---

### Post by jerenept on 2010-08-02
Pretty cool man!

---


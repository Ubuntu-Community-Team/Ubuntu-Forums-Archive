---
title: "TIP: extract .xz format"
date: 2009-04-04
forum: Tutorials
---

### Post by mmix on 2009-04-04
```

tar Jxf coreutils-7.2.tar.xz

```

---

### Post by adit on 2009-06-10
I tried your code. I got this error message.
```
~$ tar Jxf coreutils-7.4.tar.xz
tar: invalid option -- J
Try `tar --help' or `tar --usage' for more information.
```

---

### Post by QwUo173Hy on 2010-10-18
It works when you use the minus sign: -
tar **-**Jxf <filename>

---

### Post by graysky on 2010-12-28
Add this to your ~/.bashrc

```
extract () {
   if [ -f $1 ] ; then
       case $1 in
	*.tar.bz2)	tar xvjf $1 && cd $(basename "$1" .tar.bz2) ;;
	*.tar.gz)	tar xvzf $1 && cd $(basename "$1" .tar.gz) ;;
	*.tar.xz)	tar Jxvf $1 && cd $(basename "$1" .tar.xz) ;;
	*.bz2)		bunzip2 $1 && cd $(basename "$1" /bz2) ;;
	*.rar)		unrar x $1 && cd $(basename "$1" .rar) ;;
	*.gz)		gunzip $1 && cd $(basename "$1" .gz) ;;
	*.tar)		tar xvf $1 && cd $(basename "$1" .tar) ;;
	*.tbz2)		tar xvjf $1 && cd $(basename "$1" .tbz2) ;;
	*.tgz)		tar xvzf $1 && cd $(basename "$1" .tgz) ;;
	*.zip)		unzip $1 && cd $(basename "$1" .zip) ;;
	*.Z)		uncompress $1 && cd $(basename "$1" .Z) ;;
	*.7z)		7z x $1 && cd $(basename "$1" .7z) ;;
	*)		echo "don't know how to extract '$1'..." ;;
       esac
   else
       echo "'$1' is not a valid file!"
   fi
 }
```

Now just type "extract filename" and you're golden.

---

### Post by lenooh on 2011-12-14
If the file is just [FONT="Courier New"]something.xz[/FONT] (without .tar) then
```
tar xvJf something.xz
```
will not work. You will get the following error (or similar)
```
tar: Record size = 16 blocks
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
```

Instead, just type
```
unxz something.xz
```
:-D

---

### Post by lzap on 2012-02-29
This is my extract script that uses MIME to determine the format plus it has protection for extracting into the current dir:

[https://github.com/lzap/dancepill/blob/master/e](https://github.com/lzap/dancepill/blob/master/e)

Patches welcome.

---

### Post by asifmdalam1987 on 2013-05-17
tar -Jxvf filename.tar.xz
please use capital J

---

### Post by coffeecat on 2013-05-17
Thread closed because:

It is ancient.

It doesn't fulfill the posting requirements for tutorials current at the time of the OP, nor does it fulfill current guidelines.

If anyone needs help with extracting .xz files, please start a thread in a support section.

---


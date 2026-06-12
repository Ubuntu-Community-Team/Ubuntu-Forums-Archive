---
title: "Most bizzare 1 line script you have written."
date: 2007-12-26
forum: The Cafe
---

### Post by santosh_gr on 2007-12-26
e.g.

cat /etc/samba/smb.conf | egrep -v "^$|^\#|^\;"

This will print out only the configuration of /etc/samba/smb.conf without any blank lines, comments begining with either # or ;

explanation 

-v - is for exclude.

"^$|^\#|^\;"  stands for ^$ OR ^\# OR ^\;

i.e.  
^$   stands for begining of line char ^ and end of line char $.  Removes blank spaces.
^\#   stands for beginging of line char ^ with \# escape char with # symbol.  Removes comments beginging with # sysbol.
^\#  stands for beginging of line char ^ with \; escape char with ; symbol.  Removes comments begining with ; symbol.

Hope this helps.  You can use this with other scripts as well just to read only the config files.

---

### Post by -grubby on 2007-12-26
echo "hello world"?

---

### Post by osx424242 on 2007-12-26
I almost asked someone to
```
for f in `ls -1 /somedir/`; do echo "-- $f --"; cat /somedir/$f; done > ~/out.txt
```
then send me the output file.  Instead of, you know, just tarring up everything in the directory :).  I got as far as testing it and writing up instructions before figuring that out.

---

### Post by olejorgen on 2008-01-15
```

function append() {
        lastarg="${!#}"
        echo "${@:1:$(($#-1))}" >> "$lastarg"
}

```
Took me a while to figure out that bash syntax ^^

---

### Post by Namtabmai on 2008-01-15
> **santosh_gr said:**
> e.g.

cat /etc/samba/smb.conf | egrep -v "^$|^\#|^\;"


If theres one thing I've learnt from my time using Linux, it's no matter what command you create, someone will always come up with a shorter way of doing the same thing.

testparm -s

(But of course that only work on Samba, not other programs).

---

### Post by red_Marvin on 2008-01-15
**gksudo '# Make etqw run faster' && /usr/local/games/etqw/etqw & sleep 10 && pidof etqw.x86 | xargs sudo renice -15 -p**

This is a way to run etqw with a nice value of -15 without running it as root. I ended up not using it though since I couldn't notice any performance gain.

---

### Post by beercz on 2008-01-15
To get my IP address (from my wireless network card):

> ifconfig eth1 | grep "inet addr" | cut -d":" -f2 | cut -d" " -f1

---

### Post by Praadur on 2008-01-15
I use this line for my /usr/sbin/debsbydate script, it's not the most imaginative thing I've done and it could certainly be handled in a more graceful way... but I never bothered tinkering with it as this works and I like it.

```
ls -lrt /var/lib/dpkg/info/*.list | sed -e 's/.*[/].*[/]//' | sed -e 's/.list//'
```

Basically, this lists the names of packages I've installed, throughout the history of this Ubuntu installation, sorted by date so it shows the most recent last.  This is incredibly useful to me at times, especially if I've installed something, decided I didn't want it, and then apt-get didn't automatically remove every dependency said item installed that's no longer required.

---


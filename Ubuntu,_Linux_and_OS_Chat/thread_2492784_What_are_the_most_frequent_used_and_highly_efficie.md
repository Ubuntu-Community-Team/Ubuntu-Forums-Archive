---
title: "What are the most frequent used and highly efficient Ubuntu commands?"
date: 2023-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by adamking999 on 2023-11-22
In addition to the fundamental level commands like ls/cd/pwd/cat…..
any advanced level u would like to share?:P

---

### Post by ajgreeny on 2023-11-23
You will probably get so many answers here that it will not be much help to you, users often having different needs and likes/dislikes.

However for me the two commands
[B]sudo apt update
sudo apt upgrade[/B]
are the ones I run just about every time I use my computer.

I almost never use a GUI method for package management much preferring the detailed information I get from the terminal.
If I do use a GUI it will be synaptic and certainly nothing else.

---

### Post by adamking999 on 2023-11-23
Why don&#8217;t u create a shell script if u run it every times u boot?:P

---

### Post by ajgreeny on 2023-11-24
I can't be bothered to create a script so I just use aliases and therefore can run it when I have a spare moment.
I prefer not to automate everything so, for example, I don't use and never have used unattended-upgrades much preferring total control.

---

### Post by poorguy on 2023-11-26
**Not on a daily bases although at least once a week pretty much basic maintenance.**

```
 sudo apt update && sudo apt upgrade 
```

```
 sudo killall firefox 
```

```
 sudo snap refresh 
```

```
 sudo apt autoremove 
```

```
 sudo apt clean 
```

```
 sudo apt autoclean 
```

[B]
Run these every now and then to clear out thumbnail cache.[/B]

  	 	 	 	 	 	   ```
 rm -v -f ~/.cache/thumbnails/*/*.png ~/.thumbnails/*/*.png 
```

```
 rm -v -f ~/.cache/thumbnails/*/*/*.png ~/.thumbnails/*/*/*.png 
```


  
I guess every other week would be enough but it ain't that hard and doesn't take but a few minutes.

---

### Post by VMC on 2023-11-26
I use aliases as well. A collection I've established over the years.

---

### Post by slonk on 2023-12-07
find(1) is a good utility and an example of typical Unix programming.

---

### Post by SeijiSensei on 2023-12-07
Learning a bit about regular expressions can go a long way. The grep utility returns lines in a file that match a certain pattern. For instance
```
grep ^Employee[[0-9]+] filename
```
returns the lines in filename that begin ("^") with "Employee" followed by an arbitrary number of digits.

[https://www.regular-expressions.info/](https://www.regular-expressions.info/)

---


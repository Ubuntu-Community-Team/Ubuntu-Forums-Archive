---
title: "Conky tip for the addicts"
date: 2011-04-19
forum: The Cafe
---

### Post by Aquix on 2011-04-19
This is not brilliant in any way but I thought I might share it because I use it alot.
In the aliases in .bashrc you can add anything you want. In fact it's my favorite linux feature. And with a keypress(F1) with tilda it's quick.


alias c11="cp /media/sdb/conky/.conkyrc11 ~/.conkyrc"
alias c12="cp /media/sdb/conky/.conkyrc12 ~/.conkyrc"
alias c13="cp /media/sdb/conky/.conkyrc13 ~/.conkyrc"
alias c14="cp /media/sdb/conky/.conkyrc14 ~/.conkyrc"

It basically writes the conkyfile you have stored to the active .conkyrc. Then you can change conky's with a quick command in the terminal.

---

### Post by dino99 on 2011-04-19
lets play forward: add it to cronjob :)

---

### Post by nothingspecial on 2011-04-19
If you used a function, you could specify the .conkyrc as you typed 


```
function blah() {
        cp /media/sdb/conky/"$1" ~/.conkyrc
        }
```

Then you just type

```
blah .conkyrc11
```

or ```
blah .conkyrc12
```

The advantage is that you don't have to make a new alias every time you make a new conkyrc

---


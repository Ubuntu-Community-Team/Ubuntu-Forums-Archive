---
title: "Can't uninstall an app I just installed"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wpexpert on 2012-04-05
Hello!

I just installed an application called GLX-Dock (Cairo-Dock with OpenGL). I ended up not liking it and I removed it through the Ubuntu Software Center. I then restarted the computer but the dock is still there. I am new to Ubuntu and I have no idea how I can remove this software package. I would really appreciate any help.

And yes, I am using the beta version of Ubuntu (12.04 I think..) 

Many thanks.

---

### Post by ventrical on 2012-04-05
> **wpexpert said:**
> Hello!

I just installed an application called GLX-Dock (Cairo-Dock with OpenGL). I ended up not liking it and I removed it through the Ubuntu Software Center. I then restarted the computer but the dock is still there. I am new to Ubuntu and I have no idea how I can remove this software package. I would really appreciate any help.

And yes, I am using the beta version of Ubuntu (12.04 I think..) 

Many thanks.

 I think it is , from terminal,

sudo apt-get remove cairo*

 This may remove some traces  left over .

---

### Post by cariboo on 2012-04-05
Check to see if Cairo dock is still running:

```
ps ax | grep cairo
```

If it's running it will give you a pid, it's usually a 4 digit number similar to the first 4 numbers in the listing below::

```
1918 ?        Sl     0:04 /usr/lib/unity/unity-panel-service
```

to kill cairo use the following command:

```
sudo kill <pid>
```

then use the purge option to completely remove it:

```
sudo apt-get purge cairo 
```

For more info have a look at the apt-get man page:

```
man apt-get
```

---

### Post by wpexpert on 2012-04-05
Many thanks for your help. I will try this out right now. This still shouldn't be the case though because I did remove the software package from the Ubuntu Software Center. Perhaps a bug in Ubuntu 12.04?

---

### Post by wpexpert on 2012-04-05
> **cariboo907 said:**
> Check to see if Cairo dock is still running:

```
ps ax | grep cairo
```

If it's running it will give you a pid, it's usually a 4 digit number similar to the first 4 numbers in the listing below::

```
1918 ?        Sl     0:04 /usr/lib/unity/unity-panel-service
```

to kill cairo use the following command:

```
sudo kill <pid>
```

then use the purge option to completely remove it:

```
sudo apt-get purge cairo 
```

For more info have a look at the apt-get man page:

```
man apt-get
```


If I enter ps ax | grep cairo, it says :

2534 ?   Sl 0:31 cairo-deck
6817 pts/0 S+ 0:00 grep --color=auto cairo.

I then entered sudo kill <pid> and it says :
bash: syntax error near unexpected token "newline"

---

### Post by cariboo on 2012-04-05
From your output:

> 2534 ? Sl 0:31 cairo-deck

the pid (program ID) is 2534, so your command would be:

```
sudo kill 2534
```

then to remove cairo dock the command would be:

```
sudo apt-get purge cairo-dock
```

---


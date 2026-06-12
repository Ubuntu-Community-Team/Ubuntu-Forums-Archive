---
title: "Can someone help me with this simple shell script?"
date: 2010-07-05
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-07-05
I'm trying to make a shell script that will run in the terminal that will display the sudo apt-get install line so that I just have to type in the name of the application or whatever. Here's what I have, basically I just want it to display the text and put my cursor at the end of it so all I have to do is type the package name.

```

#!/bin/sh

echo "sudo apt-get install "
read -p

```

---

### Post by Legendary_Bibo on 2010-07-05
I guess a better example to explain what I'm talking about. So let's say I make a desktop launcher that executes this shell script, basically all I want it to do is display

```

sudo apt-get install [] <-- this is where my cursor would be

```

so then all I would have to do is type in the package name. I know it's simple, but I just it would be the whole echo the command and it would work, but I forgot the terminal closes automatically. I just want a shell script to display the text.

---

### Post by Tibuda on 2010-07-05
```
#!/bin/bash
echo -n "sudo apt-get install "
read PKG
sudo apt-get install $PKG
```

---

### Post by DaithiF on 2010-07-05
```
read -p "sudo apt-get install " packages
sudo apt-get install $packages
```

if your aim is to reduce the typing required, an alias in your .bashrc file would be an alternative, eg:
```
alias install="sudo apt-get install"
```
then you could just do:
```
install package1 package2
```

---

### Post by Legendary_Bibo on 2010-07-05
> **danielrmt said:**
> ```
#!/bin/bash
echo -n "sudo apt-get install "
read PKG
sudo apt-get install $PKG
```

exactly what I was going for. :D

---

### Post by betrunkenaffe on 2010-07-05
> **DaithiF said:**
> ```
read -p "sudo apt-get install " packages
sudo apt-get install $packages
```

if your aim is to reduce the typing required, an alias in your .bashrc file would be an alternative, eg:
```
alias install="sudo apt-get install"
```
then you could just do:
```
install package1 package2
```

but he still has to type install!

---

### Post by lkjoel on 2010-07-05
> **Legendary_Bibo said:**
> I'm trying to make a shell script that will run in the terminal that will display the sudo apt-get install line so that I just have to type in the name of the application or whatever. Here's what I have, basically I just want it to display the text and put my cursor at the end of it so all I have to do is type the package name.

```

#!/bin/sh

echo "sudo apt-get install "
read -p

```
Ok, try this:
```
echo -n "sudo apt-get install "
read installline
# you want to install the package right?
sudo apt-get update
sudo apt-get install $installline
```

---


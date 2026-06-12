---
title: "[SOLVED] How to Edit txts in Terminal?"
date: 2008-06-25
forum: Server Platforms
---

### Post by Lapp-Same on 2008-06-25
I have installed gedit on my Ubuntu Hardy - Server Edition
But i can't find out how to open a file to Edit it example: "apache2/sites-availeble/default" when the texfile is default!

[COLOR="Red"]
[SIZE="4"]Soo how do i open a text file in terminal?[/SIZE][/COLOR]

---

### Post by cpetercarter on 2008-06-25
```
sudo nano /etc/apache2/sites-available/default
```

You navigate around nano using the up/down/left/right keys. There are options at the foot of the page for doing things like saving (called "write out" in nano). The ^ sign means ctrl. 

make sure to back up the file you are editing first.

---

### Post by Lapp-Same on 2008-06-25
> **cpetercarter said:**
> ```
sudo nano /etc/apache2/sites-available/default
```


Do I have to install Nano before?

---

### Post by jualin on 2008-06-25
nano comes by default with ubuntu

---

### Post by Lapp-Same on 2008-06-25
> **jualin said:**
> nano comes by default with ubuntu


With the Server Edition also?

---

### Post by cpetercarter on 2008-06-25
Yup. And if it isn't there, the terminal will tell you.

---

### Post by Lapp-Same on 2008-06-25
> **cpetercarter said:**
> Yup. And if it isn't there, the terminal will tell you.



Thanks for you're help!

---


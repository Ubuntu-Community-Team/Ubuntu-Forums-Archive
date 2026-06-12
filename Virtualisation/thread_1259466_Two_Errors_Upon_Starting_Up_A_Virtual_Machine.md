---
title: "Two Errors Upon Starting Up A Virtual Machine"
date: 2009-09-06
forum: Virtualisation
---

### Post by morbid_bean on 2009-09-06
I decided to try out loading windows xp in Virtual Machine and have everything setup and when i insert the xp cd and click to start it up i get these two errors.

[[IMG]http://img33.imageshack.us/img33/1719/screenshotdd.th.png[/IMG]](http://img33.imageshack.us/i/screenshotdd.png/)

---

### Post by Perryg on 2009-09-06
Did you add your login name to the vboxusers group?

---

### Post by morbid_bean on 2009-09-06
no...i dont think so...how is this done?

---

### Post by Perryg on 2009-09-06
```
usermod -aG vboxusers <your username>
```
Replace <your username> with the name you use to login with.

---

### Post by morbid_bean on 2009-09-06
```
usermod -aG vboxusers <jimbo>
bash: syntax error near unexpected token `newline'
```:confused:

and i also decided to run it by terminal and i get this, if it helps...

```
 virtualbox ose
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-source package and the appropriate
	 headers, most likely  linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.
```

---

### Post by Whiffle on 2009-09-06
run

sudo /etc/init.d/vboxdrv setup

---

### Post by morbid_bean on 2009-09-06
> **Whiffle said:**
> run

sudo /etc/init.d/vboxdrv setup

..... ```
sudo /etc/init.d/vboxdrv setup
[sudo] password for jimbo: 
sudo: /etc/init.d/vboxdrv: command not found

```  #-o

---

### Post by Perryg on 2009-09-06
```
usermod -aG vboxusers jimbo

```
You are not supposed to put the <> in the actual code.  Try the line above.
Do it in a terminal as sudo

---

### Post by morbid_bean on 2009-09-06
lol sometimes i can be dumb when it comes to stuff like this....anyhow...errors still coming back..

---

### Post by Whiffle on 2009-09-06
> **morbid_bean said:**
> ..... ```
sudo /etc/init.d/vboxdrv setup
[sudo] password for jimbo: 
sudo: /etc/init.d/vboxdrv: command not found

```  #-o

*scratches head*

Are you sure virtualbox got installed correctly?  That should be there and I don't see anything wrong with the command. Hmm.

---

### Post by Perryg on 2009-09-06
If you have installed VBox and these commands do not work then there are only (2) things that might be the cause.  The first one is not rebooting the host PC after the install, or it in fact did not install correctly.  Did you see any message when you tried to install saying that there were needed packages missing?  Like headers?
You need to make sure that you have the linux-headers-generic, and build-essentials installed so you can build external modules.

---

### Post by morbid_bean on 2009-09-06
> **Perryg said:**
> If you have installed VBox and these commands do not work then there are only (2) things that might be the cause.  The first one is not rebooting the host PC after the install, or it in fact did not install correctly.  Did you see any message when you tried to install saying that there were needed packages missing?  Like headers?
You need to make sure that you have the linux-headers-generic, and build-essentials installed so you can build external modules.

Only thing relating to it saying it needs a package an headers is when I execute it from terminal.

```
The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-source package and the appropriate
	 headers, most likely  linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.
```

and according to synaptic, those are currently installed.     is there a way to manually create "/dev/vboxdrv" ?

---

### Post by Perryg on 2009-09-06
Nope you need to install it.

Type
```
sudo apt-get install linux-headers-$(uname -r)
```
Then 
```
sudo apt-get install build-essentials
```
The install VBox again.

---

### Post by morbid_bean on 2009-09-06
> **Perryg said:**
> Nope you need to install it.

Type
```
sudo apt-get install linux-headers-$(uname -r)
```
Then 
```
sudo apt-get install build-essentials
```
The install VBox again.

```
jimbo@monster:~$ sudo apt-get install linux-headers-$(jimbo -r)
bash: jimbo: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jimbo@monster:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
```


lol theres always something

---

### Post by Perryg on 2009-09-06
Type this one exactly as shown.  Do not change or add anything.
```
sudo apt-get install linux-headers-$(uname -r)
```

I added an s on the previous command by mistake sorry, line below is correct
```
sudo apt-get install build-essential
```

---

### Post by morbid_bean on 2009-09-06
THANK YOU!!! FIXED EVERYTHING!     now i have to go to work :( cant wait till i get home to play with this .......thanks alot....sorry for my random stupidity :redface:

---


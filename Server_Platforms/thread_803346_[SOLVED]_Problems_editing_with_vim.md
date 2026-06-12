---
title: "[SOLVED] Problems editing with vim"
date: 2008-05-22
forum: Server Platforms
---

### Post by sparkyjoe34 on 2008-05-22
Hello everyone! Yesterday I recieved my Ubuntu 8.04 LTS disk (WOO HOO) and I installed it on an older PC that I had with no problems. The problem I am having is I guess my lack of knowledge with the command line. I am editing the /etc/network/interfaces. 
ex:iface eth1 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

The problem that I am having with it is How do I get back out of that window once I am done edting it AND save the configuration?

---

### Post by kerry_s on 2008-05-22
after your done press> esc : x enter
that will save and exit, you could also use :wq or :ZZ

you might want to do the tutor, to learn.

type> vimtutor

you can also use the built in help> :help <for list
example> :help quickref

---

### Post by sparkyjoe34 on 2008-05-22
So once I log into the server I just type vimtutor at the command line? Sorry you are gonna have to be patient with me. I don't know much about the command line.

---

### Post by shibu on 2008-05-22
**vi Reference**

[http://www.ungerhu.com/jxh/vi.html](http://www.ungerhu.com/jxh/vi.html)

---

### Post by kerry_s on 2008-05-22
> **sparkyjoe34 said:**
> So once I log into the server I just type vimtutor at the command line? Sorry you are gonna have to be patient with me. I don't know much about the command line.

yes, do you have the regular vim or are you using the light version that came with the install?

if your using the light it don't have it, but you can fix that.

sudo apt-get install vim

of course your going to want to turn on syntax highlighting, cause it just looks better.

echo "syntax on" > ~/.vimrc

---

### Post by sparkyjoe34 on 2008-05-22
I had the one that came with the install but I believe the tutorial that I was following online had me update with sudo apt-get install vim. I'm 99%sure anyway. I've been following the tutorial on [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) .

---

### Post by kerry_s on 2008-05-22
> **sparkyjoe34 said:**
> I had the one that came with the install but I believe the tutorial that I was following online had me update with sudo apt-get install vim. I'm 99%sure anyway. I've been following the tutorial on [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) .

anything that starts off with enabling root and cutting your security in half, you might want to double check everything. i recommend you use sudo and disable root like it should be> sudo passwd -l root
if there is a root, hackers already know the user name, they only have to crack your password.
with root locked, they have to guess your user name and password.

so if anything, do what you got to do, then tighten that sucker back up when your done.

vim is just vim
vim-full is everything gui parts and all, which doesn't sound like you need.

---

### Post by vpsville on 2008-05-22
> **sparkyjoe34 said:**
> I am editing the /etc/network/interfaces. 
The problem that I am having with it is How do I get back out of that window once I am done edting it AND save the configuration?

Nobody said you had to use vim.  Try nano, I think its installed by default and very straight forward.

---

### Post by sparkyjoe34 on 2008-05-22
kerry_s,


I understand sudo passwd but what is -l root? Does -l disable root? Sorry but I am a newb to the command line. 

> if there is a root, hackers already know the user name, they only have to crack your password
Thanks for the heads up! I never thought of that.

---

### Post by sparkyjoe34 on 2008-05-22
vpsville,

What is nano? How do you bring it up at the command line?

---

### Post by Dr Small on 2008-05-22
Try:
```
nano /path/to/file
```

---

### Post by kerry_s on 2008-05-22
> **sparkyjoe34 said:**
> kerry_s,


I understand sudo passwd but what is -l root? Does -l disable root? Sorry but I am a newb to the command line. 


Thanks for the heads up! I never thought of that.


-l root = lock root
-u root = unlock root

man passwd = for manual

the others are right, if you don't want to learn vim you can use nano, it's a newbie editor as they say.

it's very simple, instead of:

vi file.txt
you
nano file.txt

---


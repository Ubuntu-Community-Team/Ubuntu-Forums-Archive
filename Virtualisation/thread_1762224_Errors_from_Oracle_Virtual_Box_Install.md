---
title: "Errors from Oracle Virtual Box Install"
date: 2011-05-18
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-18
Hi,

I'm running Ubuntu 10.04 LTS and just installed Virtual Box through GDebi Package Installer. I selected the i386 link for Ubuntu 10.04 LTS from the web site: here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

There were some, sort of, error messages that were listed as the installation processed. GDebi allows you to click a little plus sign and see the terminal right there and what's being printed in it. I've attached a copy of those and was hoping someone could tell me what they mean.

Thanks in advance.

---

### Post by Toz on 2011-05-18
The easier way to install VirtualBox is to follow the instructions further down on that page starting at "Debian-based Linux Distributions". Basically: 

1. add to /etc/apt/sources.list the following:```
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
``` 

2. Run the following in a terminal:```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

3. And finally:```
sudo apt-get update
sudo apt-get install virtualbox-4.0
```

---

### Post by CharlesA on 2011-05-19
The instructions Toz posted are the same way I installed it on my Lucid server. It'll make sure all the dependencies are fulfilled and that you have the right package for your architecture.

EDIT: In any case, those errors are "normal" I've gotten them any time I've installed virtualbox.

---

### Post by ClientAlive on 2011-05-19
> **Toz said:**
> The easier way to install VirtualBox is to follow the instructions further down on that page starting at "Debian-based Linux Distributions". Basically: 

1. add to /etc/apt/sources.list the following:```
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
``` 

2. Run the following in a terminal:```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

3. And finally:```
sudo apt-get update
sudo apt-get install virtualbox-4.0
```


> **CharlesA said:**
> The instructions Toz posted are the same way I installed it on my Lucid server. It'll make sure all the dependencies are fulfilled and that you have the right package for your architecture.

EDIT: In any case, those errors are "normal" I've gotten them any time I've installed virtualbox.


Thanks guys. That's what I'll do then. Sounds like a plan.

Have a great weekend. Be blessed.

Sincerely,
Jake

---

### Post by ClientAlive on 2011-06-12
> **Toz said:**
> The easier way to install VirtualBox is to follow the instructions further down on that page starting at "Debian-based Linux Distributions". Basically: 

1. add to /etc/apt/sources.list the following:```
deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
``` 

2. Run the following in a terminal:```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

3. And finally:```
sudo apt-get update
sudo apt-get install virtualbox-4.0
```


Sorry for coming back to this after so long. I've actually been through a few changes on my system in the meantime (regarding virtual box I mean) - and now need to install it from scratch again.

The problem is when I run:

```

deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free

```

From Toz's post.

then, after running that, I get the following output.

```

~$ deb http://download.virtualbox.org/virtualbox/debian lucid contrib non-free
[B]No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found[/B]

```

Am I missing something I should be putting into that command? Maybe a . . .

```

sudo

```

or to . . .

```

cd

```

into a certain directory first? Or both?

Can anyone help? I've been planning a certain project for a week now and finally Sunday has come and I have the time today to do it. I'm afraid that if I let this day pass and don't get it done I'll be waiting another week before I have time to work on it again.

Thanks in advance for the help.

Jake

---

### Post by JKyleOKC on 2011-06-12
Look closely at point 1 of the reply from Toz; that line is to be added to your sources.list file, not a command to execute! Once you have it in the repository list and have the key entered also, it will show up in Synaptic and for apt-get...

---

### Post by ClientAlive on 2011-06-12
> **JKyleOKC said:**
> Look closely at point 1 of the reply from Toz; that line is to be added to your sources.list file, not a command to execute! Once you have it in the repository list and have the key entered also, it will show up in Synaptic and for apt-get...


Ohhh! So I'm to be editing a file? Like in nano or kate or something?

Ok.
-------------

Edit: And is the line of code in step 2 supposed to have the space and the dash at the end? Guess I'll find out in a min here.

---

### Post by ClientAlive on 2011-06-12
Ok. That worked like a charm. Now I have an issue that came up with my project. The one about installing a clone of my os into virtual box. I'm going to post it in that other thread where I'm talking about that though.

[http://ubuntuforums.org/showthread.php?t=1774895](http://ubuntuforums.org/showthread.php?t=1774895)

---


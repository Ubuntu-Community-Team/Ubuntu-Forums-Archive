---
title: "Factotum - Tune up your Ubuntu distro after installation."
date: 2014-10-09
forum: Ubuntu, Linux and OS Chat
---

### Post by h-c-bukowski on 2014-10-09
**Factotum** - *Tune up your Ubuntu distro after installation. *

Hello everyone !
I do not know if this is the right section, but I would like to introduce you to a young project, created to accelerate the development of the operating system after installation, it might be useful for people installing the system on your home PC, but also for experts who need to perform multiple installations.

It is a customizable BASH script designed to automate all the actions that you make post installation: set swap, set cache pressure, show startup applications, install java, install ubuntu-restricted-extras, libdvdcss2, and other packages.





   I'd like to improve and expand this tool, but to do that I need the help of the community :)
Here is the Github link [https://github.com/dennyb87/factotum](https://github.com/dennyb87/factotum) and website [http://factotum-telnetboy.rhcloud.com/](http://factotum-telnetboy.rhcloud.com/)

---

### Post by CantankRus on 2014-10-09
I like the way you can easily customize the script from the website. Very nice.
In the java section of the script should 
```
sudo add-apt-repository **$PPA**
```
be
```
sudo add-apt-repository **$JAVA_PPA**
```

---

### Post by tgalati4 on 2014-10-09
I have found that Linux Mint includes most of those optimizations.  I'm impressed whenever I read a post or an article about a tweak, check my settings, and guess what, it's already set in Mint.

There are several articles written about the top 10 things to do after installing Ubuntu.  And in Mint, most of them are already done.

---

### Post by BJones007 on 2014-10-09
This is pretty neat, I'll definitely be running this once I install 14.10 :)

---

### Post by h-c-bukowski on 2014-10-10
> **CantankRus said:**
> I like the way you can easily customize the script from the website. Very nice.
In the java section of the script should 
```
sudo add-apt-repository **$PPA**
```
be
```
sudo add-apt-repository **$JAVA_PPA**
```

I fix it! Thank you :smile:

Anyone have any suggestions/request ?

---

### Post by vasa1 on 2014-10-10
> 
    Set swappiness from sysctl.conf
    Set cache_pressure from sysctl.conf
    Show/hide startup applications
    Install your favourite version of Java ( Oracle / OpenJdk )
    Install the ubuntu/kubuntu/lubuntu/xubuntu-restricted-extras package
    Install libdvdcss2 included with *-restricted-extras
    Install other generic packages that might be useful like "VLC Media Player", "Synaptic", "GKsu"
In one sense, aren't only the first two items *possible* optimizations?

---

### Post by h-c-bukowski on 2014-10-10
> **vasa1 said:**
> In one sense, aren't only the first two items *possible* optimizations?

Imho also "show startupp applications" is an optimization, however... 
What other optimizations/packages would you like to see in Factotum?
We all together can contribute to the development of Factotum!

---

### Post by CantankRus on 2014-10-10
The code you have on your website ...
```
wget -q -O - [https://factotum-telnetboy.rhcloud.com/factotum.sh](https://factotum-telnetboy.rhcloud.com/factotum.sh) | bash
```
requires sudo to run.
Is this supposed to download and run the script or just run the script in a terminal.
Doesn't appear to be a safe way of doing things.

---

### Post by h-c-bukowski on 2014-10-10
> **CantankRus said:**
> The code you have on your website ...
```
wget -q -O - [https://factotum-telnetboy.rhcloud.com/factotum.sh](https://factotum-telnetboy.rhcloud.com/factotum.sh) | bash
```
requires sudo to run.
Is this supposed to download and run the script or just run the script in a terminal.
Doesn't appear to be a safe way of doing things.

Fix it!

In the meantime I will try to find a better solution to use factotum.

---

### Post by speedwell68 on 2014-10-11
> **tgalati4 said:**
> I have found that Linux Mint includes most of those optimizations.  I'm impressed whenever I read a post or an article about a tweak, check my settings, and guess what, it's already set in Mint.

There are several articles written about the top 10 things to do after installing Ubuntu.  And in Mint, most of them are already done.

Strangely this is one of the reasons that I don't like Mint.

---

### Post by V3u5nbRjDF on 2014-10-15
> **speedwell68 said:**
> Strangely this is one of the reasons that I don't like Mint.

Freedom of choice!  It's a beautiful thing.

---

### Post by V3u5nbRjDF on 2014-10-15
As for Factotum, I have a script that I have worked on that basically does most of my setup that I need for Ubuntu 14.04.  I'll likely sneak a bit from your script and will be adding my script work into git soon enough.  If you're interested, it's here and it does quite  a bit of the legwork for my ruby setup.

[https://gist.github.com/trivialpackets/e11aa5356cf4921549a7](https://gist.github.com/trivialpackets/e11aa5356cf4921549a7)

---


---
title: "how can i install gdm in ubuntu 10.04"
date: 2012-09-19
forum: Server Platforms
---

### Post by sububtu on 2012-09-19
hi all...
I ve installed ubuntu 10.04 recently.
i was unable to install gdm.

i had read in some page tha i need to install Universe and multiverse repositories in /etc/apt/sources.list

But dont know how to enable Universe and multiverse repositories in /etc/apt/sources.list ;(

What i had done  was removed # fom some lines.

but when i tried to install gdm bu command sudo apt-get update , What i can see is huge error list   Like :-

"Some index files failed to download, they have been ignored, or old ones used instead"

plshelp me...

---

### Post by jerrrys on 2012-09-19
GDM is installed by default in 10.04.

How bout posting your software.list and let us see what you done.

gedit /etc/apt/sources.list

---

### Post by sububtu on 2012-09-20
There is no gedit !!!
What i can see is the ubuntu terminal (after booting)

the software source list content is :

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid main restricted**
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)  ** lucid main restricted**

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid updates restricted**  
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid updates restricted** 

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid universe **
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid universe**
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   l**ucid-updates universe**
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates universe**

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid multiverse **
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid multiverse**
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates multiverse**
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates multiverse**


deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-backports main restricted universe **
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   [B]llucid-backports main restricted universe
[/B]
deb [http://archive.canonical.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid partner**
deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[archive.canonical]("http://in.archive.ubuntu.com/ubuntu/")[.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** llucid partner**

deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security main restricted**
deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security main restricted**
deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security inverse**
deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** lucid security inverse**
deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security.]("http://in.archive.ubuntu.com/ubuntu/")[ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** lucid security multiverse**
deb-src [http://security.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   [B]lucid security multiverse


[/B]What i need is a gui[B]

:guitar:
[/B]

---

### Post by cariboo on 2012-09-20
If you installed one of the *-desktop meta packages eg: ubuntu-desktop, kubuntu-desktop, etc. You should be able to start the desktop by logging in as a normal user, and typing:

```
startx
```

at the prompt. Once you are done, just log out, and you are back at the prompt, that way you have the best of both worlds.

---

### Post by sububtu on 2012-09-20
Ok.
But i think i have not installed any of these Desktop interfaces !!!
When i entered startx i got an error:-
The program 'startx' is currently not installed. You can install it by typing sudo apt-get install xinit

then i tried apt-get install xinit
Finally :-
E: Couldn't find package xinit !!!!

---

### Post by jerrrys on 2012-09-20
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid main restricted**
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)  ** lucid main restricted**

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid updates restricted**  
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid updates restricted** 

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid universe **
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid universe**
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   l**ucid-updates universe**
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates universe**

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid multiverse **
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid multiverse**
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates multiverse**
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-updates multiverse**


[COLOR=Red]#[/COLOR]deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   **lucid-backports main restricted universe **
[COLOR=Red]#[/COLOR]deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/)   [B]llucid-backports main restricted universe
[/B]
deb [http://archive.canonical.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid partner**
[COLOR=Red]#[/COLOR]deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[archive.canonical]("http://in.archive.ubuntu.com/ubuntu/")[.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** llucid partner**

deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security main restricted**
[COLOR=Red]#[/COLOR]deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security main restricted**
deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   **lucid security inverse**
[COLOR=Red]#[/COLOR]deb-src [http://]("http://in.archive.ubuntu.com/ubuntu/")[security]("http://in.archive.ubuntu.com/ubuntu/")[.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** lucid security inverse**
deb [http://]("http://in.archive.ubuntu.com/ubuntu/")[security.]("http://in.archive.ubuntu.com/ubuntu/")[ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")  ** lucid security multiverse**
[COLOR=Red]#[/COLOR]deb-src [http://security.ubuntu.com/ubuntu/]("http://in.archive.ubuntu.com/ubuntu/")   [B]lucid security multiverse

[/B]Comment those out and do an update please

---

### Post by matt_symes on 2012-09-20
Hi

Just to make sure that something is not going bang, can you post the output of

```
dpkg -l | grep -E "xorg|gdm"
```That is a small L after dpkg and a big E. That way, we can see exactly what is installed  on your system.

Also, please post the output of

```
uname -a
``````
cat /etc/lsb-release
```

Did you install the server edition ?

Kind regards

---


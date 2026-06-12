---
title: "Can't install ubuntu-moblin-remix"
date: 2010-02-01
forum: Ubuntu Moblin Remix
---

### Post by damaxxed on 2010-02-01
The Ubuntu Moblin Remix-ISO doesn't work for me - there are bugs with my graphics card (ATI Mobility Radeon HD 4330, FGLRX) that make the screen flicker whenever I switch to another window.

Because of this I tried to install the Moblin Remix to a clean, working Ubuntu installation, like the [German Ubuntu Wiki proposes](http://wiki.ubuntuusers.de/Baustelle/Ubuntu-Moblin-Remix):

```
sudo add-apt-repository ppa:moblin/ppa
sudo apt-get install ubuntu-moblin-remix ubuntu-moblin-ppa-keyring
```

Adding the repository works, but installing "ubuntu-moblin-remix" fails, because of its dependencies.
```
Die folgenden Pakete haben nicht erfüllte Abhängigkeiten:
  ubuntu-moblin-remix: Hängt ab: empathy soll aber nicht installiert werden
                       Hängt ab: gnome-control-center soll aber nicht installiert werden
                       Hängt ab: moblin-session soll aber nicht installiert werden
                       Hängt ab: moblin-ux-settings soll aber nicht installiert werden

```
 I can't explain it precisely, but apt-get reports that the dependencies can't be installed. After adding the dependencies of the dependencies of the dependencies to the apt-get install command, it reports that some dependencies collide. (libebook1.2-9, libedataserverdbus1.2-11, .....)

---

### Post by edodefili on 2010-03-07
You have to add an

sudo apt-get update

After your add-apt-repository.

Bye

---

### Post by damaxxed on 2010-03-18
I ran "apt-get update" of course ;)

Any ideas?

---

### Post by johny_ on 2010-04-22
Got the same problem as you damaxxed

---

### Post by MaX on 2010-04-30
> **johny_ said:**
> Got the same problem as you damaxxed


Are you running the x86_64 version of ubuntu?

run
```
uname -m
``` in a terminal and see the output.

I guess there is no 64-bit version built of ubuntu-moblin-remix... to bad.

---

### Post by damaxxed on 2010-05-07
> **MaX said:**
> Are you running the x86_64 version of ubuntu?

run
```
uname -m
``` in a terminal and see the output.

I guess there is no 64-bit version built of ubuntu-moblin-remix... to bad.

Now i use the 32-bit version of Ubuntu 10.04 LTS:

```
max@max-desktop:~$ uname -m
i686
```But now I fail even earlier! Seems like the "ppa:moblin/ppa" repository has no packages for lucid. Any ideas?

---

### Post by cariboo on 2010-05-09
Ubuntu has dropped support for the Moblin remix, seeing as the project has now been taken over by the Linux Foundation and merged with Maemo. Have a look [here]("http://www.mobilecrunch.com/2010/02/15/moblin-maemo-linux-foundation-meego/") for more info.

If you want to use the Moblin remix, you can try using the Karmic ppa, there won't be one for Lucid.

---


---
title: "upgrade from 10.04 to 12.04 failed"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jagr2808 on 2012-04-15
Hi,  I'm an ubuntu 10.04 Desktop-user and is trying to upgrade to 12.04  Beta. I tried to upgrade it through update-manager, but during the  installation my computer accidently got turned of. When I started it  again, it said that I had to do a partly installation, but when I tried  that it said that I had four damaged packages that I needed to fix using  synaptic or apt-get. I tried with both, but it said that the packages  couldn't be fixed because of an "unredeemed dependence".
 
 Can anyone help me fix this, please.
 
 PS: When I starte the upgrade I only had 3GB of space, but since it  said it only needed 2GB I proceeded, and now I only have 1GB. I don't  think it has anything to do with the problem, just thought I would let  you know.

---

### Post by MG&amp;TL on 2012-04-15
10.04 to 12.04 is going to be quite a tumultuous experience...why not backup and use an install disc instead?

Anyway, your problem:

Have you tried:

```
sudo dpkg --configure -a
```

and

```
sudo apt-get install -f
```

?

---

### Post by philinux on 2012-04-15
Moved to precise testing.

---

### Post by kansasnoob on 2012-04-15
Since disc space may be an issue I'd start with:

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get autoremove
```

```
sudo apt-get update
```

```
sudo dpkg --configure -a
```

```
sudo apt-get dist-upgrade
```

Of course post any errors encountered here, but working on a dev release with such limited disc space is not a good idea :(

---

### Post by MG&amp;TL on 2012-04-15
Fix your packages before attempting to save space with the various cleaning commands. Otherwise you will get errors. 

(Just a note, no disrespect kansanoob)

---

### Post by jagr2808 on 2012-04-15
> **kansasnoob said:**
> Since disc space may be an issue I'd start with:

```
sudo apt-get clean
``````
sudo apt-get autoclean
``````
sudo apt-get autoremove
``````
sudo apt-get update
``````
sudo dpkg --configure -a
``````
sudo apt-get dist-upgrade
```Of course post any errors encountered here, but working on a dev release with such limited disc space is not a good idea :(

I still get the same error:
root@hjemmepc:~# sudo apt-get dist-upgrade
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
Du vil kanskje kjøre «apt-get -f install» for å rette på dette.
Følgende pakker har uinnfridde avhengighetsforhold:
  libc-dev-bin: Avhenger av: libc6 (< 2.12) men 2.15-0ubuntu7 er installert
  libc6-dev: Avhenger av: libc6 (= 2.11.1-0ubuntu7.10) men 2.15-0ubuntu7 er installert
  libnih1: Avhenger av: libc6 (< 2.12) men 2.15-0ubuntu7 er installert
  python-louis: Avhenger av: liblouis0 (>= 1.7.0-2) men lar seg ikke installere
E: Uinnfridde avhengighetsforhold - Prøv «-f».

I run ubuntu in norwegian, but here it is translated witk google translate

root @ home computer: ~ # sudo apt-get dist-upgrade
 Reading package lists ... Done
 Building dependency ratio
 Reading state information ... Done
 You might want to run "apt-get-f install 'to correct this.
 The following packages have unredeemed dependency:
   libc-dev-bin: Depends: libc6 (<2.12) but 2.15-0ubuntu7 is installed
   libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu7 is installed
   libnih1: Depends: libc6 (<2.12) but 2.15-0ubuntu7 is installed
   python-louis: Depends: liblouis0 (> = 1.7.0-2) but will not install
 E: unredeemed dependency - Try "-f".

apt-get-f install does not work either

---

### Post by jagr2808 on 2012-04-15
I'm trying to fix the packages. That's the problem. I can't.

---

### Post by MG&amp;TL on 2012-04-15
Output of:

```
dpkg --configure -a
```

please.

---


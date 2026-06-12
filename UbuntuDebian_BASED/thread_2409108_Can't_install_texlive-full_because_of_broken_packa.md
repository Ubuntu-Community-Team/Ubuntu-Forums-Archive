---
title: "Can't install texlive-full because of broken packages"
date: 2018-12-27
forum: Ubuntu/Debian BASED
---

### Post by cartman-10189 on 2018-12-27
Hi everyone, I'm trying to install texlive-full in Elementary OS Juno. When I launch the command 

```
sudo apt-get install texlive-full
```

an error message appears me tellling me that it's impossible to install asymptote package because of blocked broken packages. Any idea?
Maybe I have some problems with repositories: in fact some updates appear in Elementary OS software center, but I can't update them.

In the following the original message error (in italian):
```

luca@dell-luca:~$ sudo apt-get install texlive-full
[sudo] password di luca:               
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:


I seguenti pacchetti hanno dipendenze non soddisfatte:
 texlive-full : Dipende: asymptote ma non sta per essere installato
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati.

```

---

### Post by jeremy31 on 2018-12-27
Moved to Ubuntu based

---

### Post by cartman-10189 on 2018-12-27
Ok sorry if I posted in the wrong section

---

### Post by QIII on 2018-12-27
No apologies necessary.  You just owe jeremy31 a dozen virtual doughnuts.

:)

---

### Post by cartman-10189 on 2018-12-28
Haha OK. I re-post the bash in english:


```
luca@dell-luca:~$ sudo apt-get install texlive-full
[sudo] password for luca:               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 texlive-full : Depends: asymptote but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by #&amp;thj^% on 2018-12-28
See if this helps: [https://www.tug.org/texlive/acquire-netinstall.html](https://www.tug.org/texlive/acquire-netinstall.html)
Due to older versions in the repos>> I always just install the vanilla textlive, very easy instructions found here: [https://tex.stackexchange.com/questions/1092/how-to-install-vanilla-texlive-on-debian-or-ubuntu](https://tex.stackexchange.com/questions/1092/how-to-install-vanilla-texlive-on-debian-or-ubuntu)
The full installation is likely to take a long time, say between one and three hours (even on relatively fast connections).
```
tllocalmgr
Retrieving new TeXLive database from CTAN...
Initializing ...
Welcome to the TeXLive Local Manager shell. Type 'help' for assistance.
tllocalmgr> 

```

---

### Post by cartman-10189 on 2018-12-28
Solved, it was the file sources.list corrupted. It was enough to bring it back to default. Thanks everyone and happy new year!

---


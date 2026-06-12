---
title: "systemC"
date: 2009-12-21
forum: Tunisia Team
---

### Post by nidhameddine on 2009-12-21
salut
je veux installer systemC sur linux Ubuntu 9.10- the Karmic Koala.
S'il vous plait y a t il un document, ou ça sera gentil de votre part de me donner les étapes nécessaires pour effectuer cette tache.
Merci pour votre aide

---

### Post by MaWaLe on 2009-12-22
Bonjour Nidhameddine
essayes avec ce lien : [http://svenand.blogdrive.com/archive/95.html]("http://svenand.blogdrive.com/archive/95.html")
il est en anglais mais assez clair :)

---

### Post by nidhameddine on 2009-12-25
salut
merci mawel pour votre aide mais j'ai pas compris la première et la cinquième étape
**************************************************************
 1. Change to the top level directory (systemc-2.2)

2. Create a temporary directory, e.g.,

> mkdir objdir

3. Change to the temporary directory, e.g.,

> cd objdir

4. Set the following environment variable(s):

> set CXX=g++

> export CXX

5. Configure the package for your system.

> ../configure

While the 'configure' script is running, which takes a few moments, it prints messages to inform you of the features it is checking. It also detects the platform.
**********************************************************************

s'il vous plait j'ai pas bien compris la prémière étape, et quel est la commande nécessaire pour la cinquième étape.
merci pour votre aide.

---

### Post by Nizarus on 2009-12-26
1- Changer votre répertoire de travail vers le répertoire systemc-2.2
...
5- La commande est ./configure

---

### Post by nidhameddine on 2009-12-26
salut, j'ai encore un problème en exécutant la commande "gmake" ou "gmake install" ou "gmake check" je trouve toujours un problème:
*************************************************************************
e()’:
../../../../src/sysc/utils/sc_utils_ids.cpp:110: error: ‘getenv’ is not a member of ‘std’
../../../../src/sysc/utils/sc_utils_ids.cpp:111: error: ‘strcmp’ was not declared in this scope
../../../../src/sysc/utils/sc_utils_ids.cpp: At global scope:
../../../../src/sysc/utils/sc_utils_ids.cpp:119: warning: ‘sc_core::forty_two’ defined but not used
gmake[3]: *** [sc_utils_ids.o] Erreur 1
gmake[3]: quittant le répertoire « /home/nidhameddine/systemc-2.2.0/objdir/src/sysc/utils »
gmake[2]: *** [all-recursive] Erreur 1
gmake[2]: quittant le répertoire « /home/nidhameddine/systemc-2.2.0/objdir/src/sysc »
gmake[1]: *** [all-recursive] Erreur 1
gmake[1]: quittant le répertoire « /home/nidhameddine/systemc-2.2.0/objdir/src »
gmake: *** [all-recursive] Erreur 1
***************************************************************************
comment je peux résoudre ce problème

---

### Post by alaya.zied on 2009-12-27
Vu que tu va installer à partir des sources, il te faut le compilateur.
Sous Ubuntu, il suffit d'installer le paquet build-essential et tu aura tout les outils nécessaires (y compris le compilateur gcc).

sudo apt-get build-essential

---

### Post by SalahTr on 2009-12-31
> **alaya.zied said:**
> sudo apt-get build-essential

il manque install
```
sudo apt-get install build-essential
```

nidhameddine ajoutes au fichier :
```
systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp
```
les lignes suivantes:
```
#include "string.h"
#include "cstdlib"
```

---

### Post by alaya.zied on 2010-01-04
Merci SalahTr pour la correction ^^'

---

### Post by SalahTr on 2010-01-04
de rien alaya.zied

---

### Post by sabrina86 on 2011-03-24
SVP je veux savoir commment installer SystemC sous Ubuntu 10.10
Merci d'avance :P

---


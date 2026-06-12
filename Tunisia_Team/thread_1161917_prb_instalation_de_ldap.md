---
title: "prb instalation de ldap"
date: 2009-05-17
forum: Tunisia Team
---

### Post by benakacha on 2009-05-17
root@S8203-P15:~# sudo apt-get install slapd ldap-utils db4.2-util
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets supplémentaires suivants seront installés*: 
  libdb4.2
Les NOUVEAUX paquets suivants seront installés*:
  db4.2-util ldap-utils libdb4.2 slapd
0 mis à jour, 4 nouvellement installés, 0 à enlever et 60 non mis à jour.
Il est nécessaire de prendre 2062ko dans les archives.
Après cette opération, 5337ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? o
ATTENTION*: les paquets suivants n'ont pas été authentifiés.
  libdb4.2 slapd db4.2-util ldap-utils
Faut-il installer ces paquets sans vérification (o/N)*? o
Err [http://172.16.0.10](http://172.16.0.10) hardy/main libdb4.2 4.2.52+dfsg-4
  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Err [http://172.16.0.10](http://172.16.0.10) hardy-updates/main slapd 2.4.9-0ubuntu0.8.04.2
  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Err [http://172.16.0.10](http://172.16.0.10) hardy/universe db4.2-util 4.2.52+dfsg-4
  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Err [http://172.16.0.10](http://172.16.0.10) hardy-updates/main ldap-utils 2.4.9-0ubuntu0.8.04.2
  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Impossible de récupérer [http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/d/db4.2/libdb4.2_4.2.52+dfsg-4_i386.deb](http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/d/db4.2/libdb4.2_4.2.52+dfsg-4_i386.deb)  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Impossible de récupérer [http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/slapd_2.4.9-0ubuntu0.8.04.2_i386.deb](http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/slapd_2.4.9-0ubuntu0.8.04.2_i386.deb)  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Impossible de récupérer [http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/universe/d/db4.2/db4.2-util_4.2.52+dfsg-4_i386.deb](http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/universe/d/db4.2/db4.2-util_4.2.52+dfsg-4_i386.deb)  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
Impossible de récupérer [http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/ldap-utils_2.4.9-0ubuntu0.8.04.2_i386.deb](http://172.16.0.10:3142/fr.archive.ubuntu.com/ubuntu/pool/main/o/openldap2.3/ldap-utils_2.4.9-0ubuntu0.8.04.2_i386.deb)  Ne parvient pas à résoudre «*htiouech.imen@196.203.125.242.8080*»
E: Impossible de récupérer quelques archives, peut-être devrez-vous lancer apt-get update ou essayer avec --fix-missing*?

---

### Post by alaya.zied on 2009-05-18
Khalil, essaye d'allez sur le channel #ubuntu-tn sur freenode.
il y a rochdi qui s'y connait un peut mieux.
il faut être patient sur le channel (plusieur d'ntre nous travaille ...)
STP revient ici pour copier coller la solution.

---

### Post by MaWaLe on 2009-05-18
Khalil tu es en train d'utiliser un dépôt personnel d'une certaine imen htiouech pour récupérer des paquets qui ne sont pas aussi signés.

Envoi ici le contenu de ton fichier sources.list pour évrifier son intégrité (je pense que tu as ajouté des sources nonj signé qui sont en train de troubler tes téléchargemens).

---

### Post by dark of angel on 2009-05-18
[http://doc.ubuntu-fr.org/ldap_client#a_qui_cela_s_adresse](http://doc.ubuntu-fr.org/ldap_client#a_qui_cela_s_adresse)
ESPERANT QU ELLE T AIDE 
personnellement je ne sais pas

---


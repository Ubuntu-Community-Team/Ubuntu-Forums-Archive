---
title: "2 question SVP"
date: 2009-04-07
forum: Tunisia Team
---

### Post by 007up on 2009-04-07
salut tout le monde

j'ai 2 questions et j'espère que vous m'aidez

1- comment désactiver la synchronisation automatique de l'heur de l'été?
2- comment exécuté une commande Shell à l'arrêt de ubuntu ?

merci d'avance ):P

---

### Post by alaya.zied on 2009-04-08
pour la question 1: depuis le Mardi 31 Mars (un jours après le début de l'application de l'heure d'été dans quelque pays au monde) une mise à jours a été faite et qui annule l'heure d'été pour la Tunisie.
donc il suffit de faire une simple mise à jours pour ton système.

pour la question 2: je ne comprend pas ce que tu veux dire.

---

### Post by Nizarus on 2009-04-08
1- [http://nizaurs.blogspot.com/2009/03/annulation-de-lheure-dete-en-tunisie.html](http://nizaurs.blogspot.com/2009/03/annulation-de-lheure-dete-en-tunisie.html)
2 - [http://forum.ubuntu-fr.org/viewtopic.php?id=138384](http://forum.ubuntu-fr.org/viewtopic.php?id=138384)

---

### Post by RachedTN on 2009-04-09
@007up : moi aussi j'ai pas compris ta 2ème question !

---

### Post by 007up on 2009-04-09
saut 
merci Nizarus pour les réponces

et pour la 2eme question, le problème c'est que j'ai un programme qui génère une erreur si je ferme le system sans arrêter ce programme manuellement et je veux savoire s'il y a une méthode pour exécuté la commande d'arrêt de ce programme lors la fermeture du sytème automatiquement 

merci à tous

---

### Post by RachedTN on 2009-04-09
En fait chaque progarmme a un PID (c'est un numéro comme le CIN chez nous), donc normalement pour mettre fin à un programme ou un processus, on exécute cette commande : kill -15 PID  ou bien kill -9 PID
la première commande permet de terminer proprement le programme, tandis que la deuxième termine le programme "immediately"
Le problème c'est que le PID change chaque fois que ouvre ton PC, donc assoscier une tache automatique lors de la fermeture de PC sera un peu délicat : çàd il faudra faire un script d'automatisation => you have to do some programmation work :)

---

### Post by tarekdj on 2009-04-11
Pour ta 2eme question :
$ vi ~/.bach_logout
et tu y ajoute le script désiré.(ce fichier est un script utilisé lors de la déconnexion.) j'espere que sa va t'aider

---

### Post by aminesay on 2009-04-12
> **007up said:**
> 
 le problème c'est que j'ai un programme qui génère une erreur si je ferme le system sans arrêter ce programme manuellement 

quel est ce programme?

---


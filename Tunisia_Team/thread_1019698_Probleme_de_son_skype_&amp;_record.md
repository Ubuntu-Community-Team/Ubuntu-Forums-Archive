---
title: "Probleme de son skype &amp; record"
date: 2008-12-23
forum: Tunisia Team
---

### Post by dr_med_ra on 2008-12-23
salemo3aleykom

j'ai un probleme avec skype.Je ne peux pas l'utilisé.
je peux entendre mais personne ne m'entends.
Aussi l'enregistreur de son ne marche pas.
J'entends rien
Aidez moi s'il vous plait

---

### Post by dr_med_ra on 2008-12-24
pas de reponse:(

---

### Post by tarek.elleuch on 2008-12-27
tout d'abord, voulez vous précisez ta carte son, et si elle marche ou pas sur ton ordi, le type de l'ordi, la version de ubuntu qui tu utilise, les commandes uname -a et lspci peuvent aider.

à l'aveuglete, je vous demande de vérifier si ton micro marche et qu'il est bien brancher. si oui, alors tu doit augmenter le volume de micro dans alsa mixer et de choisir le bon péréohirique pour la capture dans le menu option de skype.
c'est deux lien peuvent vous être utile
[http://doc.ubuntu-fr.org/skype](http://doc.ubuntu-fr.org/skype)
[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

svp, si vous avez résolut le problème, poster ici comment vous avez fais

mes respects Mr

---

### Post by carthage on 2009-01-04
salem
download this version of skype  [http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)
open synaptic and search for alsa-oss
extract the skype oss, cd to the extracted file and type in a terminal
#padsp ./skype (without the #)
it worked for me(i've found this method in skype forums)
good luck

(PS:if u want skype to not be bound to the terminal session and to run on background type the following command on the terminal #nohup padsp ./skype&)

---

### Post by carthage on 2009-01-04
salem
visit this lilnk too 
[http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/](http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/)

it worked for me on ubuntu 8.04(hardy)

good luck

---

### Post by omrisaber on 2009-03-25
assalamu alaikom..

dr_med_ra doit répondre si c ok ou non !  (n'est ce pas?)
ok pour ton problème, si tu es encore entrain de suivre ce thread, dans les option de skype, pointe sur les options du "son" , et il te permettra de choisir ton interface sonore, tu dois généralement choisir à partir de la liste celle qui a le suffixe "hw" à la fin (hw ça veut dire hardware je crois) répète ceci avec les 3 interfaces d'entrée, de sortie et de la sonnerie, normalement tu aura ton skype fonctionnel inchallah..

---

### Post by MaWaLe on 2009-03-25
Je suppose que le problème est résolu depuis le temps vu que la question a été posée en décembre 2008.

Personnellement je pense que pour éviter ce genre de décalage temporelle il serait préférable que la personne qui pose la question marque son sujet (thread) [RESOLU] ou bien [SOLVED] une fois la solution appliquée et ce pour deux raisons :
1- Ne plus répondre à un thread caduque
2- Les gens ayant le même problème serait satisfait de trouver suite à une recherche le mot RESOLU ;)

Sinon : merci omrisaber pour l'effort

---


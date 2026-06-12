---
title: "éavoir un client et serveur sur lameme poste?"
date: 2009-11-13
forum: Tunisia Team
---

### Post by dark of angel on 2009-11-13
st atous
je veux savoir est ce qu'il ya une possibilité de tester un"ping" entre client et un serveur sous ubuntu en utilisant un virtual box (comment)sur le meme pc

et merci

---

### Post by Neo31 on 2009-11-13
tu peut clarifier ta question un peut? un peut de precision svp.
J'ai compri que tu veut faire un ping depuis une machine virtuelle vert ta machine hote, c ca?
dans ce cas assure toi que t'as bien configurer les parametres reseaux de ta machine virtuelle et que ta machine hote et ta machine virtuelle appartiennent au meme reseaux. Dans ce cas il sera biensure possible de faire le ping.
si ta machine hote est deja connecter a un routeur ou switcher... qui offre le service dhcp c'est facile, sinon a toi de configurer ton petit reseau entre la machine hote et virtuelle. je te conseil d'utiliser la configuration bridged network sur l'interface reseau de l'hote.
bonne chance.

---


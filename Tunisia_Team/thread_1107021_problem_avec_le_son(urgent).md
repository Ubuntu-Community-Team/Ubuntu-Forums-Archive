---
title: "problem avec le son(urgent)"
date: 2009-03-26
forum: Tunisia Team
---

### Post by dark of angel on 2009-03-26
j ai migrer ver ubuntu 8.10 a 100/100
maintenant après l installation je ne sais quoi faire  pas de son en plus je ne sais pas est ce que obligatoire d installer les driver ou non
carte mere 661FX-M:1.0
merci pour laide

---

### Post by alaya.zied on 2009-03-26
Bonjour dark of angel,
généralement Ubuntu vient avec les drivers nécessaires sauf s'il n'est pas open source. Dans ces cas on doit installé nous même le driver (juste on passe par Système -> administration -> hardware driver et choisir installé, Ubuntu va chercher le driver sur internet et l'installe)

Généralement on a ce genre de soucis avec quelques cartes graphiques et wifi.

Rare pour le son.

Ouvre une console et taper la commande: lspci 
ça va donner une liste dans laquelle tu trouvera l'identifiant exacte de ta carte son.

---

### Post by MaWaLe on 2009-03-27
Dark of angel
s'il te plait tu nous indique la marque de ton ordinateur, un laptop ou desktop, le résultat de la commande lspci que Zied t'a donné et ensuite on pourra aller de l'avant

Sinon la majortité des cas le problème du son est un simple paramétrage d'aLSA 

sinon est ce que tu as effectué ton installation en étant connecté à Internet ou en offline?
Est ce que tu as effectué lmes mises à jours suite à ton installation (qui doivent être de la taille de 150 à 240 Mo)?

---


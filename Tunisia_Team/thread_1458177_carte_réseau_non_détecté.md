---
title: "carte réseau non détecté"
date: 2010-04-19
forum: Tunisia Team
---

### Post by gardinia on 2010-04-19
[SIZE="5"]bonjour; 
j'ai installé Ubuntu 9.10 avec succès...le problème c'est que le système ne reconnait pas ma carte réseau eth 0= "aucune interface réseau n'a été détectée"  ...aidez moi s.v.p car je suis débutant ..  [/SIZE]

---

### Post by alaya.zied on 2010-04-20
est ce le message persiste même si tu met un câble réseau ?
vérifier aussi que le câble marche bien et qu'il est bien connecté.

---

### Post by Neo31 on 2010-04-20
Zied, ca me semble le cas dont on a parler au chat avec safoine et qu'on a parler sur la ML.
J'ai deja proposer une solution si c le cas de l'etudiante au polytech, mais pas encore de reponse.

---

### Post by Neo31 on 2010-04-22
> **gardinia]bonjour!!
je suis l'étudiante de polytec sousse..merci beaucoup pour votre aide..
le problème mnt c que je trouve une problème d'exécuter autorun.sh shell script .. pouvez vous m'aider ou au moins me guider un peu ..j'aimerai bien résoudre cette problème ..merci :) 

voici le code : 
meriem@meriem-laptop:~$ cd r8101-1.015.00
meriem@meriem-laptop:~/r8101-1.015.00$ ./autorun.sh
: command not found1:
: command not found5:
Check old driver and unload it.
./autorun.sh: line 32: syntax error near unexpected token `else'
'/autorun.sh: line 32: `else [ "$module" != "r8169" ] said:**
> salut,
si c le cas et ke mr safoine de polytech sousse a essayer de contacter ubuntu-tn, j'aimerai vous dire ke g deja essayer de l'aider sur le channel et g repondu a son message sur la ML d ke g eux un pe de temps, voila les 2 emails ke g repondu avec sur la ML, j'espere ke ca te sera utile.
tu pe verifier si tu a la mm carte realtek avec la commande :
lspci
ke tu pe taper dans le terminal.

voila l'email :
> [COLOR=Red]2eme e[/COLOR][COLOR=Red]mail[/COLOR]
[LEFT]cool, u r lucky, i got it ^^
[/LEFT]
 [COLOR=Navy][download the driver from here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E%2FRTL8101E%2FRTL8102E-GR%2FRTL8103E%20L%20%20br%3ERTL8102E%20L%20%2FRTL8101E%2FRTL8103T%20br%3ERTL8401%2FRTL8401P")[/COLOR] 
and follow the readme file inside the archive, it contains an autorun.sh shell script that you'll have to execute and it's supposed to compile the driver for you before it loads it :)
you'll need this driver in realtek page : LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64) version 1.015.00
we are here to explain any thing you didn't understand in the readme file :)
good luck ;)

[LEFT][COLOR=Red]1er email[/COLOR]
[/LEFT]
2010/4/19 Neo31 - Hide quoted text -

I encountered the same problem in ISIMahdia with a student that reported problems with the wifi driver, I remember it was exactly the same case, Toshiba Satellite. and since ISIMa passes through CCK proxies as almost all Tunisian universities he just couldn't do it there, but he didn't report anything later.
 well anyway, I did a little research and it seams **your NIC's driver (Network Interface Card) isn't included in Ubuntu by default so you'll have to download it and compile it.**
**you'll have to search for Realtek´s r8102 driver and download it :)**
Some asked for the driver from Toshiba support indicating their distribution and kernel version and they sent them the driver back, but I am not sure if it is available for all kernel versions.
Anyway the reason seam to be TOSHIBA, I had driver problems long time ago even with windows, they ship special drivers with their computers and not the standard drivers. Anyway, you'll have to compile it.
 don't worry abt it's license, I think it's GPL (free).
I'll see how i could help later on when i have more free time :)si ce n'ai pas le cas alors tu doit donner le resultat de la commande lspci sur le topic ke t'as creer et on verra apres si on aura besoin d'autres informations.
Neo31 ;)[/QUOTE]pour commencer, une petite correction a la derniere commande ifconfig eth0 up, t'as oublier sudo :p donc ca doit etre :
sudo ifconfig eth0 up
en tout cas ce n'est pas necessaire puiske eth0 est deja UP tu pe essayer de la mettre down avant de la remettre up, mais ici le probleme est dans le script.
a ce que je voit le fichier du script est deja executable. et on remarque qu'il n'as pas reussit a trouver 2 commandes, donc peu etre qu'il en manque qq depandances. il faut examiner le script pour identifier mieux le probleme.
sinon il est possible d'avoir un probleme de compatibilite avec le kernel.
je verrai le script des ke j'aurai u pe de temps, sinon y en a d'autres membres qui peuvent aider :)

---

### Post by Djamel MB on 2010-05-31
Je viens de joindre le forum, Vous avez l'air genti et pleins de bonne intention mais vous avez pas trop l'air de savoir ce que vous faites. Premiere question a poser c'est "la marque et le modele du laptop" en fonction du modele un propose la solutions.
Salam.

---

### Post by Neo31 on 2010-05-31
Djamel MB, our loco team discuss things on it's Mailing List too and this topic was started on the ML first where we asked that questions.

---


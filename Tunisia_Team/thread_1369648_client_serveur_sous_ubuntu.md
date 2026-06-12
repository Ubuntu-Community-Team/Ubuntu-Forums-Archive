---
title: "client serveur sous ubuntu"
date: 2010-01-01
forum: Tunisia Team
---

### Post by dark of angel on 2010-01-01
salut atous 
 et bonne année pour tous
 je veux programmer un petit programme de [tchat]entre en client et un serveur et pour cela je veus  de l'aide et est ce que il ya un exemple facile a comprendre 
 par exemple  le code  source qui gere cette manipulation  
 et merci pour tous

---

### Post by SalahTr on 2010-01-01
Salut dark of angel,

Bonne année à toi aussi, quel langage de programmation tu veux utiliser :?:

---

### Post by dark of angel on 2010-01-02
merci 
je préfère utiliser le Gambas le plus important que l'application tourne  et soit avec un code compréhensible

---

### Post by SalahTr on 2010-01-02
Client:
```
[COLOR="Blue"]STATIC[/COLOR] App [COLOR="Blue"]AS ClsMain[/COLOR]

[COLOR="#0000ff"]PUBLIC[/COLOR]  MySock [COLOR="#0000ff"]AS Socket[/COLOR]

[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsque la connexion est établit
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="Blue"]PUBLIC SUB [/COLOR]MySock_Ready()

  WRITE #MySock,[COLOR="DarkOrchid"]"Hello"[/COLOR],5  
[COLOR="SeaGreen"]'Envoyer au serveur (MySock) la chaine "Hello"  ayant la taille 5 [/COLOR]

[COLOR="Blue"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsque des données arrivent
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] MySock_Read()

  [COLOR="#0000ff"]DIM[/COLOR] chaine [COLOR="#0000ff"]AS String[/COLOR]
  READ #MySock,chaine,Lof(MySock) 
[COLOR="#SeaGreen"]' Lire les données à partir de serveur (MySock)
' Les données seront sauvegardés dans "chaine"
' Lof(MySock) retourne la taille des données à lire[/COLOR]
  PRINT chaine
[COLOR="#SeaGreen"]' Afficher la chaine lue[/COLOR]
  CLOSE #MySock
[COLOR="SeaGreen"]' Fermer la connexion, cela permet de libérer les ressources[/COLOR]
[COLOR="#0000ff"]

END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Constructeur 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]

[COLOR="#0000ff"]PUBLIC SUB[/COLOR] _New()

  MySock=[COLOR="#0000ff"]NEW[/COLOR] Socket [COLOR="#0000ff"]AS[/COLOR] "MySock"

  MySock.Connect([COLOR="DarkOrchid"]"name_of_host"[/COLOR],3450) 
[COLOR="#SeaGreen"]' Il faut remplacer name_of_host par le nom du poste serveur
' 3450 est à partir de quel le serveur reçoit les connexions[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsqu'il y a une erreur (le port n'est pas 
' ouvert , le réseau n'est pas accessible, le serveur refuse la connexion...)
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] MySock_Error()

   PRINT [COLOR="DarkOrchid"]"Connexion impossible "[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Point d'entrée du programme
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]STATIC PUBLIC SUB[/COLOR] Main()

  App=[COLOR="#0000ff"]NEW[/COLOR] ClsMain

[COLOR="#0000ff"]END[/COLOR]
```
Serveur:
```
[COLOR="#0000ff"]STATIC[/COLOR] Server [COLOR="#0000ff"]AS[/COLOR] ClsServer
[COLOR="#0000ff"]PUBLIC[/COLOR] Clients [COLOR="#0000ff"]AS [/COLOR]Object[]
[COLOR="#0000ff"]PUBLIC[/COLOR] Srv [COLOR="#0000ff"]AS ServerSocket[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque des données arrivent au serveur
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] Socket_Read()

  [COLOR="#0000ff"]DIM[/COLOR] chaine [COLOR="#0000ff"]AS String[/COLOR]
  READ #LAST,chaine,Lof(LAST)
[COLOR="SeaGreen"]' Lire les données envoyés par le client 
' LAST contient le nom du client
' Les données seront sauvegarder dans chaine
' Lof(LAST) retourne la taille des données[/COLOR]
  PRINT [COLOR="DarkOrchid"]"Les données reçues -->"[/COLOR] & chaine
[COLOR="SeaGreen"]' Afficher les données envoyés[/COLOR]
  WRITE #LAST,[COLOR="#9932cc"]"bye"[/COLOR],3
[COLOR="SeaGreen"]' Envoyé au client le message "bye"[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque un client ferme la connexion
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB [/COLOR]Socket_Closed()

  PRINT[COLOR="#9932cc"] "Connexion fermée"[/COLOR]
  Clients.Remove(Clients.Find([COLOR="#0000ff"]LAST[/COLOR]))
[COLOR="SeaGreen"]' Supprimer du tableau "Clients" le client
' qui a fermé la connexion 
[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque un client 
' veut établir une connexion avec le serveur
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] Srv_Connection(Host [COLOR="#0000ff"]AS String[/COLOR])

  [COLOR="#0000ff"]DIM[/COLOR] MySock [COLOR="#0000ff"]AS Socket[/COLOR]
  PRINT [COLOR="#9932cc"]" Acceptation de la connexion venant de --> "[/COLOR] & Host
[COLOR="#2e8b57"]' "Host" contient le nom du client qui veut établir la connexion[/COLOR]
  MySock=Srv.Accept()
[COLOR="#2e8b57"]' Srv.Accept() retourne Un socket permettant de communiquer avec "Host"[/COLOR]
  Clients.Add(MySock)

[COLOR="#0000ff"]END

PUBLIC SUB [/COLOR]_New()

  Clients =[COLOR="#0000ff"]NEW[/COLOR] Object[]
[COLOR="SeaGreen"]' Le tableau Clients contiendra la liste des clients[/COLOR]
  Srv=[COLOR="#0000ff"]NEW[/COLOR] ServerSocket [COLOR="#0000ff"]AS[/COLOR] "Srv"
  Srv.Port=3450
[COLOR="#2e8b57"]' 3450 le port à partir du quel le Serveur reçoit les connexion[/COLOR]
  Srv.Type=ServerSocket.Internet
[COLOR="#2e8b57"]' Srv.Type reçoit le type de connexions (le protocole utilisé) que le serveur peut accepter
' ServerSocket.Internet => Connexion TCP/IP[/COLOR]
  Srv.Listen()
[COLOR="#2e8b57"]' Lancement du serveur
' Le serveur attend des connexions[/COLOR]

[COLOR="#0000ff"]END

STATIC PUBLIC SUB[/COLOR] Main()

  Server=[COLOR="Blue"]NEW[/COLOR] ClsServer
[COLOR="#0000ff"]

END[/COLOR]
```

URL :
[http://gambasdoc.org/help... (code source & Explication) [Fr]]("http://gambasdoc.org/help/doc/network?fr#t10")
[Documentation de la classe Socket [Fr]]("http://gambasdoc.org/help/comp/gb.net/socket?fr")
[Documentation de la classe ServerSocket [En]]("http://gambasdoc.org/help/comp/gb.net/serversocket")

---

### Post by SalahTr on 2010-01-02
> **dark of angel said:**
>  
je préfère utiliser le Gambas le plus important que l'application tourne  et soit avec un code compréhensible
une application qui tourne et un code compréhensible dépend de l'habileté du programmeur et non du langage ;)

---

### Post by SalahTr on 2010-01-02
> **SalahTr said:**
> 
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Constructeur 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]

[COLOR="#0000ff"]PUBLIC SUB[/COLOR] _New()

  MySock=[COLOR="#0000ff"]NEW[/COLOR] Socket [COLOR="#0000ff"]AS[/COLOR] "MySock"

  MySock.Connect([COLOR="DarkOrchid"]"name_of_host"[/COLOR],3450) 
[COLOR="#SeaGreen"]' Il faut remplacer name_of_host par le nom du poste serveur
' 3450 est à partir de quel le serveur reçoit les connexions[/COLOR]

[COLOR="#0000ff"]END[/COLOR][/CODE]



Le constructeur sera appelé pour établir la connexion avec le serveur

---

### Post by dark of angel on 2010-01-07
> **SalahTr said:**
> Client:
```
[COLOR="Blue"]STATIC[/COLOR] App [COLOR="Blue"]AS ClsMain[/COLOR]

[COLOR="#0000ff"]PUBLIC[/COLOR]  MySock [COLOR="#0000ff"]AS Socket[/COLOR]

[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsque la connexion est établit
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="Blue"]PUBLIC SUB [/COLOR]MySock_Ready()

  WRITE #MySock,[COLOR="DarkOrchid"]"Hello"[/COLOR],5  
[COLOR="SeaGreen"]'Envoyer au serveur (MySock) la chaine "Hello"  ayant la taille 5 [/COLOR]

[COLOR="Blue"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsque des données arrivent
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] MySock_Read()

  [COLOR="#0000ff"]DIM[/COLOR] chaine [COLOR="#0000ff"]AS String[/COLOR]
  READ #MySock,chaine,Lof(MySock) 
[COLOR="#SeaGreen"]' Lire les données à partir de serveur (MySock)
' Les données seront sauvegardés dans "chaine"
' Lof(MySock) retourne la taille des données à lire[/COLOR]
  PRINT chaine
[COLOR="#SeaGreen"]' Afficher la chaine lue[/COLOR]
  CLOSE #MySock
[COLOR="SeaGreen"]' Fermer la connexion, cela permet de libérer les ressources[/COLOR]
[COLOR="#0000ff"]

END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Constructeur 
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]

[COLOR="#0000ff"]PUBLIC SUB[/COLOR] _New()

  MySock=[COLOR="#0000ff"]NEW[/COLOR] Socket [COLOR="#0000ff"]AS[/COLOR] "MySock"

  MySock.Connect([COLOR="DarkOrchid"]"name_of_host"[/COLOR],3450) 
[COLOR="#SeaGreen"]' Il faut remplacer name_of_host par le nom du poste serveur
' 3450 est à partir de quel le serveur reçoit les connexions[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera appelé lorsqu'il y a une erreur (le port n'est pas 
' ouvert , le réseau n'est pas accessible, le serveur refuse la connexion...)
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] MySock_Error()

   PRINT [COLOR="DarkOrchid"]"Connexion impossible "[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Point d'entrée du programme
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]STATIC PUBLIC SUB[/COLOR] Main()

  App=[COLOR="#0000ff"]NEW[/COLOR] ClsMain

[COLOR="#0000ff"]END[/COLOR]
```
Serveur:
```
[COLOR="#0000ff"]STATIC[/COLOR] Server [COLOR="#0000ff"]AS[/COLOR] ClsServer
[COLOR="#0000ff"]PUBLIC[/COLOR] Clients [COLOR="#0000ff"]AS [/COLOR]Object[]
[COLOR="#0000ff"]PUBLIC[/COLOR] Srv [COLOR="#0000ff"]AS ServerSocket[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque des données arrivent au serveur
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] Socket_Read()

  [COLOR="#0000ff"]DIM[/COLOR] chaine [COLOR="#0000ff"]AS String[/COLOR]
  READ #LAST,chaine,Lof(LAST)
[COLOR="SeaGreen"]' Lire les données envoyés par le client 
' LAST contient le nom du client
' Les données seront sauvegarder dans chaine
' Lof(LAST) retourne la taille des données[/COLOR]
  PRINT [COLOR="DarkOrchid"]"Les données reçues -->"[/COLOR] & chaine
[COLOR="SeaGreen"]' Afficher les données envoyés[/COLOR]
  WRITE #LAST,[COLOR="#9932cc"]"bye"[/COLOR],3
[COLOR="SeaGreen"]' Envoyé au client le message "bye"[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque un client ferme la connexion
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB [/COLOR]Socket_Closed()

  PRINT[COLOR="#9932cc"] "Connexion fermée"[/COLOR]
  Clients.Remove(Clients.Find([COLOR="#0000ff"]LAST[/COLOR]))
[COLOR="SeaGreen"]' Supprimer du tableau "Clients" le client
' qui a fermé la connexion 
[/COLOR]

[COLOR="#0000ff"]END[/COLOR]
[COLOR="SeaGreen"]''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
' Cette Méthode sera lorsque un client 
' veut établir une connexion avec le serveur
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''[/COLOR]
[COLOR="#0000ff"]PUBLIC SUB[/COLOR] Srv_Connection(Host [COLOR="#0000ff"]AS String[/COLOR])

  [COLOR="#0000ff"]DIM[/COLOR] MySock [COLOR="#0000ff"]AS Socket[/COLOR]
  PRINT [COLOR="#9932cc"]" Acceptation de la connexion venant de --> "[/COLOR] & Host
[COLOR="#2e8b57"]' "Host" contient le nom du client qui veut établir la connexion[/COLOR]
  MySock=Srv.Accept()
[COLOR="#2e8b57"]' Srv.Accept() retourne Un socket permettant de communiquer avec "Host"[/COLOR]
  Clients.Add(MySock)

[COLOR="#0000ff"]END

PUBLIC SUB [/COLOR]_New()

  Clients =[COLOR="#0000ff"]NEW[/COLOR] Object[]
[COLOR="SeaGreen"]' Le tableau Clients contiendra la liste des clients[/COLOR]
  Srv=[COLOR="#0000ff"]NEW[/COLOR] ServerSocket [COLOR="#0000ff"]AS[/COLOR] "Srv"
  Srv.Port=3450
[COLOR="#2e8b57"]' 3450 le port à partir du quel le Serveur reçoit les connexion[/COLOR]
  Srv.Type=ServerSocket.Internet
[COLOR="#2e8b57"]' Srv.Type reçoit le type de connexions (le protocole utilisé) que le serveur peut accepter
' ServerSocket.Internet => Connexion TCP/IP[/COLOR]
  Srv.Listen()
[COLOR="#2e8b57"]' Lancement du serveur
' Le serveur attend des connexions[/COLOR]

[COLOR="#0000ff"]END

STATIC PUBLIC SUB[/COLOR] Main()

  Server=[COLOR="Blue"]NEW[/COLOR] ClsServer
[COLOR="#0000ff"]

END[/COLOR]
```

URL :
[http://gambasdoc.org/help... (code source & Explication) [Fr]]("http://gambasdoc.org/help/doc/network?fr#t10")
[Documentation de la classe Socket [Fr]]("http://gambasdoc.org/help/comp/gb.net/socket?fr")
[Documentation de la classe ServerSocket [En]]("http://gambasdoc.org/help/comp/gb.net/serversocket")
MERCI C VREMANT   c tres gentil de ta part de faire cet effort  
et je te felicite pour e boulot

---

### Post by SalahTr on 2010-01-07
je t'en prie

---


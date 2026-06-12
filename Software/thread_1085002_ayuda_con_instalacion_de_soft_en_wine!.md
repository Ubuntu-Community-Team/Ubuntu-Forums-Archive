---
title: "ayuda con instalacion de soft en wine!"
date: 2009-03-02
forum: Software
---

### Post by emilianx on 2009-03-02
que tal comunidad soy nuevo por aca, en fin les cuento que adquiri hace unos dias la licencia de un soft, pero cuando quiero instalarlo me salta un error evidentemente me falta un archivo, el tema es que lo descargue y lo puse en system 32 pero no pasa nada, alguien podria ayudar? desde ya muchas gracias!

---

### Post by luks911 on 2009-03-02
Bienvenido. 
No tengo la menor idea de cuál sea el problema, pero va a ser más fácil que alguien pueda ayudarte sabiendo qué verisón de Ubuntu y de Wine usás, y cuál es el soft que querés instalar.

Saludos

---

### Post by emilianx on 2009-03-02
> **luks911 said:**
> Bienvenido. 
No tengo la menor idea de cuál sea el problema, pero va a ser más fácil que alguien pueda ayudarte sabiendo qué verisón de Ubuntu y de Wine usás, y cuál es el soft que querés instalar.

Saludos

si jeje tenes razon, disculpen el programa se llama website x5 evolution, la version de wine y ubuntu son las ultimas, saludos

---

### Post by luks911 on 2009-03-02
Ok, viendo la base de datos de aplicaciones de Wine[0], advierten que antes de instalarlo, en una terminal tenés que ejecutar
```
wget http://kegel.com/wine/winetricks && sh winetricks mfc40 mfc42
```
Eso descarga y ejecuta un script. De todos modos, vas a tener mensajes de error en la instalación y por las calificaciones que le dieron las perspectivas no son alentadoras. Probalo, capaz que en las últimas actualizaciones de wine hubo alguna mejora.
Otras posibilidades: correrlo en una máquina virtual con VirtualBox y XP, o buscar una alternativa para Linux (no te recomiendo ninguna porque no tengo mucha idea).

[0] [http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=12168](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=12168)

---


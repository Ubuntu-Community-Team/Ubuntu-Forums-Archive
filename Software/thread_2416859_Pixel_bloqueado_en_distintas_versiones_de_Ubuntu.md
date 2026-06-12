---
title: "Pixel bloqueado en distintas versiones de Ubuntu"
date: 2019-04-16
forum: Software
---

### Post by frocca17 on 2019-04-16
Gente, muy buenas!
Espero que anden muy bien (dudo que no, se viene el finde largo!)

Aclaro que catalogé el post como software porque aparentemente se trata de eso.
Primero un poco de entorno.
PC Corporativa, en la cual tengo tres particiones, un Windows 7, un Kubuntu (Completamente personalizado por mi empresa) y un Ubuntu (Instalado por mi, versión 18.04.2 LTS).

En ambos ubuntus utilizo KDE Plasma y tengo el mismo problema (a esta altura lo estoy asociando a KDE). En el centro de la pantalla un pixel "muerto", mas que muerto, bloqueado generalmente en blanco u otro tono similar.

En el windows no me pasa, no tengo problemas, incluso cambié el monitor y el problema persiste.
Si hasta acá te parece raro, te puedo decir algo aún mas raro, si tomo una captura de la pantalla, por ejemplo con Spectacle el pixel aparece en la captura (adjunto la captura).

Realmente estoy atascado con esto y no se como encararlo. En principio, KDE Plasma no lo puedo tocar demasiado, tengo que mantenerlo.

No se si se les ocurre algo (la secuencia apt-get update y apt-get upgrade la hice ya bastantes veces y no trajo mejoras).

---

### Post by frocca17 on 2019-05-14
Para la futura gente que venga a buscar sabiduría por aca les comento.
Ese pixel "muerto" en principio detecté que era "aleatorio".
Haciendo algúnas pruebas detecté que ese pixel era de un aplicativo, es decir, ese punto en particular quedaba tomado por la ventana de un aplicativo que, aún minimizado, seguía apareciendo. El aplicativo es un aplicativo Windows y ejecutado mediante citrix.
No encontré un "fix", pero al menos conozco la causa.

Gracias a todos por la ayuda.

---


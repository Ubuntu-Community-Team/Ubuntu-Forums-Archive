---
title: "Inconvenientes con servicios al inicio"
date: 2012-04-12
forum: Software
---

### Post by Sleipnirnkn on 2012-04-12
Hola gente,

Les comento mi situacion. Hace algunos dias (de obsesivo nomas) veo algunos servicios / demonios corriendo que ya no uso actualmente.
Ellos son: tor, polipo, ssh, smbd y nmbd
ejecuté la utilidad sysv-rc-conf desde la consola (y con privilegios de root) y saqué todos estos servicios de todos los runlevels.

Tambien, al ver que al reiniciar seguian ejecutandose, probé con:

'sudo update-rc.d -f ssh remove' 

con cada uno de los servicios. Si bien la respuesta fue positiva, siguen ejecutandose al reiniciar el sistema.

Pasé algo por alto o no estoy haciendo lo correcto. Alguien podria decirme como evitar que se ejecuten sin tener que desinstalar ?

Gracias de antemano.

---


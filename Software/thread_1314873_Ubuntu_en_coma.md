---
title: "Ubuntu en coma"
date: 2009-11-04
forum: Software
---

### Post by Nikolopulus on 2009-11-04
Buenas, antes que nada les agradezco por la ayuda. Les paso a contar el problema: empezó cuando abrí openoffice y me tiró un mensaje de error que decía:

"Openoffice could not save important internal information due to insufficient free disk space at the following location:
/home/nikolopulus/.openoffice.org2/user/backup"

Me pedía que libere espacio y tirara Retry. Claramente, no se comoh hacerlo. Después de esto me di cuenta que tampoco podía guardar los archivos nuevos que creaba (era ovbio)pero todo el resto funcionaba bien.
La vez siguiente que inicio encuentro que la mayoría de las cosas relativas a internet estaban desconfigurdas, se habían borrado todas las contraseñas del mozilla, los favoritos, pero no el historial, y no me deja acceder a ninguna pagina que pida usuario (foro, mail, etc). Tampoco anda el emesene, también perdió todas las configuraciones que le había puesto y cuando quiero iniciar sesión se cuelga, después de unos cuantos intentos me tira:

"Traceback (most recently call last)
File "usr/share/emesene/emesenelib/core.py", line 419, in do_login_succesful self.getMembershipListSync ()

File "usr/sare/emesene/emesenelib/ProfileManager.py", line 112, on GetMembershipList self.newCacheFile (.usr + '_ml.xml', response.body)

File "usr/share/emesene/emesenelib/core.py". line 905, in newCacheFile f.write (data)

IOError: [Errno 28] No hay espacio libre en el dispositivo

Por lo que pude probar, el resto de las cosas andan bien, en los dos usuarios que tengo, hasta descarque un juego del synaptic para probar ¿alguien tiene alguna idea de que pasa o que tengo que hacer?
Traté de ser lo más claro y corto posible. Gracias otra vez.
Ah, tengo ubuntu 8.10

---

### Post by josecuervo86 on 2009-11-04
Por los dos errores que te tira, lo primero que se me ocurre es que no tenes mas espacio en disco. Puede ser?

---

### Post by guillermolisi on 2009-11-05
Danos mas detalle sobre tamaño de las particiones y espacio libre que tenes en cada una, por favor.

---

### Post by Nikolopulus on 2009-11-05
Jaja, me siento un tonto, era tan simple. No tenía espacio libre, me olvidé que la partición más grande es la de Windows.
Gracias che

---


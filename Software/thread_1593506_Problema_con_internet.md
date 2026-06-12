---
title: "Problema con internet"
date: 2010-10-11
forum: Software
---

### Post by franco91 on 2010-10-11
Hola, llevo más o menos un año usando Ubuntu y desde que cambie de la versión 9.1 a la 10.04 que tengo problemas con internet, solo al hacer algunas cosas, como por ejemplo, usar un programa de mensajería instantánea, entrar a facebook, incluso crearme la cuenta en este foro. Con respecto a lo de la mensajería instantanea al intentar iniciar cesión con msn me tira este error:

> 
franco@franco-Satellite-L305:~$ emesene
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
If you are reading this, you may want to enable debug
It's the first option in the advanced page in preferences
Thread-1 start
Traceback (most recent call last):
  File "/usr/share/emesene/emesenelib/core.py", line 322, in _loginInputHandler
    retval = self._loginProcess(socket)
  File "/usr/share/emesene/emesenelib/core.py", line 393, in _loginProcess
    self.passportid = self.passportAuth(hash)
  File "/usr/share/emesene/emesenelib/core.py", line 591, in passportAuth
    str(e)
AuthError: Authentication error: "Can't connect to HTTPS server: [Errno 104] Conexi\xc3\xb3n reiniciada por el par"

E buscado por todas partes si alguien a tenido el mismo problema por favor dígame como lo soluciono, de ante mano gracias (:

---

### Post by Carlos C on 2010-10-17
Movido al subforo "Software". Por favor lee:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Respecto a tu problema, creo que debemos separar el problema que tienes con algunos sitios de tu problema con emesene. Prefiero que emesene lo veamos en un thread aparte. En caso de dudas, por favor lee:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Recuerda siempre dar todos los datos necesarios para comprender tu problema y tu situación. Dices que tienes dificultades con algunos sitios, pero no explicas exactamente en qué consisten esas dificultades, por lo que no es posible saber si el mismo problema afecta a cada sitio o si en cada uno tienes uno distinto. Además, ignoramos qué tipo de conexión a internet utilizas, lo que también es importante en estos casos.

Apuntando a la dificultad que tienes al entrar a algunos sitios, porque imagino que ese es el problema, ¿verdad? Creo que puedes tener dificultades con el dns que estás utilizando. Intenta cambiar de dns por una alternativa como OpenDns o los dns de google. Si no sabes como hacerlo te podemos ayudar. Lo importante es que sepas que puedes realizar el cambio tanto en el router que utilizas (en caso de que efectivamente uses uno) como en el equipo en el que tienes instalado Ubuntu.

Saludos.

---

### Post by waltercool on 2010-10-17
Por casualidad utilizas una "ñ" o acentos en tu clave de msn? Se me ocurre que puede ir por ahí...

Leí en un post que quizas puede ser porque es muy larga y recomendaron cambiar la clave y listo

---

### Post by moreback on 2010-10-17
Nop, por el mensaje de error parece estar relacionado con un problema de conexión. Pero si no nos dice qué tipo de conexión tiene, no lo podemos ayudar mucho.

---

### Post by waltercool on 2010-10-17
Es que vi un problema similar en el foro de Arch creo, y lo arreglaron cambiando la clave, lo que puse fueron suposiciones despues de que lo arregló.

---


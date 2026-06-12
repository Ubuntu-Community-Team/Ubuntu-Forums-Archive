---
title: "Pasar de ext3 a ext4 sin formatear"
date: 2009-10-17
forum: Software
---

### Post by sitiomatic on 2009-10-17
Hola, como todos, estoy ansioso esperando la final de 9.10 para actualizar.
El tema es que hoy encontre una pagina donde explican como pasar de ext3 a ext4 sin formatear y leyendo todas las bondades que cuentan de ext4 me tienta hacerlo.
Ya se que siempre hay riesgo al tocar particiones pero queria preguntar si alguien lo ha hecho y cual fue su experiencia.

---

### Post by sartrejp on 2009-10-17
Se puede hacer, no trae complicaciones, los cambios son para los nuevos datos, los demás quedan sin cambios.
Cabe aclarar que si estaba en ext3 y ahora tiene ext4 cambiaste el formato, es decir se formateó, lo que no se hace es borrar todo (el disco o la partición).

---

### Post by guidito73 on 2009-10-17
Yo me parece que corto por lo sano y hago backup y mando todo desde 0. Tengo cierta sensación de que quedaría mejor el sistema.

---

### Post by josecuervo86 on 2009-10-17
> **guidito73 said:**
> Yo me parece que corto por lo sano y hago backup y mando todo desde 0. Tengo cierta sensación de que quedaría mejor el sistema.

Y si, la verdad es que parece bastante chancho. Igual hacer back/up e instalar de 0 con Karmic tiene un +10 de movida! :P

---

### Post by guillermolisi on 2009-10-17
Cuando me decidi a cambiar ext3 por ext4 instale desde cero luego de venir actualizando desde la 7.04. Aproveche y reacomode particiones. 
Aclaro que el backup ya lo tenia porque hago todos los santos dias uno incremental y una vez por semana uno completo, todo con Bacula.

---

### Post by sitiomatic on 2009-10-17
Cuando decis backup, te referis a tus datos o tambien configuraciones de programas?
Yo laburo en internet asi que con mis datos no tengo problema, estan en la nube (para regocijo de stallman :) )
Lo que me rompe es volver a instalar/configurar las cosas que tengo andando en 9.04 por ej programas en wine, xp en virtualbox, hasta los addons de firefox es un plomazo volver a instalar. Imagino que esas cosas hay que volver a instalarlas no?

---

### Post by guillermolisi on 2009-10-17
> **sitiomatic said:**
> Cuando decis backup, te referis a tus datos o tambien configuraciones de programas?
Yo laburo en internet asi que con mis datos no tengo problema, estan en la nube (para regocijo de stallman :) )
Lo que me rompe es volver a instalar/configurar las cosas que tengo andando en 9.04 por ej programas en wine, xp en virtualbox, hasta los addons de firefox es un plomazo volver a instalar. Imagino que esas cosas hay que volver a instalarlas no?
Fundamentalmente todo lo que esta en /home/<my_user>/ con mas /etc porque en este ultimo hay muchos archivos que configuran programas que uso, entre ellos Samba, NFS, etc. Vuelvo a instalar los paquetes que necesite, de paso depuro ya que los que instale para probar y no uso mas los descarto, y copio los que necesito para que cada programa quede configurado tal como estaba antes (entre lo que esta en /etc y en /home/<my_user>)

---


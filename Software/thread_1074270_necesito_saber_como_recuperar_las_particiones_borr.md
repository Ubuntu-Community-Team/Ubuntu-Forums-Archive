---
title: "necesito saber como recuperar las particiones borradas"
date: 2009-02-19
forum: Software
---

### Post by aleittte on 2009-02-19
hola como va soy de nuevo yo! comento esta vez que ma mande una grande y tratando de redimensionar la particion swap con el gparted borre todas las particiones...... la cosa es la siguiente: estuve buscando por todos lados info de como recuperar las particiones perdidas y el resultado es que tengo 3 live cds de ubuntu, pd algo y otro mas que no se como utilizar...
lo que mas me interesa es si alguien tiene el manual de usuario del testdisk que no lo encuentro por ningun lado....y si no , si alguien hizo la misma macana que yo y lo soluciono me puede ayudar ????? hace una semana que estoy viviendo de live cd en live cd y no se que hacer........
espero que el titulo entre en los canones del foro y no me manden para otro lado, que este es un problema mayor!
por favor!!
y gracias!!!
saludos

---

### Post by kornykyano on 2009-02-19
bueno, yo no soy un experto pero si desde el LiveCD no los ves...es porque la has borrado de verdad...ha empezar desde cero :(

Saludos

---

### Post by aleittte on 2009-02-19
a ver si me explico bien :
al iniciar me tira error 22 ya que con el gparted no llegue a borrar todos los datos pero si la nominacion de la particion entonces no la reconoce, pero al correr el testdisk me dice que estan alli pero no se açcomo funciona el programa para recuperar las particiones....
o sea no las borre completamente

---

### Post by guillermolisi on 2009-02-20
> **aleittte said:**
> a ver si me explico bien :
al iniciar me tira error 22 ya que con el gparted no llegue a borrar todos los datos pero si la nominacion de la particion entonces no la reconoce, pero al correr el testdisk me dice que estan alli pero no se açcomo funciona el programa para recuperar las particiones....
o sea no las borre completamente
Si realmente las particiones no fueron borradas y solo les cambiaste el nombre (que no tengan nombre es un caso particualr de haberselo cambiado), cuando volves a ejecutar gparted o fdisk, como te muestra las particiones de ese disco ?

Si no tenes operativa la maquina, inicia con un LiveCD y abris una consola para correr fdisk o parted. El disco en custion no tiene que estar montado, asi que no deberias tener mayores problemas para ver la tabla de particiones y segun sea lo que te muestre posiblemente con solo volver a ponerles el nombre correcto logras dejar todo funcionalmente bien.

---


---
title: "Problemas con dosemu"
date: 2010-03-02
forum: Software
---

### Post by filoquin on 2010-03-02
Estoy trabajando con un programa bastante viejo que corre bajo dos. Estoy usando dosemu para emularlo. este programa usa una versión vieja de isis (base de datos). Todo funciona a la perfección si llamo a dosemu desde la consola.

Pero cuando llamo al programa desde un .sh o un lanzador del escritorio hay un comportamiento errático.

Cuando el programa en cuestión (isis) bloquea un archivo temporal para escribir en el cambia sus permisos a 644 y cambia el grupo al que pertenece del grupo común que uso para accederlo al grupo del usuario que esta ejecutando.
**el ls es algo asi**
primero
```
archivo bibliotecaria:sigebi rwxrwxrwx
```
y luego
```
archivo bibliotecaria:bilbliotecaria rw-r--r--
```

y el programa (isis) devuelve un error que no puede escribir sobre ese archivo. cuando en realidad según veo yo en la lista de procesos es el mismo usuario el que corre dosemu ambas veces.

Probe compartir el directorio por sbmfs y el problema era el mismo solo que el archivo se cambiaba a 

```
archivo nobody:nogroup rw-r--r--
```

No conozco cual es la diferencia entre ejecutar un lanzador en el escritorio y hacer un llamado desde la consola. si alguien me podria contar un poco de eso lo agradecería porque no entiendo lo que pasa y los usuarios que utilizan este programa tiene muy poco conocimiento informático y les cuesta mucho abrir la consola y llamar al dosemu.

---

### Post by juancarlospaco on 2010-03-02
Podrias llamarlo ejecutando:

**xterm +hold -e "programa-a-ejecutar parametro-del-programa"**

Podrias ponerle los permisos adecuados, 
y que se ejecute con otro usuario diferente al que le asigno los permisos,
de esa manera no podria cambiarle los permisos el programa, 
si es que funciona bien el programa asi *(los permisos solo pueden ser cambiados por sus dueños)*.
:)

---

### Post by guillermolisi on 2010-03-02
> **juancarlospaco said:**
> 
Podrias ponerle los permisos adecuados, 
y que se ejecute con otro usuario diferente al que le asigno los permisos,
de esa manera no podria cambiarle los permisos el programa, 
si es que funciona bien el programa asi *(los permisos solo pueden ser cambiados por sus dueños)*.
:)
O hacer que esos usuarios formen parte de un grupo en particular y definis/administras los permisos para ese grupo determinado para la aplicacion que utilizan.

Los permisos pueden ser cambiados solamente por sus dueños .... y por un usuario comun usando "su" o "sudo".

---

### Post by filoquin on 2010-03-06
Mil gracias por las respuestas
El grupo lo cree  (se llama sigebi) el problema con eso es que en la red aun hay unas maquinas con w98 y una con w95 que se loguean a través de un dominio nt4.

Y no encontre manera de  que no accedan como usuario nobody:nogroup. 
Creo que cada inicio de sesión en el programa (sigebi) borra los archivos temporales y los vuelve a crear.  y la única solución que me funciono fue ponerles 777 a esos archivos.  

Igual de a poco estoy eliminando las maquinas con windows e instalando linux. y migrando algunas operaciones a entornos más nuevos (cdisis + wine) pero por ahora continuo dependiendo de un programa en dos escrito en pascal. Más allá de la resistencia al cambio que es otro tema. ;)

---


---
title: "Problema con ubuntu, reinicio constante"
date: 2009-06-18
forum: Software
---

### Post by ramirosj on 2009-06-18
Hola gente, hace un par de meses que vengo con ubuntu, en mi afan por configurar las cosas, y aprender un poco, me mande un par de mocos, por lo cual tube que formatear  y puse un nombre de usuario distinto cuando formatee , por lo que en directorio home, tenia 2 nombres  de usuario, pero solo uno activado, la cuestion es que para poder usar algunas cosas de la configuracion del usuario "a", y no tener q hacer tanto quilombo de vuelta, en el "administrador de usuarios" ( no tengo ni idea de como se llamaba) le asigne a mi usuario "b", la carpeta personal "a", luego de que reinicie, cuando termina de cargar ubuntu, la maquina se me reinicia, y entra en un circulo vicioso, alguien podria ayudarme con alguna solucion que no implique formatear nuevamente? 
desde ya, muchas gracias

---

### Post by pablo.s on 2009-06-18
Podés copiar la /home del
usuario a hacia la /home del
usuario b y luego borrar al
usuario a.

---

### Post by ramirosj on 2009-06-19
La cuestion es que directamente no me deja ingresar, mientras se carga el SO se me reinicia, podria hacer que me inicie directamente desde la consola, y desde ahi copiarlo? que comando se usa para copiar? es igual q en DOS?
gracias por tu respuesta

---

### Post by gmunioz on 2009-06-19
Hola ram...:

1- Cuando inicia el ordenador, pulsa escape, te aparecerá el memu del Grub.

2- Elige recuperación, (recovery), te aparecerá un submenu, elige netroot.

3- Iniciarás como administrador, sin contraseña y con conexión a internet,

con el fin de poder solucionar los problemas que se hubieran generado, en 

consola. en la consola:

a- Ejecuta, escribiendo y dando enter:

   ```

   apt-get update 

   apt-get upgrade

   apt-get install mc

   mc
```

Se iniciará midnight commander, un administrador de archivos y mas

muchísimo mas, en modo semigráfico, con dos ventanas. Con el podrás

copiar, borrar, mover, editar, dar permisos a archivos e infinitas cosas 

más.  
   

4- Te sugiero leas esta página, antes de efectuar algun cambio de usuario

con el fin de que sepas lo que puedes y no debes hacer al respecto:

```
http://www.linuxtotal.com.mx/index.php?cont=info_admon_008
```

---

### Post by ramirosj on 2009-06-19
Gracias Gmunioz, ahora me pongo a leer eso y a ver si puedo solucionar el problema =)

---


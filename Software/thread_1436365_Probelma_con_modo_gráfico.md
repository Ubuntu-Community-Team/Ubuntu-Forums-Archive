---
title: "Probelma con modo gráfico"
date: 2010-03-22
forum: Software
---

### Post by daggaz on 2010-03-22
Hola.
Pues resulta que instalé Xubuntu Karmic en una vieja Dell Inspiron 5100 con Pentium 4 a 2.40 y 256 mb. de RAM (desconozco la tarjeta de video). Quería probar Lubuntu, pero mejor me espero a que sea oficial.
Bueno todo salió bien. Instale el software que quería utilizar en esta PC y lo puse todo como a mi me gusta, pero había algo que no me convencía: Las notificaciones del sistema aparecían distorsionadas (todo negro con algunas rallitas blancas) por lo que no podía ver lo que me quería decir Xubuntu, no conozco mucho Xfce así que me dispuse a picar botones en la configuración del gestor de ventanas y activé algo que no debía: La pantalla desapareció y cuando volvió solo podía ver más distorsión pero en toda la pantalla. Se ve como cuando el viejo Super-Nintendo se congelaba y Mario podía caminar sobre el aire, o como esos libros de formas abstractas que si los ves de cierta forma puedes ver algo en 3d... En resumen, no veo nada mas que el cursor sobre este mundo de pixeles.
Presioné Ctr+Alt+F2 y pude entrar a modo de consola (lo único que me consuela por el momento). Ya probé con 
 ```
sudo dpkg-reconfigure xserver-xorg
```...pero no funcionó de nada. Creo que debo haber activado algo así como los efectos de escritorio para Xfce y la pobre laptop no lo soportó por que la tarjetas de video de seguro es muy poco poderosa.
¿Alguien sabe como puedo repara esto? No tengo Compiz, desde luego.
 Gracias.
[B]
Actualizo:[/B]
Encontré en un blog una sugerencia que recomendaba instalar Compiz desde la terminal y luego correrlo. OK. Lo instalo con *apt-get instal*l y listo. Luego trato de ejecutarlo y me dice muchas cosas, pero al final:
```
no xterm found, exiting
```Al intentar con 
```
compiz --replace
```me dice lo mismo.
Con 
```
xfm --replace
```me dice 
```
Error: Can't open display:
usuario@xubuntu:~$ [ 747.187394] b43legacy-phy0 ERROR: PHY transmission error
```Al escribir 
```
startx
```me dice lo siguiente:
```
Fatal server error:
Server is already active for display 0[INDENT]If the server is no longer running, remove /tmp/-X0-lock
and start again
[/INDENT]
```Y con :
```
sudo xfce4.panel & *(o- s)*
```me da```

xfce4-panel: No se puede abrir el visor
```

---

### Post by daggaz on 2010-03-27
Bueno... Quizás fue lo más bobo pero me funcionó:
Entre al Live-CD, apunté los pasos para poder entrar al administrador de ventanas y desactivar los efectos (que eran: 1 click secundario, 9 abajo, 1 derecha, 1 abajo, 1 derecha, enter, 4 derecha, enter, 6 derecha, 1abajo, spacebar).
Jaja. Bueno y listo, todo regresó, pero creo que ahora se desconfiguró algo por que mi escritorio aparece recorrido hacia la derecha abajo y mi fondo de escritorio desapareció. Pero es cosa de algo más sencillo seguramente (o por meter mano en el X). Y además, sigo sin poder ver las notificiaciones de Xubuntu :<

---


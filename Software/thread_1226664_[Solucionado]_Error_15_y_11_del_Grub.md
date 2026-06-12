---
title: "[Solucionado] Error 15 y 11 del Grub"
date: 2009-07-29
forum: Software
---

### Post by jose.ibarra on 2009-07-29
Buenas a la comunidad, he reiniciado mi notebook y me ha salido un mensaje de error en el grub

```
Error 15: File not found
Press any key for continue
```Algo asi,
Busque con un disco live la solucion y me encontre con supergrub disc, un p&#341;ograma de arranque, con el cual me salta el grub instalado e inicia el Sistema Operativo, luego debia hacer esto:

Abrir Consola(y solo como root):
```
upgrade-from-grub-legacy
``````
os-prober
```SI no estuviera instalado
```
apt-get install os-prober
```y para terminar
```
update-grub
```Con esto, el grub instalado es eliminado y se instala grub-pc, y deberia quedar solucionado todo, pero cuando reinicio el sistema, me sale error 11 donde salia error 15

Ante cualquier falla o solicitud de mas info, lo hago al toque

---

### Post by aledruetta on 2009-07-29
Parece ser que el error 11 está relacionado a un error (valga la redundancia) en los nombres de las particiones en el "menu.lst".

```
sudo gedit /boot/grub/menu.lst
```

Yo no soy la persona indicada, pero si posteás ese archivo, alguien que sepa puede encontrar el error.

Saludos y suerte,
Alejandro.

---

### Post by jose.ibarra on 2009-07-29
Hola, gracias por responder mi pregunta, te lo agradezco.

Encontre una solucion a este problema, instale [grub2]("http://ubuntuforums.org/showthread.php?t=1194661"), me funciona bien hasta el momento.

Gracias, por todo.

---

### Post by pagondel on 2009-07-30
Agregado el [Solucionado] al titulo ;)

---


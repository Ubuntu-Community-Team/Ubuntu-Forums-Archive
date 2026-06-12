---
title: "VirtualBox - acceso Internet"
date: 2009-05-25
forum: Software
---

### Post by aledruetta on 2009-05-25
Hola Comunidad!

Estábamos buscando una solución de escritorio compartido en estos hilos:

[http://ubuntuforums.org/showthread.php?t=1167241](http://ubuntuforums.org/showthread.php?t=1167241)
[http://ubuntuforums.org/showthread.php?t=1167738](http://ubuntuforums.org/showthread.php?t=1167738)

y me pareció que para tratar este tema era mejor crear uno nuevo.

Tengo instalado VirtualBox en Ubuntu Jaunty, y ahí, virtualizado, un Windows XP SP3.
He notado que, puedo:

[LIST]
[*]Navegar con Firefox y con Explorer;
[*]Puedo descargar archivos;
[/LIST]
Lo que no puedo, es:

[LIST]
[*]Acceder a la cuenta de Messenger ni usar cualquier servicio que dependa de una cuenta Microsoft Live, como ser Microsoft ShareView;
[*]No puedo conectarme con Skype;
[/LIST]
La configuración de red de la máquina virtual es la siguiente (predeterminada):

[B]Adaptador 1
Habilitar Adaptador de Red [x]
Adapter Type: PCnet-Fast III (AM79C973)
Attached to: NAT[/B]

He probado con otras configuraciones:

[B]Adapter Type: INTEL PRO/1000 MT Desktop (8254OEM)
[/B][B]Attached to: Bridged Adapter
[/B]
y sólo conseguí obtener "conectividad nula o limitada"[B].
[/B]
Se me ocurre, ustedes me corregirán, que, si tengo acceso a Internet para algunos servicios y para otros no, el problema debe estar en que "algo", ya sea en XP, Ubuntu o VirtualBox, está impidiendo la conexión de esos servicios que no funcionan ¿Iptables, quizá?Por favor, si tienen alguna idea, se los agradecería mucho. Si precisan más información, me avisan.

Saludos y muchas gracias,
Alejandro.

---

### Post by aledruetta on 2009-05-25
Bueno, finalmente di con la solución.

El problema estaba en una instalación malograda del firewall ZoneAlarm, en el XP, que estaba provocando conflictos. Conseguí limpiar todos los rastros de esa instalación y pude conectarme correctamente a Internet.

Así es que, si alguien quería saberlo, Microsoft SharedView funciona en XP y VirtualBox.

Gracias, igualmente.
Alejandro.

---


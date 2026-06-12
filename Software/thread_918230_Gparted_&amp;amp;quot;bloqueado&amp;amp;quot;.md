---
title: "Gparted &amp;amp;quot;bloqueado&amp;amp;quot;"
date: 2008-09-12
forum: Software
---

### Post by ramiro_md on 2008-09-12
Gente, tengo un problemita con el particionador, resulta que quiero sacarle 10 gb una particion de 111 gb para ponerselos a la particion ubuntera, pero el gparted no me deja hacer nada con ninguna particion, me aparecen como "bloqueadas" aca dejo un screenshot para que vean de que hablo.

---

### Post by ramiro_md on 2008-09-12
aca el screen

---

### Post by santiagoward2000 on 2008-09-12
Hola!
Mirá, no sé si se pueda hacer desde Ubuntu, ya que estarías cambiando una partición que está montada. Yo te recomendaría que lo hicieras desde el LiveCD. Desmontás las particiones (incluyendo el SWAP), y podés hacerlo sin problemas.
Saludos!

---

### Post by ramiro_md on 2008-09-12
Bueno, ok, pruebo desde el livecd. Pero para saber nomas, si la desmonto, ¿lo puedo hacer desde ubuntu?..preg para no hacer cagada, estoy yetado con las particiones ajajaj.UN saludo,

---

### Post by SLA_leandrin on 2008-09-12
Si, si lo desmontás lo podés hacer sin problemas, salvo que sea la partición donde tenés el sistema (o sea, /).

---

### Post by ramiro_md on 2008-09-13
aah, entonces no me va a servir, xq quiero sacar 10 gb para ponerlos en la "/", lo cual requiere que desmonte "/" verdad ?

---

### Post by SLA_leandrin on 2008-09-13
Si, hacela facil, bootea desde el LiveCD y en dos pedos lo tenés andando. Es muy fácil de hacer...

---

### Post by Thalskarth on 2008-09-13
> **SLA_leandrin said:**
> Si, hacela facil, bootea desde el LiveCD y en dos pedos lo tenés andando. Es muy fácil de hacer...

Te recomiendo la distro [Parted Magic]("http://partedmagic.com/wiki/PartedMagic.php") que es especial para hacer trabajos con particiones... es un livecd, se bootea en segundos (mas rapido que el de ubuntu), abris el Gparted y editas todo en 5 minutos..


Saludos

---

### Post by ramiro_md on 2008-09-13
OK gente, gracias, le meto solved x adelantado =).

---

### Post by ramiro_md on 2008-09-18
Muchachos, lo probe con el livecd pero siguen apareciendo las llavecitas al costado de la particioon (en gparted). En la consola me muestra lo siguiente:

No se puede abrir /dev/scd0 en modo lectura-escritura (Sistema de solo lectura). /dev/scd0 ha sido abierto en modo de sólo lectura.
No se puede abrir /dev/scd0 en modo lectura-escritura (Sistema de solo lectura). /dev/scd0 ha sido abierto en modo de sólo lectura.
No se puede abrir /dev/scd0 - etiqueta de disco desconocida.

Probe cambiando permisos con chmod a "/media/disk" "/dev/scd0" y a "dev/sda5"..no se si estaba o no errado pero de todos modos no funciono jejeje. Igual no estoy muy ducho con el chmod, utilice los parametros "777", "770", "766" y "-w". Bueno, un saludo y espero que me den una manopla. =)

---


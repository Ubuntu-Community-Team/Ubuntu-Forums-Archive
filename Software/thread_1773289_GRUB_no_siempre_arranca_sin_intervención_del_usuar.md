---
title: "GRUB no siempre arranca sin intervención del usuario."
date: 2011-06-01
forum: Software
---

### Post by Diego912 on 2011-06-01
Hola gente,
Les cuento como viene la mano: Estamos usando Ubuntu en unas PCs que se encienden al encender un vehiculo y se apagan (bruscamente, se corta la corriente) al detener el motor del vehiculo.
El tema es que a veces Ubuntu no arranca normalmente.
En realidad el problema esta en el GRUB, ya que esas veces queda preguntando con que S.O. arrancar (que en realidad es solamente Ubuntu, porque no tienen otro S.O.) sin timeout, o sea que requiere si o si de que alguien le presione ENTER.
El problema es que nadie esta en esas PCs, tienen que arrancar automaticamente siempre.
(cuando ocurre, quedan preguntando si arrancar en modo normal o en safe mode)

La pregunta es:
Hay alguna manera de EVITAR que GRUB haga eso? O al menos ponerle que use un tiempo de espera antes de arrancar con la opcion seleccionada?

Desde ya, muchas gracias!

PD: Usamos Ubuntu 10.10 con el GRUB por default, si mal no recuerdo es la version 2 de GRUB.

---

### Post by guillermolisi on 2011-06-01
Esas PCs van a durar poco si las siguen usando asi y menos va a durar el filesystem de cada disco que, por cuestiones de consistencia, obliga a Grub hacer la parada para iniciar en modo recovery, correr un fsck, normalizar la estructura y contenidos y despues iniciar normalmente.

Confiar en una PC con Linux a la que se le da ese trato es utopico. En algun momento te deja a pie (por mas que el motor del vehiculo este en marcha). :)

---

### Post by Diego912 on 2011-06-01
Entiendo Guillermo, en realidad ese no seria el problema.
Si falla el FS se reinstalan, ya que no son maquinas que contengan informacion imprescindible, sino publicidades, y para esto mismo estan los tecnicos que las verifican una vez al dia.
Habra alguna manera de evitar esa detencion de GRUB?

---

### Post by biale on 2011-06-02
Analizá la calidad de la tensión eléctrica durante el transitorio de arranque y la calidad de la tensión eléctrica en el modo permanente.

También las vibraciones que solicitan al equipo. Sobre todo en lo que haga a los conectores y (fundamental) al disco rígido.

Para la desconexión tenes dos opciones. La primera sería adoptar Ext3 (y no 4) con las limitaciones que ya dijo Guillermo. La segunda sería correr a Ubuntu en RAM.

---

### Post by granjero on 2011-06-02
Otra cosa que podés ver de hacer es conseguir un UPS que tenga un cable serial para que le "avise" a la PC que se cortó la energía y mande la señal de apagado. Usando la batería del UPS hasta que se apague la PC. De esa manera no estresarías tanto al sistema.



Salud!

---

### Post by guillermolisi on 2011-06-02
> **biale said:**
> Analizá la calidad de la tensión eléctrica durante el transitorio de arranque y la calidad de la tensión eléctrica en el modo permanente.

También las vibraciones que solicitan al equipo. Sobre todo en lo que haga a los conectores y (fundamental) al disco rígido.

Para la desconexión tenes dos opciones. La primera sería adoptar Ext3 (y no 4) con las limitaciones que ya dijo Guillermo. La segunda sería correr a Ubuntu en RAM.
Me gusto la idea de correr en RAM y agrego: En modo Live, asi no hay problemas con ningun filesystem (inclusive ext3) y la parada del Grub.

Hay versiones de GNU/Linux que pueden correr en desde un pendrive de 1Gb y con 128 de RAM funcionan barbaro. Habria que agregar lo que requiera la aplicacion que estan usando para dimensionar una maquina a prueba de cortes de energia.

---

### Post by Diego912 on 2011-06-02
Muchas gracias por todas las respuestas!

La idea de correr en RAM, no se si pueda servir en este caso, ya que existe una gran cantidad de información (vídeo e imágenes) que están volcadas a disco (varios GBs), y que el software de Digital Signage debe reproducir secuencialmente.


Lo del UPS me parece una excelente idea! Lo que si deberían ser muy pequeños dichos UPS, porque el espacio es bastante limitado. De todos modos un UPS tiene su mayor espacio ocupado por la batería, y en este caso la batería debería ser muy pequeña, ya que Ubuntu demora no mas de 10 segundos en cerrarse y apagar el equipo. Lógicamente esta solución ayudaría a cuidar mas tanto el software como el hardware, la vida útil de ambos.


Si realmente GRUB no se detiene en el apagado incorrecto de Ubuntu sobre Ext3, entonces trabajar sobre Ext3 seria una buena solución efectiva, de bajo presupuesto, aunque quizás no sea el mejor cuidado para el hardware.

---

### Post by guillermolisi on 2011-06-03
> **Diego912 said:**
> Muchas gracias por todas las respuestas!

La idea de correr en RAM, no se si pueda servir en este caso, ya que existe una gran cantidad de información (vídeo e imágenes) que están volcadas a disco (varios GBs), y que el software de Digital Signage debe reproducir secuencialmente.


Lo del UPS me parece una excelente idea! Lo que si deberían ser muy pequeños dichos UPS, porque el espacio es bastante limitado. De todos modos un UPS tiene su mayor espacio ocupado por la batería, y en este caso la batería debería ser muy pequeña, ya que Ubuntu demora no mas de 10 segundos en cerrarse y apagar el equipo. Lógicamente esta solución ayudaría a cuidar mas tanto el software como el hardware, la vida útil de ambos.


Si realmente GRUB no se detiene en el apagado incorrecto de Ubuntu sobre Ext3, entonces trabajar sobre Ext3 seria una buena solución efectiva, de bajo presupuesto, aunque quizás no sea el mejor cuidado para el hardware.
Actualmente conseguis UPS con baterias de gel que ocupan poco espacio y te darian el tiempo suficiente para un apagado correcto.

En mi opinion, usar ext3 no seria una solucion al tema ya que tanto este como ext4 son file systems con "journal" y es una de las razones por las que Grub para para correr el fsck o iniciar la maquina en modo recuperacion.

---

### Post by biale on 2011-06-03
En un pendrive (o similar) se puede poder un arranque live y unos cuantos Gbytes de datos. Como Linux no modifica los datos no tiene que escribir nada y el montaje puede ser en modo solo lectura.

Igual la UPS puede ser una necesidad por la proteccion electrica del equipo.

---

### Post by ferfernando on 2011-11-17
He resuelto este problema modificando lo siguiente:
cambie esto
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
por esto otro
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10

Ahora aunque falle el ranque o se apague el equipo siempre espera 10 segundos.

Espero te sirva.

---

### Post by mama21mama on 2011-11-17
Creo que lo del ups es muy buena solución;

al tener energía de la batería que mande la señal de apagado.

Muy buena opción la usaría si fuesen mis equipos.

---


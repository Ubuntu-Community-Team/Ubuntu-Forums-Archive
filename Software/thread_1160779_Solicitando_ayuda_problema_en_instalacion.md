---
title: "Solicitando ayuda problema en instalacion"
date: 2009-05-16
forum: Software
---

### Post by shadow_iv on 2009-05-16
Tengo una PC Pentium III con 256 en Ram compartido con Video de 32 y dos discos duros. Por las características de la PC he decidido instalar Xubuntu (versión 9.04) que debería andar bien según los requerimientos de hardware.

He hecho correr el Live CD de xubuntu (y tb ubuntu 9.04) y anda sin problemas, pero cuando he tratado de instalar primero me pasó que se quedaba pegado en negro la pantalla antes de acceder al cualquier información gráfica de instalación, esto me ocurrió como 4 veces. Así que decidí instalarlo desde el escritorio del Live CD. Todo bién hasta cuando comenzó a copiar los archivos del sistema, se pegó en un 5% y no avanzó más. Pensé entonces que podía ser el CD  que estuviera dañano, entre a la ópción de revisar y me arrojó que justamente el CD tenía sectores malos, pero hice varias copias y todas lo mismo. Me dije entonces mi grabador es el dañado. Me llevé mis copias de los CD de instalación a otro PC más moderno y resulta que allí la revisión me decia que los CD están OK al 100% buenos. Ahora me dije, mejor me llevo las lectoras de este pc a la makina mas vieja, corrí de nuevo la revisión en la maquina mas viejita con las lectoras cambiadas y de nuevo el mismo problem ... sus CD tienen sectores dañados.

Me decidí a probar instalando xubuntu desde dentro de windows (wubi) y se instaló sin problemas, pero no anda a la velocidad que debería, ya que obvio corre dentro de una partición NTFS. He vuelto a probar instalarlo de la forma tradicional y nada. Hice un test a mis memorias y están al 100%.

No sé si debería tratar de instalar desactivando algo, ya sea el acpi o apic o lapic. ¿Qué piensan Ud., que pueda estar pasando y cuáles puedan ser mis opciones? ¿Qué diferencias habría si restrinjo algunos de los modos del GRU? se que es el acpi, pero desconozco en forma sencilla que hacen las opciones apic o lapic. ¿Qué puedo hacer?

Necesito consejos!

Saludos

---

### Post by emiliano_raso on 2009-05-16
Puede ser por la cantidad de memoria ram...

Probá con el Alternate CD [http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_con_Alternate_CD](http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_con_Alternate_CD)

---

### Post by guillermolisi on 2009-05-16
Para iniciar en modo LiveCD con 256Mb RAM alcanza pero para instalar las recomendaciones son no menos de 384.

Hay una forma para iniciar la instalacion, sin entrar en la sesion grafica, que es seleccionando la opcion de instalacion en el menu de inicio del CD, apenas arranca la maquina, debajo de la opcion de iniciar la sesion en modo Live/usar sin instalar (creo que es la segunda de arriba hacia abajo en el menu).

---

### Post by hictio on 2009-05-16
A me pasó lo mismo en todas las instalaciones que hice de Hardy para arriba en un  Pentium II @ 350 MHz con 512 MB de RAM.
Yo lo solucioné en todos los casos instalando desde el Alternate, pero a pesar de eso, usando la opción "Install a Command Line Only System", y después instalarle lo demás via aptitude.

---

### Post by shadow_iv on 2009-05-16
Pero para ubuntu es 384 Mb recomendados de memoria RAM, para Xubuntu es 198 de RAM para Live CD y 128 Mb una vez instalado.

Probe alternative CD y tengo el mismo problema. Para instalarlo vía consola ¿Cómo lo hago?. ¿Qué me dicen de las ópciones de acpi y apic o lapic?. Además he visto en algunas web quienes han logrado instalar xubuntu sin problemas en máquinas de menos recursos que la que yo tengo.

Gracias por las respuestas

---

### Post by Hei Ku on 2009-05-16
Quizas tenes algun conector mal u otro problema de hardware. Hay varios componentes intermedios ademas de la lectora. Con ese hardware estas al borde, no solo por la RAM sino por la CPU. No me refiero a linux, sino a X/Ubuntu en particular. Yo probaria con alguna version que tenga LXDE u Enlightment. Si lo que queres es probar, entonces te va a andar bien, y no te vas a volver loco en la instalacion.

---

### Post by shadow_iv on 2009-05-17
Wau!! no conocia nada de OpenGU y lo que he leído en estos pocos minutos desde su página oficial me deja sorprendido, incluso lo estoy bajando. Gracias por la información. Yo ya había decidido que si no avanzaba mucho con xubuntu iría por la instalación de Zenwalk que también lo encuentro muy bueno, de las distro Slax pero OpenGU parece que será una de mis opciones en la lista.

A pesar de ello sigo interesado en Xubuntu así que cualquier ayuda aún la seguiré agradeciendo.

Saludos

---


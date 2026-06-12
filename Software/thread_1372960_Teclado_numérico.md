---
title: "Teclado numérico"
date: 2010-01-05
forum: Software
---

### Post by Iced_R on 2010-01-05
Bueno, abro este post xq tengo ese problema. Mi teclado numérico ha muerto, pero lo chistoso es q sólo murió en Ubuntu. Tengo instalado Karmic, y sé que por tema de hardware mi teclado munérico si está vivo, pues lo uso cada vez q juego en GUIndows (tengo booteo dual en mi tarro). Ahora, la pregunta es: ¿Qué puedo hacer para intentar arreglar mi teclado numérico?

Un lspci hecho a mi computador revela esto:

```
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

Saludos, y gracias de antemano ;)

---

### Post by Carlos C on 2010-01-05
Hola.
¿Es un teclado genérico o tiene alguna particularidad especial?
¿Te aseguraste haber presionado "BloqNum"?
¿Se prende el led que señala que el teclado numérico está accionado?

Saludos.

---

### Post by moreback on 2010-01-05
Yo creo que la cosa va por ver qué configuraciones tiene en Sistema -> Preferencias -> Teclado, específicamente en la pestaña Distribuciones.

Un pantallazo sería de gran ayuda.

Saludos cordiales.

---

### Post by Iced_R on 2010-01-05
El teclado es un vil teclado numérico. De esos comunes y silvestres sin ningún botón adicional, salvo esos de Power, Sleep y Wake Up que usualmente no sirven para nada xD.

Obviamente que mantengo activo el Bloq Num, pero no funciona. Como dije, el teclado numérico no funciona, pero raramente sí funciona la tecla Intro.

Y mi distribución de teclado es la predeterminada de España. Karmic reconoce un teclado genérico de 105 teclas.

Pego el pantallazo de la distribución de teclado.

[[IMG]http://img696.imageshack.us/img696/872/pantallazos.th.png[/IMG]](http://img696.imageshack.us/i/pantallazos.png/)

---

### Post by Carlos C on 2010-01-05
Puede que esta sea la solución:

[http://ubuntuforums.org/showthread.php?t=773154](http://ubuntuforums.org/showthread.php?t=773154)

Saludos.

---

### Post by moreback on 2010-01-05
No entiendo si estás hablando de un segundo teclado numérico USB o es la extensión numérica de tu teclado normal la que ha dejado de funcionar.

Si es uno USB un **lsusb** nos daría detalles del hardware que estamos tratando.

Otra cosa sería que a lo mejor tienes activada la opción "Permitir controlar el puntero usando el teclado numérico" que aparece en la pestaña "Teclas del ratón" del diálogo que pusiste.

Saludos cordiales.


PD: no había visto el post de Carlos_C, pero apunta a la última opción que comenté.

---

### Post by Iced_R on 2010-01-06
Carlos_C, gracias. No entiendo muy bien por qué se activó esa opción, o por qué, siendo q antes funcionaba bien mi teclado numérico, de repente dejó de funcionar, pero ya puedo volver a escribir con los números.

Para los q no entiendan mucho de inglés, la respuesta sería lo q dijo moreback. Deshabilitar el poder mover el mouse con el teclado numérico. Eso se hace en Sistema > Preferencias > Teclado > Teclas del ratón. Ahi clickean el checkbox que permite mover con el teclado el puntero del mouse (el único q hay xD).

Saludos a todos, y gracias

---

### Post by suso_chopper on 2011-01-21
Gracias, tenía justamente el mismo problema ;-)

---

### Post by agabucha on 2012-08-13
:smile: Muchas gracias me sirvio de mucha ayuda :popcorn:

---

### Post by sshareit on 2012-10-30
Gracias, yo tampoco entiendo como se activo esta opcion...

---


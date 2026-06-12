---
title: "Usar impresoras en VirtualBox (especialmete Lexmark)"
date: 2009-12-28
forum: Software
---

### Post by nechus on 2009-12-28
Por si a alguien le sirve mi experiencia, les cuento que tuve muchos problemas para instalar y hacer funcionar mi Lexmark X2350 en XP corriendo en VirtualBox. Ni siquiera se tomen la molestia de tratar de hacerla funcionar en Ubuntu porque Lexmark sencillamente no da soporte a Linux. Punto.

Conecté la impresora al puerto USB, inicié Windows en VirtualBox, pero no pescaba la impresora para nada. En la pantalla de configuración de VirtualBox, en la sección USB, la impresora aparecía conectada, pero nada.

Hasta que me cayó la teja, y fui a Sistema > Administración > Usuarios y grupos, y añadí mi cuenta al grupo vboxusers.  ¡Y eso era todo!  La siguiente vez que inicié Windows empezaron a aparecer un montón de mensajes de "nuevo hardware encontrado" y pude instalar y usar la impresora.

Y si alguien todavía tiene problemas con eso, añada su cuenta al grupo lp. No pregunten por qué, porque no sé.

---

### Post by Masrealque_Dios on 2010-01-05
holaaa

algo para agregar, a veces por alguna razón si agregas tu usuario al grupo VBOXUSSER y aun no te pesca la impresora, en esa misma ares de configuracion hay otro grupo que es "lp" (LP no ip) agregan su usuario a ese grupo, reinician y listeilor :D

a mi me paso con una canon ip1300 que no me funciona con AMD64 aun no hay soporte

saludos

---


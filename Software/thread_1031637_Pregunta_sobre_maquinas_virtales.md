---
title: "Pregunta sobre maquinas virtales"
date: 2009-01-05
forum: Software
---

### Post by dj_isaco on 2009-01-05
hola muchachos mi pregunta el la siguente
si cual me conviene mas, instalar una MaqVirtual en ubuntu y correr desde ella win o instalar win en una particion diferente, ya q yo utilizo mucho el PS CS4 y con wine no corre, probe con gimp para hacer los royectos pero ahi muchas cosas q no puedo hacer.

el otro tema es si instalando la MaqVirtual puedo ver desde ella todos los archivos de mis discos y/o redes, como se hace?, ya q le instale a mi primo la virtalbox en el server del ciber del cual es dueño y no pudimos ver nada. ni la red, para controlar las pc-clientes ni sus discos rigidos.
pd: el server del ciber tiene como s.o. windows xp sp2

espero q me puedan ayudar desde ya saludos y gracias

---

### Post by guillermolisi on 2009-01-06
> **dj_isaco said:**
> hola muchachos mi pregunta el la siguente
si cual me conviene mas, instalar una MaqVirtual en ubuntu y correr desde ella win o instalar win en una particion diferente, ya q yo utilizo mucho el PS CS4 y con wine no corre, probe con gimp para hacer los royectos pero ahi muchas cosas q no puedo hacer.

el otro tema es si instalando la MaqVirtual puedo ver desde ella todos los archivos de mis discos y/o redes, como se hace?, ya q le instale a mi primo la virtalbox en el server del ciber del cual es dueño y no pudimos ver nada. ni la red, para controlar las pc-clientes ni sus discos rigidos.
pd: el server del ciber tiene como s.o. windows xp sp2

espero q me puedan ayudar desde ya saludos y gracias
En lineas generales la recomendacion es instalar Ubuntu como host OS y en una VM el XP, asi te beneficias de las caracteristicas de Linux para correr la VM.

Una limitacion a considerar es que por ahora las aplicaciones para virtualizar (VMware y VirtualBox, para ser mas preciso) no permiten aceleracion 3D en la placa de video. Con esto te digo que si necesitas usar algun plugin de PS que precise de esa funcionalidad no lo podras hacer.

Para el caso del ciber, mi recomendacion pasaria por usar VMware ya que con una sola consola de administracion podes controlar todas las VMs que tengas en uno o mas hosts (esta pensado para entornos corporativos).

Para ver otra red con Win desde Ubuntu, como la del caso del ciber, es necesario instalar y configurar Samba.

---


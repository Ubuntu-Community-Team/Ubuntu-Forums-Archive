---
title: "Coneccion Internet (gestor Synap/actualizaciones) [Ubuntu]"
date: 2009-02-10
forum: Software
---

### Post by sebasthian777 on 2009-02-10
Hola Gente!!! despues de mucho tiempo volvi por estos pagos,... pero lamentablemente para presentarles y ver si me pueden ayudar con un pequeño problema,

en mi lugar de trabajo logre convencer para que pongan ubuntu en 1 pc para ir testeando como se desenpeña con el Lazarus (programacion en pascal, onda el delphi) el tema es que la instalacion todo muy linda, la coneccion a internet tmb, puse el proxy en la configuracion del zorrito lindo (firefox) y carga bien internet, pero.....

Mi real problema radica en que cuando quiero hacer una actualizacion o descargar soft desde los repositores, ya sea utilizando el synaptic o por terminal, no se conecta... a ver, lo voy a tratar de explicar con ejemplo...


suponiendo que quiera instalar el samba por medio de la terminal con el apt-get install

```
root@digitales01-desktop:/home/digitales01# apt-get install samba
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Paquetes sugeridos:
  openbsd-inetd inet-superserver smbldap-tools
Se instalarán los siguientes paquetes NUEVOS:
  samba
0 actualizados, 1 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 3839kB de archivos.
Se utilizarán 9429kB de espacio de disco adicional desp
```

y en la ultima linea queda colgado el cursor y no avanza nunca mas :P


ahora bien, puede que tenga que configurar el tema de la coneccion de las actualizaciones ??? si me pueden ayudar se los agredesco muchisimo, yo me conecto desde el ubuntu a internet por el explorador firefox por medio de un proxy... no se si tendre que cambiar algo o modificar que :S realmente estoy con bastante laburo y me gustaria encontrar la forma de solucionar este inconveniente...


desde ya muchas gracias!!!!

un saludo grande para todos!!!:guitar:



edit:

----------------------


perdon disculpen... ahora me dice que expira el tiempo de coneccion, o sea que no se conecta, ahora si gracias!!!

---

### Post by Hei Ku on 2009-02-10
Tenes que agregarle el proxy a la configuracion del apt-get.
Creo que desde Synaptic podes tambien.

---

### Post by sebasthian777 on 2009-02-10
> **Hei Ku said:**
> Tenes que agregarle el proxy a la configuracion del apt-get.
Creo que desde Synaptic podes tambien.

Gracias, perfecto, me averguenzo de lo idiota que fui, por hacer las cosas apurado me salte eso... se agradece mucho!!!

muy buen dia y gracias otra vez! 

(pd: lo realice directamente desde el synaptic, en herramientas si mal no le pifio, :P)

---


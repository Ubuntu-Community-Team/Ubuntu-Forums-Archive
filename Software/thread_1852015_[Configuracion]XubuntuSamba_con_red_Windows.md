---
title: "[Configuracion]Xubuntu/Samba con red Windows"
date: 2011-09-29
forum: Software
---

### Post by GNic on 2011-09-29
¡Hola comunidad!.
Vengo a recurrir aqui, porque no logro conectar mi Xubuntu con todo el resto de la red de archivos windows.
Para sorpresa, tengo otra computadora con Ubuntu y se conecta perfectamente con las demás computadoras.
Hice de todo, configurar por medio de tutoriales/guias en internet, copiar y pegar los archivos de configuración del samba de Ubuntu en el Xubuntu, desactivar el firewall de Xubuntu.
Me quede sin ideas, ya que soy nuevo en el universo Ubuntu.
Espero puedan ayudarme.
Si desean que ponga en este topic las configuraciónes del smbd, avisenmen que lo hago =).
¡Muchas gracias!

---

### Post by hictio on 2011-09-29
Mhhhm... Los archivos de configuración ya lo probaste y no caminó; te fijaste si podrá ser un problema de versiones?
Que release de Ubuntu es? (en el cual funcionan las cosas) Y qué release de Xubuntu? (en el cual no camina)
Tienen las mismas versiones de Samba, smbclient, etc?

---

### Post by guillermolisi on 2011-09-29
> **GNic said:**
> ...
Hice de todo, configurar por medio de tutoriales/guias en internet, copiar y pegar los archivos de configuración del samba de Ubuntu en el Xubuntu, desactivar el firewall de Xubuntu.
...
Solo por curiosidad, no porque realmente sea necesario "desactivar" el firewall para que una LAN funcione con recursos compartidos, como procediste para "desactivar" el firewall ?

---

### Post by GNic on 2011-09-30
Gracias Hictio y Guillermolisi por sus respuestas.
Contesto las dudas:
@Hictio: Ambos SO son la misma versión (11.04) y me fije si faltaba algun paquete synaptic, pero estaba todo en regla.
@Guillermolisi: Antes de recurrir a este foro, decidi pasar por el IRC de soporte de Ubuntu y Xubuntu.
Alli me advirtieron del firewall, asi que lo busque para saber cual era, y desactivarlo por medio de la terminal.
¿recomiendan que empieze de cero con las configuraciones?
Espero esto ayude ^^.

---

### Post by guillermolisi on 2011-09-30
> **GNic said:**
> ...
@Guillermolisi: Antes de recurrir a este foro, decidi pasar por el IRC de soporte de Ubuntu y Xubuntu.
Alli me advirtieron del firewall, asi que lo busque para saber cual era, y desactivarlo por medio de la terminal.
¿recomiendan que empieze de cero con las configuraciones?
Espero esto ayude ^^.
No decis como desactivaste el firewall, solo que lo desactivaste y en Linux hay una sola forma de lograr eso: Borrar todas las reglas de IPTables.

Si hiciste eso, revisa que no te haya quedado alguna regla activa (con lo cual el firewall trabajara en funcion de ella). Si no hiciste eso, contanos que hiciste para confirmar efectivamente que esta desactivado.

---

### Post by GNic on 2011-10-03
[FONT=Trebuchet MS]Lamento no haber contestado en todo el fin de semana, pero sucede que el computador en el que tengo instalado Xubuntu esta en mi lugar de trabajo.
Me indicaron que tipeara un comando con "disable" dentro de la terminal (en estos instantes no me acuerdo exactamente del comando), por lo visto no desactive el firewall.
Aunque estoy dudando de que sea el firewall, ya que creo que el Ubuntu lo tiene activado (no puedo confirmar porque es la netbook de un compañero de trabajo).
Agradezco mucho sus respuestas.
[/FONT]

---


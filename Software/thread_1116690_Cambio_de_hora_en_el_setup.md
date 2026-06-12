---
title: "Cambio de hora en el setup"
date: 2009-04-05
forum: Software
---

### Post by rodolfolara on 2009-04-05
Amigos, cuando cambio los discos de U a W, en este ultimo simepre me aparece la hora adelanta en 3 unidades.
Si vuelvo a U, la hora es la correcta.
Seteo la hora correcta en el septu, pero U me la modifica.
Pq será?
Gracias por su pronta respuesta

---

### Post by Hei Ku on 2009-04-05
Porque Linux usa la hora en GMT, y Windows la hora local. Por eso, casualmente, te aparece siempre adelantada o atrasada en 3 horas (salvo en verano ;) )
Configura en Ubuntu para que use la hora local.

La forma mas facil es hacer click derecho sobre el reloj del panel, configurar hora, y despues destildar la casilla que dice "Usar UTC" o algo similar.

---

### Post by rodolfolara on 2009-04-06
Gracias mil!!!

---

### Post by guillermolisi on 2009-04-06
> **Hei Ku said:**
> Porque Linux usa la hora en GMT, y Windows la hora local. Por eso, casualmente, te aparece siempre adelantada o atrasada en 3 horas (salvo en verano ;) )
Configura en Ubuntu para que use la hora local.

La forma mas facil es hacer click derecho sobre el reloj del panel, configurar hora, y despues destildar la casilla que dice "Usar UTC" o algo similar.
Por las dudas revisaria en Win que huso horario esta usando. Deberia ser uno que te de -3 horas de diferencia (Buenos Aires).

Si, ademas, Win sincroniza la hora con algun servidor nttp en Internet, se va a corregir en funcion de lo que ese huso horario y tu ubicacion (pais) estes usando.

El reloj del BIOS siempre debe tener la hora loca, la que dice tu reloj de pared o pulsera. Las adecuaciones hay que hacerlas en los sistemas operativos que utilices configurando correctamente el huso horario y pais en donde estes utilizando la maquina. Sino, te vas a volver loco tratando de homologar fecha y hora entre los componentes de tu sistema (y ni hablar de los mails, que seran recibidos antes de que haberse enviado :p a los ojos del destinatario)

---


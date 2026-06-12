---
title: "Se pierde conexión"
date: 2009-05-29
forum: Software
---

### Post by pol666 on 2009-05-29
Hace unas semanas abri un tema donde comentaba que despues de quedarme sin internet y toquetear cuanto archivo tenga se me hizo un lio barbaro. Yo venia usando mi placa de red PCI hasta que dejo de funcionar en todos los sistemas, llegue a la conclucion que se habra roto cuando se salio del puerto PCI accidentalemente. Ademas con el ubuntu recien instalado pasa lo mismo, descarto entonces un problema del sistema,

Con la placa onboard linux nunca se llevo bien, algunas distribuciones ni la reconocen, En ubuntu anda, pero estoy teniendo un problema, y no se si adjudicarselo al maldito puerto ethernet o  al modem. Lo que sucede es que cada 5 minutos mas o menos se pierde la conexion a internet, pero la linea sigue activa, el modem figura como conectado, pero simplemente no hay internet, si reinicio el modem vuelve todo a la normalidad. ¡¿Que significa eso?

En este caso, mas que dejarles la configuracion WAn del modem router no puedo hacer, que los mas expertos se fijen bien si lo routie correctamente 

[[IMG]http://i44.tinypic.com/2ccngog_th.png[/IMG] ]("http://i44.tinypic.com/2ccngog.png")

PD: Ya cambie de todo, los dns, el MTU, que mas me falta?

---

### Post by guillermolisi on 2009-05-29
Cambiar de proveedor de Internet ?;)

Podes probar esa maquina con otro proveedor, sea ADSL o cable y ver como se comporta ?

Si funciona bien, no es la PC ni el software, a menos que no puedas probar usando USB (en ese caso quedaria la duda sobre el USB solamente).

Se entiende la idea ?

---

### Post by pol666 on 2009-05-29
No hay otro proveedor adsl en esta parte e Banfield guillermo :(, por 5 cuadras no llega el cableado de nada.

por cierto, hice algo momentaneo que creo que era la causa, deshabilite lo siguiente

Blacklist Status
Attack Protection
DOS Protection

Si, suena INSEGURISIMO pero estuve un buen tiempo sin cortes, voy a dejarlo así y si se corta restauro lo previo.

---

### Post by guillermolisi on 2009-05-29
> **pol666 said:**
> No hay otro proveedor adsl en esta parte e Banfield guillermo :(, por 5 cuadras no llega el cableado de nada.

por cierto, hice algo momentaneo que creo que era la causa, deshabilite lo siguiente

Blacklist Status
Attack Protection
DOS Protection

Si, suena INSEGURISIMO pero estuve un buen tiempo sin cortes, voy a dejarlo así y si se corta restauro lo previo.
Ahhh .. si vivis en Banfield te entiendo (conozco algunas personas que padecen el monopolio de Telefonica en esa localidad, muy linda por cierto).

Parece inseguro si usas Windows, pero teniendo Linux, cual es el problema ?
Hace de cuenta que tenes un cablemodem ....

Y sigue funcionando bien ?
El modem estara en buenas condiciones operativas ?

---


---
title: "Conexión VPN del tipo sstp"
date: 2013-04-16
forum: Software
---

### Post by wloose on 2013-04-16
Buenos días estimados,
       hace un par de meses la empresa para la cual trabajo a cambiado la forma de acceder a su VPN de PPTP a SSTP y no encuentro la forma de conectarme desde linux, salvo emulando windows a través del VirtualBox.
¿Es posible conectase a la VPN sin virtualizar Windows?

Desde ya muchas gracias anticipadas, voy a quedarme anciosamente sus respuestas.

Les mando un gran abraso [CENTER][COLOR=#000000]):P[/COLOR][/CENTER]

---

### Post by MeduZa on 2013-05-15
te digo una cosa, yo virtualizaria de todas formas, ya que de esa manera podes estar en tu red y en la VPN a la vez ;)
en mi trabajo usan cisco VPN que tiene cliente para linux pero prefiero crear una VM y hacer el VPN ahi, asi puedo seguir con la libertad de usar mi internet y mi radio stream :D que la red de la empresa no podría por estar blokeada o incluso bajo vigilancia!

ahora volviendo a tu pregunta la verdad que no tengo idea, nunca necesite usar ese tipo

---

### Post by gmunioz on 2013-05-17
Necesitas descargar tres paquetes de aqui:
> [http://sourceforge.net/projects/sstp-client/files/](http://sourceforge.net/projects/sstp-client/files/).
sstp-client deb package from sstp-client section
network-manager-sstp-gnome deb package from network-manager-sstp section
network-manager-sstp deb package from network-manager-sstp section
Descarga los que correspondan a tu arquitectura, i386 para 32-bit ó amd64 para 64-bit
Los que son para 32-bit eran:
> sstp-client_1.0.9_i386.deb
network-manager-sstp-gnome_0.9.4-0ubuntu2_i386.deb
network-manager-sstp_0.9.4-0ubuntu2_i386.deb
Una vez descargados, abres una terminal y los instalas mediante dpkg
> sudo su 
dpkg --install sstp-client_1.0.9_i386.deb
dpkg --install network-manager-sstp-gnome_0.9.4-0ubuntu2_i386.deb
dpkg --install network-manager-sstp_0.9.4-0ubuntu2_i386.deb
O en modo gráfico con gdebi, sistema de preferencia, pulsando sobre cada paquete y eligiendo instalar.
Reinicia.
Luego del reinicio con figura la conexión mediante el icono de conexiones eligiendo
"Conexiones VPN"
"Configurar VPN"
"Crear"
"SSTP"
Es necesario que en avanzados Yespecifiques el puerto de acceso del server
Por ejemplo sstp-ar2.reftvpn.com:993 (IMAPS port 993)

---


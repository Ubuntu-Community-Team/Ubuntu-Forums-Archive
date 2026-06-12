---
title: "Configurando mi primer server ubuntu"
date: 2011-08-07
forum: Software
---

### Post by plooxy on 2011-08-07
Un saludo foreros , necesito ayuda para montar un servidor casero , ya tiene intalado ubuntu server 11.04 soy un poco nuevo en linux pero aprendo rapido  quiero el server para FTP,Maquinas Virtuales, VPN24/7 y firewall

**Maquina(server):**
[LIST]
[*]Intel Dualcore 2.0
[*]3 Gb ram
[*]500gb
[*]2 tarjetas de red
[/LIST]

**Algunos de los programas con los que me e encontrado que me pueden servir son :**

[LIST]
[*]Firestarter
[*]Bind9
[*]dnsmasq
[*]proftp
[*]virtualbox
[/LIST]


**Esquema de la conexion :**

ADSL Router del ISP -> Swith/hub -> Servidor Ubuntu -> Router Wifi -> PC1,PC2...


por donde empezar ?

---

### Post by alfplayer on 2011-08-08
¿Por dónde empezar la respuesta? ;)

---

### Post by marohds on 2011-08-09
No entiendo por qué la conexión de un switch/hub al servidor cuando únicamente va a estar conectado a un módem de ADSL.
 
Luego, si sos nuevo en linux, te recomiendo antes probar instalar un servidor de red, algo simple como un Samba en una red local, y todo el tema de ruteo, dns y firewall dejárselo al Router que está para eso.
 
O sea, haría:
 
PC1, PC2
        |
   Router WIFI ------ Módem
        |
   Server
 
Y, me metería en temas más relevantes tales como configurar un servidor de mail interno, un sistema de backup, quizá haría un RAID por software al server. En este esquema podrías instalar un Samba para la red local y un servidor FTP para permiitir la transferencia de archivos desde y hacia la internet, así como una VPN.
 
Me abstengo el comentario sobre servidor para máquinas virtuales.
 
¿Qué utilidad querés darle al server luego de instalar todo?

---


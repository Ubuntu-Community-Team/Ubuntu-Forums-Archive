---
title: "Problema, MSN"
date: 2008-06-15
forum: Software
---

### Post by gefarion on 2008-06-15
Buenas, tengo un problema bastante extraño. Basicamente tengo una red de 2 computadoras, La cual una comparte internet a la otra. En ambas tengo instalado Kubuntu 8.04. De la maquina que se conecta directamente a internet puedo conectarme sin problemas a la red de MSN, pero despues la otra no hay forma, probe casi todos los clientes que hay (pidgin, kopete,kmess,amsn,etc) Pero no logro conectarme. Lo extraño es que desde la misma maquina desde windows xp si puedo conectarme, ya sea con el msn, pidgin o cualquier otro cliente.

Alguna idea?.

Saludos.

---

### Post by xpelaox on 2008-06-15
Hmmm pero en la maquina con el problema, tenes internet?

---

### Post by gefarion on 2008-06-15
Si, el problema es con Ubuntu en la segunda maquina. La que actua como servidor funciona sin problemas. 
Si tengo internet, anda todo, es mas con el kopete puedo conectarme a otras redes como yahoo por ej. El tema es solamente conectarme a la red msn desde linux, porque desde windows conecta.

Saludos.-

---

### Post by gefarion on 2008-06-17
Probe absolutamente todos los clientes de msn y no hay caso, reinstale y no anda. Desde el live cd tampoco. La verdad q me esta volviendo loco -.-

Alguna idea?

---

### Post by faktorqm on 2008-06-17
Proba de decirle al cliente que uses que se conecte por http, a ver que pasa. Debes tener cerrado el puerto 1863 para que no se te conecte o algo por el estilo. Salu2!

---

### Post by gefarion on 2008-06-17
Ya lo hice, pero sigue sin funcionar, al parecer segun lo que estuve viendo el problema es cuando descarga la lista de contactos.

---

### Post by Hei Ku on 2008-06-17
si arrancas el kopete desde la consola y tratas de conectar al MSN, te tira algun error en la consola? Eso podria darnos una pista.

---

### Post by gefarion on 2008-06-17
El kopete no me dice nada por consola, simplemente se queda conectando, logra bajar la lista de contactos, o al menos eso parece, pero aparecen todos desconectados. Y luego de unos minutos me tira error de contraseña.
Probe con el emesene y obtuve esta salida:

>>> VER 1 MSNP13 CVR0
<<< VER 1 MSNP13 CVR0
>>> CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0.0792 msmsgs [email]gefarion@gmail.com[/email]
<<< CVR 2 8.5.1302 8.5.1302 8.1.0178 [http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe](http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe) [http://get.live.com/es](http://get.live.com/es)
>>> USR 3 TWN I [email]gefarion@gmail.com[/email]
<<< XFR 3 NS 207.46.110.44:1863 U D
>>> VER 1 MSNP13 CVR0
<<< VER 1 MSNP13 CVR0
>>> CVR 2 0x0c0a winnt 5.1 i386 MSNMSGR 8.0.0792 msmsgs [email]gefarion@gmail.com[/email]
<<< CVR 2 8.5.1302 8.5.1302 8.1.0178 [http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe](http://msgr.dlservice.microsoft.com/download/5/6/4/5646481F-33EF-4B08-AF00-4904F7677B89/ES/Install_WLMessenger.exe) [http://get.live.com/es](http://get.live.com/es)
>>> USR 3 TWN I [email]gefarion@gmail.com[/email]
<<< GCF 0 6501
<<< USR 3 TWN S ct=1213756275,rver=5.0.3270.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
PASSPORT begin
200 OK
>>> USR 4 TWN S t=92JSPySXaCjUY4F8oGBKw1WkGufbJu36gMeftJQxjRhg4thI!piQRoK92JlVhrikBuQVA*BPKuPQED3fV7jf2MWLppFeziqK300qoPlgV96ood3uBwosbDgdOL7PSXOeUGkD4fBOUf4CY$&p=9q7X928OZBlUj8XthPZA!fzJ!dewdQJpah!91Bgr3S2WttsUQJ*opkeHPaYyvMMOnJwgID*xay1bFCAHQy4EnfiWOhW580z*TySyyhgWrtYtUFI1yLCtDdHlD4L!pNAIMbz2RueymTWPu5K0U8r*Z9tpqqrNOdxdXRN*EGiJcjDzs$
<<<
login error ;_;
Server error

Alguna idea?

PD: desde windows con el pidgin me conecto sin problemas :S.

---

### Post by gefarion on 2008-06-17
Buenas noticias, ya encontre cual es el problema, probe cambiar a windows la maquina que comparte internet y todo funciona sin problemas, asi que el problema esta en la configuracion del Kubuntu que uso para compartir internet.
Aca dejo los archivos de configuracion de la Red(ppp0 es mi conexion de speedy):

-----------------------------------------------------------------
interfaces:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


auto eth0

------------------------------------------------------------------


dhcp.conf:

ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.10;
  option domain-name-servers 200.51.211.7; <-- dns de speedy
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

---------------------------------------------------------------
este script uso para compartir internet:

iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward


---------------------------------------------------------------

Tambien estuve notando que a otro programas como por ej Ares le cuesta mucho trabajo conectarse.
Espero que con esta info alcance. Cualquier otra que necesiten solo pidan.

Saludos.

---

### Post by gefarion on 2008-06-19
Al final lo solucione instalando firestarter, pero me gustaria saber de alguien que sepa, cual era el problema en mi configuracion anterior.

Saludos.

---

### Post by nthcode on 2008-06-21
Hey, I've got the same symptom here and got it fixed.

Somehow the MRU for my connection was wrongly at 14xx,
I fixed it before by setting it 1500 (PPPoA) but forgot the save the setting, as the router rebooted itself, it reverted to the old value. 
And its fine now by setting it back to 1500 again.

Not sure if it's the same problem, hope that helps.

---

### Post by faktorqm on 2008-06-21
En este foro hablamos en castellano, tu respuesta no nos sirve de absolutamente nada.

---

### Post by madelaki on 2008-06-21
La tuya tampoco, faktorqm. No sabra español, pero quiso ayudar. Por que tanta bronca? Si no fuera por los foros y los blogs en ingles no tendriamos donde buscar soluciones para los problemas de Ubuntu.

---

### Post by faktorqm on 2008-06-21
Por que no todos saben inglés, y no todos tuvieron las mismas oportunidades en la vida, y si están acá, ¿para qué necesitan saber inglés si hablamos en castellano? (y aparte el problema ya está resuelto...) Aparte apuesto a que pocos acá saben que significa MTU.... así que si encima está en inglés (para aquel que no sepa) lo único que hace es tornar inservible la respuesta.

En Argentina las compañias no usan PPPoA, usan PPPoE, por lo tanto el MTU debe estar en 1492, no en 1500, aunque muchos routers lo soporten (y hasta algunos lo cambian automaticamente), otros no.

edito el post por uno menos agresivo: LA-LA... LAAA...

---


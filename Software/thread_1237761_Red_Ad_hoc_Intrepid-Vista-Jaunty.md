---
title: "Red Ad hoc Intrepid-Vista-Jaunty"
date: 2009-08-11
forum: Software
---

### Post by asterix77 on 2009-08-11
Estimados:

Tengo tres pc. Un notebok con intrepid, un pc con Vista, y otro PC con Jaunty. Al Notebook con Intrepid le instale el WICD con el cual es fácil configurar una red ad hoc la cual es detectada por Vista (pero no puede ingresar). Con Vista igual es fácil configurar una red Ad hoc, que es detectada por intrepid, pero tampoco puedo ingresar.
Con Jaunty no he podido crear una red Ad Hoc (con Network-Manager), ni he podido detectar las creadas por los otros dos PC.
Menciono además que tanto en Jaunty como Intrepid a través del terminal, no he podido crear una red Ad hoc.
Les comento además que antes cada Pc lo conectaba con cable cruzado, por lo que configuré samba y NFS. El problema de esto es que para usar otro pc, tenía que desconectar uno y conectar el otro.

Quiero aprovechar mis tarjetas de redes (que si soportan modo Ad Hoc), para poder conectar en lo posible los tres PC, y para lo cual les solicito su ayuda.

Saludos y se agradecen los comentarios.

---

### Post by asterix77 on 2009-08-12
¿Alguien quien me pueda ayudar con esto?

---

### Post by Carlos C on 2009-08-13
Puede ser un problema de permisos. Primero verifiquemos que tienes configurado el modo ad hoc en tu ubuntu, escribe en el terminal:
```
iwconfig
```
y veamos lo que te sale.
Saludos.

---

### Post by asterix77 on 2009-08-13
Primero que nada gracias por responder Carlos.

Bueno, al crear una red ad-hoc en mi pc con vista, con intrepid en mi notebook lo detecto (essid=casa)

# sudo iwlist wlan0 scanning

Cell 04 - Address: 7A:27:8E:87:3E:E0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000004308f170
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 000463617361
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

#sudo ifconfig wlan0 down
#sudo iwconfig wlan0 mode ad-hoc essid casa channel 10 key s:QWErt
#sudo ifconfig wlan0 up
#iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"casa"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 7A:27:8E:87:3E:E0   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Se supone que en lugares-red (intrepid) debiera aparecer el pc con vista ¿o no?.


Saludos

---

### Post by Carlos C on 2009-08-14
Si no lo ves puedes intentar ingresando directamente el ip del pc con vista.

---

### Post by asterix77 on 2009-08-14
Estimado:

Intenté reconfigurar mis tarjetas inalámbricas, colocandoles una ip a ambos equipos más una máscara de subred. Me acordé que cuando los conectaba a través de cable cruzado, configuré iptables con un márgen de rangos de ip, así es que les asigné ip dentro de ese rango. Desde intrepid no pude ver a vista dentro de lugares-red, pero ejecutando en el navegador lo que me recomendastes, pude conectarlos. Aunque desde intrepid al querer copiar archivos a vista, o desde vista a intrepid (desde intrepid), se me desconecta y se me cae la conexión. Eso no me ocurre si lo hago desde Vista a Intrepid 

¿Alguna idea del porque puede ocurrir esto?.


Otra cosa, la tasa de transferencia máxima que he logrado, es de 1,2 megas por seg. ¿Es eso normal?.


Saludos

---

### Post by Carlos C on 2009-08-16
Bueno, no soy experto en velocidad de redes, pero en mi caso, cuando copio archivos en mi red la tasa de transferencia llega a una velocidad parecida a la que consigues tú. Cuando pierdes la conexión, ¿esto ocurre en cuanto intentas copiar un archivo o alcanzas a copiar parte de él? Sería importante ver si tienes los permisos adecuados.

---

### Post by asterix77 on 2009-08-17
Hola Carlos.

Te comento que cuando trato de copiar un archivo de vista desde intrepid, generalmente se interrumpe la trasmisión de datos (pero no siempre se desconecta) , esto genera que solo se copie parte del archivo. En otros casos (los menos), se corta la conexión y hay que reconectar en forma manual.

Solo me ocurre desde inrepid, no desde vista. Tengo la sensación de que vista es "más paciente" en esperar que se reinicie la transmisión de datos, ya que al observar los distintos monitores de redes (el de intrepid y el de vista), el flujo de transmisión de los datos posee las mismas caracteristicas tanto si lo hago desde intrepid como desde vista.

Con respecto al tema de los permisos que comentas ¿como se puede verificar eso?.


Saludos

---


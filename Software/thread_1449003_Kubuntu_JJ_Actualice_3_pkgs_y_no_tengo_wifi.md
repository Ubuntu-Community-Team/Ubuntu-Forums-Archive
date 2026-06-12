---
title: "Kubuntu JJ: Actualice 3 pkgs y no tengo wifi"
date: 2010-04-07
forum: Software
---

### Post by sergiom99 on 2010-04-07
Hola gente,
esta mañana actualice estos 3 paquetes, porque me lo propuso, y al reiniciar (por otro tema) me quede sin wireless. 
> 
[ACTUALIZA] libkadm55 1.6.dfsg.4~beta1-5ubuntu2.2 -> 1.6.dfsg.4~beta1-5ubuntu2.3
[ACTUALIZA] libkrb5-dev 1.6.dfsg.4~beta1-5ubuntu2.2 -> 1.6.dfsg.4~beta1-5ubuntu2.3
[ACTUALIZA] libkrb53 1.6.dfsg.4~beta1-5ubuntu2.2 -> 1.6.dfsg.4~beta1-5ubuntu2.3


Conecta a la red, pero no puedo ni navegar ni siquiera entrar a la pagina de administracion del router. Si la conecto por cable anda todo barbaro.
Busque pero todavia no hay nada reportado.

Alguien tiene alguna idea al respecto? Puede estar relacionado?

se podria hacer un rollback a la version anterior? Como?

Gracias!
-Sergio

PS: Aclaro que la red tiene WPA2 como seguridad, y desde otra laptop funciona sin problemas.

---

### Post by sergiom99 on 2010-04-07
Update: Ahora estoy conectado, pero anda entre mal y pesimo.
Probando la misma laptop con Win XP veo que anda perfecto, asi que descarto una falla de la placa wireless.

Haciendo ping al router pierde el 60% de los paquetes, lo cual no deberia.
Estoy al 100% de señal porque para probar y usar el cable estoy al lado.

---

### Post by guillermolisi on 2010-04-07
Esos paquetes son de Kerberos 5. Estas usando Kerberos para la conexion ? Seguro que no se actualizo algo mas ?

Edit: Por que hacen referencia a una version beta ?: libkadm55 1.6.dfsg.4~[COLOR=Blue]beta1[/COLOR]-5ubuntu2.2 -> 1.6.dfsg.4~[COLOR=Blue]beta1[/COLOR]-5ubuntu2.3

---

### Post by sergiom99 on 2010-04-07
> **guillermolisi said:**
> Esos paquetes son de Kerberos 5. Estas usando Kerberos para la conexion ? Seguro que no se actualizo algo mas ?
Son de Kerberos, pero no lo uso para conectarme. O no deliberadamente, tal vez los use el WPA2. Uso Wicd para la conexion.
Las lineas que pegue las saque del log de aptitude. La actualizacion anterior solo habia hecho update del tzdata.

> **guillermolisi said:**
> Edit: Por que hacen referencia a una version beta ?: libkadm55 1.6.dfsg.4~[COLOR=Blue]beta1[/COLOR]-5ubuntu2.2 -> 1.6.dfsg.4~[COLOR=Blue]beta1[/COLOR]-5ubuntu2.3

No tengo idea, asi los bajo apt-get.

Gracias Guille!

---

### Post by guillermolisi on 2010-04-07
Es JJ 32 o 64 bits ?
Que te devuelven: 
```
sudo lshw -C network
sudo iwlist scan
iwconfig
rfkill list
lsmod
```

---

### Post by sergiom99 on 2010-04-07
Guille, te pego la data

```
sergio@kubuntu:~$ sudo lshw -C network
  *-network                           
       description: Ethernet interface
       product: MCP67 Ethernet        
       vendor: nVidia Corporation     
       physical id: a                 
       bus info: pci@0000:00:0a.0     
       logical name: eth0             
       version: a2                    
       serial: 00:1b:24:d4:e5:9c      
       size: 100MB/s                  
       capacity: 100MB/s              
       width: 32 bits                 
       clock: 66MHz                   
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:c8:e0:ae
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:79:67:c8:0e:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```
sergio@kubuntu:~$ sudo iwlist scan                                                                                                                        
lo        Interface doesn't support scanning.                                                                                                             

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:37:48:E4
                    ESSID:"CNSF2"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-90 dBm
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259C3748E41021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303010420001301054000800060050F20400011011000757525435344732100800020084103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1A:70:5E:AE:A7
                    **ESSID:"husky01"** {la mia}
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-21 dBm  Noise level:-81 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
          Link Quality:5  Signal level:235  Noise level:174
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.


```
```
$ rfkill list
bash: rfkill: orden no encontrada

```
```

$ lsmod           
Module                  Size  Used by
michael_mic            10496  2      
arc4                    9856  2      
ecb                    10752  2      
binfmt_misc            16776  1      
ppdev                  15620  0      
bridge                 56212  0      
stp                    10500  1 bridge
bnep                   20224  2       
vboxnetadp             15168  0       
vboxnetflt             22376  0       
vboxdrv               189064  2 vboxnetadp,vboxnetflt
lirc_sir               23556  0                      
lirc_dev               19892  1 lirc_sir             
input_polldev          11912  0                      
dm_crypt               20996  0                      
joydev                 18368  0                      
lp                     17156  0                      
parport                42220  2 ppdev,lp             
snd_hda_intel         436148  2                      
snd_pcm_oss            46336  0                      
snd_mixer_oss          22656  1 snd_pcm_oss          
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0                          
snd_seq_oss            37760  0                          
snd_seq_midi           14336  0                          
snd_rawmidi            29696  1 snd_seq_midi             
uvcvideo               63368  0                          
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211_crypt_tkip    16896  0                                                         
compat_ioctl32          9344  1 uvcvideo                                                 
k8temp                 12416  0                                                          
snd_timer              29704  2 snd_pcm,snd_seq                                          
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0                                                           
pcspkr                 10496  0                                                           
nvidia               7233756  32                                                          
ricoh_mmc              11904  0                                                           
sdhci_pci              15232  0                                                           
sdhci                  23940  1 sdhci_pci
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13444  0
wl                   1281364  0
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  1 nvidia
video                  25872  5
output                 11008  1 video
forcedeth              61712  0
ohci1394               38576  0
ieee1394               94660  1 ohci1394
usbhid                 42336  0
raid10                 30336  0
raid456               134928  0
async_xor              11392  1 raid456
async_memcpy           10112  1 raid456
async_tx               15184  3 raid456,async_xor,async_memcpy
xor                    24072  2 raid456,async_xor
raid1                  29952  0
raid0                  15488  0
multipath              15104  0
linear                 13312  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```


Es 32bits.

Tengo fuertes sospechas de que sea la placa.
Ya me dijeron los amigos de HP que mañana a la mañana la revisan y si hace falta me la cambian.

En XP lo que esta haciendo ahora es detectar todas las redes, pero no se conecta. Otra laptop se conecta al router como si nada.

En Kubuntu, las detecta dice que esta conectado, pero nada de nada.
Obviamente ahora estoy con el cable.

---

### Post by guillermolisi on 2010-04-08
La verdad que no veo nada raro en la info que aportaste. El driver wl esta cargado y asociado a la placa, el scan funciona y la placa esta bien reconocida y administrada (por el network manager que estes usando). No esta deshabilitada (esta encendida).

Si en Windows tampoco funciona, intentaria descartar que sea problema de hardware. Esos paquetes que actualizaste nada tienen que ver con WiFi (por lo menos hasta donde se). No seria el primer caso que conozco de una HP con hardware cocinado por alta temperatura.

---

### Post by sergiom99 on 2010-04-08
Gracias Guille por tus respuestas.
Para recapitular:
1. Estaba todo OK y justo se dio la actualizacion que baje 3 paquetes de kerberos. Al rato reinicio por otro motivo y deje de conectarme al wlan.
2. Reviso la configuracion, pruebo con el cable y funciona todo.
3. Pruebo con XP en la misma laptop y OK. Pruebo desde otra laptop y la wlan esta OK.
4. Sigo buscando y probando en Ubuntu y nada.
5. Pruebo de nuevo en XP y dejo de conectarse, pero siempre hasta ahora detecta las redes.
6. La llevo a los amigos de HP, cambiamos la placa y sale funcionando de una en XP.
7. Lo miro un poco mas en Ubuntu y el Wicd no detectaba redes porque decia que la wlan era eth1 y ahora se llama eth2. Corregido esto quedo todo perfecto.

Lo raro de todo esto es que se fue "degradando" de a poco, o sea que primero dejo de andar en Ubuntu pero andaba en XP, despues dejo de andar en XP pero nunca dejo de detectar las redes wireless, solo dejo de conectarse.
Justo coincidio con el update de esos paquetes que me hicieron sospechar, sumado que al probar la 1ra vez en Window$ funciono OK.

Asi que fallo la placa, que fue prontamente reemplazada y en 24hs solucione toda la historia.
(Aclaro que la laptop tiene unos dos años y no levanta temperatura excesiva. Nunca por sobre los 60ºC, segun lmsensors, y esto cuando miro una peli o un video)

Saludos a todos!
-Sergio

---

### Post by guillermolisi on 2010-04-08
Los casos que conozco con notebooks HP tambien comenzaron con conexion erratica y esa degradacion hasta que dejo de funcionar la antena. En los casos en que no la cambiaron, con el tiempo dejaron de funcionar otros componentes, video por ejemplo. La gran mayoria, por no decir todos, usaba WinXP.

---

### Post by sergiom99 on 2010-04-08
me aconsejas que no lo de por cerrado y haga revisar/cambiar algo mas?

---

### Post by guillermolisi on 2010-04-08
> **sergiom99 said:**
> me aconsejas que no lo de por cerrado y haga revisar/cambiar algo mas?
Es que no se me ocurre como sustentar el pedido de cambio ante el servicio tecnico de HP ya que ellos actuan si y solo si la falla es comprobable.

Si abrieron un ticket por tu tema lo cierran automaticamente si no tuvieron mas comentarios del usuario sobre la maquina despues de dos o tres dias.

Se que hay modelos de HP, como por ejemplo las tablets con AMD y nVidia (mira que casualidad), que tienen problemas de diseño y eso hace que la disipacion interna de calor termine perjudicando la motherboard. Se de varios casos, uno muy cercano, que termino "arreglando" el problema colocandole una moneda de niquel de $AR 0.25 entre la GPU nVidia y el disipador (que es solidario con el de la CPU). Cuando el disipador se enfria no hace contacto con la superficie de la GPU y esta se recalienta y apaga la maquina. Esto lo termino haciendo despues de haber cambiado tres veces la motherboard para llegar siempre a la misma situacion. Cosa de locos pero es asi.

Otros modelos economicos de notebooks HP se cocinaban tambien empezando indefectiblemente por la antena inalambrica. Cuando la llevaron al servicio tecnico se la recibieron como si fuera "cosa de todos los dias", le cambiaron la motherboard al toque y sin chistar.

---

### Post by sergiom99 on 2010-04-08
En realidad, no tengo ticket ni nada de soporte. (Sh! que no se entere Don HP)
Conozco a la gente del CAS, asi que entre y sali con la placa cambiada.
(Todavia no investigue demasiado, pero creo que la BCM4311 que me dieron soporta backtrack y todo!! :guitar:)

Problemas de temp no tengo y como te comentaba, hace casi 2.5 años que la vengo usando. No es de las economicas, se que las Compaq si han tenido bastantes problemas.

Asi que afortunadamente creo que por el momento he zafado.

---

### Post by guillermolisi on 2010-04-08
> **sergiom99 said:**
> 
Conozco a la gente del CAS, asi que entre y sali con la placa cambiada.

Tomo en cuenta el comentario por si algun dia tengo que hacerle algo a mi HP :)

---


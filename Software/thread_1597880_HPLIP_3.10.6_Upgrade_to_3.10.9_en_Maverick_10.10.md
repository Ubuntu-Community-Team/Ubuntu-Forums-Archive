---
title: "HPLIP 3.10.6 Upgrade to 3.10.9 en Maverick 10.10"
date: 2010-10-15
forum: Software
---

### Post by RafaelG on 2010-10-15
Estimados,

Tengo problemas con el HPLIP  con impresora HP Deskjet Ink Advantange K109a-z, con la nueva version maverick 10.10 no me permite imprimir, indagando un poco la version que tengo actualmente es la hplip 3.10.6 y actualmente se encuentra la version hplip 3.10.9 pero al momento de realizar el upgrade me indica lo siguiente:
> 
xxxxxxxxxxxxxxxxx:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          3.10.6-1ubuntu HP Linux Printing and Imaging System (HPLIP)
xxxxxxxxxxxxxxxxxx:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.10.6)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Bus: open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=usb, search=(None), desc=0)
Searching... (bus=usb, search=(None), desc=0)
[COLOR=DarkOrchid]**/warning: No PPD found for model deskjet_ink_advant_k109a-z using new algorithm. Trying old algorithm...**[/COLOR]
Bus: open: Can not get ibus-daemon's address.
Launchpad Bug Link: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/661533](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/661533)

---

### Post by RafaelG on 2010-10-16
Estimados,

Otro antecedente que puedo aportar del problema es el siguiente:

> E [16/Oct/2010:08:42:36 -0300] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "Deskjet_Ink_Advant_K109a-z" not available: No such file or directory 

Segun lo visto hasta el momento no hay una version oficial de **HPLIP 3.10.6 y 3.10.9** para la version Maverick 10.10, bueno por el momento la alternativa para no quedarme sin impresora fue crear desde Virtualbox una version 10.04 LTS para poder imprimir por mientras por lo que veo mi problema no se resolvera hasta que liberen un HPLIP para Maverick 10.10

Se agradece cualquier alternativa que se pueda proporcionar algun ubuntero de la comunidad

Saludos!

---

### Post by RafaelG on 2010-10-20
Estimados Colegas Ubunteros,

Para aquellos que quieran continuar el hilo del Post en Launchpad, ya que por el momento he recivido ayuda en Launchpad aunque sin tener exito para solucionar mi problema. 

Link de mi Bug en Lunchpad:
[https://bugs.launchpad.net/hplip/+bug/661533](https://bugs.launchpad.net/hplip/+bug/661533)

Se agradece ante mano cualquier ayuda con el incoveniente

Saludos!

---

### Post by RafaelG on 2010-11-09
La solucion viable que consegui fue utilizar la version hplip 3.10.6 con algunas modificaciones hasta que liberen la version hplip 3.10.9 para maverick, dejo link con la modificacion que hay que hacer en maverick.

[http://www.omgubuntu.co.uk/2010/11/fix-blank-photo-prints-problem-in-gimp/](http://www.omgubuntu.co.uk/2010/11/fix-blank-photo-prints-problem-in-gimp/)

Saludos!

---


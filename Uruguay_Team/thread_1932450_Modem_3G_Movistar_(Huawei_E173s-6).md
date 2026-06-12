---
title: "Modem 3G Movistar (Huawei E173s-6)"
date: 2012-02-27
forum: Uruguay Team
---

### Post by beuno on 2012-02-27
Vengo intentando hacer andar el Modem 3G de Movistar, pero no estoy teniendo suerte.
Pude llegar hasta el punto de que lo reconozca Network Manager, pero despues no me conecta.
Estoy usando 12.04.

Para aquellos que tengan el mismo modem, estas son las instrucciones para que lo reconozca Network Manager:

Primero, fijate si tenes el mismo model:

```
beuno@beuno-thinkpad:~$ lsusb | grep Huawei
Bus 001 Device 014: ID 12d1:1c23 Huawei Technologies Co., Ltd.
```

(puede terminar en 1c23 o 1c24, los modems Huawei a veces tienen 2 Buses)

Si es el mismo creemos un archivo nuevo:
```
sudo gedit /etc/usb_modeswitch.d/12d1:1c24
```

Ahi pegale esto:
```
#############################
# Huawei E173

DefaultVendor= 0x12d1
DefaultProduct=0x1c24

TargetVendor= 0x12d1
TargetProduct= 0x1c23


#MessageContent="5553424312345678000000000000001106 0000000000000000000000000000"
MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20
```

Ahora:
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```

Buscamos la seccion donde ya diga E173, y agregamos abajo:
```
# Huawei E173 (product 1c24)
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c24", RUN+="usb_modeswitch '%b/%k'"
```

Y ahora solo hay que ejecutar:
```
sudo modprobe usbserial vendor=0x12d1 product=0x1c23
```

Esperar 30 segundos y deberia aparecer en Network Manager.


Al final de todo eso, a mi no me conecta, pero parece intentarlo.

En el log (/var/log/syslog) veo esto:
<warn> (ttyUSB0): failed to look up interface index

Parece relacionado a este bug: [https://bugzilla.redhat.com/show_bug.cgi?id=597296](https://bugzilla.redhat.com/show_bug.cgi?id=597296)

Bueno, hasta aca llegue, si alguien sabe algo mas, bienvenido sea  :)

---

### Post by maniat1k on 2012-04-05
Yo tengo un modem alcatel y lo pude hacer andar por que seguí unos pasos que leí en el extinto foro uruguayo de Ubuntu: si los encuentro los publico quizás hallan puntos en los que te puedas prender a ver si sacas alguna conclusión.

Saludos

---


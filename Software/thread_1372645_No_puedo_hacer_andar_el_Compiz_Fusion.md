---
title: "No puedo hacer andar el Compiz Fusion"
date: 2010-01-04
forum: Software
---

### Post by Piero71 on 2010-01-04
Me pasó con dos máquinas distintas, pero con la misma placa de video: nVidia geForce MX4000

Al principio tuve problemas, ya que luego de instalada la placa, me quedaron las ventanas sin borde ni título. Lo solucioné agregando "metacity --replace" al inicio.

Pero ahora, tengo el compiz instalado y configurado a mi gusto, pero no hace nada. Googlé por todos lados y no encuentro como arreglarlo...
Si voy a Sistema/Preferencias/apariencia/Efectos visuales y elijo "Extra" me aparece una vetana diciendo "buscando controladores disponibles". Luego de eso desaparecen otra vez los bordes y tìtulos de las ventanas y me pregunta si quiero mantener la configuración. Obvio, le digo que no para recuperar el control de las ventanas. Si acepto la configuración, me quedan las ventanas sin bordes, botones, barra de tìtulo, etc. Al reiniciar la maquina, vuelve todo a la normalidad, "Efectos Visuales" sigue como "Ninguno".

¿qué estoy haciendo mal? ¿La placa de video es muy chica para el compiz?

saludos!!

---

### Post by leonardomdq on 2010-01-04
Hola Piero, no creo que la MX4000 se aguante compiz-fusion, sino me equivoco tiene 128 MB de RAM, cierto? 
Probaste si tenes aceleracion grafica?

Abri una terminal y tira estos dos comandos...
```
$ glxinfo | grep direct

``````
$ glxgears

```Saludos
Leonardo

---

### Post by Piero71 on 2010-01-05
si, leonard, tengo aceleración gráfica...

---


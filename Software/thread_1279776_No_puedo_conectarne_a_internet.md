---
title: "No puedo conectarne a internet"
date: 2009-10-01
forum: Software
---

### Post by emi_cba on 2009-10-01
Hola que tal!! escribo para comentar mi situación y pedir ayuda si es posible. Tengo una notebook Bangho en la cual en una partición tengo Win Vista y en la otra Ubuntu 9.04 amd64. A la vez tengo una PC de escritorio con WinXP la cual esta conectada a internet mediante ADSL con la amburguesa HUAWEI SmartAX MT810. A esta PC de escritorio la conecto punto a punto con un cable UTP a la notebook y en Windows Vista tengo internet, mientras que en Ubuntu nisiquiera pude hacerle un ping. En Vista no le toque nada, le deje las configuraciones de red como vino por defecto. En Ubuntu tube que renegar para poder instalarlo y configurar la placa de video debido a que tengo un chipset SIS M672 + SIS 968. 
Si alguien podría darme una mano les agradeceria. Saludos

---

### Post by emiliano_raso on 2009-10-01
Perdon por mi ignorancia en cuestion de nombres pero la onda es que conectás la notebook con un cable de red que sale de un modem?

Si es asi probá
```
sudo pppoeconf
```

---

### Post by staar on 2009-10-01
lo que yo entendí es que la pc con Ventanas XP, a la que se conecta con un cable cruzado, le comparte el internet a la notebook, habría que ver de cual modo esta realizando esto...

para que te podamos ayudar mejor, y hacernos una idea de como es tu red, en los dos Ventanas, andá a Ejecutar, corré *cmd* una vez abierta la "consola" de Ventanas, corré el comando ```
ipconfig /all
``` copiá las salidas y pegalas en un mensaje acá...

en teoría, y si no hay nada raro, con poner en ubuntu las mismas configuraciones que en el V*sta, tendría que salir andando...

saludos

---

### Post by emi_cba on 2009-10-01
Mi forma de conectarme es como dijo staar. En win Vista estaba en DHCP y le puse a ubuntu también con DHCP y no pasa nada, nisiquiera un ping al gateway o DNS. Yo tengo una placa sis190, en una de esas es el problema. Para mi tengo que configurar o instalar algo o nose que

---


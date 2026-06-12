---
title: "Logmein"
date: 2009-10-04
forum: Software
---

### Post by capcabgue on 2009-10-04
Hola:

Tengo un notebook dell Inspiron 1525 con Ubuntu 9.04 de 64 bits, en mi casa tengo un PC con Ubuntu 8.04. ambos computadores (más el de mi sra que es guin2) salen a Internet mediante un Router dlink di-524 y servicio de Internet de teléfonica con IP dinámica, estos 3 PCS más la impresora forman mi LAN de la casa.
En ocasiones, cuando estoy en la pega o en cualquier parte Mac Donalds, copec, etc. necesito conectarme remotamente a los pcs de la casa, mediante internet. Lo cual no he podido hacer ya que están todos los pcs están con las IP de la red local distribuidas por el router.
Mi punto es que despues de mucho googlear, encontré LOGmein que hacía lo que yo quería, pero desgraciadamente es para Guin2. Alguien sabe de algún SW similar o que haga lo mismo en Ubuntu o como se puede instalar LogMein en la versión de 64 bit (encontre un script para 8.04 de 32).
Sé por lo que he leído que una solución es crear una VPN entre ambas redes, pero desgraciadamente no tengo ni idea de como hacer una, si tienen muuuuuucha paciencia y me dan un manual algo asi como "VPN for dummies at Ubuntu", por su puesto en español, lo puedo intentar, espero no molestar demasiado con mis preguntas, supongo que con el equipamiento que tengo puedo crearlo.
Ahora si alguien sabe de una forma sencilla para conectarme (me dijeron que medianto no-ip), les pido consejo.

Bueno gracias y espero haber sido claro en lo que quiero (conectar 2 pcs mediante escritorio remoto y ambos pcs están en LANs distintas).

Gracias

---

### Post by moreback on 2009-10-05
No lo he probado nunca, pero el _Hamachi_ se usa para lo mismo y hay una versión para Linux. Con un poco de suerte (google mediante) deberías encontrar algún tutorial en los internets.

Saludos.

---

### Post by maxmoraga on 2009-10-06
Asi es, usar hamachi te permite crear una VPN  de manera sencilla yo siempre lo uso, asi que aqui van los pasos para instalarlo:

primero. habilitar el kernel.
```
sudo modprobe tun
```

luego edita el archivo /etc/modules y agrega tun al final de este. el archivo debiera quedar algo como lo siguiente:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
 
lp
rtc
tun
```

ahora debemos ver que el kernel se halla avilitado correctamente:
```
ls /dev/net/tun
```

ahora descargamos e instalamos hamachi:
```
wget http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz

tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-x/
sudo make install
sudo tuncfg

```

iniciar autoconfiguracion de hamachi:
```
sudo hamachi-init
```

y debieras ver algo como lo siguiente:
```
Initializing Hamachi configuration (/home/user/.hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making (/home/user/.hamachi directory .. ok
  saving (/home/user/.hamachi/client.pub .. ok
  saving (/home/user/.hamachi/client.pri .. ok
  saving (/home/user/.hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.
```

ahora para iniciar hamachi:
```
hamachi start
```

crearce un nick:
```
sudo hamachi set-nick "tuNick"
```

ahora para logiarse y entrar a una red vpn existente o crear una nueva:
```
#Login
sudo hamachi login

#unirse a una red
sudo hamachi join REDNOMBRE PASSWORD
#O crear una nueva red
sudo hamachi create REDNOMBRE PASSWORD

#activar la coneccion a la red
sudo hamachi go-online REDNOMBRE
```


aunque tambien puedes usar un cliente grafico para hamachi:
puedes descargarlo en [http://hamachi-gui.sourceforge.net/index.html]("http://hamachi-gui.sourceforge.net/index.html")

y lo instalas con:
```
sudo dpkg -i  "ARCHIVODESCARGADO"
```

y para ejecutarlo:
```
sudo hamachi-gui
```

Saludos y espero te sea de ayuda.:)

---

### Post by capcabgue on 2009-10-06
Gracias:

Ya instalé hamachi (ayer) todo OK, es decir me sale lo mismo que me dices que es lo que indica la página oficial de hamachi, en su instalación.
Sin embargo, cuando apago el notebook y trato de iniciar hamachi nuevamente me arroja un error, que desconozco:
06 08:14:24.257 [   0] [14744] tap: connect() failed 2 (No such file or directory).
Para poder lanzar nuevamente hamachi, tengo que hacer todos los pasos de nuevo, es una tontera hacerlo, pero así cuando hago "hamachi start" no me arroja  error.

Alguien sabe que es lo que está pasando? o Cómo solucionarlo?

Gracias

---

### Post by capcabgue on 2009-10-06
Gracias por el Tip, ya logré instalar hamachi y crear la vpn para conectar ambos pc, lo puedo reiniciar cada vez que quiero.
Lo único que hice fue seguir las indicaciones que dio maxmoraga, con la única excepción que descomprimí e instalé hamachi en /usr/src/hamachi...luego todos los pasos por igual.
Si a alguien le interesa lo hice siguiendo este tuto también (que es casi lo mismo que dice aqui en el foro).
[http://forums.hamachi.cc/viewtopic.php?t=3523](http://forums.hamachi.cc/viewtopic.php?t=3523)
Gracias

---


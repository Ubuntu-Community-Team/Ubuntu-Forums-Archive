---
title: "abrir puertos"
date: 2008-09-02
forum: Software
---

### Post by boniato on 2008-09-02
Hola

Quiero abrir el puerto 23 para poder usar telnet, y no puedo
Primero hice lo que dice faktorqm en este topic
[http://ubuntuforums.org/showthread.php?t=577416&page=2](http://ubuntuforums.org/showthread.php?t=577416&page=2)
Después como tengo adsl y router belkin, intente configurar el router para abrir el puerto 23,pero sin éxito. Acá dejo una imagen del intento
[http://img141.imageshack.us/img141/5613/puertotelnbq7.jpg](http://img141.imageshack.us/img141/5613/puertotelnbq7.jpg)

la cuestión es que si pongo 
```
nmap 192.168.2.2 -p 23
```
siempre da
```

PORT   STATE  SERVICE
23/tcp closed telnet
```

ademas probando usar telnet en mi propia maquina tampoco se conecta```

$telnet 192.168.2.2
Trying 192.168.2.2...
telnet: Unable to connect to remote host: Connection refused
```

Por cualquier cosa gracias
Saludos

---

### Post by Mister X on 2008-09-02
Tenes corriendo un servidor telnet en la maquina destino?

Podes tener 2 problemas: o que haya un firewall que esté filtrando el puerto 23, en este caso sí se aplica el concepto de "abrir" el puerto; o bien no hay ningun servicio escuchando ese puerto, en este caso un servidor telnet.

---

### Post by faktorqm on 2008-09-02
Claro, primero tenes que tener a alguien escuchando en el 23 de la otra pc, despues asegurarte que la otra pc no tenga el 23 bloqueado, no la tuya. cuando vos abris una conexion saliente, no se abre por tu 23, se abre por cualquier puerto. salu2!

---

### Post by boniato on 2008-09-02
Mil gracias ! Funciono era simplemente instalar el paquete telnetd
por mas detalles 
[http://laurel.datsi.fi.upm.es/~rpons/personal/trabajos/lpractico/node138.html](http://laurel.datsi.fi.upm.es/~rpons/personal/trabajos/lpractico/node138.html)

una cosa rara que paso, es que inmediatamente después de la instalación del paquete no andaba el servidor telnet, sino que tuve que reiniciar la pc para poder hacerlo andar. Ademas tampoco anda la sugerencia que dice en el link que cite: 
```
Es necesario reiniciar el demonio de red, lo haremos con:
/etc/init.d/inetd restart
```
probé eso y dice que no existe el archivo.
parece ser que la única forma de reiniciar el dominio red (que no se que diablos es) en ubuntu es reiniciando la computadora ...

saludos

---

### Post by sergiom99 on 2008-09-02
tambien podes hacer:
~$ sudo /etc/init.d/networking restart

---

### Post by boniato on 2008-09-02
```
~$ sudo /etc/init.d/networking restart 
```

no me funciono ese comando , o sea que si modifico el archivo inetd.conf (que esta en /etc), y después meto ese comando sigue el servidor telnet andando normalmente, en cambio si reinicio la computadora si se ven los efectos de modificar el archivo inetd.conf

gracias igual
saludos

---

### Post by sergiom99 on 2008-09-02
lo hiciste sin el '~$ '? o sea:
```
 sudo /etc/init.d/networking restart
```

---

### Post by Mister X on 2008-09-03
> **boniato said:**
> Mil gracias ! Funciono era simplemente instalar el paquete telnetd
por mas detalles 
[http://laurel.datsi.fi.upm.es/~rpons/personal/trabajos/lpractico/node138.html](http://laurel.datsi.fi.upm.es/~rpons/personal/trabajos/lpractico/node138.html)

una cosa rara que paso, es que inmediatamente después de la instalación del paquete no andaba el servidor telnet, sino que tuve que reiniciar la pc para poder hacerlo andar. Ademas tampoco anda la sugerencia que dice en el link que cite: 
```
Es necesario reiniciar el demonio de red, lo haremos con:
/etc/init.d/inetd restart
```
probé eso y dice que no existe el archivo.
parece ser que la única forma de reiniciar el dominio red (que no se que diablos es) en ubuntu es reiniciando la computadora ...

saludos

en Ubuntu creo que a partir de Hardy se reemplazo el inetd por xinetd, asi que el demonio que debias reiniciar era el xinetd

---


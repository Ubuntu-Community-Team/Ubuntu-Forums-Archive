---
title: "ñumessenger"
date: 2011-03-07
forum: Software
---

### Post by mama21mama on 2011-03-07
[[IMG]http://twitpic.com/show/thumb/4osyb5.png[/IMG]]("http://twitpic.com/4osyb5")[[IMG]http://twitpic.com/show/thumb/4762i2.png[/IMG]]("http://twitpic.com/4762i2")[[IMG]http://twitpic.com/show/thumb/4pchjm.png[/IMG]]("http://twitpic.com/4pchjm")[[IMG]http://twitpic.com/show/thumb/4pmuzh.png[/IMG]]("http://twitpic.com/4pmuzh")



Bueno un cliente mensajero para el geek... :guitar:
Esta en estado frieze
su ultima versión es 6.7.12

Los puertos que usa son ncat (multiusuario servidor cliente) 6699, cryptcat chat 6896,6898; cryptcat files 6868 y modo normal 6899
El modo normal la ip se pone seguida del port ejemplo: **90.164.84.111:6899**
para probar mensaje de bienvenida poner este host tal cual: **mamalibre.2.je**
Tiene un manual de usuario incluido.

En fin, es una [GUI]("http://es.wikipedia.org/wiki/Interfaz_gr%C3%A1fica_de_usuario") que usa el [cryptcat]("http://cryptcat.sourceforge.net/") con la tecnología [Twofish]("http://es.wikipedia.org/wiki/Twofish"), que por defecto es para 2 clientes o sea PC a PC. Tiene soporte de transferencia de archivos.

El modo multiusuario con [ncat]("http://nmap.org/ncat/") usa la tecnología [ssl]("http://es.wikipedia.org/wiki/Ssl") y establece un servidor con soporte hasta 100 clientes.

Y bueno... el modo normal usa la tecnología de SimpleHTTPServer de Python; terminando un poco 3 modos de chat con soporte de transferencia, 2 modos con encriptación segura ni [echelon]("http://es.wikipedia.org/wiki/ECHELON") puede con ellos.


[Video de pruebas]("http://www.youtube.com/watch?v=oko2hXV6iwg&hd=1") primeros pasos
[Video probando los dos modos]("http://www.youtube.com/watch?v=wqYkYmMcFIk&hd=1")
[mismo video otra fuente]("http://vimeo.com/20810892")

Download: [http://mamalibre.no-ip.org/numessenger_6.7.12_all_lubuntu.deb](http://mamalibre.no-ip.org/numessenger_6.7.12_all_lubuntu.deb)
MD5sum: 7d8d8cce2ff13810ed0832ac98ea8d88

source code via launchpad (bazaar)
> [https://launchpad.net/numessenger](https://launchpad.net/numessenger)source code via git
> [https://github.com/mama21mama/numessenger](https://github.com/mama21mama/numessenger) 

la dependencia que solo esta en Launchpad
GtkDialog -> [https://launchpad.net/ubuntu/karmic/i386/gtkdialog/2:0.7.20-4](https://launchpad.net/ubuntu/karmic/i386/gtkdialog/2:0.7.20-4)

---

### Post by mama21mama on 2011-05-04
Nueva versión de la gui mas segura para comunicación y transferencia de archivos.

un poco de historia:

la tecnología twofish desafió a todo aquel que pudiera romperla, hasta ahora la historia dice que no hubo un solo caso.
En ese momento daban mas de 10.000 dolares para quien la rompiera, cuando recién se termino de desarrollar y probar.

=D>=D>=D>=D>

---

### Post by Fitoschido on 2011-10-22
Buena aplicación, gracias!!

La única pega que le veo es que no se puede traducir a otros idiomas :|

Saludos

---

### Post by mama21mama on 2011-10-23
Hola,

corregí el post y puse la ultima versión.

También puse la dependencia ya que el repo de karmic no la allo mas. Ahora esta en launchpad.

Para mas adelante te debo las traducciones.

---


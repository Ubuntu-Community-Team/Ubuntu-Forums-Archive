---
title: "Migracion ERM + BBDD"
date: 2013-12-09
forum: Software
---

### Post by Bytesn+1 on 2013-12-09
Gente, 

buenas tardes, les consulto lo siguiente. Hace unos dias empece a realizar una migracion de SO a Ubuntu 13.10 de un Windows XP pero como todo tuve una serie de problemas con un ERM hecho en visual basic 6. La cosa es mas o menos asi: el sistema esta hecho en VB 6, se conecta con una base oracle 10.2. Con el cliente oracle para ubuntu no tuve drama, ya que al momento de hacer las pruebas llego bien a la base, pero el problema radica cuando quiero hacer que el programa conecte con la BBDD, el error es el siguiente "no se puede conectar con la base".

Esto es lo que instale para que funcione el cliente oracle. A lo mejor me esta faltando algo para hacer la conexion con el ERM.

oracle-instantclient-basic_10.2.0.3-2_i386.deb
oracle-instantclient-devel_10.2.0.3-2_i386.deb
oracle-instantclient-sqlplus_10.2.0.3-2_i386.deb

El ERM lo pude emular bien con wine, en ese caso no tuve drama.

Se que puede ser algo muy general la explicacion y en el caso de necesitar algo mas especifico no hay drama, pero si alguien alguna vez le paso siempre es bienvenida una sugerencia.

Saludos.

---

### Post by gmunioz on 2013-12-14
Si la aplicación Ms Windows se está ejecutando con Wine, se requiere que el cliente Oracle para Ms Windows esté instalado en Wine.

---


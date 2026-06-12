---
title: "Ubuntu RAID 1 + cuentas de usuario ¡Problema!"
date: 2009-09-20
forum: Software
---

### Post by matixslp on 2009-09-20
Amig@s,
Les cuento que aprovechando que renové la pc, y me quedó la anterior (ECS P4M800 Pro M + Celeron D 2.53 Ghz + 512 Ram) decidí armar un raid 1 con dos discos sata de 500Gb.
Antes de comprar los discos, me decidí a buscar como podía hacer el raid 1, pasé por freenas y me gusto, pero prefiero un SO completo donde voy a poder tener mas soporte, etc etc.
Bueno, para hacer pruevas elegi Ubuntu (mi pc principal como todas las de casa tienen win), instalé VMware y en ella un ubuntu, cree dos discos virtuales y crear el raid fué un flash ...
Ahora, les quería consultar sobre los permisos.
EN casa usamos las pc, mi novia, mis hermanas, mis viejos y yo.
Cree un grupo (flia) y un usuario con carpeta personal por cada persona que va a hacer backup en el raid.
El raid esta montado en /home/tute/raid
y ahi adentro las carpetas.
Comparti las carpetas y le asigne que cada owner pueda entrar y el resto nada ni entrar ni listar ni nada.
Cuando trato de entrar desde una compu de la red, veo las carpetas pero no puedo entrar me dice que no tengo permisos.:confused:
Que hice mal? por que no me puedo conectar a la carpeta, o no me pide nombre de usuario o contraseña?
Muchas gracias por la ayuda!!!

---

### Post by pablo.s on 2009-09-20
Preguntas:

1)Por qué decidiste montar
un servidor con Windows,
luego VMware, luego Ubuntu
virtualizado?
2) Que protocolo usás para la
compartición de las carrpetas?
¿Samba, supongo?
3) Que permisos le diste a cada
carpeta?

---

### Post by matixslp on 2009-09-21
> **pablo.s said:**
> Preguntas:

1)Por qué decidiste montar
un servidor con Windows,
luego VMware, luego Ubuntu
virtualizado?
2) Que protocolo usás para la
compartición de las carrpetas?
¿Samba, supongo?
3) Que permisos le diste a cada
carpeta?

Perdón pablo, quizas no me expresé bien.
En mi compu principal (donde tengo windows 7) instalé el VMware y ahi ubuntu.
La idea es virtualizar el server (solo para hacer pruevas y no comprar los dos discos rigidos de gusto) Quiero provar si yo lo puedo hacer, mantener y que realmente sea confiable - por eso hago pruevas preliminares en VMware antes de gastar 150 USD en discos rigidos-.

La estructura de directorios es la siguiente
EN mi cuenta de usuario (tute) tengo montado el raid
/home/tute/raid 
Adentro del raid hay 3 carpetas (las 3 carpetas estan compartidas)
/home/tute/raid/lili
/home/tute/raid/dani
/home/tute/raid/Nueva carpeta

Aca van las capturas de pantalla

[[IMG]http://img230.imageshack.us/img230/7743/usersr.th.png[/IMG]](http://img230.imageshack.us/i/usersr.png/)
[[IMG]http://img16.imageshack.us/img16/5633/tute.th.png[/IMG]](http://img16.imageshack.us/i/tute.png/)
[[IMG]http://img210.imageshack.us/img210/9344/raidsharing.th.png[/IMG]](http://img210.imageshack.us/i/raidsharing.png/)
[[IMG]http://img176.imageshack.us/img176/3692/raidpermissions.th.png[/IMG]](http://img176.imageshack.us/i/raidpermissions.png/)
[[IMG]http://img200.imageshack.us/img200/5194/nuevacarpeta.th.png[/IMG]](http://img200.imageshack.us/i/nuevacarpeta.png/)
[[IMG]http://img443.imageshack.us/img443/5194/nuevacarpeta.th.png[/IMG]](http://img443.imageshack.us/i/nuevacarpeta.png/)
[[IMG]http://img29.imageshack.us/img29/2897/lili.th.png[/IMG]](http://img29.imageshack.us/i/lili.png/)
[[IMG]http://img121.imageshack.us/img121/2391/dani.th.png[/IMG]](http://img121.imageshack.us/i/dani.png/)

---


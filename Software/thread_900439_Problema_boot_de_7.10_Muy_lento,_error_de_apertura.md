---
title: "Problema boot de 7.10 Muy lento, error de apertura de GDE"
date: 2008-08-25
forum: Software
---

### Post by sonhadorpr on 2008-08-25
Apreciados amigos Ubunteros:
De nuevo aquí en los foros buscando ayuda.
Algún día contestaré una pregunta, o haré un "How-To".
Pero por el momento, tengo un problema de funcionamiento adecuado con una máquina.
Les daré las especificaciones de la máquina a lo último.
Les describiré el problema ahora:

Primero, haciendo Dual-Boot WinXP con Ubuntu 7.10
Elijo Ubuntu 7.10 normal boot.
Empieza a hacer las verificaciones de sistema normales, y luego se tarda, con unos puntitos
....
....
....
....
como 15 minutos simplemente para llegar a la pantalla login
Cuando llego a la pantalla login, entonces pongo mi user y mi password, y luego se tarda como 15 minutos más, en entrar al Desktop.
Cuando POR FIN entra al Desktop, me sale un error muy feo:
(Perdonen que se los ponga en Inglés, ya que, así está configurada mi máquina, no en Español.)
************************************************************************************************************************************************************
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
************************************************************************************************************************************************************

Entonces, luego de esto, no puedo hacer nada con la máquina, solo puedo apagarla manualmente, presionando el botón de apagado; no hay otra opción.
Intenté acceder el shell, presionando ctrl-alt-f4, y la pantalla se va en negro, como si fuera el sistema apagado, y el monitor se duerme; no detecta entrada de vídeo en sistema.
Luego, como dije, tengo que apagar la máquina manualmente.

Al re-butiar la PC, escojo la opción de recovery.
Esta opción me tira al root@misistema-ubuntu.
Una vez estoy dentro (por lo menos me deja hacer eso, para poder arreglar el problema) no sé qué debo hacer.
Alguien sabe?
Por favor, paso-a-paso, ya que soy muy novato.

Gracias.

La otra opción, (claro está, que no quiero hacer) sería tratar de borrar esa partición y re-instalar Ubuntu, lo que es verdaderamente un poco complicado, cuando ya Windows XP está instalado en el Ordenador, y no quiero tener que re-instalar 2 sistemas operativos, cuando solamente tengo problemas con uno, claro que el WinXP corre a las mil maravillas.

Les agradezco cualquier comentario de ayuda.

Saludos desde Puerto Rico

Specs de sistema.
Máquina Dell Optiplex 755
Con Proc. Intel Core 2 vPro E6550 @2.33GHz
2GB RAM
Disco Duro de 250GB

--
ROM
Registered Ubuntu User #23478
Registered Linux User #457355

---

### Post by pol666 on 2008-08-25
Instalaste algun tema, o modificaste algo en el gnome y lo moviste de lugar, lo esta buscando y por eso tarda tanto ... habria que ver que fuye lo que hiciste que paso eso

---


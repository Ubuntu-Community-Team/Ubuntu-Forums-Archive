---
title: "¿Alguien usa el correo @arnet.com.ar con Evolution?"
date: 2009-05-26
forum: Software
---

### Post by guillermon on 2009-05-26
Hola: 
     He logrado que una persona migre a Linux, y como suele pasar, surge algún problemilla... Dicha persona usa mucho el Outlook Express, y posee el correo de arnet. Y no he podido configurárselo; no sé cómo tendría que especificarse el tema de los puertos... Si alguien lo usa, ¿puede contarme cómo hizo? No encuentro nada en la web...
    Esta persona tiene instalado Xubuntu 8.10 . Muchas gracias desde ya. Saludos

Guillermo

---

### Post by freewareprophet on 2010-02-26
> **guillermon said:**
> Hola: 
     He logrado que una persona migre a Linux, y como suele pasar, surge algún problemilla... Dicha persona usa mucho el Outlook Express, y posee el correo de arnet. Y no he podido configurárselo; no sé cómo tendría que especificarse el tema de los puertos... Si alguien lo usa, ¿puede contarme cómo hizo? No encuentro nada en la web...
    Esta persona tiene instalado Xubuntu 8.10 . Muchas gracias desde ya. Saludos

Guillermo

Hola, yo estaba buscando lo mismo y encontré tu pregunta. acá tenés la de Thunderbird (Windows), pero básicamente es lo mismo, aún si fuera OLook. El servidor pop, la cuenta [email]usuario@arnet.com.ar[/email], miralo vos mismo:

```
Dentro del cliente de correo Thunderbird, ir al menú superior, hacer clic en la opción “Herramientas” y luego en la opción “Configuración de las cuentas...”. Allí, seleccionar la cuenta de correo. Luego, se despliega el árbol y se ingresa en "Configuración del servidor". En la misma pantalla se modifica el campo “Nombre de usuario” agregando @arnet.com.ar (ver fig. 1)
```
[IMG]http://servicios.arnet.com.ar/arnetonline/ayuda-online/imgs/winxpthunderbird-1.jpg[/IMG]
```
Luego ingresar en el árbol a la opción "Servidor de salida (SMTP)" y hacer clic en el botón "Editar". Aparecerá la siguiente ventana (ver fig. 2):
```
[IMG]http://servicios.arnet.com.ar/arnetonline/ayuda-online/imgs/winxpthunderbird-2.jpg[/IMG]
```
En esa pantalla, en "Seguridad e identificación" tildar la opción "Utilizar nombre y contraseña". Modificar además el "Nombre de usuario" agregando @arnet.com.ar. En la opción "Utilizar conexión segura", tildar "No".
Por último, hacer clic en “Aceptar”.
```

[Acá]("http://servicios.arnet.com.ar/arnetonline/cambios_correo.asp#1")tenés las que están disponibles en Arnet, si no ves las img las podés mirar ahí.

```
Entrante: pop3.arnet.com.ar
Saliente:smtp.arnet.com.ar
Usuario:fulano_de_tal@arnet.com.ar
Autenticación: Segura (SSL)
```

---

### Post by z37a on 2010-02-27
Arnet en una época para evitar saturar sus redes bloqueaban el puerto 25, y solo bajo pedido del cliente se desbloqueaba.

Esto lo hacían ya que hay muchos virus y spywares que afectan a windows convirtiendo la CP en un zombie para enviar mails por smtp en forma masiva.

Si bien la persona ya uso por outlook yo llamaría a Arnet a ver si lo volvieron a bloquear o no(cuando arrrancaron con e bloqueo no avisaron y todo el mundo llamaba, hacen esas cosas sin avisar). Y de paso pedile los datos de conexión como el pop3, si usa encriptacion o no y el smtp si requiere autentificacion y/o encriptacion.

---

### Post by guillermolisi on 2010-02-27
> **z37a said:**
> Arnet en una época para evitar saturar sus redes bloqueaban el puerto 25, y solo bajo pedido del cliente se desbloqueaba.

Esto lo hacían ya que hay muchos virus y spywares que afectan a windows convirtiendo la CP en un zombie para enviar mails por smtp en forma masiva.

Si bien la persona ya uso por outlook yo llamaría a Arnet a ver si lo volvieron a bloquear o no(cuando arrrancaron con e bloqueo no avisaron y todo el mundo llamaba, hacen esas cosas sin avisar). Y de paso pedile los datos de conexión como el pop3, si usa encriptacion o no y el smtp si requiere autentificacion y/o encriptacion.
Avisaron en el portal de Arnet, luego del login del usuario, cosa que casi nadie hace, solo porque era informacion que debian mantener en el ambito de los usuarios, no del publico en general.

De ahi saque todas las instrucciones necesarias para rehabilitar amigos y clientes en ese momento.

Hace poco moficiaron el dominio y a algunas cuentas les cambiaron arnet.com.ar por arnet-biz.com.ar, dependiendo del contrato que habian suscripto (supongo que esta informacion tambien estaba o aun esta en el portal para clientes de Arnet.

---


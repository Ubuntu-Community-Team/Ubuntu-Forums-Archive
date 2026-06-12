---
title: "Greenstone + Ubuntu Problema!!!"
date: 2009-06-11
forum: Software
---

### Post by armengolx7 on 2009-06-11
Que tal estimados, antes de formular las preguntas les explico un poco el escenario.

En la empresa donde laboro poseemos dos servidores Ubuntu y uno Suse ademas de unos cuantos Windows 2003.

 La cuestion es que en uno de los Ubuntu se "montó" la libreria digital GREENSTONE, supongo que ya han escuchado de ella (Sino chequenla que esta muy buena y es libre y completamente editable mediante PERL o C++). Es una aplicacion web, lo que sucede es que no se guarda en el tipico /var/www... sino en este caso en /usr/local/gsdl/cgi-bin  [IMG]http://informaticanicaragua.net/Smileys/default/shocked.gif[/IMG] . Que configuracion debo de hacer en apache o en algun otro archivo para que:

1- Al digitar localhost, no me aparezca el tipico "IT WORKS!" sino la pagina del greenstone.
2- Que en vez de localhost le de en la barra del explorador... digamos bibliotecavirtual.miempresa.com.ni  [IMG]http://informaticanicaragua.net/Smileys/default/grin.gif[/IMG]

Cabe recalcar que hasta el momento dicha pagina sera de unico acceso en la red local de la institucion.

Espero que me ayuden en este inconveniente y de esta manera fomentar mas el uso de GNU.

Gracias de antemano!

---

### Post by sergiom99 on 2009-06-11
Aca tenes casi todo lo que necesitas:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/es/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/es/httpd.html)

Tenes que crear directorios virtuales y los podes apuntar a /usr/local/...

Suerte!

---

### Post by armengolx7 on 2009-06-12
Muchas Gracias... Estoy trabajandolo... En cuanto surja algo lo notifico!! Gracias!

---

### Post by armengolx7 on 2009-06-12
He realizado algunos de los pasos que me indica el documento del link que me enviaste. 

Pues al restart apache me envia el warning : NameVirtualHost SRVGREENSTONE:0 has no VirtualHost. 

Pues bueno alli el mensaje esta claro el detalle es que no encontre como es que se añade el virtualhost. Pero de todos modos apache inicia bien. 

El detalle ahora esta en que si introduzco en el explorador bibliotecavirtual.midominio.com me aparece el mismo "IT WORKS!". Veo que estoy "cerca" de publicar pero no le doy aun....


Gracias de nuevo... y si necesitas que adjunte algo de la configuracion avisame...

---

### Post by sergiom99 on 2009-06-12
Te pongo un ejemplo de lo que deberias agregar en el httpd.conf

```
<VirtualHost cp.hosting.com.ar:80>
        ServerAdmin server@host.com.ar
        DocumentRoot /home/cp/html      
        ServerName cp.hosting.com.ar     
        ErrorLog logs/cp-error_log      
        CustomLog logs/cp-access_log combined
 <Directory>
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
  </Directory>
</VirtualHost>

```
Aca lo que estas definiendo es un host virtual en el Apache que atiende al nombre de 'cp.hosting.com.ar' en el puerto 80.
Los documentos del site van en '/home/cp/html'
Hacer que desde internet se pueda llegar a cp.hosting.com.ar es otro tema (tenes que configurar el servidor de DNS que maneja el dominio hosting.com.ar)

Si lo vas a armar con Apache, te recomiendo que le pegues una leida a la wiki de ellos para ver como asegurar la instalacion y demas. Esto en realidad no es un tema de Ubuntu Server sino de config del servicio Apache.

Si no te anda, postea aca como tenes el archivo httpd.conf.
Saludos. Sergio

---

### Post by sergiom99 on 2009-06-13
contanos como te fue...

---


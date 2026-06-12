---
title: "Configurar redmine en Ubuntu Server"
date: 2012-04-17
forum: Uruguay Team
---

### Post by tricopablo1 on 2012-04-17
Buenos dias instale El administrador de proyectos Redmine en un ubuntu server 11 y no le puedo configurar el correo saliente. quiero configurarselo por sendmail y en la pagina del redmine me diece:

Las notificaciones están desactivadas porque el servidor de correo no está configurado. 
Configure el servidor de SMTP en /etc/redmine/<instance>/configuration.yml y reinicie la aplicación para activar los cambios.


copie de /usr/share/redmine/config# el archivo configuration.yml.example como configuration.yml y lo modiofique como dice ahi le agregue en default la linea

 production:
        email_delivery:
        delivery_method: :sendmail

le di reestar al apache2 pero nada me sigue diciendo lo mismo

---

### Post by maniat1k on 2012-04-20
debería ser así:[INDENT][FONT=Courier New]~# cat  /usr/share/redmine/config/configuration.yml
 production:
   email_delivery:
     delivery_method: :sendmail
[/FONT][/INDENT]proba si te funciona sendmail... mandate un par de mails como root a ver que sale...

tirate un  **tail -f/var/log/mail.err **o un **tail -f**** /var/log/mail.log**

agrega eso a ver que te sale...
saludos

---

### Post by tricopablo1 on 2012-04-20
el send mail esta configurado porque el servidor por medio del webmin me envía las actualizaciones para que las instale.

# default configuration options for all environments
default:
  # Outgoing emails configuration (see examples above)

production:
email_delivery:
delivery_method: :sendmail



eso dice y despues le hice un 


 /etc/init.d/apache2 restart


y me sigue diciendo 


Las notificaciones están desactivadas porque el servidor de correo no está configurado. 
Configure el servidor de SMTP en /etc/redmine/<instance>/configuration.yml y reinicie la aplicación para activar los cambios.

---

### Post by maniat1k on 2012-04-24
Ok, pégate una mirada a este: [http://www.redmine.org/boards/2/topics/15323](http://www.redmine.org/boards/2/topics/15323)
En la configuración del correo ([http://www.redmine.org/projects/redmine/wiki/EmailConfiguration](http://www.redmine.org/projects/redmine/wiki/EmailConfiguration)) dice algo sobre correos asincrónicos (ni idea en realidad por que me anduvo de una). 

pasa por aca: [http://www.redmineblog.com/articles/asynchronous-email-delivery/](http://www.redmineblog.com/articles/asynchronous-email-delivery/) y por acá [http://www.redmine.org/projects/redmine/wiki/RedmineReminderEmails](http://www.redmine.org/projects/redmine/wiki/RedmineReminderEmails)

los pasos que yo hice los publique en respuesta en askubuntu: quizás te sirvan yo que se. [http://askubuntu.com/questions/102715/how-can-i-reinstall-redmine/110981#110981](http://askubuntu.com/questions/102715/how-can-i-reinstall-redmine/110981#110981)

esto es lo que te dice?

Las notificaciones están desactivadas porque** el servidor de correo no está configurado**. 
Configure el servidor de SMTP en  /etc/redmine/<instance>/configuration.yml y reinicie la aplicación  para activar los cambios.

la primera parte dice que el servidor de correo no esta configurado...

fijate en el log a ver que más sacas...

---


---
title: "Cambiar directorio raiz de Apache"
date: 2023-07-02
forum: Ubuntu Application Development
---

### Post by gatoher on 2023-07-02
Hola a todos estoy intentado que apache me lea una web que tengo en  /home/carlos/prueba a la vez que tengo otras en /var/www/html. He  cambiado en apache.conf lo siguiente:

```

<Directory />     
   Options FollowSymLinks       
 AllowOverride  None        
Require all denied
</Directory>

 <Directory  /usr/share>       
    AllowOverride None       
   Require all  granted
</Directory> 

 **<Directory /home/carlos/prueba/>**          
   Options Indexes FollowSymLinks       
   AllowOverride None      
   Require all granted
</Directory>

   <Directory /var/www/>      
      Options Indexes
     FollowSymLinks       
    AllowOverride None         
   Require all granted
 </Directory>




```


Luego cree un virtualHost lo tengo asi:

```


<VirtualHost *:8080>        

  ServerName prueba.ddns.net        
  ServerAdmin [EMAIL="xxxxxxxxx@gmail.com"]xxxxxxxxx@gmail.com[/EMAIL]
  DocumentRoot /home/lucas/prueba/



```




Los permisos de /home/lucas/prueba están en 777 por que no me importa, pero no me encuentra la ruta.

Not Found

The requested URL was not found on this server.

Estoy trabajando en ubuntu 22.10 y la versión de mi apache es Apache/2.4.54 (Ubuntu).¿Alguna idea que puedo estar haciendo mal?

---


---
title: "Apache2 no ejecuta .pl"
date: 2009-05-23
forum: Software
---

### Post by zeroadrenaline on 2009-05-23
Tengo este temita, puedo acceder a mi V.Host pero los archivos .pl en vez de ejecutarlos los descarga.Uso debian, apache2, mod-perl2 habilitado, perl 5

Les paso los pedacitos de codigo que me parece intereszan.
Contenido de /etc/apache2/apache2.conf:

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

AddHandler cgi-script .cgi

Contenido de mi V.Host (Puede que tenga algunas desprolijidades, todabia estoy agarrandole la onda a esto):

<VirtualHost *>
DocumentRoot /var/www/oratio
Alias /oratio/ /va/www/oratio/
<Directory "/var/www/oratio">
allow from all
AddHandler cgi-script .pl
Options +Indexes ExecCGI Includes FollowSymlinks
</Directory>
LogLevel warn

<Directory "/var/www/oratio/users">
        Order Deny,Allow
        Deny from All
</Directory>

ErrorLog /var/log/apache2/oratio.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel error
CustomLog /var/log/apache2/access.log combined

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
 AllowOverride None
 Options ExecCGI Includes FollowSymlinks
 Order allow,deny
 Allow from all
</Directory>
</VirtualHost>

---


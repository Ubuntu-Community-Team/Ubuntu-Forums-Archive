---
title: "lan hdd fopen permision denied (fstab + apache2 + php)"
date: 2008-09-05
forum: Server Platforms
---

### Post by firmis132 on 2008-09-05
hello,

i have a headless ubuntu lan server which runs apache2 and at start up mounts a lan hdd with fstab.
the root directory is set to the lan hdd and works fine, but when it tries to write a new file with fopen - permission denied.
i check chown and chmod and owner is root and 664, so it can be opened by php...
the folder containing the new file belongs to apache and is 777

fstab------------                                                  
//10.0.0.3/folder  /media/folder  cifs  guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0   
------------------

etc/apache2/sites-enabled/server.site.conf------
<VirtualHost 10.0.0.101>                                                                                                                           
DocumentRoot /media/folder                                                                                                            
ServerName server.site                                                                                                                    
<Directory "/media/folder">                                                                                                           
allow from all                                                                                                                                     
Options +Indexes                                                                                                                                   
</Directory>                                                                                                                                       
</VirtualHost>  
---------------------------------------------------

any suggestions what might be wrong?
thanks

---

### Post by firmis132 on 2008-09-05
ok solved myself

fstab should be
\\10.0.0.3\folder  /media/folder  cifs  user,dir_mask=0777,password=****,uid=33,file_mask=0777,iocharset=utf8,gid=33,username=root  0  0

so the uid is the id of www-data and gid is for group www-data
that all

---

### Post by windependence on 2008-09-05
You need execute permissions on the folder that is 644 so that the script can enter the directory.

-Tim

---


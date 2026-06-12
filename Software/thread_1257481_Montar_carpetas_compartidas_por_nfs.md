---
title: "Montar carpetas compartidas por nfs"
date: 2009-09-03
forum: Software
---

### Post by pol666 on 2009-09-03
tengo dos pc's conectadas al router y desde ahí busque formas de compartir archivos mediante la red local, vi que podia hacerlo con nfs, no se si hay otra si es mejor o peor..

bien, la cuestión es que la pc del living actua como servidor nfs ya que quiero acceder a ese disco mediante mi computadora, hasta ahí funciona, lo que no logro hacer es que monte la carpeta al inicio (aún estando conectadas ambas computadoras)

puse esta linea en el fstab

> 192.168.1.101:/home/mabel /media/living nfs rw 0 0


pero no sirve de nada y tengo que montarla manualmente con este comando

> sudo mount -t nfs 192.168.1.101:/home/mabel /media/living

Salvo que haga un script que arranque al inicio pero si hay otra posibilidad mejor...

---

### Post by guillermolisi on 2009-09-03
Y el /etc/exports del server dice .... ?

Que pasa si ejecutas esa mismo mount pero sin sudo ?

---

### Post by pol666 on 2009-09-03
mount: sólo el usuario root puede efectuar esta acción

---

### Post by guillermolisi on 2009-09-03
Ok.

No pegaste el contenido de /etc/exports del server ...

En mi /etc/fstab de la red de mi casa tengo
```
# NFS
ubuntu804server:/home/guille/downloads /media/server/downloads nfs user,atime,auto,rw,nodev,exec,nosuid 0 0
```

donde el directorio /media/server esta con mi user y mi grupo, al igual que /media/server/downloads

y en el /etc/exports del server
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/guille/downloads  90.0.0.0/255.255.255.0(sync,rw)
```

Verifica owner y group del punto de montaje y adecualos si hace falta.
En el /etc/fstab la opcion "user" permite que la monte y desmonte cualquier usuario.
rw indica que el recurso se exporta y monta como read-write.

---

### Post by pol666 on 2009-09-03
Gracias, mañana cuento si funciono :)

---


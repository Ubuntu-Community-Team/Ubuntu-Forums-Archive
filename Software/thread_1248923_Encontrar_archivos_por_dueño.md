---
title: "Encontrar archivos por dueño"
date: 2009-08-24
forum: Software
---

### Post by armagedonc on 2009-08-24
Hola , necesito encontrar un archivo en una base de datos pero tiene que ser de un usuario en particular, mas bien de un grupo de usuarios que no estan bajo un mismo grupo pero sus nombres de usuario tienen similitudes.
Ya probe con find -user "nombre" lo cual me da los archivos que pertenecen a "nombre" el asunto es que al usar wildcards find no arroja nada.

---

### Post by moreback on 2009-08-24
Deberías leer la página de manual del comando find:

```
man find
```Si lo lees, te darás cuenta que las opciones para los usuarios y grupos son: **-user** y **-group** y que no se te olvide que la forma de invocar find es:

```
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [path...] [expression]
```

O sea algo así:

```
find -user usuario_del_sistema /ruta/a/los/archivos "texto"
```

Saludos.

---

### Post by armagedonc on 2009-08-24
Eso ya lo intente pero no es lo que busco , si utilizo eso me arroja resultados de un usuario y los archivos que busco pertenecen a un gurpo de usuarios con similitudes en su uid y no pertencen al mismo gid, si uso wildcards como por ejemplo find -user /etc juan* no encuentra nada. Necesito algo que encuentre dueños de archivo que tengan similitud en su uid.

---

### Post by armagedonc on 2009-08-25
algo.

---


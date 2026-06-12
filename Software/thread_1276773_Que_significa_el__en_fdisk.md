---
title: "Que significa el * en fdisk?"
date: 2009-09-27
forum: Software
---

### Post by emiliano_raso on 2009-09-27
> **santiagoward2000 said:**
> Bienvenido! :)
Para ver si borraste la partición de Windows cuando instalaste Ubuntu, abrí una terminal (Aplicaciones > Accesorios > Terminal), y escribí:
```
sudo fdisk -l
```
Te va a pedir tu contraseña (ojo que no ves nada cuando la ingresás, pero entra igual). Si la partición de Windows sigue ahí, vas a ver un ítem en la lista con sistema NTFS.
Si tenés alguna duda, podés pegar el resultado que ves en la terminal acá, para ver si te podemos ayudar mejor.
Ojalá no hayas perdido nada.
Suerte!

Me cuelgo del thread:
Al tirar fdisk -l me da lo siguiente:

```
debian:/home/emiliano# fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x355f251c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1274    10231808    7  HPFS/NTFS
/dev/sda2   *        1275       10383    73168042+   7  HPFS/NTFS
/dev/sda3           10384       19457    72886905   83  Linux
```

Que significa el asterisco?

---

### Post by santiagoward2000 on 2009-09-27
> **emiliano_raso said:**
> Que significa el asterisco?

El asterisco te marca la partición que está marcada como inicio. Por lo que entiendo (que aclaro no es mucho) algunos bootloaders buscan esta marca para decidir desde qué partición arrancar. En nuestro caso, donde tenemos grub, que le podemos decir qué partición queremos que arranque, no nos hace mucha diferencia.
Igual estaría buenísimo si alguien quiere explicarlo mejor.
Saludos!

---

### Post by Hei Ku on 2009-09-27
Y te descolgamos. :D

Encima que es nuevo, no lo mareen con cosas off-topic.

---

### Post by juancarlospaco on 2009-09-27
**Boot Flag**

*Bandera Bota?*

---

### Post by emiliano_raso on 2009-09-27
Pero mi maquina arranca con el GRUB de la particion con Debian, no con SDA2 que tiene Windows xD y justamente es la qeu tiene el asterisco...

---

### Post by santiagoward2000 on 2009-09-27
> **emiliano_raso said:**
> Pero mi maquina arranca con el GRUB de la particion con Debian, no con SDA2 que tiene Windows xD y justamente es la qeu tiene el asterisco...

Es que esa marca indica qué partición es booteable para Windows. El arranque de Windows la busca para elegir en qué partición arrancar. El grub no le presta atención, vos le decís con cuál querés que arranque desde su configuración, no desde la partición.

---

### Post by guillermolisi on 2009-09-27
> **santiagoward2000 said:**
> Es que esa marca indica qué partición es booteable para Windows. El arranque de Windows la busca para elegir en qué oartición arrancar. El grub no le presta atención, vos le decís con cuál querés que arranque desde su configuración, no desde la partición.
Y si no me equivoco y recuerdo mal, el boot flag viene de la epoca del MS-DOS.

---

### Post by emiliano_raso on 2009-09-27
Ahhh... Ahora entendi. Gracias gente.

---

### Post by santiagoward2000 on 2009-09-27
> **emiliano_raso said:**
> Ahhh... Ahora entendi. Gracias gente.

De nada :)

---


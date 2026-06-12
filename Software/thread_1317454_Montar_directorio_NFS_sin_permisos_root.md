---
title: "Montar directorio NFS sin permisos root"
date: 2009-11-06
forum: Software
---

### Post by Fistandantilus on 2009-11-06
es posible?

estoy googleando y no encuentro nada coherente... 

la idea es crear una carpeta, por ejemplo, ~/.imports/[algo] y montar un directorio exportado en un servidor nfs sin hacer "sudo mount" ni agregarlo en el fstab con la opción "users"...

Mi duda se basa en lo siguiente:
Imaginen se administrar una red con 100 máquinas y uno, o varios, servidores nfsv4 con autenticación basada en usuarios. Si no puedo hacer que los usuarios tengan la posibilidad de que ellos mismos puedan montar los directorios, por cada persona a la que le de permisos para acceder a un directorio voy a tener que modificar la configuración de la maquina(en la que este en ese momento) para que monte el/los directorio/s automáticamente(con la opción "users" para que lo vuelva a montar en caso de que caiga el server)... es doble configuración!!! U_U

osea si yo ya le di permisos de acceso a "ESE"  usuario para "TAL" directorio, debería poder montarlo...

por otro lado, si al ñato se le "rompió" la máquina y quiere usar otra que esta a disposición, no va a poder laburar hasta que un "bendito admin" se la configure(física o remotamente, no viene al caso)...

Capaz estoy encarando mal el problema, si es así estoy abierto a cualquier alternativa(menos SAMBA).

Saludos!.

---

### Post by Fistandantilus on 2009-11-07
Lo ven posible encararlo desde los permisos?

¿ Existe alguna manera de darle permisos a un usuario determinado para usar el comando "mount"( o "mount.nfs4", en este caso) ? o esta hardcodeado que únicamente el usario root puede hacer uso de esos comandos, sin excepción?  

También estoy intentando con la posibilidad de usar "autofs"... ¿ Alguien lo ha usado ? ¿ Algún comentario sobre "autofs" ?

---

### Post by guillermolisi on 2009-11-07
> **Fistandantilus said:**
> Lo ven posible encararlo desde los permisos?

¿ Existe alguna manera de darle permisos a un usuario determinado para usar el comando "mount"( o "mount.nfs4", en este caso) ? o esta hardcodeado que únicamente el usario root puede hacer uso de esos comandos, sin excepción?  

También estoy intentando con la posibilidad de usar "autofs"... ¿ Alguien lo ha usado ? ¿ Algún comentario sobre "autofs" ?
Supongo que, como casi siempre, alguna solucion hay.

La version 9.10 tiene un [bug heredado de Debian]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524760") respecto de NFSv3, por lo cual decidi cambiar a NFSv4.

Para ello primero busque casos en Ubuntu Forums y encontre [este thread]("http://ubuntuforums.org/showthread.php?t=1308241") (en Ingles).
Luego, con [este tutorial]("https://help.ubuntu.com/community/NFSv4Howto") (tambien en Ingles), que no esta completo pero es suficiente como para empezar, adecue mi LAN para usar NFSv4. La gran diferencia entre tu contexto y el mio es que en mi caso no hay mas que un usuario y es el mismo tanto en el server como en el cliente.

Dado mi contexto, opte por NFSv4 sin Kerberos authentication.

---

### Post by Fistandantilus on 2009-11-07
buenisimo!, ahora me estoy yendo pero en cuanto pueda los voy a ver.

gracias.

---

### Post by Fistandantilus on 2009-11-26
A pesar del tiempo que pasó desde que inicie este thread todabia lo sigo investigando.

Hay 2 cosas interesante que he encontrado sobre "Montar directorios NFS sin permisos root" que me gustaria compartir:

1) Según la implementación actual del comando "mount.nfs"/"mount.nfs4" no hay duda alguna que **no es posible montar un directorio nfs sin permisos root y que no se encuentre en fstab con la opción "users"**. Cito una porción de código donde hace el chequeo(para lo que entienden C):
```

    if (uid != 0) {
        struct mntentchn *mc;

        if ((mc = getfsfile(mount_point)) == NULL ||
            strcmp(mc->m.mnt_fsname, spec) != 0 ||
            strcmp(mc->m.mnt_type, fs_type) != 0) {
            nfs_error(_("%s: permission denied: no match for %s "
                "found in /etc/fstab"), progname, mount_point);
            goto out_usage;
        }

        /*
         * 'mount' munges the options from fstab before passing them
         * to us, so it is non-trivial to test that we have the correct
         * set of options and we don't want to trust what the user
         * gave us, so just take whatever is in /etc/fstab.
         */
        mount_opts = strdup(mc->m.mnt_opts);
    }

```2) Encontre un proyecto muy interesante al respecto pero que esta muy(negrita, mayúsculas y todo lo que se ocurra para remarcarlo) verde.
Actualmente lo estoy chusmeando y si puedo cerrar un par de detalles que me parecen muy importantes me gustaria empaquetarlo para que los que lo quieran probar puedan hacerlo facilmente.

les dejo el link del proyecto: [http://github.com/bmario/nfs-mount](http://github.com/bmario/nfs-mount)

En caso de tener mas noticias sobre el tema voy a seguir posteando en este mismo thread ya que me parece un punto muy importante, principalmente para la gente que no desee compartir archivos por medio de samba y este buscando alternativas.

Saludos!.

---

### Post by fmsismo on 2009-11-26
Podes hacer un script que haga el mount y darle al usuario sudo para ese script.

Sino podes configurar el automount para que cualquier usuario monte un nfs en el /net

---

### Post by EnriqueK on 2009-11-26
No se ti te servirá , pero para que un programa  (script) pueda ser ejecutado por quienes no tengan permisos de administrador es agregando 4000 a los números octales de los permisos, el siguiente sería un ejemplo simple que te puede orientar.
Supongamos que queros crear un script para  reinicuar el equipo sin que te pida contraseña
1,. Abre un nuevo documento de textos en tu carpeta de usuario y pones

#!/bin/sh
sudo reboot
2.- Lo guardas con el nombre de reiniciar
3.- Click secundario sonre este Script ->-Propiedades --> Permisos--> Marcas el casillero Permitir ejecutar el archivo como programa
4.- Seguidamente ejecuta los comandos  siguientes
sudo cp reiniciar /usr/bin
sudo chmod 4777 /usr/bin/reiniciar
5.- A partir de ahora podrás reiniciar el equipo poniendo en terminal reiniciar o también podrás crear un lanzador y ninguno va a pedir contraseña

Mas informaciñin la podñes conseguir buscando por "·modificar suid"

---

### Post by Fistandantilus on 2009-11-26
@fmsismo: Al automount ya lo habia evaluado anteriormente pero hay un punto donde no me convence, que es la configuración. Estoy buscando un algún método para el montaje libre de configuración en cuanto a que directorio es el que se puede montar. Con el automount tenes el pro de no tener que ser root para montar pero al igual que al usar el fstab, hay que indicarle que es lo se va a auto-montar.

@EnriqueK: A pesar que con eso solucionaría 2 temas(el hecho de no tener que ser root y no estar atado a un archivo de configuración) no me convence por el lado de la seguridad...

El proyecto al cual hago referencia me parecio piola por los siguientes puntos:
- La interfaz para montar/desmontar es gráfica(un systray) 
- Como en la soluciones propuestas tampoco es necesario ser root para montar/desmontar
- En contraste con la solución de EnriqueK, es posible agregar algún control de seguridad. Dentro de los cambios que me gustaría hacerle es el hecho de que labure con policyKit para las autorizaciones.

No se si estoy explicando correctamente mi punto de vista. 

De todas maneras agradesco las soluciones propuestas ya que en si mismas son válidas.

Saludos.

---

### Post by EnriqueK on 2009-11-26
Con el método que te he explicado no creo que se afecte la seguridad por que el root va a dar permiso de ejecución solamente para un script o programa en particular, no se está abriendo la tranquera para que pase el malón, mas bien creo que este método es  mas seguro que otros ya que en con estos  puedes llegar a no saber en ciencia cierta si no has dejado abiertas otra(s) tranqueras(s),

---

### Post by Fistandantilus on 2009-11-26
Entiendo tu punto, es verdad que con ese método no estaría permitiendo a los usuario normales ejecutar el comando que les plazca. 
Justamente por eso lo considero como una opción válida, pero si existe la posibilidad de poder hacerlo por medio de una interfaz gráfica y a su vez tener la posiblidad de aplicarle un mejor control sobre que usuario(o grupos) pueden o no montar/desmontar para que cualquier ñato pueda hacerlo me parece que vale la pena investigarlo.

Te comento xq digo "cualquier ñato", en mi maquina tengo una partición específicamente para datos(música, películas, documentos, etc) y la exporto por medio de nfs para que desde la máquina de viejo el pueda acceder a esa información y además usarla para lo que le parezca conveniente. Le configuré el fstab para que la monte automáticamente, el problema está cuando el prende su máquina y no está prendida la mía. En ese caso tiene 2 posiblidades, o reinciar su máquina o ejecutar "sudo mount -a"("-a" para simplificarle las cosas). En caso de agregarle la opción "users" o "user=[nombre_de_usario]" podría hacerlo sin sudo, pero en ese caso tendría que escribir el path que desea montar. Como lo soluciono? le anoto el comando para que el pueda hacerlo sin mi intervención(principalmente si yo no estoy). Pero en base de esa necesidad es que me surgió la duda si existe algún gui para configurar el nfs(tanto las importaciones como las exportaciones). Por otro lado en mi 1er post lo quise llevar a un caso mas puntual desde el punto de vista de un sysadmin dentro de una red conformada toda con máquinas con linux.

Espero que comprendas mi punto de vista, 

Saludos!.

---


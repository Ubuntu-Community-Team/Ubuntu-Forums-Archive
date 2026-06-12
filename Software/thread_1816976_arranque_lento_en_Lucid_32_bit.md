---
title: "arranque lento en Lucid 32 bit"
date: 2011-08-02
forum: Software
---

### Post by asterix77 on 2011-08-02
Hola a todos:

He instalado ubuntu lucid 32 bit en un disco duro externo seagate de un tera. Al principio el arranque era normal, cosas de 30 segundos diría yo. El problema al parecer surgió luego de una actualización del sistema, a decir verdad la primera de ella, que fueron más o menos unos 120 megas.

Entre todas las actualizaciones estaba una de grub2, que al instalarse no sé porqué me preguntó donde instalarse. Aparecieron dos opciones una fue sdc a secas, y la otra fue de sdc1

sdc es mi disco duro externo, el cual tiene una partición ext4 para la raiz (sdc1), otra para mi /home (sdc2), otra para swap (sdc3), y el resto lo dejé NTFS


Disco /dev/sdc: 1000.2 GB, 1000204885504 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0009afac

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        2189    17583111   83  Linux
/dev/sdc2            2190        6249    32611950   83  Linux
/dev/sdc3            6250        6710     3702982+  82  Linux swap / Solaris
/dev/sdc4            6711      121601   922861957+   7  HPFS/NTFS


Y desde entonces que el sistema en el arranque ha tenido problemas, el grub aparece rápido, pero de aquí a que se vea el splash pueden pasar de 2 a 5 minutos. No sé si lo que le comenté anteriormente tiene que ver con el problema.


Otra cosa que me he dado cuenta, es que a veces por una fracción de segundos, aparece un mensaje (fracción de segundos antes de que aparezca el splash)el cual es el siguiente:

$ dmesg | grep Timed
[   36.735003] tpm_tis 00:03: Operation Timed out

En google este problema al parecer no está muy descrito, pero tiene al parecer algo que ver con el ventilador.


Es como si el pc se quedara esperando "algo", y al no encontrarlo recién prosigue con el arranque.

Otra cosa que me pasa y tal vez tenga relación con lo mismo, es que al apagar el pc, este se cuelga otra vez en el splash, y no responde ninguna acción, no quedando otra alternativa que apagarlo a la mala (presionando 5 segundos el botón del encendido), y apagandola desde la consola pasa lo mismo.


Espero que alguien me pueda dar una solución o al menos una pista.

Saludos

---

### Post by guillermolisi on 2011-08-03
No me quedo claro en que lugar del disco portatil instalaste Grub2.

---

### Post by asterix77 on 2011-08-03
Al instalar el sistema operativo por primera vez, dejé el grub en sdc1, luego al actualizarse no sé porqué me ofreció 2 alternativas que fueron sdc y sdc1, marqué ambas opciones.


Saludos

---

### Post by guillermolisi on 2011-08-03
En general, para instalaciones simples, la recomendacion es instalar Grub en el MBR del disco, es decir en /dev/sdc. Luego Grub se encarga de releevar los sistemas operativos que encuentre en las demas particiones para armar su menu.

---

### Post by alfplayer on 2011-08-04
tpm_tis es del sistema TPM (Trusted Platform Module). Intentá deshabilitarlo en el BIOS.

---

### Post by biale on 2011-08-04
Sacale las opciones de arranque " quiet splash" para ver que es lo que mas le cuesta...

---


---
title: "Samba funciona solo en un sentido y no es el firewall"
date: 2011-11-13
forum: Software
---

### Post by esbrinartot on 2011-11-13
Samba me monta la carpeta de impresoras y puede acceder a otros ordenadores pero no me monta la carpeta de datos
hace 12 horas por esbrinartot Internet y redes

Equipo en que tengo el problema: Lubuntu 11.10 con LXDE con gestor de ventanas openbox y gestor de archivos PcmanFM 0.9.9

Buenas, he configurado samba y me funciona todo bien a excepción de que no me monta la carpeta en la que quiero compartir los datos "fallo al montar la compartición windows" "la ubicación especificada no esta montada". Por lo tanto si quiero puedo obtener información de otros ordenadores pero los otros no pueden obtener de mi ordenador. No es problema de firewall ya que lo tengo desactivado, y las impresoras si me las deja compartir.

Para instalar samba copie exactamente el procedimiento de mi ordenador de sobremesa que funciona a la perfección. Por lo tanto no entiendo porque no funciona. Describo la configuración y paquetes instalados para que alguien me aconseje:

sudo apt-get install samba samba-client smbfs smbclient

creo la carpeta home/joan/public

(El siguiente es hacer carpeta compartida la folder. Por lo tanto instalo nautilus-share y mediante nautilus pongo la carpeta compatida)

sudo gedit /etc/samba/smb.conf
y añado el siguiente texto:
[public]
comment = Public Folder
path = /home/joan/public
;	browseable = yes
writeable = yes
guest ok = yes
public = yes
create mask = 0777
directory mask = 0777

Me aseguro que el nombre del grupo es correcto y pongo security = share

sudo chmod 777 /home/joan/public
chown nobody:nogroup /home/joan/public

Alguien sabe que me dejo?? Puede ser que El gestor de archivos PCman no pueda montar paritciones? Hay algún pluggin o solución sin cambiar de gestor? Puede que no me la monte pq la unidad home la tengo encriptada?

---

### Post by guillermolisi on 2011-11-15
> **esbrinartot said:**
> Samba me monta la carpeta de impresoras y puede acceder a otros ordenadores pero no me monta la carpeta de datos
hace 12 horas por esbrinartot Internet y redes

Equipo en que tengo el problema: Lubuntu 11.10 con LXDE con gestor de ventanas openbox y gestor de archivos PcmanFM 0.9.9

Buenas, he configurado samba y me funciona todo bien a excepción de que no me monta la carpeta en la que quiero compartir los datos "fallo al montar la compartición windows" "la ubicación especificada no esta montada". Por lo tanto si quiero puedo obtener información de otros ordenadores pero los otros no pueden obtener de mi ordenador. No es problema de firewall ya que lo tengo desactivado, y las impresoras si me las deja compartir.
Como desactivaste el firewall ?

> Para instalar samba copie exactamente el procedimiento de mi ordenador de sobremesa que funciona a la perfección. Por lo tanto no entiendo porque no funciona. Describo la configuración y paquetes instalados para que alguien me aconseje:

sudo apt-get install samba samba-client smbfs smbclient

creo la carpeta home/joan/public

(El siguiente es hacer carpeta compartida la folder. Por lo tanto instalo nautilus-share y mediante nautilus pongo la carpeta compatida)

sudo gedit /etc/samba/smb.conf
y añado el siguiente texto:
[public]
comment = Public Folder
path = /home/joan/public
;	browseable = yes
writeable = yes
guest ok = yes
public = yes
create mask = 0777
directory mask = 0777

Me aseguro que el nombre del grupo es correcto y pongo security = share

sudo chmod 777 /home/joan/public
chown nobody:nogroup /home/joan/public

Alguien sabe que me dejo?? Puede ser que El gestor de archivos PCman no pueda montar paritciones? Hay algún pluggin o solución sin cambiar de gestor? Puede que no me la monte pq la unidad home la tengo encriptada?
En la otra maquina que tenes funcionando a la perfeccion tambien /home esta encriptado ?

---

### Post by esbrinartot on 2011-11-15
Ya lo solucione. El problema es que tengo cifrada la partición Home y al parecer si tienes la unidad cifrada no te monta la carpeta. Cambie la carpeta de ubicación, más concretamente en unidad ntfs compartida ente windows y Lubuntu. Ahora funciona perfecto.

---


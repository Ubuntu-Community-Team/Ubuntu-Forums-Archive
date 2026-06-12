---
title: "programa para saber el nombre y modelo del la placa madre de un PC"
date: 2012-06-22
forum: Software
---

### Post by drazhe on 2012-06-22
Hola comunidad.

¿Existe algún programa similar al AIDA64 o Everest pero para Ubuntu?

O mejor aún, alguna manera de saber el nombre de la placa madre y de video y del hardware en general de un PC desde algún comando de la consola o aplicación que tenga o se le pueda instalar a Ubuntu?

---

### Post by rojojuan on 2012-06-22
En consola: sudo lshw
También tengo instalado hardinfo, que suministra muy buenos datos.



> **drazhe said:**
> Hola comunidad.

¿Existe algún programa similar al AIDA64 o Everest pero para Ubuntu?

O mejor aún, alguna manera de saber el nombre de la placa madre y de video y del hardware en general de un PC desde algún comando de la consola o aplicación que tenga o se le pueda instalar a Ubuntu?

---

### Post by drazhe on 2012-06-22
> **rojojuan said:**
> En consola: sudo lshw
También tengo instalado hardinfo, que suministra muy buenos datos.

Gracias! me sirve muchisimo la información que me diste...

---

### Post by granjero on 2012-06-23
hola, yo tengo hecho un script que lo copiás al escritorio le das permiso de ejecución y lo ejecutás. Hace una carpeta en el escritorio con 3 archivos con mucha data de tu hardware.

salud!
```
#!/bin/bash
clear
echo "Script de analisis de hardware."
echo ""
mkdir -p $(pwd -P)/Hardwarescript
cd $(pwd -P)/Hardwarescript
echo "obteniendo datos DMI (SMBIOS)..."
sudo dmidecode  >> dmidecode.txt
sleep 2
echo "listo."
echo "obteniendo datos del hardware..."
sudo lshw >> lshw.txt
sleep 2
echo "listo."
echo "obteniendo datos PCI..."
sudo lspci >> lspci.txt
sleep 2
echo "todos los datos necesarios han sido guardados con exito." 
sleep 2

```

Salud!

---

### Post by drazhe on 2012-06-23
> **granjero said:**
> hola, yo tengo hecho un script que lo copiás al escritorio le das permiso de ejecución y lo ejecutás. Hace una carpeta en el escritorio con 3 archivos con mucha data de tu hardware.

salud!
```
#!/bin/bash
clear
echo "Script de analisis de hardware."
echo ""
mkdir -p $(pwd -P)/Hardwarescript
cd $(pwd -P)/Hardwarescript
echo "obteniendo datos DMI (SMBIOS)..."
sudo dmidecode  >> dmidecode.txt
sleep 2
echo "listo."
echo "obteniendo datos del hardware..."
sudo lshw >> lshw.txt
sleep 2
echo "listo."
echo "obteniendo datos PCI..."
sudo lspci >> lspci.txt
sleep 2
echo "todos los datos necesarios han sido guardados con exito." 
sleep 2

```

Salud!

Gracias, pero no entiendo mucho esto de los scripts.... voy a ver que tal me va... pero con el comando de la consola ya me alcanza...

---


---
title: "Bluetooth Broadcasting (Envia un archivo a varios dispositivos)"
date: 2009-01-31
forum: Software
---

### Post by Darkade on 2009-01-31
Este es un pequeño script que hice como una broma que hice en mi universidad. Basicamente envia un archivo por bluetooth a todos lo que tengan bluetooth activado. Obviamente lo pueden aceptar o rechazar... pero por lo que vi ni uno solo lo rechazo XDDD

Disfruten la broma y si tienen opiniones sobre el script por favor posteenlas

Antes de usarlo requiere que instalen obexftp.

```
sudo apt-get install obexftp
```

Si alguien conoce una mejor aplicacion para enviar archivos por bluetooth por favor recomiendenmela \\:D/

```
#!/bin/bash

if [ -n "$1" ]; then

	if [ -f "$1" ]; then

		devices=$(hcitool scan | cut -c1-18 | sed '1d')
		echo "Se intentara enviar el archivo $1 a los siguientes dispositivos:"
		echo $devices;	echo

		for direccion in $devices; do
			echo "Intentando enviar $1 a $direccion"; echo
			obexftp -b $direccion -p $1
		done
	
	else
	echo "El archivo no existe"
	fi

else
echo "No se ha especificado un archivo"
fi
```

---

### Post by sussanitta on 2009-10-08
hola me gustari me pudieras ayudar a como instalarlo en el sistema operativo

---


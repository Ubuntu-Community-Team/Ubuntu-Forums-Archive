---
title: "Tecla de imprimir bloqueada para archivos pdf"
date: 2008-10-01
forum: Software
---

### Post by Matiuss on 2008-10-01
Hola!

No puedo imprimir pdf's.
La tecla para imprimir un archivo pdf en el evince me aparece bloqueada. Lo único que puedo hacer es imprimirla a otro archivo pdf o ps.
La impresora está instalada y funciona perfectamente si quiero imprimir un rtf, un .doc, o la página de prueba. He leído por ahí que puedo ser que el pdf esté protegido por contraseña contra impresión. ¿Puede ser?
Hay una solución para eso que convierte el archivo en un ps con el comando $ pdftops. Lo hice y me pasa exactamente lo mismo.
¿Alguna ayuda?

Saludos!

---

### Post by ariel on 2008-10-04
> **Matiuss said:**
> Hola!

No puedo imprimir pdf's.
La tecla para imprimir un archivo pdf en el evince me aparece bloqueada. Lo único que puedo hacer es imprimirla a otro archivo pdf o ps.
La impresora está instalada y funciona perfectamente si quiero imprimir un rtf, un .doc, o la página de prueba. He leído por ahí que puedo ser que el pdf esté protegido por contraseña contra impresión. ¿Puede ser?
Hay una solución para eso que convierte el archivo en un ps con el comando $ pdftops. Lo hice y me pasa exactamente lo mismo.
¿Alguna ayuda?

Saludos!

Normalmente si el archivo esta protegido contra impresion, solo Adobe Reader respeta la proteccion y bloquea la impresion; evince la ignora.

En evince, si en el menu seleccionas File > Print, te aparece listada tu impresora? Si no aparece, el menu ppal de ubuntu seleccional System > Administration > Printing y agregala.

De ultima, podes probar abrir el pdf con acrobat reader, para instalarlo:

```
sudo apt-get install acroread
```

---

### Post by santiagoward2000 on 2008-10-04
> **ariel said:**
> De ultima, podes probar abrir el pdf con acrobat reader, para instalarlo:

```
sudo apt-get install acroread
```

El Acrobat no está en los repositorios de Hardy. Para instalarlo, podés seguir estas instrucciones para agregar los repositorios de Medibuntu:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Saludos!

---


---
title: "No puedo instalar nada"
date: 2009-06-17
forum: Software
---

### Post by layevska on 2009-06-17
**Te**ngo ubuntu jaunty y cuando trato de instalar un .DEB me sale algo de error de artquitectura :S

---

### Post by staar on 2009-06-17
o.O eso no debería pasarte con todos los paquetes...
tenés ubuntu de 64 bits? cual es el error exacto que te sale? y al tratar de instalar qué?

saludos

---

### Post by josecuervo86 on 2009-06-17
Seguramente tenes arquitectura 64 bits no? Cuando bajes un deb que no esta en los repositorios fijate que este sea X86-64 o AMD64, de lo contrario no lo vas a poder instalar.

---

### Post by layevska on 2009-06-17
Si, tengo el 64 bits xD


ps al tratar de instalar cualquier .Deb

y el error que me da es este Error: wrong architecture 'i386'

---

### Post by fmsismo on 2009-06-17
Como te trataban de explicar los foreros, bajaste un paquete para arquitectura i386, vos estas usando amd64, si bien lo podes forzar y puede que ande, lo mejor es bajar directamente uno para x86-64 o amd64.  Si no podes conseguir la aplicación en 64bits, avisa y te ayudamos con esa de 32.

Saludos

---

### Post by layevska on 2009-06-17
installer_kbasic_professional_linux.bin: installer_kbasic_professional_linux.bin: cannot execute binary file


 :SS

al tratar de instalar el Kbasic en .bin

miren lo que me sale

---

### Post by pablo.s on 2009-06-17
No le has dado permisos
de ejecución:

chmod 755 (aqui va el nombre del archivo)

---

### Post by layevska on 2009-06-18
ya le di los permisos pero no puedo instalarlo :S me sale lo mismo

---


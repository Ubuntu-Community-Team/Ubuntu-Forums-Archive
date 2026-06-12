---
title: "VirtualBox con usb"
date: 2009-11-16
forum: Software
---

### Post by oscarenzo on 2009-11-16
Buenas tardes a todos, tengo un problemilla con virtualbox, a ver si me pueden echar un cable, tengo un pc corriendo sobre ubuntu jaunty, con virtuabox 3.0.10 r54097.

Pero mi problemilla es que no me detecta mis dispositivos usb, alguien me puede echar un cable que puedo hacer?.

Gracias de antemano

---

### Post by Mauro22 on 2009-11-16
Hola!


Estas usando la version OSE ?? o la de còdigo cerrado??


Es decir:

La instalaste desde el repositorio o la bajaste de la web?

---

### Post by guillermolisi on 2009-11-16
La pregunta de Mauro va porque la version OSE (Open Source Edition) no soporta USB. La PUEL, de uso libre pero de alcance personal y no open source, si soporta USB.

---

### Post by leosr on 2009-11-16
Hola.
Acá tenés un tutorial para instalar VirtualBox:
[http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/](http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/) ; fijate que tu usuario pertenezca al grupo VBoxusers.

Asegurate que el que tenés instaldo sea el que dice Guillemo bajado desde la página de VirtualBox.

Saludos.

---

### Post by josecuervo86 on 2009-11-16
Casi seguro que es la cerrada, porque la de los repos es 3.0.8. Si estamos habalando de la cerrada, tenes que ir a la configuración de la maquina virtual y de ahí al apartado USB, y crear un filtro para cada dispositivo que quieras ver en tu maquina virtual apretando sobre el botoncito **+**.

[EDIT] Muy importante lo que dice leosr, tenes que estar en el grupo vboxusers. Anda a **Sistema** > **Administración** >**Usuarios y grupos** luego apreta sobre las **llaves** que aparecen para poder realizar los cambios, pone tu clave y dale [Enter]. Despues anda a **Gestionar grupos** y busca el grupo llamado **vboxusers** (que esta casi al fondo) apreta sobre el y loego sobre **propiedades**. Una vez que se abre la ventana de propiedades tilda tu usuario como perteneciente a ese grupo. Cerra todo y despues proba que onda.

**Paso a paso:**

---

### Post by oscarenzo on 2009-11-16
he instalado la versión de la web, supongo que es la versión cerrada, lo que pasa es que he hecho lo que dice josecuervo86, he creado un filtro para ese dispositivo, osea cuando le doy a crear filtro en ese signo "+", me detecta el usb, le creo el filtro, luego inicio mi xp, pero nada, no lo reconoce, que mas puedo hacer? algún consejo?

PD: Luego de lo que hago lo que dices tengo que cerrar sesión? o ya debe de ir?

gracias por sus respuestas

---

### Post by oscarenzo on 2009-11-16
Gracias por su ayuda chicos, ya he conseguido que funcione, hice los pasos que indico josecuervo86, gracias por todo.

Saludos.

---


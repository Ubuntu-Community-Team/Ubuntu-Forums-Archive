---
title: "Depósito de claves, desactivar."
date: 2011-04-27
forum: Software
---

### Post by javiermartinezv on 2011-04-27
Señores: agradeceré me ayuden en esto. Recién tengo una semana instalado Ubuntu y aún hay algunas cosas que quedo pillo. 
Por ejemplo, no sé por qué ni cómo, cada vez que recién entro al escritorio me sale una ventana señalándome que ingrese la clave para desbloquear el "depósito de claves"...
Asumo que es donde se conservan todas las claves que uso, pero.... es necesario que me pregunten SIEMPRE la clave de desbloqueo del depósito??? Puedo desactivar esta opción? 
Es molesto ingresala cada vez. 
Muchas gracias. 
Saludos.

Javier Martínez.

---

### Post by ivanovnegro on 2011-04-27
Pues, esta clave es importante para administrar el sistema, desinstalar, instalar programas, jugar con las configuraciones.
Yo, no la desactivaría pero se puede.
Es una parte importante de Linux en general.

---

### Post by bichopro on 2011-04-27
No es normal que te la pida siempre. 
Lugares / Carpeta de usuario (cambia según el nombre de tu usuario).
Dentro presionamos Control + H para ver las capetas y archivos ocultos. Buscamos la carpeta .gnome2, ingresamos a keyrings y eliminamos el archivo default.keyring.

Eso soluciona el error de contraseñas guardadas, ya que elimina la contraseña del anillo directamente. Se puede asignar una nueva o hacer lo que hice yo, dejarlo vacío y asignarlo como depósito de contraseñas inseguro.

---

### Post by 3nG3ndR0 on 2011-04-27
> **javiermartinezv said:**
> Señores: agradeceré me ayuden en esto. Recién tengo una semana instalado Ubuntu y aún hay algunas cosas que quedo pillo. 
Por ejemplo, no sé por qué ni cómo, cada vez que recién entro al escritorio me sale una ventana señalándome que ingrese la clave para desbloquear el "depósito de claves"...
Asumo que es donde se conservan todas las claves que uso, pero.... es necesario que me pregunten SIEMPRE la clave de desbloqueo del depósito??? Puedo desactivar esta opción? 
Es molesto ingresala cada vez. 
Muchas gracias. 
Saludos.

Javier Martínez.

es una lata ese mensaje lo desactivas como dicen aquí [link]("http://ubuntuparatodos.wordpress.com/2010/05/05/quitar-el-dialogo-desbloquear-el-deposito-de-inicio/") esta bien detallado con fotos y todo

---

### Post by Killer Jacker on 2011-04-29
> **bichopro said:**
> No es normal que te la pida siempre. 
Lugares / Carpeta de usuario (cambia según el nombre de tu usuario).
Dentro presionamos Control + H para ver las capetas y archivos ocultos. Buscamos la carpeta .gnome2, ingresamos a keyrings y eliminamos el archivo default.keyring.

Eso soluciona el error de contraseñas guardadas, ya que elimina la contraseña del anillo directamente. Se puede asignar una nueva o hacer lo que hice yo, dejarlo vacío y asignarlo como depósito de contraseñas inseguro.
A mi me pasaba lo mismo, pero hice lo mismo que Bichopro. Al final lo dejé como depósito de claves inseguro, con clave vacía. Cuando le cambies la clave, la dejas en blanco. De todos modos hay otras formas de asegurar tus datos personales, como encryptar tu cuenta y espacio de usuario. ;)

---

### Post by YA§uOtL]gS7y£xpj}R on 2011-11-05
> **3nG3ndR0 said:**
> es una lata ese mensaje lo desactivas como dicen aquí [link]("http://ubuntuparatodos.wordpress.com/2010/05/05/quitar-el-dialogo-desbloquear-el-deposito-de-inicio/") esta bien detallado con fotos y todo
Gracias por el aporte.:D

---

### Post by moreback on 2012-01-25
De seguro les pide clave para el depósito porque configuraron el login automático.

---


---
title: "Cambiar ext3 por ext4 en partición /home"
date: 2010-06-06
forum: Software
---

### Post by jorval on 2010-06-06
Última pregunta antes de instalar Ubuntu 10.04 (espero).  En mi PC y Notebook tengo instalado Ubuntu 8.04 en 3 particiones: raíz, home y swap. 

Al instalar ahora Ubuntu 10.04 desde un live CD tengo entendido que en la partición raíz tendré por defecto el sistema de archivos ext4 pero ¿que hago con la home? Sé que puedo continuar con ext3, pero si deseo cambiar a ext4 ¿que tengo que hacer al instalar el SO? ¿Sencillamente le pongo ext4 a la home? O tengo que hacer algo más. 

Desde ya muy agradecido.

---

### Post by Thalskarth on 2010-06-06
> **jorval said:**
>  ¿que tengo que hacer al instalar el SO? ¿Sencillamente le pongo ext4 a la home? O tengo que hacer algo más. 

Al instalar el SO, deberías marcar la particion de /home como /home para que Ubuntu sepa y la reconozco como tal, aunque quede en ext3.
No te conviene marcarla como ext4 durante la instalación, porque estarías formateandola y se borrará todo lo que alla en ella (salvo que esa sea tu intencion).

Lo mejor es que instales todo normal, marcando solo que la reconozco como /home pero sin formatearla o que desde el livecd ejecutes un comando que te transforma de ext3 a ext4 sin borrar nada y luego isntales
Acá en este link está bien explicado paso a paso: [http://temasvariados.wordpress.com/2010/04/08/de-ext3-a-ext4/](http://temasvariados.wordpress.com/2010/04/08/de-ext3-a-ext4/)

---

### Post by jorval on 2010-06-08
Gracias Thalskarth. Instalé Ubuntu 10.04 dejando /home con ext3. Seguro que para la próxima LTS el cambio será automático. Saludos.

---


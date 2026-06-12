---
title: "[SOLUCIONADO] Privilegios de usuario"
date: 2009-06-14
forum: Software
---

### Post by ParamDaya on 2009-06-14
[FONT=Georgia][SIZE=2][B]Estimados

Soy nuevo en el mundo de Ubuntu y necesito su ayuda para que me digan como puedo tener los privilegios necesarios para crear y modificar carpetas que son root u de otra propiedad que no me permite hacer nada.

Resulta que necesito crear una carpeta en /media y no me deja, porque mi usuario no tiene los privilegios para hacerlo.

Que puedo hacer?

Gracias....[/B][/SIZE][/FONT] :p

---

### Post by Carlos C on 2009-06-14
Para eso debes usar "sudo". Por ejemplo si quieres crear una carpeta llamada "Disco_Externo" en /media debes escribir en el terminal:
```
sudo mkdir /media/Disco_Externo
```
Te recomiendo que te informes bien cómo funciona "sudo" ya que corres el riesgo de estropear tu sistema. Por esta razón te sugiero que leas lo que dice la Guía Ubuntu al respecto:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

---

### Post by ParamDaya on 2009-06-14
> **Carlos C said:**
> Para eso debes usar "sudo". Por ejemplo si quieres crear una carpeta llamada "Disco_Externo" en /media debes escribir en el terminal:
```
sudo mkdir /media/Disco_Externo
```Te recomiendo que te informes bien cómo funciona "sudo" ya que corres el riesgo de estropear tu sistema. Por esta razón te sugiero que leas lo que dice la Guía Ubuntu al respecto:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

[FONT=Georgia][SIZE=2][B]Muchas gracias...... funciono sin problemas su instrucción...... 

Ahora, a seguir aprendiendo.....[/B][/SIZE][/FONT]

---

### Post by moreback on 2009-06-15
No es por nada pero creo que crear directorios a manopla en /media no es correcto, ya que lo mejor es montar particiones con **gnome-mount**.

---

### Post by pagondel on 2009-06-17
> **moreback said:**
> No es por nada pero creo que crear directorios a manopla en /media no es correcto, ya que lo mejor es montar particiones con **gnome-mount**.
Si se desea montar un dispositivo de forma temporal, se puede usar /mnt ;) y de esa forma no crear un directorio dentro de /media y despues borrarlo

---


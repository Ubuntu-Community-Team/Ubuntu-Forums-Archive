---
title: "Impresora PDF y permisos"
date: 2009-12-22
forum: Software
---

### Post by quethzel on 2009-12-22
[SIZE=4]hola soy nuevo en ubuntu e instalar la impresora de tipo PDF.
el problema es q la carpeta en la q guarda los archivos no puedo acceder a ella por q dise q no soy el propietario. En propiedades dise  q el propietario es root y las opciones de abajo estan deshabilitadas ¿Saben como puedo entrar ?[/SIZE]
:confused:

---

### Post by euzkoarima on 2009-12-22
Sugiero cambiar el propietario desde consola. Para ello selecciona menú aplicaciones -> Accesorios -> Terminal

Ahi escribi
```
cd 
```

(ojo: hay un espacio en blanco, necesario, atrás de cd) y luego arrastrás con el mouse la carpeta del problema a la pantalla del terminal, te tiene que quedar algo como
```
wado@Excalibur:~$ cd '/home/wado/PDF' 

```

dale enter y luego ingresa

```
sudo chown vos:vos .
```

pero reemplazando donde dice 'vos' por tu nombre de usuario, que dicho sea de paso es lo que aparece primero en la línea. En el ejemplo que dí arriba, mi usuario es 'wado'

Te va a pedir una clave, es la misma que usas para ingresar cuando inicias sesión.

No se si tenés o no archivos en ese directorio, si fuera el caso, y tampoco tenés permisos, lo cambias poniendo en la consola:

```
sudo chown vos:vos *
```

Valen las mismas aclaraciones sobre 'vos'

Saludos,
Eduardo

---


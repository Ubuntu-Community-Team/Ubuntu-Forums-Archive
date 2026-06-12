---
title: "HOLAA!! Ayuda con el bash"
date: 2008-08-01
forum: Software
---

### Post by bfharreguy on 2008-08-01
HOla, como estan ? tengo una duda sobre el bash, tengo un programa que solo funciona con mi usuario, pero si lo ejecuto como root, no funciona, la idea es ejecutar este programa cuando inicia el sistema, si lo coloco en una linea del inicio, se ejecuta pero tira error porque no es el usuario correcto. Hay alguna forma de poder ejecutar esta aplicacion bajo bash con un determinado usuario?? es decir, que la ejecucion se cumpla con otro usuario, con algun comando?? como lo hago saludos!!!:popcorn:

---

### Post by sergiom99 on 2008-08-01
creo que podes poner:
```
 su usuario programa.sh
```
ahora no tengo la compu como para probarlo.
Suerte.

---

### Post by brunovecchi on 2008-08-02
No entiendo bien tu situación... si el script funciona cuando lo ejecutás con "tu" usuario y no el root, bastaría con agregar tu script en Sistema->Sesiones->Programas de inicio.
Eso debería hacer que tu script se ejecute al iniciar el sistema y bajo tu usuario, por lo que no debería dar ningún error. Asegurate antes de hacer a tu script ejecutable con:

```
chmod +x nombre_de_tu_script.sh 
```

---


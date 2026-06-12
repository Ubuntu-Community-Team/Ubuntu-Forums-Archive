---
title: "Cheese no funciona"
date: 2011-05-09
forum: Software
---

### Post by vrolok on 2011-05-09
Hola, bueno, aqui estoy otra vez pidiendo su ayuda.
Lo que pasa es que quise grabar un video con mi webcam en ubuntu 10.04, y me di cuenta que no tenia instalado ningun paquete para hacerlo, asi que decidi instalar cheese.
Lo instale y en la terminal no me marco ningun error.
Entonces a la hora de abrir cheese sale una ventana con una pantalla negra y se enciende el led de mi webcam y como a los 5 segundos que hace esto el programa se cierra solo y obviamente no puedo grabar ni tomar fotos. No se que hacer y tampoco se que informacion necesiten para ayudarme. Por lo pronto les digo que mi ubuntu es Ubuntu 10.04.1 LTS de 32 bits, mi maquina es Toshiba Satelllite y mi webcam esta integrada a la maquina.

---

### Post by Sortega on 2011-05-09
Hola, ejecuta cheese por terminal y pega lo que te genera aca, para poder ver si arroja algún error o algo por el estilo.

Saludos

---

### Post by 3nG3ndR0 on 2011-05-09
a mi cheese no me graba bien los vídeos los graba cortado, y no e encontrado solución alguna

---

### Post by silex89 on 2011-05-10
Solía tener el mismo problema con mi otrora laptop, en ese tiempo usaba Feisty y la soluciónque le dí fue recompilar el kernel jajaja xD, luego de hacer modprobes y otros trucos más.

Espero no sea tu caso, por lo menos tienes una buena señal: La camara es detectada, lo que significa que el driver está instalado y "funcionando". Quizá solo sea un tema de compatibilidad entre tu webcam y el programa....


Suerte!

---

### Post by vrolok on 2011-05-16
Bueno, antes ke nada kiero diskulparme por kontestar hasta ahora, lo ke pasa es ke no habia tenido oportunidad de konektarme a internet y por eso no habia visto el foro.

Bueno, ejekute cheese desde terminal y esto es lo ke me arrojó:
```

progname=cheese; RGBA=on
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 81 error_code 8 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Bueno eso es todo.

---

### Post by RafaelG on 2011-05-17
Vrolok;

Creo que el siguente link te ayudara con tu problema, revisalo y nos avisas como te fue.

[http://zaybort.linuxerz.org/2011/02/problemas-con-el-cheese/](http://zaybort.linuxerz.org/2011/02/problemas-con-el-cheese/)

Saludos,

---

### Post by vrolok on 2011-05-17
Gracias por el link RafaelG, lo revise e hice lo ke indikaban y se solucionó mi problema, muchas gracias!!!

---

### Post by RafaelG on 2011-05-17
> **vrolok said:**
> Gracias por el link RafaelG, lo revise e hice lo ke indikaban y se solucionó mi problema, muchas gracias!!!

Otra Maquina Libre!

---


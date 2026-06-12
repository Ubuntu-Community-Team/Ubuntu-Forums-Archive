---
title: "Log de Escritorio Remoto"
date: 2008-10-24
forum: Software
---

### Post by wittycasla on 2008-10-24
Puedo hacer Escritorio remoto sin problemas hacia mi Ubuntu.

Quisiera saber dónde queda un log de las conexiones a mi Ubuntu.

Gracias.-

---

### Post by hictio on 2008-10-24
Hay varios programas para ver conexiones (e intentos de) a tu maquina Linux, yo conozco los que funcionan en el Terminal, pero seguramente haya alguna version con GUI.

La data en si se guarda en el directorio '/var/log/' fundamentalmente en el archvio 'auth.log' (un archivo de texto plano); y en el archivo 'wtmp' (en forma binaria).

Para verlos, abri un Terminal, y tipea:
```

last | less

```

Una parte del mio:
```

esteban  pts/2        10.120.10.3      Sat Oct 25 00:06   still logged in   
esteban  pts/1        :0.0             Fri Oct 24 23:58   still logged in   
esteban  pts/1        :0.0             Fri Oct 24 20:48 - 21:33  (00:45)    
esteban  pts/6        :0.0             Fri Oct 24 20:06 - 20:31  (00:24)    
esteban  pts/6        :0.0             Fri Oct 24 19:26 - 20:02  (00:36)    
esteban  pts/5        :0.0             Fri Oct 24 19:03   still logged in   
esteban  pts/4        :0.0             Fri Oct 24 18:37 - 21:09  (02:32)    
esteban  pts/1        :0.0             Fri Oct 24 17:21 - 20:34  (03:13)    
esteban  pts/5        :0.0             Fri Oct 24 10:57 - 10:58  (00:00)    
esteban  pts/4        :0.0             Fri Oct 24 10:57 - 16:39  (05:42)    
esteban  pts/3        :0.0             Fri Oct 24 10:23 - 23:37  (13:13)    
esteban  pts/2        :0.0             Fri Oct 24 10:23 - 23:37  (13:13)    
esteban  pts/1        :0.0             Fri Oct 24 10:21 - 16:39  (06:17)    
esteban  pts/0        :0.0             Fri Oct 24 04:16   still logged in   
esteban  tty3                          Fri Oct 24 04:13   still logged in   
esteban  tty3                          Fri Oct 24 04:13 - 04:13  (00:00)    
reboot   system boot  2.6.24-19-generi Fri Oct 24 04:13 - 00:14  (20:00)    

```

Para salir del programa, tipeas 'q'.
El otro es 'lastlog' que te muestra cuando es la ult. vez que se loggeo alguien a la maquina.

Y tambien tenes 'faillog', para ver si algun usuario tuvo problemas al loggearse.

---

### Post by wittycasla on 2008-10-26
Muchas gracias... ahora me llama la atención que mi resultado sea tan corto, comparado al tuyo...

wittycas pts/0        :0.0             Sun Oct 26 13:24   still logged in   
wittycas pts/0        :0.0             Sun Oct 26 13:20 - 13:21  (00:00)    
wittycas pts/0        :0.0             Sat Oct 25 12:51 - 12:57  (00:06)    
wittycas pts/0        :0.0             Sat Oct 25 10:50 - 11:05  (00:14)    

Gracias otra vez.

---

### Post by hictio on 2008-10-26
Me imagino que es porque en mi maquina desactive el login grafico, me gusta bootear a consola, especialmente en Ubuntu, porque se puede poner facil con alta resolucion, ademas, uso muchisimo el Terminal por trabajo, y cada Terminal que abre lo registra como un login.
Abrite un par de Terminales (Alt + F2 tipea gnome-terminal ENTER, hacelo un par de veces) y despues tipea de vuelta 'last'.

---


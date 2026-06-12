---
title: "No puedo descomprimir archivos"
date: 2009-11-18
forum: Software
---

### Post by WooS on 2009-11-18
Estaba queriendo instalar el songbird pero me encuentro con un problema que ya lo he querido solucionar antes pero no le encuentro la vuelta. Cuando quiero descomprimir desde la terminal me sale esto
woos@woos-laptop:~$ tar -xvvzf Songbird_1.2.0-1146_linux-i686.tar.gz
tar: Songbird_1.2.0-1146_linux-i686.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores

Alguien sabe xq pasa eso?

---

### Post by Mauro22 on 2009-11-18
> **WooS said:**
> 
tar: Songbird_1.2.0-1146_linux-i686.tar.gz: No se puede open: No existe el fichero ó directorio

Hola!!


Más explicito el error, imposible... fijate si estas en la misma carpeta y el archivo 1) está ahi; 2) se llama asi.

---

### Post by matias_tati on 2009-11-18
> **WooS said:**
> Estaba queriendo instalar el songbird pero me encuentro con un problema que ya lo he querido solucionar antes pero no le encuentro la vuelta. Cuando quiero descomprimir desde la terminal me sale esto
woos@woos-laptop:~$ tar -xvvzf Songbird_1.2.0-1146_linux-i686.tar.gz
tar: Songbird_1.2.0-1146_linux-i686.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores

Alguien sabe xq pasa eso?

Y para que desde la consola? Con un click derecho/extraer aqui y listo!!!
Saludos!!!

---

### Post by santiagoward2000 on 2009-11-18
> **WooS said:**
> Estaba queriendo instalar el songbird pero me encuentro con un problema que ya lo he querido solucionar antes pero no le encuentro la vuelta. Cuando quiero descomprimir desde la terminal me sale esto
woos@woos-laptop:~$ tar -xvvzf Songbird_1.2.0-1146_linux-i686.tar.gz
tar: Songbird_1.2.0-1146_linux-i686.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores

Alguien sabe xq pasa eso?

Hola!
El error dice que el archivo no se encuentra. El **~** que hay en la terminal quiere decir que estás en tu **Home**. ¿El archivo lo bajaste a tu home, o está en otra carpeta? Si está en otra carpeta, tenés que ir a donde lo bajaste con el comando **cd**. Por ejemplo, si lo bajaste a la carpeta **Downloads** (ubicada dentro de tu home), hacés:
```
cd ~/Downloads
```
y ahí tendrías que poder descomprimirlo sin problemas.

_Para más información:_
[Explicación por Staar.]("http://ubuntuforums.org/showpost.php?p=8058308&postcount=5")
Saludos!

---


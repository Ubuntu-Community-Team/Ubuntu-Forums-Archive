---
title: "[SOLUCIONADO] Problemas con los videos en la web!!!"
date: 2009-07-11
forum: Software
---

### Post by pelaolinux on 2009-07-11
hola de nuevos a todos !!! 
necesito ayuda, tengo problemas con los vídeos de las paginas como los de youtube y de otras paginas que solamente se me escucha  el sonido y la pantalla donde muestra el vídeo aparese en blanca, ni siquiera aparese el reproductor con el video y al rato se me queda congelado el firefox en gris :S . quien sabe por q me susede eso y como lo puedo solucionar ???? 

Saludos querido amigos de team chile ubuntu !!! ;)

---

### Post by moreback on 2009-07-11
Remueve los paquetes swfdec-mozilla y mozilla-plugin-gnash e instala flashplugin-installer.

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
sudo apt-get install flashplugin-installer
```

---

### Post by CdK1 on 2009-07-11
sudo apt-get install flashplugin-nonfree

---

### Post by pelaolinux on 2009-07-11
Muchas gracias por la ayuda... ):P
saludos!

---

### Post by pelaolinux on 2009-07-11
> **moreback said:**
> Remueve los paquetes swfdec-mozilla y mozilla-plugin-gnash e instala flashplugin-installer.

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash
sudo apt-get install flashplugin-installer
```


muchas gracias [moreback]("http://ubuntuforums.org/member.php?u=633286") !!! 
ahora me funciona todo los videos correctamente .... 
saludos!!!

---


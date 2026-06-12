---
title: "mplayer codecs &amp; demuxers"
date: 2008-12-26
forum: Software
---

### Post by User21 on 2008-12-26
A la hora de ver mis peliculas y series, noto un ligero desplazamiento inapropiado en la reproducción de los archivos. En su mayoría, son todos videos AVI / DivX / XVid. Es como si el video fuese pegado por pedazos, rapidamente. Durante mucho tiempo no le di importancia, pero se torna molesto en tomas rapidas y quiero finalmente solucionarlo. No encontre una respuesta acertada. [**Aqui**]("http://ubuntu-ar.org/themes/website2007/images/TwinViewenUbuntu.jpg") tienen un ejemplo de lo que me refiero. 
Tiene algo que ver con los codecs & demuxers? Alguno que haya solucionado este problema. No es problema ni de memoria ni procesador ni nada similar.

---

### Post by KrossX on 2008-12-27
Ah, eso es "tearing". Es provocado por la falta de sincronía con el tiempo de renderizado de la imagen (es independiente del video y de los codecs).

Como veo que tienes el driver nVIDIA, si usas el render XV en el reproductor, asegúrate de tener Sync to VBlank para XV en el panel de nVIDIA activado. Prueba desactivándolo también, en caso que haya algún conflicto.

---


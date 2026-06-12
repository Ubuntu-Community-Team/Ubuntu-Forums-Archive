---
title: "Tamaño de la ISO en DVD"
date: 2012-05-18
forum: Software
---

### Post by drazhe on 2012-05-18
Hola Comunidad, estoy descargando la iso del dvd de Ubuntu 12.04 LTS Precise Pangolin, y me encuentro que el tamaño del archivo es de solo 1.5gb cuando el de las anteriores solia ser de 4Gb y pico más o menos... 

¿Está bien ese tamaño para la ISO del DVD? ¿está completa? porque en lo personal me parece poco en comparación con las anteriores... además de que recuerdo haber leído notas donde hablaban que las iso de los cds iban a pasar de 700 a 750mb y que el DVD lo reduzcan tanto me hace pensar que le han quitado muchisimos paquetes...

---

### Post by hictio on 2012-05-19
Nunca bajé los ISOs para DVD hasta ahora, siempre bajé los ISOs para CD, y hace tiempo que no los quemo, sino que lo uso desde USB.
Pero, lo mejor, independientemente que bajes CD o DVD, es que una vez hayas terminado la descarga hagas un chequeo MD5sum del archivo y o compares con los que tienen en la [página web](https://help.ubuntu.com/community/UbuntuHashes) para descartar una descarga corrupta.

Para comparar, en Linux, lo único que tenés que hacer, una vez que el ISO terminó de descargar, abrí un Terminal, hacé cd al directorio donde está el ISO y:

```

md5sum imagen.iso ENTER

```

Va a tardar unos minutos, dependiendo de la velocidad de tu máquina y del tamaño dle ISO, y tiene que retornar un string, compará ese string con los de la página web, especificamente con el de la imagen que descargaste, tienen que ser exactamente igual.

---

### Post by drazhe on 2012-05-19
> **hictio said:**
> Nunca bajé los ISOs para DVD hasta ahora, siempre bajé los ISOs para CD, y hace tiempo que no los quemo, sino que lo uso desde USB....



el cheksum esta correto, pero me llamó mucho la atención el adelgazamiento que tuvo el DVD, porque de 4.2gb que tenía lucid por ejemplo, pasó a 1.5gb de Precise... es evidente que sacaron muchisimos paquetes.. y la idea del DVD es justamente tenerlos encima para no bajarlos de internet...

---


---
title: "Problemas de resolucion de video"
date: 2009-12-18
forum: Venezuela Team
---

### Post by DMNUX on 2009-12-18
Saludos,soy nuevo en linux y necesito ayuda.tengo una tarjeta de video nvidia geforce fx 5200,la resolucion no pasa de 800x600 o menos,como puedo hacer?he tratado de instalar la version mas reciente de drivers (version 173) pero la hacerlo la resolucion solo me toma hasta 640x480,entonces vuelvo al driver anterior para que al menos me tome la resolucion de 800x600

---

### Post by CdK1 on 2009-12-22
Debes configurar tu xorg.conf para darle otra resolución, ej.-

    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes       "1280x1024"
    EndSubSectio

---


---
title: "LinuxSampler"
date: 2009-04-17
forum: Software
---

### Post by NickCis on 2009-04-17
Hola, despues de buscar mucho por google, pude instalar el LinuxSampler, usando la guia del mismo sitio (si ya se ustedes diran, que soy medio bolu, por no fijarme en la pagina por una guia pero bueh).
Guia: [http://www.linuxsampler.org/debian.html](http://www.linuxsampler.org/debian.html)

El problema, es que para usar este programa tenes que compilar el libgig. En la pagina te explica como crear el deb y todo lindo. Al compilarlo, se te general 3 debs, libgig libgig-dev y gigtools. 

El problema es que libgig entra en conflicto con el libgig6 (que si usas este, no podes instalar el linuxsampler, por que te dice que libgig no ta instalado) de los repositorios.
 
Entonces si yo actualizo mis programas via comando "apt-get dist-upgrade", me dice que los programas libgig-dev y gigtools, no cumplen las dependencias y se nececita instalar libgig6.
Acto seguido, intenta instalar libgig6, pero entra en conflicto con libgig entonces no lo instala. Diciendo que tenes que solucinar los problemas con el comando "apt-get -f install". Ejecutando ese comando te devuelve el mismo problema con la misma supuesta solucion.
Ademas, por este "conflicto de dependecias" no puedo usar el aptitude (ya que siempre me dice que tengo que ejecutar "apt-get -f install").
Mi solucion momentaria fue desinstalar todo, y volverlo a instalar, absteniendome de actualizar.

Como puedo arreglar este supuesto "problema de dependencias"?.

Saludos.

---


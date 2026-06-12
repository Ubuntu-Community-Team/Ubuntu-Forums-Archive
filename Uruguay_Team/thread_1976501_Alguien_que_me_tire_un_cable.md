---
title: "Alguien que me tire un cable"
date: 2012-05-08
forum: Uruguay Team
---

### Post by xGrp on 2012-05-08
Saludos amigos del foro

Resulta que para un proyecto de Virtualización en mi trabajo se me hace necesario munirme de un par de direcciones de IP

Los administradores de la Red me dicen que tienen las direcciones agotadas u.u

Yo estuve mirando la configuración de algunas maquinas y me encuentro que usan el tipo de red de clase A con una mascara de 24 bit

ej 10.RRR.RRR.HHH

ME GUSTARIA QUE ALGUIEN DEL FORO ME CONFIRME SI MI PENSAMIENTO ES CORRECTO

según el ejemplo anterior

tengo 16 bit para utilizar ya que el primer octeto no varia nunca y el ultimo octeto me queda para los host

de acuerdo a mis calculos ese sistema en base a la mascara que vi en varias maquinas
(255.255.255.0)

me da la pauta de combinar los 16 bit que tengo (2do y 3er octeto)

o sea 255*255 =  65025 subredes de 254 host c/u

ALGUIEN DE QUE ME INDIQUE SI MI PENSAMIENTO ES CORRECTO  POR FAVOR (quiero saber si el ignorante soy yo)

Desde ya gracias

---

### Post by guillermolisi on 2012-05-09
No se si interpreto bien tu pregunta, pero con una mascara para red Clase B 255.255.255.0 solo tenes posibilidad para 254 hosts (el 255 se reserva para broadcasting) que corresponden al octeto enmascarado con 0 (cero).

Por otra parte y mas alla de tus calculos, habria que ver como esta planteada la topologia de la red y como se estan administrando las redes y subredes a nivel IP y sus mascaras. Que obtengas resultados que interpretas como que aun quedan posibilidades de direcciones libres no necesariamente significa que sea asi el asunto en realidad.

---

### Post by xGrp on 2012-05-09
MMM entonces por lo que comentas yo no estaría tan errado en la teoría, el tema pasa que yo no me dedico a las redes pero para desarrollar sé al menos lo mas básico, en el anunciado anterior daría la pauta de que esa red está mal hecha ya que utilizan mascaras de clase C en redes de clase A, por eso mi duda si realmente está mal hecha o fue creada así a proposito. y si la falta de direcciones se debíera a un desconocimiento de los recursos, pero lo mío es teoría como tu mencionas y creo que no se pueden agotar las direcciones teniendo tantas posibilidades de ampliar los nodos bastaría con colocar un nuevo router. pero quería una opinion ya que me manejo por la lógica 
 
perdon si no me exprese bien antes. estamos en contacto

---

### Post by guillermolisi on 2012-05-09
Correcto, estan enmascarando de esa forma la red y no podria decirte si esta bien o mal ya que eso depende mucho de lo que mencione antes respecto de como esta armada y como la administran (generalmente en base a conocimientos y a recursos - lease switches, VLANs, cableado, funcionalidad de servicios en la red, etc.)

---


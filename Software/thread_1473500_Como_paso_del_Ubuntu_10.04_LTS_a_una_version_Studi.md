---
title: "Como paso del Ubuntu 10.04 LTS a una version Studio?"
date: 2010-05-05
forum: Software
---

### Post by adriano_seth on 2010-05-05
Hola muchachos, quisiera saber si existe la posibilidad de transformar el ubuntu 10.04 en el Ubuntu Studio, ya que este ultimo lo conozco un poco mejor. Otra cosa que quisiera saber es si instalando una version anterior de ubuntu puedo tener mayor compatibilidad con mi chipset Intel GMA500 ya que en este momento me causa muchos problemas. Muchas gracias por todo.

---

### Post by guillermolisi on 2010-05-05
> **adriano_seth said:**
> Hola muchachos, quisiera saber si existe la posibilidad de transformar el ubuntu 10.04 en el Ubuntu Studio, ya que este ultimo lo conozco un poco mejor. Otra cosa que quisiera saber es si instalando una version anterior de ubuntu puedo tener mayor compatibilidad con mi chipset Intel GMA500 ya que en este momento me causa muchos problemas. Muchas gracias por todo.
Para pasar a la version Studio tendiras que cambiar el kernel.
Ubuntu viene con la veriante Generic y Studio usa la RT (Real Time).

Tanto esto como el agregado de los programas propios de Studio se pueden hacer utilizando Synaptic y/o el Centro de Software.

Respecto de la placa de video, te pasara lo mismo que estas experimentando ahora ya que los drivers de video estan en el kernel y el cambio de Generic por RT no altera esa cuestion.

---


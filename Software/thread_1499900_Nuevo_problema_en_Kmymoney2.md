---
title: "Nuevo problema en Kmymoney2"
date: 2010-06-02
forum: Software
---

### Post by Brath-ga on 2010-06-02
Estoy usando el Kmymoney versió 1.0.4 y tengo el siguiente problema con los asientos planificados:

Tengo planificado el pago de varias tarjetas de crédito en el apartado de _Transferencias_.

Hace poco edité una de ellas y no se porqué se me pasó al apartado de _Recibos_.

Comprobé que las que están bien, tienen la siguiente descripción:
Método de pago : Depósito en cuenta y están consideradas como transferencias.
Pero esta en concreto que se me movió está igual lo de depósito en cuenta pero no me deja considerarla como Transferencia, solo me deja como Depósito o como Retirada.

Espero que alguien pueda ayudarme.

---

### Post by Hei Ku on 2010-06-02
Si editas la cuenta/categoria a la que vas a pasar la plata, y le pones una cuenta de activo o pasivo, te va a cambiar a transferencia automaticamente.

---

### Post by Brath-ga on 2010-06-04
Gracias, Hei Ku, pero no entiendo bien.

Se trata de pagos mensuales de tarjetas de crédito y las cuentas ya están en la categoría de Pasivos, cuentas por pagar.
Al editarlas no tengo nada que cambiar pues está bien.

---

### Post by Brath-ga on 2010-06-04
Creo que veo en donde está el problema.
Los dos asientos planificados den donde tengo el problema son asientos múltiples, es decir, con gastos a mayores ( seguro de pagos ).
Sin embargo las que no me dan problemas, son asientos con solo una linea.

---

### Post by Hei Ku on 2010-06-04
Una transferencia es solo cuando las cuentas involucrados son activos o pasivos. Si hay categorias de ingresos o gastos, pasa a ser un recibo o deposito. Esto es automatico.
Si es una cuenta multiple, en cuanto agregas una categoria corre la misma regla, y se cambia automaticamente a recibo o deposito.

---

### Post by Brath-ga on 2010-06-08
Gracias Hei Ku.

Supuse que era de eso, tendré que reprogramar los asientos de otra forma.

---

### Post by Hei Ku on 2010-06-08
Y cual es el problema, salvo la clasificacion?

---

### Post by Brath-ga on 2010-08-26
Hei ku.

La clasificación es importante a nivel visual en asientos programados, pero aparte, el comportamiento del propio asiento para los informes, es completamente diferente.

---


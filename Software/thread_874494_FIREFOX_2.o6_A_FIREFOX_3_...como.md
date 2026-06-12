---
title: "FIREFOX 2.o6 A FIREFOX 3 ...como ??"
date: 2008-07-30
forum: Software
---

### Post by leonardo83 on 2008-07-30
Buenas, estoy usando Gutsy y hasta ahora no encontre la necesidad de pasarme a Hardy, pero quiero actualizar firefox, me descargue el archivo .tar.gz de la pagina de mozilla, me pueden decir como hago para actualizarlo? por defecto en gutsy la opcion de Upgrade viene deshabilitada :(

Gracias! Saludos:)

---

### Post by Hei Ku on 2008-07-30
salvo que hayan hecho la actualizacion de los repositorios, no hay manera de hacer un upgrade. Lo que podrias hacer es desinstalar el de Gutsy y usar el que te bajaste de la pagina de Mozilla. Son dos cosas totalmente diferentes.

---

### Post by Aspergillus on 2008-07-30
O bien podes tener los dos funcionando en la maquina, no te van a crear conflicto ni nada, lo que haces es descomprimir el tar con el firefox 3 en una carpeta en tu home ponele que se llame Firefox mismamente y ejecutas el navegador desde el mismo ejecutable de firefox en esa carpeta, cuando te lo habra la primera vez te va a decir si queres convertirlo en el navegador por defecto, y meter los marcadores y demas cosas del firefox 2, haces todo eso y listo ya lo tenes funcionando

cualquier cosa si algun programa te sigue usando la version anterior lo que haces es ir al programa en cuestion y las opciones que tenga en alguna parte te tiene que dejar poner el navegador predeterminado para ese programa, le decis que use el firefox 3 poniendole la ruta de acceso y listo

espero que te funcione

---

### Post by rober-mpp on 2008-07-30
Una solucion media fea podria ser, agregar el repositorio de 8.04 que tenga ff3 a /etc/apt/sources.list, apt-get update, y sin actualizar nada mas ( para no romper nada ), apt-get install firefox-3. Logicamente despues borrar ese repo de la lista y hacer el update de nuevo, para evitar problemas con futuras instalaciones.

Creo que deberia andar.

Suerte!

---

### Post by Hei Ku on 2008-07-30
> **rober-mpp said:**
> Una solucion media fea podria ser, agregar el repositorio de 8.04 que tenga ff3 a /etc/apt/sources.list, apt-get update, y sin actualizar nada mas ( para no romper nada ), apt-get install firefox-3. Logicamente despues borrar ese repo de la lista y hacer el update de nuevo, para evitar problemas con futuras instalaciones.

Creo que deberia andar.

Suerte!

Si no depende de otra cosa, puede andar. Pero es feo, feo. Para eso te conviene ejecutarlo desde el tar.gz en tu home.

---

### Post by margori on 2008-07-30
> **leonardo83 said:**
> ... estoy usando Gutsy y hasta ahora no encontre la necesidad de pasarme a Hardy, pero quiero actualizar firefox...

Encontre que existe un paquete en el repositorio de backports de gutsy. Esta el paquete de Firefox 3 beta 4.

Lo que tenes que hacer es habilitar con "backports" en synaptic y actualizar la lista. Normalmente no hay problemas, pero vos decidis si tomas el riesgo de actualizar Gutsy a lo mas cercano a Hardy sin hacer cambio de distribución.

---

### Post by vampichoke on 2008-07-31
A mi me acaba de pasar algo bizarrisimo. 

tengo firefox 3. pero si lo cierro y lo vuelvo a abrir me aparece firefox2 O.º). cierro sesion abro de nuevo y me aparece q se actualizo. y otra vez tengo firefox 3... alguien sabe q onda?

o sea no me genera problemas. pero a veces es raro, jeje.

puede q sea q toke algo q me guarde las sesiones? no recuerdo haber pasado del fire3 al 2. 

q loco no? (si a alguien le paso o sabe digame asi me kedo con 1 solo firefox =)

---

### Post by leonardo83 on 2008-07-31
Bueno no pude lograr actulaizar el firefox, pero lo necesitaba porque hace unos dias me aparecia error solo en Hotmail porque me decia que el browser necesitaba actualizarse, ya fue, lo vere con Opera je.
Un abrazo y gracias por todo!

---


---
title: "configuracion de named"
date: 2010-04-28
forum: Software
---

### Post by sergiom99 on 2010-04-28
Hola gente,
tengo esta consulta que tal vez sea ligeramente OT, pero confio en su buena voluntad.

Tengo un server que entre otras cosas corre named para hacer de servidor DNS.
En la zona de un dominio, quiero hacer un subdominio (ya esta) y hacer un MX para que reciba mail para ese subdominio.

Ahora esta asi:
```

$TTL 86400
; Zone file for dominio.com.ar
;
; The full zone file
;
@       IN      SOA     ns1.dominio1.com.ar. hostmaster.dominio.com.ar. (
                        2010042208      ; serial, todays date + todays serial
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        1W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns1.dominio1.com.ar.       ; Inet Address of name server
                NS      ns2.dominio1.com.ar.       ; Inet Address of name server
                MX      10 mail.dominio.com.ar.  ; Primary Mail Exchanger
;
mail            A       200.80.88.42
www             A       200.80.88.43
ftp             A       67.228.181.146
cms             A       67.228.181.146

```

Entonces, yo lo que quiero hacer es que mail.dominio.com.ar sea el MX para el dominio y hacer un mail.cms.dominio.com.ar para que sea el MX para cms.dominio.com.ar. La web de cms.dominio.com.ar esta funcionando ok, pero no doy pie con bola con lo del mail.Probe varias configuraciones, se daran cuenta por el serial, pero no logre hacer que el mail lo dirija a ese servidor. (Probando, entre otras cosas, con mxtoolbox.com)

como tengo que armar el archivo de zona para lograrlo?

Gracias a todos por sus comentarios.
-Sergio

---

### Post by alfplayer on 2010-04-29
No estoy hábil con Bind, pero en ese archivo no aparece ningún registro para "mail.cms". Por lo menos faltaría un registro MX y otro A.

---

### Post by sergiom99 on 2010-04-30
lo habia probado, pero mxtoolbox.com no encontraba un mx para ese prefijo.
Y estaba preguntando a mi dns...

intento de nuevo entonces.

---


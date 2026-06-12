---
title: "IPTABLES y HTTPS (whitelisting)"
date: 2011-02-23
forum: Software
---

### Post by quedefantasma on 2011-02-23
Estimados, estoy luchando con el problema de administrar las conexiones https (443) en mi proxy de internet.

Como es sabido, Squid no puede filtrar este tipo de conexiones en modo transparente... por lo tanto, tengo usuarios navegando sitios no permitidos (ej. [https://facebook.com](https://facebook.com)) y probabilidad de encontrarme con ultrsurf...u otros indeseados.

Como la red solo necesita tener asegurados algunos sitios https (ej. bancos) estoy pensando en pasar mi firewall a DROP por defecto (hasta ahora no me animaba) y habilitar solamente algunos sitios incluidos en una whitelist (para no tener que crear una regla por cada sitio)

Estoy buscando como conformar este tipo de reglas en internet...pero no doy con el blanco.

Podría alguien orientarme? Donde se crearía dicha whitelist? Como hago que la regla "leea" esta lista?

Gracias de antemano, Saludos.

---

### Post by quedefantasma on 2011-02-24
Avanzando...(aun no funcionando)

Encontré un articulo que me esta guiando al objetivo, voy dejando los avances.

- El primer paso seria crear una cadena customizada (CUSTOM CHAINS)
[FONT=monospace]
[/FONT]iptables -N nombre_de_la_cadena (en mi caso: https_whitelist)

- Agregar una regla para la cadena, por ejemplo...
[FONT=monospace]
[/FONT]iptables -A https_whitelist -p tcp -s 192.168.0.0/24 -d banco.com.ar --ports 443 -j ACCEPT

- Finalmente especificar el destino de la cadena customizada en la seccion correspondiente
[FONT=monospace]
[/FONT]iptables -A FORWARD -j https_whitelist

Ahora voy a probar y corregir...

Comentarios, observaciones? Gracias a todos...slds.

---


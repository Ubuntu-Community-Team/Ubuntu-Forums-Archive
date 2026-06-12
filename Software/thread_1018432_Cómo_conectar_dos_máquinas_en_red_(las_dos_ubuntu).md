---
title: "Cómo conectar dos máquinas en red (las dos ubuntu)"
date: 2008-12-21
forum: Software
---

### Post by erdosain9 on 2008-12-21
Hola.  Para no abrir un nuevo tema... resulta que me quedé sin conexión... (Tendo dos máquinas que compartían la conexión a través de Firestarter) llamé a Fibertel y lo arreglaron pero ahora no puedo conectarme desde una de las máquinas (la cliente)... qué puede ser?????????
Mi nueva dirección ip es esta: 190.19.97.113
y la máscara es esta: 255.255.255.0
ruta predeterminada: 190.19.97.1

Cómo tendría que configurar ahora para que vuelva a funcionar mi máquina cliente...

Saludos y gracias

---

### Post by guillermolisi on 2008-12-21
> **erdosain9 said:**
> Hola.  Para no abrir un nuevo tema... resulta que me quedé sin conexión... (Tendo dos máquinas que compartían la conexión a través de Firestarter) llamé a Fibertel y lo arreglaron pero ahora no puedo conectarme desde una de las máquinas (la cliente)... qué puede ser?????????
Mi nueva dirección ip es esta: 190.19.97.113
y la máscara es esta: 255.255.255.0
ruta predeterminada: 190.19.97.1

Cómo tendría que configurar ahora para que vuelva a funcionar mi máquina cliente...

Saludos y gracias

Podrias reiniciar los servicios de red ejecutando en consola
```
sudo /etc/init.d/networking restart
```

como para que tome algun cambio que aun no registro.

Recorda que Firestater no es el firewall sino una interface grafica que te permite administrar iptables en forma amigable.

---


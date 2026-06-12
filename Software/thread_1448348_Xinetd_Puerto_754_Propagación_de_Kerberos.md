---
title: "Xinetd Puerto 754 Propagación de Kerberos"
date: 2010-04-06
forum: Software
---

### Post by romeroc24 on 2010-04-06
Hola, no puedo abrir el puerto 754/tcp con xinetd para la propagación de kerberos el servicio se llama krb_prop.

El archivo /etc/xinetd.conf tiene:

```

defaults
{

}

includedir /etc/xinetd.d

```

El archivo /etc/xinetd.d/krb_prop tiene:

```

service krb_prop
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        user            = root
        wait            = no
        server          = /usr/sbin/kpropd
}

```

Cuando hago:

```

$sudo nmap -sU -sT localhost

```

Aparecen algunos puertos menos el 754/tcp.

---


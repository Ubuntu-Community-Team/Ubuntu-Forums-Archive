---
title: "Ubuntu server 16.04.4 cannot update behind firewall"
date: 2018-08-30
forum: Server Platforms
---

### Post by azkara22 on 2018-08-30
I have a fresh install of Ubuntu server 16.04.4 LTS in a virtual machine behind the company's firewall at work but the system is unable to get updates via apt update.

I have connection with the DNS severs and I am able to resolve the IP addresses. The IT team have opened the port 80 outbound to the [http://es.archive.ubuntu.com]("http://es.archive.ubuntu.com/") and [http://security.ubuntu.com]("http://security.ubuntu.com/") repositories, but the system gets stuck connecting to the servers.

We've reviewed the firewall logs and it even lets the connection pass so it should be ok. I've tried to force IPv4 in case IPv6 was making some issues on the firewall but nothing.
```

jazkarate@vm-startstop:~$ sudo apt -o Acquire::ForceIPv4=true update
0% [Conectando a es.archive.ubuntu.com (91.189.88.152)] [Conectando a security.ubuntu.com (91.189.88.161)]

```
After some time I get the connection errors
```

jazkarate@vm-startstop:~$ sudo apt -o Acquire::ForceIPv4=true update
Err:1 http://es.archive.ubuntu.com/ubuntu xenial InRelease
  No se pudo conectar a es.archive.ubuntu.com:80 (91.189.88.162), caducó el tiempo para conexión [IP: 91.189.88.162 80]
Err:2 http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease
  No se pudo conectar a es.archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:3 http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease
  No se pudo conectar a es.archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
  No se pudo conectar a security.ubuntu.com:80 (91.189.91.26), caducó el tiempo para conexión [IP: 91.189.91.26 80]
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Todos los paquetes están actualizados.
W: Fallo al obtener http://es.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  No se pudo conectar a es.archive.ubuntu.com:80 (91.189.88.162), c
W: Fallo al obtener http://es.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  No se pudo conectar a es.archive.ubuntu.com:http: [IP: 91
W: Fallo al obtener http://es.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  No se pudo conectar a es.archive.ubuntu.com:http: [IP:
W: Fallo al obtener http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  No se pudo conectar a security.ubuntu.com:80 (91.189.91.26
W: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.

```

Thanks in advance,
Jon

---

### Post by darkod on 2018-08-30
1. Does the firewall need an incoming rule for the return traffic? Or is that allowed by default? If it is not allowed, you would need it.

2. The error message is listing the IPs. Have you tried creating a rule using the destination IP as opposed to URL? Maybe it doesn't translate something correctly.

3. To check for sure if the rule is not working as intended, the IT team can create temporary rule allowing all http traffic from that source server (not limiting it to any URL). If that works, then the problem is in the rule.

---

### Post by TheFu on 2018-08-31
Besides darkod's ideas, would setting a proxy help? APT will work over an http proxy.

---


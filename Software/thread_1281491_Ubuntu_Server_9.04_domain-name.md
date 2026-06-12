---
title: "Ubuntu Server 9.04 domain-name"
date: 2009-10-03
forum: Software
---

### Post by Fistandantilus on 2009-10-03
Hola a todos!

Tengo un problema para cambiar el nombre de dominio de un server y hace 2 dias que no puedo resolverlo.
El tema es asi, al intenter instalar el kerberos en la maquina toma la configuración de los paquetes como "default realm" el nombre de dominio de la maquina y realiza el resto de configuración en base de ese default realm.
Ahora bien, la maquina la tengo debajo de un router linksys que esta configurado con DHCP y como tengo internet por telecentro me retorna por dhcp que el dominio de la maquina es "CPE.TELECENTRO.NET.AR" ahora estoy cambiando el dominio en todos lados para q no me tome el de telecentro pero me sigue retornando siempre el mismo.
Q hize:

[LIST]
[*]Modifique la conf del router para que el dominio sea "linux.local" y sigue = q antes
[*]Cambien el archivo /etc/dhcp3/dhclient.conf y le saque de request "domain-name, domain-name-servers y domain-search" y se los puse a manopla.
[*]y modifique tambien /etc/hosts y le agregue la linea "127.0.0.1 userver.linux.local userver"
[/LIST]
pero cuando instalo el kerberos me sigue tirando como default real "CPE.TELECENTRO.NET.AR" y no se donde lo esta sacando. Para instalar el krb uso la siguiente linea:
sudo apt-get install krb5-kdc krb5-admin-server

y cada vez quiero probar si me cambio el dominio purgo el krb con la siguiente linea:
sudo apt-get pruge krb5-kdc krb5-admin-server; sudo apt-get autoremove

el autoremove lo hago para que me desintale un par de dependencia automaticas q me instalo antes. 

A su vez elimino todos los archivos de conf que encuentro(/etc/krb.conf, /etc/krb5-kdm/* y /var/lib/[otro dir q no me acuerdo el nombre]/*)

Probe tambien de desintalar el dhcp3-client y tocar el /etc/networking/interfaces a mano tambien pero en ese caso no me toma ningun dominio y revientan las configuraciones de los paquetes...

Despues de modificar la conf del router instale un server de prueba en una vm y me toma ahora por defecto el dominio linux.local por dhcp pero no voy a reinstalar el server... ya tengo levantado un dns, OpenLDAP, Apache y MySQL...

Alguna idea de donde me puede estar tomando el nombre de dominio?

Saludos!

PD: si hago "hostname -fqdn" me retorna userver.linux.local xq en ese caso me lo esta tomando de /etc/hosts
[LEFT]
[/LEFT]

---

### Post by Fistandantilus on 2009-10-04
Creo que encontre el problema pero no se como resolverlo.
Éste es el script "config" que esta dentro del paquete "krb5-config.deb"(dependencia de krb5-kdc):
```

#!/bin/sh

set -e

. /usr/share/debconf/confmodule || exit
db_version 2.0

db_get krb5-config/default_realm || true
if [ "x$RET" = "x" ] ; then
    if db_get krb4-config/default_realm && [ "x$RET" != "x" ] ; then
    db_set krb5-config/default_realm "$RET"
    else
    domain=`dnsdomainname 2>/dev/null || true`

    # This is a hack, copied from krb5.conf, since we don't have any files
    # when the config script runs.
    case "$domain" in
    media.mit.edu|*.media.mit.edu)           realm=MEDIA-LAB.MIT.EDU ;;
    csail.mit.edu|*.csail.mit.edu)           realm=CSAIL.MIT.EDU     ;;
    mit.edu|*.mit.edu)               realm=ATHENA.MIT.EDU    ;;
    whoi.edu|*.whoi.edu)               realm=ATHENA.MIT.EDU    ;;
    slac.stanford.edu|*.slac.stanford.edu) realm=SLAC.STANFORD.EDU ;;
    stanford.edu|*.stanford.edu)           realm=stanford.edu      ;;
    *)
        realm=`echo "$domain" | tr 'a-z' 'A-Z'`
        ;;
    esac
    db_set krb5-config/default_realm "$realm"
    fi
fi

# The following sed script is used to extract the default realm from the
# krb5.conf file.  It should be run with perl -lanF= and must not use any
# Perl not present in perl-base (since this package doesn't depend on Perl).
extract_realm='
    if (/^\s*\[libdefaults\]/i ... /^\s*\[(?!libdefaults).*\]/) {
        next unless /^[^#;]+=/;
        $F[0] =~ s/\s//g;
        $F[1] =~ s/\s//g;
        print $F[1] if $F[0] =~ /^default[-_]realm$/i;
    }
'

db_get krb5-config/read_conf || true
if [ -f /etc/krb5.conf ] && [ "$RET" = "true" ] ; then
    db_set krb5-config/read_conf false
    realm=`perl -lanF= -e "$extract_realm" /etc/krb5.conf`
    if [ -n "$realm" ] ; then
    db_set krb5-config/default_realm "$realm"
    fi
fi

db_input medium krb5-config/default_realm || true
db_input low krb5-config/dns_for_default || true

db_go

```Por lo que estuve leyendo, el script "config" se ejecuta pre-instalación de un paquete y como krb5-config.deb es una dependencia de krb5-kdc.deb se configura antes. 
Parece que si encuentra "krb5-config/default_realm" con db_get usa ese string como "default_realm" sino le setea lo que le retorna "dnsdomainname". Ahora me pongo a pensar y si esta bien que me setee "CPE.TELECENTRO.NET.AR" xq la 1era vez que lo instale ese era el dominio que devolvia "dnsdomainname" pero ya no(chequeado).
Ahora supuestamente cuando purgo el paquete supuestamente hace un "db_purge" por lo que "db_get krb5-config/default_realm" ya no deberia retornar nada y tomar mi nuevo dominio... pero no es asi. Por mas que lo purgue y vuelva a reinstalar el paquete me sigue tomando el dominio viejo.

¿Alguien sabe como chequear si realmente despues de purgar el paquete sigue existiendo en "krb5-config/default_realm" el dominio anterior?
o como hago para para borrar o setearlo a mano... 

Realmente no me queda claro si es un bug con los scripts de configuración del paquete, y si es asi tengo intenciones de notificarlo en lauchpad pero antes me gustaria chequearlo.

Saludos!.

PD: Puede ser que mi interpretación de la situación sea completamente incorrecta dado mi casi nulo conocimiento de debconf y scripts de configuración de paquetes, si es asi por favor diganme como deberia interpretarlo.

---

### Post by Fistandantilus on 2009-10-04
Eaea parece que era eso...
Modifique el script de configuración para hardcoderarle un string vacio a "krb5-config/default_realm" y me tomo el dominio actual!

Levante un issue en lauchpad al respecto:
[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/442766](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/442766)


Mi ingles es asqueroso!!! :guitar:

---

### Post by guillermolisi on 2009-10-04
> **Fistandantilus said:**
> Eaea parece que era eso...
Modifique el script de configuración para hardcoderarle un string vacio a "krb5-config/default_realm" y me tomo el dominio actual!

Levante un issue en lauchpad al respecto:
[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/442766](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/442766)


Mi ingles es asqueroso!!! :guitar:
Gracias por compartir el tema con todos !!

---


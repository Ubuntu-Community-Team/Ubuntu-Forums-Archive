---
title: "Active Directory y ms exchange"
date: 2009-11-25
forum: Software
---

### Post by Gideon26 on 2009-11-25
Hola gente mi consulta como lo ven arriba es que alternativas tenemos para ubuntu server 9.10 o 9.04,  de montar algo como se monta en un windows server. me refiero al active directory y al ms exchange server.

---

### Post by guillermolisi on 2009-11-25
> **Gideon26 said:**
> Hola gente mi consulta como lo ven arriba es que alternativas tenemos para ubuntu server 9.10 o 9.04,  de montar algo como se monta en un windows server. me refiero al active directory y al ms exchange server.
El equivalente a Active Directory es LDAP.
El equivalente a MS Exchange es ... no tiene equivalente ya que usa un protocolo privado, MAPI, de MS.

Podes montar un mailserver pero no tendras funcionalidad MAPI, solo POP3, SPOP3, IMAP4 y, logicamente, SMTP.

---

### Post by Gideon26 on 2009-11-25
> **guillermolisi said:**
> El equivalente a Active Directory es LDAP.
El equivalente a MS Exchange es ... no tiene equivalente ya que usa un protocolo privado, MAPI, de MS.

Podes montar un mailserver pero no tendras funcionalidad MAPI, solo POP3, SPOP3, IMAP4 y, logicamente, SMTP.

Muchas Gracias guillermolisi, preguntaba porque en todo lo que es servidores en linux voy medio frito, un soft parecido a la forma de configurar etc. al ms exchange?? alguna idea??

---

### Post by guillermolisi on 2009-11-25
> **Gideon26 said:**
> Muchas Gracias guillermolisi, preguntaba porque en todo lo que es servidores en linux voy medio frito, un soft parecido a la forma de configurar etc. al ms exchange?? alguna idea??
La verdad que no se si es parecido de configurar (porque la ultima version de Exchange que use fue la 5.5), pero alternativas con versiones comunitarias y privativas (licencia por uso) hay varias. Una de ellas se llama Scalix (que tienen ambas posibilidades y segun su documentacion posee MAPI).

---

### Post by juancarlospaco on 2009-11-26
*Zimbra....*

---


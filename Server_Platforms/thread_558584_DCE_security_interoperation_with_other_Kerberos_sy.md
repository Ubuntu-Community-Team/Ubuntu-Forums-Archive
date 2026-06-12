---
title: "DCE security interoperation with other Kerberos system."
date: 2007-09-24
forum: Server Platforms
---

### Post by river22_34 on 2007-09-24
To use authenticated DCE services, you must have credentials from
  the DCE security service; vanilla Kerberos v5 tickets aren't sufficient.
  But then, to use DCE services you must be using DCE RPC, so this
  is not really a problem.

  Going the other way, it is expected that a DCE security server
  can issue tickets that can be used by vanilla Kerberos applications.
  The Open Group was wary of promising this until the Kerberos v5 specs were
  published, but now that the Kerberos RFC has been published, Open Group
  anticipates guaranteeing interoperability sometime "soon".

  In a little more detail, the way to think about this is as follows:

        Kerberos offers 2 services (Authentication Service, Ticket
        Granting Service) over 1 communication mechanism (UDP port 88).

        DCE security offers 3 services (AS, TGS, Privilege Service) over
        2 communication mechanisms (UDP port 88, RPC).

        Where Kerberos and DCE security intersect (AS, TGS over UDP port
        88), the services are identical.

  DCE V1.1 supports the GSSAPI, so non-DCE services that use GSSAPI
  can be integrated with DCE security server.

Please feel free to post your own comments regarding this discussion.Thank you.

---


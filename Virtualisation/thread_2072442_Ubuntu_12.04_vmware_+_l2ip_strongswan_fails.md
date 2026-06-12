---
title: "Ubuntu 12.04 vmware + l2/ip strongswan fails"
date: 2012-10-17
forum: Virtualisation
---

### Post by Roshow on 2012-10-17
We have yet get L2/IP to work with Ubuntu 12 on a vmware enterprise cloud setup. Having it auth off a FreeRadius.

The thinking is that this is a missing kernel module but the DC says their images are not customized and we really have not got anywhere with them.

Our configurations work on every other hypervisor and environment we have tested.

> charon: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Oct 15 16:43:13 charon: 00[CFG] loaded IKE secret for {IP}
%any
Oct 15 16:43:13 charon: 00[CFG] sql plugin: database URI not set
Oct 15 16:43:13 charon: 00[LIB] plugin 'sql': failed to load -
sql_plugin_create returned NULL
Oct 15 16:43:13 charon: 00[CFG] loaded 0 RADIUS server configurations
Oct 15 16:43:13 charon: 00[LIB] plugin 'medsrv' failed to load:
/usr/lib/ipsec/plugins/libstrongswan-medsrv.so: cannot open shared object file:
No such file or directory
Oct 15 16:43:13 charon: 00[CFG] mediation client database URI not
defined, skipped
Oct 15 16:43:13 charon: 00[LIB] plugin 'medcli': failed to load -
medcli_plugin_create returned NULL
Oct 15 16:43:13 charon: 00[LIB] plugin 'nm' failed to load:
/usr/lib/ipsec/plugins/libstrongswan-nm.so: cannot open shared object file: No
such file or directory
Oct 15 16:43:13 charon: 00[CFG] HA config misses local/remote address
Oct 15 16:43:13 charon: 00[LIB] plugin 'ha': failed to load -
ha_plugin_create returned NULL

Any advise would be great, if I can answer any further questions please let me know.

---

### Post by Roshow on 2012-10-23
Anyone with any experience on the possible issue?

---


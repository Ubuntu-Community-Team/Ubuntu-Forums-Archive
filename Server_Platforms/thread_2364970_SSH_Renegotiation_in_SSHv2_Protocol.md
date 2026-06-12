---
title: "SSH Renegotiation in SSHv2 Protocol"
date: 2017-06-30
forum: Server Platforms
---

### Post by manogna on 2017-06-30
Hi,

 Changing of SSH deamon side ciphers is not affecting ongoing  session,While performing SSH renegotiation for protocol SSHv2 using  rekeyLimit tag in sshd_config file.
  We have modified /etc/ssh/sshd_config file with rekeyLimit as below :
  reKeyLimit default 30s
  So,for every 30seconds renegotiation is performed for ongoing  sessions.But when we change cipher values in /etc/ssh/sshd_config file  which are incompatible to client ciphers,New sessions are not opened but the existing sessions are ongoing.

  Is there any cache present in SSH that needs to be cleaned up to  consider new ciphers for ongoing sessions ?? Or Do we need to set any  options in /etc/ssh/sshd_config file for the changes to be considered  for ongoing sessions??

                                                                                                                                 We would like to know  What actually happen during SSH renegotiation in SSHv2.Does new  keys(session keys) generate ??If so how they are generated??

---

### Post by howefield on 2017-06-30
Not a chat thread, so moved to the "*Server Platforms*" forum for a better fit.

---


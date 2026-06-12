---
title: "samba help"
date: 2009-05-20
forum: Server Platforms
---

### Post by zeker446 on 2009-05-20
hi there, i have a storage server with ubuntu 9.04 and samba share installed, but when users create a folder the other users cant write in it, so i want that everybody can write, modify the new folders created by other user help me please

---

### Post by BadBoy4Live on 2009-05-20
Did you make your shares writeble ?

[sharename]
path = /.....
**writable = yes**

---

### Post by zeker446 on 2009-05-20
yes
 i going to post my smb config here


 # Nome do seu Servidor
    comment = Servidor SAMBA PDc
  # Domínio do servidor PDC
    workgroup = FLORIGROUP
    Netbios nane = SERVIDOR
    server string = SERVIDOR
  # Indica ser obrigatório o uso de usuário e senha
    security = Domain
    os level = 33
    announce as = NT Server
    domain logons = yes
  # Qual script será executa a ser logado %U significa nome do usuário
    logon script = %U.bat
  # Opções principais para se tornar o PDC
    domain master = yes
    local master = yes
    preferred master = yes
    keep alive = 20
    debug level = 3
    getwd cache = yes
    log file = /var/log/samba_log.%u
;    null passwords = no
    socket options = TCP_NODELAY IPTOS_LOWDELAY    
#Caminho para os scripts de logon

[netlogon]
    comment = Compartilhamento de Scripts
      # Não esquece de criar a pastas e colocar os scripts dentro
    path = /etc/samba/scripts/
;    public = no
    browseable = no
;    writeable = no

[W]
    path = /share/disco1
    guest ok = yes
    writeable = yes
;    browseable = yes

[Y]
    guest ok = yes
    writeable = yes
    path = /share/disco2
;    browseable = yes
 
[homes]
    comment = Pastas dos Usuários
;    public = no
    browseable = no
    writeable = yes


please help me my boss is making me crasy :O

---

### Post by zeker446 on 2009-05-20
problem solved

---


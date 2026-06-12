---
title: "Trouble with PDC SAMBA"
date: 2009-05-25
forum: Server Platforms
---

### Post by rodfall on 2009-05-25
[global]


  	workgroup = MeuDominio
        netbios name = MeuNome
  	server string = %h server (Samba %v)
  	domain master = yes
  	domain logons = yes
  	logon script = netlogon.bat
  	logon path =
  	socket options = IPTOS_LOWDELAY TCP_NODELAY
        # invalid users = root
  	bind interfaces only = True
  	interfaces = eth0
        hosts deny = ALL
  	hosts allow = 192.168.1. 127.0.0.1
  	create mask = 0644
  	directory mask = 0755
  	security = user
  	encrypt passwords = yes
  	os level = 100
  	preferred master = yes
  	local master = yes

[pub]

path = /home/pub
available = yes
browseable = yes
writable = yes



[netlogon]
	comment = Servico de Logon
  	path = /var/spool/samba/netlogon
  	guest ok = Yes
  	browseable = No


[homes]
  	comment = Diretorio Home
  	valid users = %S
  	guest ok = Yes
  	browseable = No


this is my config...


and i've made this steps

# mkdir -p /etc/skel/profile.pds
# groupadd maquinas
# useradd -g maquinas -d /dev/null -s /bin/false maquina01$
# passwd -l maquina01$



# smbpasswd -a -m maquina01
# net groupmap add ntgroup="Domain Admins" unixgroup=ntadmin rid=513 type=d
# useradd -g users -G ntgroup -d /home/usuario01 -m -c "usuario01" usuario01
# passwd usuario01
 smbpasswd -a usuario01


then here is Ok...

BUT when i go to windows... in System Properties in Network ID i can't reach my Samba for PDC

what i'm donig wrong...

some one see ?


thanks for the help

---


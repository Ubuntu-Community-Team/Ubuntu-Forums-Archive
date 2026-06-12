---
title: "Samba Error --- Shared Folder Show in All Computer on LAN"
date: 2009-02-05
forum: Server Platforms
---

### Post by silentsilent on 2009-02-05
Hi..

im using ubuntu server 8.04 and samba 3.0.28a-1ubuntu4.7

i think my smb.conf configuration is messed up but is work..
my destination is read write for randhi only... read only to other user.. but recently something is wrong.

My shared folder in samba show in all computer in my network (LAN) so the other computer (wind*wsxp) shared folder is gone and just showing folder from samba.

My server work as router and firewall too, and this is the schema:

ADSLmodem (bridge) --- ubuntu server --- switch --- all other computers

my server ip is 192.168.0.1 ( as a wins server )
client ip is 192.168.0.5-32 ( wins assigned via dhcp server )

wonder what the problem is

My smb.conf :
```
[global]
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	announce version = 5.0
	username map = /etc/samba/smbusers
	null passwords = yes
	encrypt passwords = yes
	passdb backend = tdbsam
	wins support = true
	netbios name = mail
	server string = Indomulya server
	printing = CUPS
	workgroup = INDOMULYA
	syslog only = yes
	os level = 20
	printcap name = CUPS
	syslog = 1
	security = user
    ; General server settings





; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Backup]
	read list = nobody,@nogroup
	wide links = no
	invalid users = root,samba,@root,@samba
	path = /mnt/sda5/backup
	write list = randhi,silent,r4ndhi,@randhi,@silent,@r4ndhi
	force group = randhi
	force user = randhi
	comment = File Backup ( read only )
	valid users = randhi,nobody,silent,r4ndhi,@randhi,@nogroup,@silent,@r4ndhi
	create mode = 0644
	public = yes
	user = randhi,nobody,silent,r4ndhi,@randhi,@nogroups,@silent,@r4ndhi
	directory mode = 0755

[BackupLVM]
	guest account = randhi
	writeable = yes
	wide links = no
	path = /backup
	write list = randhi,@randhi
	force group = randhi
	force user = randhi
	comment = File Backup ( read only )
	valid users = randhi,@randhi
	user = randhi,@randhi
	public = yes
	create mode = 0644
	directory mode = 0755

[Master Software]
	read list = nobody,@nogroup
	wide links = no
	invalid users = root,samba,@root,@samba
	path = /mnt/sda6/master/software
	write list = randhi,silent,r4ndhi,@randhi,@silent,@r4ndhi
	force group = randhi
	force user = randhi
	comment = Master Software ( Read Only )
	valid users = randhi,nobody,silent,r4ndhi,@randhi,@nogroup,@silent,@r4ndhi
	create mode = 0644
	public = yes
	user = randhi,nobody,silent,r4ndhi,@randhi,@nogroups,@silent,@r4ndhi
	directory mode = 0755

[ISO Files]
	read list = nobody,@nogroup
	wide links = no
	invalid users = root,samba,@root,@samba
	path = /mnt/sda6/master/ISO
	write list = randhi,silent,r4ndhi,@randhi,@silent,@r4ndhi
	force group = randhi
	force user = randhi
	comment = Kumpulan CD image / ISO ( Read Only )
	valid users = randhi,nobody,silent,r4ndhi,@randhi,@nogroup,@silent,@r4ndhi
	create mode = 0644
	public = yes
	user = randhi,nobody,silent,r4ndhi,@randhi,@nogroups,@silent,@r4ndhi
	directory mode = 0755

[Acronis Image]
	read list = nobody,@nogroup
	wide links = no
	invalid users = root,samba,@root,@samba
	path = /mnt/sda6/master/acronis
	write list = randhi,silent,r4ndhi,@randhi,@silent,@r4ndhi
	force group = randhi
	force user = randhi
	comment = Backup image seluruh komputer Indo Mulya ( Read Only )
	valid users = randhi,nobody,silent,r4ndhi,@randhi,@nogroup,@silent,@r4ndhi
	create mode = 0644
	public = yes
	user = randhi,nobody,silent,r4ndhi,@randhi,@nogroups,@silent,@r4ndhi
	directory mode = 0755

[Acer 6292]
	read list = nobody,@nogroup
	wide links = no
	invalid users = root,samba,@root,@samba
	path = /acer6292
	write list = randhi,silent,r4ndhi,@randhi,@silent,@r4ndhi
	force group = randhi
	force user = randhi
	comment = Backup image seluruh komputer randhi
	valid users = randhi,nobody,silent,r4ndhi,@randhi,@nogroup,@silent,@r4ndhi
	create mode = 0644
	public = yes
	user = randhi,nobody,silent,r4ndhi,@randhi,@nogroups,@silent,@r4ndhi
	directory mode = 0755

[Shared to All]
	force user = nobody
	comment = Untuk shared ke semua orang ( read write )
	wide links = no
	writeable = yes
	public = yes
	path = /mnt/sda6/shared
	force group = nogroup

```

---


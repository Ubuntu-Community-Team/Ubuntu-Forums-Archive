---
title: "[SOLVED] SAMBA 3.28a 8.04 LTS current master browser = UNKNOWN"
date: 2008-11-29
forum: Server Platforms
---

### Post by george_pc_70 on 2008-11-29
Hello all 

I already searched this forum and google 

I have a broken samba config and non of the pc's(XP pro) can logon to my samba domain

It seams that my samba server is assigning himself as master browser to eth0 instead of eth1 , this means non of the XP's will get a response as the eth0 is the outside world

any idea what the problem can be ?

my globel smb.conf
[global]
workgroup = SPESWORKGROUP
name resolve order = lmhosts hosts bcast 
#wins
idmap gid = 10000-20000
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
obey pam restrictions = yes
printer name = HP2420dn
veto files = /Maildir/
passwd program = /usr/bin/passwd %u
dns proxy = No
writable = yes
logon script = logon.cmd
idmap uid = 10000-20000
debug level = 10
os level = 255
add machine script = /usr/sbin/useradd -d /var/lib/nobody -g 100 -s /bin/false -M %u
max log size = 1000
log level = 10
log file = /var/log/samba/log.%m
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
logon drive = U:
guest ok = Yes
interfaces = eth1 lo
logon home = 
passdb backend = tdbsam
#wins support = true
netbios aliases = spesforum
server string = spesforum(Samba, Ubuntu)
path = /tmp
unix password sync = Yes
logon path = 
add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
syslog = 0
panic action = /usr/share/samba/panic-action %d
domain logons = Yes
bind interfaces only = Yes
preferred master = Yes
domain master = Yes
local master = yes


thx for a response hope someone can help me as it broke down this week during an update

George

---

### Post by bab1 on 2008-11-30
As you are running a multi homed host need to be very specific.  I believe the IP addresse for "interfaces = xxx.xxx.xxx.xxx", rather than the eth0 designation.  See [**here.**]("http://www.rxn.com/services/faq/smb/using_samba/html/ch04_06.htm")

---

### Post by george_pc_70 on 2008-11-30
changed it but still got this error


[2008/11/30 11:23:35, 4] 

nmbd/nmbd_workgroupdb.c:dump_workgroups(282)
  dump_workgroups()
   dump workgroup on subnet     192.168.3.1: netmask=  255.255.255.0:
  	SPESWORKGROUP(1) current master browser = UNKNOWN
  		SPESFORUM 40899a03 (spesforum(Samba, Ubuntu))
[2008/11/30 11:23:35, 9] nmbd/nmbd_namelistdb.c:find_name_on_subnet(133)
  find_name_on_subnet: on subnet 192.168.3.1 - name SPESWORKGROUP<1e> NOT FOUND
[2008/11/30 11:23:35, 8] nmbd/nmbd_elections.c:check_elections(361)
  check_elections: Cannot send election packet yet as name SPESWORKGROUP<1e> not yet registered on subnet 192.168.3.1

thx already for the help
anybody else has a clue

George

PS 



checked with 
net getlocalsid
what domain the server had and adjusted my samba config to that name 



	name resolve order = wins host bcast
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	preserve case = yes
	obey pam restrictions = yes
	enable privileges = yes
	delete user from group script = /usr/bin/gpasswd -d "%u" "%g"
	time server = yes
	veto files = /Maildir/
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = spesforum
	logon script = netlogon.bat
	local master = yes
	workgroup = SPESFORUM
	debug level = 0
	os level = 255
	security = user
	short preserve case = yes
	add machine script = /usr/sbin/useradd -g machines -c "Samba Machine" -d /dev/null -s /bin/false '%u'
	delete user script = /usr/sbin/userdel "%u"
	max log size = 1000
	log level = 0
	log file = /var/log/samba/log.%m
	guest account = nobody
	add group script = /usr/sbin/groupadd "%g"
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	delete group script = /usr/sbin/groupdel "%g"
	add user to group script = /usr/sbin/usermod -G "%g" "%u"
	logon drive = H:
	domain master = yes ; When domain logons = Yes the default setting for this parameter is Yes
	encrypt passwords = true
	passdb backend = tdbsam
	wins support = yes
	server string = Domain Controller
	unix password sync = yes
	logon path = 
	add user script = /usr/sbin/useradd -m "%u"
	set primary group script = /usr/sbin/usermod -g "%g" "%u"
	syslog = 10
	preferred master = yes
	panic action = /usr/share/samba/panic-action %d
	domain logons = yes
	pam password change = yes

---


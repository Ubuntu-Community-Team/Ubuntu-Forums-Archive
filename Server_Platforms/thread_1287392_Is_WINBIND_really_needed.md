---
title: "Is WINBIND really needed?"
date: 2009-10-10
forum: Server Platforms
---

### Post by BarryDocks on 2009-10-10
Might be a bit of a basic question, but do I really need winbind on my server?  Server fell over last night and the only thing I can find in the logs is a winbind error.  My thought is that is not required but I'm not sure what will happen if I uninstall it?:confused:

Thanks for any help/suggestions.


8.04 server 64-bit edition acting as a file for a MS-Access DB, print and zoneminder server with 6 xp clients via samba.

Samba config: 
```
[global]
	netbios name = FileServer
	workgroup = WORKGROUP
	server string = %v
	password level = 8
	log file = /var/log/samba/log.%m
	max log size = 50
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	dns proxy = No
	security = user 
	encrypt passwords = yes
	printcap name = cups
	load printers = yes
	printing = cups
	cups options = raw
	local master = yes
	preferred master = yes
	os level = 65
;	hosts allow = 10.1.0.0/255.255.255.0

[printers]
  	comment = All Printers
   	path = /var/spool/samba
  	browseable = no
# to allow user 'guest account' to print.
   	guest ok = yes
   	writable = no
   	printable = yes
   	create mode = 0700

[print$]
  	path = /var/lib/samba/printers
  	browseable = yes
  	read only = yes
  	write list = root

# A useful application of samba is to make a PDF-generation service
# To streamline this, install windows postscript drivers (preferably 
# colour)on the samba server, so that clients can automatically install
# them.

;[pdf-generator]
;   path = /var/tmp
;   guest ok = No
;   printable = Yes
;   comment = PDF Generator (only valid users)
   #print command = /usr/share/samba/scripts/print-pdf file path win_path recipient IP &
;   print command = /usr/share/samba/scripts/print-pdf %s ~%u \\\\\\\\%L\\\\%u %m %I &

# Case Preservation can be handy - system default is _no_
# NOTE: These can be set on a per share basis
;  preserve case = no
;  short preserve case = no
# Default case is normally upper case for all DOS files
;  default case = lower
# Be very careful with case sensitivity - it can break things!
;  case sensitive = no

# a service which has a different directory for each machine that 
# connects this allows you to tailor configurations to incoming 
# machines. You could also use the %u option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes

;[homes]
;	comment = Home Directories
;	read only = No
;	browseable = No

[Adrian]
	comment = Adrians Files
	path = /media/disk/adrian
	valid users = adrian, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Music]
	path = /media/disk/music
	read only = No
	guest only = Yes
	guest ok = Yes
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[CCTV]
	path = /media/disk/cctv
	read only = No
	guest only = Yes
	guest ok = Yes
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Staff]
	path = /media/disk/staff
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Focus Data]
	comment = Data files for Focus and clinical records
	path = /media/disk/focus_data
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
	kernel oplocks = no
	oplocks = false
	level2 oplocks = false

[Practice Documents]
	comment = Practice documents and files
	path = /media/disk/practice_documents
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[HoyaLog]
	comment = HoyaLog files
	path = /media/disk/hoyalog
	valid users = adrian, dispensing, office
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Clinical Images]
	comment = Clinical image files
	path = /media/disk/clinical_images
	valid users = adrian, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
	kernel oplocks = no
	oplocks = false
	level2 oplocks = false

[SAGE]
	comment = SAGE accounts files
	path = /media/disk/sage
	valid users = adrian, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Drivers_etc]
	comment = Windows drivers & device settings
	path = /media/disk/drivers_etc
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

```

daemon log:
```
Oct 10 09:57:09 fileserver winbindd[5625]: [2009/10/10 09:57:09, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Oct 10 09:57:09 fileserver winbindd[5625]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Oct 10 09:57:09 fileserver winbindd[5625]: [2009/10/10 09:57:09, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Oct 10 09:57:09 fileserver winbindd[5625]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Oct 10 09:57:40 fileserver winbindd[6021]: [2009/10/10 09:57:40, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Oct 10 09:57:40 fileserver winbindd[6021]:   ERROR: Initialization failed for alloc backend, deferred! 
Oct 10 09:57:40 fileserver smbd[7824]: [2009/10/10 09:57:40, 0] auth/auth_util.c:create_builtin_administrators(792) 
Oct 10 09:57:40 fileserver smbd[7824]:   create_builtin_administrators: Failed to create Administrators 
Oct 10 09:57:40 fileserver winbindd[6021]: [2009/10/10 09:57:40, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Oct 10 09:57:40 fileserver winbindd[6021]:   ERROR: Initialization failed for alloc backend, deferred! 
Oct 10 09:57:40 fileserver smbd[7824]: [2009/10/10 09:57:40, 0] auth/auth_util.c:create_builtin_users(758) 
Oct 10 09:57:40 fileserver smbd[7824]:   create_builtin_users: Failed to create Users 
Oct 10 09:57:40 fileserver winbindd[5625]: [2009/10/10 09:57:40, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Oct 10 09:57:40 fileserver winbindd[5625]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Oct 10 09:57:40 fileserver winbindd[5625]: [2009/10/10 09:57:40, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Oct 10 09:57:40 fileserver winbindd[5625]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
```

---

### Post by swerdna on 2009-10-10
I don't see anything in smb.conf that calls for winbind.

OTOH you have "kernel oplocks" calls in [Focus Data] and in [Clinical Images]. Kernel oplocks is a [global] parameter, not a [service] parameter. You should move it.

I like your [global] structure -- just right for a SOHO workgroup, except perhaps for "name resolve order = bcast host lmhosts wins"

---

### Post by BarryDocks on 2009-10-10
> **swerdna said:**
> I don't see anything in smb.conf that calls for winbind.

OTOH you have "kernel oplocks" calls in [Focus Data] and in [Clinical Images]. Kernel oplocks is a [global] parameter, not a [service] parameter. You should move it.

I like your [global] structure -- just right for a SOHO workgroup, except perhaps for "name resolve order = bcast host lmhosts wins"

Thanks for this,  I didn't realise kernal oplocks was a global parameter, it's needed for multi user access to the access db which is in those shares.

So if I uninstall windbind nothing will happen?

Just out of interest what will "name resolve order = bcast host lmhosts wins" do exactly?

Also what is a "SOHO workgroup"?  sorry to show my ignorance.

---

### Post by swerdna on 2009-10-10
> **BarryDocks said:**
> Thanks for this,  I didn't realise kernal oplocks was a global parameter, it's needed for multi user access to the access db which is in those shares.
So put a hash mark (#) at beginning of those two lines and put the call instead in [global] and test if everything still works as per before moving it.
> So if I uninstall windbind nothing will happen?Why don't you test first by temporarily turning it off. Start the network and when it settles down and is working nicely, turn winbind off with this command in a terminal window:```
sudo /etc/init.d/winbind stop
```Then see if the network keeps running or falls over.

> Just out of interest what will "name resolve order = bcast host lmhosts wins" do exactly?This property is an instruction to Samba on how to resolve netbios names to IP addresses. Least effort is for me to quote from here: [http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
> This option is used by the programs in the Samba suite to determine what naming services to use and in what order to resolve host names to IP addresses. Its main purpose to is to control how netbios name resolution is performed. The option takes a space separated string of name resolution options.

The options are: "lmhosts", "host", "wins" and "bcast". They cause names to be resolved as follows:

    *

      lmhosts : Lookup an IP address in the Samba lmhosts file. If the line in lmhosts has no name type attached to the NetBIOS name (see the manpage for lmhosts for details) then any name type matches for lookup.
    *

      host : Do a standard host name to IP address resolution, using the system /etc/hosts , NIS, or DNS lookups. This method of name resolution is operating system depended for instance on IRIX or Solaris this may be controlled by the /etc/nsswitch.conf file. Note that this method is used only if the NetBIOS name type being queried is the 0x20 (server) name type or 0x1c (domain controllers). The latter case is only useful for active directory domains and results in a DNS query for the SRV RR entry matching _ldap._tcp.domain.
    *

      wins : Query a name with the IP address listed in the WINSSERVER parameter. If no WINS server has been specified this method will be ignored.
    *

      bcast : Do a broadcast on each of the known local interfaces listed in the interfaces parameter. This is the least reliable of the name resolution methods as it depends on the target host being on a locally connected subnet.

You are using the default which is:```
name resolve order = lmhosts host wins bcast 
```So by default the Samba naming daemon will try first your lmhosts file which likely doesn't exist or is empty. Then it will try the file /etc/hosts which won't contain any info on your machine names and IP addresses for the network (unless you hand-coded it in)....and so on. So to cut down on confusion for your server in trying to locate the network machines, you might as well use something meaningful, and the list I wrote down is meaninful in your case, unlike the default. You see, these three lines:```
	local master = yes
	preferred master = yes
	os level = 65

```instruct your Server to assemble a list of machines and their IP addresses for the LAN and to serve those names out to the other machines on the LAN so they can all find each other. But it depends for good working on Broadcast Name Resolution -- and that requires the naming daemon to use "bcast" as it's first port of call when assembling the list of machines on the LAN, instead of what you are using now, which puts "bcast" as the last thing to try.

> Also what is a "SOHO workgroup"?  sorry to show my ignorance.

Acronym for Small Office or Home Office, meaning anything that doesn't have complex systems like multiple subnets (multiple IP masks) and Domain Controllers, wins servers etc, such as are found in large companies or multi-floored, multi-building, government departments. Maybe ,= 20-30 computers might define a SOHO LAN, sort of.

FFI on small business LANs here: [The Samba LAN Primer for Ubuntu]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by BarryDocks on 2009-10-14
I have uninstalled winbind and everything seems ok!

Thankyou for taking the time to answer my queries, very helpful

---


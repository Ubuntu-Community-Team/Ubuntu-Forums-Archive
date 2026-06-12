---
title: "User login in LTSP Servert"
date: 2021-05-08
forum: Ubuntu/Debian BASED
---

### Post by kishore16 on 2021-05-08
Hi,
I have configured LTSP Server in Ubuntu MATE 20.04. In that my Administarator and client user can login in server but in client pc Administrator user can login but client user can't login. I am selecting and typing the clientuser password and I am selecting Enter , for 2 seconds it was complete black screen and it comes back to login screen. Now i changed clientuser to Administrator but I can't login still now..

Please help me to solve this problem.

---

### Post by Tadaen_Sylvermane on 2021-05-08
Post your /etc/ltsp/ltsp.conf

I had trouble with the default sshfs for /home/"$USER". Switching to nfs for /home solved my issues. I never checked if that was resolved as I stopped using LTSP awhile ago.

---

### Post by kishore16 on 2021-05-10
Hi 
I found one thing that when I create a new user their directory should be created in /home/"$USER" but it was not there and my Administrator directory only avaliable inside /home directory. Now what can I do to solve this issue ?
Because of this directory problem the client user can't login I think so. This I found through by viewing the syslog and I checked by login in client user there the directory is not avaliable. By adding the client user in Administrator group it also not found /home/"$USER".
 I have deleted my client users from my LTSP server but this was not updated in the LTSP image. I need solution for these issue as soon as possible.

" LTSP is my Final year project so please help me to solve this issue and the project is in submission stage so please help me to solve this issue."

---

### Post by kishore16 on 2021-05-10
# /bin/sh -n
# LTSP configuration file
# Documentation=man:ltsp.conf(5)


# The special [server] section is evaluated only by the ltsp server
[server]
# Enable NAT on dual NIC servers
# NAT=1


# Provide a full menu name for x86_32.img when `ltsp ipxe` runs
# IPXE_X86_32_IMG="Debian Buster"


# The special [common] section is evaluated by both the server and ltsp clients
[common]
# Specify an alternative TFTP_DIR
# TFTP_DIR=/var/lib/tftpboot


# In the special [clients] section, parameters for all clients can be defined.
# Most ltsp.conf parameters should be placed here.
[clients]
# Specify an /etc/fstab line for NFS home; note this is insecure
# FSTAB_HOME="server:/home /home nfs defaults,nolock 0 0"


# MAC address, IP address, or hostname sections can be used to apply settings
# to specific clients.
[61:6c:6b:69:73:67]
# HOSTNAME=pc01
# Include parameters from another section, defined below
# INCLUDE=crt_monitor


# Shell "case" expressions can be used in MAC, IP, or hostname sections.
# This matches all Raspberry Pi MAC addresses.
[b8:27:eb:*|dc:a6:32:*]
# FSTAB_BOOT="/dev/mmcblk0p1  /boot  vfat  defaults  0  2"


# If you have proper DNS, you can use hostname sections
[administrator-pc]
# Only allow the administrator to log in to this client
# PWMERGE_SUR="administrator"


# You can also group parameters into named sections and INCLUDE= them elsewhere
[crt_monitor]
# Force EDID and resolution to 1024x768 for clients with old CRT monitors
X_HORIZSYNC="28.0-87.0"
X_VERTREFRESH="43.0-87.0"
X_MODES='"1024x768" "800x600" "640x480"'

---

### Post by Tadaen_Sylvermane on 2021-05-11
I think you misunderstand how LTSP users work. It imports the /etc/{passwd|group|shadow} from the host. So you don't create users in the image rather you use users that exist on the server. Even if you use a separate chroot for the image it still uses users from the host. The /home/"$USER" directories are also on the host in the /home directory. The reasoning is clear. To add a user in the image one would need to rebuild the image every single time.

I can't remember how it was in the documentation. I know I got hung up on that part as well back when I was messing with it.

---


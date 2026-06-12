---
title: "Desperate for samba help - how difficult can it be??!!"
date: 2007-04-03
forum: Server Platforms
---

### Post by jnorris235 on 2007-04-03
If anyone will kindly take me step by step...want laptop and desktop and NAS attached to router to samba together!
Laptop (called chi) and desktop (called tao) both Kubuntu Edgy, and NAS hard disk (called ting) attached to my wireless router. I can FTP between them all - I can even see as a Samba my wifes windows laptop, but after 6 weeks of trying, nothing else.

Samba is installed on both computers and apparently on the NAS too. 
On the computers Samba-common is too.
Even installed swat but it doesn't work
limsmbclient, smbclient, smbfs - all installed. I probably installed something called cifs too. God knows!

All correct so far?

Why aren't they installed with samba (I thought that was what dependencies were).
So...
Fiddled with fstab adding this>>
//192.168.2.2/jon /mnt/nas smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

Don't know why - I was told to. I created the folder mnt/nas (why nas? tried ting too!). Does it have to be mounted and if so why not mount th eother computer too?

Fiddled with smb.conf (this is all that is uncommented though). chi is the laptops name, china is the domain name>>
[global]
; General server settings
netbios name = chi
server string = 
workgroup = china
announce version = 5.0
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 

passdb backend = tdbsam
null passwords = yes
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto

---

### Post by huygens on 2007-04-03
It is a bit confusing. After reading your whole message, I did not figure out what is your problem :-(
So you have 3 "computers" and a NAS:
  - Kubuntu laptop called chi
  - Kubuntu desktop called tao
  - NAS drive called ting
  - Windows laptop called ??

And you are trying to exchange data I presume. But what is not functioning? Is it when you access the ting from the Windows laptop or from the Kubuntu computers? Or the problem is that you cannot access shares on chi from tao, or on tao from windows, etc.

I have a not so far similar configuration here at home which works :-) so I'm sure I can help you, if only I know on what...

---

### Post by bullgr on 2007-04-04
yes your message is realy a bit confusing...

to help you i give you my settings from a working ubuntu file server using samba to connect
winblows clients to the server files.

installing samba
> sudo apt-get install samba smbfs

config samba
> sudo gedit /etc/samba/smb.conf

delete all the crap and type...> 

[global]
netbios name = server
server string = server
workgroup = Workgroup
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
encrypt pass = yes
wins support = yes

[your_homefolder]
path = /home/your_homefolder
available = yes
browseable = yes
public = yes
writable = yes

[c]
path = /mnt/c
available = yes
browseable = yes
public = yes
writable = yes

[d]
path = /mnt/d
available = yes
browseable = yes
public = yes
writable = yes

of course in Global you can change netbios name and server string in what you like to name
your server and in workgroup give your workgroup name

the c and d are my disk drives mounted in /mnt/c and /mnt/d.
with this options the winblows user can do anything on the disks.

hope i help...

---

### Post by huygens on 2007-04-04
> **bullgr said:**
> [...] delete all the crap and type... [...]

hmmm.... ;-) before deleting all the "crap", make a back-up of it. I'm using this "crap" and it works like a charm. So in case you need to reverse to something "stable", you would better make a back-up ;-)
Though no offence bullgr, I'm sure it is working for you, but the "crap" does also work for me :-)

I also wrote a few lines about [setting up Samba almost without using the command line]("http://www.berthon.eu/ice_and_fire/?p=9"). This was applicable to Ubuntu 6.06 (a.k.a Dapper Drake), but his applicable to Edgy and Feisty.

---

### Post by bullgr on 2007-04-04
> **huygens said:**
> hmmm.... ;-) before deleting all the "crap", make a back-up of it. I'm using this "crap" and it works like a charm. So in case you need to reverse to something "stable", you would better make a back-up ;-)
Though no offence bullgr, I'm sure it is working for you, but the "crap" does also work for me :-)


yes, what is "crap" for me, is working for someone else...
i use the word "crap" because i remember that until i found "my solution" for the smb.conf i was frustated of the complexity and the useless (for me) stuff are writen on the file.

sorry...

---


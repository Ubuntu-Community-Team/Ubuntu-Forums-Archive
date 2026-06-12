---
title: "Script to backup Vmware server virtual machines."
date: 2008-10-25
forum: Server Platforms
---

### Post by ezacon on 2008-10-25
Here is my script to backup the vmware server virtual machines.
I have 4 VM and usualy only 2 are running. The script checks the VM status, if it is running, it is paused then backup the directory and if it was running before backup, restart it.
The backup is stored in a vetwork drive. The script also checks if the drive is mounted and mount it if it is not.
Finaly, it send a notification mail. Well realy the mail part is not running for me, because the mail server is in another machine and still no idea how to make mail command to use another mail server (with smt auth).
It is probably no very 'clean'. It is my first script in linux.
Any improvement or fix the mail part are welcome.
Sorry for my poor english.
```
#!/bin/sh
LOGFILE="bckvm`date +%y%m%d`.log"
VMPATH="/var/lib/vmware/Virtual Machines/"
#=====================================================================================
# Funcion 'backvm'. Invoca 'archiva' con parametros de cada VM
backvm()
{
# Copia maquina virtual windows 2003 server (sERPA)
archiva "Windows Server 2003 Enterprise Edition.vmx" "win2k3" "win2k3"
# Copia maquina virtual cliente windows XP
archiva "Windows XP Professional.vmx" "Windows XP Professional" "winxp"
# Copia maquina virtual Ubuntu recovery
archiva "Plantilla Ubuntu Server 64.vmx" "Plantilla Ubuntu Server 64" "ubunturecover"
# Copia maquina virtual mail (Zimbra)
archiva "Ubuntu.vmx" "mail" "mail"
}
#=====================================================================================
# Funcion 'archiva'. Pausa y copia la maquina virtual que se proporciona como parametros
# $1=> Archivo VM. $2=> Directorio VM. $3=> Nombre VM
archiva()
{
echo `date`:Iniciada copia de VM  >> /root/copias/$LOGFILE
echo Archivo de VM: $1  >> /root/copias/$LOGFILE
echo Directorio de VM: $2  >> /root/copias/$LOGFILE
echo Nombre de VM: $3  >> /root/copias/$LOGFILE
VMSTAT=$(vmware-cmd "$VMPATH$2/$1" getstate)
case $VMSTAT in
        "getstate() = on")
                /usr/bin/vmware-cmd "$VMPATH$2/$1" suspend
                echo `date`:Parando maquina virtual $2 >> /root/copias/$LOGFILE
                VMRUN="y"
                ;;
        "getstate() = off")
                echo `date`:Maquina virtual $2 no está arrancada >> /root/copias/$LOGFILE
                VMRUN="n"
                ;;
        *)
                echo `date`:Estado de la maquina virtual desconocido >> /root/copias/$LOGFILE
                VMRUN="n"
esac
/bin/tar \
        --create \
        --verbose \
        --preserve \
        --gzip \
        --ignore-failed-read \
        --file=/media/copias/"$3".tgz \
        "$VMPATH$2"/ \
        >> /root/copias/$LOGFILE
case $VMRUN in
        "y")
                /usr/bin/vmware-cmd "$VMPATH$2/$1" start
                echo `date`:Iniciando maquina virtual $2 >> /root/copias/$LOGFILE
                ;;
        "n")
                echo `date`:No se inicia maquina virtual $2 >> /root/copias/$LOGFILE
                ;;
esac
echo `date`:Finalizada copia de maquina $3 >> /root/copias/$LOGFILE
}
#=====================================================================================
echo `date`:Inicio de copia de maquinas virtuales > /root/copias/$LOGFILE
ISMOUNT=$(cat /proc/mounts|grep /media/copias)
if [ -z "${ISMOUNT}" ];
        then
                echo Montando disco de copias >> /root/copias/$LOGFILE
                mount /media/copias
                if [ $? -ge 1 ]
                        then
                                echo No se ha podido montar el disco de copias >> /root/copias/$LOGFILE
                        else
                                backvm
                fi
        else
                backvm
fi
echo `date`:Proceso finalizado >> /root/copias/$LOGFILE
# email subject
SUBJECT="Copia de seguridad de maquinas virtuales `date`"
# Email To ?
EMAIL="abtadmin@abtelectronica.com"
# Email text/message
EMAILMESSAGE="/root/copias/$LOGFILE"
# send an email using /bin/mail
/usr/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
cp /root/copias/$LOGFILE /media/copias/$LOGFILE
/bin/umount /media/copias

```

---

### Post by ezacon on 2008-10-29
The mail part is solved using the email utility:
[http://www.cleancode.org/projects/email](http://www.cleancode.org/projects/email)

It allow to use a remote smtp mail server with autentication.
It is not included in Ubuntu repos, so you have to compile it.

Here is a litle howto for email utility:
[http://www.linux.com/feature/136877](http://www.linux.com/feature/136877)

The sintax is similar to mail, so i have uninstalled emailtools and exim and put a symlink called mail in /usr/bin pointing to email binary.

---

### Post by parrimin on 2009-07-30
Hey, this is what i need. Im gonna test it with my images.

---


---
title: "Problems with SEC"
date: 2007-05-15
forum: Server Platforms
---

### Post by ionuribe on 2007-05-15
Hello, 
I'm working with SEC(Simple Event Correlator) to generate alerts with the logs recived from a firewall.

The rules that SEC has to execute are:


```
# Asignación de variables 
# Pipe # 
type=Single 
ptype=RegExp 
pattern=(SEC_STARTUP|SEC_RESTART|SEC_SOFTRESTART) 
desc=SEC Initialization_Pipe 
context=SEC_INTERNAL_EVENT 
action=assign %secdb_pipe /var/log/secdb.pipe 
# Generar alarma cuando se presentaron más de 100 mensajes 
# de cualquier tipo en 1 hora 
# IDS # 
type=SingleWithThreshold 
ptype=RegExp 
continue=TakeNext 
pattern=(.*) 
desc=xx eventos en yy minutos IDS 
window=3600 
thresh=100 
action=write %secdb_pipe ALR|1|5|firewall|3|0003|%f|%h|Más de 100 mensajes en 1 hora * 
IDS 
```


The objective is to introduce the alerts in a table called Alarms. 
With the **action** sentence the data is introduce in a table in a B.D.
 

Then I generate a script to have access into the B.D that contains the table:


```
###SE CREA LA PILA FIFO SI NO HA SIDO TODAVIA CREADA### 


if [ ! -e /var/log/secdb.pipe ] 
then 
mkfifo /var/log/secdb.pipe 

fi 

###SE LEE LA PILA FIFO### 

while [ -e /var/log/secdb.pipe ] 
do 
mysql -u usuario --password= contraseña sec_db </var/log/mysql.pipe>/dev/null 
done 
```


The problem is that when I execute SEC with the following sentence,


```
sec -detach -conf=/var/log/dbinsert_sec.pl -input=/var/log/mail.log 
```


where dbinsert_sec.pl are the previus perl sentences that sec has to execute and mail.log contains the logs from the firewall.

I receive the following error messages: 

```
Simple Event Correlator version 2.3.2 
Changing working directory to / 
Reading configuration from /var/log/dbinsert_sec.pl 
/var/log/dbinsert_sec.pl line 2: Line # Pipe # does not conform to keyword=value format or keyword is not alphanumeric 
/var/log/dbinsert_sec.pl line 3: Line type=Single does not conform to keyword=value format or keyword is not alphanumeric 
```



I receive the same message for the rest of the sec sentences defined. 

If someone could help me, I would ve very great

ionuribe.

---


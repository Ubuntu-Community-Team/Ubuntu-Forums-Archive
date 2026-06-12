---
title: "Problemas Con Wine.... No Anda!"
date: 2008-07-15
forum: Software
---

### Post by leonardo83 on 2008-07-15
Que tal gente, tengo un problema.
Instale Wine ok en ubuntu 7.10, andaba ok pero despues me decidi a desinstalarlo, tenia un programa de win (mmlogic para la facu) y PC Suite de Nokia, cuestion que eligo desinstalar wine desde Aplicaicones-Wine-Desinstalar Wine, se elimina segun pantalla pero sigue apareciendo en el menu! y ya sin la opcionde desinstalar, entonces voya  menu principal y lo destildo para que ya no aparzca en el menu de Aplicaciones.

Cuestion que segun Agregar y quitar prgramas ya no estaba instalado en mi Pc, entonvces al tiempo lo quise instalar de nuevo todo ok, pero ahoras cuando quiero instalar programas me aparecen una serie de datoas raros en la termianl, instala todo pero no aparecen esos programas para elegir en el menu de wine!! no se que est apasando ni se como borrarlo definitivasmente como para instaalr winde de cero, borrando todos los posibles restos.
si les es de ayuda, esto es lo que aparecio cuando instalo en teoria ok ese programa, pero no aparecio en el menu :(
```
tormentor@tormentor-desktop:~$ wine  mmlogic14.exe
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```

aiutoooooooo!! saludos :confused::confused::confused::confused:

---

### Post by Tosh78 on 2008-07-16
Probaste de desinstalarlo desde Synaptic? Yo hace poco lo desinstale desde ahi y volvi a instalarlo sin ningun problema.
Con respecto a que no te aparezcan los programas en el menu, a mi me pasa lo mismo pero si con la consola voy al directorio donde tengo instalados los programas y pongo "wine nombredelprograma" funciona perfectamente.

---

### Post by Mauro22 on 2008-07-16
Para borralo hace:

sudo apt-get purge wine

y tambien borra la carpeta ".wine" en tu home...


OJO, Asi perdes todo lo instalado con wine, y tambien la configuracion...

---

### Post by leonardo83 on 2008-07-17
gracias gente, no se qu epaso pero segui los pasos del amigo ahi arriba, despues de elegir purge en consola me recomienda ademas "autoremove", asi que lo elegi tambien, lo reinstale desde synaptic.

Ahora en el menu de Wine en aplicaciones ya no aparece la opcion programas!! entonces ni siquiera aparece notepad que ya viene por defecto :(
Desinstale, instale de nuevo, instale de nuevo cualquier programa .exe. se instala con la pantalla como que se carga ok, pero no aparece en ningun lugar, y en la terminal aparece l mismo emnsaje de error que copie antes. leyendo ese codigo, puede ser que haga falta modificar algo del "registro"? Ya tenia problemas con Windows y ahora persisten en Linux :(

Espero me tiren unja soga como para poder hacer que esto funcione de una vez, saludos :confused:

---

### Post by leonardo83 on 2008-07-20
Burno el incinveninete persiste y como algunas cosas de windows no me van a funcar en linux, cada tanto volvere a winME, lastima pero no se resolvio WIne y no pienso ni en joda reinstalar todo por ese programa. :mad:

Un abrazo, gracias a los que me ayudaron :(

---


---
title: "Iniciar sesión automaticamente en kubuntu"
date: 2009-05-29
forum: Software
---

### Post by guisheca on 2009-05-29
Que tal comunidad, resulta que estoy usando hace un buen tiempo kubuntu, el cual tiene cosas por pulirse pero el aspecto estético me puede mas que cualquier cosa jeje.
El problema está en que quiero setear a mi usuario para que inicie sesión sin tener que poner nombre de usuario y contraseña. Ya se que eso se lo elige en la instalación, lo que pasa que instalé inicialmente ubuntu (gnome,gdm) y luego instale kde 4.2.3 (kdm) y ahora me quedé sin esa opción.
Fuí a configuración del sistema>avanzado>gestor de acceso, pero allí no puedo elegir nungún usuario para que inicie automaticamante, aparece la pestaña en blanco.
He llegado a la ubicación de un archivito llamado kdmrc, que es el que gobierna el comportamiento de kdm, pero no se como editarlo para que realice la tarea que necesito.
Por las dudas les dejo el contenido del archivo:

```
[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/halt
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=false
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=Bespin
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Bienvenida/o a Debian en %n
GreeterPos=50,50
HiddenUsers=
Language=es
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/oxygen
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-br -nolisten tcp
ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
DefaultUser=killermo
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling

```

Tengo instalado kubuntu 9.04 64 bits.
Saludos y gracias.

---

### Post by staar on 2009-05-29
mi kdmrc con login automático activado ```

[General]                                                                                                       
ConfigVersion=2.4                                                                                               
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6                                                                       
PidFile=/var/run/kdm.pid                                                                                        
ReserveServers=:1,:2,:3                                                                                         
ServerVTs=-7                                                                                                    
StaticServers=:0                                                                                                

[Shutdown]
BootManager=None
HaltCmd=/sbin/halt
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=All
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/usr/share/config/kdm/Xreset
Session=/usr/share/config/kdm/Xsession
SessionsDirs=/usr/share/config/kdm/sessions,/usr/share/apps/kdm/sessions
Setup=/usr/share/config/kdm/Xsetup
Startup=/usr/share/config/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
ColorScheme=
FaceSource=AdminOnly
FailFont=Droid Sans,9,-1,5,75,0,0,0,0,0
ForgingSeed=1239554593
GUIStyle=Bespin
GreetFont=Droid Sans,14,-1,5,50,0,0,0,0,0
GreetString=Bienvenido %s en %n
GreeterPos=50,50
HiddenUsers=
Language=es
LogoArea=Clock
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
MaxShowUID=65000
MinShowUID=500
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Droid Sans,9,-1,5,50,0,0,0,0,0
Theme=/usr/share/apps/kdm/themes/archlinux-simplyblack
UseBackground=true
UseTheme=true
UserCompletion=true
UserList=true

[B][X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=true
NoPassUsers=staarbreaker
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/X -br -novtswitch -quiet

[X-:*-Greeter]
AllowClose=false
DefaultUser=staarbreaker
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Default

[X-:0-Core]
AutoLoginEnable=true
AutoLoginLocked=false
AutoLoginUser=staarbreaker
ClientLogFile=.xsession-errors[/B]

[Xdmcp]
Enable=false
Willing=/usr/share/config/kdm/Xwilling

```

saludos

---

### Post by guisheca on 2009-05-29
Muchísimas gracias staar! problema solucionado. Esas son las ventajas de haber pasado por arch, ahí te das cuenta que siempre hay un archivito de texto por editar para que todo funcione jejeje.
Saludos y gracias nuevamente.

---


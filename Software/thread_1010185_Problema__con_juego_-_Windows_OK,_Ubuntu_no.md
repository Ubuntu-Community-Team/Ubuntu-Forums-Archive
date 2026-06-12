---
title: "Problema  con juego - Windows OK, Ubuntu no"
date: 2008-12-13
forum: Software
---

### Post by Tosh78 on 2008-12-13
Hola! Posteo aca, porque ya busque por todos, en el subforo de juegos tambien, pero sigo sin poder solucionar mi problema y hasta ahora solo dos personas tenemos este problema. A ver si algun alma caritativa me puede dar una mano.
Bueno, el tema es el siguiente. Quiero jugar un juego (Football Manager 2009) en Ubuntu con wine. Ya instale todo lo necesario, y el juego se instalo perfectamente. El tema es que a la hora de correrlo, me tira el siguiente error:

Cannot run game: Failed to set up graphics system.

Al principio pense que seria algo de hardware, pero lo instale en la particion de windows en la misma maquina y funciona perfectamente.
Lo que me devuelve la consola es esto:

```
 fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:advapi:CheckTokenMembership ((nil) 0x13f288 0x32fc54) stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d7e314c,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7d7e3348,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x7d6d2464,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20028 0x00000000
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x20028
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10026
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub
fixme:shell:IsUserAdmin stub 
```

Alguien podria mirar esto y decirme si se le ocurre que puede ser?

---

### Post by Hei Ku on 2008-12-13
Tira un punto de errores de clases stub. Probablemente clases que estan creadas pero en wine no hacen nada. Te fijates en wineHQ, a ver que dicen sobre este juego?

---

### Post by Thalskarth on 2008-12-14
No se, pero a mi me pasa algo parecido.

en hardy, tenia el civilization IV, el heroes V y el simcity 4 instaldos mediante wine y andaban sin dramas.

con intrepid no pude hacer funcionar ninguno de los 3 :S

---


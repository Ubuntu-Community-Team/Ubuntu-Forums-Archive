---
title: "error con wine"
date: 2009-10-26
forum: Software
---

### Post by Geruntu on 2009-10-26
Hola gente!! tengo el siguiente problema no puedo configurar el wine en mi ubuntu 9.04!! me sale el siguiente error 

[B][COLOR=Black]geruntu@geruntu-desktop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
geruntu@geruntu-desktop:~[/COLOR][/B]
si alguien me puede ayudar!!

---

### Post by Fak89 on 2009-10-26
Yo te diría que lo elimines completamente y lo instales nuevamente. Te tira errores en Sistem32 (lo cual no es nada bueno ni en el mismo win), aunque podrías reemplazar el archivo dll, los ejecutables dudo que puedas repararlos o reemplazarlos..

Y .. este tipo de temas va para Software ;)

---

### Post by Geruntu on 2009-10-28
Gracias por responder!! ya hice lo q me recomendaste y sigue igual!! alguna otra variante?

---

### Post by Mauro22 on 2009-10-28
> > when I use $wine winecfg at the terminal I get: 
> 
> Code: 
> darrencarter@darrencarter-laptop:~$ wine winecfg 
> err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found 
> err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135 
> err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515 
> err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found 
> err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found 
> err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135 
> 
> 
> 
> 
> So is there any way to fix this? Thanks in advance. 




> Hace:

 WINEDLLOVERRIDES="rpcrt4=b" wine winecfg 

 Despues remove todo lo relacionado de 'ole/rpc' de la lista de reemplazos... 


De acá: [http://www.nabble.com/I-broke-wine-td23045731.html](http://www.nabble.com/I-broke-wine-td23045731.html)

---

### Post by moviglez on 2009-12-13
Gracias mil.

Con esto me ha vuelto a funcionar.

Saludos.

---


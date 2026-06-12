---
title: "Ubuntu 20.04 - Se cae la sesión cuando apago y prendo el monitor"
date: 2020-07-23
forum: Software
---

### Post by elleon on 2020-07-23
Hola! Espero estar posteando en el lugar correcto.
El tema es el siguiente: estaba funcionando todo sin problemas hasta ayer, 22/07. 
Luego de instalar las siguientes actualizaciones:


```
facundo@razorback:~$ awk '$1=="2020-07-22" && $3=="upgrade"' /var/log/dpkg.log
2020-07-22 13:22:48 upgrade base-files:amd64 11ubuntu5 11ubuntu5.1
2020-07-22 13:22:52 upgrade python3.8-dev:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:52 upgrade libpython3.8-dev:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:53 upgrade libpython3.8:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:54 upgrade python3.8-venv:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:55 upgrade python3.8:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:56 upgrade libpython3.8-stdlib:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:57 upgrade python3.8-minimal:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:58 upgrade libpython3.8-minimal:amd64 3.8.2-1ubuntu1.1 3.8.2-1ubuntu1.2
2020-07-22 13:22:59 upgrade libpulse-dev:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:00 upgrade libpulse-mainloop-glib0:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:01 upgrade libpulsedsp:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:01 upgrade pulseaudio-utils:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:02 upgrade pulseaudio-module-bluetooth:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:03 upgrade pulseaudio:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:05 upgrade libpulse0:amd64 1:13.99.1-1ubuntu3.4 1:13.99.1-1ubuntu3.5
2020-07-22 13:23:08 upgrade ubuntu-drivers-common:amd64 1:0.8.1.1 1:0.8.4~0.20.04.1
2020-07-22 13:23:09 upgrade sudo:amd64 1.8.31-1ubuntu1 1.8.31-1ubuntu1.1
2020-07-22 13:23:11 upgrade ubuntu-release-upgrader-gtk:all 1:20.04.21 1:20.04.23
2020-07-22 13:23:12 upgrade ubuntu-release-upgrader-core:all 1:20.04.21 1:20.04.23
2020-07-22 13:23:13 upgrade python3-distupgrade:all 1:20.04.21 1:20.04.23
2020-07-22 13:23:13 upgrade evince-common:all 3.36.5-0ubuntu1 3.36.7-0ubuntu1
2020-07-22 13:23:15 upgrade evince:amd64 3.36.5-0ubuntu1 3.36.7-0ubuntu1
2020-07-22 13:23:17 upgrade libevdocument3-4:amd64 3.36.5-0ubuntu1 3.36.7-0ubuntu1
2020-07-22 13:23:18 upgrade libevview3-3:amd64 3.36.5-0ubuntu1 3.36.7-0ubuntu1
2020-07-22 13:23:19 upgrade libnss3:amd64 2:3.49.1-1ubuntu1.2 2:3.49.1-1ubuntu1.3
2020-07-22 13:23:20 upgrade evolution-data-server:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:21 upgrade libcamel-1.2-62:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:21 upgrade evolution-data-server-common:all 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:22 upgrade libedataserver-1.2-24:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:23 upgrade libecal-2.0-1:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:24 upgrade libedata-cal-2.0-1:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:25 upgrade libebook-contacts-1.2-3:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:26 upgrade libedata-book-1.2-26:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:26 upgrade libebackend-1.2-10:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:27 upgrade libebook-1.2-20:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:28 upgrade libedataserverui-1.2-2:amd64 3.36.3-0ubuntu1 3.36.4-0ubuntu1
2020-07-22 13:23:28 upgrade mutter-common:all 3.36.3-0ubuntu0.20.04.1 3.36.4-0ubuntu0.20.04.1
2020-07-22 13:23:29 upgrade gir1.2-mutter-6:amd64 3.36.3-0ubuntu0.20.04.1 3.36.4-0ubuntu0.20.04.1
2020-07-22 13:23:30 upgrade libmutter-6-0:amd64 3.36.3-0ubuntu0.20.04.1 3.36.4-0ubuntu0.20.04.1
2020-07-22 13:23:31 upgrade im-config:all 0.44-1ubuntu1 0.44-1ubuntu1.1
2020-07-22 13:23:32 upgrade libfprint-2-2:amd64 1:1.90.1+tod1-0ubuntu4 1:1.90.2+tod1-0ubuntu1~20.04.1
2020-07-22 13:23:33 upgrade libfprint-2-tod1:amd64 1:1.90.1+tod1-0ubuntu4 1:1.90.2+tod1-0ubuntu1~20.04.1
2020-07-22 13:23:34 upgrade linux-firmware:all 1.187.1 1.187.2
2020-07-22 13:23:45 upgrade simple-scan:amd64 3.36.0-0ubuntu1 3.36.3-0ubuntu0.20.04.0
2020-07-22 13:23:47 upgrade yaru-theme-gnome-shell:all 20.04.7 20.04.8
2020-07-22 13:23:48 upgrade yaru-theme-gtk:all 20.04.7 20.04.8
2020-07-22 13:23:49 upgrade yaru-theme-icon:all 20.04.7 20.04.8
2020-07-22 13:23:53 upgrade yaru-theme-sound:all 20.04.7 20.04.8
2020-07-22 13:23:54 upgrade mutter:amd64 3.36.3-0ubuntu0.20.04.1 3.36.4-0ubuntu0.20.04.1
2020-07-22 21:46:00 upgrade ffmpeg:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:01 upgrade libavdevice58:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:02 upgrade libavfilter7:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:03 upgrade libswscale5:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:03 upgrade libavformat58:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:04 upgrade libavcodec58:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:05 upgrade libswresample3:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:06 upgrade libpostproc55:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:07 upgrade libavresample4:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:07 upgrade libavutil56:amd64 7:4.2.2-1ubuntu1 7:4.2.4-1ubuntu0.1
2020-07-22 21:46:09 upgrade libsnmp-base:all 5.8+dfsg-2ubuntu2.1 5.8+dfsg-2ubuntu2.2
2020-07-22 21:46:10 upgrade libsnmp35:amd64 5.8+dfsg-2ubuntu2.1 5.8+dfsg-2ubuntu2.2
2020-07-22 21:46:11 upgrade unattended-upgrades:all 2.3 2.3ubuntu0.1
```

Sucede que ahora cada vez que enciendo el monitor (el cual se apaga manualmente o por tiempo de inactividad) me aparece una pantalla con fondo blanco y un texto que dice "Ocurrió un error y el sistema no se puede recuperar". y me obliga a cerrar la sesión y volver a loguearme.
Luego funciona "todo bien" pero el problema persiste.

Tengo la sospecha que el problema viene por el lado de Xorg pero no tengo el conocimiento técnico necesario para determinar si es algo que puedo arreglar o si debo reinstalar Ubuntu.

Algo de ayuda se agradecerá mucho. Saludos.

---


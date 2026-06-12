---
title: "jack server doesn't start"
date: 2012-11-16
forum: Ubuntu Studio
---

### Post by xandler on 2012-11-16
hi,
i installed ubuntu studio 12.10 today but jack doesn't start at all, please help!
thx

xandler

```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]15:38:00.072 Steckfeld deaktiviert.[/COLOR]
 [COLOR=#999999]15:38:00.076 Statistik zurückgesetzt.[/COLOR]
 [COLOR=#cccc99]15:38:00.081 ALSA-Verbindung geändert.[/COLOR]
 [COLOR=#999999]15:38:00.089 D-BUS: Dienst ist verfügbar (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]15:38:00.097 Schaubild der ALSA-Verbindungen geändert.[/COLOR]
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]15:38:01.645 D-BUS: JACK-Server konnte nicht gestartet werden. Tut mir leid[/COLOR]
 Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Fri Nov 16 15:38:01 2012: Starting jack server...
 Fri Nov 16 15:38:01 2012: Jack: Server `default' registered
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitClients
 Fri Nov 16 15:38:01 2012: JACK server starting in realtime mode with priority 10
 Fri Nov 16 15:38:01 2012: Jack: JackShmMem::new index = 0 attached = 1335e000 size = 82274202 
 Fri Nov 16 15:38:01 2012: Jack: JackShmMem::new placement size = 13047706
 Fri Nov 16 15:38:01 2012: Jack: Succeeded in locking 82274202 byte memory area
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitClients
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::InitClients
 Fri Nov 16 15:38:01 2012: Jack: JackShmMem::new index = 1 attached = 2054c000 size = 994 
 Fri Nov 16 15:38:01 2012: Jack: Succeeded in locking 994 byte memory area
 Fri Nov 16 15:38:01 2012: Jack: JackPosixThread::StartImp : create non RT thread
 Fri Nov 16 15:38:01 2012: Jack: JackPosixThread::ThreadHandler : start
 Fri Nov 16 15:38:01 2012: Jack: capture device hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: playback device hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: playback device hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: capture device hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: apparent rate = 44100
 Fri Nov 16 15:38:01 2012: Jack: frames per period = 1024
 Fri Nov 16 15:38:01 2012: Jack: JackDriver::Open capture_driver_name = hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: JackDriver::Open playback_driver_name = hw:0,0
 Fri Nov 16 15:38:01 2012: Jack: Check protocol client = 8 server = 8
 Fri Nov 16 15:38:01 2012: Jack: JackEngine::ClientInternalOpen: name = system
 Fri Nov 16 15:38:01 2012: Jack: JackEngine::AllocateRefNum ref = 0
 Fri Nov 16 15:38:01 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
 Fri Nov 16 15:38:01 2012: Jack: JackEngine::NotifyAddClient: name = system
 Fri Nov 16 15:38:01 2012: Jack: JackGraphManager::SetBufferSize size = 1024
 Fri Nov 16 15:38:01 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
 Fri Nov 16 15:38:01 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Fri Nov 16 15:38:01 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
 Fri Nov 16 15:38:01 2012: control device hw:0
 Fri Nov 16 15:38:01 2012: control device hw:0
 Fri Nov 16 15:38:01 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Fri Nov 16 15:38:01 2012: [1m[31mERROR: Audio device hw:0,0 cannot be acquired...[0m
 Fri Nov 16 15:38:01 2012: Jack: ~JackDriver
 Fri Nov 16 15:38:01 2012: [1m[31mERROR: Cannot initialize driver[0m
 Fri Nov 16 15:38:01 2012: Jack: no message buffer overruns
 Fri Nov 16 15:38:01 2012: Jack: JackPosixThread::Stop
 Fri Nov 16 15:38:01 2012: Jack: JackPosixThread::ThreadHandler : exit
 Fri Nov 16 15:38:01 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Fri Nov 16 15:38:01 2012: Jack: Succeeded in unlocking 82274202 byte memory area
 Fri Nov 16 15:38:01 2012: Jack: JackShmMem::delete size = 0 index = 0
 Fri Nov 16 15:38:01 2012: Jack: ~JackDriver
 Fri Nov 16 15:38:01 2012: Jack: Succeeded in unlocking 994 byte memory area
 Fri Nov 16 15:38:01 2012: Jack: JackShmMem::delete size = 0 index = 1
 Fri Nov 16 15:38:01 2012: Jack: Cleaning up shared memory
 Fri Nov 16 15:38:01 2012: Jack: Cleaning up files
 Fri Nov 16 15:38:01 2012: Jack: Unregistering server `default'
 Fri Nov 16 15:38:01 2012: [1m[31mERROR: Failed to open server[0m
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:5580): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Fri Nov 16 15:38:02 2012: Saving settings to "/home/alexander/.config/jack/conf.xml" ...
 [COLOR=#ff0000]15:38:05.155 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Gesamtbetrieb schlug fehl. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.[/COLOR]
 Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
 Cannot connect to server request channel
 jack server is not running or cannot be started

```

---


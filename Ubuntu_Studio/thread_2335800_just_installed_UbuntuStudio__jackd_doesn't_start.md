---
title: "just installed UbuntuStudio : jackd doesn't start"
date: 2016-09-01
forum: Ubuntu Studio
---

### Post by dario-marrini on 2016-09-01
Hi everybody,
I'm trying to use ubuntustudio to avoid configuration problem, but just installed I have the first one : jackd doesn't start; I tried to read many web pages but I didn't find anything helpful.

here the log :

[COLOR=#999999]15:30:32.269 Resetta le statistiche.[/COLOR]
[COLOR=#cccc99]15:30:32.296 Connessioni di ALSA cambiate.[/COLOR]
[COLOR=#999999]15:30:32.298 D-BUS: Servizio disponibile (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
[COLOR=#66cc99]15:30:32.442 Cambiamento nel grafico delle connessioni di ALSA.[/COLOR]
[COLOR=#ff0000]15:30:33.941 D-BUS: il server JACK non può essere avviato. Mi dispiace[/COLOR]
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
Thu Sep  1 15:30:33 2016: Starting jack server...
Thu Sep  1 15:30:33 2016: JACK server starting in realtime mode with priority 10
Thu Sep  1 15:30:33 2016: self-connect-mode is "Don't restrict self connect requests"
Thu Sep  1 15:30:33 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Thu Sep  1 15:30:33 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Thu Sep  1 15:30:33 2016: ERROR: Audio device hw:0 cannot be acquired...
Thu Sep  1 15:30:33 2016: ERROR: Cannot initialize driver
Thu Sep  1 15:30:33 2016: ERROR: JackServer::Open failed with -1
Thu Sep  1 15:30:33 2016: ERROR: Failed to open server
Thu Sep  1 15:30:35 2016: Saving settings to "/home/dario/.config/jack/conf.xml" ...
[COLOR=#ff0000]15:30:50.041 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni.[/COLOR]
Cannot connect to server socket err = File o directory non esistente
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock

I hope your help

bye

dario

---

### Post by CrocoDuck on 2016-09-02
Give us the outputs of these commands:

```

cat .jackdrc
aplay -l
arecord -l

```

---


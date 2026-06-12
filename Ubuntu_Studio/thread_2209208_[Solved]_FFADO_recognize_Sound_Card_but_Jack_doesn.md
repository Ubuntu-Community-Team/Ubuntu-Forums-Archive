---
title: "[Solved] FFADO recognize Sound Card but Jack doesn't start"
date: 2014-03-04
forum: Ubuntu Studio
---

### Post by Massimo_Morelli on 2014-03-04
Hi guys,

I do not know if this is the right section to show my trouble.

Untill 2 weks ago I used a Notebook HP to produce my music and with these everytings works fine, but now i've bought a new PC tower that i've assembled.

The  trouble is with my firewire sound card Saffire Pro 24 DSP. It is  recognaized by FFADO driver but, when a press  start on Jack I notice that the green led "FW" of my sound card turns  on, than jack stops and the led turns off.
So, the message window of jack says:

```
14:57:31.174 Patchbay deactivated.
14:57:31.176 Reset statistics .
Connections 14:57:31.182 ALSA changed.
14:57:31.221 D-BUS : Service available (org.jackaudio.service jackdbus ) .
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
14:57:31.226 Changing the graph of connections of ALSA.
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
14:58:14.140 D-BUS : JACK server can not be started . I'm sorry
Tue March 4 14:57:49 2014: Starting jack server ...
Tue March 4 14:57:49 2014: JACK server starting in realtime mode with priority 10
Tue March 4 14:57:49 2014: Jack: JackPosixThread :: StartImp : create non- RT thread
Tue March 4 14:57:49 2014: Jack: JackPosixThread :: ThreadHandler : start
Tue March 4 14:57:49 2014: Jack: JackDriver :: Open capture_driver_name =
Tue March 4 14:57:49 2014: Jack: JackDriver :: Open playback_driver_name =
Tue March 4 14:57:49 2014: Jack: Check protocol client- server = 8 = 8
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientInternalOpen : name = system
Tue March 4 14:57:49 2014: Jack: JackEngine :: AllocateRefNum ref = 0
Tue March 4 14:57:49 2014: Jack: JackPosixSemaphore :: Allocate name = val = 0 jack_sem.0_default_system
Tue March 4 14:57:49 2014: Jack: JackEngine :: NotifyAddClient : name = system
Tue March 4 14:57:49 2014: Jack: JackGraphManager :: SetBufferSize size = 128
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: DirectConnect first: ref1 = 0 ref2 = 0
Tue March 4 14:57:49 2014: Jack: JackGraphManager :: ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue March 4 14:57:49 2014: Jack: JackDriver :: SetupDriverSync driver sem in flush mode
Tue March 4 14:57:49 2014: Jack: JackSocketServerChannel :: Open
Tue March 4 14:57:49 2014: Jack: JackServerSocket :: Bind: addr.sun_path / dev/shm/jack_default_0_0
Tue March 4 14:57:49 2014: Jack: JackSocketServerChannel :: BuildPoolTable size = 1
Tue March 4 14:57:49 2014: Jack: JackEngine :: Open
Tue March 4 14:57:49 2014: Jack: JackClientSocket :: Connect : addr.sun_path / dev/shm/jack_default_0_0
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientInternalOpen : name = freewheel
Tue March 4 14:57:49 2014: Jack: JackEngine :: AllocateRefNum ref = 1
Tue March 4 14:57:49 2014: Jack: JackPosixSemaphore :: Allocate name = val = 0 jack_sem.0_default_freewheel
Tue March 4 14:57:49 2014: Jack: JackEngine :: NotifyAddClient : name = freewheel
Tue March 4 14:57:49 2014: Jack: JackDriver :: ClientNotify ref = 1 driver = name = freewheel system notify = 0
Tue March 4 14:57:49 2014: Jack: JackDriver :: ClientNotify ref = 0 driver = freewheel name = system notify = 0
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: DirectConnect first: ref1 = 1 ref2 = 1
Tue March 4 14:57:49 2014: Jack: JackGraphManager :: ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Tue March 4 14:57:49 2014: Jack: JackDriver :: SetupDriverSync driver sem in flush mode
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fBufferSize 128 fSampleRate 44100
Tue March 4 14:57:49 2014: ERROR : firewire MSG : Streaming thread running with Realtime scheduling , priority 15
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 01 (Analog / By : 03) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 01 (Analog / By : 03) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 1  name = firewire_pcm : 00130e04020040a9_1394 : 01 (Analog / By : 03) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 1
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 1
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 02 (Analog / By : 04) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 02 (Analog / By : 04) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 2  name = firewire_pcm : 00130e04020040a9_1394 : 02 (Analog / By : 04) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 2
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i ] 2
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 03 (Analog / By : 01) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 03 (Analog / By : 01) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 3  name = firewire_pcm : 00130e04020040a9_1394 : 03 (Analog / By : 01) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 3
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 3
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 04 (Analog / By : 02) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 04 (Analog / By : 02) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 4  name = firewire_pcm : 00130e04020040a9_1394 : 04 (Analog / By : 02) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 4
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 4
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 05 ( SPDIF / In : 01) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 05 ( SPDIF / In : 01) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 5  name = firewire_pcm : 00130e04020040a9_1394 : 05 ( SPDIF / In : 01) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 5
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 5
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 06 ( SPDIF / In : 02) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 06 ( SPDIF / In : 02) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 6  name = firewire_pcm : 00130e04020040a9_1394 : 06 ( SPDIF / In : 02) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 6
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 6
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 07 ( ADAT / By : 01) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 07 ( ADAT / By : 01) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 7  name = firewire_pcm : 00130e04020040a9_1394 : 07 ( ADAT / By : 01) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 7
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 7
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 08 ( ADAT / By : 02) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 08 ( ADAT / By : 02) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 8  name = firewire_pcm : 00130e04020040a9_1394 : 08 ( ADAT / By : 02) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 8
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 8
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 09 ( ADAT / By : 03) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 09 ( ADAT / By : 03) _in type =  32 bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 9  name = firewire_pcm : 00130e04020040a9_1394 : 09 ( ADAT / By : 03) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 9
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 10 (ADAT / By : 04) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 10 (ADAT / By : 04) _in type = 32  bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 10  name = firewire_pcm : 00130e04020040a9_1394 : 10 (ADAT / By : 04) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 10
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 10
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 11 (ADAT / In , 05) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 11 (ADAT / In , 05) _in type = 32  bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 11  name = firewire_pcm : 00130e04020040a9_1394 : 11 (ADAT / In , 05) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 11
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 11
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 12 (ADAT / By : 06) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 12 (ADAT / By : 06) _in type = 32  bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 12  name = firewire_pcm : 00130e04020040a9_1394 : 12 (ADAT / By : 06) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 12
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i ] 12
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 13 (ADAT / By : 07) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 13 (ADAT / By : 07) _in type = 32  bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 13  name = firewire_pcm : 00130e04020040a9_1394 : 13 (ADAT / By : 07) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 13
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 13
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 14 (ADAT / By : 08) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 14 (ADAT / By : 08) _in type = 32  bit float mono audio flags = 22 buffer_size = 128
Tue March 4  14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux port_index = 14  name = firewire_pcm : 00130e04020040a9_1394 : 14 (ADAT / By : 08) _in  type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 14
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i ] 14
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 15 (Mute : 00) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 15 (Mute : 00) _in type = 32 bit  float mono audio flags = 22 buffer_size = 128
Tue March 4 14:57:49  2014: Jack: JackGraphManager :: AllocatePortAux port_index = 15 name =  firewire_pcm : 00130e04020040a9_1394 : 15 (Mute : 00) _in type = 32 bit  float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 15
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 15
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio capture  port firewire_pcm : 00130e04020040a9_1394 : 16 (Mute : 00) _in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 16 (Mute : 00) _in type = 32 bit  float mono audio flags = 22 buffer_size = 128
Tue March 4 14:57:49  2014: Jack: JackGraphManager :: AllocatePortAux port_index = 16 name =  firewire_pcm : 00130e04020040a9_1394 : 16 (Mute : 00) _in type = 32 bit  float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 16
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i ] 16
Tue March 4 14:57:49 2014: ERROR : firewire MSG : Registering capture midi port firewire_pcm : 00130e04020040a9_midi 0_in
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_midi 0_in type = 8 bit raw midi flags =  22 buffer_size = 128
Tue March 4 14:57:49 2014: Jack:  JackGraphManager :: AllocatePortAux port_index = 17 name = firewire_pcm :  00130e04020040a9_midi 0_in type = 8 bit raw midi
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddOutputPort ref = 0 port = 17
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fCapturePortList [i] 17
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 01 (Analog / Out :  01) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 01 (Analog / Out :  01) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 18 name = firewire_pcm : 00130e04020040a9_1394 : 01 (Analog  / Out : 01) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 18
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 18
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 02 (Analog / Out :  02) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 02 (Analog / Out :  02) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 19 name = firewire_pcm : 00130e04020040a9_1394 : 02 (Analog  / Out : 02) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 19
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 19
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 03 (Analog / Out :  03) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 03 (Analog / Out :  03) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 20 name = firewire_pcm : 00130e04020040a9_1394 : 03 (Analog  / Out : 03) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 20
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i] 20
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 04 (Analog / Out :  04) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 04 (Analog / Out :  04) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 21 name = firewire_pcm : 00130e04020040a9_1394 : 04 (Analog  / Out : 04) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 21
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 21
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 05 (Analog / Out :  05) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 05 (Analog / Out :  05) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 22 name = firewire_pcm : 00130e04020040a9_1394 : 05 (Analog  / Out : 05) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 22
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 22
Tue  March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio  playback port firewire_pcm : 00130e04020040a9_1394 : 06 (Analog / Out :  06) _OUT
Tue March 4 14:57:49 2014: Jack: JackEngine :: PortRegister  ref = 0 name = firewire_pcm : 00130e04020040a9_1394 : 06 (Analog / Out :  06) _OUT type = 32 bit float mono audio flags = 21 buffer_size = 128
Tue  March 4 14:57:49 2014: Jack: JackGraphManager :: AllocatePortAux  port_index = 23 name = firewire_pcm : 00130e04020040a9_1394 : 06 (Analog  / Out : 06) _OUT type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 23
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 23
Tue March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio playback port firewire_pcm : 00130e04020040a9_1394 : 07_out
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 07_out type = 32 bit float mono  audio flags = 21 buffer_size = 128
Tue March 4 14:57:49 2014: Jack:  JackGraphManager :: AllocatePortAux port_index = 24 name = firewire_pcm :  00130e04020040a9_1394 : 07_out type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 24
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i] 24
Tue March 4 14:57:49 2014: ERROR : firewire MSG : Registering audio playback port firewire_pcm : 00130e04020040a9_1394 : 08_out
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_1394 : 08_out type = 32 bit float mono  audio flags = 21 buffer_size = 128
Tue March 4 14:57:49 2014: Jack:  JackGraphManager :: AllocatePortAux port_index = 25 name = firewire_pcm :  00130e04020040a9_1394 : 08_out type = 32 bit float mono audio
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 25
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 25
Tue March 4 14:57:49 2014: ERROR : firewire MSG : Registering playback midi port firewire_pcm : 00130e04020040a9_midi 0_out
Tue  March 4 14:57:49 2014: Jack: JackEngine :: PortRegister ref = 0 name =  firewire_pcm : 00130e04020040a9_midi 0_out type = 8 bit raw midi flags =  21 buffer_size = 128
Tue March 4 14:57:49 2014: Jack:  JackGraphManager :: AllocatePortAux port_index = 26 name = firewire_pcm :  00130e04020040a9_midi 0_out type = 8 bit raw midi
Tue March 4 14:57:49 2014: Jack: JackConnectionManager :: AddInputPort ref = 0 port = 26
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackEngine :: ClientNotify : no callback for notification = 9
Tue March 4 14:57:49 2014: Jack: JackFFADODriver :: Attach fPlaybackPortList [i ] 26
Tue March 4 14:57:49 2014: Jack: Clock source : system clock via clock_gettime
Tue March 4 14:57:49 2014: Jack: JackServer :: Start
Tue March 4 14:57:49 2014: Jack: JackThreadedDriver :: Start
Tue March 4 14:58:02 2014: ERROR : firewire ERR : Could not start streaming threads
Tue March 4 14:58:02 2014: ERROR : Can not start driver
Tue March 4 14:58:02 2014: ERROR : JackServer :: Start () failed with -1
Tue March 4 14:58:02 2014: ERROR : Failed to start server
Tue March 4 14:58:02 2014: Jack: JackServer :: Close
Tue March 4 14:58:02 2014: Jack: JackServerSocket :: Close / dev/shm/jack_default_0_0
Tue March 4 14:58:02 2014: Jack: JackFFADODriver :: Detach
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1945 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
14:58:19.792  JACK was not able to start as a client. - Operation failed . - Could  not connect to JACK server . Check the message window for more  information.
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel

```

Any suggestion?

---

### Post by Massimo_Morelli on 2014-03-04
This is the reply of the command ffado-diag

```
emenems@emenems-studio:~$ ffado-diag


FFADO diagnostic utility 2.1.9999-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.11.0-17-lowlatency
    Preempt (low latency)... True
    RT patched.............. False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
  /dev/fw* permissions:
crw-------  1 root root  249, 0 mar  4 18:25 /dev/fw0
crw-rw----+ 1 root audio 249, 1 mar  4 18:25 /dev/fw1
  User IDs:
uid=1000(emenems) gid=1000(emenems) gruppi=1000(emenems),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),108(lpadmin),123(sambashare)
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
   g++ ............... sh: 1: g++: not found
   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags ........... Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   g++ ............... g++ (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.9.6 for Qt version 4.8.3
   jackd ............. sh: 1: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.9
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.2
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.6.8
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 uname -a...
   Linux emenems-studio 3.11.0-17-lowlatency #11-Ubuntu SMP PREEMPT Fri Feb 7 00:51:05 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Hardware...
   Host controllers:
03:00.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller [1033:00f2] (rev 01) (prog-if 10 [OHCI])
    Subsystem: NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller [1033:00f2]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (5000ns min, 11000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci

   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Stepping:              3
CPU MHz:               3101.000
BogoMIPS:              6197.69
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:      [28, 0, 0, 0], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [3, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:       [1, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:       [3, 1, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count:     [11, 4, 16, 2], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   18: PID:  None, count: [64362, 42588, 2437, 2], Sched None (priority None), drivers: ['firewire_ohci']
 IRQ   23: PID:  None, count:     [12, 8, 14, 3], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   40: PID:  None, count: [12234, 89004, 18, 292], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   41: PID:  None, count: [1628, 4173, 8761, 262], Sched None (priority None), drivers: ['ahci']
 IRQ   42: PID:  None, count:   [14, 0, 1224, 2], Sched None (priority None), drivers: ['eth0']
 IRQ   43: PID:  None, count: [759, 161, 120, 125], Sched None (priority None), drivers: ['i915']
 IRQ   44: PID:  None, count:      [11, 0, 0, 0], Sched None (priority None), drivers: ['mei_me']
 IRQ   45: PID:  None, count:    [218, 1, 11, 4], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   46: PID:  None, count:    [536, 3, 14, 0], Sched None (priority None), drivers: ['snd_hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
If running a kernel earlier than 2.6.37 and problems are experienced, either 
try with the old Firewire kernel stack or upgrade to a newer kernel 
(preferrably 2.6.37 or later).


```



This is from ffado-test Discover 


```
emenems@emenems-studio:~$ ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.1.9999-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

1393956542713398: Warning (dice_eap.cpp)[1791] read: No routes found. Base 0x7, offset 0x4000
1393956542741583: Warning (dice_eap.cpp)[1226] updateNameCache: What is this function about?
 DICE Parameter Space info:
  Global  : offset=0x0028 size=0360
  TX      : offset=0x0190 size=0568
                nb=   1 size=0280
  RX      : offset=0x03C8 size=1128
                nb=   1 size=0280
  UNUSED1 : offset=0x0830 size=0016
  UNUSED2 : offset=0x0000 size=0000
 Global param space:
  Owner            : 0x00000000FFFF0000
  Notification     : 0x00000040
  Nick name        : Saffire Pro 24-D
  Clock Select     : 0x01 0x0C
  Enable           : false
  Clock Status     : locked 0x01
  Extended Status  : 0x00000000
  Samplerate       : 0x0000AC44 (44100)
  Version          : 0x01000400
  Version          : 0x01000400 (1.0.4.0)
  Clock caps       : 0x112C001E
  Clock sources    :
    AES1
    AES2
    SPDIF-OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    Unused
    Unused
    Unused
    Unused
    Internal
 TX param space:
  Nb of xmit        : 1
  Transmitter 0:
   ISO channel       :  -1
   ISO speed         :   2
   Nb audio channels :  16
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     ADAT 1
     ADAT 2
     ADAT 3
     ADAT 4
     ADAT 5
     ADAT 6
     ADAT 7
     ADAT 8
     Loop 1
     Loop 2
 RX param space:
  Nb of recv        : 1
  Receiver 0:
   ISO channel       :   1
   Sequence start    :   0
   Nb audio channels :   8
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     Mon 1
     Mon 2
     Line 3
     Line 4
     Line 5
     Line 6
     SPDIF L
     SPDIF R
no message buffer overruns
```

and this from ffado-test ListDevices


 ```
emenems@emenems-studio:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.1.9999-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e04020040a9  0x0000130E  0x00000008   Focusrite - SAFFIRE_PRO_24DSP
no message buffer overruns
```

---

### Post by CrocoDuck on 2014-03-06
Hi! Give the output of

```

lspci -vnn

```

and

```

cat .jackdrc

```

---

### Post by jhay2 on 2014-03-07
Have you already tried to run jack first using? 
jack_control start ?

If not . Execute the command . The check if errors still there

---

### Post by Massimo_Morelli on 2014-03-08
Hi...sorry for my delay...

this is the output of lspci -vnn

```
emenems@emenems-studio:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
    Subsystem: ASRock Incorporation Device [1849:0c00]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Device [1849:0412]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: ASRock Incorporation Device [1849:0c0c]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0534000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05) (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device [1849:8c31]
    Flags: bus master, medium devsel, latency 0, IRQ 40
    Memory at f0520000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: ASRock Incorporation Device [1849:8c3a]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f053f000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: ASRock Incorporation Device [1849:153b]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f053d000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation Device [1849:8c2d]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f053c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: ASRock Incorporation Device [1849:d892]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0530000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dfa00000-dfbfffff
    Prefetchable memory behind bridge: 00000000dfc00000-00000000dfdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=32
    Memory behind bridge: f0400000-f04fffff
    Capabilities: <access denied>

00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05) (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation Device [1849:8c26]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f053b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
    Subsystem: ASRock Incorporation Device [1849:8c44]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device [1849:8c02]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f060 [size=32]
    Memory at f053a000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: ASRock Incorporation Device [1849:8c22]
    Flags: medium devsel, IRQ 11
    Memory at f0539000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]

02:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: f0400000-f04fffff
    Capabilities: <access denied>

03:00.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller [1033:00f2] (rev 01) (prog-if 10 [OHCI])
    Subsystem: NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller [1033:00f2]
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci


```



and thi of cat .jackdrc

```
emenems@emenems-studio:~$ cat .jackdrc
cat: .jackdrc: File o directory non esistente

```

That means unknown file or directory

---

### Post by Massimo_Morelli on 2014-03-08
I've trying this:

I've open ffado mixer  and it has recognaized the sound card, after in the terminal I did jack_control start and this is the output:

```
emenems@emenems-studio:~$ jack_control start
--- start
emenems@emenems-studio:~$
```

than I opened qjackctl and it was initiated ith 48000 and in the panel of connection i sow pulseaudio, but in the option panel there was select firewire and 44100....
I stopped jack and tried to restart it but it was locked as usual

---

### Post by CrocoDuck on 2014-03-09
Interesting... you device should work. Give also the output of these ones:

```

ls /usr/bin | grep jackd

```

```

groups

```

I suspect that the configuration could be a little messed up.

---

### Post by Massimo_Morelli on 2014-03-09
It's incredible!

i don't known whats happened but after that I give ls /usr/bin | grep jackd and groups I tyied to start again jack and this time jack has started and everything works perfectly




Do I misunderstood or those were just diagnostic commands?

Can you explane me?

Anyway i'm very glad!

the output of the command was theese:


ls /usr/bin | grep jackd

```
emenems@emenems-studio:~$ ls /usr/bin | grep jackd
jackd
jackdbus
emenems@emenems-studio:~$
```

groups
```
emenems@emenems-studio:~$ groups
emenems adm cdrom sudo audio dip plugdev lpadmin sambashare
emenems@emenems-studio:~$
```

---

### Post by jejeman on 2014-03-09
>  Do I misunderstood or those were just diagnostic commands?Those are just info commands.

---

### Post by Massimo_Morelli on 2014-03-09
In fact....

after a system reboot, jack does't start...  :(:confused:

and this is the log of jack

notice : this is a google translation 'cause  it would be in Italian

```
15:39:53.420 Patchbay deactivated.
15:39:53.425 Reset statistics .
Connections 15:39:53.437 ALSA changed.
15:39:53.475 D-BUS : Service available ( aka org.jackaudio.service jackdbus ) .
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
15:40:31.742 D-BUS : JACK server can not be started . I'm sorry
Sun March 9 15:40:06 2014: Starting jack server ...
Sun March 9 15:40:06 2014: JACK server starting in realtime mode with priority 10
Sun March 9 15:40:16 2014: ERROR : firewire ERR : Could not start streaming threads
Sun March 9 15:40:16 2014: ERROR : Can not start driver
Sun March 9 15:40:16 2014: ERROR : JackServer :: Start () failed with -1
Sun March 9 15:40:16 2014: ERROR : Failed to start server
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
15:40:34.972 JACK was not able to start as a client. - Operation failed . - Could not connect to JACK server . Check the message window for more information.
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1619 ) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
```

---

### Post by CrocoDuck on 2014-03-09
> **Massimo_Morelli said:**
> 
Can you explane me?


The commands I suggested are mean to understand if jack executables are in the right place and if your user is in the audio group, which is. Try to launch jack using this:

```

/usr/bin/jackd -P89 -t5000 -dfirewire -r96000 -p128 -n3

```

---

### Post by Massimo_Morelli on 2014-03-10
Thanks for your help guys!

The command you sugget does't work and this is the output:

```
emenems@emenems-studio:~$ /usr/bin/jackd -P89 -t5000 -dfirewire -r96000 -p128 -n3
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 89
libffado 2.1.9999- built Feb  1 2013 04:49:43
1394443700373791: Warning (dice_eap.cpp)[1791] read: No routes found. Base 0x7, offset 0x4000
1394443700406075: Warning (dice_eap.cpp)[1226] updateNameCache: What is this function about?
 DICE Parameter Space info:
  Global  : offset=0x0028 size=0360
  TX      : offset=0x0190 size=0568
                nb=   1 size=0280
  RX      : offset=0x03C8 size=1128
                nb=   1 size=0280
  UNUSED1 : offset=0x0830 size=0016
  UNUSED2 : offset=0x0000 size=0000
 Global param space:
  Owner            : 0x00000000FFFF0000
  Notification     : 0x00000000
  Nick name        : Saffire Pro 24-D
  Clock Select     : 0x02 0x0C
  Enable           : false
  Clock Status     : locked 0x01
  Extended Status  : 0x00000000
  Samplerate       : 0x0000AC44 (44100)
  Version          : 0x01000400
  Version          : 0x01000400 (1.0.4.0)
  Clock caps       : 0x112C001E
  Clock sources    :
    AES1
    AES2
    SPDIF-OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    Unused
    Unused
    Unused
    Unused
    Internal
 TX param space:
  Nb of xmit        : 1
  Transmitter 0:
   ISO channel       :  -1
   ISO speed         :   2
   Nb audio channels :  16
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     ADAT 1
     ADAT 2
     ADAT 3
     ADAT 4
     ADAT 5
     ADAT 6
     ADAT 7
     ADAT 8
     Loop 1
     Loop 2
 RX param space:
  Nb of recv        : 1
  Receiver 0:
   ISO channel       :  -1
   Sequence start    :   0
   Nb audio channels :   8
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     Mon 1
     Mon 2
     Line 3
     Line 4
     Line 5
     Line 6
     SPDIF L
     SPDIF R
Setting sample rate: 96000
 DICE Parameter Space info:
  Global  : offset=0x0028 size=0360
  TX      : offset=0x0190 size=0568
                nb=   1 size=0280
  RX      : offset=0x03C8 size=1128
                nb=   1 size=0280
  UNUSED1 : offset=0x0830 size=0016
  UNUSED2 : offset=0x0000 size=0000
 Global param space:
  Owner            : 0xE0000000FFC1FFFF
  Notification     : 0x00000010
  Nick name        : Saffire Pro 24-D
  Clock Select     : 0x04 0x0C
  Enable           : false
  Clock Status     : locked 0x04
  Extended Status  : 0x00000000
  Samplerate       : 0x00017700 (96000)
  Version          : 0x01000400
  Version          : 0x01000400 (1.0.4.0)
  Clock caps       : 0x112C001E
  Clock sources    :
    AES1
    AES2
    SPDIF-OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    Unused
    Unused
    Unused
    Unused
    Internal
 TX param space:
  Nb of xmit        : 1
  Transmitter 0:
   ISO channel       :  -1
   ISO speed         :   2
   Nb audio channels :  12
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     ADAT 1
     ADAT 2
     ADAT 3
     ADAT 4
     Loop 1
     Loop 2
 RX param space:
  Nb of recv        : 1
  Receiver 0:
   ISO channel       :  -1
   Sequence start    :   0
   Nb audio channels :   8
   Nb midi channels  :   1
   AC3 caps          : 0x00000000
   AC3 enable        : 0x00000000
   Channel names     :
     Mon 1
     Mon 2
     Line 3
     Line 4
     Line 5
     Line 6
     SPDIF L
     SPDIF R
firewire ERR: Could not start streaming threads
Cannot start driver
JackServer::Start() failed with -1
Failed to start server


```

---

### Post by CrocoDuck on 2014-03-10
Uhm... Have a look at this: [http://forum.ubuntu-it.org/viewtopic.php?t=411088](http://forum.ubuntu-it.org/viewtopic.php?t=411088) and this: [http://www.ffado.org/?q=node/1204](http://www.ffado.org/?q=node/1204) . I've got some questions about your computer: is the firewire port emebedded in the motherboard? Is it a PCI firewire extension? A PCIe? How did you install and configured your system? Is your system ubuntu studio? If you customized a standard ubuntu installation check again this page: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) . I can't understan up to now if you are experiencing an instable driver issue or a configuration issue.

---

### Post by jejeman on 2014-03-10
I don't have the same firewire device, but:
I needed to first turn on firewire device, and than to boot OS in order to firewire card work with JACK.
I needed to disable jackd_dbus, pluseaudio etc.
It knows to be a pain.

Is it working on Live Ubuntu Studio system? I'm asking this because JACK "gets dirty" and the device is never working again. Never could find out why or how.

---

### Post by Massimo_Morelli on 2014-03-10
The firewire is a PCI card this is fro lspci in terminal:
```
03:00.0 FireWire (IEEE 1394): NEC Corporation uPD72874 [Firewarden] IEEE1394a OHCI 1.1 Link/3-port PHY Controller (rev 01)
```

My OS is Ubuntu Studio 13.10 downloaded from the site and instll in the pc by a bootable usb, but I have tryied also KXStudio with the same result

I don't know what is the problem but between configuration and instable driver i think is the second 'cause the configuration is identical to the one I have on the laptop, and in the laptop everythings works fine
Even the fact that Jack started yesterday without changing anything makes me think it is a driver issue

@ jejeman
My sound card is powered by the pc with 6pin firewire cable and ffado recognize the sond card everytime I turn on the sytem.
How do you disable jackd_dbus, pluseaudio etc? What's etc? (I mean what else do you do)

---

### Post by Massimo_Morelli on 2014-03-10
**@** CrocoDuck

The first post you suggest is in italian, luckily is my leanguage, but there is't nothing interesting, it's a different problem
The second... I had seen i some days ago and I tried to follow what is suggested, but I am not able to understand what should I do

---

### Post by jejeman on 2014-03-10
Yes, my card is also powered via firewire bus. I turn on power switch as soon as the PC starts, before GURB and US booting.
Etc is whatever I figure out that is better for the things to work. Like the thing with powering card before US boots. This is practically nonsense, it should work no metter when I turn it on, but what to do...

Jackd Dbus I turn it off in QJackctl settings. But if you start jackd via CLI this should not metter.
Pulseaudio is not a problem, but pulseaudio jack sink is. You can turn pulseaudio off with
```
echo "autospawn = no" > ~/.pulse/client.conf
pulseaudio -k
```
> ffado recognize the sond card everytime I turn on the sytem.So it was here too. But JACK wont work with it.
I didn't had the strength to resolve that issue the proper way, since I found my "voodoo" workaround.

---

### Post by CrocoDuck on 2014-03-10
> **Massimo_Morelli said:**
> 
My sound card is powered by the pc with 6pin firewire cable

With my firewire soundcard I had basically your same troubles when trying to make it work. I was sure that the powering through the firewire cable was working, because the leds were turned up and ffado recognized the device. I found that somehow the power supplied by the computer was insufficient. So I plugged the external DC power supply and it started working like a charm. If you didn't, have a try. I linked that italian page to you because the blacklist advice. It is common to have conflicts with other audio devices. Have a try also with blacklisting if you didn't.

---

### Post by Massimo_Morelli on 2014-03-10
Ok, before testing the external power and the blacklist I've starting jack without d-bus server option and jack seemed to start, then it stopped and the log is this:

at the end it says: Client name = qjackctl conflits with another running client



```
14:31:40.116 Patchbay deactivated.
14:31:40.117 Reset statistics .
Connections 14:31:40.122 ALSA changed.
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
14:31:40.128 Changing the graph of connections of ALSA.
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
14:31:46.201 JACK is starting ...
14:31:46.201 / usr / bin / jackd - dfirewire - r44100 - p1024 - n3
Can not connect to server socket err = File or directory does not exist
Can not connect to server request channel
jack server is not running or can not be started
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
14:31:46.207 JACK was started with PID = 1574.
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
no message buffer overruns
no message buffer overruns
no message buffer overruns
Jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others .
Copyright 2004-2013 Graeme .
Jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software , and you are welcome to redistribute it
Under Certain Conditions ; see the file COPYING for details
JACK server starting in realtime mode with priority 10
libffado 2.1.9999 built - February 1st 2013 04:49:43
1394458306449620 : ? [ 31mWarning ( dice_eap.cpp ) [ 1791 ] read : No routes found. Base 0x7 , offset 0x4000
? [ 0m1394458306481549 : ? [ 31mWarning ( dice_eap.cpp ) [ 1226 ] updateNameCache : What is this function about?
? [0m DICE Parameter Space info:
  Global : offset = 0x0028 size = 0360
  TX: offset = 0x0190 size = 0568
                nb = 1 size = 0280
  RX: offset = 0x03C8 size = 1128
                nb = 1 size = 0280
  UNUSED1 : offset = 0x0830 size = 0016
  UNUSED2 : offset = 0x0000 size = 0000
 Global param space :
  Owner : 0x00000000FFFF0000
  Notification : 0x00000000
  Nick name : Saffire Pro 24 -D
  Clock Select : 0x02 0x0C
  Enable: false
  Clock Status: Locked 0x01
  Extended Status: 0x00000000
  Samplerate : 0x0000AC44 ( 44100 )
  Version: 0x01000400
  Version: 0x01000400 ( 1.0.4.0 )
  Clock caps: 0x112C001E
  Clock sources:
    AES1
    AES2
    SPDIF -OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    unused
    unused
    unused
    unused
    Internal
 TX param space :
  Nb of xmit : 1
  Transmitter 0 :
   ISO channel: -1
   ISO speed: 2
   Nb audio channels: 16
   Nb midi channels: 1
   AC3 caps: 0x00000000
   AC3 enable: 0x00000000
   Channel names:
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     ADAT 1
     ADAT 2
     ADAT 3
     ADAT 4
     ADAT 5
     ADAT 6
     ADAT 7
     ADAT 8
     loop 1
     loop 2
 RX param space :
  Nb of recv : 1
  Receiver 0:
   ISO channel: -1
   Sequence Start : 0
   Nb audio channels: 8
   Nb midi channels: 1
   AC3 caps: 0x00000000
   AC3 enable: 0x00000000
   Channel names:
     Mon 1
     Mon 2
     line 3
     line 4
     line 5
     line 6
     SPDIF L
     SPDIF R
Setting Sample Rate : 44100
 DICE Parameter Space info:
  Global : offset = 0x0028 size = 0360
  TX: offset = 0x0190 size = 0568
                nb = 1 size = 0280
  RX: offset = 0x03C8 size = 1128
                nb = 1 size = 0280
  UNUSED1 : offset = 0x0830 size = 0016
  UNUSED2 : offset = 0x0000 size = 0000
 Global param space :
  Owner : 0xE0000000FFC1FFFF
  Notification : 0x00000000
  Nick name : Saffire Pro 24 -D
  Clock Select : 0x01 0x0C
  Enable: false
  Clock Status: Locked 0x01
  Extended Status: 0x00000000
  Samplerate : 0x0000AC44 ( 44100 )
  Version: 0x01000400
  Version: 0x01000400 ( 1.0.4.0 )
  Clock caps: 0x112C001E
  Clock sources:
    AES1
    AES2
    SPDIF -OPT
    SPDIF
    AES_ANY
    ADAT
    ADAT_AUX
    Word Clock
    unused
    unused
    unused
    unused
    Internal
 TX param space :
  Nb of xmit : 1
  Transmitter 0 :
   ISO channel: -1
   ISO speed: 2
   Nb audio channels: 16
   Nb midi channels: 1
   AC3 caps: 0x00000000
   AC3 enable: 0x00000000
   Channel names:
     IP 1
     IP 2
     IP 3
     IP 4
     SPDIF L
     SPDIF R
     ADAT 1
     ADAT 2
     ADAT 3
     ADAT 4
     ADAT 5
     ADAT 6
     ADAT 7
     ADAT 8
     loop 1
     loop 2
 RX param space :
  Nb of recv : 1
  Receiver 0:
   ISO channel: -1
   Sequence Start : 0
   Nb audio channels: 8
   Nb midi channels: 1
   AC3 caps: 0x00000000
   AC3 enable: 0x00000000
   Channel names:
     Mon 1
     Mon 2
     line 3
     line 4
     line 5
     line 6
     SPDIF L
     SPDIF R
14:31:56.699 JACK was not able to start as a client. - Operation failed . - Error communicating with the server JACK . Check the message window for more information.
firewire ERR : Could not start streaming threads
Can not start driver
JackServer :: Start () failed with -1
Failed to start server
Can not read socket fd = 18 err = Connection interrupted by the corresponding
CheckRes error
Could not read result type = 22
Client name = qjackctl conflits with another client running
Can not connect to the server
14:32:03.671 JACK is stopping ...
14:32:32.406 JACK is stopping ...
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
( qjackctl : 1564) : Gtk - CRITICAL **: IA__gtk_widget_get_direction : assertion ' GTK_IS_WIDGET ( widget ) ' failed
```

---

### Post by jejeman on 2014-03-10
Kill em all, jackd or qjackctl.

---

### Post by Massimo_Morelli on 2014-03-10
I edit the the blacklist file in this way:
sudo gedit /etc/modprobe.d/blacklist

and write blacklist snd_hda_intel inside the text file...the text file was empty

I connected the external power supply

Nothing is changed

---

### Post by Massimo_Morelli on 2014-03-10
@jejeman sorry, what do you mean?

---

### Post by Massimo_Morelli on 2014-03-10
this is the output from the command lsmod | grep snd:

```
emenems@emenems-studio:~$ lsmod | grep snd
snd_seq_dummy          12798  0 
snd_hda_codec_realtek    51465  1 
snd_hda_codec_hdmi     41276  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_hda_intel          44075  5 
snd_seq                61560  6 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_hda_codec         188696  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               101983  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
soundcore              12680  1 snd
emenems@emenems-studio:~$ 


```

---

### Post by jejeman on 2014-03-10
Well, you need to reboot in order for blacklist to work.

I meant kill all jackd, qjackctl processes, regarding the log comment you outlined. Sometimes processes can hang.

---

### Post by Massimo_Morelli on 2014-03-10
I have reeboot before restarting jack but nothings heppened.

So, I've tried something different.

I've reinstall Ubuntu Studio 13.10 from the bootable usb at the first boot notice something strange:

Top right of screen were there is time date connections username ecc there is the audio icon (like a speaker) but if I click it nothing appears and I don't have audio setting in the settings panel.
Another thing: before to connect the external sound card to pc for the first time after SO reintallation I tried to start jack with alsa and the default settings but jack report the same probem as always

---

### Post by Massimo_Morelli on 2014-03-10
Ok ,I'm able to start jack whit alsa choosing the right card from the arrow to the right of the driver settings

---

### Post by Massimo_Morelli on 2014-03-10
Jack started, without d-bus server option after the new OS reinstallation.

What's this option?

Now I've fear to close jack.....maybe can I leave the pc turn on, forever? :P

What can I' check before closing?

---

### Post by CrocoDuck on 2014-03-10
You should be able to have fun even without the dbus option I guess: [https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#JACK2_D-Bus](https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#JACK2_D-Bus) , [https://wiki.archlinux.org/index.php/D-Bus](https://wiki.archlinux.org/index.php/D-Bus) . Check your configuration file save location (mine is the default one, .jackdrc). That file was missing before. If the installation went smooth then all the configurations should be the default ones. When reinstalling, I suggest to erase the partitions with Gparted during a live session, then reboot and install the actual system. Seems to me that ubuntu mess up things when reinstalling on top of a previus installation.

---

### Post by Massimo_Morelli on 2014-03-10
After a system restart jack does't run anymore...no way

I've try to install Ubuntu Studio 32 bit and at the first boot ffado recognize the sound card as UNKNOWN...opend jack and jack started, but there was some xrun...I stopped it, change settings and jack started whitout xrun in 1 hour.

I thought that 32 bit is neded from my system...turn off the pc, restart again, ffado recognize the sound card as saffire pro 24 dsp, but jack don't start...no way...I have tried changing all kinds of settings...no way

I'm desperate ... I do not know anymore what to do ... it's one week that I'm locked up at home trying and trying 16 hours per day ... I'm very tired    :cry::cry::cry:

---

### Post by CrocoDuck on 2014-03-11
The fact that sometimes it works and a lot of time doesn't is weird. Sometimes a lot of instabilities are caused by the firewire controller chipest in your firewire port or by the bus into wich you put your port. Please, lspci desn't tell if the bus have physical slots or it exists only internally. Are you using a firewire expansion card? If so, you plugged in a PCI slot or in a PCIe one? If so, you may expect instabilities.

---

### Post by Massimo_Morelli on 2014-03-11
Hi   
yes it is a pci firewire card whit chipset Nec corporationu PD72874 on a pci slot of asus z87 pro3.
do you suggest to change the pci firewire card.  If yes what card what chipset do you suggest?

---

### Post by jejeman on 2014-03-11
[http://www.ffado.org/?q=node/251](http://www.ffado.org/?q=node/251)
I don't exactly believe in this chipset thing. But even if a wanted to by TI chip, I can't, because it is not available in my country.
I have NEC chip.

Also, only in AVLinux 6.0 I have managed to use firewire card on my laptop. So, there is a lot involved in software realm, newer kernels won't work at all on that laptop, regarding the RT firewire audio of course.

---

### Post by CrocoDuck on 2014-03-11
Focusrite recommends Texas Instruments or VIA, I suggest Texas Instruments because of linux support. [https://d3se566zfvnmhf.cloudfront.net/sites/default/files/answerbase/Focusrite_IEEE_1394_Compatibility_article.pdf](https://d3se566zfvnmhf.cloudfront.net/sites/default/files/answerbase/Focusrite_IEEE_1394_Compatibility_article.pdf) . Anyhow, I cannot guarantee that buying a new card will solve the problem. You said that everything is working fine on your HP laptop. Let's see your laptop hardware. Repost the output of lspci -vnn from your laptop.

---

### Post by Massimo_Morelli on 2014-03-11
Hi guys, sorry, sometimes I've to work


Yes I known, it's just an attemp
My laptop has RICOH 5C832 Chipset, but it's integratet chip.

I  found, here in Florence a shop wich has a firewire card whit VIA VT6306  chipset. This chipset it's recommended fro FOCUSRITE and seems  compatible whit Linux.
I could not find a card with chipset Texas Instruments available
In one hour i can test it.

fingers crossed

---

### Post by Massimo_Morelli on 2014-03-11
I'm back!

I've install the new firewire card whit VIA VT6306 chipset...
the first boot it was perfect...jack started immediately, no x-run in 20 minutes
Now...I have fear!

I try to turn off and on again.

fingers crossed

---

### Post by Massimo_Morelli on 2014-03-11
YESSSSS!!!!

jack started again!! whitout problem

damn chipset nec!!!

The turning point was the Focusrite device compatibility document (tanks to CrocoDuck)

thanks to everyone who helped me ... I am very grateful



:guitar:

---

### Post by CrocoDuck on 2014-03-11
[COLOR=#ff8c00]QUACK!!![/COLOR] Glad to have been useful! As jejeman said:

[QUOTE=jejeman]
a lot involved in software realm
[/QUOTE]

TI chipset are told to be te best for the linux + audio combo, anyhow this is not the whole story. The support depends on drivers and kernels too and sometimes a lot change between versions. If you will experience some issue again consider to give a try to some other distro. It can give some hint and you can understand how to solve the issues with your favourite one! Here a list of nice distros:

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)
[http://tangostudio.tuxfamily.org/](http://tangostudio.tuxfamily.org/)
[http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)
[http://puppylinux.org/wikka/PuppyStudio](http://puppylinux.org/wikka/PuppyStudio) (old but gold)
[http://www.dynebolic.org/](http://www.dynebolic.org/) (old but gold)
[http://puredyne.goto10.org/](http://puredyne.goto10.org/) (still old but gold, these ones are useful to test your system under older software)
[https://spins.fedoraproject.org/it/jam-kde/](https://spins.fedoraproject.org/it/jam-kde/)
[http://www.ap-linux.com/](http://www.ap-linux.com/)

Any distro can be configured for audio puroposes. I've shared sometimes this thread I started on linux musicians: [http://linuxmusicians.com/viewtopic.php?f=19&t=10837](http://linuxmusicians.com/viewtopic.php?f=19&t=10837) . I've collected there links from all over the internet. Take a look if you want. Have fun, I hope that everything will go smooth now!

---

### Post by Massimo_Morelli on 2014-03-11
I tried to install kxstudio which is suggested by most linux audio italian user community, but I had some issues installing it in a ssd , so untill I solve this problem I'll use ubuntu studio which hasn't any problem with ssd installation. 
Is there a dedicated session for kxstudio?

anyway, the incompatibility was beetwen the sund card and the pci firewire's chipset which works fine with linux but not whit focusrite sound card yet

---


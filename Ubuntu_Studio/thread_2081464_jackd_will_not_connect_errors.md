---
title: "jackd will not connect errors"
date: 2012-11-06
forum: Ubuntu Studio
---

### Post by zealibib slaughter on 2012-11-06
I've been chasing this problem down for hours now and still cant figure out what happened.  I was running qjackctl and guitarix fine up till i decided to change the tuning and started lingot.  Now jack won't start.  I've purged lingot and purged and reinstalled jack, alsa and pulseaudio. I've made sure I am a member of the audio group and tried everything I could find on google and here.  So far this is what I have found.  Jack is looking for /dev/audio which doesn't exist. I've tried to change the input and output but it still doesn't help 

EDIT btw this is on ubuntu studio 12.04 64bit

here is the errors
```
23:04:28.738 Patchbay deactivated.
23:04:29.008 Statistics reset.
23:04:29.098 ALSA connection change.
23:04:29.121 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
23:04:29.133 ALSA connection graph change.
23:04:35.885 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Tue Nov  6 23:04:35 2012: Starting jack server...
Tue Nov  6 23:04:35 2012: Jack: server `default' registered
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 23:04:35 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 23:04:35 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 23:04:35 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 23:04:35 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 23:04:35 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 23:04:35 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 23:04:35 2012: Jack: Create non RT thread
Tue Nov  6 23:04:35 2012: Jack: ThreadHandler: start
Tue Nov  6 23:04:35 2012: Jack: playback device hw:0
Tue Nov  6 23:04:35 2012: Jack: capture device hw:0
Tue Nov  6 23:04:35 2012: Jack: apparent rate = 44100
Tue Nov  6 23:04:35 2012: Jack: frames per period = 1024
Tue Nov  6 23:04:35 2012: Jack: capture device hw:0,0
Tue Nov  6 23:04:35 2012: Jack: playback device hw:0,0
Tue Nov  6 23:04:35 2012: Jack: JackDriver::Open capture_driver_name = hw:0,0
Tue Nov  6 23:04:35 2012: Jack: JackDriver::Open playback_driver_name = hw:0,0
Tue Nov  6 23:04:35 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 23:04:35 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 23:04:35 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 23:04:35 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 23:04:35 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 23:04:35 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 23:04:35 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 23:04:35 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 23:04:35 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 23:04:35 2012: control device hw:0
Tue Nov  6 23:04:35 2012: control device hw:0
Tue Nov  6 23:04:35 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Tue Nov  6 23:04:35 2012: [1m[31mERROR: Audio device hw:0,0 cannot be acquired...[0m
Tue Nov  6 23:04:35 2012: Jack: ~JackDriver
Tue Nov  6 23:04:35 2012: [1m[31mERROR: Cannot initialize driver[0m
Tue Nov  6 23:04:35 2012: Jack: no message buffer overruns
Tue Nov  6 23:04:35 2012: Jack: JackPosixThread::Stop
Tue Nov  6 23:04:35 2012: Jack: ThreadHandler: exit
Tue Nov  6 23:04:35 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Tue Nov  6 23:04:35 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 23:04:35 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 23:04:35 2012: Jack: ~JackDriver
Tue Nov  6 23:04:35 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 23:04:35 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 23:04:35 2012: Jack: cleaning up shared memory
Tue Nov  6 23:04:35 2012: Jack: cleaning up files
Tue Nov  6 23:04:35 2012: Jack: unregistering server `default'
Tue Nov  6 23:04:35 2012: [1m[31mERROR: Failed to open server[0m
Tue Nov  6 23:04:37 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
23:04:39.883 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

the jack logfile at ~/.log/jack/jackdbus.log
```
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 5 ref2 = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 3 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 6 dst = 9
Tue Nov  6 22:18:43 2012: Connecting 'PulseAudio JACK Sink:front-right' to 'gx_head_amp:in_0'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_0 dst = system:playback_1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_0 dst_name = system:playback_1
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 14 dst = 3
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 14 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 14 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 3 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 14 dst = 3
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_0' to 'system:playback_1'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_0 dst = system:playback_2
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_0 dst_name = system:playback_2
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 14 dst = 4
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 14 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 14 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 4 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 14 dst = 4
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_0' to 'system:playback_2'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_0 dst = PulseAudio JACK Source:front-left
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_0 dst_name = PulseAudio JACK Source:front-left
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 14 dst = 7
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 14 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 14 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 7 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 4 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 6 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 14 dst = 7
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_0' to 'PulseAudio JACK Source:front-left'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_0 dst = PulseAudio JACK Source:front-right
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_0 dst_name = PulseAudio JACK Source:front-right
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 14 dst = 8
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 14 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 14 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 8 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 4 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 14 dst = 8
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_0' to 'PulseAudio JACK Source:front-right'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_1 dst = system:playback_2
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_1 dst_name = system:playback_2
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 15 dst = 4
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 15 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 15 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 4 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 15 dst = 4
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_1' to 'system:playback_2'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_1 dst = system:playback_1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_1 dst_name = system:playback_1
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 15 dst = 3
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 15 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 15 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 3 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 15 dst = 3
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_1' to 'system:playback_1'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_1 dst = PulseAudio JACK Source:front-left
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_1 dst_name = PulseAudio JACK Source:front-left
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 15 dst = 7
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 15 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 15 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 7 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 4 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 15 dst = 7
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_1' to 'PulseAudio JACK Source:front-left'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_fx:out_1 dst = PulseAudio JACK Source:front-right
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_fx:out_1 dst_name = PulseAudio JACK Source:front-right
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 15 dst = 8
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 6, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is true
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 15 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 15 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 8 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 4 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 6 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 15 dst = 8
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_fx:out_1' to 'PulseAudio JACK Source:front-right'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Jack: JackRequest::ConnectNamePorts
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = gx_head_amp:out_0 dst = gx_head_fx:in_0
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::CheckConnect src_name = gx_head_amp:out_0 dst_name = gx_head_fx:in_0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortConnect src = 11 dst = 13
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = 6, src = 5, dst = 6)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is true
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Connect port_src = 11 port_dst = 13
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 11 port_dst = 13
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Connect port_src = 13 port_dst = 11
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 6 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 4 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 1 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 5 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 5 ref2 = 6
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackClient::kPortConnectCallback src = 11 dst = 13
Tue Nov  6 22:18:43 2012: Connecting 'gx_head_amp:out_0' to 'gx_head_fx:in_0'
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 11
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: JackRequest::Notification
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 4
Tue Nov  6 22:18:43 2012: Jack: JackClient::kGraphOrderCallback
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 3 client = PulseAudio JACK Sink name = PulseAudio JACK Sink notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 6 client = gx_head_fx name = gx_head_fx notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 4 client = PulseAudio JACK Source name = PulseAudio JACK Source notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 4 client = PulseAudio JACK Source name = PulseAudio JACK Source notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 2
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 6 client = gx_head_fx name = gx_head_fx notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 3 client = PulseAudio JACK Sink name = PulseAudio JACK Sink notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 2
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 2 fd = 9
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 3 fd = 11
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 4 fd = 13
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 5 fd = 15
Tue Nov  6 22:18:43 2012: Stopping jack server...
Tue Nov  6 22:18:43 2012: Jack: JackClient::Deactivate
Tue Nov  6 22:18:43 2012: Jack: JackEngine::ClientDeactivate ref = 2 name = dbusapi
Tue Nov  6 22:18:43 2012: Jack: JackServer::Deactivate client = 2 was not activated
Tue Nov  6 22:18:43 2012: Jack: JackServer::Deactivate client = 2 was not activated
Tue Nov  6 22:18:43 2012: Jack: JackProcessSync::TimedWait time out = 5000000
Tue Nov  6 22:18:43 2012: Jack: fPollTable i = 1 fd = 8
Tue Nov  6 22:18:43 2012: Jack: JackRequest::Notification
Tue Nov  6 22:18:43 2012: Jack: JackProcessSync::TimedWait finished delta = 16752.0
Tue Nov  6 22:18:43 2012: Jack: JackClient::Deactivate res = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 4
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 3 client = PulseAudio JACK Sink name = PulseAudio JACK Sink notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 6 client = gx_head_fx name = gx_head_fx notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RecalculateLatency port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 4 client = PulseAudio JACK Source name = PulseAudio JACK Source notify = 18
Tue Nov  6 22:18:43 2012: Client 'system' with PID 0 is out
Tue Nov  6 22:18:43 2012: Client 'PulseAudio JACK Sink' with PID 2140 is out
Tue Nov  6 22:18:43 2012: Client 'PulseAudio JACK Source' with PID 2140 is out
Tue Nov  6 22:18:43 2012: Client 'gx_head_amp' with PID 2474 is out
Tue Nov  6 22:18:43 2012: Client 'gx_head_fx' with PID 2474 is out
Tue Nov  6 22:18:43 2012: Jack: jack_client_close
Tue Nov  6 22:18:43 2012: Jack: JackClient::Close ref = 2
Tue Nov  6 22:18:43 2012: Jack: JackClient::Deactivate
Tue Nov  6 22:18:43 2012: Jack: JackEngine::ClientCloseAux ref = 2
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RemoveAllPorts ref = 2
Tue Nov  6 22:18:43 2012: Jack: JackProcessSync::TimedWait time out = 1000000
Tue Nov  6 22:18:43 2012: Jack: JackProcessSync::TimedWait finished delta = 11463.0
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 2 driver = system name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 2 driver = freewheel name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 2 client = PulseAudio JACK Sink name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 2 client = PulseAudio JACK Source name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 2 client = gx_head_amp name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 2 client = gx_head_fx name = dbusapi notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_dbusapi
Tue Nov  6 22:18:43 2012: Jack: jack_client_close res = 0
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 1 driver = freewheel name = freewheel notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackServer::Stop
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 4 client = PulseAudio JACK Source name = PulseAudio JACK Source notify = 18
Tue Nov  6 22:18:43 2012: Jack: JackPosixThread::Kill
Tue Nov  6 22:18:43 2012: Jack: JackPosixMutex::Unlock res = 1
Tue Nov  6 22:18:43 2012: ERROR: Unknown error...
Tue Nov  6 22:18:43 2012: Jack: JackThreadedDriver::Stop
Tue Nov  6 22:18:43 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:18:43 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:18:43 2012: Jack: JackServer::Close
Tue Nov  6 22:18:43 2012: Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackAudioDriver::Detach
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortUnRegister ref = 0 port_index = 1
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 1 dst = 65535
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 1 dst = 7
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 0, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 1 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 1 port_dst = 7
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 7 port_dst = 1
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 0 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 1 dst = 9
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 0, dst = 5)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 1 port_dst = 9
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 1 port_dst = 9
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 9 port_dst = 1
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 0 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortUnRegister ref = 0 port_index = 2
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 2 dst = 65535
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 2 dst = 8
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 0, dst = 4)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 2 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 2 port_dst = 8
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 8 port_dst = 2
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 0 ref2 = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 2 dst = 9
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 0, dst = 5)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 2 port_dst = 9
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 2 port_dst = 9
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 9 port_dst = 2
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 0 ref2 = 5
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortUnRegister ref = 0 port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 3 dst = 65535
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 5 dst = 3
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 3, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 5 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 5 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 3 port_dst = 5
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 3 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 14 dst = 3
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 14 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 14 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 3 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 15 dst = 3
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 15 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 15 port_dst = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 3 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectAllInput port_index = 3
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 3 
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortUnRegister ref = 0 port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 4 dst = 65535
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 6 dst = 4
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 3, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 6 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 6 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 4 port_dst = 6
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 3 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 3 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 14 dst = 4
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 14 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 14 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 4 port_dst = 14
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::PortDisconnect src = 15 dst = 4
Tue Nov  6 22:18:43 2012: Jack: CheckPortsConnect(caller = -1, src = 6, dst = 0)
Tue Nov  6 22:18:43 2012: Jack: src_self is false
Tue Nov  6 22:18:43 2012: Jack: dst_self is false
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::Disconnect port_src = 15 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 15 port_dst = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::Disconnect port_src = 4 port_dst = 15
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DecConnectionRef: ref1 = 6 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 12
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 12
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectAllInput port_index = 4
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 4 
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 5 client = gx_head_amp name = gx_head_amp notify = 10
Tue Nov  6 22:18:43 2012: Jack: JackEngine::NotifyClient: no callback for event = 10
Tue Nov  6 22:18:43 2012: Jack: JackDriver::Close
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectRefNum cur_index = 15 ref1 = 0 ref2 = 0
Tue Nov  6 22:18:43 2012: Jack: JackEngine::ClientCloseAux ref = 0
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RemoveAllPorts ref = 0
Tue Nov  6 22:18:43 2012: Jack: JackDriver::ClientNotify ref = 0 driver = freewheel name = system notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 0 client = PulseAudio JACK Sink name = system notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 0 client = PulseAudio JACK Source name = system notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 0 client = gx_head_amp name = system notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 0 client = gx_head_fx name = system notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_system
Tue Nov  6 22:18:43 2012: Jack: JackDriver::Close
Tue Nov  6 22:18:43 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 1 ref2 = 1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::DisconnectRefNum cur_index = 15 ref1 = 1 ref2 = 1
Tue Nov  6 22:18:43 2012: Jack: JackEngine::ClientCloseAux ref = 1
Tue Nov  6 22:18:43 2012: Jack: JackGraphManager::RemoveAllPorts ref = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 1 client = PulseAudio JACK Sink name = freewheel notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 1 client = PulseAudio JACK Source name = freewheel notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 1 client = gx_head_amp name = freewheel notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::ClientNotify ref = 1 client = gx_head_fx name = freewheel notify = 1
Tue Nov  6 22:18:43 2012: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_freewheel
Tue Nov  6 22:18:43 2012: Jack: JackEngine::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackEngine::Close external client = PulseAudio JACK Sink
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::Close
Tue Nov  6 22:18:43 2012: Jack: JackSocketNotifyChannel::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 2
Tue Nov  6 22:18:43 2012: Jack: JackEngine::Close external client = PulseAudio JACK Source
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::Close
Tue Nov  6 22:18:43 2012: Jack: JackSocketNotifyChannel::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 3
Tue Nov  6 22:18:43 2012: Jack: JackEngine::Close external client = gx_head_amp
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::Close
Tue Nov  6 22:18:43 2012: Jack: JackSocketNotifyChannel::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 4
Tue Nov  6 22:18:43 2012: Jack: JackEngine::Close external client = gx_head_fx
Tue Nov  6 22:18:43 2012: Jack: JackExternalClient::Close
Tue Nov  6 22:18:43 2012: Jack: JackSocketNotifyChannel::Close
Tue Nov  6 22:18:43 2012: Jack: JackClientSocket::Close
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 5
Tue Nov  6 22:18:43 2012: Jack: no message buffer overruns
Tue Nov  6 22:18:43 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:18:43 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:18:43 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:18:43 2012: Jack: ~JackDriver
Tue Nov  6 22:18:43 2012: Jack: ~JackDriver
Tue Nov  6 22:18:43 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:18:43 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:18:43 2012: Jack: cleaning up shared memory
Tue Nov  6 22:18:43 2012: Jack: cleaning up files
Tue Nov  6 22:18:43 2012: Jack: unregistering server `default'
Tue Nov  6 22:18:58 2012: Starting jack server...
Tue Nov  6 22:18:58 2012: Jack: server `default' registered
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:18:58 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:18:58 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:18:58 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:18:58 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:18:58 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:18:58 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:18:58 2012: Jack: Create non RT thread
Tue Nov  6 22:18:58 2012: Jack: ThreadHandler: start
Tue Nov  6 22:18:58 2012: Jack: playback device hw:0
Tue Nov  6 22:18:58 2012: Jack: capture device hw:0
Tue Nov  6 22:18:58 2012: Jack: apparent rate = 44100
Tue Nov  6 22:18:58 2012: Jack: frames per period = 1024
Tue Nov  6 22:18:58 2012: Jack: JackDriver::Open capture_driver_name = hw:0
Tue Nov  6 22:18:58 2012: Jack: JackDriver::Open playback_driver_name = hw:0
Tue Nov  6 22:18:58 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:18:58 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:18:58 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:18:58 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:18:58 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:18:58 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:18:58 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:18:58 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:18:58 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:18:58 2012: control device hw:0
Tue Nov  6 22:18:58 2012: control device hw:0
Tue Nov  6 22:18:58 2012: ERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory
Tue Nov  6 22:18:58 2012: ERROR: Audio device hw:0 cannot be acquired...
Tue Nov  6 22:18:58 2012: Jack: ~JackDriver
Tue Nov  6 22:18:58 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:18:58 2012: Jack: no message buffer overruns
Tue Nov  6 22:18:58 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:18:58 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:18:58 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:18:58 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:18:58 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:18:58 2012: Jack: ~JackDriver
Tue Nov  6 22:18:58 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:18:58 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:18:58 2012: Jack: cleaning up shared memory
Tue Nov  6 22:18:58 2012: Jack: cleaning up files
Tue Nov  6 22:18:58 2012: Jack: unregistering server `default'
Tue Nov  6 22:18:58 2012: ERROR: Failed to open server
Tue Nov  6 22:19:00 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:19:15 2012: ERROR: Invalid container address 'driver':'ignorehw':'(null)' supplied to method 'SetParameterValue'.
Tue Nov  6 22:19:16 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:19:16 2012: ERROR: Invalid container address 'driver':'wordlength':'(null)' supplied to method 'SetParameterValue'.
Tue Nov  6 22:19:17 2012: Starting jack server...
Tue Nov  6 22:19:17 2012: Jack: server `default' registered
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:17 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:19:17 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:19:17 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:19:17 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:17 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:19:17 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:19:17 2012: Jack: Create non RT thread
Tue Nov  6 22:19:17 2012: Jack: ThreadHandler: start
Tue Nov  6 22:19:17 2012: Jack: playback device hw:0
Tue Nov  6 22:19:17 2012: Jack: capture device hw:0
Tue Nov  6 22:19:17 2012: Jack: apparent rate = 44100
Tue Nov  6 22:19:17 2012: Jack: frames per period = 1024
Tue Nov  6 22:19:17 2012: Jack: JackDriver::Open capture_driver_name = hw:0
Tue Nov  6 22:19:17 2012: Jack: JackDriver::Open playback_driver_name = hw:0
Tue Nov  6 22:19:17 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:19:17 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:19:17 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:19:17 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:19:17 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:19:17 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:19:17 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:19:17 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:19:17 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:19:17 2012: control device hw:0
Tue Nov  6 22:19:17 2012: control device hw:0
Tue Nov  6 22:19:17 2012: ERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory
Tue Nov  6 22:19:17 2012: ERROR: Audio device hw:0 cannot be acquired...
Tue Nov  6 22:19:17 2012: Jack: ~JackDriver
Tue Nov  6 22:19:17 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:19:17 2012: Jack: no message buffer overruns
Tue Nov  6 22:19:17 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:19:17 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:19:17 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:19:17 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:19:17 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:19:17 2012: Jack: ~JackDriver
Tue Nov  6 22:19:17 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:19:17 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:19:17 2012: Jack: cleaning up shared memory
Tue Nov  6 22:19:17 2012: Jack: cleaning up files
Tue Nov  6 22:19:17 2012: Jack: unregistering server `default'
Tue Nov  6 22:19:17 2012: ERROR: Failed to open server
Tue Nov  6 22:19:19 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:19:30 2012: Starting jack server...
Tue Nov  6 22:19:30 2012: Jack: server `default' registered
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:30 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:19:30 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:19:30 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:19:30 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:19:30 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:19:30 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:19:30 2012: Jack: Create non RT thread
Tue Nov  6 22:19:30 2012: Jack: ThreadHandler: start
Tue Nov  6 22:19:30 2012: Jack: playback device hw:0
Tue Nov  6 22:19:30 2012: Jack: capture device hw:0
Tue Nov  6 22:19:30 2012: Jack: apparent rate = 44100
Tue Nov  6 22:19:30 2012: Jack: frames per period = 1024
Tue Nov  6 22:19:30 2012: Jack: JackDriver::Open capture_driver_name = hw:0
Tue Nov  6 22:19:30 2012: Jack: JackDriver::Open playback_driver_name = hw:0
Tue Nov  6 22:19:30 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:19:30 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:19:30 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:19:30 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:19:30 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:19:30 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:19:30 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:19:30 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:19:30 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:19:30 2012: control device hw:0
Tue Nov  6 22:19:30 2012: control device hw:0
Tue Nov  6 22:19:30 2012: ERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory
Tue Nov  6 22:19:30 2012: ERROR: Audio device hw:0 cannot be acquired...
Tue Nov  6 22:19:30 2012: Jack: ~JackDriver
Tue Nov  6 22:19:30 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:19:30 2012: Jack: no message buffer overruns
Tue Nov  6 22:19:30 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:19:30 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:19:30 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:19:30 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:19:30 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:19:30 2012: Jack: ~JackDriver
Tue Nov  6 22:19:30 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:19:30 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:19:30 2012: Jack: cleaning up shared memory
Tue Nov  6 22:19:30 2012: Jack: cleaning up files
Tue Nov  6 22:19:30 2012: Jack: unregistering server `default'
Tue Nov  6 22:19:30 2012: ERROR: Failed to open server
Tue Nov  6 22:19:32 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:20:00 2012: Starting jack server...
Tue Nov  6 22:20:00 2012: Jack: server `default' registered
Tue Nov  6 22:20:00 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:20:00 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:20:00 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:20:00 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:20:00 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:20:00 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:20:01 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:20:01 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:20:01 2012: Jack: Create non RT thread
Tue Nov  6 22:20:01 2012: Jack: ThreadHandler: start
Tue Nov  6 22:20:01 2012: Jack: playback device hw:0
Tue Nov  6 22:20:01 2012: Jack: capture device hw:0
Tue Nov  6 22:20:01 2012: Jack: apparent rate = 44100
Tue Nov  6 22:20:01 2012: Jack: frames per period = 1024
Tue Nov  6 22:20:01 2012: Jack: capture device /dev/audio
Tue Nov  6 22:20:01 2012: Jack: playback device /dev/audio
Tue Nov  6 22:20:01 2012: Jack: JackDriver::Open capture_driver_name = /dev/audio
Tue Nov  6 22:20:01 2012: Jack: JackDriver::Open playback_driver_name = /dev/audio
Tue Nov  6 22:20:01 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:20:01 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:20:01 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:20:01 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:20:01 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:20:01 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:20:01 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:20:01 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:20:01 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:20:01 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:20:01 2012: Acquired audio card Audio-1
Tue Nov  6 22:20:01 2012: creating alsa driver ... /dev/audio|/dev/audio|1024|3|44100|0|0|nomon|swmeter|-|32bit
Tue Nov  6 22:20:01 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:20:01 2012: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Tue Nov  6 22:20:01 2012: Jack: JackDriver::Close
Tue Nov  6 22:20:01 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Tue Nov  6 22:20:01 2012: Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:20:01 2012: Jack: JackEngine::ClientCloseAux ref = 0
Tue Nov  6 22:20:01 2012: Jack: JackGraphManager::RemoveAllPorts ref = 0
Tue Nov  6 22:20:01 2012: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_system
Tue Nov  6 22:20:01 2012: Jack: ~JackDriver
Tue Nov  6 22:20:01 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:20:01 2012: Jack: no message buffer overruns
Tue Nov  6 22:20:01 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:20:01 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:20:01 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:20:01 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:20:01 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:20:01 2012: Jack: ~JackDriver
Tue Nov  6 22:20:01 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:20:01 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:20:01 2012: Jack: cleaning up shared memory
Tue Nov  6 22:20:01 2012: Jack: cleaning up files
Tue Nov  6 22:20:01 2012: Jack: unregistering server `default'
Tue Nov  6 22:20:01 2012: ERROR: Failed to open server
Tue Nov  6 22:20:01 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:27:41 2012: Starting jack server...
Tue Nov  6 22:27:41 2012: Jack: server `default' registered
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:41 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:27:41 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:27:41 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:27:41 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:41 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:27:41 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:27:41 2012: Jack: Create non RT thread
Tue Nov  6 22:27:41 2012: Jack: ThreadHandler: start
Tue Nov  6 22:27:41 2012: Jack: playback device hw:0
Tue Nov  6 22:27:41 2012: Jack: capture device hw:0
Tue Nov  6 22:27:41 2012: Jack: apparent rate = 44100
Tue Nov  6 22:27:41 2012: Jack: frames per period = 1024
Tue Nov  6 22:27:41 2012: Jack: capture device /dev/audio
Tue Nov  6 22:27:41 2012: Jack: playback device /dev/audio
Tue Nov  6 22:27:41 2012: Jack: JackDriver::Open capture_driver_name = /dev/audio
Tue Nov  6 22:27:41 2012: Jack: JackDriver::Open playback_driver_name = /dev/audio
Tue Nov  6 22:27:41 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:27:41 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:27:41 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:27:41 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:27:41 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:27:41 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:27:41 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:27:41 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:27:41 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:27:41 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:27:41 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:27:41 2012: ERROR: Failed to acquire device name : Audio-1 error : Cannot allocate memory
Tue Nov  6 22:27:41 2012: ERROR: Audio device /dev/audio cannot be acquired...
Tue Nov  6 22:27:41 2012: Jack: ~JackDriver
Tue Nov  6 22:27:41 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:27:41 2012: Jack: no message buffer overruns
Tue Nov  6 22:27:41 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:27:41 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:27:41 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:27:41 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:27:41 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:27:41 2012: Jack: ~JackDriver
Tue Nov  6 22:27:41 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:27:41 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:27:41 2012: Jack: cleaning up shared memory
Tue Nov  6 22:27:41 2012: Jack: cleaning up files
Tue Nov  6 22:27:41 2012: Jack: unregistering server `default'
Tue Nov  6 22:27:41 2012: ERROR: Failed to open server
Tue Nov  6 22:27:43 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:27:57 2012: Starting jack server...
Tue Nov  6 22:27:57 2012: Jack: server `default' registered
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:57 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:27:57 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:27:57 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:27:57 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:27:57 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:27:57 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:27:57 2012: Jack: Create non RT thread
Tue Nov  6 22:27:57 2012: Jack: ThreadHandler: start
Tue Nov  6 22:27:57 2012: Jack: playback device hw:0
Tue Nov  6 22:27:57 2012: Jack: capture device hw:0
Tue Nov  6 22:27:57 2012: Jack: apparent rate = 44100
Tue Nov  6 22:27:57 2012: Jack: frames per period = 1024
Tue Nov  6 22:27:57 2012: Jack: capture device /dev/audio
Tue Nov  6 22:27:57 2012: Jack: playback device /dev/audio
Tue Nov  6 22:27:57 2012: Jack: JackDriver::Open capture_driver_name = /dev/audio
Tue Nov  6 22:27:57 2012: Jack: JackDriver::Open playback_driver_name = /dev/audio
Tue Nov  6 22:27:57 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:27:57 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:27:57 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:27:57 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:27:57 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:27:57 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:27:57 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:27:57 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:27:57 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:27:57 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:27:57 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:27:57 2012: ERROR: Failed to acquire device name : Audio-1 error : Cannot allocate memory
Tue Nov  6 22:27:57 2012: ERROR: Audio device /dev/audio cannot be acquired...
Tue Nov  6 22:27:57 2012: Jack: ~JackDriver
Tue Nov  6 22:27:57 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:27:57 2012: Jack: no message buffer overruns
Tue Nov  6 22:27:57 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:27:57 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:27:57 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:27:57 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:27:57 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:27:57 2012: Jack: ~JackDriver
Tue Nov  6 22:27:57 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:27:57 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:27:57 2012: Jack: cleaning up shared memory
Tue Nov  6 22:27:57 2012: Jack: cleaning up files
Tue Nov  6 22:27:57 2012: Jack: unregistering server `default'
Tue Nov  6 22:27:57 2012: ERROR: Failed to open server
Tue Nov  6 22:27:58 2012: Saving settings to "/home/jerry/.config/jack/conf.xml" ...
Tue Nov  6 22:28:41 2012: ERROR: Can't execute this method with stopped JACK server
Tue Nov  6 22:29:48 2012: Starting jack server...
Tue Nov  6 22:29:48 2012: Jack: server `default' registered
Tue Nov  6 22:29:48 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:29:48 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:29:48 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:29:48 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:29:48 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:29:49 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:29:49 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:29:49 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:29:49 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:29:49 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:29:49 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:29:49 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:29:49 2012: Jack: Create non RT thread
Tue Nov  6 22:29:49 2012: Jack: ThreadHandler: start
Tue Nov  6 22:29:49 2012: Jack: playback device hw:0
Tue Nov  6 22:29:49 2012: Jack: capture device hw:0
Tue Nov  6 22:29:49 2012: Jack: apparent rate = 44100
Tue Nov  6 22:29:49 2012: Jack: frames per period = 1024
Tue Nov  6 22:29:49 2012: Jack: capture device /dev/audio
Tue Nov  6 22:29:49 2012: Jack: playback device /dev/audio
Tue Nov  6 22:29:49 2012: Jack: JackDriver::Open capture_driver_name = /dev/audio
Tue Nov  6 22:29:49 2012: Jack: JackDriver::Open playback_driver_name = /dev/audio
Tue Nov  6 22:29:49 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:29:49 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:29:49 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:29:49 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:29:49 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:29:49 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:29:49 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:29:49 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:29:49 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:29:49 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:29:49 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:29:49 2012: ERROR: Failed to acquire device name : Audio-1 error : Cannot allocate memory
Tue Nov  6 22:29:49 2012: ERROR: Audio device /dev/audio cannot be acquired...
Tue Nov  6 22:29:49 2012: Jack: ~JackDriver
Tue Nov  6 22:29:49 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:29:49 2012: Jack: no message buffer overruns
Tue Nov  6 22:29:49 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:29:49 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:29:49 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:29:49 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:29:49 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:29:49 2012: Jack: ~JackDriver
Tue Nov  6 22:29:49 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:29:49 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:29:49 2012: Jack: cleaning up shared memory
Tue Nov  6 22:29:49 2012: Jack: cleaning up files
Tue Nov  6 22:29:49 2012: Jack: unregistering server `default'
Tue Nov  6 22:29:49 2012: ERROR: Failed to open server
Tue Nov  6 22:30:50 2012: Starting jack server...
Tue Nov  6 22:30:50 2012: Jack: server `default' registered
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:30:50 2012: JACK server starting in realtime mode with priority 10
Tue Nov  6 22:30:50 2012: Jack: JackShmMem::new index = 0 attached = 40a3000 size = 82246176 
Tue Nov  6 22:30:50 2012: Jack: JackShmMem::new placement size = 13048352
Tue Nov  6 22:30:50 2012: Jack: Succeeded in locking 82246176 byte memory area
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitConnections size = 6523136 
Tue Nov  6 22:30:50 2012: Jack: JackConnectionManager::InitClients
Tue Nov  6 22:30:50 2012: Jack: JackShmMem::new index = 1 attached = 10fa3000 size = 1040 
Tue Nov  6 22:30:50 2012: Jack: Succeeded in locking 1040 byte memory area
Tue Nov  6 22:30:50 2012: Jack: Create non RT thread
Tue Nov  6 22:30:50 2012: Jack: ThreadHandler: start
Tue Nov  6 22:30:51 2012: Jack: playback device hw:0
Tue Nov  6 22:30:51 2012: Jack: capture device hw:0
Tue Nov  6 22:30:51 2012: Jack: apparent rate = 44100
Tue Nov  6 22:30:51 2012: Jack: frames per period = 1024
Tue Nov  6 22:30:51 2012: Jack: capture device /dev/audio
Tue Nov  6 22:30:51 2012: Jack: playback device /dev/audio
Tue Nov  6 22:30:51 2012: Jack: JackDriver::Open capture_driver_name = /dev/audio
Tue Nov  6 22:30:51 2012: Jack: JackDriver::Open playback_driver_name = /dev/audio
Tue Nov  6 22:30:51 2012: Jack: Check protocol client = 8 server = 8
Tue Nov  6 22:30:51 2012: Jack: JackEngine::ClientInternalOpen: name = system
Tue Nov  6 22:30:51 2012: Jack: JackEngine::AllocateRefNum ref = 0
Tue Nov  6 22:30:51 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Tue Nov  6 22:30:51 2012: Jack: JackEngine::NotifyAddClient: name = system
Tue Nov  6 22:30:51 2012: Jack: JackGraphManager::SetBufferSize size = 1024
Tue Nov  6 22:30:51 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Tue Nov  6 22:30:51 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Tue Nov  6 22:30:51 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Tue Nov  6 22:30:51 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:30:51 2012: ERROR: control open "/dev/audio" (No such file or directory)
Tue Nov  6 22:30:51 2012: ERROR: Failed to acquire device name : Audio-1 error : Cannot allocate memory
Tue Nov  6 22:30:51 2012: ERROR: Audio device /dev/audio cannot be acquired...
Tue Nov  6 22:30:51 2012: Jack: ~JackDriver
Tue Nov  6 22:30:51 2012: ERROR: Cannot initialize driver
Tue Nov  6 22:30:51 2012: Jack: no message buffer overruns
Tue Nov  6 22:30:51 2012: Jack: ThreadHandler: exit
Tue Nov  6 22:30:51 2012: Jack: JackPosixThread::Stop
Tue Nov  6 22:30:51 2012: ERROR: JackServer::Open() failed with -1
Tue Nov  6 22:30:51 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Tue Nov  6 22:30:51 2012: Jack: JackShmMem::delete size = 0 index = 0
Tue Nov  6 22:30:51 2012: Jack: ~JackDriver
Tue Nov  6 22:30:51 2012: Jack: Succeeded in unlocking 1040 byte memory area
Tue Nov  6 22:30:51 2012: Jack: JackShmMem::delete size = 0 index = 1
Tue Nov  6 22:30:51 2012: Jack: cleaning up shared memory
Tue Nov  6 22:30:51 2012: Jack: cleaning up files
Tue Nov  6 22:30:51 2012: Jack: unregistering server `default'
Tue Nov  6 22:30:51 2012: ERROR: Failed to open server

```

output of aplay -l
```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions

```

output of arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

output of cat /proc/asound/cards
 ```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbe38000 irq 41

```

hope someone can help on this

Maybe some of this info will help someone. It is working now although I dont know why.  I decided to take a break and powered down my system. On restart everything is back to normal.  I'm not clear what the difference is between this and the ten reboots I done is but it did start working.  After reviewing the logs I was starting to think that jack didn't have enough available memory to start. That still doesn't explain why jack was trying to access /dev/audio.  Hope this will help someone down the line sometime.

---

### Post by portets on 2012-12-22
I appear to have this exact same issue on 12.10 64-bit. Only mine hasn't spontaneously resolved itself. I have tried everything I can find and have been attempting for hours. :-|

Any ideas?

---

### Post by damocci on 2012-12-25
I'm a complete amateur at Linux but from what I gather the one thing we have in common is that the three of us are using the 64-bit version of the OS. It seems as though most of the installation instructions posted all over the net are 32-bit instructions. Maybe if you can figure out how to substitute the 32-bit absolutes with 64-bit equivalents (like how you would switch Program Files and Program Files (x86) in Windows) that might solve the problem. I can't figure it out myself right now

---

### Post by jejeman on 2012-12-26
> **damocci said:**
> I'm a complete amateur at Linux but from what I gather the one thing we have in common is that the three of us are using the 64-bit version of the OS. It seems as though most of the installation instructions posted all over the net are 32-bit instructions. Maybe if you can figure out how to substitute the 32-bit absolutes with 64-bit equivalents (like how you would switch Program Files and Program Files (x86) in Windows) that might solve the problem. I can't figure it out myself right now
There should be nothing different beetween 64bit and 32bit regarding this issue.
Give me an example of "32bit" instructions.

---


---
title: "Ventrilo works at first..."
date: 2009-01-06
forum: Wine
---

### Post by Jaz969 on 2009-01-06
Ok, so I'm trying to run Ventrilo through wine with a CA0106 soundcard. At first it works, but in a couple minutes, it makes me lose all my sound. Like if I ran Amarok, I cannot hear music unless I end the session and log back in. Below I pasted my terminal for ventrilo.exe


```

jimmy@ubuntu:~$ winecfg
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
jimmy@ubuntu:~$ cd /ventrilo
bash: cd: /ventrilo: No such file or directory
jimmy@ubuntu:~$ cd ~/ventrilo
jimmy@ubuntu:~/ventrilo$ wine ./ventrilo.exe
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:win:FlashWindowEx 0x327698
fixme:wave:widRecorder Recovering from XRUN!
fixme:wave:widRecorder Recovering from XRUN!
fixme:wave:widRecorder Recovering from XRUN!
fixme:wave:widRecorder Recovering from XRUN!
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
err:wave:wodOpen Error open: Device or resource busy
fixme:wave:widRecorder Recovering from XRUN!
fixme:winmm:MMDRV_Exit Closing while ll-driver open
jimmy@ubuntu:~/ventrilo$ 

```

---


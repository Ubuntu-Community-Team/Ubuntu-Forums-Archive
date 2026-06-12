---
title: "COD 2 Installation problem"
date: 2009-04-10
forum: Wine
---

### Post by McTricks on 2009-04-10
Ok, this is weird...

I open up the terminal and type:

```
wine /media/COD2CD1/setup.exe
```

Then, the install opens, I go through all the agreements and it starts installing, but then, the installation finishes, without _actually_ installing the program... it didn't even ask me for CD2... all that seemed to install was the icons

Am I doing something wrong?

---

### Post by McTricks on 2009-04-10
Bump

---

### Post by asdfoo on 2009-04-11
> **McTricks said:**
> Bump

which Wine version? 1.1.19?

terminal output?

---

### Post by McTricks on 2009-04-11
1) How do I check my version?

2) This is everything that I have in the terminal... it looks like it was too long for it to hold on to everthing

```
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
fixme:wave:wodOpen unimplemented format: WAVE_FORMAT_ADPCM
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x5004c
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x5004c
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x5004c
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x5004c
fixme:wavemap:wodWrite Not all src buffer has been written, expect bogus sound
fixme:advapi:LookupAccountNameW (null) L"mctricks" (nil) 0x7dfb84f8 (nil) 0x7dfb84fc 0x7dfb84f0 - stub
fixme:advapi:LookupAccountNameW (null) L"mctricks" 0xd01a18 0x7dfb84f8 0xcfd4f8 0x7dfb84fc 0x7dfb84f0 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:RpcImpersonateClient (0xd6af90): stub
fixme:rpc:RpcRevertToSelfEx (0xd6af90): stub
fixme:rpc:RpcImpersonateClient (0xd6b548): stub
fixme:rpc:RpcRevertToSelfEx (0xd6b548): stub
fixme:rpc:RpcImpersonateClient (0xd6b4c8): stub
fixme:rpc:RpcRevertToSelfEx (0xd6b4c8): stub
fixme:rpc:RpcImpersonateClient (0xd6b3d8): stub
fixme:rpc:RpcRevertToSelfEx (0xd6b3d8): stub
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 17 ignored L"CreateFolder" table values
fixme:rpc:RpcImpersonateClient (0x1b41288): stub
fixme:rpc:RpcRevertToSelfEx (0x1b41288): stub
fixme:wavemap:wodWrite Not all src buffer has been written, expect bogus sound
fixme:msi:MsiGetMode 4 6
fixme:rpc:RpcImpersonateClient (0x1b41f40): stub
fixme:rpc:RpcRevertToSelfEx (0x1b41f40): stub
fixme:rpc:RpcImpersonateClient (0x1b40c80): stub
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:rpc:RpcRevertToSelfEx (0x1b40c80): stub
fixme:rpc:RpcImpersonateClient (0x1b43188): stub
fixme:rpc:RpcRevertToSelfEx (0x1b43188): stub
fixme:rpc:RpcImpersonateClient (0x1b42aa8): stub
fixme:rpc:RpcRevertToSelfEx (0x1b42aa8): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x4c0000001a
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:advapi:LookupAccountNameW (null) L"mctricks" (nil) 0x33d058 (nil) 0x33d05c 0x33d050 - stub
fixme:advapi:LookupAccountNameW (null) L"mctricks" 0x1b49f60 0x33d058 0x1b48e68 0x33d05c 0x33d050 - stub
fixme:shell:IShellLinkA_fnGetPath (0xcf5670): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf5670): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf5288): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf5288): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xc8eed8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xc8eed8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba7430): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba7430): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf56e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf56e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf5560): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf5560): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba75e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba75e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba75e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba75e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf56e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0xcf56e8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba99f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1ba99f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1baa090): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1baa090): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Current Working Directory: F:\
Autorun.ini Location: F:\setup\rsrc\autorun.ini
Program Windows Class: WinSupClass
Program Windows Class: InstallShield_Win
Program Windows Class: TApplication
Program Windows Class: CoD2
Program Windows Class: CoD2
Program Windows Caption: Call of Duty(R) 2
Program Windows Caption: Call of Duty 2 Multiplayer
Program Windows Caption: Call of Duty 2
Launch Program Location: .\setup\rsrc\launch.exe
mctricks@lester:~$ err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```

---

### Post by McTricks on 2009-04-11
Bump

---

### Post by asdfoo on 2009-04-11
> **McTricks said:**
> Bump

stop doing this, you only irritate people.


to find the Wine version, type wine --version at a terminal, if it's less than 1.1.18, visit [http://winehq.org/](http://winehq.org/) to download a beta release

---

### Post by McTricks on 2009-04-12
Dang... I feel like an idot... I didn't realize that 8.04 was an LTS release... I'm still using it...

---


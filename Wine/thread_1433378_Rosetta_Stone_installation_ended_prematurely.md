---
title: "Rosetta Stone installation ended prematurely"
date: 2010-03-19
forum: Wine
---

### Post by qogima1024 on 2010-03-19
I have searched the forums for a solution to this but nothing has worked when i try and install Rosetta Stone it always says that the installation ended prematurely i have copy-pasted the terminal after running "wine [path to setup.exe]" below. Any help on this would be greatly appreciated, I don't want to have to dual box windoze just to use this.







blaine@localhost:~$ wine '/media/cdrom0/setup.exe' 
fixme:system:SetProcessDPIAware stub!
fixme:advapi:CheckTokenMembership ((nil) 0x138510 0x36fd0c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x138510 0x36fd0c) stub!
fixme:advapi:LookupAccountNameW (null) L"blaine" (nil) 0x33e79c (nil) 0x33e7a0 0x33e794 - stub
fixme:advapi:LookupAccountNameW (null) L"blaine" 0x1425b8 0x33e79c 0x13b478 0x33e7a0 0x33e794 - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:msi_dialog_handle_event Unknown progress message 3
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:msi:msi_dialog_handle_event Unknown progress message 3
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 6 ignored L"CreateFolder" table values
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:DllCanUnloadNow 
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
^Cblaine@localhost:~$

edit:

if anyone knows how to disable emoticons that would be great

---

### Post by asdfoo on 2010-03-19
you don't say which version of Wine you are using, so I will assume it is an old one.

Upgrade to the latest, which is 1.1.41 [http://winehq.org/download](http://winehq.org/download)

---

### Post by feedmecereal on 2010-03-20
Check out [this tutorial]("http://ubuntuforums.org/showthread.php?t=1334710").

---


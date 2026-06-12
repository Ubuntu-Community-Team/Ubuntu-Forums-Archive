---
title: "Wine/libSM6 &quot;Unresolved symbol uuid_unparse_lower&quot;"
date: 2009-11-06
forum: Wine
---

### Post by chslaxcoach on 2009-11-06
I am using Ubuntu 9.04, Wine version 1.1.32 and libsm6 version 2:1.1.0-1

When I try to do almost anything wine-related from command line I get an unresolved symbol error in the libSM.so.6 library.

I can run 'Notepad' successfully from the Wine menu, but I could not install IE7.  Even winecfg gives me this link error.

I had things working fine using the 'ies4linux' installation but that stopped working.  So I have tried re-installing wine a couple times.  After doing:

```

sudo apt-get remove --purge wine
rm -rf ~/.wine
sudo apt-get install wine

```

This is what I got when running 'winecfg'

```

dave@dhenning-ubuntu:~/Desktop: winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower

*** FREEZE ***

```

Does anyone have any clue why I am getting this unresolved symbol?  

I don't know if it is Wine-related, but I don't see it at any other time.

For what it's worth, I can run the 'winecfg' program using the menu item.  Both it and Notepad take a couple seconds and a couple screen flickers to get going, but they seem to work.

I also tried installing IE7 and got these related errors shown below:

```

dave@dhenning-ubuntu:~/Desktop$ wine IE7-WindowsXP-x86-enu.exe 
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": /usr/lib/libSM.so.6: undefined symbol: uuid_unparse_lower
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Unknown error (127).

```

Thanks in advance for any help,
Dave ...

---


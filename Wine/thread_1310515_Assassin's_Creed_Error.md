---
title: "Assassin's Creed Error"
date: 2009-11-01
forum: Wine
---

### Post by charkoal on 2009-11-01
When i click to install this game it comes up with the error message: Error Code:	-5003 : 0xffffec75
Error Information:
>SetupNew\SetupDLL.cpp (719)

I also tried to install it with cedega but the same error occurs.

---

### Post by beastrace91 on 2009-11-02
What Wine version? What Cedega Engine are you trying it with?

~Jeff

---

### Post by charkoal on 2009-11-02
Cedega Version 6.0.2 

Wine version 0.9.59

---

### Post by charkoal on 2009-11-02
I updated wine to version 1.1.32

I have looked up on and have seen other have installed it with this version, but I cant seem to get the installer to even start now when I open the setup.exe with wine now.

If anyone has a solution to this I would like to hear it thanks.

After some looking around I try to install it now and it comes up with a new error but similar to the previous one: Error Code:	-5001 : 0xffffec6b
Error Information:
>SetupNew\SetupDLL.cpp (77)

---

### Post by alex.rayu on 2009-11-02
That is a heave game. You are unlikely to enjoy it under wine even if you succeed in installing it.

---

### Post by beastrace91 on 2009-11-02
> **alex.rayu said:**
> That is a heave game. You are unlikely to enjoy it under wine even if you succeed in installing it.

Depends on your hardware. I rock alot of newer titles under Wine/Cedega just fine under Ubuntu.

Regarding the crash - try using different Wine versions. The posting in the appdb says it yields good results for 1.1.30 on Ubuntu. Also regarding the Cedega version - do you have a subscription? If so try it under the latest 7.3 engine as their appdb lists it works quiet well under that one.

~Jeff

---

### Post by charkoal on 2009-11-02
I tried installing the game using crossover now, seeing I cant get it to install with winie and a different message comes up saying i need to be on admin acc.

Whats the terminal code to get admin please?

---

### Post by beastrace91 on 2009-11-02
By "admin" do you mean super user? If so just prefix your command with **sudo**

~Jeff

---

### Post by charkoal on 2009-11-02
I mean administrator

---

### Post by charkoal on 2009-11-03
I run it in terminal and this message comes up:

charkoal@Compaqv3000:~$ cd /media/cdrom0
charkoal@Compaqv3000:/media/cdrom0$ wine setup.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:winedevice:ServiceMain driver L"SecDrv" failed to load
err:menubuilder:init_xdg error looking up the desktop directory
charkoal@Compaqv3000:/media/cdrom0$ 

Do you know what i need to do in order to fix this?

---

### Post by charkoal on 2009-11-03
Sorry for the double post there was a problem but i fixed it. To do with the post I mean.

---


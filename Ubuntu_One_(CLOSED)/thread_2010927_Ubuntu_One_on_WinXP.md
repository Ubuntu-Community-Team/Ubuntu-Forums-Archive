---
title: "Ubuntu One on WinXP"
date: 2012-06-26
forum: Ubuntu One (CLOSED)
---

### Post by Trucoto on 2012-06-26
Hello, I want to use Ubuntu One between my Ubuntu 12.04 box (at home) and my Windows XP box (at work). No problems on creating an account from Ubuntu; on Windows I installed the previous version but as I have a proxy it didn't work; I installed version 3.0.2 (it seems it has a proxy option) but after install it won't start. No matter how many times I click in the icon, nothing happens. Any ideas?

---

### Post by firetag on 2012-06-27
Sorry, I can't help, but I have the same Problem running on Server 2003 SP2.
Calling u1sdtool gives the following output:

[FONT=Courier New]C:\Programme\ubuntuone\dist>u1sdtool.exe
Traceback (most recent call last):
  File "u1sdtool", line 59, in <module>
  File "ubuntuone\platform\__init__.pyc", line 34, in <module>
  File "ubuntu_sso\xdg_base_directory\__init__.pyc", line 55, in <module>
  File "ubuntu_sso\xdg_base_directory\windows.pyc", line 77, in <module>
  File "ubuntu_sso\xdg_base_directory\windows.pyc", line 46, in get_special_fold
ers
  File "win32com\__init__.pyc", line 5, in <module>
  File "win32api.pyc", line 12, in <module>
  File "win32api.pyc", line 10, in __load
ImportError: DLL load failed: Die angegebene Prozedur wurde nicht gefunden.
[/FONT]
any suggestion anyone?
thanks in advance.

---

### Post by martinro on 2012-06-30
> **Trucoto said:**
> Hello, I want to use Ubuntu One between my Ubuntu 12.04 box (at home) and my Windows XP box (at work). No problems on creating an account from Ubuntu; on Windows I installed the previous version but as I have a proxy it didn't work; I installed version 3.0.2 (it seems it has a proxy option) but after install it won't start. No matter how many times I click in the icon, nothing happens. Any ideas?

Known bug on 3.0.2 windows installer 
[https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/1017019](https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/1017019)

---


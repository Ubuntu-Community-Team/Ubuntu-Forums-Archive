---
title: "Installing pyside6"
date: 2023-08-18
forum: Ubuntu Dev Link Forum
---

### Post by yoav_by on 2023-08-18
Hello,

I have some python programs that uses pyside6 (developed under manjaro). When trying to run them the following error is printed:
```
ModuleNotFoundError: No module named 'PySide6'
```
Tried to re-activate the virtual environment but that didn't help.

Trying to install pyside6 system-wide doesn't work. The command:
```
pip install pyside6-essentials
```
Emmits the error: 
```
This environment is externally managed
```
Tried using pipx, that didn't work too.

Help will be appreciated.

TIA

---

### Post by TheFu on 2023-08-18
I'm not a python guy, but Ubuntu ships with specific versions of python to be used by the OS.  NEVER touch those.  What you need to do is to create the python environment that you need using environment variable management under your account only, not system-wide.  This can be handled manually, but there are tools that specifically do this.  **pyenv** is one. There are others.  So, install pyenv, then using that to install the specific version of python you want/need, all the modules for that specific python and whatever pyside6 needs.

You can have 1 version or 50 versions of python as completely separate environments this way. AND it will all work.  I know it does for perl and ruby, which use similar tools.   Using these separate environments is how professionals deploy their code in self-contained packages across different servers.

For more on these: [https://stackoverflow.com/questions/38217545/what-is-the-difference-between-pyenv-virtualenv-anaconda](https://stackoverflow.com/questions/38217545/what-is-the-difference-between-pyenv-virtualenv-anaconda)  That's what google found.

After your account is setup to use a specific version of python, you need to be careful when using system tools, since the python you are using for developing python programs will be used.  This can have terrible impacts, especially during complex tasks like patching the OS.  I once left a much newer version of perl setup and did an OS major release upgrade.  It ended poorly. The system wouldn't boot.  Python is much more important to Ubuntu than perl, so I bet the problems will be much greater.  

Some of these tools have a way to automatically change to the correct environment when you enter a specific directory hierarchy. This is really handy, since when you are in those directories, you are, by definition, coding and want to use the specific version of python, pip, et al.

Sorry, I don't have any specific answer, but perhaps provided a path to greatly improve your coding methods.

And don't forget to use a version control system!  Even when programming alone, that habit has saved me too many times to name.

---


---
title: "error: externally-managed-environment"
date: 2023-03-24
forum: Ubuntu Development Version
---

### Post by hoboy on 2023-03-24
I am using ubuntu 23.04 since some updates I can''t use python comment in the terminal
it cause this error. 
as far as I know this is not debian.
python -m pip install Jinja2                                                                                     
error: externally-managed-environment                                                                                       
                                                                                                                            
× This environment is externally managed                                                                                    
&#9584;&#9472;> To install Python packages system-wide, try apt install                                                                 
    python3-xyz, where xyz is the package you are trying to                                                                 
    install.                                                                                                                
                                                                                                                            
    If you wish to install a non-Debian-packaged Python package,                                                            
    create a virtual environment using python3 -m venv path/to/venv.                                                        
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make                                                         
    sure you have python3-full installed.                                                                                   
                                                                                                                            
    If you wish to install a non-Debian packaged Python application,                                                        
    it may be easiest to use pipx install xyz, which will manage a                                                          
    virtual environment for you. Make sure you have pipx installed.                                                         
                                                                                                                            
    See /usr/share/doc/python3.11/README.venv for more information.                                                         
                                                                                                                            
note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.

---

### Post by MAFoElffen on 2023-03-24
You have syntax errors on 
```

[COLOR=#ff0000]python[/COLOR] -m [COLOR=#ff0000]pip[/COLOR] install Jinja2

```
Which tries to install it as a systemwide package, instead of a user package in a Python virtual environment... And if it had worked, it would have been a bad idea on Lunar anyways. It's a good thing that it did not work.

Explanation. 'python' does not exist on Ubuntu, unless you installed compatibility package 'python-is-python3'. 'python3' invokes Python 3. The 'pip' was for Python2. For Python 3 is pip3. But do not do that. Jinja2 **will not** **work** on Lunar.

If you are using pip or pip3, then you invoke as a user into a virtual environment, such as
```

pip3 install <packagename>

```
To install the pip3 installed package into a virtual environment in the user's home folder... But...

Jinja2 system requirements are as follows
> 
Jinja2 works with Python 2.6.x, 2.7.x and >= 3.3. If you are using Python 3.2 you can use an older release of Jinja2 (2.6) as support for Python 3.2 was dropped in Jinja2 version 2.7.

Python3 version 3.3 shipped with Ubuntu 12.10 (October 2012)... Many years ago.

On Lunar:
```

mafoelffen@lunar-server-04:~$ pyhton3 --version
Python 3.10.8

```
As you can see, Jinja2 will not work on that version.

---

### Post by hoboy on 2023-03-25
Thanks it is not only Jinja, it is python in general.
python --version
Python 3.11.2

pip install --upgrade pip
error: externally-managed-environment

× This environment is externally managed
&#9584;&#9472;> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
    
    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.
    
    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
    
    See /usr/share/doc/python3.11/README.venv for more information.

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.

---

### Post by hoboy on 2023-03-25
So it is the python not working 

pip install tensorflow==2.12.*
error: externally-managed-environment

× This environment is externally managed
&#9584;&#9472;> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
    
    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.
    
    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
    
    See /usr/share/doc/python3.11/README.venv for more information.

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.

---


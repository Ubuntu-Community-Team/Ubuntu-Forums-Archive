---
title: "Problems installing virtualenv &amp; virtualenvwrapper"
date: 2013-05-03
forum: Virtualisation
---

### Post by charliezen on 2013-05-03
I am trying to install virtualenv and wrapper and I get the following error:

IOError: [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/pymongo-2.4.2.egg-info/top_level.txt'

I indeed dont have permission to that file.

I have tried doing everything when in the root account and most of it works,
except when I come to actually using virtualenv. 

When I "source" for a new environment, it does not work, and "sudo source" doesnt work, as we know.

Today I discovered that I get the same error when doing "pip freeze" so it is an access problem but
I do not know how to solve this... 

appreciate the help, thanks...

---

### Post by sanukcm on 2013-05-12
Having exactly the same problem. Following the instructions: 

```
$ sudo apt-get install python-pip
$sudo pip install virtualenv
$sudo pip install virtualenvwrapper
$mkdir ~/.virtualenvs
```

Then appending this to my ~/.bashrc file: 


```
export WORKON_HOME=~/.virtualenvs
export PROJECT_HOME=$HOME/Projects
source /usr/local/bin/virtualenvwrapper.sh

```



When I run ```
source ~/.bashrc
```

I get the following: 


```
Traceback (most recent call last):
  File "/usr/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/dist-packages/virtualenvwrapper/hook_loader.py", line 16, in <module>
    from stevedore import ExtensionManager
  File "/usr/local/lib/python2.7/dist-packages/stevedore/__init__.py", line 1, in <module>
    #
  File "/usr/local/lib/python2.7/dist-packages/stevedore/extension.py", line 4, in <module>
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2727, in <module>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 700, in subscribe
    callback(dist)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2727, in <lambda>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2227, in activate
    self.insert_on(path)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2334, in insert_on
    self.check_version_conflict()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2373, in check_version_conflict
    for modname in self._get_metadata('top_level.txt'):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2221, in _get_metadata
    for line in self.get_metadata_lines(name):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1209, in get_metadata_lines
    return yield_lines(self.get_metadata(name))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1201, in get_metadata
    return self._get(self._fn(self.egg_info,name))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1316, in _get
    stream = open(path, 'rb')
IOError: [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/virtualenv_clone-0.2.4.egg-info/top_level.txt'
virtualenvwrapper.sh: There was a problem running the initialization hooks. 


If Python could not import the module virtualenvwrapper.hook_loader,
check that virtualenv has been installed for
VIRTUALENVWRAPPER_PYTHON=/usr/bin/python and that PATH is
set properly.

```

Looks like there were some [similar problems previously a few years back]("https://bitbucket.org/dhellmann/virtualenvwrapper/issue/62/") - but recently it seems that others are [getting this working in ubuntu without any hassle]("http://roundhere.net/journal/virtualenv-ubuntu-12-10/")... 

Any ideas?

---

### Post by sanukcm on 2013-05-12
Had some dinner and came back to this. I hate messing with permissions / groups with a tool like pip and the packages it installs - but I can't find a better solution. It looks like pip is setting the group for packages to "staff". 

```

$ ls -l /usr/local/lib/python2.7/dist-packages/virtualenv_clone-0.2.4.egg-info/top_level.txt 
-rw-r----- 1 root staff 16 May 13 00:46 /usr/local/lib/python2.7/dist-packages/virtualenv_clone-0.2.4.egg-info/top_level.txt

```

Adding my user to the staff group sorted me out. Is the group for all pip installed packages set to staff? Are you supposed to add yourself to this group when you install pip? I didn't see this in the documentation and I used pip on a python project a few months back on another ubuntu machine and never ran into this. Strange...

---


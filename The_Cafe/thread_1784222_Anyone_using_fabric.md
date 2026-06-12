---
title: "Anyone using fabric?"
date: 2011-06-16
forum: The Cafe
---

### Post by P1C0 on 2011-06-16
..and willing to share a script? :p

I am talking about this: [fabric]("http://docs.fabfile.org/en/1.0.1/index.html")

Here is an example of automating the compiling of a LaTeX document:
```

from fabric.api import local

file = "simAuction"
printer = "lp"

def clean():
    extensions = [".log",".nav",".toc",".out",".vrb",".snm",".blg",".lof",".bbl",".glo",".lot",".ist",".aux"]
    for extension in extensions:
       local("rm -f " + file + extension)

def all():
    local("rm -f " + file + ".pdf")
    clean()
    local("pdflatex " + file + ".tex")
    local("bibtex " + file + ".aux")
    local("pdflatex " + file + ".tex")
    local("pdflatex " + file + ".tex")
    local("evince " + file + ".pdf" + " &")
    clean()

def p():
    local("lpr -P " + printer + " " + file + ".pdf")
    local("lpq -P " + printer)

```

Could it be done with a makefile? Of course. But fabric also allows remote administration tasks:
```

from fabric.api import run, sudo, local

def host_type():
    run('uname -s')

def disk_size():
    run('df -h')

def update():
    sudo('apt-get update')
    sudo('apt-get upgrade')

```

and..
```

$ fab -H puppy@hive,puppy@oblivion,puppy@work,root@oldie,kitty@linus,kitty@teleios
host_type
[kitty@teleios] Executing task 'host_type'
[kitty@teleios] run: uname -s
[kitty@teleios] Login password:
[kitty@teleios] out: Linux
[kitty@teleios] out:
[kitty@linus] Executing task 'host_type'
[kitty@linus] run: uname -s
[kitty@linus] out: Linux
[kitty@linus] out:
[puppy@hive] Executing task 'host_type'
[puppy@hive] run: uname -s
[puppy@hive] out: OpenBSD
[puppy@hive] out:
[root@oldie] Executing task 'host_type'
[root@oldie] run: uname -s
[root@oldie] out: OpenBSD
[root@oldie] out:
[puppy@work] Executing task 'host_type'
[puppy@work] run: uname -s
[puppy@work] out: Linux
[puppy@work] out:
[puppy@oblivion] Executing task 'host_type'
[puppy@oblivion] run: uname -s
[puppy@oblivion] out: Linux
[puppy@oblivion] out:

Done.
Disconnecting from kitty@teleios... done.
Disconnecting from work... done.
Disconnecting from oblivion... done.
Disconnecting from kitty@linus... done.
Disconnecting from root@oldie... done.
Disconnecting from hive... done.

```

---

### Post by cgroza on 2011-06-16
Interesting...

---

### Post by juancarlospaco on 2011-06-17
I dont have any, but i want to make a [bottle]("http://bottlepy.org/") web gui to use fabric scripts

---

### Post by P1C0 on 2011-06-17
> **juancarlospaco said:**
> I dont have any, but i want to make a [bottle]("http://bottlepy.org/") web gui to use fabric scriptsPlease share it (or at least part of it) when done!

I find the whole fabric thing cool, but then ..python == coolness :p

---

### Post by juancarlospaco on 2011-06-17
Dont even started, im practicing with bottle right now...

---

### Post by P1C0 on 2011-06-17
Replaced string concatenation with the environment dictionary. Also a small change in p() function. This is a final fabfile.py for compiling LaTeX \m/ 

```
from fabric.api import env, local

env.file = 'simAuction'

def clean():
    extensions = ['log','nav','toc','out','vrb','snm','blg','lof','bbl','glo','lot','ist','aux']
    for env.extension in extensions:
       local('rm -f {file}.{extension}'.format(**env))

def all():
    local('rm -f {file}.pdf'.format(**env))
    clean()
    local('pdflatex {file}.tex'.format(**env))
    local('bibtex {file}.aux'.format(**env))
    local('pdflatex {file}.tex'.format(**env))
    local('pdflatex {file}.tex'.format(**env))
    local('evince {file}.pdf &'.format(**env))
    clean()

def p():
    local('lpr {file}.pdf'.format(**env))
    local('lpq')
```

---


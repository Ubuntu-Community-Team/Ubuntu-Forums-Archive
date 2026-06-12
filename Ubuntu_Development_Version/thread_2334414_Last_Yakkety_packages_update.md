---
title: "Last Yakkety packages update"
date: 2016-08-19
forum: Ubuntu Development Version
---

### Post by s-bodet on 2016-08-19
Hi all,

I'm running Yakkety and the last update broke lots of things :[INDENT]- mysqld still eating more than 100 MB of memory (known issue, tried several workarounds without success),
- cannot launch VMWare Workstation Player anymore, VMWare returns an error message regarding the gcc version (VMWare expects to find the 5.3.1 version),
- no audio anymore (tried several things like reinstall the whole ALSA stuff, I even compiled from sources without success).[/INDENT]

That LTS is a very very big disappointment cause I was in a testing process to implement some SDN stuff in my Cloud.
I cannot rely on unreliable distro :-(
I even plan to restart all those testings with a Red Hat distro.

Hence my question : am I the only one who suffers from those defects ?
What's your feedback about the quality of Yakkety ?

Thx in advance for your feedback !

-sb

---

### Post by howefield on 2016-08-19
Thread moved to the "*Ubuntu Development Version*" forum.

Why would you be running a release in early development if you need something more stable ?

Yakkety should not be run unless you are prepared (expecting) for breakage and to assist in the reporting/developments of the release.

---

### Post by ventrical on 2016-08-19
> **s-bodet said:**
> Hi all,

I'm running Yakkety and the last update broke lots of things :[INDENT]- mysqld still eating more than 100 MB of memory (known issue, tried several workarounds without success),
- cannot launch VMWare Workstation Player anymore, VMWare returns an error message regarding the gcc version (VMWare expects to find the 5.3.1 version),
- no audio anymore (tried several things like reinstall the whole ALSA stuff, I even compiled from sources without success).[/INDENT]

That LTS is a very very big disappointment cause I was in a testing process to implement some SDN stuff in my Cloud.
I cannot rely on unreliable distro :-(
I even plan to restart all those testings with a Red Hat distro.

Hence my question : am I the only one who suffers from those defects ?
What's your feedback about the quality of Yakkety ?

Thx in advance for your feedback !

-sb

The way things are with yakkety now you have to employ added terminal commands.

```

sudo dpkg --configure -a

and 

sudo apt-get install -f

```

should fix things for now.

Regards..

---


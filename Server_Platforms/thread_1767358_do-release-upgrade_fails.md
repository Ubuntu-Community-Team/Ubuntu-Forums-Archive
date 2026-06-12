---
title: "do-release-upgrade fails"
date: 2011-05-25
forum: Server Platforms
---

### Post by isecore on 2011-05-25
So I decided to take the plunge and upgrade my server to Natty. It's a 9.10 server that got upgraded to 10.04 then to 10.10 and now the plan was to make it into a 11.04 machine.

So I do the usual precautions and then punch do-release-upgrade in a screened shell.

Unlike the previous times it produces the following output:

```
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 10, in <module>
    from UpdateManager.Core.DistUpgradeFetcherCore import DistUpgradeFetcherCore
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 34, in <module>
    import GnuPGInterface
ImportError: No module named GnuPGInterface
```

... after which absolutely nothing happens.

So, any clue where to begin with fixing this? Reinstalling is of course NOT an option.

---

### Post by lykwydchykyn on 2011-05-25
Is python-gnupginterface installed?  If not, I'd say installing it would be a good first step.

---

### Post by isecore on 2011-05-26
> **lykwydchykyn said:**
> Is python-gnupginterface installed?  If not, I'd say installing it would be a good first step.

Yes, it's installed. That was the first thing I checked. No go, despite it being installed. I even tried removing it and reinstalling it. No dice.

---

### Post by lykwydchykyn on 2011-05-26
Do you have multiple versions of python installed?

What happens if you open a python prompt and paste in the exact import command from the error?

---

### Post by isecore on 2011-05-26
```
>>> import GnuPGInterface
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named GnuPGInterface
>>>
```

---

### Post by lykwydchykyn on 2011-05-26
> **isecore said:**
> ```
>>> import GnuPGInterface
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named GnuPGInterface
>>>
```

If in fact the library is installed as you say, the only other possibility is that you have multiple versions of python installed, and the library is installed for the wrong version.  The default python install (which appears to be 2.6) is not finding the module.

Either that, or python is somehow subtly wrecked on your system.  Without more data, I can't say.

---

### Post by isecore on 2011-05-26
Damn. So how would I go about finding out if I have multiple Pythons installed? I haven't used anything except the official sources (no PPAs or compiled from source) so maybe it's from an older upgrade?

I'll have to experiment with this, but thanks for your input and help. Much appreciated.

---

### Post by lykwydchykyn on 2011-05-26
check your package manager.  Python releases are usually named like "python2.6" or "python2.5".  aptitude (the package manager, not the abstract quality) is helpful in this regard.  Fire it up and browse under the "local or obsolete" section for old installs of python.

---

### Post by isecore on 2011-05-26
I went through the system. The only python-related packages I have installed are all version 2.6, so no old pythons clogging up the works as far as I can tell. Weird.

---

### Post by isecore on 2011-05-28
Come on, anyone else have any suggestions?

---

### Post by isecore on 2011-06-03
Okay, so for what it's worth - this seemed to solve the problem. I removed the following packages which seemed to be orphaned.

python-smartpm
python-software-properties
update-notifier-common
libmpfr1ldbl
zlibc
libdjvulibre-text

Now do-release-upgrade doesn't immediately spit out the original error. I will attempt the upgrade later tonight and see how it goes.

---

### Post by ASedinkin on 2012-06-24
Also you can try this:
In file /usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py
between lines #33 and #34:
import sys
import GnuPGInterface
add line:
sys.path.append('/usr/share/pyshared/')

So finally you need to see next lines:
import sys
sys.path.append('/usr/share/pyshared/')
import GnuPGInterface

This should help if module python-gnupginterface was installed.

---

### Post by isecore on 2012-06-25
Thanks for the suggestion, I'll try it later this evening!

> **ASedinkin said:**
> Also you can try this:
In file /usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py
between lines #33 and #34:
import sys
import GnuPGInterface
add line:
sys.path.append('/usr/share/pyshared/')

So finally you need to see next lines:
import sys
sys.path.append('/usr/share/pyshared/')
import GnuPGInterface

This should help if module python-gnupginterface was installed.

---

### Post by alecz20 on 2012-09-05
You can try this to solve the python interface error:

```

 cp /usr/share/pyshared/GnuPGInterface.py /usr/lib/python2.6/

```

reference: [http://ulm.ccc.de/pipermail/ssls-dev/2009-February/000051.html](http://ulm.ccc.de/pipermail/ssls-dev/2009-February/000051.html)

---

### Post by bronkeydain on 2012-12-31
> **alecz20 said:**
> You can try this to solve the python interface error:

```

 cp /usr/share/pyshared/GnuPGInterface.py /usr/lib/python2.6/

```

reference: [http://ulm.ccc.de/pipermail/ssls-dev/2009-February/000051.html](http://ulm.ccc.de/pipermail/ssls-dev/2009-February/000051.html)

I had the same problem and your suggestion fixed my problem. Thx.

---


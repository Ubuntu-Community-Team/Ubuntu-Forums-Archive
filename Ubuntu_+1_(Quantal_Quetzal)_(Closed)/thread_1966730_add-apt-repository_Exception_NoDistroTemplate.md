---
title: "add-apt-repository Exception: NoDistroTemplate"
date: 2012-04-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-04-27
```
[08:43:34] ahsl@AL-DESK01:[~]: sudo add-apt-repository ppa:nijel/gammu-testing
[sudo] password for ahsl: 
You are about to add the following PPA to your system:
 This repository contains latest testing versions of Gammu - <http://wammu.eu/gammu/>.
 More info: https://launchpad.net/~nijel/+archive/gammu-testing
Press [ENTER] to continue or ctrl-c to cancel adding it

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 160, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 584, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

I'm assuming this is because we are theoretically running QQ and the PPA goes up to Precise, right?

Regards,
Effenberg

---

### Post by Bowmore on 2012-04-27
Nope, it's because you haven't updated the distribution template, see
[http://ubuntuforums.org/showpost.php?p=11878025&postcount=39](http://ubuntuforums.org/showpost.php?p=11878025&postcount=39)

I've not tested that one but my own and that works for ppa:s too.

---

### Post by effenberg0x0 on 2012-04-27
> **Bowmore said:**
> Nope, it's because you haven't updated the distribution template, see
[http://ubuntuforums.org/showpost.php?p=11878025&postcount=39](http://ubuntuforums.org/showpost.php?p=11878025&postcount=39)

I've not tested that one but my own and that works for ppa:s too.

Thanks for the tip Bowmore, I hadn't seen that post. It's fixed.

Regards,
Effenberg

---

### Post by toobuntu on 2012-05-01
Shouldn't this be a sticky thread?

---

### Post by ventrical on 2012-05-01
> **toobuntu said:**
> Shouldn't this be a sticky thread?


I put that up in the sudo command sticky. If you know of any other sudo commands that would fit for crash recovery then feel free to put them up there.

---

### Post by jbicha on 2012-05-02
This happens every release but it should be fixed now:

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/000287.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/000287.html)

---

### Post by xebian on 2012-05-03
> **jbicha said:**
> This happens every release but it should be fixed now:

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/000287.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/000287.html)

IIRC you were following up with eric5 since 12.04.  Now that 12.10 is going python3 all the way I think eric( still eric4 in quantal) should be upgraded as well to eric5.?

---


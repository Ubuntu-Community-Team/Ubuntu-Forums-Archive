---
title: "[lubuntu Jammy Jellyfish] How do I enable apport?"
date: 2022-03-02
forum: Ubuntu Development Version
---

### Post by breakdaze on 2022-03-02
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport) says:
> How to enable apport

Apport itself is running at all times because it collects crash data for whoopsie (see ErrorTracker). However, the crash interception component is still disabled. To enable it permanently, do:

sudo nano /etc/apport/crashdb.conf

... and add a hash symbol # in the beginning of the following line:

        'problem_types': ['Bug', 'Package'],

To disable crash reporting just remove the hash symbol. 

But, on the live system I booted, I don't see it in there:
```
lubuntu@lubuntu:~$ cat /etc/apport/crashdb.conf
# map crash database names to CrashDatabase implementations and URLs

default = 'ubuntu'

def get_oem_project():
    '''Determine OEM project name from Distribution Channel Descriptor

    Return None if it cannot be determined or does not exist.
    '''
    try:
        dcd = open('/var/lib/ubuntu_dist_channel').read()
        if dcd.startswith('canonical-oem-'):
            return dcd.split('-')[2]
    except IOError:
        return None
                                                                                                                                             
databases = {                                                                                                                                
    'ubuntu': {                                                                                                                              
        'impl': 'launchpad',                                                                                                                 
        'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',                                        
        'dupdb_url': 'http://people.canonical.com/~ubuntu-archive/apport-duplicates',                                                        
        'distro': 'ubuntu',                                                                                                                  
        'escalation_tag': 'bugpattern-needed',                                                                                               
        'escalated_tag': 'bugpattern-written',                                                                                               
    },                                                                                                                                       
    'canonical-oem': {                                                                                                                       
        'impl': 'launchpad',                                                                                                                 
        'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',
        'project': get_oem_project(),
    },
    'debug': {
        # for debugging
        'impl': 'memory',
        'bug_pattern_url': '/tmp/bugpatterns.xml',
        'distro': 'debug'
    },
}

```

---

### Post by guiverc on 2022-03-02
If you've having issues with the installer (`calamares`) with Lubuntu, you just need to use the command (from a terminal; ie. use Ctrl+Alt+T to open; or you can use menu options too)

```

ubuntu-bug calamares
```

ie. I'm telling `ubuntu-bug` to file against the package `calamares` in that example.

You can just enter the command `ubuntu-bug` without options, to be offered some choices too; which is what I do with ISOs which use `subiquity` (ie. a *snap* package).

Apport should already be usable; and to file bugs; you don't need to use the **apport debugger**, only use the part of it that files the bugs.  Ubuntu *jammy* is not yet **stable** so you shouldn't need to change anything.

I've not run today's *daily*, so I'm unaware of any issues that exist onlyon today's ISO, but I've not noted any today on IRC or in my inbox.

---

### Post by wildmanne39 on 2022-03-02
Moved to the Development sub-forum.

---

### Post by breakdaze on 2022-03-02
Ah, got it. I usually use CTRL+ALT+F2 or similar, although the font is rather painful to read on my monitor for some reason. 

I noticed Jammy runs on tty1, while 20.04.4 runs on tty7. The wiki stuff I read doesn't apply here, is what you're saying. Just switch to a different tty text terminal and run: ubuntu-bug calamares

This is the first I heard of "ubuntu-bug"

Well, I will try it later after work...

---

### Post by guiverc on 2022-03-02
:)   

FYI:  I mentioned `ubuntu-bug calamares` in the thread [https://ubuntuforums.org/showthread.php?t=2472438&page=2](https://ubuntuforums.org/showthread.php?t=2472438&page=2) yesterday in that is what I would have used to likely file the bug with your error (as an example).

I didn't mention opening terminal on GUI sorry; as I assumed it was all people would use. 

If you're writing about a bug it's far easier when you can see what you're describing on screen; plus `firefox` will be opened (`ubuntu-bug` doesn't adjust to `w3m` or `lynx` if on a text terminal only.. you're given a very long-strong to type into a GUI that's no fun to copy on a pure text terminal)

---


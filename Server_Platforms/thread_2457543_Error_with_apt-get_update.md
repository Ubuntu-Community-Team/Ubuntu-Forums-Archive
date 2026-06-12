---
title: "Error with apt-get update"
date: 2021-02-04
forum: Server Platforms
---

### Post by NotQuiteSU on 2021-02-04
When I run apt-get update, I get the following error

```
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code


```

Any help would be appreciated

---

### Post by TheFu on 2021-02-04
Doubt I can help, but my first questions were:
[LIST]
[*]which release?
[*]what exact command?
[*]what exact output?
[*]did it ever work? If so, when?
[*]what changed? Any guesses?  Was anything related to python modified?
[*]why don't people post terminal output using 'code tags' so it is easier to read? [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.
[/LIST]

---

### Post by NotQuiteSU on 2021-02-04
I installed Python3 recently and tried to set it as the default for python. Not sure if that went well. My app using python3 is working, but maybe something else was hosed.

As for output, that's exactly the screen. But here's further info:

```

sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease
Hit:5 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu bionic InRelease
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

```

---

### Post by TheFu on 2021-02-04
> **NotQuiteSU said:**
> I installed Python3 recently and tried to set it as the default for python. Not sure if that went well. My app using python3 is working, but maybe something else was hosed. 

Don't do that. You've broken your system.  Put it back. If you don't have backups, you'll probably need to reinstall.  This is called shooting yourself in the chest. At least you missed your head, but it would have been better to hit your foot.  ;)  We've all done things like this before.

**NEVER touch the system installed python or perl programs.**
Use **pyenv** if you need a different version(s) of python for your own custom code.

---

### Post by NotQuiteSU on 2021-02-04
well, luckily this isn't a major issue and a single purpose server. I guess when I have some time, I'll reinstall from scratch

---

### Post by SeijiSensei on 2021-02-04
Do you get the same errors running apt as you do with apt-get?

---

### Post by TheFu on 2021-02-04
> **NotQuiteSU said:**
> well, luckily this isn't a major issue and a single purpose server. I guess when I have some time, I'll reinstall from scratch

Actually, if the system is on any network, then it **IS** a major issue.  An unpatched computer on any network is just waiting to be hacked.  

Sometimes there are mitigations to drastically reduce the attack vectors, but those often defeat the reason to use the system.  If you are building webapps, stop now and do a fresh install. Running any network services is too dangerous.  Just a few days ago, there was an ssh patch that cannot wait, for example.

---

### Post by NotQuiteSU on 2021-02-04
This is an unexposed server, no web apps, anything like that. No external connectivity to worry with. But I appreciate your feedback

---

### Post by #&amp;thj^% on 2021-02-04
It sounds like a bad idea to me to change python to Python 3. The default way to invoke scripts written in Python 2 is **"python my-script-p2.py",** while it's **"python3 my-script-p3.py".** I would expect many many system scripts to rely on this.
I agree with TheFu, messing with setting python2/3 as a default can be a show stopper
```

cd  /usr/lib/python3/dist-packages
ls -la /usr/lib/python3/dist-packages
sudo cp apt_pkg.cpython-36m-x86_64-linux-gnu.so apt_pkg.so
```
That code is a rough guess you'll have to figure out the correct syntax.

I spoke with a couple of devs about the new python changes, and was pointed to:
If you have Ubuntu 20.04 LTS (Focal Fossa) you can install python-is-python3:
```

sudo apt install python-is-python3
```

which replaces the symlink in /usr/bin/python to point to /usr/bin/python3.

Also to use python3, you can use the following command in terminal:
```
 alias python=python3
```

---

### Post by NotQuiteSU on 2021-02-04
So looks like I was wrong.

```

 python -V
Python 2.7.17

```

So I installed Python3, I didn't change the python alias

---

### Post by NotQuiteSU on 2021-02-04
```

cd  /usr/lib/python3/dist-packages ls -la /usr/lib/python3/dist-packages
sudo cp apt_pkg.cpython-36m-x86_64-linux-gnu.so apt_pkg.so

```

This did the trick

---


---
title: "Where did my tab to auto-complete go for my terminal?"
date: 2013-03-01
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-01
normally when i type "sudo apt-get ins" and i hit the tab key it auto-completes install and i could also auto-complete package names
for some reason it is not working on my fresh install of xubuntu raring from todays (March 1st, 2013) daily iso

---

### Post by screaminj3sus on 2013-03-01
working fine for me in xubuntu raring fresh installed the other day

---

### Post by Toz on 2013-03-01
A few things to check:

1. Are you using the bash shell?

2. Is **bash-completion** installed?

3. Does the file **/usr/share/bash-completion/completions/apt-get** exist?

4. Have you tried re-installing bash-completion?

---

### Post by pqwoerituytrueiwoq on 2013-03-01
1. assuming env would tell me if i am running bash, i am running bash
2. yep
3. yep
4. just tried reconfiguring and reinstalling to no avail
i can't seem to auto complete "apt-get" if i start it with sudo (still cant auto-complete 'install')
edit: it works on my guest session, must have been fixed during todays updates, and i just have a outdated config fine in my home folder, but idk which i need to delete

---

### Post by Toz on 2013-03-01
What happens if you source bash_completion:
```
. /usr/share/bash-completion/bash_completion
```
Does it work then?

---

### Post by pqwoerituytrueiwoq on 2013-03-01
```
~$ apt-get ins_init_completion: command not found
_init_completion: command not found
_init_completion: command not found
```

---

### Post by Toz on 2013-03-01
Is that the response that you get when sourcing the /usr/share/bash-completion/bash_completion file? Very odd.

```
ls -l /usr/share/bash-completion/bash_completion
```
...I get:
```
-rw-r--r-- 1 root root 66440 Jul 23  2012 /usr/share/bash-completion/bash_completion
```

Did you change your ~/.bashrc file? Within it:
```
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

---

### Post by pqwoerituytrueiwoq on 2013-03-01
i had this issue litterally after clean installing todays daily iso fro xubuntu, 1st thing i did was open a terminal and go to install synaptic when i noticed it
```
chad@chad-A54C-NB91:~$ ls -l /usr/share/bash-completion/bash_completion
-rw-r--r-- 1 root root 66440 Oct 23 18:12 /usr/share/bash-completion/bash_completion
chad@chad-A54C-NB91:~$ cat .bashrc
cat: .bashrc: No such file or directory
chad@chad-A54C-NB91:~$ cat ~/.bashrc
cat: /home/chad/.bashrc: No such file or directory
chad@chad-A54C-NB91:~$
```

---

### Post by Toz on 2013-03-01
How about:
```
echo $SHELL
```

---

### Post by pqwoerituytrueiwoq on 2013-03-01
```
~$ echo $SHELL
/bin/bash
```

going to sleep now...

---

### Post by Toz on 2013-03-02
> chad@chad-A54C-NB91:~$ cat ~/.bashrc
cat: /home/chad/.bashrc: No such file or directory
Bash is your shell but you don't have a .bashrc file. Try creating one:
```
cp /etc/skel/.bashrc ~/.bashrc
```
...log out and in again.

(assuming that /etc/skel/.bashrc exists)

---

### Post by pqwoerituytrueiwoq on 2013-03-02
that got it
edit: where did mark as solved go under thread tools?

---

### Post by Toz on 2013-03-02
> **pqwoerituytrueiwoq said:**
> that got it
edit: where did mark as solved go under thread tools?

I wonder what happened with that daily build that the .bashrc file wasn't properly copied over? If I have time, I'm going to try to grab the current daily build and test. Might warrant a bug report if its reproduceable.

---

### Post by pqwoerituytrueiwoq on 2013-03-02
the only thing i did special was before installing i made my home folder and my user folder and placed my music and .mozilla folders on to the disk and then installed without formating the drive
on a side note there was a old backed up xp partition on the drive, it appears to have been detected as windows 8, the boot loader on it may have gotten replaced by win8 at some point, the windows installer really lacks options, but i don't care about that as i have not used windows is years (unless i was attempting to fix it for someone)

did you edit the title? or is there a option i did not see?

---

### Post by cariboo on 2013-03-02
I edited the thread for you, but you should be able to do it yourself, click Edit Post on your first post, then select Advanced Editor, above the edit box you should see a prefix drop down, where you can select the Solved prefix.

We were looking at some of the forum plugins this afternoon, and found by disabling some of them, some of things we expected to work, that weren't, started working again. Thread Solved is actually a plugin, that we will have to submit to Canonical IS for security checks, before we can install it.

---

### Post by Worp8d on 2013-05-26
> **Toz said:**
> Bash is your shell but you don't have a .bashrc file. Try creating one:
```
cp /etc/skel/.bashrc ~/.bashrc
```
...log out and in again.

(assuming that /etc/skel/.bashrc exists)

Worked for me too, thanks! Been after a solution for that one for a while.

---


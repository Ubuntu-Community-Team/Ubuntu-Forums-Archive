---
title: "NOPASSWD doesn't apply in sudoers"
date: 2010-06-09
forum: Security
---

### Post by TheSimon on 2010-06-09
Hi,  

I'be this weird problem with sudo. I can't make the  NOPASSWD option to work propertly.
I've tried both:
```
simon    ALL=NOPASSWD:/usr/bin/whoami
```and 
```
simon   ALL=(root)  NOPASSWD:/usr/bin/whoami
```I've few machines that run RH  with  the exactly same row without any problem. I've searched the doc's and  google and couldn't find similar problem. (I've found [this topic]("http://ubuntuforums.org/showthread.php?t=607598")  and in order to eliminate script problem, I tried with whoami)


```
simon@abc:~/SYNC$   sudo cat /etc/sudoers
[sudo] password for simon:
# /etc/sudoers
#
#  This file MUST be edited with the 'visudo' command as root.
#
#  See the man page for details on how to write a sudoers file.
#

Defaults          env_reset

# Host alias specification

# User alias  specification

# Cmnd alias specification

# User privilege  specification
root    ALL=(ALL) ALL
simon    ALL=NOPASSWD:/usr/bin/whoami
# Uncomment to allow members of group  sudo to not need a password
# (Note that later entries override this,  so you might need to move
# it further down)
# %sudo  ALL=NOPASSWD: ALL

# Members of the admin group may gain root  privileges
%admin ALL=(ALL) ALL
simon@abc:~/SYNC$ sudo -k
simon@abc:~/SYNC$   sudo /usr/bin/whoami
[sudo] password for simon:
simon@abc:~/SYNC$


```

(BTW, I edit the sudoers file with visudo of course)

---

### Post by sisco311 on 2010-06-09
Hi and welcome to the forums!

You have to add the line after the %admin ... line:
```

# /etc/sudoers
#
#  This file MUST be edited with the 'visudo' command as root.
#
#  See the man page for details on how to write a sudoers file.
#

Defaults          env_reset

# Host alias specification

# User alias  specification

# Cmnd alias specification

# User privilege  specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group  sudo to not need a password
# (Note that later entries override this,  so you might need to move
# it further down)
# %sudo  ALL=NOPASSWD: ALL

# Members of the admin group may gain root  privileges
%admin ALL=(ALL) ALL

**simon    ALL=NOPASSWD:/usr/bin/whoami**

```

[I]Sudo reads the sudoers file and applies permissions in order from top to bottom. So the last line in the file will overwrite any previous conflict with the config settings. So it is best to put new configuration lines at the bottom.
[/I]

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by TheSimon on 2010-06-09
Gr8! That worked like a magic. I knew it is something obvious.

Now some forum support question :) How do I mark this as solved?

---

### Post by sisco311 on 2010-06-09
> **TheSimon said:**
> Gr8! That worked like a magic. I knew it is something obvious.

Now some forum support question :) How do I mark this as solved?

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

For a screenshot see the link from my signature.

---


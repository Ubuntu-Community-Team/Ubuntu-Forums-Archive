---
title: "how to generate new .Xauthority file?"
date: 2010-01-20
forum: Server Platforms
---

### Post by gobbledigook on 2010-01-20
Hi!

After i upgraded to 9.10 i've been getting errors when i start vncserver and startx

```
xauth:  timeout in locking authority file /home/server/.Xauthority
```

now i just figured i'd delete the .Xauthority file from my home folder and generate a new one! Unfortunately i negated to find out HOW to do this before going ahead and deleting the file... D'oh! Can anyone please point me in the right direction?

---

### Post by kiranmurari on 2010-01-21
Hi,
```
xauth:  timeout in locking authority file /home/server/.Xauthority
```The above error occurs due to permissions issue. /home/server/.Xauthority might have had root permissions. 
Please start the vncserver as the user, instead of root or sudo.

On creating a new .Xauthority file, the following commands can be issued:
```
karmic@karmic-desktop:~$ HOST=`hostname`
karmic@karmic-desktop:~$ key=`perl -e 'srand; printf int(rand(100000000000000000))'`
karmic@karmic-desktop:~$ key=$key$key
karmic@karmic-desktop:~$ xauth add ${HOST}/unix:0 . $key
xauth:  creating new authority file /home/karmic/.Xauthority
xauth: (argv):1:  key contains odd number of or non-hex characters
```Hope this helps.

---

### Post by gobbledigook on 2010-01-21
thanx kiranmurari :)

i tried as you suggested but got the same error:
```
server@server:~$ HOST=`hostname`
server@server:~$ key=`perl -e 'srand; printf int(rand(100000000000000000))'`
server@server:~$ key=$key$key
server@server:~$ xauth add ${HOST}/unix:0 . $key
xauth:  timeout in locking authority file /home/server/.Xauthority

```

but after realised that xauth would just create an .xauthority if one didn't exist so i changed the permissions of my home dir:
```
sudo chmod 777 /home/server/
```

and when i started xauth it worked!

:popcorn:

---

